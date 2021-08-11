---
title: Kapitel 3 – Funktionell beskrivning av Azure RTOS NetX Secure DTLS
description: Det här kapitlet innehåller en funktionell beskrivning av Azure RTOS NetX Secure DTLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7db319e45c6d1f4a2030734fc01fefc4f3907aebeec1b3f47a5bde57dd5bfcc4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797099"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>Kapitel 3: Funktionell beskrivning av Azure RTOS NetX Secure DTLS

## <a name="execution-overview"></a>Körningsöversikt

Det här kapitlet innehåller en funktionell beskrivning av Azure RTOS NetX Secure DTLS. Det finns två primära typer av programkörning i ett NetX Secure DTLS-program: initiering och anrop till programgränssnitt. 

NetX Secure förutsätter att ThreadX och NetX/NetXDuo finns. Från ThreadX krävs trådkörning, stängning, periodiska timers och ömsesidig exkludering. Från NetX/NetXDuo krävs UDP- och IP-nätverksfunktioner och drivrutiner.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>Datagram Transport Layer Security (DTLS) och Transport Layer Security (TLS)

NetX Secure DTLS implementerar Datagram Transport Layer Security version 1.2 som definieras i RFC 6347. DTLS version 1.0 definierades i RFC 4347 och motsvarar TLS version 1.1. På grund av att DTLS i stort sett är ett tillägg till TLS, beslutades att nästa version skulle använda samma versionsnummer som motsvarande TLS-version. Därför finns det ingen DTLS version 1.1 eftersom DTLS version 1.2 motsvarar TLS version 1.2.

> [!NOTE]
> NetX Secure stöder DTLS version 1.2. DTLS 1.0 (RFC 4347) **stöds inte** för närvarande.

*Secure Sockets Layer* (SSL) var det ursprungliga namnet på TLS innan det blev en standard i RFC 2246 och "SSL" används ofta som ett allmänt namn för TLS-protokollen. Den senaste versionen av SSL var 3.0 och TLS 1.0 kallas ibland SSL version 3.1. Alla versioner av det officiella SSL-protokollet betraktas som föråldrade och osäkra, och netX Secure tillhandahåller för närvarande ingen SSL-implementering.

TLS anger ett protokoll för att generera *sessionsnycklar* som skapas under TLS-handskakningen mellan en TLS-klient och -server och dessa nycklar används för att kryptera data som skickas av programmet under  TLS-sessionen. 

DTLS är nära kopplat till TLS, eftersom de underliggande säkerhetsmekanismerna delas mellan protokollen. TLS är dock utformat för att fungera över ett transportlagerprotokoll som ger garantier om paketleverans och -ordning (nästan alltid TCP i praktiken) och fungerar inte över ett opålitligt protokoll som UDP. Det är just på grund av UDP som DTLS introducerades: DTLS utformades för att hantera UDP:s opålitliga natur och liknande protokoll. Den gör detta genom att inkludera ordnings- och tillförlitlighetslogik (t.ex. återöverföring av bort ignorerade data) som liknar tillförlitliga protokoll som TCP.

En fullständig diskussion om TLS finns i kapitel 3 i användarhandboken för NetX Secure TLS, så det här dokumentet fokuserar på skillnaderna mellan TLS och DTLS.

### <a name="dtls-record-header"></a>DTLS-postrubrik

Alla giltiga DTLS-poster måste ha ett DTLS-huvud, som du ser i bild 1. Rubriken är samma som TLS med tillägget av två nya fält: 16-bitars *epoken* och 48-bitars *sekvensnumret*, som beskrivs nedan.

![Diagram över en DTLS-postrubrik.](media/image2.png)

**Bild 1 – DTLS-postrubrik**

Fälten i TLS-postrubriken definieras på följande sätt:

| TLS-rubrikfält | Syfte  |
| ---------------- | --------- |
| **8-bitars meddelandetyp** | Det här fältet innehåller typen av DTLS-post som skickas. Giltiga typer är följande:<br />– ChangeCipherSpec: 0x14<br />– Avisering: 0x15<br />– Handskakning: 0x16<br />– Programdata: 0x17<br /> |
| **16-bitars protokollversion** | Det här fältet innehåller DTLS-protokollversionen. Giltiga värden är följande:<br />– DTLS 1.1: 0xFEFD |
|  **16-bitars epok** |  Det här fältet innehåller DTLS "epoch" som är en räknare som ökas varje gång krypteringstillståndet ändras (t.ex. när nya sessionsnycklar genereras).  |
|  **48-bitars sekvensnummer** |  Det här fältet innehåller ett sekvensnummer som identifierar den här specifika posten. Den används av DTLS för att underhålla postordning och kontrollera om det finns behov av vidareöverföring. |
|  **16-bitars längd** |  Det här fältet innehåller längden på de data som är inkapslade i DTLS-posten.  |

### <a name="dtls-handshake-record-header"></a>DTLS Handshake Record-rubrik

En giltig DTLS-handskakningspost måste ha ett DTLS Handshake-huvud, som du ser i bild 2.

![Diagram över ett DTLS Handshake Record-huvud.](media/image3.png)

**Bild 2 – DTLS Handshake-postrubrik**

Fälten i DTLS Handshake-postrubriken definieras på följande sätt:

