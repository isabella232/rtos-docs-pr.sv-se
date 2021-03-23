---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX POP3
description: NetX Duo POP3-klientens API är utformat för att tillhandahålla ett e-postöverförings system för små arbets stationer för att få åtkomst till klient post-släpp på POP3-servrar för att hämta klient mail.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4d41da1e1e87e59c5c40674a58b288ac62ec8c78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825848"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX POP3

Post Office Protocol version 3 (POP3) är ett protokoll som har utformats för att tillhandahålla ett e-postöverförings system för små arbets stationer för att få åtkomst till klient post-släpp på POP3-servrar för att hämta klient mail. POP3 använder Transmission Control Protocol (TCP)-tjänster för att utföra e-postöverföring. Därför är POP3 ett mycket tillförlitligt innehålls överförings protokoll.

POP3 tillhandahåller dock inte omfattande åtgärder vid e-posthantering. Vanligt vis hämtas mail av klienten och tas sedan bort från serverns maildrop.

## <a name="netx-duo-pop3-client-requirements"></a>NetX Duo POP3-klient krav

### <a name="client-requirements"></a>Klient krav

NetX POP3 client API kräver en tidigare skapad NetX Duo IP-instans med *nx_ip_create* och en tidigare skapad netx-adresspool med *nx_packet_pool_create*. Eftersom NetX Duo-klienten använder TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* anropet innan du använder netx Duo POP3-klient-API: et på samma IP-instans. POP3-klienten använder en TCP-socket för att ansluta till en POP3-server på serverns POP3-port. Detta anges vanligt vis på den *välkända porten 110, men ingen POP3-klient eller server krävs för att använda den här porten.*

Storleken på den modempool som används för att skapa POP3-klienten är en användare som kan konfigureras i form av paketets nytto last och antalet tillgängliga paket. Om paketet bara används i POP3-klienten för att skapa, behöver paketets nytto last inte vara mer än 100-120 byte beroende på användar namn och lösen ord, eller APOP Digest. ANVÄNDAR kommandot med den lokala värdens användar namn är förmodligen det största meddelande som skickas av POP3-klienten. Det går att dela samma adresspool i nx_ip_create (IP-standardpool) eftersom den interna IP-operatiosn inte kräver mycket stor paket nytto last för att skicka och ta emot TCP-kontroll data.

Men det är inte allmänt fördelaktigt för Ethernet-drivrutinen att använda samma modempool som POP3-klientens adresspool. I allmänhet ställer nytto lasten i nytto lasten för inhämtade paket till IP-instansen MTU (vanligt vis 1500 byte) av nätverks gränssnittet som är mycket större än POP3-klient meddelanden. Inkommande POP3-meddelanden skulle normalt vara mycket större data storlek och utgående POP3-klient meddelanden

## <a name="netx-duo-pop3-client-creation"></a>NetX Duo POP3-klient skapande

Det finns två tjänster för att skapa POP3-klienten. Den rekommenderade tjänsten är *nxd_pop3_client_create* som tar en NXD_ADDRESSs adress data typ som accepterar IPv4-eller IPv6-adresser för POP3-servern. Den andra POP3-klienten Create service, *nx_pop3_client_create* accepterar bara IPv4-adresser för POP3-servern. Båda tjänsterna binder TCP-socket-porten och ansluter till POP3-servern.

När du har anslutit till POP3-servern kan POP3-klient programmet anropa *nx_pop3_client _mail_items_get* för att hämta antalet e-postobjekt i rutan maildrop:

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

Om ett eller flera objekt finns i klientens maildrop kan programmet Hämta storleken på ett särskilt e-postobjekt med hjälp av tjänsten *nx_pop3_client_get_mail_item* :

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

Det första e-postobjektet i maildrop är vid index 1.

För att hämta det faktiska e-postmeddelandet kan programmet anropa *nx_pop3_client_mail_item_get_message_data* -tjänsten för att hämta e-postmeddelande paketen tills tjänsten anger att det sista paketet tas emot final_packet av argumentet indatamängd:

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

Om du vill ta bort ett särskilt e-postobjekt anropar programmet *nx_pop3_client_mail_item_delete* med samma index som används i föregående *nx_pop3_client_get_mail_item* anrop.

Klienten kan tas bort med hjälp av tjänsten *nx_pop3_client_delete* . Observera att det är upp till programmet att ta bort POP3-anslutningspoolen med hjälp av *nx_packet_pool_delete* -tjänsten där den inte längre används.

## <a name="netx-duo-pop3-client-constraints"></a>NetX Duo POP3-klient begränsningar

Det finns vissa begränsningar i NetX Duo POP3-klient implementeringen:

