---
title: Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX Secure DTLS
description: Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX Secure DTLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 347bd83fa8c72ced2e8678a92ec5c5f8393c136d
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550209"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>Kapitel 3: funktionell beskrivning av Azure återställnings tider NetX Secure DTLS

## <a name="execution-overview"></a>Översikt över körning

Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX Secure DTLS. Det finns två primära typer av program körning i ett NetX Secure DTLS-program: initierings-och program gränssnitts anrop. 

NetX Secure förutsätter att ThreadX och NetX/NetXDuo finns. Från ThreadX kräver det tråd körning, avstängning, periodiska timers och ömsesidiga undantags funktioner. Från NetX/NetXDuo krävs det funktioner och driv rutiner för UDP och IP-nätverk.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>Datagram Transport Layer Security (DTLS) och Transport Layer Security (TLS)

NetX Secure DTLS implementerar Datagram Transport Layer Security protokoll version 1,2 som definieras i RFC 6347. DTLS version 1,0 har definierats i RFC 4347 och motsvarar TLS-version 1,1. På grund av att DTLS är i princip ett tillägg till TLS, bestämde vi att nästa version skulle använda samma versions nummer som motsvarande TLS-version. Det finns därför ingen DTLS version 1,1 eftersom DTLS version 1,2 motsvarar TLS-version 1,2.

> [!NOTE]
> NetX Secure stöder DTLS version 1,2. DTLS 1,0 (RFC 4347) stöds **inte** för närvarande.

*Secure Sockets Layer* (SSL) var det ursprungliga namnet på TLS innan det blev standard i RFC 2246 och "SSL" används ofta som ett generiskt namn för TLS-protokollen. Den senaste versionen av SSL var 3,0 och TLS 1,0 kallas ibland SSL version 3,1. Alla versioner av det officiella "SSL"-protokollet betraktas som föråldrade och oskyddade och för närvarande NetX Secure ger inte SSL-implementering.

TLS anger ett protokoll för att generera *sessionsnycklar* som skapas under TLS- *handskakningen* mellan en TLS-klient och-server och dessa nycklar används för att kryptera data som skickas av programmet under TLS- *sessionen.*

DTLS är nära kopplad till TLS, eftersom de underliggande säkerhets mechansims delas mellan protokollen. TLS är dock utformat för att fungera över ett transport lager protokoll som ger garantier om paket leverans och ordning (nästan alltid TCP i praktiken) och kommer inte att fungera över ett opålitligt protokoll som UDP. Det är precis på grund av UDP som DTLS introducerades: DTLS har utformats för att hantera den otillförlitliga typen av UDP och liknande protokoll. Detta sker genom att du inkluderar ordnings-och Tillförlitlighets logik (t. ex. återöverföring av ignorerade data) liknande de pålitliga protokoll som TCP.

En fullständig beskrivning av TLS ingår i kapitel 3 i NetX Secure TLS User ' s guide, så det här dokumentet fokuserar på skillnaderna mellan TLS och DTLS.

### <a name="dtls-record-header"></a>DTLS post rubrik

Alla giltiga DTLS-poster måste ha ett DTLS-huvud, som visas i bild 1. Huvudet är detsamma som TLS med att lägga till två nya fält: 16-bitars *epok* och 48-bitars *ordnings nummer*, som beskrivs nedan.

![Diagram över en DTLS post-rubrik.](media/image2.png)

**Figur 1 – post rubriken DTLS**

Fälten i TLS-postrubriken definieras enligt följande:

| Fält för TLS-huvud | Syfte  |
| ---------------- | --------- |
| **8-bitars meddelande typ** | Det här fältet innehåller den typ av DTLS-post som skickas. Giltiga typer är följande:<br />- ChangeCipherSpec: 0x14<br />-Avisering: 0x15<br />-Hand skakning: 0x16<br />– Program data: 0x17<br /> |
| **16-bitars protokoll version** | Det här fältet innehåller DTLS-protokollets version. Giltiga värden är följande:<br />-DTLS 1,1:0xFEFD |
|  **16-bitars epok** |  Det här fältet innehåller DTLS "epok" som är en räknare som ökas varje gång krypterings statusen ändras (t. ex. när nya sessionsnycklar genereras).  |
|  **48-bitars sekvensnummer** |  Det här fältet innehåller ett sekvensnummer som identifierar den här posten. Den används av DTLS för att underhålla post beställningar och kontrol lera återöverförings behov. |
|  **16-bitars längd** |  Det här fältet innehåller längden på de data som kapslats i DTLS-posten.  |

### <a name="dtls-handshake-record-header"></a>Post rubrik för DTLS-handskakning

Alla giltiga DTLS-handskaknings poster måste ha ett DTLS-huvud, som visas i bild 2.

![Diagram över ett DTLS-handskaknings post huvud.](media/image3.png)

**Bild 2 – post rubriken för DTLS-handskakningen**

Fälten i post huvudet för DTLS-handskakning definieras enligt följande:

| Fält för TLS-huvud | Syfte  |
| ---------------- | ------------------------------------------------ |
| **8-bitars meddelande typ** | Det här fältet innehåller den typ av DTLS-post som skickas. Giltiga typer är följande:<br />- ChangeCipherSpec: 0x14<br />-Avisering: 0x15<br />-Hand skakning: 0x16<br />– Program data: 0x17 |
|  **16-bitars epok** | Det här fältet innehåller DTLS "epok" som är en räknare som ökas varje gång krypterings statusen ändras (t. ex. när nya sessionsnycklar genereras). |
|  **48-bitars sekvensnummer** | Det här fältet innehåller ett sekvensnummer som identifierar den här posten. Den används av DTLS för att underhålla post beställningar och kontrol lera återöverförings behov. |
|  **16-bitars protokoll version** | Det här fältet innehåller DTLS-protokollets version. Giltiga värden är följande:<br />-DTLS 1,1:0xFEFD |
| **16-bitars längd** | Det här fältet innehåller längden på de data som kapslats i DTLS-posten. |
| **8-bitars hand Skaknings typ** | Det här fältet innehåller meddelande typen hand skakning. Giltiga värden är följande:<br />-HelloRequest: 0x00<br />-Sitt hälsnings: 0x01<br />-ServerHello: protokollnumret 0x02<br />-Certifikat: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />-ClientKeyExchange: 0x10<br />-Färdig: 0x14 |
| **24-bitars längd** | Det här fältet innehåller längden på hand skaknings meddelande data. |
| **16-bitars sekvensnummer** | Det här fältet innehåller ett sekvensnummer. |

