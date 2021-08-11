---
title: Kapitel 1 – Introduktion till Azure RTOS NetX POP3-klient
description: Klient-API:et Azure RTOS NetX POP3 tillhandahåller ett e-posttransportsystem för små arbetsstationer för åtkomst till Klient-e-postlyssnare på POP3-servrar för att hämta klient-e-post.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6abaa778da6203d0df367894165cb29ca629ab5e24403a35af1995f032cf0d4c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798817"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a>Kapitel 1 – Introduktion till Azure RTOS NetX POP3-klient

Post Office Protocol Version 3 (POP3) är ett protokoll som utformats för att tillhandahålla ett e-posttransportsystem för små arbetsstationer för att få åtkomst till client maildrops på POP3-servrar för att hämta klient-e-post. POP3 använder Transmission Control Protocol (TCP) för att utföra e-postöverföring. Pop3 är därför ett mycket tillförlitligt protokoll för innehållsöverföring.

POP3 tillhandahåller dock inte omfattande åtgärder för e-posthantering. Normalt hämtas e-post av klienten och tas sedan bort från serverns maildrop.

## <a name="netx-pop3-client-requirements"></a>NetX POP3-klientkrav

### <a name="client-requirements"></a>Klientkrav

För Azure RTOS NETX POP3-klient-API:et krävs en tidigare skapad NetX IP-instans med *hjälp av nx_ip_create* och en tidigare skapad NetX-paketpool med hjälp av *nx_packet_pool_create*. Eftersom NetX POP3-klienten använder TCP-tjänster måste  TCP aktiveras med nx_tcp_enable-anropet innan NetX POP3-klienttjänsterna används på samma IP-instans. POP3-klienten använder en TCP-socket för att ansluta till en POP3-server på serverns POP3-port. Detta anges vanligtvis på den *välkända port 110, men varken POP3-klient* eller server krävs för att använda den här porten.

Storleken på paketpoolen som används för att skapa POP3-klienten är användarkonfigurerbar vad gäller paketnyttolast och antal paket som är tillgängliga. Om paketet endast används i POP3 Client Create-tjänsten behöver paketnyttolasten inte vara mer än 100–120 byte beroende på längden på användarnamn och lösenord, eller sammanfattning av APOP. Kommandot USER med den lokala värdens användarnamn är förmodligen det största meddelandet som skickas av POP3-klienten. Det går att dela samma paketpool i nx_ip_create (IP-standardpaketpool) eftersom de interna IP-åtgärderna inte kräver en mycket stor paketnyttolast för att skicka och ta emot TCP-kontrolldata.

Det kanske dock inte är fördelaktigt för nätverksdrivrutinen att använda samma paketpool som POP3-klientens paketpool. I allmänhet är nyttolasten för nyttolasten för den mottagna paketpoolen inställd på IP-instansens MTU (vanligtvis 1500 byte) för nätverksgränssnittet som är mycket större än POP3-klientmeddelanden. Inkommande POP3-meddelanden är vanligtvis mycket större data än utgående POP3-klientmeddelanden

## <a name="netx-pop3-client-creation"></a>Skapa NetX POP3-klient

POP3-klienten skapar tjänsten, *nx_pop3_client_create* TCP-socketen och ansluter med POP3-servern.

När du har anslutit med POP3-servern kan POP3-klientprogrammet anropa *nx_pop3_client _mail_items_get* för att hämta antalet e-postobjekt som finns i e-postlyssnarrutan:

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

Om ett eller flera objekt finns i Client maildrop kan programmet hämta storleken på ett specifikt e-postobjekt med hjälp *av nx_pop3_client_get_mail_item tjänsten:*

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

Det första e-postobjektet i maildrop är vid index 1.

För att hämta det faktiska e-postmeddelandet kan programmet anropa *nx_pop3_client_mail_item_get_message_data-tjänsten* för att hämta e-postpaketen tills tjänsten anger att det sista paketet tas emot av final_packet indataargumentet:

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

Om du vill ta bort ett specifikt *e-postobjekt anropar programmet nx_pop3_client_mail_item_delete* med samma index som användes i *föregående nx_pop3_client_get_mail_item anrop.*

Klienten kan tas bort  med hjälp av nx_pop3_client_delete tjänsten. Observera att det är upp till programmet att ta bort POP3-klientens paketpool med hjälp *nx_packet_pool_delete-tjänsten* som inte längre har någon användning för den.

## <a name="netx-pop3-client-constraints"></a>Begränsningar för NetX POP3-klient

Det finns vissa begränsningar i NetX POP3-klientimplementering:

