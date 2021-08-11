---
title: Kapitel 3 – Funktionell beskrivning av Azure RTOS NetX Secure
description: Det här kapitlet innehåller en funktionell beskrivning av NetX Secure TLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 711195e60771ebd467c69df49ef7665f32e13a17c21ca839404e829449cf1401
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797977"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-secure"></a>Kapitel 3 – Funktionell beskrivning av Azure RTOS NetX Secure

## <a name="execution-overview"></a>Körningsöversikt

Det här kapitlet innehåller en funktionell beskrivning av Azure RTOS NetX Secure TLS. Det finns två primära typer av programkörning i ett NetX Secure TLS-program: initiering och anrop till programgränssnitt. 

*NetX Secure förutsätter att ThreadX och NetX/NetXDuo finns. Från ThreadX krävs trådkörning, stängning, periodiska timers och ömsesidig exkludering. Från NetX/NetXDuo krävs TCP/IP-nätverksfunktioner och drivrutiner.*

## <a name="transport-layer-security-tls-and-secure-sockets-layer-ssl"></a>Transport Layer Security (TLS) och Secure Sockets Layer (SSL)

Den säkra nätverksprotokollkomponenten i NetX secure är en implementering av Transport Layer Security-protokollet (TLS) enligt beskrivningen i RFCs 2246 (version 1.0), 4346 (version 1.1), 5246 (version 1.2) och 8446 (version 1.3). Dessutom ingår supportrutiner för grundläggande X.509 (RFC 5280).

NetX Secure TLS stöder TLS-versionerna 1.2 och 1.3. Implementeringar tillhandahålls för de nu föråldrade TLS 1.0 och TLS 1.1, men de måste initieras explicit och rekommenderas inte för användning i nya produkter.

*Secure Sockets Layer* (SSL) var det ursprungliga namnet på TLS innan det blev en standard i RFC 2246 och "SSL" används ofta som ett allmänt namn för TLS-protokollen. Den senaste versionen av SSL var 3.0 och TLS 1.0 kallas ibland SSL version 3.1. Alla versioner av det officiella SSL-protokollet betraktas som föråldrade och osäkra, och netX Secure tillhandahåller för närvarande ingen SSL-implementering.

TLS anger ett protokoll för att generera *sessionsnycklar* som skapas under TLS-handskakningen mellan en TLS-klient och -server och dessa nycklar används för att kryptera data som skickas av programmet under  TLS-sessionen. 

TLS-data är *indelade i* poster som i begrepp motsvarar ett TCP-paket. Varje TLS-post har ett -huvud och TLS-krypterade poster har också en sidfot (hash för kontrollsumma). TLS-handskakningsposter har ytterligare en rubrik inkapslad i den större TLS-posten. TLS-posten kapslas in av transportlagrets nätverksprotokoll på samma sätt som ett TCP-paket kapslas in av ett IP-paket.

### <a name="tls-13"></a>TLS 1.3

I augusti 2018 slutförs TLS 1.3-specifikationen. Den nya versionen av protokollet är en ganska viktig uppdatering som ändrar vissa grundläggande aspekter av den underliggande säkerheten och prestandan hos TLS. Dessa ändringar är dock i stort sett osynliga för den typiska TLS-användaren eftersom de främst gäller för TLS-handskakningstillståndsdatorn och genereringen av sessionsnyckel. Ett antal valfria funktioner och tillägg har också lagts till. Följande är en sammanfattning av ändringarna och hur de påverkar TLS-funktionen.

- Handskakningstillståndsdatorn optimerades genom att ta bort ett helt utbyte av meddelanden från servern.
- Nyckelgenereringen har uppdaterats för att använda en standardiserad rutin som kallas HKDF (HMAC-baserad nyckelgenereringsfunktion) och kopplar sessionsnycklarna till alla handskakningsmeddelanden (i stället för några få utvalda parametrar).
- Alla TLS 1.2 och tidigare chiffer är inaktuella och är inkompatibla med TLS 1.3. På samma sätt är alla TLS 1.3-chiffer oanvändbara med tidigare versioner.
- Alla TLS 1.3-chiffer ger PFS (Perfect Forward Secrecy) med tillfälliga nycklar<sup>6</sup> 
- TLS 1.3 tar bort "meddelandeautentiseringskoden" (MAC) i varje post och använder AEAD<sup>7-chiffer</sup>
- Några ytterligare valfria funktioner har lagts till, inklusive 0-RTT (noll tur och retur-tid) som gör att programdata kan skickas under handskakningen. 0-RTT är helt valfritt och stöds för närvarande inte i Azure RTOS TLS.

TLS 1.3 påverkar inte användarprogram i någon större utsträckning. API:et är exakt detsamma mellan versionerna och chiffersuiter markeras så att en enda chiffertabell kan användas.

För att kunna använda TLS 1.3 måste NX_SECURE_TLS_ENABLE_TLS_1_3 definieras globalt. TLS 1.3 är inaktiverat som standard i Azure RTOS TLS.

6. "Tillfälliga" nycklar är asymmetriska nyckelpar som genereras under TLS-handskakningen och som endast används för utbyte av hemligheter för den sessionen. Nyckelparet tas bort efter användning – detta förhindrar att en angripare kan komma åt krypterade data i en registrerad TLS-session även om en privat certifikatnyckel komprometteras när som helst i framtiden – därav "Perfect Forward Secrecy".

7. Autentiserad kryptering med associerade data – ett läge för chiffer som AES som kombinerar kryptering och integritetskontroll i en enda åtgärd, vilket eliminerar behovet av en separat hash av data för integritetskontroll.

### <a name="tls-record-header"></a>TLS-postrubrik

Alla giltiga TLS-poster måste ha ett TLS-huvud, som du ser i Fel! Det går inte att hitta referenskällan.

![Diagram över ett TLS-posthuvud.](media/image2.png)

Bild 1 – TLS-postrubrik

Fälten i TLS-postrubriken definieras på följande sätt:

| TLS-rubrikfält | Syfte     |
| ---------------- | ------------- |
| **8-bitars meddelandetyp** | Det här fältet innehåller typen av TLS-post som skickas. Giltiga typer är följande:<br />– ChangeCipherSpec<sup>8:</sup>0x14<br />– Avisering: 0x15<br />– Handskakning: 0x16<br />– Programdata: 0x17 |
| **16-bitars protokollversion** | Det här fältet innehåller TLS-protokollversionen. Giltiga värden är följande:<br />– SSL 3.0: 0x0300<br />– TLS 1.0: 0x0301<br />– TLS 1.1: 0x0302<br />– TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>9:</sup>** **0x0303** |
| **16-bitars längd** | Det här fältet innehåller längden på de data som är inkapslade i TLS-posten. |

8. I TLS 1.3 används inte längre ChangeCipherSpec-meddelandet, även om det fortfarande kan skickas av kompatibilitetsskäl. Då ignoreras meddelandet.

9. TLS 1.3 skulle tekniskt sett ha värdet 0x0304 om det här schemat har fortsatt, men protokollet har ändrats till att ha den faktiska protokollversionen i ett tillägg, så alla TLS 1.3-poster använder 0x0303 i protokollversionsfält för bakåtkompatibilitet.

### <a name="tls-handshake-record-header"></a>TLS-handskakningspostrubrik

En giltig TLS-handskakningspost måste ha ett TLS Handshake-huvud, som du ser i bild 2.

![Diagram över ett TLS Handshake-posthuvud.](media/image3.png)

Bild 2 – Postrubrik för TLS-handskakning

Fälten i TLS Handshake-postrubriken definieras på följande sätt:

| TLS-rubrikfält | Syfte |
| ---------------- |----------------------- |
| **8-bitars meddelandetyp** | Det här fältet innehåller typen av TLS-post som skickas. Giltiga typer är följande:<br />– ChangeCipherSpec<sup>10:</sup>0x14<br />– Avisering: 0x15<br />– Handskakning: 0x16<br />– Programdata: 0x17 |
| **16-bitars protokollversion** | Det här fältet innehåller TLS-protokollversionen. Giltiga värden är följande:<br />– SSL 3.0: 0x0300<br />– TLS 1.0: 0x0301<br />– TLS 1.1: 0x0302<br />– TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>11:</sup>** **0x0303** |
| **16-bitars längd**    | Det här fältet innehåller längden på de data som är inkapslade i TLS-posten. |
| **8-bitars handskakningstyp** | Det här fältet innehåller meddelandetypen handskakning. Giltiga värden är följande (*meddelanden i **fetstil lades** till i TLS 1.3):<br />- HelloRequest: 0x00<br />– ClientHello: 0x01<br />– ServerHello: 0x02<br />- **HelloVerifyRequest:** **0x03**<br />- **NewSessionTicket:** **0x04**<br />- **EndOfEarlyData:** **0x05**<br />- **EncryptedExtensions:** **0x08**<br />– Certifikat: 0x0B<br />– ServerKeyExchange: 0x0C<br />– CertificateRequest: 0x0D<br />– ServerHelloDone: 0x0E<br />– CertificateVerify: 0x0F<br />– ClientKeyExchange: 0x10<br />– Klart: 0x14<br />- **KeyUpdate:** **0x18**<br />- **MessageHash:** **0xFE** |
| **24-bitars längd**    | Det här fältet innehåller längden på handskakningens meddelandedata. |

10. I TLS 1.3 används inte längre ChangeCipherSpec-meddelandet, även om det fortfarande kan skickas av kompatibilitetsskäl. Då ignoreras meddelandet.

11. TLS 1.3 skulle tekniskt sett ha värdet 0x0304 om schemat har fortsatt, men protokollet har ändrats till att ha den faktiska protokollversionen i ett tillägg, så alla TLS 1.3-poster använder 0x0303 i protokollversionsfält för bakåtkompatibilitet.

### <a name="the-tls-handshake-and-tls-session"></a>TLS-handskakningen och TLS-sessionen

En typisk TLS-handskakning (version 1.0-1.2) visas i bild 3. En TLS-handskakning börjar när TLS-klienten skickar ett *ClientHello-meddelande* till en TLS-server som anger att den vill starta en TLS-session. Meddelandet innehåller information om krypteringen som klienten vill använda för sessionen, tillsammans med information som används för att generera sessionsnycklarna senare i handskakningen. Alla meddelanden i TLS-handskakningen krypteras inte förrän sessionsnycklarna har genererats. TLS 1.3 ändrar handskakningen något – informationen visas i nästa avsnitt.

TLS-servern svarar på ClientHello med ett ServerHello-meddelande som anger ett val från de krypteringsalternativ som tillhandahålls av klienten. ServerHello följs av ett certifikatmeddelande där servern tillhandahåller ett digitalt certifikat för att autentisera sin identitet till klienten. Slutligen skickar servern ett ServerHelloDone-meddelande för att indikera att den inte har några fler meddelanden att skicka. Servern kan också skicka andra meddelanden efter ServerHello och i vissa fall kanske den inte skickar ett certifikatmeddelande, därav behovet av ServerHelloDone-meddelandet.

När klienten har tagit emot alla serverns meddelanden har den tillräckligt med information för att generera sessionsnycklarna. TLS gör detta genom att skapa en delad bit slumpmässiga data som kallas *För master-hemlighet,* som är en fast storlek och används som start för att generera alla nycklar som behövs när kryptering har aktiverats. Hemligheten före huvudnyckeln krypteras med hjälp av algoritmen för offentlig nyckel (t.ex. RSA) som anges i Hello-meddelanden (se nedan för information om algoritmer för offentliga nycklar) och den offentliga nyckel som tillhandahålls av servern i certifikatet. En valfri TLS-funktion som kallas I förväg delade nycklar (PSK) möjliggör chiffer som inte använder ett certifikat utan istället använder ett hemligt värde som delas mellan värdarna (vanligtvis via fysisk överföring eller annan skyddad metod). Den delade hemligheten används för att generera för master-hemligheten i stället för att använda ett krypterat meddelande för att skicka för masterhemligheten. Se avsnittet om i förväg delade nycklar nedan.

Den krypterade för masterhemligheten skickas till servern i ClientKeyExchange-meddelandet. När servern tar emot ClientKeyExchange-meddelandet dekrypterar den förinstallerade hemligheten med hjälp av den privata nyckeln och fortsätter att generera sessionsnycklarna parallellt med TLS-klienten.

När sessionsnycklarna har genererats kan alla ytterligare meddelanden krypteras med hjälp av algoritmen för privat nyckel (t.ex. AES) som valts i Hello-meddelandena. Ett sista okrypterat meddelande med namnet ChangeCipherSpec skickas av både klienten och servern för att indikera att alla ytterligare meddelanden kommer att krypteras.

Det första krypterade meddelandet som skickas av både klienten och servern är också det slutliga TLS-handskakningsmeddelandet med namnet Finished (Slutfört). Det här meddelandet innehåller en hash för alla handskakningsmeddelanden som tas emot och skickas. Denna hash används för att verifiera att inget av meddelandena i handskakningen har manipulerats eller skadats (vilket indikerar en möjlig säkerhetsöverträdelse).

När slutförda meddelanden tas emot och handskakningshashar verifieras börjar TLS-sessionen och programmet börjar skicka och ta emot data. Alla data som skickas av endera sidan under TLS-sessionen hashas först med hjälp av den hash-algoritm som valts i Hello-meddelanden (för att tillhandahålla meddelandeintegritet) och krypteras med hjälp av den valda algoritmen för privat nyckel med de genererade sessionsnycklarna.

Slutligen kan en TLS-session endast avslutas om antingen klienten eller servern väljer att göra det. En trunkerad session betraktas som ett säkerhetsintrång (eftersom en angripare kan försöka förhindra att alla data skickas från att tas emot) så ett särskilt meddelande skickas när någon av sidorna vill avsluta sessionen, vilket kallas en CloseNotify-avisering. Både klienten och servern måste skicka och bearbeta en CloseNotify-avisering för en lyckad sessionsavstängning.

![Diagram över en typisk TLS-handskakning.](media/image4.png)

Bild 3 – Typisk TLS-handskakning

### <a name="tls-13-handshake"></a>TLS 1.3 Handshake

TLS 1.3 är en ganska stor genomgång av TLS-protokollet. Merparten av ändringarna har gjorts i handskakningen för att öka säkerheten och prestandan. En typisk TLS 1.3-handskakning visas i bild 4. Den största skillnaden kan ses i antalet utbyten mellan servern och klienten.

I TLS 1.2 och tidigare skulle servern skicka två flighter<sup>med 12</sup> meddelanden – först ServerHello och sedan ett ChangeCipherSpec-meddelande innan det krypterade slutförda meddelandet som avslutar handskakningen skickas. I TLS 1.3 skickar servern allt i den första flygresan – ServerHello, tillägg, certifikat och Finished . ChangeCipherSpec-meddelandet har tagits bort och servern genererar sina sessionsnycklar och börjar kryptera handskakningsmeddelanden direkt efter ServerHello.

Det nya arrangemanget innebär att mer av TLS-handskakningen skyddas av kryptering, vilket begränsar mängden klartextdata som en angripare kan komma åt. Dessutom innebär borttagningen av den andra serverresan (som bara var en ChangeCipherSpec följt av en Slutförd) att en TLS-klient inte längre behöver vänta på att börja överföra programdata – så snart klienten skickar ett eget slutfört meddelande startas sessionen.

12. En flygresa är helt enkelt en samling TLS-meddelanden som skickas samtidigt i en grupp.

![Diagram över en TLS 1.3-handskakning.](media/image5.png)

Bild 4 – TLS 1.3 Handskakning

> [!NOTE]
> *TLS 1.3 introducerade också begreppet "tidiga data" och 0-RTT (noll tur och retur), vilket innebär att vissa programdata kan skickas i den första meddelanderesan. Den här valfria funktionen har främst lagts till som en optimering för webbläsarens svarstider (t.ex. för att skicka tidiga HTTP-huvuden för att börja återge en sida). Från och Azure RTOS 6.0 stöds inte den här funktionen.*

### <a name="initialization"></a>Initiering

NetX- eller NetXDuo TCP/IP-stacken måste initieras innan du använder NetX Secure TLS. Se användarhandboken för NetX eller NetXDuo för information om hur du initierar TCP/IP-stacken korrekt.