| TLS-rubrikfält | Syfte  |
| ---------------- | ------------------------------------------------ |
| **8-bitars meddelandetyp** | Det här fältet innehåller typen av DTLS-post som skickas. Giltiga typer är följande:<br />– ChangeCipherSpec: 0x14<br />– Avisering: 0x15<br />– Handskakning: 0x16<br />– Programdata: 0x17 |
|  **16-bitars epok** | Det här fältet innehåller DTLS "epoch" som är en räknare som ökas varje gång krypteringstillståndet ändras (t.ex. när nya sessionsnycklar genereras). |
|  **48-bitars sekvensnummer** | Det här fältet innehåller ett sekvensnummer som identifierar den här specifika posten. Den används av DTLS för att underhålla postordning och kontrollera om det finns behov av vidareöverföring. |
|  **16-bitars protokollversion** | Det här fältet innehåller DTLS-protokollversionen. Giltiga värden är följande:<br />– DTLS 1.1: 0xFEFD |
| **16-bitars längd** | Det här fältet innehåller längden på de data som är inkapslade i DTLS-posten. |
| **8-bitars handskakningstyp** | Det här fältet innehåller meddelandetypen handskakning. Giltiga värden är följande:<br />- HelloRequest: 0x00<br />– ClientHello: 0x01<br />– ServerHello: 0x02<br />– Certifikat: 0x0B<br />– ServerKeyExchange: 0x0C<br />– CertificateRequest: 0x0D<br />– ServerHelloDone: 0x0E<br />– CertificateVerify: 0x0F<br />– ClientKeyExchange: 0x10<br />– Klart: 0x14 |
| **24-bitars längd** | Det här fältet innehåller längden på handskakningsmeddelandedata. |
| **16-bitars sekvensnummer** | Det här fältet innehåller ett sekvensnummer. |

### <a name="the-dtls-handshake-and-dtls-session"></a>DTLS-handskakningen och DTLS-sessionen

En typisk DTLS-handskakning visas i bild 3. Den är nästan identisk med den typiska TLS-handskakningen med en viktig skillnad – när ClientHello-meddelandet först skickas svarar servern med ett nytt DTLS-specifikt meddelande, *HelloVerifyRequest* som innehåller en "cookie". DTLS-klienten måste svara med ett andra ClientHello-meddelande som innehåller cookien innan handskakningen kan fortsätta. Den här mekanismen har lagts till i DTLS för att förhindra vissa DoS-attacker (Denial of Service) eftersom UDP är ett anslutningslöst protokoll (TCP kräver en dedikerad anslutning/port så att TLS inte drabbas av samma problem).

En DTLS-handskakning börjar när klienten skickar ett *ClientHello-meddelande* till en DTLS-server som anger att den vill starta en DTLS-session. Meddelandet innehåller information om krypteringen som klienten vill använda för sessionen, tillsammans med information som används för att generera sessionsnycklarna senare i handskakningen. Alla meddelanden i DTLS-handskakningen krypteras inte förrän sessionsnycklarna har genererats. Som nämnts ovan kan DTLS-servern skicka en HelloVerifyRequest som svar på ClientHello, vilket tvingar klienten att svara med en andra uppdaterad ClientHello.

När du får det andra ClientHello-meddelandet verifierar DTLS-servern cookien och om den är korrekt svarar den med ett ServerHello-meddelande som anger ett val från de krypteringsalternativ som tillhandahålls av klienten. ServerHello följs av ett certifikatmeddelande där servern tillhandahåller ett digitalt certifikat för att autentisera sin identitet för klienten (om X.509-verifiering används). Slutligen skickar servern ett ServerHelloDone-meddelande för att indikera att den inte har några fler meddelanden att skicka. Servern kan också skicka andra meddelanden efter ServerHello och i vissa fall kanske den inte skickar ett certifikatmeddelande (till exempel när i förväg delade nycklar används), därav behovet av ServerHelloDone-meddelandet.

När klienten har tagit emot alla serverns meddelanden har den tillräckligt med information för att generera sessionsnycklarna. TLS/DTLS gör detta genom att skapa en delad bit slumpmässiga data som kallas *för* masterhemlighet, som är en fast storlek och används som start för att generera alla nycklar som behövs när kryptering har aktiverats. För masterhemligheten krypteras med hjälp av algoritmen för offentlig nyckel (t.ex. RSA) som anges i Hello-meddelanden (se nedan för information om algoritmer för offentliga nycklar) och den offentliga nyckeln som tillhandahålls av servern i certifikatet. En valfri TLS/DTLS-funktion som kallas I förväg delade nycklar (PSK) möjliggör chiffer som inte använder ett certifikat utan i stället använder ett hemligt värde som delas mellan värdarna (vanligtvis via fysisk överföring eller annan skyddad metod). När PSK är aktiverat används den i förväg delade hemliga nyckeln för att generera för masterhemligheten. Se avsnittet om i förväg delade nycklar i "Autentiseringsmetoder" nedan.

I en vanlig TLS/DTLS-handskakning skickas den krypterade för masterhemligheten till servern i ClientKeyExchange-meddelandet. När servern tar emot ClientKeyExchange-meddelandet dekrypterar den förinstallerade hemligheten med hjälp av den privata nyckeln och fortsätter att generera sessionsnycklarna parallellt med TLS/DTLS-klienten.

När sessionsnycklarna har genererats kan alla ytterligare meddelanden krypteras med hjälp av algoritmen för privat nyckel (t.ex. AES) som valts i Hello-meddelanden. Ett sista okrypterat meddelande med namnet ChangeCipherSpec skickas av både klienten och servern för att indikera att alla ytterligare meddelanden kommer att krypteras.

Det första krypterade meddelandet som skickas av både klienten och servern är också det sista TLS-handskakningsmeddelandet, med namnet Finished (Slutfört). Det här meddelandet innehåller en hash för alla handskakningsmeddelanden som tas emot och skickas. Den här hashen används för att kontrollera att inga meddelanden i handskakningen har manipulerats eller skadats (vilket indikerar ett möjligt säkerhetsintrång).

När slutförda meddelanden tas emot och handskakningshashar har verifierats börjar TLS/DTLS-sessionen och programmet börjar skicka och ta emot data. Alla data som skickas av endera sidan under TLS/DTLS-sessionen hashas först med hjälp av den hash-algoritm som valts i Hello messages (för att tillhandahålla meddelandeintegritet) och krypteras med hjälp av den valda privata nyckelalgoritmen med de genererade sessionsnycklarna.