### <a name="the-dtls-handshake-and-dtls-session"></a>DTLS-handskakning och DTLS-sessionen

En typisk DTLS-handskakning visas i bild 3. Den är nästan identisk med den typiska TLS-handskakningen med en viktig skillnad – när sitt hälsnings-meddelandet först skickas svarar servern med ett nytt DTLS meddelande *HelloVerifyRequest* som innehåller en "cookie". DTLS-klienten måste svara med ett andra sitt hälsnings-meddelande som innehåller den cookien innan hand skakningen kan fortsätta. Den här mekanismen har lagts till i DTLS för att förhindra vissa DoS-attacker (Denial of Service) eftersom UDP är ett protokoll för anslutnings fel (TCP kräver en dedikerad anslutning/port så att TLS inte drabbas av samma problem).

En DTLS-handskakning börjar när klienten skickar ett *sitt hälsnings* -meddelande till en DTLS-Server, vilket indikerar att de vill starta en DTLS-session. Meddelandet innehåller information om den kryptering som klienten vill använda för sessionen, tillsammans med information som används för att generera sessionsnycklar senare i hand skakningen. Alla meddelanden i DTLS-handskakningen krypteras inte förrän sessionsnycklarna har skapats. Som nämnts ovan kan DTLS-servern skicka en HelloVerifyRequest som svar på sitt hälsnings, vilket tvingar klienten att svara med en andra uppdaterad sitt hälsnings.

Vid mottagandet av det andra sitt hälsnings verifierar DTLS-servern cookien och om korrekt svarar med ett ServerHello-meddelande som anger ett val från de krypterings alternativ som anges av klienten. ServerHello följs av ett certifikat meddelande där servern tillhandahåller ett digitalt certifikat för att autentisera sin identitet för klienten (om X. 509-verifiering används). Slutligen skickar servern ett ServerHelloDone-meddelande som anger att det inte finns några fler meddelanden att skicka. Servern kan eventuellt skicka andra meddelanden efter ServerHello och i vissa fall kan det inte skicka ett certifikat meddelande (till exempel när i förväg delade nycklar används), och därför måste ServerHelloDone-meddelandet.

När klienten har tagit emot alla serverns meddelanden har den tillräckligt med information för att generera sessionsnycklar. TLS/DTLS gör detta genom att skapa en delad bit av slumpmässiga data som kallas för *huvud hemlighet*, som är en fast storlek och som används som ett Seed för att generera alla nycklar som behövs när kryptering har Aktiver ATS. Hemligheten för huvud repliken krypteras med algoritmen för offentlig nyckel (t. ex. RSA) som anges i Hello-meddelandena (se nedan för information om algoritmer för offentliga nycklar) och den offentliga nyckel som tillhandahålls av servern i dess certifikat. En valfri TLS/DTLS-funktion som kallas PSK (i förväg delade nycklar) aktiverar krypteringssviter som inte använder ett certifikat utan använder i stället ett hemligt värde som delas mellan värdarna (vanligt vis via fysisk överföring eller annan säker metod). När PSK är aktiverat används den i förväg delade hemliga nyckeln för att generera den hemliga hemligheten. Se avsnittet om i förväg delade nycklar i "autentiseringsmetoder" nedan.

I en vanlig TLS/DTLS-handskakning skickas den krypterade huvud hemligheten till-servern i ClientKeyExchange-meddelandet. Servern, vid mottagning av ClientKeyExchange-meddelandet, dekrypterar hemligheten för huvud repliken med dess privata nyckel och fortsätter att generera sessionsnycklar parallellt med TLS/DTLS-klienten.

När sessionsnycklarna har genererats kan alla ytterligare meddelanden krypteras med hjälp av algoritmen för privat nyckel (t. ex. AES) som valts i Hello-meddelandena. Ett slutligt okrypterat meddelande som kallas ChangeCipherSpec skickas av både klienten och servern för att indikera att alla ytterligare meddelanden kommer att krypteras.

Det första krypterade meddelandet som skickas av både klienten och servern är också det sista TLS-handskaknings meddelandet, som kallas slutfört. Det här meddelandet innehåller en hash av alla handskaknings meddelanden som har tagits emot och skickats. Denna hash används för att kontrol lera att inget av meddelandena i hand skakningen har manipulerats eller skadats (vilket innebär att säkerheten kan brytas).

När de färdiga meddelandena tas emot och hand skaknings-hasharna verifieras, börjar TLS/DTLS-sessionen och programmet börjar skicka och ta emot data. Alla data som skickas på endera sidan under TLS/DTLS-sessionen hashas först med den hash-algoritm som valts i Hello-meddelandena (för att tillhandahålla meddelande integritet) och krypteras med den valda algoritmen för privat nyckel med de genererade sessionsnycklarna.

Slutligen kan en TLS/DTLS-session endast avslutas om antingen klienten eller servern väljer att göra det. En trunkerad session betraktas som en säkerhets överträdelse (eftersom en angripare kan försöka förhindra att alla data som skickas tas emot) så att ett särskilt meddelande skickas när någon sida vill avsluta sessionen, som kallas en CloseNotify-avisering. Både klienten och servern måste skicka och bearbeta en CloseNotify-avisering för att en lyckad session ska kunna stängas.