När NetX TCP/IP-stacken har initierats kan TLS aktiveras. Internt hanteras all TLS-nätverkstrafik och -bearbetning av NetX/NetXDuo-stacken utan att användaren behöver göra något. TLS har dock vissa specifika krav som måste hanteras separat från den underliggande nätverksstacken. Dessa parametrar tilldelas till TLS-kontrollblocket med namnet ***NX_SECURE_TLS_SESSION** _ med hjälp av tjänsten _ *_nx_secure_tls_session_create_** .

TLS har två lägen: Server och Klient, som båda kan aktiveras i ett program (men endast ett läge per NetX-socket) och var och en har sina egna specifika krav, som beskrivs nedan.

I båda lägena kräver NetX Secure TLS att en TCP-socket (***NX_TCP_SOCKET** _) skapas och konfigureras för TCP-kommunikation med fjärrvärden. TCP-socketen tilldelas till en TLS-sessionsinstans med tjänsten _ *_nx_secure_tls_session_start_** enligt beskrivningen nedan.

### <a name="initialization--tls-server"></a>Initiering – TLS-server

Förutom en TCP-socket kräver NetX Secure TLS-serverläget ett digitalt certifikat *,* som är ett dokument som används för att identifiera TLS-servern för den anslutande TLS-klienten och certifikaten motsvarande privat nyckel *,* vanligtvis för RSA-krypteringsalgoritmen. Standarden International Telecommunications Union X.509 anger det certifikatformat som används av TLS och det finns flera verktyg för att skapa digitala X.509-certifikat.

För NetX Secure TLS måste X.509-certifikatet vara binärt kodat med asn.1-formatet (Distinguished Encoding Rules DER). DER är standardformatet för TLS over-the-wire binary för certifikat.

Den privata nyckeln som är associerad med det angivna certifikatet måste vara i DER-Encoded PKCS#1-format. Den privata nyckeln används bara på enheten och överförs aldrig via kabel. Skydda privata nycklar eftersom de ger säkerhet för TLS-kommunikation!

För att initiera TLS-servercertifikatet måste programmet ange en pekare till en buffert som innehåller de DER-kodade X.509-certifikatet och valfria DER-kodade PKCS#1 RSA privata nyckeldata med hjälp av tjänsten ***nx_secure_x509_certificate_intialize** _ som fyller i strukturen _ *NX_SECURE_X509_CERT** med lämpliga certifikatdata för användning av TLS.

När servercertifikatet har initierats måste det läggas till i TLS-kontrollblocket med hjälp ***av nx_secure_tls_local_certificate_add tjänsten.***

När serverns certifikat har lagts till i TLS-kontrollblocket kan socketen användas för att upprätta en säker TLS-serveranslutning.

### <a name="initialization--tls-client"></a>Initiering – TLS-klient

NetX Secure TLS-klientläge kräver ett betrott certifikatarkiv *,* som är en samling X.509-kodade digitala certifikat från betrodda certifikatutfärdare (CA:er). Dessa certifikat antas av TLS-protokollet vara "betrodda" och utgör grunden för autentisering av certifikat som tillhandahålls av TLS-serverentiteter till NetX Secure TLS-klienten.

Ett betrott *CA-certifikat* kan antingen vara själv signerat eller signerat av en annan certifikatutfärdare, i vilket fall det certifikatet kallas en *mellanliggande CA* (ICA). I ett typiskt TLS-program tillhandahåller servern ICA-certifikat tillsammans med dess servercertifikat, men det enda kravet för lyckad autentisering är att en kedja med utfärdare (certifikat som används för att signera andra certifikat) kan spåras från servercertifikatet tillbaka till ett betrott CERTIFIKATutfärdarcertifikat i det betrodda certifikatarkivet. Den här kedjan kallas för en  *kedja av förtroende eller* *certifikatkedja*.

För att initiera en betrodd certifikatutfärdare eller ett ICA-certifikat måste programmet ange en pekare till en buffert som innehåller det DER-kodade X.509-certifikatet med tjänsten ***nx_secure_x509_certificate_intialize** _ som fyller strukturen _ *NX_SECURE_X509_CERT** med lämpliga certifikatdata för användning av TLS.

Betrodda certifikat som har initierats läggs sedan till  i TLS-kontrollblocket med hjälp av nx_secure_tls_trusted_certificate_add tjänsten. Om du inte lägger till ett certifikat misslyckas TLS-klientsessionen eftersom det inte finns något sätt för TLS-protokollet att autentisera TLS-fjärrservervärdar.

TLS-klienten behöver också utrymme för att det inkommande servercertifikatet ska allokeras (förutsatt att läget Fördelade nycklar inte används). Från och med NetX Secure TLS 5.12 är det inte längre nödvändigt att programmet allokerar utrymme för fjärrcertifikat. Det äldre alternativet för att allokera utrymme för ett servercertifikat är dock fortfarande tillgängligt och användar allokerade certifikat kommer att användas före den interna optimeringen av certifikatbufferten <sup>13</sup> . Mer information ***finns i nx_secure_tls_remote_certificate_allocate tjänsten.***

När det betrodda certifikatarkivet har skapats och utrymmet för servercertifikatet har allokerats kan socketen användas för att upprätta en säker TLS-klientanslutning.

13. Optimeringen använder den "paketbuffert" som tillhandahålls av användarprogrammet till TLS-sessionen med *hjälp av nx_secure_tls_session_packet_buffer_set* för att allokera X.509-parsningsstrukturerna i stället för att använda de strukturer som anges av användaren i tidigare versioner av NetX Secure TLS. Det är osannolikt att en certifikatkedja överskrider storleken på paketbufferten. Då kan paketbuffertens storlek ökas eller *så kan nx_secure_tls _remote_certificate_allocate* användas för att allokera mer utrymme för certifikatkedjan.

### <a name="application-interface-calls"></a>Anrop till programgränssnitt

NetX Secure TLS-program gör vanligtvis funktionsanrop inifrån programtrådar som körs under ThreadX RTOS. Viss initiering, särskilt för de underliggande protokollen för nätverkskommunikation (t.ex. TCP och IP) kan anropas från ***tx_application_define*.** Mer information om hur du initierar nätverkskommunikation finns i användarhandboken för NetX/NetXDuo.

TLS använder krypteringsrutiner som är processorintensiva åtgärder. I allmänhet utförs dessa åtgärder inom kontexten för anrop av tråd.

### <a name="tls-session-start"></a>Start av TLS-session

TLS kräver ett underliggande transportlagernätverksprotokoll för att fungera. Protokollet som vanligtvis används är TCP. För att upprätta en NetX Secure TLS-session måste en TCP-anslutning upprättas med hjälp av NETX/NetXDuo TCP API. En **NX_TCP_SOCKET** måste skapas och en anslutning upprättas med hjälp av tjänsterna nx_tcp_server_socket_listen _ och ***_*_nx_tcp_server_socket_accept_*_ (för TLS-server)*** eller tjänsten _ nx_tcp_client_socket_connect (för TLS-klienten).

När en TCP-anslutning har upprättats skickas TCP-socketen till ***nx_secure_tls_session_start tjänsten.***

### <a name="tls-packet-allocation"></a>TLS-paketallokering

NetX Secure TLS använder samma paketstruktur som NetX/NetXDuo TCP (***NX_PACKET** _) förutom att i stället för att anropa _*_nx_packet_allocate-tjänsten_*_ måste tjänsten _ *_nx_secure_tls_packet_allocate_** anropas så att utrymmet för TLS-huvudet kan allokeras korrekt.

### <a name="tls-session-send"></a>Skicka TLS-session

När TLS-sessionen har startat kan programmet skicka data med hjälp av tjänsten ***nx_secure_tls_session_send** _ . Den skickande tjänsten används identiskt med _*_nx_tcp_socket_send-tjänsten_*_ och tar en _*_NX_PACKET-datastruktur_*_ som innehåller de data som skickas. Endast dessa data krypteras av NX Secure TLS-stacken innan de skickas och paketet måste allokeras med hjälp av _*_nx_secure_tls_packet_allocate_**.

### <a name="tls-session-receive"></a>Mottagning av TLS-session

När TLS-sessionen har startat kan programmet börja ta emot data med hjälp av tjänsten ***nx_secure_tls_session_receive** _ . Precis som TLS-sessionen skickar är den här tjänsten identisk med _*_nx_tcp_socket_receive_**, förutom att inkommande data dekrypteras och verifieras av TLS-stacken innan de returneras i paketstrukturen.

### <a name="tls-session-close"></a>Stängning av TLS-session

När en TLS-session är klar måste både TLS-klienten och servern skicka en CloseNotify-avisering till den andra sidan för att stänga av sessionen. Båda sidor måste ta emot och bearbeta aviseringen för att säkerställa en lyckad sessionsavstängning.

Om fjärrvärden skickar en CloseNotify-avisering bearbetar alla anrop till tjänsten ***nx_secure_tls_session_receive** _ aviseringen, skickar motsvarande avisering tillbaka till fjärrvärden och returnerar värdet _*_NX_SECURE_TLS_SESSION_CLOSED_**. När sessionen har stängts misslyckas eventuella ytterligare försök att skicka eller ta emot data med den TLS-sessionen.

Om programmet vill stänga TLS-sessionen måste tjänsten ***nx_secure_tls_session_end** _ anropas. Tjänsten skickar CloseNotify-aviseringen och bearbetar svaret CloseNotify. Om svaret inte tas emot returneras felvärdet _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_** som anger att TLS-sessionen inte har stängts av korrekt, vilket är ett möjligt säkerhetsintrång.

### <a name="tls-alerts"></a>TLS-aviseringar

TLS är utformat för att ge maximal säkerhet, så alla avvikande beteenden i protokollet anses vara en potentiell säkerhetsöverträdelse. Därför betraktas eventuella fel vid meddelandebearbetning eller kryptering/dekryptering som allvarliga fel som avslutar handskakningen eller sessionen omedelbart.

Det är relativt enkelt att hantera fel i ett lokalt program, men fjärrvärden måste känna till att ett fel har uppstått för att kunna hantera situationen korrekt och förhindra eventuella säkerhetsöverträdelser. Därför skickar TLS ett *aviseringsmeddelande till* fjärrvärden vid eventuella fel.

Aviseringar behandlas på samma sätt som andra TLS-meddelanden och krypteras under sessionen för att förhindra att en angripare samlar in information från den typ av avisering som tillhandahålls. Under handskakningen är de aviseringar som skickas begränsade i omfånget för att begränsa mängden information som kan hämtas av en potentiell angripare.

CloseNotify-aviseringen, som används för att stänga TLS-sessionen, är den enda icke-allvarliga aviseringen. Även om det betraktas som en avisering och skickas som ett aviseringsmeddelande, skiljer sig CloseNotify från andra aviseringar på så sätt att det inte indikerar att ett fel har uppstått.

Aviseringsvärdet och "nivå" (nivåerna är "varning" och "allvarligt" – de flesta TLS-aviseringar är "allvarliga") definieras i TLS-rfc:erna och anger vilken typ av fel som har inträffat. De flesta andra TLS-aviseringar än CloseNotify kan betraktas som en indikation på ett potentiellt säkerhetsproblem och resulterar i att TLS-sessionen eller handskakningen avbryts. Om ett TLS API-anrop returnerar **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) kan API-tjänsten **_nx_secure_tls_session_alert_value_get_** (ny i NetX Secure TLS version 5.12) användas för att hämta TLS-aviseringsvärdet och TLS-nivån som programmet kan använda för beslut om svar på säkerhetsproblem. I de flesta fall bör alla aviseringar som tas emot från fjärrvärden förutom CloseNotify betraktas som ett allvarligt fel, även om det finns vissa avbrott – mer information finns i TLS RFCs.

### <a name="tls-session-renegotiation"></a>Omförhandling av TLS-session

TLS stöder begreppet "omförhandling", vilket helt enkelt är en omförhandling av TLS-sessionsparametrarna i kontexten för en befintlig TLS-session. Det innebär i praktiken att de nya handskakningsmeddelandena krypteras och autentiseras med hjälp av den befintliga sessionen. Omförhandling används när en TLS-värd vill generera nya sessionsparametrar (t.ex. generera nya TLS-sessionsnycklar) utan att behöva slutföra den befintliga sessionen. Omförhandling kan till exempel vara önskvärt om säkerhetsprinciper för ett program kräver att sessionsnycklar endast används under en begränsad tid, men en TLS-session förblir aktiv efter den tiden.

Ett problem med omförhandling av sessioner är att gör TLS sårbart för en specifik Man-in-the-Middle-attack där en angripare kan övertyga en server att initiera en omförhandling med nya parametrar, vilket gör att angriparen kan kapa TLS-sessionen. För att åtgärda det här problemet introducerades tillägget Secure Renegotiation Indication (Säker omförhandlingsindikation) (se **avsnittet Fel! Det går inte att hitta referenskällan.** -avsnittet).

NetX Secure TLS har fullständigt stöd för omförhandling av sessioner och tillägget Secure Renegotiation Indication.

När du tar emot data från en fjärrvärd hanteras omförhandlingar (och tillägget) automatiskt utan interaktion med programmet. Om du vill få ett meddelande om omförhandling av sessioner kan ett återanrop för omförhandling tillhandahållas *med nx_secure_tls_session_renegotiate_callback_set tjänsten.* Återanropet anropas när en omförhandling begärs av fjärrvärden, vilket gör att programmet kan vidta åtgärder om det behövs.

Om du vill initiera en omförhandling från en aktiv TLS-session anropar du *bara nx_secure_tls_session_renegotiate-tjänsten* i den önskade TLS-sessionen.

### <a name="tls-session-resumption"></a>Återupptagande av TLS-session

Återupptagande av TLS-session bör inte förväxlas med omförhandling av sessioner, trots vissa likheter. Om *omförhandling* av session innebär att starta en ny handskakning i en befintlig TLS-session är återaktivering av *session* en helt valfri funktion som innebär att starta om en stängd TLS-session utan att utföra en fullständig TLS-handskakning. För att uppnå detta kan en TLS-implementering cachelagra sessionsparametrarna och nycklarna och associera dem med ett *sessions-ID,* en unik identifierare som angavs i den ursprungliga handskakningen. Genom att ange ett sessions-ID till en TLS-server anger en klient att en tidigare TLS-session mellan värdarna fanns och slutfördes en tid tidigare och att klienten fortfarande har tillståndet att återupprätta sessionen med en minskad handskakning. Eftersom sessionsnycklarna teoretiskt sett fortfarande är hemliga och endast kända av de två kommunicerande värdarna kan servern starta en ny TLS-session och kringgå det mesta av den normala handskakningen.

Att återuppta sessionen kan vara användbart för att undvika de potentiellt dyra åtgärderna för offentliga nycklar som används för att dela huvudhemligheten för nyckelgenerering och verifiera certifikatsignaturer, men det kräver också att sessionsparametrarna, nycklarna och kryptografitillståndet bevaras i minnet för alla möjliga sessioner (åtminstone under en konfigurerbar tidsperiod).

Den aktuella versionen av NetX Secure TLS stöder inte återupptagande av session – sessions-ID ignoreras helt enkelt av TLS-servrar och TLS-klienter tillhandahåller alltid ett NULL-sessions-ID som uppmanar servern att utföra en fullständig handskakning. Bristen på sessionssammanslagning bör inte orsaka problem med samverkan eftersom det är en helt valfri funktion och alla TLS-implementeringar måste som standard utföra en fullständig handskakning om sessions-ID:t är NULL eller okänt.

### <a name="protocol-layering"></a>Protokollskiktning

TLS-protokollet passar in i nätverksstacken mellan transportlagret (t.ex. TCP) och programlagret. TLS anses ibland vara ett transportlagerprotokoll (därav *Transport Layer* Security), men eftersom det fungerar som ett program med avseende på de underliggande nätverksprotokollen (till exempel TCP) grupperas det ibland i programlagret.

TLS kräver ett transportlagerprotokoll som stöder i ordningsföljd och förlustfri leverans, till exempel TCP. På grund av detta krav kan TLS inte köras ovanpå UDP eftersom UDP inte garanterar leverans av datagram. Ett separat protokoll som kallas *DTLS,* som är en modifierad version av TLS, används för program som behöver säkerhet för TLS över ett datagramprotokoll som UDP. NetX Secure stöder DTLS, men dokumentationen för DTLS är separat från det här dokumentet.