Slutligen kan en TLS/DTLS-session endast avslutas om antingen klienten eller servern väljer att göra det. En trunkerad session betraktas som ett säkerhetsintrång (eftersom en angripare kan försöka förhindra att alla data skickas från att tas emot). Därför skickas ett särskilt meddelande när någon av sidorna vill avsluta sessionen, vilket kallas closeNotify-avisering. Både klienten och servern måste skicka och bearbeta en CloseNotify-avisering för en lyckad sessionsavstängning.

![Diagram över en typisk DTLS-handskakningssession.](media/image4.png)

**Bild 3 – Typisk DTLS-handskakning**

### <a name="initialization"></a>Initiering

NetX- eller NetXDuo-stacken måste initieras innan du använder NetX Secure DTLS. Mer information om hur du initierar TCP/IP-stacken för UDP finns i användarhandboken för NetX eller NetXDuo.

När NetX UDP har initierats kan DTLS aktiveras. Internt hanteras all DTLS-nätverkstrafik och -bearbetning av NetX/NetXDuo-stacken utan att användaren behöver göra något. DTLS har dock vissa specifika krav som måste hanteras separat från den underliggande nätverksstacken. DTLS-klientåtgärden dessa parametrar tilldelas till DTLS-kontrollblocket med namnet ***NX_SECURE_DTLS_SESSION** _. För DTLS-serveråtgärden kallas kontrollblocket _ *_NX_SECURE_DTLS_SERVER_** och innehåller den infrastruktur som behövs för att hantera flera DTLS-sessioner på en enda UDP-port . Observera att detta skiljer sig från TLS där varje TLS-session är bunden till en enda TCP-port.

De två DTLS-lägena Server och Klient kan aktiveras i ett program (men bara ett läge per NetX-socket) och var och en har sina egna specifika krav, som beskrivs nedan.

### <a name="initialization--dtls-server"></a>Initiering – DTLS-server

NetX Secure DTLS-serverläget skiljer sig från TLS-serverläget på grund av användningen av UDP för det underliggande transportprotokollet för nätverket. Med TCP är porten bunden till en enda fjärrvärd under TLS-sessionens varaktighet. UDP har ingen uppfattning om tillstånd när det gäller fjärrvärden, så DTLS-begäranden från olika värdar tas alla emot i samma UDP-gränssnitt. DTLS måste därför upprätthålla sessionstillståndet i stället för att förlita sig på socketen som med TLS och TCP. Därför upprätthåller DTLS-serverkontrollblocket (NX_SECURE_DTLS_SERVER) en mappning av fjärrvärdinformation (IP-adress och port) till DTLS-sessioner. Alla inkommande data på UDP-socketen som tilldelats en DTLS-server mappas till en befintlig eller ny DTLS-session baserat på fjärrvärden. Därför kräver DTLS-serverskapandet flera ytterligare parametrar utöver vad TLS- och DTLS-klienten behöver.

Förutom DTLS-serverkontrollblocket, TLS-chiffer och cachebufferten scratchspace/metadata kräver DTLS-servrar en buffert för att underhålla DTLS-sessioner och en buffert för paketsammansättning som används för att dekryptera inkommande DTLS-poster.

Förutom sessionsbuffertar kräver DTLS-servrar ett digitalt certifikat *,* som är ett dokument som används för att identifiera TLS-servern till den anslutande TLS-klienten och certifikaten motsvarande privat nyckel *,* vanligtvis för RSA-krypteringsalgoritmen. Standarden International Telecommunications Union X.509 anger det certifikatformat som används av TLS/DTLS och det finns många verktyg för att skapa digitala X.509-certifikat.

För NetX Secure DTLS måste X.509-certifikatet vara binärt kodat med formatet Distinguished Encoding Rules (DER) i ASN.1. DER är standardformatet för TLS over-the-wire binary för certifikat.

Den privata nyckeln som är associerad med det angivna certifikatet måste vara i DER-Encoded PKCS#1-format. Den privata nyckeln används bara på enheten och överförs aldrig via kabeln. Skydda privata nycklar eftersom de ger säkerhet för TLS/DTLS-kommunikation!

För att initiera DTLS-servercertifikatet måste programmet ange en pekare till en buffert som innehåller de DER-kodade X.509-certifikatet och valfria DER-kodade PKCS#1 RSA privata nyckeldata med ***hjälp av nx_secure_x509_certificate_intialize-tjänsten,*** som fyller i **NX_SECURE_X509_CERT-strukturen** med lämpliga certifikatdata för användning av TLS.

När servercertifikatet har initierats måste det läggas till i  TLS-kontrollblocket med hjälp av nx_secure_dtls_server_local_certificate_add tjänsten.

När serverns certifikat har lagts till i DTLS-serverns kontrollblock kan servern användas för säker DTLS-kommunikation (se exemplet ovan).

### <a name="initialization--dtls-client"></a>Initiering – DTLS-klient

NetX Secure DTLS-klientläget är enkelt jämfört med DTLS-servern eftersom det bara finns en enda utgående anslutning till fjärrvärden via UDP-socketen.

För att konfigurera en DTLS-klient krävs ett betrott certifikatarkiv *,* som är en samling X.509-kodade digitala certifikat från betrodda certifikatutfärdare (CA:er). Dessa certifikat antas av DTLS-protokollet vara "betrodda" och utgör grunden för autentisering av certifikat som tillhandahålls av DTLS-serverentiteter till NetX Secure DTLS-klientprogrammet.

Ett betrott *CA-certifikat* kan antingen vara själv signerat eller signerat av en annan certifikatutfärdare, i vilket fall certifikatet kallas en *mellanliggande certifikatutfärdare* (ICA). I ett typiskt TLS/DTLS-program tillhandahåller servern ICA-certifikaten tillsammans med dess servercertifikat, men det enda kravet för lyckad autentisering är att en kedja av utfärdare (certifikat som används för att signera andra certifikat) kan spåras från servercertifikatet tillbaka till ett betrott CA-certifikat i det betrodda certifikatarkivet. Den här kedjan kallas för en *kedja av förtroende eller* *certifikatkedja*.