![Diagram över en typisk DTLS-handskaknings session.](media/image4.png)

**Bild 3 – typisk DTLS-handskakning**

### <a name="initialization"></a>Initiering

NetX-eller NetXDuo-stacken måste initieras innan du använder NetX Secure DTLS. I användar handboken för NetX eller NetXDuo hittar du information om hur du korrekt initierar TCP/IP-stacken för UDP-åtgärder.

När NetX-UDP har initierats kan DTLS aktive ras. Internt hanteras all DTLS nätverks trafik och bearbetning av NetX/NetXDuo-stacken utan att användaren behöver göra något. DTLS har dock vissa särskilda krav som måste hanteras separat från den underliggande nätverks stacken. DTLS klient åtgärd dessa parametrar tilldelas till DTLS-kontroll blocket som kallas ***NX_SECURE_DTLS_SESSION** _. För DTLS-server åtgärd kallas kontroll block _ *_NX_SECURE_DTLS_SERVER_** och innehåller den infrastruktur som krävs för att hantera flera DTLS-sessioner på en enskild UDP-port – Observera att detta skiljer sig från TLS där varje TLS-session är kopplad till en enda TCP-port.

De två DTLS lägena, server och klient, kan aktive ras i ett program (men bara ett läge per NetX-socket) och varje har sina egna specifika krav, som beskrivs nedan.

### <a name="initialization--dtls-server"></a>Initiering – DTLS-Server

NetX Secure DTLS Server mode skiljer sig från TLS server mode på grund av användningen av UDP för det underliggande protokollet för nätverks transport. Med TCP är porten kopplad till en enda fjärrvärd under TLS-sessionens varaktighet. UDP har ingen teoretiskt tillstånd med avseende på Fjärrvärdet, så DTLS-begäranden från olika värdar kommer att tas emot i samma UDP-gränssnitt. Därför måste DTLS underhålla sessionstillstånd i stället för att förlita dig på socketen som TLS och TCP. Av den anledningen har DTLS Server Control Block (NX_SECURE_DTLS_SERVER) en mappning av fjär värd information (IP-adress och port) till DTLS-sessioner. Alla inkommande data på UDP-socketen som tilldelats en DTLS-Server mappas till en befintlig eller ny DTLS-session baserat på fjärrvärden. Därför kräver skapandet av DTLS-servern flera ytterligare parametrar utöver vad TLS-och DTLS-klienten behöver.

Förutom DTLS Server Control Block, TLS-krypteringssviter och chiffrering ScratchSpace/metadata kräver DTLS-servrar en buffert för att underhålla DTLS-sessioner och en paket omassembly-buffert som används för att dekryptera inkommande DTLS-poster.

Förutom session-buffertarna kräver DTLS-servrar ett *digitalt certifikat*, vilket är ett dokument som används för att identifiera TLS-servern för den anslutande TLS-klienten och certifikat motsvarande *privata nyckel*, vanligt vis för RSA-krypteringsalgoritmen. International tele Union X. 509 standard anger det certifikat format som används av TLS/DTLS och det finns flera olika verktyg för att skapa X. 509-digitala certifikat.

För NetX Secure DTLS måste X. 509-certifikatet vara Binary-kodat med Distinguished Encoding Rules (DER)-formatet för ASN. 1. DER är standard TLS-formatet för TLS-överföring för certifikat.

Den privata nyckeln som är associerad med det tillhandahållna certifikatet måste vara i DER-Encoded PKCS # 1-format. Den privata nyckeln används bara på enheten och skickas aldrig över kabeln. Håll privata nycklar säkra eftersom de ger säkerhet för TLS/DTLS-kommunikation!

För att initiera DTLS-servercertifikatet måste programmet tillhandahålla en pekare till en buffert som innehåller det DER-kodade X. 509-certifikatet och en DER-kodad PKCS # 1 RSA-Datadata med hjälp av tjänsten ***nx_secure_x509_certificate_intialize*** , som fyller **NX_SECURE_X509_CERT** -strukturen med lämpliga certifikat data som ska användas av TLS.

När Server certifikatet har initierats måste det läggas till i TLS-kontroll-blocket med hjälp av tjänsten ***nx_secure_dtls_server_local_certificate_add*** .

När serverns certifikat har lagts till i DTLS Server Control Block kan servern användas för säker DTLS-kommunikation (se exemplet ovan).

### <a name="initialization--dtls-client"></a>Initiering – DTLS-klient

NetX Secure DTLS client mode är enkelt i drift jämfört med DTLS-servern eftersom det bara finns en enda utgående anslutning till fjärrvärden över UDP-socketen.

För att kunna konfigurera en DTLS-klient kräver det ett *betrott certifikat Arkiv*, som är en samling X. 509 digitala certifikat från betrodda certifikat utfärdare (ca: er). Dessa certifikat antas av att DTLS-protokollet är "betrott" och fungerar som underlag för att autentisera certifikat som tillhandahålls av DTLS-Server enheter till NetX säkra DTLS-klient programmet.

Ett certifikat för betrodd certifikat utfärdare kan antingen vara *självsignerat* eller signerat av en annan certifikat utfärdare, vilket innebär att certifikatet kallas *mellanliggande ca* (ICA). I ett typiskt TLS/DTLS-program tillhandahåller servern ICA-certifikat tillsammans med dess server certifikat, men det enda kravet för lyckad autentisering är att en kedja av utfärdare (certifikat som används för att signera andra certifikat) kan spåras från Server certifikatet tillbaka till ett certifikat för betrodd certifikat utfärdare i det betrodda certifikat arkivet. Den här kedjan kallas en *kedja av förtroende* eller en *certifikat kedja*.