![Diagram över tcp/IP- och TLS-protokollskikt.](media/image6.png)

Bild 5 – TCP/IP- och TLS-protokolllager

## <a name="network-communications-security"></a>Säkerhet för nätverkskommunikation

Att skydda kommunikationen över offentliga nätverk och Internet är ett ytterst viktigt ämne och ämnet för ett stort antal böcker, artiklar och lösningar. Ämnet är mind-torigt komplext, men kan reduceras till en enkel idé: skicka information via ett nätverk så att endast det avsedda målet kan komma åt eller ändra informationen. Detta går in i tre viktiga begrepp: sekretess, integritet och autentisering. TLS-protokollet innehåller lösningar för alla tre.

### <a name="secrecy"></a>Sekretess

När du skickar data via ett nätverk är det ofta viktigt att data inte kan hämtas av en skadlig entitet. Om data skickas via en TCP/IP-anslutning kan alla med åtkomst till nätverket läsa dessa data med hjälp av nätverksverktyg som är enkla att använda. För att förhindra att data hämtas måste de kodas så att de inte kan läsas förutom av det avsedda målet – detta är *sekretess.* I TLS ger krypteringsalgoritmer som RSA och AES sekretess.

### <a name="integrity"></a>Integritet

Ibland räcker det inte med sekretess för att skydda data i ett nätverk. I vissa fall kan det vara möjligt för en illvillig entitet att ändra innehållet i ett TCP-paket utan att behöva veta vad paketet innehåller. Krypterade data kan ändras, vilket gör dekrypteringen ogiltig eller ändrar parametrarna för meddelandet, vilket leder till det resultat som angriparen kan vara intresserad av att uppnå. I nätverket kan vi inte hindra en angripare från att ändra data under överföring, men vi kan tillhandahålla en mekanism för att veta om data har ändrats eller inte. När data ändras under överföring blir de kända och data kan avvisas. Det här konceptet *är integritet*. I TLS tillhandahålls integriteten av en klass med kryptografiska rutiner som kallas *hash-funktioner.* Några exempel på hash-funktioner är MD5 och SHA-1.

### <a name="authentication"></a>Autentisering

Det tredje viktiga konceptet inom nätverkskommunikationssäkerhet är tanken att data endast ska förmedlas till det avsedda målet. En angripare kan försöka utgöra en legitim entitet för att ta emot data som är avsedda för en annan värd. Även om data skickas med sekretess- och integritetsmekanismer på plats, kan angriparen fortfarande uppnå önskat resultat (en kompromettion av säker kommunikation) genom det här bedrägeriet. För att förhindra detta krävs en mekanism för att bevisa identiteten för en fjärrvärd innan känsliga data skickas. Processen för att bevisa identiteten för en fjärrvärd är *autentisering.* I TLS tillhandahålls autentisering med digitala certifikat, hash-funktioner och en mekanism som kallas *digitala signaturer* som använder en egenskap för kryptering med offentlig nyckel (beskrivs nedan). En begränsad men användbar form av autentisering kan också tillhandahållas med en *i förväg delad nyckel* (PSK).

## <a name="tls-encryption"></a>TLS-kryptering

TLS-protokollet är ett ramverk för att tillhandahålla säker nätverkskommunikation via Internet med hjälp av kryptering. Kryptering definieras vanligtvis som en process för att koda data på ett sätt som gör det mycket svårt att hämta ursprungliga data (eller information om dessa data) utan *en nyckel.* I datorsystem baseras krypteringen på komplex matematik som ändliga fält och kan klassificeras i två *typer:* privat nyckel *(eller symmetrisk* kryptering) och offentlig nyckel *(eller* *asymmetrisk kryptering).* Exempel på kryptering av privata nycklar är AES (Advanced Encryption Standard) och RC4 (Rivest Cipher 4). Exempel på kryptering med offentliga nycklar är RSA (Rivest, Shamir, Adleson) och Diffie-Hellman chiffer.

TLS-protokollet använder både krypteringsrutiner för privata nycklar och offentliga nycklar för att ge en balans mellan prestanda, säkerhet och flexibilitet.

### <a name="private-key-encryption"></a>Private-Key kryptering

Kryptering med privat nyckel har använts i tusentals år. Grundläggande ersättningschiffrering (där en bokstav eller ett ord ersätts med en annan orelaterad bokstav eller ett annat ord) är de tidigaste kända exemplen på kryptering, men med införandet av den privata nyckeln för informationsåldern har krypteringen förbättrats avsevärt.

En privat nyckelchiffrering använder en "nyckel" som helt enkelt är ett värde (som i allmänhet kan vara ett ord, en fras eller ett tal) som används för att koda vissa data på något sätt så att endast en entitet som har åtkomst till den nyckeln kan avkoda data på ett meningsfullt sätt. Nyckeln används för både kryptering och dekryptering av data, därav det andra namnet *symmetrisk kryptering*.

Chiffer med privata nycklar är vanligtvis snabba och ganska enkla att implementera, även om matematiken är mycket komplex. Därför använder TLS chiffer för privata nycklar för den största delen av säker kommunikation.

Kryptering med privat nyckel har dock problem när vi försöker tillämpa den på allmän nätverkskommunikation: nyckeln måste delas mellan båda datorerna som försöker kommunicera. I det allmänna fallet är det opraktiskt och ofta omöjligt att kommunicera en privat nyckel på ett säkert sätt mellan två datorer på Internet, eftersom det kan antas att nätverkstrafiken kan hämtas av ett antal entiteter i de olika hopp som data tar när de dirigeras via Internet. Om nyckeln hämtas av en skadlig entitet komprometteras alla data som krypterats med den nyckeln. Eftersom de flesta datorer på Internet bara har en nätverksanslutning och inte en annan säker kanal för kommunikation är det samma sak att skicka nycklar via nätverket för att skicka data okrypterade – det ger ingen säkerhet.

Därför räcker det inte med kryptering med privat nyckel för att implementera ett säkerhetsprotokoll för allmän nätverkskommunikation. Det är här kryptering med offentlig nyckel kan vara till hjälp.

NetX Secure TLS stöder kryptering med privat AES-nyckel.

### <a name="public-key-encryption"></a>Public-Key kryptering

Till skillnad från kryptering av privata nycklar är kryptering av offentliga nycklar ett ganska nytt begrepp, som utvecklades på 1970-talet. Med hjälp av ett begrepp som kallas "trap-door-funktioner" inom matematiken upptäcktes att det fanns ett sätt att dela en nyckel över ett nätverk utan att äventyra säkerheten för sedan krypterade data.

Krypteringen av offentliga nycklar fungerar på så sätt att nyckeln (i den krypteringssenyt för privata nycklar som beskrivs ovan) delas upp i två delar: en privat nyckel och en offentlig nyckel *,* där den offentliga nyckelkrypteringen får sitt namn.  Konceptet är att en av dessa nycklar (vanligtvis den offentliga nyckeln) används för kryptering, medan den andra används för dekryptering. Den här asymmetri med nycklar är orsaken till det andra namnet för kryptering av offentliga nycklar: *asymmetrisk kryptering*.

Matematiken bakom kryptering av offentliga nycklar är ganska komplex,  men tanken är att den offentliga nyckeln bara kan användas för kryptering, och att hämta den nyckeln tillåter inte att krypterade data hämtas. Den privata nyckeln är i sin tur det enda sättet att dekryptera data som krypteras med den offentliga nyckeln. Genom att hålla den privata nyckeln hemlig behöver alla som vill kommunicera säkert med ägaren av den privata nyckeln bara kryptera sina data med motsvarande offentliga nyckel med vetskapen att endast någon som har tillgång till den privata nyckeln kan hämta säkra data.

NetX Secure TLS stöder RSA-kryptering med offentlig nyckel.

> [!IMPORTANT] 
> *RSA är en mycket processorintensiv åtgärd om programvarans RSA-implementering används. Större nyckelstorlekar ökar bearbetningskraften som krävs av en kvadratisk faktor – 4 x långsammare för en 2X-ökning av nyckelstorleken.*

### <a name="public-key-authentication"></a>Public-Key autentisering

En intressant sidoeffekt av krypteringsbegreppet för offentliga nycklar är att den kan användas för att tillhandahålla  autentisering och kryptering genom att utföra åtgärden i omvänd ordning: kryptera med hjälp av den privata nyckeln och dekryptera med hjälp av den offentliga *nyckeln.* Den faktiska mekanismen för att göra detta beror på vilken algoritm för offentlig nyckel som används, men konceptet är detsamma.

För att autentisera med hjälp av autentisering med offentlig nyckel krypterar ägaren av en privat nyckel en del data (vanligtvis en kryptografisk hash av de data som ska autentiseras) med hjälp av den privata nyckeln. Sedan kan någon som vill autentisera att data kommer från ägaren av den privata nyckeln använda den associerade offentliga nyckeln för att dekryptera data – om dekrypteringen lyckas och förutsatt att användaren litar på giltigheten för den offentliga nyckeln kan användaren vara säker på att data kommer från ägaren av den privata nyckeln.

I TLS används autentisering med offentlig nyckel för att verifiera giltigheten för ett digitalt certifikat som tillhandahålls av en TLS-server (och eventuellt TLS-klienten) med hjälp av offentliga nycklar från det betrodda certifikatarkivet. Certifikatet kontrolleras mot en offentlig nyckel i arkivet och data i certifikatet används för att kontrollera serverns identitet.

NetX Secure TLS stöder RSA-autentisering.

### <a name="cryptographic-hashing"></a>Kryptografisk hashing

Kryptering är inte den enda kryptografiska åtgärd som används i TLS. För att kunna tillhandahålla meddelandeintegritet under en TLS-session krävs en kontrollsumma för att säkerställa att meddelandeinnehållet inte har manipulerats. En enkel kontrollsumma (som används i TCP) är dock inte tillräcklig för att garantera en acceptabel integritetsnivå eftersom den enkelt kan inverteras av en kunskapsbar angripare. Den mekanism som används av TLS för att tillhandahålla meddelandeintegritet kallas för en *kryptografisk hash*.

Kryptering är en 1:1-kodning – det vill säga att hela originaldata kan hämtas från krypterade data. En hash mappar dock en godtycklig mängd data till ett fast storleksvärde, precis som en kontrollsumma. Till skillnad från en enkel kontrollsumma är en hash särskilt utformad för att minska *kollisioner*, där olika indata resulterar i samma utdata. Om en bit i en enkel kontrollsumma vändas från 1 till 0 och en annan bit från 0 till 1 är kontrollsumman densamma. Med en kryptografisk hash skulle utdata skilja sig avsevärt, vilket gör det svårt för en angripare att ändra hash-data och få hash-åtgärden på ändrade data fortfarande att resultera i samma värde (och därmed felaktigt verifiera integriteten för dessa data).

TLS använder ett antal olika hash-algoritmer för att tillhandahålla integritet för meddelanden, både programmeddelanden och TLS-kontrollmeddelanden. Dessa inkluderar MD5, SHA-1 och SHA-256.

NetX Secure TLS stöder MD5-, SHA-1- och SHA-256-hashning.

## <a name="tls-extensions"></a>TLS-tillägg

TLS tillhandahåller ett antal tillägg som ger ytterligare funktioner för vissa program. Dessa tillägg skickas vanligtvis som en del av ClientHello- eller ServerHello-meddelanden, vilket indikerar för en fjärrvärd att du vill använda ett tillägg eller ange ytterligare information för användning vid upprättandet av en säker TLS-session.

I allmänhet ger tillägg valfria parametrar till TLS i början av handskakningen som vägleder de operativa åtgärderna. Vissa tillägg kräver programindata eller beslutsfattande, medan andra hanteras automatiskt.

I följande tabell beskrivs de TLS-tillägg som för närvarande stöds av NetX Secure TLS:

| **Tilläggsnamn**              | **Beskrivning**              |
| ------------------------------- |----------------------------- |
| Säker omförhandlingsindikation | Det här tillägget minskar en sårbarhet för man-in-the-middle-angrepp som kan uppstå under en omförhandling av handskakning.|
| Servernamnindikator          | Med det här tillägget kan en TLS-klient ange ett specifikt DNS-namn till en TLS-server, så att servern kan välja rätt autentiseringsuppgifter (förutsätter att servern har flera identitetscertifikat och nätverksinloggningspunkter). |
| Signaturalgoritmer            | Det här tillägget gör det möjligt för en TLS-klient att tillhandahålla en lista över godkända signaturer och hash-algoritmer till en TLS-server. |

Översikt över TLS-tillägg som stöds

### <a name="secure-renegotiation-indication"></a>Säker omförhandlingsindikation

TLS stöder begreppet att utföra en handskakning i en befintlig TLS-session, och använder därmed den etablerade sessionen för att kryptera handskakningsmeddelandena. Den här processen gör att de kryptografiska sessionsnycklarna kan upprättas igen utan att TLS-sessionen avslutas (se avsnittet "TLS-sessionsförhandling").

Tyvärr, efter att TLS har använt omförhandling under en längre tid, upptäcktes att det fanns en säkerhetsrisk för en man-i-mitten-attack som utnyttjar omförhandlingsfunktionen. Tillägget Säker omförhandlingsindikering introducerades för att stänga säkerhetsrisken. I princip använder secure renegotiation-tillägget hashen Slutfört meddelande från den etablerade anslutningen för att verifiera att de ursprungliga värdarna deltar i omförhandlingshandskakningen – i princip används hashen som en verifieringstoken under antagandet att en angripare inte kan förfalska hashen (som kräver åtkomst till sessionsnycklarna).

NetX Secure TLS hanterar omförhandling automatiskt och använder tillägget Säker omförhandling som standard. Ingen programinteraktion krävs.

### <a name="server-name-indication"></a>Servernamnindikator

Under TLS-handskakningen förväntar sig en TLS-klient att en fjärrserver tillhandahåller ett identitetscertifikat så att klienten kan autentisera servern. Det kan dock finnas fall där en server tillhandahåller flera olika tjänster med olika "virtuella" servrar som var och en har unika identiteter. Om det gäller en enskild server med flera identiteter kan en TLS-klient ange ett specifikt DNS-namn som servern använder för att välja rätt autentiseringsuppgifter – mekanismen för att ange det här namnet är SNI-tillägget (Servernamnindikator).

För ett program som använder SNI-tillägget krävs viss interaktion. För TLS-klienter måste programmet ange ett DNS-namn som ska skickas till fjärrservern. För TLS-servrar måste programmet läsa DNS-namnet från tillägget och välja ett lämpligt certifikat att skicka tillbaka till klienten.

Följande avsnitt innehåller mer information om hur du använder SNI-tillägget i NetX Secure TLS.

### <a name="sni-extension--tls-client"></a>SNI-tillägg – TLS-klient

En NetX Secure TLS-klient som vill använda SNI-tillägget måste ange ett DNS-namn till TLS som ska tillhandahållas under handskakningen. Det här namnet måste initieras och anges innan du startar en TLS-session eftersom tillägget skickas i ClientHello-meddelandet som startar handskakningsprocessen.

Följande kodfragment illustrerar användningen av tillägget. Först initieras NX_SECURE_X509_DNS_NAME-objekt med önskat servernamn. Innan du startar TLS-sessionen anges sedan namnet till TLS med hjälp av SNI-tilläggs-API:et. När namnet har angetts krävs ingen ytterligare åtgärd. Se API-referensen i kapitel 4  
  
Beskrivning av NetX Secure Services för mer information om enskilda funktioner.

```C
/* The dns_name variable will contain our desired server name. */
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize the server DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, "www.example.com", 
                                            strlen("www.example.com"));


/* Initialize SNI extension in previously-initialized TLS Session. */
status = nx_secure_tls_session_sni_extension_set(&client_tls_session, &dns_name);

/* Now start the TLS session, starting with establishing the TCP connection – if 
   TLS is started before initializing the SNI extension, the extension will not be 
   sent in the ClientHello message! */
status = nx_tcp_client_socket_connect(&client_socket, IP_ADDRESS(1, 2, 3, 4), 443, 
                                      5 * NX_IP_PERIODIC_RATE);

status = nx_secure_tls_session_start(&client_tls_session, &client_socket, 
                                     NX_WAIT_FOREVER);
```
### <a name="sni-extension--tls-server"></a>SNI-tillägg – TLS-server