För att initiera en betrodd certifikatutfärdare eller ett ICA-certifikat måste programmet ange en pekare till en buffert som innehåller det DER-kodade X.509-certifikatet med hjälp av tjänsten ***nx_secure_x509_certificate_intialize** _ som fyller i strukturen _ *NX_SECURE_X509_CERT** med lämpliga certifikatdata för användning av TLS.

DTLS-klienten behöver också utrymme för att det inkommande servercertifikatet ska allokeras (förutsatt att läget Fördelad nyckel inte används) och en buffert för att montera paket i DTLS-poster som ska dekrypteras. Dessa buffertar skickas som parametrar till tjänsten ***nx_secure_dtls_session_create*** (mer information finns i API-referens).

Betrodda certifikat som har initierats läggs sedan till i det skapade DTLS-sessionskontrollblocket med hjälp ***av nx_secure_dtls_session_trusted_certificate_add tjänsten.*** Om du inte lägger till ett certifikat misslyckas DTLS-klientsessionen eftersom DTLS-protokollet inte kan autentisera fjärrservervärdar.

När det betrodda certifikatarkivet har skapats kan sessionen användas för att upprätta en säker TLS-klientanslutning.

### <a name="application-interface-calls"></a>Anrop till programgränssnitt

NetX Secure DTLS-program gör vanligtvis funktionsanrop inifrån programtrådar som körs under ThreadX RTOS. Viss initiering, särskilt för de underliggande protokollen för nätverkskommunikation (t.ex. UDP och IP) kan anropas från ***tx_application_define*.** Mer information om hur du initierar nätverkskommunikation finns i användarhandboken för NetX/NetXDuo.

DTLS använder krypteringsrutiner som är processorintensiva åtgärder. I allmänhet utförs dessa åtgärder inom kontexten för anrop av tråd.

### <a name="dtls-session-start"></a>Start av DTLS-session

DTLS kräver ett underliggande transportlagernätverksprotokoll för att fungera. Protokollet som vanligtvis används är TCP. För att upprätta en NetX Secure TLS-session **måste en NX_UDP_SOCKET** skapas och skickas till **_nx_secure_dtls_client_session_start_** för DTLS-klienter.

DTLS-servrar fungerar annorlunda. UDP-socketen som används för inkommande DTLS-klientbegäranden finns i NX_SECURE_DTLS_SERVER-kontrollblocket och initieras i anropet till ***nx_secure_dtls_server_create** _, vilket tar den lokala UDP-porten som en parameter. Tjänstens _*_nx_secure_dtls_server_start_*_ sedan för att starta DTLS-servern för att hantera inkommande begäranden. Alla inkommande begäranden hanteras i återanropsrutiner som _tillhandahålls till nx_secure_dtls_server_create*: en för anslutningar och en för att ta emot meddelanden. Det är upp till_ programmet att hantera start av DTLS-sessionen när ett anslutningsmeddelande tas emot (återanropet av anslutningsavisering anropas av DTLS) genom att anropa * nx_secure_dtls_server_session_start . Programmet måste också hantera inkommande data när motringning av meddelanden anropas (som följer en slutförd DTLS-handskakning) genom att anropa _*_nx_secure_dtls_session_receive_**. Informationen om detta finns i exemplet ovan och i API-referensen för var och en av ovanstående tjänster.

### <a name="dtls-packet-allocation"></a>DTLS-paketallokering

NetX Secure DTLS använder samma paketstruktur som NetX/NetXDuo TCP (***NX_PACKET** _) förutom att i stället för att anropa _*_nx_packet_allocate-tjänsten_*_ måste tjänsten _ *_nx_secure_dtls_packet_allocate_** anropas så att utrymmet för DTLS-huvudet kan allokeras korrekt.

### <a name="dtls-session-send"></a>Skicka DTLS-session

När TLS-sessionen har startat kan programmet  skicka data med hjälp av nx_secure_dtls_session_send tjänsten. Den skickande tjänsten används identiskt med tjänsten ***nx_udp_socket_send** _ och använder datastrukturen _ *_NX_PACKET_** som innehåller de data som skickas, en mål-IP-adress och en UDP-målport.

> [!IMPORTANT]
> När du skickar data med nx_secure_dtls_session_send är det viktigt att använda samma IP-adress och port som användes för att upprätta DTLS-sessionen, såvida det inte finns en mekanism för att flytta sessionen till en ny adress och UDP-port direkt (detta är inte vanligt).

Alla data som skickas via DTLS krypteras av NX Secure DTLS-stacken och de konfigurerade krypteringsrutinerna innan de skickas.

### <a name="dtls-session-receive"></a>Ta emot DTLS-session

När DTLS-sessionen har startat kan programmet börja ta emot data med hjälp av tjänsten ***nx_secure_Dtls_session_receive** _ . Precis som DTLS-sessionen skickar används den här tjänsten på samma sätt som _*_nx_udp_socket_receive_**, förutom att inkommande data dekrypteras och verifieras av DTLS-stacken innan de returneras i paketstrukturen.

### <a name="tls-session-close"></a>Stängning av TLS-session

När en DTLS-session är klar måste både DTLS-klienten och servern skicka en CloseNotify-avisering till den andra sidan för att stänga av sessionen. Båda sidor måste ta emot och bearbeta aviseringen för att säkerställa en lyckad sessionsavstängning.

Om fjärrvärden skickar en CloseNotify-avisering bearbetar alla anrop till tjänsten ***nx_secure_dtls_session_receive** _ aviseringen, skickar motsvarande avisering tillbaka till fjärrvärden och returnerar värdet _*_NX_SECURE_TLS_SESSION_CLOSED_**. När sessionen har stängts misslyckas eventuella ytterligare försök att skicka eller ta emot data med DTLS-sessionen.