För att initiera en betrodd certifikat utfärdare eller ett ICA-certifikat måste programmet tillhandahålla en pekare till en buffert som innehåller det DER-kodade X. 509-certifikatet med hjälp av tjänsten ***nx_secure_x509_certificate_intialize** _, som fyller i strukturen _ *NX_SECURE_X509_CERT** med lämpliga certifikat data som ska användas av TLS.

DTLS-klienten behöver också utrymme för att det inkommande server certifikatet ska tilldelas (förutsatt att ett i förväg delad nyckel läge inte används) och en buffert för montering av paket i DTLS-poster som ska dekrypteras. Dessa buffertar skickas in som parametrar till tjänsten ***nx_secure_dtls_session_create*** (mer information finns i API-referensen).

Betrodda certifikat som har initierats läggs sedan till i det skapade DTLS session Control-blocket med hjälp av tjänsten ***nx_secure_dtls_session_trusted_certificate_add*** . Om du inte lägger till ett certifikat Miss lyckas DTLS-klientsessionen eftersom det inte finns något sätt för DTLS-protokollet att autentisera fjärrserver-värdar.

När det betrodda certifikat arkivet har skapats kan sessionen användas för att upprätta en säker TLS-klient anslutning.

### <a name="application-interface-calls"></a>Program gränssnitts anrop

NetX säkra DTLS-program gör vanligt vis att funktions anrop inifrån program trådar som körs under ThreadX-återställnings tider. Vissa initieringar, särskilt för underliggande nätverks protokoll för nätverks kommunikation (t. ex. UDP och IP), kan anropas från ***tx_application_define *.** Mer information om hur du initierar nätverkskommunikation finns i användar handboken för NetX/NetXDuo.

DTLS gör den stora användningen av krypterings rutiner som är processor intensiva åtgärder. De här åtgärderna utförs vanligt vis inom ramen för anrop av tråd.

### <a name="dtls-session-start"></a>DTLS-session startades

DTLS kräver ett underliggande nätverks protokoll för transport skikt för att fungera. Protokollet används vanligt vis för TCP. För att kunna upprätta en NetX säker TLS-session måste en **NX_UDP_SOCKET** skapas och skickas till **_nx_secure_dtls_client_session_start_** -tjänsten för DTLS-klienter.

DTLS-servrar fungerar annorlunda. UDP-socketen som används för inkommande DTLS-klient begär Anden finns i NX_SECURE_DTLS_SERVER kontroll block och initieras i anropet till ***nx_secure_dtls_server_create** _, som tar den lokala UDP-porten som en parameter. Tjänsten _*_nx_secure_dtls_server_start_*_ används sedan för att starta DTLS-servern för att hantera inkommande begär Anden. Alla inkommande begär Anden hanteras i callback-rutiner som ges till _nx_secure_dtls_server_create *: en för anslutningar och en för att ta emot meddelanden. Det är upp till programmet för att hantera start av DTLS-sessionen när ett anslutnings meddelande tas emot (anslutnings anropet för att meddela om att det anropas av DTLS) genom att anropa ***nx_secure_dtls_server_session_start**_. Programmet måste också hantera inkommande data när motringningen ta emot meddelande anropas (som följer en slutförd DTLS-handskakning) genom att anropa _ *_nx_secure_dtls_session_receive_* *. Informationen om detta finns i exemplet ovan och i API-referensen för var och en av de ovan nämnda tjänsterna.

### <a name="dtls-packet-allocation"></a>DTLS paket tilldelning

NetX Secure DTLS använder samma paket struktur som NetX/NetXDuo TCP (***NX_PACKET** _), förutom att i stället för att anropa tjänsten _*_nx_packet_allocate_*_ måste tjänsten _ *_nx_secure_dtls_packet_allocate_** anropas så att utrymmet för DTLS-huvudet kan allokeras korrekt.

### <a name="dtls-session-send"></a>Skicka DTLS-session

När TLS-sessionen har startats kan programmet skicka data med hjälp av tjänsten ***nx_secure_dtls_session_send*** . Sändnings tjänsten är identisk med ***nx_udp_socket_send** _-tjänsten, med en _ *_NX_PACKET_** data struktur som innehåller de data som skickas, en mål-IP-adress och en UDP-målport.

> [!IMPORTANT]
> När du skickar data med hjälp av nx_secure_dtls_session_send, är det viktigt att använda samma IP-adress och port som användes för att upprätta DTLS-sessionen, om det inte finns någon mekanism för att flytta sessionen till en ny adress och UDP-port på plats (detta är inte vanligt).

Alla data som skickas över DTLS krypteras av NX Secure DTLS-stacken och de konfigurerade krypterings rutinerna innan de skickas.

### <a name="dtls-session-receive"></a>Ta emot DTLS-session

När DTLS-sessionen har startats kan programmet ta emot data med hjälp av tjänsten ***nx_secure_Dtls_session_receive** _. Precis som DTLS-sessionen skickar, är den här tjänsten identisk med _ *_nx_udp_socket_receive_* *, förutom att inkommande data dekrypteras och verifieras av DTLS-stacken innan de returneras i paket strukturen.

### <a name="tls-session-close"></a>Sessionen stängs av TLS

När en DTLS-session har slutförts måste både DTLS-klienten och servern skicka en CloseNotify-avisering till den andra sidan för att stänga av sessionen. Båda sidorna måste ta emot och bearbeta aviseringen för att säkerställa att en lyckad session stängs av.

Om fjärrvärden skickar en CloseNotify avisering, bearbetar alla anrop till ***nx_secure_dtls_session_receive** _-tjänsten aviseringen, skickar motsvarande avisering tillbaka till fjärrvärden och returnerar värdet _ *_NX_SECURE_TLS_SESSION_CLOSED_* *. När sessionen har stängts Miss lyckas ytterligare försök att skicka eller ta emot data med den DTLS sessionen.