På TLS-serversidan kan SNI-tillägget bearbetas av programmet för att välja rätt autentiseringsuppgifter (t.ex. certifikat) som ska tillhandahållas till fjärrklienten under handskakningen. För att göra detta måste programmet ange ett sessionsanrop som anropas efter att ett ClientHello-meddelande har mottagits.

Exempelkoden för nx_secure_tls_session_server_callback_set API (se sidan 122) visar parsningen av ett inkommande SNI-tillägg med hjälp av ett serveranrop. I princip tar TLS-servern emot en ClientHello och anropar återanropet. Programmet använder sedan  nx_secure_tls_session_sni_extension_parse-API:et för att parsa tilläggsdata som tillhandahålls till motringningen för att hitta SNI-tillägget och returnera det angivna DNS-namnet (observera att tillägget endast stöder ett enda DNS-namn). När namnet har erhållits använder programmet det för att hitta och skicka lämpligt serveridentitetscertifikat (och utfärdarkedjan om tillämpligt).

### <a name="signature-algorithms-extension"></a>Signature Algorithms Extension

Det här tillägget är specifikt för TLS 1.2 och gör att TLS-klienten kan tillhandahålla en lista över godkända signatur- och hash-algoritmpar som är godtagbara för användning vid generering och verifiering av digitala signaturer. Listan genereras automatiskt av NetX Secure TLS för TLS-klienter med hjälp av chiffertabellen som nx_secure_tls_session_create *.* Ingen programinteraktion krävs.

## <a name="authentication-methods"></a>Autentiseringsmetoder

TLS tillhandahåller ramverket för att upprätta en säker anslutning mellan två enheter över ett osäkert nätverk, men en del av problemet är att känna till enhetens identitet i den andra änden av anslutningen. Utan en mekanism för att autentisera identiteten för fjärrvärdar blir det en trivial åtgärd för en angripare att utgöra en betrodd enhet.

Inledningsvis kan det verka som att användningen av IP-adresser, maskinvaru-MAC-adresser eller DNS skulle ge en relativt hög konfidensnivå för att identifiera värdar i ett nätverk, men med tanke på typen av TCP/IP-teknik och hur enkelt det är att förfalska adresser och DNS-poster skadade (t.ex. via DNS-cache-förfalskning) blir det tydligt att TLS behöver ytterligare ett skyddslager mot bedrägliga identiteter.

Det finns olika mekanismer som kan ge det här extra lagret av autentisering för TLS, men det vanligaste är det *digitala certifikatet.* Andra mekanismer är PSK (Pre-Shared Keys) och lösenordsscheman.

### <a name="digital-cerificates"></a>Digitala certifikat

Digitala certifikat är den vanligaste metoden för att autentisera en fjärrvärd i TLS. I princip är ett digitalt certifikat ett dokument med specifik formatering som tillhandahåller identitetsinformation för en enhet i ett datornätverk.

TLS använder vanligtvis ett format som kallas X.509, en standard som utvecklats av International T telecom Union, även om andra format för certifikat kan användas om TLS-värdarna kan komma överens om vilket format som används. X.509 definierar ett specifikt format för certifikat och olika kodningar som kan användas för att skapa ett digitalt dokument. De flesta X.509-certifikat som används med TLS kodas med en variant av ASN.1, en annan telekommunikationsstandard. I ASN.1 finns det olika digitala kodningar, men den vanligaste kodningen för TLS-certifikat är standard Distinguished Encoding Rules (DER). DER är en förenklad delmängd av ASN.1 Basic Encoding Rules (BER) som är utformad för att vara entydig, vilket gör parsning enklare. Via kabel kodas TLS-certifikat vanligtvis i binär DER, och det är det format som NetX Secure förväntar sig för X.509-certifikat.

Även om DER-formaterade binära certifikat används i det faktiska TLS-protokollet kan de genereras och lagras i ett antal olika kodningar, med filnamnstillägg som .pem, .crt och .p12. De olika varianterna används av olika program från olika tillverkare, men i allmänhet kan alla konverteras till DER med hjälp av allmänt tillgängliga verktyg.

Den vanligaste av de alternativa certifikatkodningarna är PEM. PEM-formatet (från Privacy-Enhanced Mail) är en base-64-kodad version av DER-kodningen som ofta används eftersom kodningen resulterar i utskrivbar text som enkelt kan skickas med e-post eller webbaserade protokoll.