Om programmet vill stänga TLS-sessionen måste tjänsten ***nx_secure_dtls_session_end** _ anropas. Tjänsten skickar CloseNotify-aviseringen och bearbetar svaret CloseNotify. Om svaret inte tas emot returneras felvärdet _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_** som anger att DTLS-sessionen inte har stängts av korrekt, vilket är en möjlig säkerhetsöverträdelse.

### <a name="tlsdtls-alerts"></a>TLS/DTLS-aviseringar

TLS/DTLS är utformat för att ge maximal säkerhet, så avvikande beteende i protokollet anses vara en potentiell säkerhetsöverträdelse. Därför betraktas eventuella fel i meddelandebearbetning eller kryptering/dekryptering som allvarliga fel som avslutar handskakningen eller sessionen omedelbart.

Det är relativt enkelt att hantera fel i ett lokalt program, men fjärrvärden måste känna till att ett fel har uppstått för att kunna hantera situationen korrekt och förhindra eventuella säkerhetsöverträdelser. Därför skickar TLS/DTLS ett *aviseringsmeddelande* till fjärrvärden vid eventuella fel.

Aviseringar behandlas på samma sätt som andra TLS/DTLS-meddelanden och krypteras under sessionen för att förhindra att en angripare samlar in information från den typ av avisering som tillhandahålls. Under handskakningen är de aviseringar som skickas begränsade i omfånget för att begränsa mängden information som kan hämtas av en potentiell angripare.

CloseNotify-aviseringen, som används för att stänga TLS/DTLS-sessionen, är den enda aviseringen som inte är allvarligare. Även om det betraktas som en avisering och skickas som ett aviseringsmeddelande, skiljer sig CloseNotify från andra aviseringar på så sätt att det inte indikerar att ett fel har uppstått.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>Omförhandling av TLS/DTLS-session och återupptagande

TLS stöder begreppet "omförhandling", vilket helt enkelt är en omförhandling av TLS-sessionsparametrar i kontexten för en befintlig TLS-session.

Återupptagande av *TLS-session* bör inte förväxlas med *omförhandling av sessioner,* trots vissa likheter. Om *omförhandling* av sessioner inbegriper start av en ny handskakning i en befintlig TLS-session är återaktivering av session en helt valfri funktion som innebär att starta om en stängd TLS-session utan att utföra en fullständig TLS-handskakning. 

NX Secure DTLS hanterar inkommande omförhandlingsbegäranden från fjärrvärdar. Det stöder **inte** återintagande av sessioner. En mer fullständig diskussion om dessa funktioner finns i kapitel 3 i användarhandboken för NetX Secure TLS.

### <a name="protocol-layering"></a>Protokollskiktning

TLS-protokollet (och därmed även DTLS) passar in i nätverksstacken mellan transportlagret (t.ex. TCP eller UDP) och programlagret. TLS anses ibland vara ett transportlagerprotokoll (därav *Transport Layer* Security), men eftersom det fungerar som ett program med avseende på de underliggande nätverksprotokollen grupperas det ibland i programlagret.

TLS kräver ett transportlagerprotokoll som stöder leverans i ordningsföljd och förlustfri leverans, till exempel TCP. På grund av detta krav kan TLS inte köras ovanpå UDP eftersom UDP inte garanterar leverans av datagram. *DTLS* är en modifierad version av TLS som används för program som behöver säkerhet för TLS via ett datagramprotokoll som UDP.

![Diagram över ett TLS-protokollskikt.](media/image6.png)

**Bild 4 – Protokollskikten TCP/IP, UDP och TLS/DTLS**

## <a name="network-communications-security-and-encryption"></a>Säkerhet och kryptering för nätverkskommunikation

Att skydda kommunikationen över offentliga nätverk och Internet är ett ytterst viktigt ämne och ämnet för ett stort antal böcker, artiklar och lösningar. Ämnet är snidigt komplext, men kan reduceras till en enkel idé: att skicka information via ett nätverk så att endast det avsedda målet kan komma åt eller ändra informationen. Detta går in i tre viktiga begrepp: sekretess, integritet och autentisering. TLS/DTLS-protokollet tillhandahåller lösningar för alla tre.

Kryptering används på olika sätt för att tillhandahålla sekretess, integritet och autentisering inom TLS- och DTLS-protokollen. Krypteringen måste tillhandahållas till TLS eller DTLS när en session eller serverinstans skapas, eftersom TLS tillhandahåller ett flexibelt ramverk för att använda kryptering och inte själva krypteringen. NetX Secure DTLS tillhandahåller nödvändiga krypteringsrutiner för de flesta program så att du inte behöver bekymra dig om att hitta rätt kryptering.

En mer detaljerad beskrivning av dessa ämnen finns i kapitel 3 i användarhandboken för NetX Secure TLS.

## <a name="tls-and-dtls-extensions"></a>TLS- och DTLS-tillägg

TLS (och därför DTLS) tillhandahåller ett antal tillägg som ger ytterligare funktioner för vissa program. Dessa tillägg skickas vanligtvis som en del av ClientHello- eller ServerHello-meddelanden, vilket indikerar för en fjärrvärd att du vill använda ett tillägg eller ange ytterligare information för användning vid upprättandet av en säker TLS-session.

NetX Secure DTLS stöder alla tillägg som finns i NetX Secure TLS, och en fullständig beskrivning av dessa finns i NetX Secure TLS användarhandbok, kapitel 3.

## <a name="authentication-methods"></a>Autentiseringsmetoder

TLS och DTLS tillhandahåller ramverket för att upprätta en säker anslutning mellan två enheter över ett osäkert nätverk, men en del av problemet är att känna till enhetens identitet i den andra änden av anslutningen. Utan en mekanism för att autentisera identiteten för fjärrvärdar blir det en trivial åtgärd för en angripare att utgöra en betrodd enhet.