Om programmet vill stänga TLS-sessionen måste tjänsten ***nx_secure_dtls_session_end** _ anropas. Tjänsten kommer att skicka CloseNotify-aviseringen och bearbeta svars CloseNotify. Om svaret inte tas emot returneras ett felvärde på _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, vilket tyder på att DTLS-sessionen inte stängdes på rätt sätt, vilket möjliggör en säkerhets överträdelse.

### <a name="tlsdtls-alerts"></a>TLS/DTLS-aviseringar

TLS/DTLS har utformats för att ge maximal säkerhet, så alla Errant beteenden i protokollet betraktas som en potentiell säkerhets överträdelse. Av den anledningen betraktas eventuella fel vid meddelande bearbetning eller kryptering/dekryptering av allvarliga fel som avslutar hand skakningen eller sessionen omedelbart.

Vid hantering av fel i ett lokalt program är det relativt enkelt att ta reda på att ett fel har inträffat för att hantera situationen på ett korrekt sätt och förhindra ytterligare eventuella säkerhets överträdelser. Av den anledningen skickar TLS/DTLS ett *varnings* meddelande till fjärrvärden vid eventuella fel.

Aviseringar behandlas på samma sätt som andra TLS/DTLS-meddelanden och krypteras under sessionen för att förhindra att en angripare samlar in information från den typ av avisering som tillhandahålls. Under hand skakningen är de skickade aviseringarna begränsade inom räckvidden för att begränsa den mängd information som kan erhållas av en potentiell angripare.

CloseNotify-aviseringen som används för att stänga TLS/DTLS-sessionen är den enda icke-allvarliga varningen. Även om det anses vara en avisering och skickas som ett varnings meddelande, är en CloseNotify till skillnad från andra aviseringar i att det inte indikerar att ett fel har uppstått.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>TLS/DTLS för att återförhandla och återupptas

TLS stöder begreppet "omförhandling" som bara är en omförhandling av TLS-sessionens parametrar inom kontexten för en befintlig TLS-session.

Återupptagning av TLS- *sessioner bör inte* förväxlas med *omförhandling* av sessionen, trots vissa likheter. Om omstarten av *sessionen innebär att* starta en ny hand skakning inom en befintlig TLS *-session* är sessionen återupptagning en helt valfri funktion som inbegriper omstart av en stängd TLS-session utan att utföra en fullständig TLS-handskakning.

NX Secure DTLS hanterar inkommande begär Anden om omförhandling från fjärranslutna värdar. Den har **inte** stöd för att återuppta sessionen. En mer fullständig beskrivning av de här funktionerna finns i kapitel 3 i användar handboken för Secure TLS-NetX.

### <a name="protocol-layering"></a>Protokoll skikt

TLS-protokollet (och därmed även DTLS) passar i nätverks stacken mellan transport lagret (t. ex. TCP eller UDP) och program skiktet. TLS anses ibland vara ett transport skikt protokoll (därmed *Transport Layer* Security), men eftersom det fungerar som ett program med avseende på de underliggande nätverks protokollen, grupperas ibland i program lagret.

TLS kräver ett transport lager protokoll som stöder in-och förlustfri överföring, till exempel TCP. På grund av detta krav kan TLS inte köras ovanpå UDP eftersom UDP inte garanterar leverans av datagram. *DTLS* är en modifierad version av TLS, används för program som behöver TLS-TLS över ett datagram-protokoll som UDP.

![Diagram över TLS-protokoll skiktning.](media/image6.png)

**Bild 4 – TCP/IP, UDP och TLS/DTLS protokoll lager**

## <a name="network-communications-security-and-encryption"></a>Säkerhet och kryptering för nätverks kommunikation

Att skydda kommunikation över offentliga nätverk och Internet är ett kritiskt viktigt ämne och ämnet för ett stort antal böcker, artiklar och lösningar. Avsnittet är en bogglingly komplex, men det kan minskas till en enkel idé: att skicka information via ett nätverk så att endast det avsedda målet kan komma åt eller ändra informationen. Detta bryts ned i tre viktiga begrepp: sekretess, integritet och autentisering. TLS/DTLS-protokollet tillhandahåller lösningar för alla tre.

Kryptering används på olika sätt för att tillhandahålla sekretess, integritet och autentisering inom TLS-och DTLS-protokollen. Krypteringen måste anges till TLS eller DTLS när en session eller Server instans skapas som TLS, vilket ger ett flexibelt ramverk för att använda kryptering och inte själva krypteringen. NetX Secure DTLS innehåller de nödvändiga krypterings rutinerna för de flesta program, så du behöver inte bekymra dig om att hitta lämplig kryptering.

En mer detaljerad beskrivning av de här ämnena finns i kapitel 3 i användar handboken för Secure TLS-NetX.

## <a name="tls-and-dtls-extensions"></a>TLS-och DTLS-tillägg

TLS (och därför DTLS) innehåller ett antal tillägg som ger ytterligare funktioner för vissa program. Dessa tillägg skickas vanligt vis som en del av sitt hälsnings-eller ServerHello-meddelandena, vilket indikerar att en fjärrvärd vill använda ett tillägg eller tillhandahålla ytterligare information som används för att upprätta en säker TLS-session.

NetX Secure DTLS stöder alla tillägg som finns i NetX Secure TLS, och en fullständig beskrivning av dem finns i NetX Secure TLS user guide, kapitel 3.

## <a name="authentication-methods"></a>Autentiseringsmetoder

TLS och DTLS ger ramverket för att upprätta en säker anslutning mellan två enheter över ett oskyddat nätverk, men en del av problemet är att känna till identiteten för enheten i den andra änden av anslutningen. Utan en mekanism för att autentisera identiteten för fjärranslutna värdar blir det en trivial åtgärd för en angripare att utgöra en betrodd enhet.