Att generera ett certifikat för ditt NetX Secure-program ligger vanligtvis utanför omfånget för den här handboken, men OpenSSL-kommandoradsverktyget ([www.openssl.org](http://www.openssl.org)) är allmänt tillgängligt och kan konverteras mellan de flesta format.

Beroende på ditt program kan du generera egna certifikat, tillhandahållas av en tillverkare eller myndighet eller köpa certifikat från en kommersiell certifikatutfärdare.

Om du vill använda ett digitalt certifikat i NetX Secure-programmet måste du först konvertera certifikatet till ett binärt DER-format och, om du vill, konvertera den associerade privata nyckeln (till exempel "privat exponent" för RSA) till ett binärt format, vanligtvis en PKCS#1-formaterad, DER-kodad RSA-nyckel eller en DER-kodad ECC-nyckel. När konverteringen är klar är det upp till dig att läsa in certifikatet och den privata nyckeln på enheten. Möjliga alternativ är att använda ett flash-baserat filsystem eller generera en C-matris från data (med ett verktyg som "xxd" från Linux) och kompilera certifikatet och nyckeln till ditt program som konstanta data.

När certifikatet har lästs in på enheten kan TLS-API:et användas för att associera certifikatet med en TLS-session.

Mer information och exempel på hur du använder X.509-certifikat med NetX Secure TLS finns i avsnittet Importera X.509-certifikat till NetX Secure.

Mer information finns i följande TLS-tjänster i API-referensen:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add
- nx_secure_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Information om TLS-klientcertifikat

TLS-klientimplementeringarna kräver vanligtvis inte att ett "lokalt" certifikat<sup>14</sup> läses in på enheten. Undantaget till detta är när Klientcertifikatautentisering är aktiverat, men detta är mycket mindre vanligt.

En TLS-klient kräver att minst ett "betrott" certifikat<sup>15</sup> läses in (fler kan läsas in om det behövs) och utrymme för att ett "fjärrcertifikat<sup>16"</sup> ska allokeras.

Mer information om hur du lägger till betrodda certifikat och allokerar utrymme för fjärrcertifikat finns i TLS API-referensen för följande tjänster: nx_secure_tls_remote_certificate_allocate, nx_secure_tls_trusted_certificate_add.

14. Ett "lokalt" certifikat är ett certifikat som identifierar den lokala enheten– det vill säga det tillhandahåller identitetsinformation för den enhet där TLS-programmet läses in.

15. Ett "betrott" certifikat är ett certifikat som utgör grunden för förtroende och autentisering av fjärrenheten, antingen direkt eller via en PKI (Public Key Infrastructure). Roten i förtroendekedjan kallas vanligtvis för en "certifikatutfärdare" eller ett CA-certifikat.

16. Ett "fjärrcertifikat" avser det certifikat som skickas av fjärrvärden under TLS-handskakningen. Den tillhandahåller identitet för den fjärrvärden och autentiseras genom att jämföra den med ett "betrott" certifikat på den lokala enheten.

### <a name="tls-server-certificate-specifics"></a>Information om TLS-servercertifikat

TLS-serverimplementeringarna kräver vanligtvis inte att "betrodda" certifikat läses in på enheten eller fjärrcertifikat ska allokeras. Undantaget är när Klientcertifikatautentisering är aktiverat (detta är mindre vanligt).

En TLS-server kräver att ett "lokalt" certifikat läses in så att servern kan tillhandahålla det till fjärrklienten under TLS-handskakningen för att autentisera servern för klienten.

Mer information om hur du läser in lokala certifikat för användning med NetX TLS-serverprogram finns i API-referensen för följande tjänster: 
- nx_secure_tls_local_certificate_add, 
- nx_secure_tls_local_certificate_remove.

### <a name="pre-shared-keys-psk"></a>I förväg delade nycklar (PSK)

En annan mekanism för identifieringsautentisering i TLS är begreppet I förväg delade nycklar (PSK). Om du använder en PSK-chiffersvit behöver du inte göra processorintensiva krypteringsåtgärder med offentliga nycklar, vilket är en boon för resursbegränsade inbäddade enheter. PSK ersätter certifikatet i TLS-handskakningen och används i stället för den krypterade för masterhemligheten för generering av TLS-sessionsnyckel.

PSK-chiffer är begränsade i den mening att en delad hemlighet måste finnas på båda enheterna innan en TLS-session kan upprättas. Det innebär att enheterna måste ha lästs in med den hemligheten på något annat sätt än en TLS PSK-anslutning . PSK:er kan uppdateras via en TLS PSK-anslutning, men enheten måste nödvändigtvis börja med en PSK som läses in via någon annan mekanism. En sensorenhet och dess gatewayenhet kan till exempel läsas in med PSK:er i fabriken innan den levereras, eller så kan en standard-TLS-anslutning (med ett certifikat) användas för att läsa in PSK.

PSK-chiffer finns i ett par former, som beskrivs i RFC 4279. Den första använder RSA eller Diffie-Hellman nycklar som används på samma sätt som de offentliga nycklar som överförs i certifikatet i standard-TLS-handskakningar. Det andra formuläret, som används mer i en resursbegränsad miljö, använder en PSK som används för att direkt generera sessionsnycklarna (till exempel för användning av AES), vilket undviker användningen av dyra RSA- eller Diffie-Hellman-åtgärder.

NetX Secure stöder den andra formen av PSK-chiffer, vilket gör det möjligt för program att ta bort all krypteringskod och minnesanvändning med offentliga nycklar. PSK är inte en AES-nyckel, men kan anses vara mer som ett lösenord som de faktiska nycklarna genereras från. Det finns några begränsningar för vad PSK-värdet kan vara, men längre värden ger bättre säkerhet (samma som med lösenord).

Om du vill använda PSK med NetX Secure-programmet måste du först definiera det globala **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Detta görs vanligtvis via kompileringsinställningarna, men definitionen kan också placeras i nx_secure_tls.h-huvudfilen. När makrot har definierats kompileras PSK-chifferstöd till ditt NetX Secure TLS-program.

När PSK-stöd är aktiverat kan du använda TLS-API:et för att konfigurera PSK:er för ditt program. Varje PSK kräver ett PSK-värde (den faktiska hemliga "nyckeln" – skydda det här värdet), ett "identitetsvärde" som används för att identifiera den specifika PSK och ett "identitetstips" som används av en TLS-server för att välja ett visst PSK-värde.

Själva PSK kan vara ett binärt värde eftersom det aldrig skickas via en nätverksanslutning. PSK kan ha ett värde på upp till 64 byte.

Identiteten och tipset måste vara utskrivbara teckensträngar formaterade med UTF-8. Identitets- och tipsvärdena kan vara valfri längd på upp till 128 byte.

Identiteten och PSK bildar ett unikt par som läses in på varje enhet i nätverket som behöver kommunicera med varandra.

"Tipset" används främst för att definiera specifika programprofiler för att gruppera PSK:er efter funktion eller tjänst. Dessa värden måste avtalas i förväg och är programberoende. Till exempel använder OpenSSL-kommandoradsserverprogrammet (med PSK aktiverat) standardsträngen "Client_identity", som måste tillhandahållas av en TLS-klient för att fortsätta med TLS-handskakningen.

Mer information om PSK:er finns i NetX Secure API-referensen för följande tjänster: nx_secure_tls_client_psk_set, nx_secure_tls_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importera X.509-certifikat till NetX Secure

Digitala certifikat krävs för de flesta TLS-anslutningar på Internet. Certifikat är en metod för att autentisera tidigare okända värdar via  Internet med hjälp av betrodda certifikatutfärdare eller certifikatutfärdare. Om du vill ansluta din NetX Secure-enhet till en kommersiell molntjänst (till exempel Amazon Web Services) måste du importera certifikat till ditt program genom att läsa in dem på enheten.

Tillsammans med certifikat behöver du ibland även en *privat nyckel som* är associerad med certifikatet. I vissa program (till exempel TLS-klient när autentisering med klientcertifikat inte används) räcker certifikatet, men om certifikatet används för att identifiera din enhet behöver du en privat nyckel. Privata nycklar genereras vanligtvis när du skapar certifikatet och lagras i en separat fil, ofta krypterade med ett lösenord.

### <a name="certificate-types"></a>Typer av certifikat

Digitala certifikat används vanligtvis för att identifiera entiteter i ett nätverk, men beroende på vilket program de har har de lite olika egenskaper.

### <a name="local-certificates"></a>Lokala certifikat

I den här dokumentationen refererar vi till "lokala certifikat" som de certifikat som tillhandahåller en identitet för vår lokala enhet (ett annat möjligt namn kan vara "enhetscertifikat"). Dessa certifikat kommer att tillhandahållas till en fjärrvärd när fjärrvärden vill autentisera den lokala enheten.

### <a name="remote-certificates"></a>Fjärrcertifikat

I den här dokumentationen refererar "fjärrcertifikat" till de certifikat som tillhandahålls av en fjärrvärd under TLS-handskakningen i förekommande fall. Utrymme för dessa certifikat måste allokeras, annars kan NetX Secure inte parsa dem och slutföra TLS-handskakningen.

### <a name="signing-certificates"></a>Signeringscertifikat

Ett "signeringscertifikat" används för att digitalt signera andra certifikat eller data för autentisering. Dessa certifikat kan vara mellanliggande certifikat eller rotcertifikat i en PKI (Public Key Infrastructure) och används vanligtvis inte för att identifiera enskilda enheter eller värdar.

### <a name="root-ca-certificates"></a>Rotcertifikatutfärdarcertifikat

"Rotcertifikatutfärdarcertifikat" är signeringscertifikat som utgör grunden för en PKI och är självsignerade, i stället för att signeras av ett annat signeringscertifikat. Minst ett rotcertifikatutfärdarcertifikat krävs vanligtvis för att en TLS-klient ska kunna verifiera fjärrservrar.

### <a name="certificate-formats"></a>Certifikatformat

Digitala certifikat är helt enkelt filer som innehåller strukturerade data kodade med ASN.1-syntaxen. Det finns dock olika format där certifikat kan lagras och det är viktigt att ha rätt format innan du läser in ett certifikat i ett NetX Secure-program.

De vanligaste formaten för certifikat är DER och PEM. DER (för *Distinguished Encoding Rules*, ett ASN.1-format) är det binära format som används av TLS vid den inledande handskakningen. PEM (från *Privacy Enhanced Mail*) är en base-64-kodad version av DER-formatet som är lämplig för e-post eller att skicka via HTTP på webben. Olika leverantörer använder olika filnamnstillägg för certifikat, till exempel ".pem" eller ".crt" för PEM-certifikat och ".der" för DER-certifikat. Om du har ett certifikat och det inte är tydligt vilket format som används kan du genom att öppna filen i en textredigerare fastställa typen eftersom DER-filer är kodade binära och PEM-filer är vanlig ASCII-text som börjar med rubriken "-----BEGIN CERTIFICATE-----".

NetX Secure kräver att certifikatet är i binärt DER-format, så du måste konvertera certifikatet till DER-format innan du importerar. Detta kan göras med lättillgängliga verktyg som OpenSSL.

Om du behöver en privat nyckel för ditt program kodas nyckelfilen med PEM eller DER i ett visst format (PKCS#1 för RSA, RFC 5915 för ECC). Den privata nyckelfilen måste konverteras till DER innan den importeras.

Följande OpenSSL-kommandon ges som ett exempel för att konvertera certifikat och RSA-nyckelfiler till det DER-format som krävs av NetX Secure (ECC är liknande – se OpenSSL-dokumentationen).

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
### <a name="private-keys-and-certificates"></a>Privata nycklar och certifikat

För certifikat som identifierar en enhet måste den associerade privata nyckeln läsas in tillsammans med certifikatet. Den privata nyckeln (som kan vara till för en av algoritmerna för offentlig nyckel, till exempel RSA, Diffie-Hellman eller Elliptic-Curve-kryptografi) används av en TLS-server för att dekryptera det inkommande nyckelmaterialet ("för originalhemligheten") från en TLS-klient, vilket autentiserar sig för klienten. För en TLS-klient gäller att om ett identitetscertifikat (ett certifikat med dess associerade privata nyckel) tillhandahålls och en server begär ett klientcertifikat, används den privata nyckeln för att autentisera klienten – i fallet med RSA krypterar klienten en token med hjälp av den privata nyckeln som servern sedan dekrypterar med hjälp av klientens offentliga nyckel,  tillhandahålls i klientcertifikatet (Diffie-Hellman- och ECC-autentisering sker på liknande sätt, men informationen är lite annorlunda).

I NetX secure används tjänsten *nx_secure_x509_certificate_initialize* för att initiera ett X.509-certifikat (se avsnittet "Läsa in certifikat på enheten" för mer information) och eventuellt associera en privat nyckel med det certifikatet.

Om en privat nyckel anges markeras certifikatet som det "identitetscertifikat" som används för att identifiera enheten. Nyckeln skickas som en sammanhängande binär blob och en längd, med en associerad nyckeltyp. Nyckeltypen beror på nyckeltypen (t.ex. RSA, ECC osv.) och formatet (t.ex. PKCS#1 DER). Om ingen nyckel anges kan värdet NX_SECURE_X509_KEY_TYPE_NONE (värde 0x0) skickas för att indikera att ingen nyckel har angetts (en längd på 0 och en NX_NULL-pekare för dataparametern får samma effekt).

I följande tabell visas de nyckeltyper som är kända för NetX Secure och den associerade typidentifierare som ska skickas till *nx_secure_x509_certificate_initialize*. Ytterligare nyckeltyper kommer att läggas till allt eftersom fler krypteringsalgoritmer läggs till i NetX Secure.

| Identifierare                              | Algoritm | Format   | Kodning | Värde |
| --------------------------------------- | --------- | -------- | -------- | ----- |
| NX_SECURE_X509_KEY_TYPE_NONE            | Ingen      | Saknas      | Saknas      | 0x0   |
| NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER   | RSA       | PKCS#1   | Der      | 0x1   |
| NX_SECURE_X509_KEY_TYPE_EC_DER          | ECDSA     | RFC 5915 | Der      | 0x2   |

### <a name="user-defined-private-key-types"></a>Användardefinierade typer av privata nycklar

Värdena för nyckeltypsidentifierarna för *den* nx_secure_x509_certificate_initialize tjänsten styr de åtgärder som vidtas när den privata nyckeln tillhandahålls. För kända typer ligger värdena i intervallet 0x0000 0000 – 0x0000 FFFF (de nedersta 16 bitarna i ett 32-bitars heltal utansignerat heltal). För plattformar med anpassade nyckeltyper<sup>17</sup> (vilket är fallet för vissa maskinvarubaserade krypteringsmotorer) kan en användardefinierad nyckeltyp i intervallet 0x0000 1 000-0xFFFF FFFF (översta 16 bitar som inte är noll) skickas som nyckeltyp. Om någon av de översta 16 bitarna av nyckeltypen anges skickas data för den privata nyckeln direkt till lämplig kryptografirutin (t.ex. RSA) som anges i TLS-chiffertabellen. Användardefinierade nyckeltyper parsas inte eller bearbetas inte på annat sätt innan de skickas till den kryptografiska rutinen. Dessutom skickas även den användardefinierade nyckeltypen till den kryptografiska rutinen så att all lämplig bearbetning kan hanteras på den nivån.

Observera att användardefinierade nyckeltyper vanligtvis används för specifika maskinvaruplattformar som använder anpassade (eventuellt krypterade) nyckeldata. Detta innebär i allmänhet att nyckeldata genereras eller kodas med hjälp av en mekanism som är specifik för den maskinvaruleverantören (eller en specifik standard, i fallet med en standard som PKCS#11). Mer information finns i dokumentationen för maskinvaruplattformen.

17. Användardefinierade nyckeltyper kräver en motsvarande anpassad kryptografirutin för att hantera det anpassade nyckelformatet. Den kryptografiska rutinen måste ha en matchande algoritm (t.ex. RSA) och skickas till TLS i chiffertabellen. 

### <a name="loading-certificates-onto-your-device"></a>Läsa in certifikat på din enhet

Alla metoder för att läsa in en fil på enheten räcker för att importera dina certifikat.

Den enklaste metoden för att läsa in ett certifikat är att konvertera de binära DER-kodade data till en C-matris och kompilera dem till ditt program som en konstant. Detta kan enkelt göras med verktyg som "xxd" i Linux (med alternativet "-i").

Du kan också läsa in certifikatet i ett flash-filsystem eller andra lagringsalternativ så länge du kan skicka en pekare till certifikatdata till NetX Secure-API:et.

### <a name="certificate-files-needed-for-netx-secure"></a>Certifikatfiler som behövs för NetX Secure

Vilka certifikatfiler du behöver importera beror på ditt program. I allmänhet kräver TLS-servrar ett certifikat för att identifiera enheten och TLS-klienter kräver ett eller flera betrodda certifikat *för* att autentisera fjärrservrar. I följande tabell visas de certifikat som behövs för vissa olika TLS-program.

| **TLS-funktioner/-alternativ**                     | **Certifikat/nycklar som krävs (minimum)**              |
| ------------------------------------------------- | --------------------------------------------------- |
| TLS-klient                                        | Rotcertifikatutfärdarcertifikat                                 |
| TLS-server                                        | Lokalt certifikat, privat nyckel för certifikatet |
| TLS-server med klientcertifikatautentisering | Lokalt certifikat, privat nyckel, rotcertifikatutfärdare             |
| TLS-klient med klientcertifikatautentisering | Lokalt certifikat, privat nyckel, rotcertifikatutfärdare             |
| TLS-klient eller server med endast i förväg delade nycklar    | Ingen (PSK används i stället för certifikat)             |

De relevanta tjänsterna för att läsa in certifikat är följande:

| **API-namn**                                   | **Syfte**                                            |
| ---------------------------------------------- |------------------------------------------------------- |
| nx_secure_x509_certificate_initialize      | Måste anropas för att alla certifikat ska fylla NX_SECURE_X509_CERT strukturen med dina certifikatdata och din privata nyckel. |
| nx_secure_tls_local_certificate_add       | Lägg till ett lokalt certifikat i en TLS-session för att identifiera din enhet.                                                                |
| nx_secure_tls_local_certificate_remove    | Ta bort ett lokalt certifikat från en TLS-session.                                                                                   |
| nx_secure_tls_remote_certificate_allocate | Allokera utrymme för ett fjärrcertifikat (kallas med en oinniterad NX_SECURE_X509_CERT).                                   |
| nx_secure_tls_trusted_certificate_add     | Lägg till ett certifikat i en TLS-session som ett betrott certifikat för autentisering av fjärrvärdar.                                     |
| nx_secure_tls_trusted_certificate_remove  | Ta bort ett betrott certifikat från en TLS-session.                                                                                 |

### <a name="working-with-aws-iot-certificates"></a>Arbeta med AWS IoT-certifikat

I Amazon Web Services IoT-gränssnittet väljer du "Säkerhet" på sidomenyn och sedan "Certifikat". Skapa ett nytt certifikat och följ anvisningarna för att ladda ned det nya enhetscertifikatet.

När du har laddat ned certifikaten måste du konvertera dem till DER-format med hjälp av OpenSSL eller ett liknande verktyg.

Obs! AWS tillhandahåller också en offentlig nyckelfil. Den offentliga nyckeln finns i det lokala enhetscertifikatet, så den behöver inte importeras till ditt program.

Här är ett exempel på kommandon för att konvertera det lokala enhetscertifikatet och dess privata nyckel till DER-format för användning med NetX Secure:

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
De konverterade filerna kan importeras till ditt program enligt anvisningarna ovan.

## <a name="x509-certificate-validation-in-netx-secure"></a>X.509-certifikatverifiering i NetX Secure 

När du använder TLS med X.509-certifikat för värdidentifiering och verifiering är det viktigt att förstå hur dessa certifikat faktiskt verifieras. Även om TLS-specifikationen inte innehåller detaljerade instruktioner om hur du validerar ett certifikat, refererar den till X.509-specifikationen (RFC 5280). I allmänhet förväntas TLS utföra minst grundläggande verifiering av inkommande certifikat (de certifikat som tillhandahålls av fjärrvärden under TLS-handskakningen) och NetX Secure TLS skiljer sig inte åt.

### <a name="basic-x509-validation"></a>Grundläggande X.509-validering

För inkommande certifikat utför NetX Secure TLS grundläggande X.509-sökvägsverifiering. Processen omfattar att kontrollera varje certifikats digitala signatur mot dess utfärdarcertifikat, som kan tillhandahållas av fjärrvärden eller finnas i det betrodda certifikatarkivet (mer information om hur du importerar X.509-certifikat till NetX Secure finns i avsnittet Importera X.509-certifikat till NetX Secure). Valideringsprocessen upprepas rekursivt på utfärdarcertifikaten tills ett betrott certifikat har nåtts eller kedjan avslutas (med ett själv signerat certifikat eller ett certifikat som saknas). Om ett betrott certifikat nås verifieras certifikatet, annars avvisas det. I varje steg i verifieringsprocessen kontrolleras dessutom utgångsdatumet för varje certifikat mot den tid som tillhandahålls av programmets tidsstämpelfunktion (mer information finns i tjänsten "nx_secure_tls_session_time_function_set".

X.509-specifikationen innehåller också en algoritm för att stödja "principer", som är identifierare som finns i ett X.509-tillägg som kan kontrolleras under sökvägsverifieringen. NetX Secure behandlar för närvarande X.509-certifikat som om alternativet "anyPolicy" har definierats – det vill säga att alla principer är godtagbara och den valfria principkontrollen utförs inte. NetX Secure X.509-implementeringen kan utökas med den här funktionen i en framtida version. För tillfället kan principtillägget hämtas från ett certifikat med hjälp av *nx_secure_x509_extension_find* API.

När den grundläggande sökvägsverifieringen är klar anropar TLS återanropet för certifikatverifiering som tillhandahålls av programmet med *hjälp av nx_secure_tls_session_certificate_callback_set-API:et.* Om inget återanrop anges anses certifikatet vara betrott efter verifieringen av den lyckade sökvägen. Om ett återanrop anges utför återanropet eventuell ytterligare validering av certifikatet som krävs av programmet. Returvärdet från motringning används för att avgöra om du vill fortsätta med TLS-handskakningen eller avbryta handskakningen på grund av ett valideringsfel.

Motringningen anropas med en pekare till relevant TLS-session och en NX_SECURE_X509_CERT pekare till certifikatet som ska verifieras. Mellan TLS-sessionen och certifikatet har programmet alla data som behövs från TLS för att utföra ytterligare verifieringskontroller.

För att underlätta ytterligare validering tillhandahåller NetX Secure X.509-rutiner för vissa vanliga verifieringsåtgärder, inklusive DNS-verifiering och kontroll av listan över återkallade certifikat. Alla dessa rutiner är lämpliga för återanrop av certifikatverifiering, men kan också användas för att utföra kontroll av X.509-certifikat utanför linjen.

I följande tabell sammanfattas tillgängliga hjälpfunktioner för X.509-certifikatbearbetning. Mer detaljerade förklaringar av åtgärderna finns i följande avsnitt och API-referensen i kapitel 4  
  
Beskrivning av NetX Secure Services ger ytterligare information om de specifika rutinerna.

| **API-namn**                             | **Beskrivning**                               |
| ---------------------------------------- | -------------------------------------- |
| nx_secure_x509_common_name_dns_check               | Kontrollera X.509-ämnets eget namn och SubjectAltName mot ett förväntat DNS-namn |
| nx_secure_x509_crl_revocation_check                 | Sök efter ett återkallat certifikat i en lista över återkallade X.509-certifikat (CRL)       |
| nx_secure_x509_extended_key_usage_extension_parse | Parsa och hitta en specifik OID för utökad nyckelanvändning i ett certifikat                   |
| nx_secure_x509_key_usage_extension_parse           | Parsa och returnera nyckelanvändningsbitfältet i ett certifikat                            |
| nx_secure_x509_extension_find                        | Hitta och returnera råa DER-kodade ASN.1-data för ett visst tillägg.            |

X.509-hjälpfunktioner för användning i återanropet för certifikatverifiering

### <a name="x509-extensions"></a>X.509-tillägg

X.509-specifikationen beskriver ett antal "tillägg" som kan användas för att ange ytterligare information som kan användas vid verifiering av certifikat. De här tilläggen är till största delen valfria och krävs inte för säker validering av ett digitalt certifikat mot ett betrott rotcertifikat. NetX Secure stöder dock vissa grundläggande tillägg. Stöd för ytterligare tillägg kan läggas till i framtida versioner.

De tillägg som stöds för närvarande visas i följande tabell:

| Tilläggsnamn           | Description                                                                   | Relevant API                                             |
| ------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| Nyckelanvändning                | Tillhandahåller godtagbara användningsområden för ett certifikats offentliga nyckel i ett bitfält         | nx_secure_x509_key_usage_extension_parse           |
| Utökad nyckelanvändning       | Tillhandahåller ytterligare godtagbara användningsområden för ett certifikats offentliga nyckel med hjälp av OID:er | nx_secure_x509_extended_key_usage_extension_parse |
| Alternativt namn för certifikatmottagare | Tillhandahåller alternativa DNS-namn som också representeras av certifikatet   | nx_secure_x509_common_name_dns_check               |

### <a name="unsupported-x509-extensions"></a>X.509-tillägg som inte stöds

NetX Secures X.509-implemenation tillhandahåller även en tjänst för att extrahera tillägg som inte stöds: *nx_secure_x509_extension_find*. Det här API:et är avsett för avancerade användare eftersom det kräver kunskap om DER-kodad ASN.1 för att parsa de data som returneras. Den används internt för att extrahera tillägg som stöds, men tillhandahålls för att underlätta utvecklingen av anpassat stöd för X.509-tillägg.

Om du nx_secure_x509_extension_find en NX_SECURE_X509_EXTENSION skickas ett certifikat tillsammans med certifikatet och ett tilläggs-ID, som är en heltalsrepresentation av OID-strängen med variabel längd för en känd tilläggstyp. En fullständig lista över OID:er som stöds för X.509-tillägg finns i API-referensen för nx_secure_x509_extension_find på sidan 178.

Strukturen NX_SECURE_X509_EXTENSION definieras på följande sätt:

```C
typedef struct NX_SECURE_X509_EXTENSION_STRUCT
{
    /* Identifier (maps to OID) for this extension. */
    USHORT nx_secure_x509_extension_id;

    /* Critical flag - boolean value. */
    USHORT nx_secure_x509_extension_critical;

    /* Pointer to DER-encoded extension data. */
    const UCHAR *nx_secure_x509_extension_data;
    ULONG        nx_secure_x509_extension_data_length;
} NX_SECURE_X509_EXTENSION;
```
När tjänsten returneras fylls strukturen i med relevanta data från certifikatet. Fältet nx_secure_x509_extension_id används vanligtvis för interna syften, men fylls i med relevant OID-heltalsrepresentation. Fältet nx_secure_x509_extension_critical exponerar det kritiska X.509-tilläggsflaggan (booleskt). Fälten nx_secure_x509_extension_data och nx_secure_x509_extension_data_length innehåller en pekare till DER-kodade ASN.1-data för tillägget och längden på dessa data.

Den faktiska parsningen av asn.1-tilläggsdata ligger utanför omfånget för det här dokumentet, men om du har åtkomst till NetX Secure TLS-källan kan du se hur parsningen utförs oavsett var nx_secure_x509_extension_find anropas för tillägg som stöds.

### <a name="x509-dns-validation"></a>X.509 DNS-verifiering

En vanlig certifikatverifieringsåtgärd i TLS innebär att kontrollera namnet på Top-Level-domänen (TLD) för en fjärrvärd mot X.509-certifikatet som tillhandahålls av värden under TLS-handskakningen. Den här åtgärden hjälper till att säkerställa att certifikatet verkligen matchar värdservern som tillhandahöll det, förutsatt att DNS-sökning kan vara betrott. I NetX Secure TLS tillhandahålls den här funktionen av **tjänsten nx_secure_x509_common_name_dns_check**, som tar certifikatet och en sträng som innehåller TLD-delen av DEN URL som används för att komma åt värden. TLD jämförs med certifikatets eget namn-fält och om det matchar NX_SUCCESS returneras. Om det gemensamma namnet inte matchar kontrollerar rutinen även om X.509-certifikattillägget *subjectAltName finns.* Om det finns ett subjectAltName kontrolleras även alla DNSName-poster i tillägget mot det angivna TLD:t. Om det finns någon matchning NX_SUCCESS returneras igen. Om ingen matchning hittas returneras ett fel som lämpar sig för att returnera från återanropet för certifikatverifiering.

### <a name="x509-key-usage-and-extended-key-usage-extensions"></a>X.509-nyckelanvändning och utökade nyckelanvändningstillägg

Tilläggen X.509-nyckelanvändning och utökad nyckelanvändning innehåller information om hur ett certifikats offentliga nyckel kan användas vid autentisering av certifikatet. Nyckelanvändningen tillhandahålls av certifikatets utfärdare när certifikatet signeras och utfärdas. Nyckelanvändningen kan användas av en TLS-värd för att kontrollera att certifikatet har behörighet att användas för att autentisera en TLS-fjärrvärd och utföra andra åtgärder.

Tillägget nyckelanvändning består av ett enkelt bitfält där var och en av bitarna representerar en specifik nyckelanvändning. En fullständig lista över dessa värden finns i API-referensen *för* nx_secure_x509_key_usage_extension_parse på sidan 183. En mer fullständig beskrivning av nyckelanvändningsbitarna och deras betydelser finns i RFC 5280, avsnitt 4.2.1.3.

Tillägget för utökad nyckelanvändning, t.ex. nyckelanvändningstillägget, innehåller information om godkänd nyckelanvändning. Men för att ge stöd för godtycklig användning använder tillägget för utökad nyckelanvändning OID:er i stället för ett bitfält. När du parsar ett tillägg för utökad nyckelanvändning i NetX Secure X.509 tillhandahålls ett heltal som representerar OID av programmet – *nx_secure_x509_extended_key_usage_extension_parse-tjänsten* returnerar sedan om OID:t finns. En fullständig lista över OID:er som stöds för användning av utökad nyckel finns i API-referensen *för nx_secure_x509_extended_key_usage_extension_parse* på sidan 175. En mer fullständig beskrivning av OID:erna och deras betydelser finns i RFC 5280, avsnitt 4.2.1.12.

### <a name="x509-crl-revocation-status-checking"></a>Kontroll av återkallade X.509-listor över återkallade certifikat

X.509 innehåller en  mekanism som kallas listan över återkallade certifikat (CRL) som gör att en digital certifikatsigneringsutfärdare kan återkalla giltigheten för certifikat som den har signerat. Alla program som behöver verifiera certifikat från en signeringsutfärdare kan hämta en lista över återkallade certifikat och jämföra certifikat som signerats av den utfärdaren (utfärdaren) med listan över återkallade certifikat för att se om deras status har återkallats av någon anledning (till exempel komprometterad privat nyckel). På så sätt kan programmet undvika att använda potentiellt farliga certifikat som klarar andra certifikatverifieringskontroller.

Att hämta en lista över återkallade certifikat görs av ett program genom att ladda ned den DER-kodade listan från en fördefinierad server eller på något annat sätt. Den faktiska konfigurationen varierar från utfärdare till utfärdare, så NetX Secure tillhandahåller inte någon mekanism för att hämta listor över återkallade certifikat, men det tillhandahåller en rutin för att kontrollera ett certifikat mot en lista över **återkallade certifikat, nx_secure_x509_crl_revocation_check**.

API:et tar en DER-kodad CRL, ett certifikatarkiv (till exempel det i en TLS-session) att kontrollera mot och certifikatet som ska kontrolleras. Rutinen verifierar först själva listan över återkallade certifikat mot det betrodda arkivet (en del av certifikatarkivet som tillhandahålls av programmet). Detta är viktigt för att skydda mot bedrägliga listor över återkallade certifikat som används för DoS-attacker och fastställer att listan över återkallade certifikat faktiskt kommer från rätt utfärdare. Efter CRL-verifieringen kontrolleras utfärdaren – om utfärdaren av listan över återkallade certifikat inte matchar utfärdaren av certifikatet, är listan över återkallade certifikat inte giltig för certifikatet och ett fel returneras. Det är upp till programmet att avgöra om TLS-handskakningen kan fortsätta i det här läget. Om utfärdarna matchar genomsöks listan över återkallade certifikat efter serienumret för certifikatet som verifieras. Om serienumret finns i listan returneras ett fel som anger att certifikatet har återkallats. Om ingen matchning hittas NX_SUCCESS returneras.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Klientcertifikatautentisering i NetX Secure TLS

När du använder X.509-certifikatautentisering kräver TLS-protokollet att TLS-serverinstansen tillhandahåller ett certifikat för identifiering, men som standard behöver TLS-klientinstansen inte ange ett certifikat för autentisering med hjälp av en annan form av autentisering i stället (t.ex. en kombination av användarnamn/lösenord). Detta matchar den vanligaste användningen av TLS på Internet för webbplatser. En onlinebutik måste till exempel bevisa för en potentiell kund med hjälp av en webbläsare att servern är legitim, men användaren kommer att använda ett inloggnings-/lösenord för att få åtkomst till ett specifikt konto.

Standardfallet är dock inte alltid önskvärt, så TLS tillåter eventuellt att TLS-serverinstansen begär ett certifikat från fjärrklienten. När den här funktionen är aktiverad skickar TLS-servern ett CertificateRequest-meddelande till TLS-klienten under handskakningen. Klienten måste svara med ett eget certifikat och ett CertificateVerify-meddelande som innehåller en kryptografisk token som visar att klienten äger den matchande privata nyckel som är associerad med certifikatet. Om verifieringen misslyckas eller om certifikatet inte är anslutet till ett betrott certifikat på servern misslyckas TLS-handskakningen.

Det finns två separata fall för klientcertifikatautentisering i TLS – i följande avsnitt beskrivs båda fallen.

### <a name="client-certificate-authentication-for-tls-clients"></a>Klientcertifikatautentisering för TLS-klienter

En TLS-klient kan försöka ansluta till en server som begär ett certifikat för klientautentisering. I det här fallet måste klienten tillhandahålla ett certifikat till servern och verifiera att den äger den matchande privata nyckeln, annars avslutar servern TLS-handskakningen.

I NetX Secure TLS finns det ingen särskild konfiguration som stöder den här funktionen, men programmet måste ange ett lokalt identifieringscertifikat för TLS-klientinstansen med *hjälp av nx_secure_tls_local_certificate_add tjänsten.* Om inget certifikat tillhandahålls av programmet, men fjärrservern använder klientcertifikatautentisering och begär ett certifikat, misslyckas TLS-handskakningen. Certifikatet som tillhandahålls till TLS-sessionen *med nx_secure_tls_local_certificate_add* måste kännas igen av fjärrservern för att slutföra TLS-handskakningen.

### <a name="client-certificate-authentication-for-tls-servers"></a>Klientcertifikatautentisering för TLS-servrar

TLS-serverfallet för klientcertifikatautentisering är något mer komplext än TLS-klientfallet eftersom funktionen är valfri. I det här fallet måste TLS-servern begära ett certifikat från den fjärranslutna TLS-klienten och sedan bearbeta Meddelandet CertificateVerify för att verifiera att fjärrklienten äger den matchande privata nyckeln och sedan måste servern kontrollera att certifikatet som tillhandahålls av klienten kan spåras till ett certifikat i det lokala betrodda certifikatarkivet.

I NetX Secure TLS Server-instanser styrs klientcertifikatautentisering av <br>
*<span class="underline"> _</span> nx-säker <span class="underline">_</span>tls-sessionsklient <span class="underline"> _</span> <span class="underline">_</span><span class="underline"> _</span> verifierar <span class="underline">_</span>aktivera* och<br>
*nx <span class="underline"> _</span> secure <span class="underline">_</span>tls <span class="underline"> _</span> session client <span class="underline">_</span><span class="underline"> _</span> verify <span class="underline">_</span>disable* services.

Om du vill aktivera klientcertifikatautentisering måste ett program anropa<br>
*nx <span class="underline"> _</span> secure <span class="underline">_</span>tls <span class="underline"> _</span> session client <span class="underline">_</span><span class="underline"> _</span> verify <span class="underline">_</span>enable with* the TLS Server session instance before calling *nx_secure_tls_session_start*. Observera att anrop av den här tjänsten på en TLS-session som används för TLS-klientanslutningar inte har någon effekt.

När autentisering med klientcertifikat är aktiverat begär TLS-servern ett certifikat från TLS-fjärrklienten under TLS-handskakningen. I NetX Secure TLS Server kontrolleras klientcertifikatet mot arkivet med betrodda certifikat som skapats med *nx <span class="underline"> _</span> secure_tls <span class="underline">_</span>betrott <span class="underline"> _</span> <span class="underline">_</span>* certifikat som följer X.509-utfärdarkedjan. Fjärrklienten måste tillhandahålla en kedja som ansluter dess identitetscertifikat till ett certifikat i det betrodda arkivet, annars misslyckas TLS-handskakningen. Om meddelandebearbetningen av CertificateVerify misslyckas misslyckas dessutom TLS-handskakningen.

Signaturmetoderna som används för CertificateVerify-metoden är fasta för TLS version 1.0 och TLS version 1.1 och anges av TLS-servern i TLS version 1.2. För TLS 1.2 följer signaturmetoderna som stöds vanligtvis de relevanta metoder som anges i tabellen med kryptografiska metoder, men vanligtvis RSA med SHA-256 (se avsnittet "Kryptografi i NetX Secure TLS" för mer information om hur du initierar TLS med kryptografiska metoder).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografi i NetX Secure TLS

TLS definierar ett protokoll där kryptografi kan användas för att skydda nätverkskommunikationen. Därför lämnar den faktiska kryptografin öppen för TLS-användare. Specifikationen kräver endast att ett enda chiffer implementeras – när det gäller TLS 1.2 är chifferuten TLS_RSA_WITH_AES_128_CBC_SHA, vilket anger användningen av RSA för åtgärder med offentlig nyckel, AES i CBC-läge med 128-bitars nycklar för sessionskryptering och SHA-1 för meddelandeautentiseringshasher.

Eftersom NetX Secure är TLS 1.2-kompatibelt möjliggör det obligatoriska TLS_RSA_WITH_AES_128_CBC_SHA-chifferet som standard, men med tanke på antalet möjliga implementeringar för var och en av de kryptografiska metoderna på grund av maskinvarufunktioner och andra överväganden, tillhandahåller NetX Secure ett allmänt kryptografiskt API som gör att användaren kan ange vilka kryptografiska metoder som ska användas med TLS.

Obs! Den allmänna kryptografiska API-mekanismen gör det också möjligt för användare att implementera sina egna chiffer, men detta rekommenderas för avancerade användare som är bekanta med TLS-chiffer och tillägg. Kontakta din Express Logic-representant om du är intresserad av att stödja dina egna chiffer.

### <a name="cryptographic-methods"></a>Kryptografiska metoder

NetX Secure TLS implementerar DES, 3DES, AES, MD5, HMAC-MD5, SHA-1, HMAC-SHA1, SHA-256, HMAC-SHA256, RSA och ECC (valda kurvor) i programvara med maskinvarudrivrutiner för vissa maskinvaruplattformar. Ett program kan använda de kryptografiska rutiner som medföljer NetX Secure eller använda anpassade rutiner som tillhandahålls av slutanvändaren eller tredje part.

Den *NX_CRYPTO_METHOD är* ett kontrollblock som utformats för ett program för att beskriva en viss implementering av en kryptografisk algoritm som ska användas med NetX Secure TLS. Med NX_CRYPTO_METHOD *kan ett* program enkelt integrera sin egen kryptografiimplementering i NetX Secure. Strukturen *NX_CRYPTO_METHOD* deklareras som:

```C
typedef struct NX_CRYPTO_METHOD_STRUCT
{
    /* Symbolic name of the algorithm. */
    USHORT nx_crypto_algorithm;

    /* Size of the key, in bits. */
    USHORT nx_crypto_key_size_in_bits;

    /* Size of the IV block, in bits, used for encryption. */
    USHORT nx_crypto_IV_size_in_bits;

    /* Size of the ICV block, in bits, used for authentication. */
    USHORT nx_crypto_ICV_size_in_bits;

    /* Size of the crypto block, in bytes. */
    ULONG nx_crypto_block_size_in_bytes;

    /* Size of the metadata area. */
    ULONG nx_crypto_metadata_size;

    /* nx_crypto_init function initializes the crypto method with the
        "secret key" or other state  information. The initialization 
        routine should return a handle to the caller.  This handle is 
        used in subsequent crypto operations to identify the session.  
        */

    UINT (*nx_crypto_init) (NX_CRYPTO_METHOD     *method,
                            UCHAR               *key, 
                            NX_CRYPTO_KEY_SIZE   key_size_in_bits,
                            VOID               **handler,
                            VOID                *crypto_metadata,
                            VOID                 crypto_metadata_size);

    /* NetX Secure calls the nx_crypto_cleanup routine when a TLS
       session is to be deleted (or updated).  Resources allocated 
       during the crypto operation should be released in this routine.  
       */
    UINT (*nx_crypto_cleanup) (VOID *handler);

    /* nx_crypto_operation is the actual crypto or hash operation. Note 
       that both input and output buffers are prepared by the caller. 
       For encryption or decryption operations, the crypto operation 
       routine uses the output buffer for encrypted or decrypted data. 
       For authentication operations, the authentication routine shall 
       use the output buffer for the digest. */
    UINT (*nx_crypto_operation)(UINT  op, 
                  VOID              *handler, 
                  NX_CRYPTO_METHOD  *method,
                  UCHAR             *key,
                  NX_CRYPTO_KEY_SIZE key_size_in_bits,
                  UCHAR             *input,
                  ULONG              input_length_in_byte,
                  UCHAR             *iv_ptr,
                  UCHAR             *output,
                  ULONG              output_length_in_byte,
                  VOID              *crypto_metadata,
                  VOID               crypto_metadata_size,
                  NX_PACKET*         packet_ptr,
                  VOID (*nx_crypto_hw_process_callback(NX_PACKET 
                                                       *packet_ptr, 
                                                        UINT status);
} NX_CRYPTO_METHOD;
```

Nedan visas beskrivningen av varje element i *NX_CRYPTO_METHOD* struktur:

- nx_crypto_algorithm: Det här fältet identifierar algoritmen  som beskrivs i variabelmetoden Vissa giltiga värden för NetX Secure TLS är följande (se nx_crypto_const.h för specifika värden):
    
  - NX_CRYPTO_NONE    
  - NX_CRYPTO_ENCRYPTION_NULL    
  - NX_CRYPTO_ENCRYPTION_AES_CBC    
  - NX_CRYPTO_AUTHENTICATION_NONE    
  - TLS_HASH_SHA_1    
  - TLS_HASH_SHA_256    
  - TLS_HASH_MD5    
  - TLS_CIPHER_RSA    
  - TLS_CIPHER_NULL

- nx_crypto_key_size_in_bits: Det här fältet anger storleken på den hemliga nyckel som används av metoden .

- nx_crypto_IV_size_in_bits: Det här fältet anger storleken på initieringsvektorn (IV). Observera att I de flesta fall används IV-blocket endast för krypterings-/dekrypteringsalgoritmer. Autentiserings- och verifieringsalgoritmer använder sällan det här fältet.

- nx_crypto_ICV_size_in_bits: Det här fältet anger storleken på ICV-blocket (Integrity Check Value). Obs! Det här blocket är för IPsec-användning och används inte i TLS. Mer information finns i NetX Duo IPsec.

- nx_crypto_block_size_in_bytes: Det här fältet anger storleken på det kryptografiska algoritmblocket för blockbaserade chiffer i byte. I de flesta fall används detta av krypteringsrutiner och sällan av autentiseringsrutiner.

- nx_crypto_metadata_area_size: Det här fältet anger storleken på det metadataområde som den här metoden kräver. Varje implementering kan kräva visst minne för att lagra tillståndsinformation eller för att lagra mellanliggande data (till exempel nyckeltransformeringsmaterial) eller för att använda som ett scratch-område. Mängden utrymme som krävs av en implementering anges i det här fältet. Programmet tillhandahåller minnesutrymmet när du skapar en TLS-session. Den kryptografiska funktionen ansvarar för att hantera det här metadataområdet.

- nx_crypto_init: Det här är initieringsfunktionen för den kryptografiska algoritmen. För en implementering som inte behöver en initieringsrutin kan det här fältet anges till NX_NULL. En typisk användning av en initieringsfunktion är att initiera algoritmens interna datastruktur. NetX Secure TLS hanterar initiering av den kryptografiska rutinen genom att anropa den här funktionen internt.

Prototypen för initieringsfunktionen är:

```C
UINT crypto_init_function(NX_CRYPTO_METHOD *method, 
                          UCHAR *key, 
                          UINT  key_size_in_bits, 
                          VOID  **handle, 
                          VOID  *crypto_metadata_area, 
                          ULONG crypto_metadata_area_size);
```

  - -metoden är en pekare till kontrollblocket för kryptometoden.

  - nyckeln är den hemliga nyckelsträngen för bearbetning av datapaketen.

  - key_size_in_bits definierar storleken på den hemliga nyckeln i bitar.

  - handle är ett implementeringsdefinierat objekt som identifierar en viss kryptografisession. Värdet genereras av initieringsrutinen och skickas tillbaka till anroparen. Den efterföljande kryptografiåtgärden eller rensningsrutinen använder den här referensen för att identifiera sessionen.

  - crypto_metadata är en pekare till metadataområdet som krävs av implementeringen av den här algoritmen. För algoritmer som inte behöver ett metadataområde anges det här fältet till NX_NULL och initieringsrutinen får inte komma åt metadataområdet.

  - crypto_metadata_size anger storleken på metadataområdet. För SAs som skapats utan metadataområde är det här fältet inställt på noll och initieringsrutinen får inte komma åt metadataområdet.

  - Den här rutinen *NX_SUCCESS* om initieringen lyckas. Anroparen behandlar andra returvärden som fel.

- nx_crypto_cleanup: Det här är rensningsrutinen som definierats för implementeringen av en krypteringsalgoritm. Den anropas när en TLS-session tas bort eller startas om.

Prototypen för rensningsfunktionen är:

```C
UINT crypto_cleanup_function(VOID *handle);
```
- -referensen skickas till rensningsfunktionen av anroparen. Referensen initieras av kryptografiinitieringsrutinen och används för att identifiera tillståndet för krypteringsalgoritmen.

- Den här *rutinen NX_SUCCESS* om rensningsprocessen lyckas. Anroparen behandlar andra returvärden som fel.

- nx_crypto_operation: Det här är rutinen som utför de faktiska krypterings-, dekrypterings- och autentiseringstjänsterna. Åtgärdsrutinens funktionsprototyp är:

```C
UINT crypto_operation_function(UINT   op,
          VOID  *handle,  
          NX_CRYPTO_METHOD* method,
          UCHAR *key,
          UCHAR  key_size_in_bits,
          UCHAR* input,
          ULONG  input_length_in_byte,
          UCHAR* iv_ptr,
          UCHAR* output,
          ULONG  output_length_in_byte,
          VOID *crypto_metadata,
          ULONG crypto_metadata_size,
          NX_PACKET *packet_ptr,
          VOID (*nx_crypto_hw_process_callback)(NX_PACKET 
                          *packet_ptr, UINT status));
```

- op anger vilken typ av åtgärd som den här rutinen förväntas utföra. Giltiga värden är:
    
    - NX_CRYPTO_ENCRYPT
    - NX_CRYPTO_DECRYPT
    - NX_CRYPTO_AUTHENTICATE
    - NX_CRYPTO_VERIFY

- -referensen skickas till åtgärdsfunktionen av anroparen. Den genereras av krypteringsinitieringsrutinen.
- metoden pekar på kontrollblocket för kryptometoden
- pekar på den hemliga nyckel som används för den här åtgärden
- key_size_in_bits är storleken på den hemliga nyckeln i bitar
- input (indata) är en pekare till början av meddelandet som ska köras.
- input_length_in_byte skickas av anroparen för att ange storleken på meddelandet som ska köras.
- iv_ptr konfigureras av anroparen för att peka på början av ett IV-block. Observera att minnet för IV-blocket tillhandahålls av anroparen. För kryptering ska åtgärdsfunktionen skriva IV-informationen till det här minnesblocket. för dekryptering ska åtgärdsfunktionen hämta IV-informationen från det här minnesblocket. Algoritmer för autentiserings- och verifieringsåtgärd använder vanligtvis inte initieringsvektorn.
- utdata konfigureras av anroparen för att peka på en utdatabuffert. Observera att minnet för utdatabufferten tillhandahålls av anroparen. För kryptering ska åtgärdsfunktionen skriva chiffertexten till utdatabufferten. för dekryptering ska åtgärden skriva den avkodade texten (klartext) till utdatabufferten; för autentisering ska hash-värdet skrivas till utdatabufferten. För verifiering används utdatabufferten för att lagra hash-information.
- output_length_in_byte anger storleken på utdatabufferten
- crypto_metadata pekar på det metadataområde som ska användas av den här kryptografiåtgärden. Området med kryptometadata initieras vanligtvis av crypto_init_function.
- crypto_metadata_size anger storleken på metadataområdet.
- Den här *rutinen NX_SUCCESS* returnerar information om åtgärdsprocessen lyckas. Anroparen behandlar andra returvärden som fel.
- packet_ptr: Paketet som innehåller de data som bearbetas. Obs! Den här parametern används inte av TLS och ska anges till NX_NULL.
- nx_crypto_hw_process_callback: En återanropsfunktion som tillhandahålls av krypteringsmetoden. Detta används om kryptofunktionen tillhandahålls av maskinvara och kräver en återanropsrutin.

NetX Secure TLS tillhandahåller följande krypteringsmetoder:

- *AES*  
- *RSA*  
- *Null*

NetX Secure TLS tillhandahåller följande autentiseringsmetoder:

- *HMAC-MD5*  
- *HMAC-SHA1*  
- *HMAC-SHA256*

I följande exempel visas hur du konfigurerar *NX_CRYPTO_METHOD* för att använda krypterings- och autentiseringsmetoderna som tillhandahålls av NetX Duo IPsec.

***Aes:***

```C
/* AES-CBC 128. */
NX_CRYPTO_METHOD crypto_method_aes_cbc_128 = 
{
    /* AES crypto algorithm                             */
    NX_CRYPTO_ENCRYPTION_AES_CBC,                       

    /* Key size in bits. For AES-128 this value is 128  */
    NX_CRYPTO_AES_128_KEY_LEN_IN_BITS,              
   
    /* IV size in bits.  For AES-128 this value is 128  */
    NX_CRYPTO_AES_IV_LEN_IN_BITS,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  For AES this value is 16   */
    (NX_CRYPTO_AES_BLOCK_SIZE_IN_BITS >> 3),        

    /* Metadata size in bytes, for AES this value is 262*/
    sizeof(NX_CRYPTO_AES),              

    /* AES-CBC initialization routine.                  */
    _nx_secure_crypto_method_aes_init,               

    /* AES-CBC cleanup routine, not used.               */
    NX_NULL,                                        

    /* AES-CBC operation                                */
    _nx_secure_crypto_method_aes_operation           
};

/* RSA. */
NX_CRYPTO_METHOD crypto_method_rsa = 
{
    /* RSA crypto algorithm                             */
    TLS_CIPHER_RSA,                       

    /* Key size. RSA key sizes vary, so set to 0.         */
    0,              
   
    /* IV size in bits.  RSA does not use an IV.         */
    0,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  RSA does not have a block size. */
    0,        

    /* Metadata size in bytes, for RSA use the control block. */
    sizeof(NX_CRYPTO_RSA),              

    /* RSA initialization routine.                  */
    _nx_secure_crypto_method_rsa_init,               

    /* Cleanup routine, not used.                    */
    NX_NULL,                                        

    /* RSA operation                                */
    _nx_secure_crypto_method_rsa_operation           

};
```
***Null***

```C
/* NULL encryption method. */
NX_CRYPTO_METHOD crypto_method_null = 
{
    NX_CRYPTO_ENCRYPTION_NULL,/* Name of the crypto algorithm  */
    0,                        /* Key size in bits, not used    */
    0,                        /* IV size in bits, not used     */
    0,                        /* ICV size in bits, not used    */
    4,                        /* Block size in bytes           */
    0,                        /* Metadata size in bytes        */
    NX_NULL,                  /* Initialization routine,unused */
    NX_NULL,                  /* Cleanup routine, not used     */
    _nx_secure_crypto_method_null_operation  /* NULL operation  
*/
}; 
```
***HMAC-SHA1***
```C
NX_CRYPTO_METHOD crypto_method_hmac_sha1 = 
{
    /* HMAC SHA1 algorithm                               */
    TLS_HASH_SHA1,            


    /* Key size in bits. For HMAC-SHA1 this value is 160 */ 
    NX_CRYPTO_HMAC_SHA1_KEY_LEN_IN_BITS,              

    /* IV size in bits, not used                         */
    0,                                            

    /* Transmitted ICV size in bits. Unused.             */
    0, 

    /* Block size in bytes, not used                     */
    0,                                            

    /* Metadata size in bytes                            */
    sizeof(NX_SHA1_HMAC),                                            

    /* Initialization routine, not used                  */
    NX_NULL,                                      

    /* Cleanup routine, not used                         */
    NX_NULL,                                          

    /* HMAC SHA1 operation                               */
    _nx_secure_crypto_method_hmac_sha1_operation   
};
```
***Ingen***

En särskild metod **NX_CRYPTO_NONE** används för att signalera IPsec-modulen att krypteringen eller autentiseringstjänsten inte krävs. Den konfigureras på följande sätt:

```C
/* NX_CRYPTO_NONE means encryption or authentication
   method is not needed.  */
NX_CRYPTO_METHOD crypto_method_none = 
{
    NX_CRYPTO_NONE,       /* Name of the crypto algorithm */
    0,                    /* Key size in bits, not used   */
    0,                    /* IV size in bits, not used    */
    0,                    /* ICV size in bits, not used   */
    0,                    /* Block size in bytes          */
    0,                    /* Metadata size in bytes       */
    NX_NULL,              /* Initialization routine, not used */
    NX_NULL,              /* Cleanup routine, not used    */
    NX_NULL               /* NULL operation               */
};                                               
```
### <a name="initializing-tls-with-cryptographic-methods"></a>Initiera TLS med kryptografiska metoder

När du har skapat dina kryptografiska rutiner som överensstämmer med signaturerna för kryptografimetoden som beskrivs i föregående avsnitt måste du skicka dem till TLS när du initierar ett NX_SECURE_TLS_SESSION-kontrollblock. Detta görs i TLS-nx_secure_tls_session_create:

```C
UINT  nx_secure_tls_session_create(
              NX_SECURE_TLS_SESSION*     session_ptr,
              const NX_SECURE_TLS_CRYPTO*    tls_cipher_table,
              VOID*                encryption_metadata_area,
              ULONG                 encryption_metadata_size
);
```
- session_pointer är en pekare till ditt NX_SECURE_TLS_SESSION kontrollblock.
- tls_cipher_table är en pekare till ett NX_SECURE_TLS_CRYPTO kontrollblock som beskrivs nedan.
- encryption_metadata_area pekar på utrymme som används av kryptografiska rutiner i TLS.
- encryption_metadata_size är storleken på metadataområdet i byte.

### <a name="elliptic-curve-cryptography-ecc-in-netx-secure-tls"></a>ECC (Elliptic Curve Cryptography) i NetX Secure TLS

ECC (Elliptic Curve Cryptography) tillhandahåller ett kryptografischema med offentliga nycklar som kan användas i stället för RSA. ECC är vanligtvis snabbare och använder mindre nycklar än RSA, så det kan vara ett värdefullt alternativ för inbäddad TLS. I X-Ware-versioner före Azure RTOS 6.0 levererades ECC som ett tillägg, vilket krävde installation av ECC-källkoden i projektet. Azure RTOS 6.0 integrerad ECC i huvudkodbasen så att du inte längre behöver installera ECC-filerna. ECC kräver dock fortfarande samma initiering som de tidigare versionerna.

### <a name="supported-ecc-curves"></a>ECC-kurvor som stöds

NetX Secure implementerar delar av kurvorna enligt <http://www.secg.org/sec2-v2.pdf> . Följande kurvor stöds<sup>18:</sup>

  - secp256r1 
  - secp384r1 
  - secp521r1 

Om andra ECC-kurvor används *returnerar nx_secure_tls_session_start()-rutinen* felet NX_SECURE_TLS_NO_SUPPORTED_CIPHERS anger att kurvor som inte stöds har använts.

Observera att även TLS-certifikatkedjan kan krypteras av ECC-algoritmer. Även om de kurvor som tillhandahålls av TLS-klienten stöds, är det möjligt att ECC-kurvan som används i certifikatkedjan inte stöds. I det här fallet *nx_secure_tls_session_start* rutinen NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER.

Ett standardexempel på chiffertabell för ECC finns i nx_crypto_generic_ciphersuites.c. Mer information om chiffertabeller finns i avsnittet "Kryptografisk TLS-chiffertabell".

18. Observera att implementeringar för kurvorna secp192r1 och secp224r1 också tillhandahålls för äldre program. Dessa kurvor anses dock vara svaga och bör inte användas för ny programutveckling.

### <a name="crypto-methods-for-ecc"></a>Kryptometoder för ECC

Kryptometoder för Elliptic Curve-grupper:

- NX_CRYPTO_METHOD crypto_method_ec_secp192<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp224<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp256;  
- NX_CRYPTO_METHOD crypto_method_ec_secp384;  
- NX_CRYPTO_METHOD crypto_method_ec_secp521;

Krypteringsmetoderna för ECC-kurvor definieras i nx_crypto_generic_ciphersuites.c.

Kryptometod för ECDHE:

- NX_CRYPTO_METHOD crypto_method_ecdhe;

Kryptometod för ECDSA:

- NX_CRYPTO_METHOD crypto_method_ecdsa;

Kryptografimetoderna ECDSA och ECDHE definieras i nx_crypto_generic_ciphersuites.c.

I kombination med andra kryptografimetoder som RSA, SHA och AES kan de användas som byggstenar för chiffersvituppslagstabellen.

### <a name="enabling-ecc-support-for-tls"></a>Aktivera ECC-stöd för TLS

ECC är aktiverat som standard för TLS. Om du vill inaktivera ECC-stöd måste NX_SECURE_DISABLE_ECC_CIPHERSUITE måste definieras.

För att ändringen ska gälla måste du återskapa NetX Secure Library och alla program som använder det biblioteket.

I programkoden måste API:et *n x_secure_tls_ecc_initialize()* anropas när TLS-sessionen har skapats. Det här API:et meddelar TLS-sessionen vilken typ av kurvor som ska användas för TLS-nyckelutbytesåtgärder och certifikatverifiering. Om en ECC-algoritm väljs under TLS-handskakningsfasen, växlar klienten och servern ECC-kurvarelaterade parametrar för att avgöra vilken kurva som ska användas.

Följande kodsegment illustrerar hur du använder API:et. Observera att argumenten (*nx_crypto_ecc_supported_groups, nx_crypto_ecc_supported_groups_size och nx_crypto_ecc_curves)* definieras i *nx_crypto_generic_ciphersuites.c*. Därför kan dessa symboler användas direkt.

```C
status = nx_secure_tls_ecc_initialize(&tls_session,     
                    nx_crypto_ecc_supported_groups,      
                    nx_crypto_ecc_supported_groups_size,     
                    nx_crypto_ecc_curves);
```
Exempelkonfigurationen i nx_crypto_generic_ciphersuites.c innehåller en ECC-chifferssuite-uppslagstabell som används när ECC är aktiverat. Om du vill använda ECC skickar nx_crypto_tls_ciphers_ecc som chiffertabellparameter när du skapar TLS-sessioner med nx_secure_tls_session_create. Exempeltabellen innehåller både ECC- och icke-ECC-chiffer.

### <a name="tls-cryptographic-cipher-table"></a>Kryptografisk TLS-chiffertabell

Strukturen NX_SECURE_TLS_CRYPTO definieras som:

```C
typedef struct NX_SECURE_METHODS_STRUCT
{
    /* Table that maps ciphersuites to crypto methods. */
    NX_SECURE_TLS_CIPHERSUITE_INFO* nx_secure_tls_ciphersuite_lookup_table;
    USHORT nx_secure_tls_ciphersuite_lookup_table_size;

    /* Table that maps X.509 cipher identifiers to crypto methods. */
    NX_SECURE_X509_CRYPTO *nx_secure_tls_x509_cipher_table;
    USHORT nx_secure_tls_x509_cipher_table_size;

    /* Specific routines needed for specific TLS versions. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_md5_method;
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha1_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_1_method;
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha256_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_sha256_method;
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    const NX_CRYPTO_METHOD *nx_secure_tls_hkdf_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_hmac_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_ecdhe_method;
#endif

} NX_SECURE_TLS_CRYPTO;
```
Tabellen skapas genom att fylla i posterna för den här strukturen i en statisk konstant som finns i NetX Secure TLS-projektet, som vanligtvis finns med kryptografiska rutiner och moduler.

Till exempel innehåller det kryptografiska biblioteket för enbart programvara ("generisk") som medföljer NetX Secure följande tabelldefinition (för chiffersvit som inte är ECC-stöd<sup>19</sup>):

```C
/* Define the cipher table object we can pass into TLS. */
const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers =
{
    /* TLS Ciphersuite lookup table and size. */
    _nx_crypto_ciphersuite_lookup_table,
    sizeof(_nx_crypto_ciphersuite_lookup_table) / 
    sizeof(NX_SECURE_TLS_CIPHERSUITE_INFO),

    /* X.509 certificate cipher table and size. */
    _nx_crypto_x509_cipher_lookup_table,
    sizeof(_nx_crypto_x509_cipher_lookup_table) / sizeof(NX_SECURE_X509_CRYPTO),

    /* TLS version-specific methods. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    &crypto_method_md5,
    &crypto_method_sha1,
    &crypto_method_tls_prf_1,
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    &crypto_method_sha256,
    &crypto_method_tls_prf_sha_256
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    &crypto_method_hkdf,
    &crypto_method_hmac,
    &crypto_method_ecdhe,
#endif
};
```
I strukturen är den första posten TLS-chiffertabellen. Strukturen NX_SECURE_TLS_CIPHERSUITE_INFO kryptografiska rutiner (i form av NX_CRYPTO_METHOD pekare) till specifika chiffer som definieras i TLS-specifikationerna. Det andra värdet är antalet poster i tabellen som det första fältet pekar på.

Nästa fält pekar på en tabell med rutiner som används av X.509 när digitala certifikat bearbetas och strukturen för NX_SECURE_X509_CRYPTO liknar NX_SECURE_TLS_CIPHERSUITE_INFO. Följande fält är antalet poster i tabellen.

Efter uppslagstabellen finns ett antal rutiner som behövs för specifika versioner av TLS. Innan TLS version 1.2 till exempel var nyckelgenereringen och handskakningens hash-rutiner fasta för att använda en kombination av SHA-1 och MD5 – metoderna för dessa rutiner anropas specifikt i chifferstrukturen eftersom de inte är knutna till specifika chiffer. I TLS version 1.2 väljs nyckelgenererings- och hash-rutinerna av chiffersviten, men för chiffer som inte anger vilka rutiner som ska användas används SHA-256-hashmetoden och chifferstrukturen anger den rutinen specifikt.

TLS 1.3 kräver några extra specifika chiffer för olika åtgärder.

19. Observera att TLS 1.3-stöd kräver ECC – använd nx_crypto_tls_ciphers_ecc TLS 1.3 är aktiverat.

### <a name="tls-ciphersuite-lookup-table"></a>TLS Ciphersuite Lookup Table

Om du vill fylla i chiffertabellen för TLS måste du också skapa en chifferuppslagstabell som mappar kryptografiska rutiner till specifika chifferidentifierare. Identifierarna är IANA-registrerade värden som är universella. Mer information finns i TLS RFCs. Rutinerna representerar de fem separata metoderna som används i varje chiffer (vissa chiffer kanske inte använder alla 5): offentlig chiffer, autentisering med offentlig nyckel, sessionschiffrering, sessionshashrutin och TLS Pseudo-Random Function (PRF). I följande tabell beskrivs var och en av de 5 metoderna:

| **Rutinkategori**      | **Beskrivning**                                                                                       | **Exempelalgoritmer**                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Offentligt chiffer             | Används för att utbyta nycklar under TLS-handskakningen                                                        | RSA, Diffie-Hellman, ECC                                          |
| Autentisering med offentlig nyckel | Används för att autentisera eller signera data under TLS-handskakningen                                            | RSA, DSS                                                          |
| Sessionschiffrering            | Symmetrisk nyckelalgoritm som används för att kryptera programdata under TLS-sessionen                       | AES, RC4                                                          |
| Sessionshash              | Används för att bevara integriteten för meddelanden under TLS-sessionen (garanterar att data inte har ändrats) | SHA-1, SHA-256                                                    |
| TLS PRF                   | Används för att generera nyckelmaterial och i handskakningshashar i TLS-handskakningen                          | PRF baseras på hash-rutiner – SHA-1 + MD5, SHA-256, SHA-512 |

Strukturen NX_SECURE_TLS_CIPHERSUITE_INFO definieras på följande sätt:

```C
typedef struct NX_SECURE_TLS_CIPHERSUITE_INFO_struct
{
    /* The IANA value of the ciphersuite as defined by the TLS spec.*/
    USHORT nx_secure_tls_ciphersuite;

    /* The Public Key operation in this suite - RSA or DH. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_cipher;

    /* The Public Authentication method used for signing data. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_auth;

    /* The session cipher being used - AES, RC4, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_session_cipher;

    /* The size of the initialization vectors for the session cipher (bytes).*/
    USHORT nx_secure_tls_iv_size;

    /* The key size for the session cipher (bytes). */
    UCHAR nx_secure_tls_session_key_size;

    /* The hash being used - MD5, SHA-1, SHA-256, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_hash;

    /* The size of the hash being used. SHA-1 is 20 bytes, MD5 is 16 bytes.*/
    USHORT nx_secure_tls_hash_size;

    /* The TLS PRF being used – this is only for TLSv1.2. */
    NX_CRYPTO_METHOD *nx_secure_tls_prf;

} NX_SECURE_TLS_CIPHERSUITE_INFO;
```
Fältet nx_secure_tls_ciphersuite innehåller IANA-chiffersvitvärdet och de NX_CRYPTO_METHOD pekarna representerar de 5 metoder som används av chiffersviten. Skalära värden (nx_secure_tls_iv_size, nx_secure_tls_key_size och nx_secure_tls_hash_size) är information, vilket ger information som kanske inte är tillgänglig i NX_CRYPTO_METHOD poster.

Som exempel tittar vi på standard chifferuten för TLS, TLS_RSA_WITH_AES_128_CBC_SHA, som anger användning av RSA, AES-CBC med 128-bitars nycklar och SHA-1 för sessions-hashing. Ingen TLS PRF har angetts för detta chifferuten, så i TLSv1.2-läge använder den standard-SHA-256 PRF. Observera att alla chiffer använder SHA-1+MD5 PRF i TLS 1.0 och 1.1, oavsett vilken PRF som anges i tabellen.

Posten i den NX_SECURE_TLS_CIPHERSUITE_INFO i det allmänna kryptografiska biblioteket definieras på följande sätt:

```C
{ 
  TLS_RSA_WITH_AES_128_CBC_SHA,     /* Ciphersuite identifier */
  &crypto_method_rsa,               /* Public-key cipher (NX_CRYPTO_METHOD)*/
  &crypto_method_rsa,               /* Authentication method(NX_CRYPTO_METHOD)*/
  &crypto_method_aes_cbc_128,       /* Session cipher method(NX_CRYPTO_METHOD)*/
  16,                               /* Session cipher IV size in bytes */
  16,                               /* Session cipher key size in bytes */
  &crypto_method_hmac_sha1,         /* Session hash routine(NX_CRYPTO_METHOD) */
  20,                               /* Session hash output size in bytes */
  &crypto_method_tls_prf_sha_256    /* TLSv1.2 PRF */
},
```

Observera att nyckelstorleken för sessionschiffret bestäms av chiffer, men för metoderna med offentlig nyckel är nyckelstorleken inte känd förrän TLS-handskakningen är på gång eftersom de offentliga nycklarna finns i de digitala certifikat som utbyts under handskakningen.

### <a name="x509-cipher-lookup-table"></a>X.509 Chiffer, uppslagstabell

Precis som NX_SECURE_TLS_CIPHERSUITE_INFO mappar NX_SECURE_X509_CRYPTO kryptografiska rutiner till kända värden. När det gäller X.509 är identifierarna faktiskt OID:er som definieras av X.509 och registrerade med ISO- och ITU-standardkropparna. OID:er är variabellängdsvärden med flera byte som utformats för att unikt identifiera olika information i olika telekommunikationsstandarder, inklusive kryptografiska rutiner som används i digitala certifikat. Eftersom OID är variabel längd mappar NetX Secure TLS de officiella OID-värdena till konstanter med fast längd som används internt (se nx_secure_x509.h). Dessa konstanter används i NX_SECURE_X509_CRYPTO struktur, som definieras enligt följande:

```C
/* Structure to hold X.509 cryptographic routine information. */
typedef struct NX_SECURE_X509_CRYPTO_struct
{
    /* Internal NetX Secure identifier for certificate "ciphersuite" which consists
       of a hash and a public key operation. These can be mapped to OIDs in X.509.
        */
    USHORT nx_secure_x509_crypto_identifier;

    /* Public-Key Cryptographic method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_public_cipher_method;

    /* Hash method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_hash_method;
} NX_SECURE_X509_CRYPTO;
```

Det första fältet, *nx_secure_x509_crypto_identifier*, är den interna OID-representationen som används av NetX Secure.

Det andra och tredje fältet pekar NX_CRYPTO_METHOD objekt som representerar de kryptografiska metoder som identifieras av OID, en åtgärd med offentlig nyckel som är parad med en hashrutin. Observera att varje digitalt certifikat kan ha fler än en OID för kryptografiska rutiner.

Metodtabellen för X.509 skapas på samma sätt som ciphersuite-uppslagstabellen. Vi ska till exempel titta på OID för RSA_SHA1. Det faktiska OID-RSA_SHA1 är följande:

```C
{iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1) sha1-with-rsa-
signature(5)}
```
OID representeras i ASN.1-syntax och har ett numeriskt värde på 1.2.840.113549.1.1.5. Det här värdet kodas sedan i binärt format och skapar följande byte:

```C
UCHAR RSA_SHA1_OID = { 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x05 };
```
Den faktiska konverteringen från ASN.1 till binärformatet ligger utanför omfånget för det här dokumentet. Sök efter ASN.1-kodningar för OID för mer information. Den binära representationen av de OID:er som stöds av NetX Secure finns i *filen nx_secure_x509.c*.

När vi har en mappning av den faktiska OID:en till en internt igenkänd konstant kan vi skapa en post för RSA_SHA1 i NX_SECURE_X509_CRYPTO-tabellen:

```C
{ 
    NX_SECURE_TLS_X509_TYPE_RSA_SHA_1,    /* Internal OID constant. */
    &crypto_method_rsa,                   /* RSA method (NX_CRYPTO_METHOD). */ 
    &crypto_method_sha1                   /* SHA-1 method (NX_CRYPTO_METHOD). */
}, 
```
### <a name="default-tls-routines"></a>TLS-standardrutiner

Som nämnts ovan kräver TLS vissa standardrutiner för nyckelgenerering och meddelandeverifiering under handskakningen. Den primära rutinen är TLS Pseudo-Random Function eller PRF. PRF baseras på hash-rutiner och kan användas för att generera en godtycklig mängd pseudoslumpdata<sup>20</sup> för nyckelgenerering eller andra ändamål.

Förutom PRF använder varje version av TLS standard-hash-rutiner som också måste tillhandahållas. För TLS version 1.0 och 1.1 är dessa hash-rutiner MD5 och SHA-1. TLS version 1.2 kräver endast SHA-256.

I NX_SECURE_TLS_CRYPTO-strukturen finns det NX_CRYPTO_METHOD-pekare för MD5, SHA-1, SHA-256, TLS version 1.0/1.1 PRF och standard-PRF för TLS 1.2.

TLS 1.3-stöd lägger till fält för HKDF (nyckelgenerering), HMAC (för specifika hash-åtgärder som används under handskakningen) och ECDHE (krävs för TLS 1.3-funktioner).

I det allmänna biblioteket för programvarukryptografi finns programvaruversioner av TLS PRF. För TLS 1.0/1.1 kallas den här funktionen *för nx_crypto_tls_prf_1*. För TLS 1.2 kallas funktionen *för nx_secure_tls_prf_sha256*. Suffixet "1" representerar den äldre PRF-referensen för TLS 1.0 och suffixet "sha256" syftar på det faktum att TLS 1.2-standard-PRF baseras på SHA-256. När stöd för andra PRF-rutiner krävs återspeglar suffixet för dessa rutiner den hash-metod som används. Eftersom PRF-rutinerna baseras på hash-metoder kan de underliggande hash-rutinerna maskinvaruaccelereras oberoende av olika målplattformar.

Förutom TLS-chiffer- och X.509-uppslagstabellerna kan standardrutinen för PRF och hash fyllas i NX_SECURE_TLS_CRYPTO-strukturen och användas för att initiera en TLS-session.

20. "Pseudoslump" syftar på det faktum att PRF är deterministiskt, vilket innebär att den alltid producerar samma utdata med samma indata, men slumpmässigt i det faktum att utdata inte är förutsägbara. TLS använder den här egenskapen för PRF för att generera sessionsnycklar från olika offentliga data i kombination med huvudhemligheten som utbyts under handskakningen med hjälp av en chiffer för offentlig nyckel som RSA.

### <a name="cryptographic-metadata"></a>Kryptografiska metadata

Innan vi kan initiera TLS-sessionen med NX_SECURE_TLS_CRYPTO-tabellen måste vi allokera buffertutrymme för kryptografiska rutinmetadata. Metadata används för att lagra alla tillstånd som är associerade med en viss rutin, som representeras av dess kontrollblock. Fältet *nx_crypto_metadata_area_size* för varje NX_CRYPTO_METHOD måste anges till storleken på den kontrollstruktur som är associerad med den rutinen, annars kommer TLS-initieringen inte att ta hänsyn till det utrymme som behövs, vilket kan orsaka problem med buffertöverskridning.

Innan TLS-sessionen skapas måste metadatabufferten allokeras. Bufferten delas automatiskt upp med nx_secure_tls_session_create och utrymme reserveras för var och en av de rutiner som anges i tabellen med kryptografiska metoder. Observera att eftersom endast en chiffer är aktiv i taget i en TLS-session påverkar inte antalet chiffersuiter det nödvändiga metadatautrymmet – utrymmet är reserverat för var och en av de 5 chiffersvitrutinerna med den maximala blockstorleken för kontrollen för den kategorin i chifferssuite-uppslagstabellen.

För att göra det enkelt att beräkna metadatabuffertstorleken *utför nx_secure_metadata_size_calculate* samma beräkningar som nx_secure_tls_session_create men returnerar helt enkelt den totala nödvändiga metadatabuffertstorleken i byte.

### <a name="initializing-the-tls-session"></a>Initiera TLS-sessionen

När NX_CRYPTO_METHOD och NX_SECURE_TLS_CRYPTO har skapats och metadataområdet har reserverats kan vi initiera en TLS-session på följande sätt (värden som tas från ovanstående exempel):

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Cryptographic routine metadata buffer. Size is determined by calling 
nx_secure_tls_metadata_size_calculate with the nx_crypto_tls_ciphers table referenced 
above. */
UCHAR crypto_metadata[4500];

/* Initialize our TLS session using our cipher table and metadata area. Note that we can 
use sizeof for the metadata array because the size parameter expects the size in bytes.*/

nx_secure_tls_session_create(
    &tls_session,            /* Pointer to TLS session.      */
    &nx_crypto_tls_ciphers,  /* Pointer to cipher table.     */
    crypto_metadata,         /* Cryptography metadata buffer.*/
    sizeof(crypto_metadata), /* Size of metadata buffer.     */
);
```
