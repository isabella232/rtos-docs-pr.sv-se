---
title: Kapitel 1 – Introduktion till Azure RTOS NetX POP3
description: NetX Duo POP3-klient-API:et är utformat för att tillhandahålla ett e-posttransportsystem för små arbetsstationer för åtkomst till Klient-maildrops på POP3-servrar för att hämta klient-e-post.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0143b142a39bbda28ae20d41adf08119b8b2f8f99d510a456743b4f447802833
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797236"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a>Kapitel 1 – Introduktion till Azure RTOS NetX POP3

Post Office Protocol Version 3 (POP3) är ett protokoll som utformats för att tillhandahålla ett e-posttransportsystem för små arbetsstationer för åtkomst till klient-maildrops på POP3-servrar för att hämta klient-e-post. POP3 använder Transmission Control Protocol (TCP) för att utföra e-postöverföring. På grund av detta är POP3 ett mycket tillförlitligt protokoll för innehållsöverföring.

POP3 tillhandahåller dock inte omfattande åtgärder för e-posthantering. Normalt laddas e-post ned av klienten och tas sedan bort från serverns e-postdroppe.

## <a name="netx-duo-pop3-client-requirements"></a>NetX Duo POP3-klientkrav

### <a name="client-requirements"></a>Klientkrav

NetX POP3-klient-API:et kräver en tidigare skapad NetX Duo IP-instans med *hjälp av nx_ip_create* och en tidigare skapad NetX-paketpool med hjälp av *nx_packet_pool_create*. Eftersom NetX Duo POP3-klienten använder TCP-tjänster måste  TCP aktiveras med nx_tcp_enable-anropet innan NetX Duo POP3-klient-API:et används på samma IP-instans. POP3-klienten använder en TCP-socket för att ansluta till en POP3-server på serverns POP3-port. Detta anges vanligtvis på den *välkända port 110, men varken POP3-klient* eller server krävs för att använda den här porten.

Storleken på paketpoolen som används för att skapa POP3-klienten är användarkonfigurerbar vad gäller paketnyttolast och antal paket som är tillgängliga. Om paketet endast används i POP3 Client Create-tjänsten behöver paketnyttolasten inte vara längre än 100–120 byte beroende på längden på användarnamn och lösenord, eller APOP-sammanfattning. Kommandot USER med den lokala värdens användarnamn är förmodligen det största meddelandet som skickas av POP3-klienten. Det är möjligt att dela samma paketpool i nx_ip_create (IP-standardpaketpool) eftersom den interna IP-operatiosn inte kräver särskilt stor paketnyttolast för att skicka och ta emot TCP-kontrolldata.

Det är dock inte allmänt fördelaktigt för Ethernet-drivrutinen att använda samma paketpool som POP3-klientpaketpoolen. I allmänhet är nyttolasten för nyttolasten för den mottagna paketpoolen inställd på IP-instansens MTU (vanligtvis 1 500 byte) för nätverksgränssnittet som är mycket större än POP3-klientmeddelanden. Inkommande POP3-meddelanden är vanligtvis mycket större datastorlek än utgående POP3-klientmeddelanden

## <a name="netx-duo-pop3-client-creation"></a>Skapa NetX Duo POP3-klient

Det finns två tjänster för att skapa POP3-klienten. Den rekommenderade tjänsten är *nxd_pop3_client_create* som tar en NXD_ADDRESS-adressdatatyp som accepterar IPv4- eller IPv6-adresser för POP3-servern. Den andra POP3-klient *create-tjänsten, nx_pop3_client_create*, accepterar endast IPv4-adresser för POP3-servern. Båda tjänsterna binder TCP-socketporten och ansluter till POP3-servern.

När du har anslutit med POP3-servern kan POP3-klientprogrammet anropa *nx_pop3_client _mail_items_get* för att hämta antalet e-postobjekt som finns i e-postrutan:

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

Om ett eller flera objekt finns i Client maildrop kan programmet hämta storleken på ett specifikt e-postobjekt med hjälp *av nx_pop3_client_get_mail_item tjänsten:*

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

Det första e-postobjektet i maildrop är vid index 1.

För att hämta det faktiska e-postmeddelandet kan programmet anropa *nx_pop3_client_mail_item_get_message_data-tjänsten* för att hämta e-postmeddelandepaketen tills tjänsten anger att det sista paketet tas emot av final_packet indataargumentet:

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

Om du vill ta bort ett specifikt *e-postobjekt anropar programmet nx_pop3_client_mail_item_delete* med samma index som användes i *föregående nx_pop3_client_get_mail_item anrop.*

Klienten kan tas bort  med hjälp av nx_pop3_client_delete tjänsten. Observera att det är upp till programmet att ta bort POP3-klientpaketpoolen med *hjälp nx_packet_pool_delete-tjänsten* som inte längre har någon användning för den.

## <a name="netx-duo-pop3-client-constraints"></a>NetX Duo POP3-klientbegränsningar