Inledningsvis kan det verka som att användningen av IP-adresser, maskinvaru-MAC-adresser eller DNS skulle ge en relativt hög förtroendenivå för att identifiera värdar i ett nätverk, men med tanke på typen av TCP/IP-teknik och hur enkelt det är att förfalska adresser och SKADADE DNS-poster (t.ex. genom DNS-cache-förfalskning) blir det tydligt att TLS behöver ytterligare ett skyddslager mot bedrägliga identiteter.

Det finns olika mekanismer som kan ge det här extra lagret av autentisering för TLS, men det vanligaste är det *digitala certifikatet.* Andra mekanismer är PSK (Pre-Shared Keys) och lösenordsscheman.

### <a name="digital-cerificates"></a>Digitala certifikat

Digitala certifikat är den vanligaste metoden för att autentisera en fjärrvärd i TLS. I princip är ett digitalt certifikat ett dokument med specifik formatering som tillhandahåller identitetsinformation för en enhet i ett datornätverk.

TLS använder vanligtvis ett format som kallas X.509, en standard som utvecklats av International Telecommunication Union, även om andra format för certifikat kan användas om TLS-värdarna kan komma överens om vilket format som används. X.509 definierar ett specifikt format för certifikat och olika kodningar som kan användas för att skapa ett digitalt dokument. De flesta X.509-certifikat som används med TLS kodas med en variant av ASN.1, en annan telekommunikationsstandard. I ASN.1 finns det olika digitala kodningar, men den vanligaste kodningen för TLS-certifikat är Distinguished Encoding Rules (DER). DER är en förenklad delmängd av ASN.1 Basic Encoding Rules (BER) som är utformad för att vara entydig, vilket gör parsning enklare. Via kabel kodas TLS-certifikat vanligtvis i binär DER, och det är det format som NetX Secure förväntar sig för X.509-certifikat.

Även om DER-formaterade binära certifikat används i det faktiska TLS-protokollet kan de genereras och lagras i ett antal olika kodningar, med filnamnstillägg som .pem, .crt och .p12. De olika varianterna används av olika program från olika tillverkare, men i allmänhet kan alla konverteras till DER med hjälp av allmänt tillgängliga verktyg.

Den vanligaste av de alternativa certifikatkodningarna är PEM. PEM-formatet (från Privacy-Enhanced Mail) är en base-64-kodad version av DER-kodningen som ofta används eftersom kodningen resulterar i utskrivbar text som enkelt kan skickas med e-post eller webbaserade protokoll.