Inlednings vis kan det verka som att använda IP-adresser, MAC-adresser för maskin vara eller DNS ger en relativt hög exakthet för att identifiera värdar i ett nätverk, men med tanke på vilken typ av TCP/IP-teknik som kan vara falska och vilka adresser som kan vara falska och DNS-poster skadas (t. ex. genom DNS-cachelagring av data), är det klart att TLS behöver ett extra skydd mot bedrägliga identiteter.

Det finns olika mekanismer som kan ge detta extra lager av autentisering för TLS, men det vanligaste är det *digitala certifikatet.* Andra mekanismer är i förväg delade nycklar (PSK) och lösen ords scheman.

### <a name="digital-cerificates"></a>Digital certifikat

Digitala certifikat är den vanligaste metoden för att autentisera en fjärran sluten värd i TLS. I stort sett är ett digitalt certifikat ett dokument med en speciell formatering som ger identitets information för en enhet i ett dator nätverk.

TLS använder normalt ett format som kallas X. 509, en standard som utvecklats av International Telecommunication union, även om andra certifikat utfärdare kan användas om TLS-värdarna kan komma överens om det format som används. X. 509 definierar ett särskilt format för certifikat och olika kodningar som kan användas för att skapa ett digitalt dokument. De flesta X. 509-certifikat som används med TLS kodas med hjälp av en variant av ASN. 1, en annan telekommunikations standard. I ASN. 1 finns olika digitala kodningar, men den vanligaste kodningen för TLS-certifikat är Distinguished Encoding Rules (DER) standard. DER är en förenklad del av de grundläggande kodnings reglerna för ASN. 1 (BER) som är utformade för att vara entydiga, vilket gör det enklare att parsa. TLS-certifikat kodas vanligt vis i binärt DER, och detta är det format som NetX säkrar för X. 509-certifikat.

Även om DER-formaterade binära certifikat används i det faktiska TLS-protokollet kan de skapas och lagras i ett antal olika kodningar, med fil namns tillägg som. PEM,. CRT och. p12. Olika varianter används av olika program från olika tillverkare, men alla kan ofta konverteras till DER med hjälp av mycket tillgängliga verktyg.

De vanligaste av de alternativa certifikat kodningarna är PEM. PEM-formatet (från Privacy-Enhanced mail) är en Base-64-kodad version av DER-kodningen som ofta används eftersom kodningen resulterar i utskrivbar text som enkelt kan skickas via e-post eller webbaserade protokoll.