1. NetX POP3-klienten stöder inte AUTH-kommandot även om den implementerar APOP-autentisering med DIGEST-MD5 för klientserverns autentiseringsutbyte.

1. NetX POP3-klienten implementerar inte alla POP3-kommandon (t.ex. TOP- eller UIDL-kommandona). Nedan visas en lista över kommandon som den stöder:
   - Noop
   - RSET

## <a name="netx-pop3-client-login"></a>NetX POP3-klientinloggning

En NetX POP3-klient måste autentisera sig (logga in) på en POP3-server för att få åtkomst till en maildrop. Detta kan antingen användas med kommandona USER/PASS och ange ett användarnamn och lösenord som pop3-servern känner till, eller genom att använda APOP-kommandot och MD5-sammanfattningen som beskrivs nedan.

Användarnamnet är vanligtvis ett fullständigt kvalificerat domännamn (innehåller en lokal del och ett domännamn, avgränsade med ett @-tecken). När du använder POP3-kommandona USER och PASS skickar klienten sitt användarnamn och lösenord okrypterat via Internet.

För att undvika säkerhetsrisken med att rensa användarnamn och lösenord i textning kan NetX POP3-klienten konfigureras att använda APOP-autentisering genom att *ange APOP_authentication-parametern* i *nx_pop3_client_create-tjänsten:*

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

Eller för endast IPv4-program *nx_pop3_client_create* tjänsten:

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

När klienten skickar kommandot APOP tar den en MD5-sammanfattning som innehåller serverdomänen, lokal tid och process-ID som extraherats från serverhälsningen, plus klientlösenordet. POP3-servern skapar en MD5-sammanfattning som innehåller samma information och om dess MD5-sammanfattning matchar klientens MD5-sammanfattning autentiseras klienten.

Om APOP-autentiseringen misslyckas försöker NetX POP3-klienten använda user/pass-autentisering.

## <a name="the-pop3-client-maildrop"></a>The POP3 Client Maildrop

Klient-e-post lagras på en POP3-server i en postlåda eller "maildrop". En client maildrop på en POP3-server representeras som en 1-baserad lista över e-postobjekt. Det innebär att varje e-post refereras till av dess index i maildrop list med det första e-postobjektet vid index 1 (inte noll). POP3-kommandon refererar till specifika e-postobjekt efter deras index i den här listan.

## <a name="the-pop3-protocol-state-machine"></a>POP3-protokolltillståndsdatorn

POP3-protokollet kräver att både klienten och servern upprätthåller tillståndet för POP3-sessionen. Först försöker klienten ansluta till POP3-servern. Om det lyckas går det in i POP3-protokollet som har tre distinkta tillstånd som definieras av RFC 1939. Det ursprungliga tillståndet är auktoriseringstillståndet där det måste identifiera sig för servern. I auktoriseringstillståndet kan POP3-klienten bara utfärda kommandona USER och PASS, och i den ordningen, eller APOP-kommandot.

När POP3-klienten har autentiserats går klientsessionen in i transaktionstillståndet. I det här tillståndet kan klienten ladda ned och begära borttagning av e-post. Kommandona som tillåts i transaktionstillståndet är LIST, STAT, RETR, DELE, RSET och QUIT. Vanligtvis skickar POP3-klienten ett STAT-kommando följt av en serie RETR-kommandon (ett för varje e-postobjekt i sin maildrop).

När klienten utfärdar kommandot QUIT för inleder POP3-sessionen uppdateringstillståndet där TCP-anslutningen initieras från servern. Om du vill ladda ned e-post senare kan POP3-klientprogrammet anropa när `nx_pop3_client_mail_items_get` som helst för att söka efter ny e-post i maildrop.

### <a name="pop3-server-reply-codes"></a>POP3-serverns svarskoder

- **+OK:** Servern använder det här svaret för att acceptera ett klientkommando. Servern kan innehålla ytterligare information efter "+OK" men kan inte anta att klienten kommer att bearbeta den här informationen, förutom vid nedladdning av e-postdata eller LIST- eller DELE-kommandon. I det senare fallet refererar argumentet efter kommandot till indexet för e-postobjektet i Client maildrop.

- **-ERR:** Servern använder det här svaret för att avvisa ett klientkommando. Servern kan skicka ytterligare information efter "-ERR" men kan inte anta att klienten kommer att bearbeta den här informationen.

### <a name="sample-pop3-client---server-session"></a>Exempel på POP3-klient – serversession

**Grundläggande POP3-exempel med USER/PASS:**

```c
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

```c
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

## <a name="rfcs-supported-by-netx-pop3-client"></a>RFC:er som stöds av NetX POP3-klienten

NetX Client POP3 är kompatibel med RFC 1939.