Det finns vissa begränsningar i NetX Duo POP3-klientimplementering:

1. NetX Duo POP3-klienten stöder inte AUTH-kommandot även om den implementerar APOP-autentisering med digest-MD5 för klientserverns autentiseringsutbyte.
2. NetX Duo POP3 Client implementerar inte alla POP3-kommandon (t.ex. TOP- eller UIDL-kommandon). Nedan visas en lista över kommandon som den stöder:
   - Noop
   - RSET

## <a name="netx-duo-pop3-client-login"></a>NetX Duo POP3-klientinloggning

En NetX Duo POP3-klient måste autentisera sig (logga in) på en POP3-server för att få åtkomst till en e-postdroppe. Det kan antingen göra det med hjälp av USER/PASS-kommandona och genom att ange ett användarnamn och lösenord som pop3-servern känner till, eller genom att använda APOP-kommandot och MD5-sammanfattningen som beskrivs nedan.

Användarnamnet är vanligtvis ett fullständigt domännamn (innehåller en lokal del och ett domännamn, avgränsade med ett @-tecken). När du använder POP3-kommandona USER och PASS skickar klienten sitt användarnamn och lösenord okrypterat via Internet.

För att undvika säkerhetsrisken för att rensa textning av användarnamn och lösenord kan NetX Duo POP3-klienten konfigureras för att använda APOP-autentisering genom att *ange APOP_authentication-parametern* i *nxd_pop3_client_create-tjänsten:*

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

Eller för endast IPv4-program *nx_pop3_client_create* tjänsten:

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

När klienten skickar APOP-kommandot tar den som enda argument en MD5-sammanfattning som innehåller serverdomänen, lokal tid och process-ID som extraherats från serverhälsningen, plus klientlösenordet. POP3-servern skapar en MD5-sammanfattning som innehåller samma information och om dess MD5-sammanfattning matchar klientens MD5-sammanfattning autentiseras klienten.

Om APOP-autentiseringen misslyckas försöker NetX Duo POP3-klienten använda USER/PASS-autentisering.

## <a name="the-pop3-client-maildrop"></a>The POP3 Client Maildrop

Klient-e-post lagras på en POP3-server i en postlåda eller "maildrop". En klient-maildrop på en POP3-server representeras som en 1-baserad lista över e-postobjekt. Det innebär att varje e-post refereras till av dess index i maildrop-listan med det första e-postobjektet vid index 1 (inte noll). POP3-kommandon refererar till specifika e-postobjekt efter index i den här listan.

## <a name="the-pop3-protocol-state-machine"></a>POP3-protokolltillståndsdatorn

POP3-protokollet kräver att både klienten och servern upprätthåller tillståndet för POP3-sessionen. Först försöker klienten ansluta till POP3-servern. Om det lyckas ingår det i POP3-protokollet som har tre distinkta tillstånd som definieras av RFC 1939. Det ursprungliga tillståndet är auktoriseringstillståndet där det måste identifiera sig för servern. I auktoriseringstillståndet kan POP3-klienten bara utfärda kommandona USER och PASS, och i den ordningen, eller APOP-kommandot.

När POP3-klienten har autentiserats förs klientsessionen in i transaktionstillståndet. I det här tillståndet kan klienten ladda ned och begära borttagning av e-post. Kommandona som tillåts i transaktionstillståndet är LIST, STAT, RETR, DELE, RSET och QUIT. Vanligtvis skickar POP3-klienten ett STAT-kommando följt av en serie RETR-kommandon (ett för varje e-postobjekt i sin maildrop).

När klienten utfärdar kommandot QUIT förs POP3-sessionen in i uppdateringstillståndet där TCP-anslutningen initieras från servern. Om du vill ladda ned e-post vid en annan tidpunkt kan POP3-klientprogrammet anropa nx_pop3_client_mail_items_get för att söka efter ny e-post i maildrop.

### <a name="pop3-server-reply-codes"></a>POP3-serverns svarskoder

- +OK Servern använder det här svaret för att acceptera ett klientkommando. Servern kan innehålla ytterligare information efter "+OK" men kan inte anta att klienten kommer att bearbeta den här informationen, förutom vid nedladdning av e-postdata eller LIST- eller DELE-kommandon. I det senare fallet "argument" efter att kommandot refererar till indexet för e-postobjektet i Client maildrop.
- -ERR Servern använder det här svaret för att avvisa ett klientkommando. Servern kan skicka ytterligare information efter "-ERR" men kan inte anta att klienten kommer att bearbeta den här informationen.

### <a name="sample-pop3-client---server-session"></a>Exempel på POP3-klient – serversession

**Grundläggande POP3-exempel med USER/PASS:**

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

**Grundläggande POP3-exempel med APOP (och LISTA i stället för STAT):**

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a>RFC:er som stöds av NetX Duo POP3-klienten

NetX Duo Client POP3 är kompatibel med RFC 1939.