Att skapa ett certifikat för ditt NetX-säkra program ligger vanligt vis utanför omfånget för den här hand boken, men kommando rads verktyget OpenSSL ([www.openssl.org](http://www.openssl.org)) är mycket tillgängligt och kan konverteras mellan de flesta format.

Beroende på ditt program kan du skapa egna certifikat, tillhandahålla certifikat av en tillverkare eller myndighets organisation eller köpa certifikat från en kommersiell certifikat utfärdare.

Om du vill använda ett digitalt certifikat i NetX-skyddat program måste du först konvertera certifikatet till ett binärformat och eventuellt konvertera den tillhör ande privata nyckeln ("privat exponent" för RSA, till exempel) till ett binärformat, vanligt vis en PKCS # 1-formaterad, DER-kodad RSA-nyckel. När konverteringen är klar är det upp till dig att läsa in certifikatet och den privata nyckeln på enheten. Möjliga alternativ är att använda ett Flash-baserat fil system eller skapa en C-matris från data (med ett verktyg som "XXD" från Linux) och kompilera certifikatet och nyckeln till ditt program som konstant data.

När ditt certifikat har lästs in på enheten kan DTLS-API: et användas för att koppla certifikatet till en DTLS-session eller-server.

Mer information och exempel på hur du använder X. 509-certifikat med NetX Secure DTLS finns i avsnittet "Importera X. 509-certifikat till NetX Secure" i användar handboken för NetX Secure TLS.

Mer information hittar du i följande DTLS-tjänster i API-referensen:

- nx_secure_x509_certificate_initialize,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Certifikats information för TLS-klient

DTLS-klientens implementeringar kräver vanligt vis inte att ett lokalt certifikat ska läsas in på enheten. Ett lokalt certifikat är ett certifikat som identifierar den lokala enheten. Mer specifikt ger ett lokalt certifikat identitets information för den enhet som TLS/DTLS-programmet har lästs in på. Undantaget till detta är när autentisering av klient certifikat är aktiverat, men detta är mindre vanligt.

En DTLS-klient kräver att minst ett betrott certifikat läses in (mer kan läsas in om det behövs) och att ett fjärrcertifikat ska tilldelas. Ett betrott certifikat är ett certifikat som tillhandahåller en grund för förtroende och autentisering av fjär renheten, antingen direkt eller via en PKI (Public Key Infrastructure). Roten i förtroende kedjan kallas vanligt vis för en certifikat utfärdare eller CA-certifikat. Ett fjärrcertifikat syftar på det certifikat som skickas av fjärrvärden under TLS-handskakningen. Den ger identitet för den fjärranslutna värden och autentiseras genom att jämföra den med ett betrott certifikat på den lokala enheten.

Mer information om hur du lägger till betrodda certifikat och hur du allokerar utrymme för fjärrcertifikat finns i TLS API-referensen för följande tjänster: nx_secure_dtls_session_create nx_secure_dtls_session_trusted_certificate_add.

### <a name="tlsdtls-server-certificate-specifics"></a>TLS/DTLS Server-certifikat information

DTLS Server-implementeringar kräver vanligt vis inte "betrodda" certifikat att läsas in på enheten eller fjärrcertifikaten som ska allokeras. Det här undantaget är när autentisering av klient certifikat är aktiverat.

En TLS-server kräver att ett "lokalt" certifikat (eller "identitets certifikat)" läses in så att servern kan ge den till fjärrklienten under TLS-handskakningen för att autentisera servern för klienten.

Mer information om hur du läser in lokala certifikat för användning med NetX TLS server-program finns i API-referensen för följande tjänster: nx_secure_dtls_server_local_certificate_add nx_secure_dtls_server_local_certificate_remove.


### <a name="pre-shared-keys-psk"></a>I förväg delade nycklar (PSK)

En alternativ mekanism för att tillhandahålla identifierings autentisering i TLS är begreppet i förväg delade nycklar (PSK). Om du använder en PSK-ciphersuite elimineras behovet av att utföra processor intensiva krypterings åtgärder för offentliga nycklar, en Boon för resurs begränsade inbäddade enheter. PSK ersätter certifikatet i TLS/DTLS-handskakningen och används i stället för den krypterade huvud repliken för generering av TLS/DTLS-sessionsnycklar.

PSK-krypteringssviter är begränsade i den mening att en delad hemlighet måste finnas på båda enheterna innan en TLS/DTLS-session kan upprättas. Det innebär att enheterna måste ha lästs in med den hemligheten med hjälp av ett säkert sätt än en TLS PSK-anslutning – PSKs kan uppdateras via en TLS PSK-anslutning, men enheten måste nödvändigt vis börja med en PSK som läses in via någon annan mekanism. Till exempel kan en sensor enhet och dess gateway-enhet läsas in med PSKs i fabriken innan det levereras, eller en standard-TLS-anslutning (med ett certifikat) kan användas för att läsa in PSK.

PSK-krypteringssviter levereras i ett par formulär som beskrivs i RFC 4279. Först används RSA-eller Diffie-Hellman nycklar som används på samma sätt som de offentliga nycklar som skickas i certifikatet i standard-TLS-handskakning. Det andra formuläret, som används i en resurs begränsad miljö, använder en PSK som används för att direkt generera sessionsnycklar (för användning av AES, till exempel), så att du undviker användningen av dyra RSA-eller Diffie-Hellman-åtgärder.

NetX Secure stöder den andra formen av PSK-krypteringssviter, vilket gör det möjligt för program att ta bort all krypterings kod för offentliga nycklar och minnes användning. Själva PSK är inte en AES-nyckel, men kan anses som ett lösen ord som de faktiska nycklarna genereras från. Det finns några begränsningar för vad PSK-värdet kan vara, även om längre värden ger högre säkerhet (samma som med lösen ord).

Om du vill använda PSK med ditt NetX-säkra program måste du först definiera det globala makrot **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Detta görs vanligt vis via dina kompilator inställningar, men definitionen kan också placeras i huvud filen nx_secure_tls. h. Med det definierade makrot kommer PSK ciphersuite-stödet att kompileras till ditt NetX-säkra DTLS-program.

När PSK-stödet är aktiverat kan du använda DTLS-API: et för att konfigurera PSKs för ditt program. Varje PSK kräver ett PSK-värde (den faktiska hemliga nyckeln "– Behåll det här värdet säkert), ett" Identity "-värde som används för att identifiera specifika PSK och ett" identitets tips "som används av en TLS-server för att välja ett visst PSK-värde.

Själva PSK-objektet kan vara ett binärt värde eftersom det aldrig skickas via en nätverks anslutning. PSK kan vara valfritt värde upp till 64 byte långt.

Identiteten och tipset måste vara utskrivbara sträng strängar formaterade med UTF-8. Värdena för identitet och ledtråd kan vara en valfri längd på upp till 128 byte.

Identiteten och PSK-formen bildar ett unikt par som läses in på varje enhet i nätverket som behöver kommunicera med varandra.

"Tipset" används främst för att definiera specifika program profiler för att gruppera PSKs efter funktion eller tjänst. Dessa värden måste överenskommas i förväg och är beroende av program. Som exempel använder OpenSSL kommando rads serverprogram (med PSK aktiverat) standard strängen "Client_identity", som måste tillhandahållas av en TLS-klient för att kunna fortsätta med TLS-handskakningen.

Mer information om PSKs finns i NetX Secure API-referens för följande tjänster: nx_secure_dtls_psk_add nx_secure_dtls_server_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importerar X. 509-certifikat till NetX Secure

Digitala certifikat krävs för de flesta TLS-anslutningar på Internet. Certifikat ger en metod för att autentisera tidigare okända värdar via Internet genom användning av betrodda mellanhänder, vanligt vis kallade *certifikat utfärdare eller certifikat* utfärdare. Om du vill ansluta din NetX-enhet till en kommersiell moln tjänst (till exempel Amazon Web Services) måste du importera certifikat till ditt program genom att läsa in dem på enheten.

Tillsammans med certifikat behöver du ibland även en *privat nyckel* som är kopplad till ditt certifikat. I vissa program (t. ex. TLS-klient när autentisering av klient certifikat används inte) är certifikatet tillräckligt, men om ditt certifikat används för att identifiera din enhet behöver du en privat nyckel. Privata nycklar skapas vanligt vis när du skapar ditt certifikat och lagras i en separat fil, ofta krypterat med ett lösen ord.

En detaljerad beskrivning av hur du importerar certifikat till NetX-säkra program finns i kapitel 3 i användar handboken för NetX Secure TLS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Autentisering av klient certifikat i NetX Secure TLS

När du använder autentisering med X. 509-certifikat kräver TLS/DTLS-protokollet att DTLS-serverinstansen ger ett certifikat för identifiering, men som standard behöver DTLS-klient instansen inte tillhandahålla ett certifikat för autentisering med hjälp av en annan form av autentisering i stället (t. ex. en kombination av användar namn/lösen ord). Detta matchar den vanligaste användningen av TLS på Internet för webbplatser. Till exempel måste en detaljist webbplats bevisa för en potentiell kund som använder en webbläsare som servern är legitim, men användaren använder ett inloggnings-/lösen ord för att få åtkomst till ett speciellt konto.

Standard fallet är dock inte alltid önskvärt, så TLS/DTLS kan också tillåta att DTLS-serverinstansen begär ett certifikat från fjärrklienten. När den här funktionen är aktive rad skickar DTLS-servern ett CertificateRequest-meddelande till DTLS-klienten under hand skakningen. Klienten måste svara med ett eget certifikat och ett CertificateVerify-meddelande som innehåller en kryptografisk token som styrker att klienten äger den matchande privata nyckeln som är kopplad till certifikatet. Om verifieringen Miss lyckas eller om certifikatet inte är anslutet till ett betrott certifikat på servern Miss lyckas TLS-handskakningen.

Det finns två separata fall för autentisering av klient certifikat i TLS – följande avsnitt beskriver båda fallen.

### <a name="client-certificate-authentication-for-dtls-clients"></a>Autentisering av klient certifikat för DTLS-klienter

En DTLS-klient kan försöka ansluta till en server som begär ett certifikat för klientautentisering. I det här fallet måste klienten ange ett certifikat för servern och kontrol lera att den äger den matchande privata nyckeln eller att servern avslutar DTLS-handskakningen.

I NetX Secure DTLS finns det ingen särskild konfiguration som stöder den här funktionen, men programmet måste ange ett lokalt identifierings certifikat för TLS-klientcertifikatet med hjälp av tjänsten *nx_secure_tls_session_local_certificate_add* . Om inget certifikat tillhandahålls av programmet men fjärrservern använder autentisering av klient certifikat och begär ett certifikat, kommer DTLS-handskakningen att Miss läge. Det certifikat som angavs för DTLS-sessionen med *nx_secure_dtls_session_local_certificate_add* måste identifieras av fjärrservern för att DTLS-handskakningen ska kunna slutföras.

### <a name="client-certificate-authentication-for-tls-servers"></a>Autentisering av klient certifikat för TLS-servrar

DTLS-serverns fall för autentisering av klient certifikat är något mer komplicerat än DTLS-klientens fall på grund av att funktionen är valfri. I det här fallet måste TLS-servern uttryckligen begära ett certifikat från fjärr-TLS-klienten, sedan bearbeta CertificateVerify-meddelandet för att verifiera att den fjärranslutna klienten äger den matchande privata nyckeln och servern måste kontrol lera att det certifikat som tillhandahålls av klienten kan spåras till ett certifikat i det lokala betrodda certifikat arkivet.

I NetX Secure TLS Server-instanser kontrol leras klient certifikatets autentisering av *nx_secure_dtls_server_x509_client_verify_configure* -och *nx_secure_dtls_server_x509_client_verify_disable* -tjänsterna.

Om du vill aktivera autentisering av klient certifikat måste ett program anropa *nx_secure_dtls_server_x509_client_verify_configure* med DTLS innan du anropar *nx_secure_dtls_server_start*. Verifieringen kräver att utrymme allokeras för inkommande klient certifikat som anges som en parameter för att *nx_secure_dtls_server_x509_client_verify_configure.* Observera att bufferten måste vara tillräckligt stor för att rymma den högsta certifikat kedja som tillhandahålls av en klient *gånger antalet DTLS Server-sessioner*. Varje server session kräver utrymme som kommer att allokeras från den angivna bufferten. Kontrol lera att bufferten är tillräckligt stor eller att det uppstår ett fel om den angivna klient certifikat kedjan är för stor.

När autentisering av klient certifikat är aktiverat kommer DTLS-servern begära ett certifikat från DTLS-klienten under DTLS-handskakningen. I NetX Secure DTLS-servern kontrol leras klient certifikatet mot arkivet med betrodda certifikat som skapats med *nx_secure_dtls_server_trusted_certificate_add* genom att följa kedjan för X. 509-utfärdaren. Fjärrklienten måste ange en kedja som ansluter sitt identitets certifikat till ett certifikat i det betrodda arkivet eller så Miss DTLS-handskakningen. Även om bearbetningen av CertificateVerify-meddelanden Miss lyckas kommer DTLS-handskakningen att Miss lyckas.

De autentiseringsmetoder som används för metoden CertificateVerify är fasta för TLS version 1,0 och TLS-version 1,1 och anges av TLS-servern i TLS version 1,2, då NetX Secure DTLS är baserad. För DTLS 1,2 följer de autentiseringsmetoder som stöds vanligt vis de relevanta metoder som anges i tabellen med kryptografiska metoder, men vanligt vis RSA med SHA-256 (se avsnittet "kryptografi i NetX Secure TLS" för mer information om att initiera TLS med kryptografiska metoder).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografi i NetX Secure TLS

TLS definierar ett protokoll där kryptografi kan användas för att skydda nätverkskommunikation. Därför lämnar den den faktiska kryptografin att använda ganska stor öppen för TLS-användare. För specifikationen krävs bara att en enda ciphersuite implementeras – i händelse av TLS 1,2 är ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, vilket indikerar användningen av RSA för offentliga nyckel åtgärder, AES i CBC-läge med 128-bitars nycklar för sessions kryptering och SHA-1 för hash-meddelanden för meddelandeautentisering.

Som standard är TLS 1,2-kompatibel och den obligatoriska TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite som standard, men med tanke på antalet möjliga implementeringar för var och en av de kryptografiska metoderna på grund av maskin varu funktioner och andra överväganden, är NetX Secure en allmän krypterings-API som gör att en användare kan ange vilka kryptografiska metoder som ska användas med TLS.

> [!NOTE]
> Med den allmänna kryptografiska API-mekanismen kan användare implementera sina egna krypteringssviter, men detta rekommenderas för avancerade användare som är bekanta med TLS-krypteringssviter och-tillägg. Kontakta din uttryckliga Logic-representant om du är intresse rad av att stödja din egen krypteringssviter.

Mer information om hur du konfigurerar kryptografiska metoder för DTLS finns i NetX Secure TLS user guide, kapitel 3. Samma process gäller både TLS-och DTLS.