Att generera ett certifikat för ditt NetX Secure-program ligger vanligtvis utanför omfånget för den här handboken, men OpenSSL-kommandoradsverktyget ([www.openssl.org](http://www.openssl.org)) är allmänt tillgängligt och kan konverteras mellan de flesta format.

Beroende på ditt program kan du generera egna certifikat, tillhandahållas av en tillverkare eller myndighet eller köpa certifikat från en kommersiell certifikatutfärdare.

Om du vill använda ett digitalt certifikat i NetX Secure-programmet måste du först konvertera certifikatet till ett binärt DER-format och, om du vill, konvertera den associerade privata nyckeln (till exempel "privat exponent" för RSA) till ett binärt format, vanligtvis en PKCS#1-formaterad, DER-kodad RSA-nyckel. När konverteringen är klar är det upp till dig att läsa in certifikatet och den privata nyckeln på enheten. Möjliga alternativ är att använda ett flash-baserat filsystem eller generera en C-matris från data (med ett verktyg som "xxd" från Linux) och kompilera certifikatet och nyckeln till ditt program som konstanta data.

När certifikatet har lästs in på enheten kan DTLS-API:et användas för att associera certifikatet med en DTLS-session eller -server.

Mer information och exempel på hur du använder X.509-certifikat med NetX Secure DTLS finns i avsnittet Importera X.509-certifikat till NetX Secure i användarhandboken för NetX Secure TLS.

Mer information finns i följande DTLS-tjänster i API-referensen:

- nx_secure_x509_certificate_initialize,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Information om TLS-klientcertifikat

DTLS-klientimplementeringarna kräver vanligtvis inte att ett lokalt certifikat läses in på enheten. Ett lokalt certifikat är ett certifikat som identifierar den lokala enheten. Mer specifikt tillhandahåller ett lokalt certifikat identitetsinformation för den enhet där TLS/DTLS-programmet läses in. Undantaget till detta är när Klientcertifikatautentisering är aktiverat, men detta är mindre vanligt.

En DTLS-klient kräver att minst ett betrott certifikat läses in (fler kan läsas in om det behövs) och utrymme för att ett fjärrcertifikat ska allokeras. Ett betrott certifikat är ett certifikat som ger en grund för förtroende och autentisering av fjärrenheten, antingen direkt eller via en infrastruktur för offentliga nycklar (PKI). Roten i förtroendekedjan kallas vanligtvis certifikatutfärdare eller CA-certifikat. Ett fjärrcertifikat refererar till det certifikat som skickas av fjärrvärden under TLS-handskakningen. Den tillhandahåller identitet för den fjärrvärden och autentiseras genom att jämföra den med ett betrott certifikat på den lokala enheten.

Mer information om hur du lägger till betrodda certifikat och allokerar utrymme för fjärrcertifikat finns i TLS API-referensen för följande tjänster: nx_secure_dtls_session_create, nx_secure_dtls_session_trusted_certificate_add.

### <a name="tlsdtls-server-certificate-specifics"></a>Information om TLS/DTLS-servercertifikat

DTLS-serverimplementeringarna kräver vanligtvis inte att "betrodda" certifikat läses in på enheten eller fjärrcertifikat ska allokeras. Undantaget är när Klientcertifikatautentisering är aktiverat.

En TLS-server kräver att ett "lokalt" (eller "identitet") certifikat läses in så att servern kan tillhandahålla den till fjärrklienten under TLS-handskakningen för att autentisera servern för klienten.

Mer information om hur du läser in lokala certifikat för användning med NetX TLS-serverprogram finns i API-referensen för följande tjänster: nx_secure_dtls_server_local_certificate_add, nx_secure_dtls_server_local_certificate_remove.


### <a name="pre-shared-keys-psk"></a>I förväg delade nycklar (PSK)

En annan mekanism för identifieringsautentisering i TLS är begreppet I förväg delade nycklar (PSK). Om du använder en PSK-chiffersvit behöver du inte göra processorintensiva krypteringsåtgärder med offentliga nycklar, vilket är en boon för resursbegränsade inbäddade enheter. PSK ersätter certifikatet i TLS/DTLS-handskakningen och används i stället för den krypterade pre master-hemligheten för generering av TLS/DTLS-sessionsnyckel.

PSK-chiffer är begränsade i den mening att en delad hemlighet måste finnas på båda enheterna innan en TLS/DTLS-session kan upprättas. Det innebär att enheterna måste ha lästs in med den hemligheten på något annat sätt än en TLS PSK-anslutning– PSK:er kan uppdateras via en TLS PSK-anslutning, men enheten måste nödvändigtvis börja med en PSK som läses in via någon annan mekanism. En sensorenhet och dess gatewayenhet kan till exempel läsas in med PSK:er i fabriken innan den levereras, eller så kan en standard-TLS-anslutning (med ett certifikat) användas för att läsa in PSK.

PSK-chiffer finns i ett par former, som beskrivs i RFC 4279. Den första använder RSA eller Diffie-Hellman nycklar som används på samma sätt som de offentliga nycklar som överförs i certifikatet i standard-TLS-handskakningar. Det andra formuläret, som används mer i en resursbegränsad miljö, använder en PSK som används för att direkt generera sessionsnycklarna (till exempel för användning av AES), vilket undviker användningen av dyra RSA- eller Diffie-Hellman-åtgärder.

NetX Secure stöder den andra formen av PSK-chiffer, vilket gör det möjligt för program att ta bort all krypteringskod och minnesanvändning med offentliga nycklar. PSK är inte en AES-nyckel, men kan anses vara mer som ett lösenord som de faktiska nycklarna genereras från. Det finns några begränsningar för vad PSK-värdet kan vara, men längre värden ger högre säkerhet (samma som med lösenord).

Om du vill använda PSK med NetX Secure-programmet måste du först definiera det globala **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Detta görs vanligtvis via kompileringsinställningarna, men definitionen kan också placeras i nx_secure_tls.h-huvudfilen. När makrot har definierats kompileras PSK-chifferstöd till ditt NetX Secure DTLS-program.

När PSK-stöd är aktiverat kan du använda DTLS-API:et för att konfigurera PSK:er för ditt program. Varje PSK kräver ett PSK-värde (den faktiska hemliga "nyckeln" – skydda det här värdet), ett "identitetsvärde" som används för att identifiera den specifika PSK och ett "identitetstips" som används av en TLS-server för att välja ett visst PSK-värde.

Själva PSK kan vara ett binärt värde eftersom det aldrig skickas via en nätverksanslutning. PSK kan ha ett värde på upp till 64 byte.

Identiteten och tipset måste vara utskrivbara teckensträngar formaterade med UTF-8. Identitets- och tipsvärdena kan vara valfri längd på upp till 128 byte.

Identiteten och PSK bildar ett unikt par som läses in på varje enhet i nätverket som behöver kommunicera med varandra.

"Tipset" används främst för att definiera specifika programprofiler för att gruppera PSK:er efter funktion eller tjänst. Dessa värden måste avtalas i förväg och är programberoende. Till exempel använder OpenSSL-kommandoradsserverprogrammet (med PSK aktiverat) standardsträngen "Client_identity", som måste tillhandahållas av en TLS-klient för att kunna fortsätta med TLS-handskakningen.

Mer information om PSK:er finns i NetX Secure API-referensen för följande tjänster: nx_secure_dtls_psk_add, nx_secure_dtls_server_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importera X.509-certifikat till NetX Secure

Digitala certifikat krävs för de flesta TLS-anslutningar på Internet. Certifikat är en metod för att autentisera tidigare okända värdar via  Internet med hjälp av betrodda certifikatutfärdare eller certifikatutfärdare. Om du vill ansluta din NetX Secure-enhet till en kommersiell molntjänst (till exempel Amazon Web Services) måste du importera certifikat till ditt program genom att läsa in dem på enheten.

Tillsammans med certifikat behöver du ibland även en *privat nyckel som* är associerad med certifikatet. I vissa program (till exempel TLS-klient när autentisering med klientcertifikat inte används) räcker certifikatet, men om certifikatet används för att identifiera din enhet behöver du en privat nyckel. Privata nycklar genereras vanligtvis när du skapar certifikatet och lagras i en separat fil, ofta krypterad med ett lösenord.

En detaljerad beskrivning av hur du importerar certifikat till NetX Secure-program finns i kapitel 3 i användarhandboken för NetX Secure TLS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Klientcertifikatautentisering i NetX Secure TLS

När du använder X.509-certifikatautentisering kräver TLS/DTLS-protokollet att DTLS-serverinstansen tillhandahåller ett certifikat för identifiering, men som standard behöver DTLS-klientinstansen inte ange ett certifikat för autentisering med hjälp av en annan form av autentisering i stället (t.ex. en kombination av användarnamn/lösenord). Detta matchar den vanligaste användningen av TLS på Internet för webbplatser. En onlinebutik måste till exempel bevisa för en potentiell kund med hjälp av en webbläsare att servern är legitim, men användaren kommer att använda ett inloggnings-/lösenord för att få åtkomst till ett specifikt konto.

Standardfallet är dock inte alltid önskvärt, så TLS/DTLS tillåter eventuellt att DTLS-serverinstansen begär ett certifikat från fjärrklienten. När den här funktionen är aktiverad skickar DTLS-servern ett CertificateRequest-meddelande till DTLS-klienten under handskakningen. Klienten måste svara med ett eget certifikat och ett CertificateVerify-meddelande som innehåller en kryptografisk token som visar att klienten äger den matchande privata nyckel som är associerad med certifikatet. Om verifieringen misslyckas eller om certifikatet inte är anslutet till ett betrott certifikat på servern, misslyckas TLS-handskakningen.

Det finns två separata fall för klientcertifikatautentisering i TLS – i följande avsnitt beskrivs båda fallen.

### <a name="client-certificate-authentication-for-dtls-clients"></a>Klientcertifikatautentisering för DTLS-klienter

En DTLS-klient kan försöka ansluta till en server som begär ett certifikat för klientautentisering. I det här fallet måste klienten tillhandahålla ett certifikat till servern och verifiera att den äger den matchande privata nyckeln, annars avslutar servern DTLS-handskakningen.

I NetX Secure DTLS finns det ingen särskild konfiguration som stöder den här funktionen, men programmet måste ange ett lokalt identifieringscertifikat för TLS-klientinstansen med *hjälp av nx_secure_tls_session_local_certificate_add tjänsten.* Om inget certifikat tillhandahålls av programmet, men fjärrservern använder klientcertifikatautentisering och begär ett certifikat, misslyckas DTLS-handskakningen. Certifikatet som tillhandahålls till DTLS-sessionen *med nx_secure_dtls_session_local_certificate_add* måste identifieras av fjärrservern för att DTLS-handskakningen ska kunna slutföras.

### <a name="client-certificate-authentication-for-tls-servers"></a>Klientcertifikatautentisering för TLS-servrar

DTLS-serverfallet för klientcertifikatautentisering är något mer komplext än DTLS-klientfallet eftersom funktionen är valfri. I det här fallet måste TLS-servern begära ett certifikat från den fjärranslutna TLS-klienten och sedan bearbeta CertificateVerify-meddelandet för att verifiera att fjärrklienten äger den matchande privata nyckeln och sedan måste servern kontrollera att certifikatet som tillhandahålls av klienten kan spåras till ett certifikat i det lokala betrodda certifikatarkivet.

I NetX Secure TLS Server-instanser styrs klientcertifikatautentisering *av nx_secure_dtls_server_x509_client_verify_configure* och *nx_secure_dtls_server_x509_client_verify_disable* tjänster.

Om du vill aktivera autentisering med klientcertifikat måste *ett program anropa nx_secure_dtls_server_x509_client_verify_configure* med DTLS-serversessionsinstansen innan det *anropar nx_secure_dtls_server_start*. Verifieringen kräver att utrymme allokeras för inkommande klientcertifikat som tillhandahålls som en parameter för *nx_secure_dtls_server_x509_client_verify_configure.* Observera att bufferten måste vara tillräckligt stor för att innehålla certifikatkedjan för maximal storlek som tillhandahålls av en klient gånger antalet *DTLS-serversessioner.* Varje serversession kräver utrymme som allokeras från den enda angivna bufferten. Kontrollera att bufferten är tillräckligt stor eller att ett fel inträffar om den angivna klientcertifikatkedjan är för stor.

När Klientcertifikatautentisering är aktiverat begär DTLS-servern ett certifikat från DTLS-fjärrklienten under DTLS-handskakningen. I NetX Secure DTLS Server kontrolleras klientcertifikatet mot arkivet med betrodda certifikat som skapats *med nx_secure_dtls_server_trusted_certificate_add* genom att följa X.509-utfärdarkedjan. Fjärrklienten måste tillhandahålla en kedja som ansluter dess identitetscertifikat till ett certifikat i det betrodda arkivet, annars misslyckas DTLS-handskakningen. Om meddelandebearbetningen av CertificateVerify misslyckas misslyckas dessutom DTLS-handskakningen.

Signaturmetoderna som används för CertificateVerify-metoden är fasta för TLS version 1.0 och TLS version 1.1 och anges av TLS-servern i TLS version 1.2, där NetX Secure DTLS baseras. För DTLS 1.2 följer signaturmetoderna som stöds vanligtvis de relevanta metoder som anges i kryptografimetodtabellen, men vanligtvis RSA med SHA-256 (se avsnittet "Kryptografi i NetX Secure TLS" för mer information om hur du initierar TLS med kryptografiska metoder).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografi i NetX Secure TLS

TLS definierar ett protokoll där kryptografi kan användas för att skydda nätverkskommunikationen. Därför lämnar den faktiska kryptografin öppen för TLS-användare. Specifikationen kräver endast att ett enda chiffer implementeras – när det gäller TLS 1.2 är chiffersuite TLS_RSA_WITH_AES_128_CBC_SHA, vilket anger användningen av RSA för åtgärder med offentlig nyckel, AES i CBC-läge med 128-bitars nycklar för sessionskryptering och SHA-1 för meddelandeautentiseringshasher.

Eftersom NetX Secure är TLS 1.2-kompatibelt möjliggör det obligatoriska TLS_RSA_WITH_AES_128_CBC_SHA-chifferet som standard, men med tanke på antalet möjliga implementeringar för var och en av de kryptografiska metoderna på grund av maskinvarufunktioner och andra överväganden, tillhandahåller NetX Secure ett allmänt kryptografiskt API som gör att en användare kan ange vilka kryptografiska metoder som ska användas med TLS.

> [!NOTE]
> Den allmänna kryptografiska API-mekanismen gör det också möjligt för användare att implementera sina egna chiffer, men detta rekommenderas för avancerade användare som är bekanta med TLS-chiffer och tillägg. Kontakta din Express Logic-representant om du är intresserad av att stödja dina egna chiffer.

Se netX Secure TLS användarhandbok, kapitel 3 för en detaljerad diskussion om hur du konfigurerar kryptografiska metoder för DTLS. Samma process gäller för både TLS och DTLS.