1. NetX Duo POP3-klienten har inte stöd för kommandot AUTH, men den implementerar APOP-autentisering med DIGEST-MD5 för Exchange-autentisering av klientautentisering.
2. NetX Duo POP3-klienten implementerar inte alla POP3-kommandon (t. ex. TOP-eller UIDL-kommandon). Nedan visas en lista med kommandon som stöder:
   - NOOP
   - RSET

## <a name="netx-duo-pop3-client-login"></a>NetX Duo POP3-klient inloggning

En NetX Duo POP3-klient måste autentisera sig själv (inloggning) till en POP3-server för att få åtkomst till en maildrop. Det kan göra detta antingen genom att använda användar-/PASS-kommandon och ange användar namn och lösen ord som är kända för POP3-servern, eller med hjälp av kommandot APOP och MD5 Digest som beskrivs nedan.

Användar namnet är vanligt vis ett fullständigt kvalificerat domän namn (innehåller en lokal del och ett domän namn, avgränsat med ett @-värde). När du använder POP3-kommandona användare och PASS skickar klienten sitt användar namn och lösen ord okrypterat via Internet.

För att undvika säkerhets risken för klartext och lösen ord för text, kan NetX Duo POP3-klienten konfigureras att använda APOP-autentisering genom att ange parametern *APOP_authentication* i *nxd_pop3_client_create* -tjänsten:

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

*Nx_pop3_client_create* tjänsten för endast IPv4-program:

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

När klienten skickar kommandot APOP tar det bara en MD5-Digest som innehåller Server domänen, lokal tid och process-ID som extraheras från serverns hälsning, plus klientens lösen ord. POP3-servern skapar en MD5-Digest som innehåller samma information och om dess MD5-Digest matchar klientens MD5-Digest, autentiseras klienten.

Om APOP-autentiseringen Miss lyckas, kommer NetX Duo POP3-klienten att försöka USER/PASS-autentisering.

## <a name="the-pop3-client-maildrop"></a>POP3-maildrop

Klientens e-post lagras på en POP3-server i en post låda eller "maildrop". En klient-maildrop på en POP3-server representeras som en 1-baserad lista över e-postobjekt. Det vill säga att varje post refereras till av sitt index i maildrop-listan med det första e-postobjektet vid index 1 (inte noll). POP3-kommandon refererar till vissa e-postobjekt baserat på deras index i den här listan.

## <a name="the-pop3-protocol-state-machine"></a>Tillstånds datorn för POP3-protokollet

POP3-protokollet kräver att både klienten och servern behåller status för POP3-sessionen. Först försöker klienten ansluta till POP3-servern. Om det lyckas går det in i POP3-protokollet som har tre distinkta tillstånd definierade av RFC 1939. Start tillståndet är det tillstånd där det måste identifiera sig för servern. I tillståndet Authorization kan POP3-klienten endast utfärda användare och PASS-kommandon, i den ordningen eller kommandot APOP.

När POP3-klienten har autentiserats, anger klientens session transaktions statusen. I det här läget kan klienten Ladda ned och begära borttagning av e-post. De kommandon som tillåts i transaktions tillstånd är LIST, STAT, RETR, &, RSET och avsluta. Normalt skickar POP3-klienten ett STAT-kommando följt av en serie med RETR-kommandon (en för varje e-postobjekt i dess maildrop).

När klienten utfärdar kommandot QUIT, anger POP3-sessionen det uppdaterings tillstånd där den initierar TCP-från koppling från servern. För att hämta e-post vid en annan tidpunkt kan POP3-klient programmet anropa nx_pop3_client_mail_items_get för att söka efter ny e-post i maildrop.

### <a name="pop3-server-reply-codes"></a>Svars koder för POP3-server

- + OK servern använder det här svaret för att acceptera ett klient kommando. Servern kan innehålla ytterligare information efter "+ OK" men det går inte att anta att klienten bearbetar informationen, förutom vid hämtning av e-postmeddelande data eller LIST-eller &-kommandon. I det senare fallet refererar argumentet efter kommandot till indexet för e-postobjektet i-klientens maildrop.
- -FEL servern använder det här svaret för att avvisa ett klient kommando. Servern kan skicka ytterligare information efter "-ERR", men kan inte förutsätta att klienten bearbetar den här informationen.

### <a name="sample-pop3-client---server-session"></a>Exempel på POP3-klient-server-session

**Grundläggande POP3-exempel som använder USER/PASS:**

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

**Grundläggande POP3-exempel med APOP (och lista i stället för STAT):**

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

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a>RFC: er som stöds av NetX Duo POP3-klienten

NetX Duo-klienten POP3 är kompatibel med RFC 1939.
