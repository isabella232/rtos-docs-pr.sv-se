---
title: Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX Secure
description: Det här kapitlet innehåller en funktions Beskrivning av NetX Secure TLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c28ad0255f99986a4ddfe5faefad81e70840e5e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825686"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-secure"></a>Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX Secure

## <a name="execution-overview"></a>Översikt över körning

Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX Secure TLS. Det finns två primära typer av program körning i ett NetX Secure TLS-program: initierings-och program gränssnitts anrop. 

*NetX Secure förutsätter att ThreadX och NetX/NetXDuo finns. Från ThreadX kräver det tråd körning, avstängning, periodiska timers och ömsesidiga undantags funktioner. Från NetX/NetXDuo krävs det funktioner och driv rutiner för TCP/IP-nätverk.*

## <a name="transport-layer-security-tls-and-secure-sockets-layer-ssl"></a>Transport Layer Security (TLS) och Secure Sockets Layer (SSL)

Secure Network Protocol-komponenten i NetX Secure är en implementering av Transport Layer Security-protokollet (TLS) som beskrivs i RFC 2246 (version 1,0), 4346 (version 1,1), 5246 (version 1,2) och 8446 (version 1,3). Det ingår också stöd för Basic X. 509 (RFC 5280).

NetX Secure TLS stöder TLS-versionerna 1,2 och 1,3. Implementeringar tillhandahålls för nu-föråldrade TLS 1,0 och TLS 1,1, men de måste uttryckligen initieras och rekommenderas inte för användning i nya produkter.

*Secure Sockets Layer* (SSL) var det ursprungliga namnet på TLS innan det blev standard i RFC 2246 och "SSL" används ofta som ett generiskt namn för TLS-protokollen. Den senaste versionen av SSL var 3,0 och TLS 1,0 kallas ibland SSL version 3,1. Alla versioner av det officiella "SSL"-protokollet betraktas som föråldrade och oskyddade och för närvarande NetX Secure ger inte SSL-implementering.

TLS anger ett protokoll för att generera *sessionsnycklar* som skapas under TLS- *handskakningen* mellan en TLS-klient och-server och dessa nycklar används för att kryptera data som skickas av programmet under TLS- *sessionen.*

TLS-data är indelade i *poster* som är likvärdiga med ett TCP-paket. Varje TLS-post har en rubrik, och TLS-krypterade poster har också en sidfot (kontroll Summa hash). TLS-handskaknings poster har ett ytterligare sidhuvud inkapslat i den större TLS-posten. TLS-posten kapslas av transport skiktets nätverks protokoll på samma sätt som ett TCP-paket kapslas av ett IP-paket.

### <a name="tls-13"></a>TLS 1,3

I augusti 2018 slutfördes TLS 1,3-specifikationen. Den nya versionen av protokollet är en ganska viktig uppdatering som ändrar vissa grundläggande aspekter av den underliggande säkerheten och prestandan hos TLS. Dessa ändringar är dock i stort sett osynliga för den typiska TLS-användaren, eftersom de tillämpas främst på TLS-hand skaknings tillstånds dator och skapande av sessionsnyckel. Ett antal valfria funktioner och tillägg har också lagts till. Följande är en sammanfattning av ändringarna och hur de påverkar TLS-funktioner.

- Hand skaknings datorn optimerades genom att ett helt utbyte av meddelanden togs bort från servern.
- Generering av nycklar har uppdaterats för att använda en standardiserad rutin som kallas HKDF (HMAC-baserad nyckel härledning) och sambandet med sessionsnycklar till alla hand skaknings meddelanden (i stället för några val parametrar).
- Alla TLS 1,2 och tidigare krypteringssviter är föråldrade och är inkompatibla med TLS 1,3. På samma sätt går det inte att använda alla TLS 1,3-krypteringssviter med tidigare versioner.
- Alla TLS 1,3-krypteringssviter ger PFS (Perfect Forward Secrecy) med tillfälliga nycklar<sup>6</sup> 
- TLS 1,3 tar bort "Message Authentication Code" (MAC) i varje post till förmån för att använda AEAD<sup>7</sup> -chiffer
- Vissa ytterligare valfria funktioner lades till, inklusive 0-alternativ (Zero-fördröjning) som gör att program data kan skickas under hand skakningen. 0-sökalternativ är helt valfria och stöds för närvarande inte i Azure återställnings tider TLS.

TLS 1,3 påverkar inte användar programmen avsevärt. API: et är exakt detsamma mellan versionerna, och krypteringssviter markeras så att en enda ciphersuite-tabell kan användas.

För att kunna använda TLS 1,3 måste makro NX_SECURE_TLS_ENABLE_TLS_1_3 globalt definieras. TLS 1,3 är inaktiverat som standard i Azure återställnings tider TLS.

6. "Tillfälliga" nycklar är asymmetriska nyckel par som genereras under TLS-handskakningen och används för hemligheter som Exchange endast för den sessionen. Nyckel paret tas bort efter användningen – detta hindrar en angripare från att kunna komma åt krypterade data i en inspelad TLS-session även om en privat certifikat nyckel komprometteras när som helst, i framtiden – därmed "Perfect Forward Secrecy".

7. Autentiserad kryptering med associerade data – ett läge för chiffer som AES som kombinerar kryptering och integritets kontroll i en enda åtgärd, vilket eliminerar behovet av en separat hash av data för integritets kontroll.

### <a name="tls-record-header"></a>TLS-posthuvud

Alla giltiga TLS-poster måste ha ett TLS-huvud, som visas i fel! Referens källan hittades inte.

![Diagram över en TLS-post-rubrik.](media/image2.png)

Bild 1 – TLS-posthuvud

Fälten i TLS-postrubriken definieras enligt följande:

| Fält för TLS-huvud | Syfte     |
| ---------------- | ------------- |
| **8-bitars meddelande typ** | Det här fältet innehåller den typ av TLS-post som skickas. Giltiga typer är följande:<br />-ChangeCipherSpec<sup>8</sup>: 0x14<br />-Avisering: 0x15<br />-Hand skakning: 0x16<br />– Program data: 0x17 |
| **16-bitars protokoll version** | Det här fältet innehåller TLS-protokollets version. Giltiga värden är följande:<br />-SSL 3,0:0x0300<br />-TLS 1,0:0x0301<br />-TLS 1,1:0x0302<br />-TLS 1,2:0x0303<br />- **TLS 1,3 <sup>9</sup>**: **0x0303** |
| **16-bitars längd** | Det här fältet innehåller längden på de data som kapslats i TLS-posten. |

8. I TLS 1,3 används inte längre ChangeCipherSpec-meddelandet, trots att det fortfarande kan skickas av kompatibilitetsinställningar, vilket innebär att meddelandet ignoreras.

9. TLS 1,3 skulle tekniskt ha värdet 0x0304 om schemat fortsatte, men protokollet ändrades till att ha den faktiska protokoll versionen i ett tillägg, så alla TLS 1,3-poster använder 0x0303 i protokoll versions fält för bakåtkompatibilitet.

### <a name="tls-handshake-record-header"></a>Post rubrik för TLS-handskakning

Alla giltiga TLS-handskaknings poster måste ha en TLS-handskakning-rubrik, som visas i bild 2.

![Diagram över en post rubrik för TLS-handskakning.](media/image3.png)

Bild 2 – post rubriken TLS-handskakning

Fälten i post rubriken TLS-handskakning definieras enligt följande:

| Fält för TLS-huvud | Syfte |
| ---------------- |----------------------- |
| **8-bitars meddelande typ** | Det här fältet innehåller den typ av TLS-post som skickas. Giltiga typer är följande:<br />-ChangeCipherSpec<sup>10</sup>: 0x14<br />-Avisering: 0x15<br />-Hand skakning: 0x16<br />– Program data: 0x17 |
| **16-bitars protokoll version** | Det här fältet innehåller TLS-protokollets version. Giltiga värden är följande:<br />-SSL 3,0:0x0300<br />-TLS 1,0:0x0301<br />-TLS 1,1:0x0302<br />-TLS 1,2:0x0303<br />- **TLS 1,3 <sup>11</sup>**: **0x0303** |
| **16-bitars längd**    | Det här fältet innehåller längden på de data som kapslats i TLS-posten. |
| **8-bitars hand Skaknings typ** | Det här fältet innehåller meddelande typen hand skakning. Giltiga värden är följande (* meddelanden i **fetstil** har lagts till i TLS 1,3):<br />-HelloRequest: 0x00<br />-Sitt hälsnings: 0x01<br />-ServerHello: protokollnumret 0x02<br />- **HelloVerifyRequest**: **0x03**<br />- **NewSessionTicket**: **0x04**<br />- **EndOfEarlyData**: **0x05**<br />- **EncryptedExtensions**: **0x08**<br />-Certifikat: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />-ClientKeyExchange: 0x10<br />-Färdig: 0x14<br />- **Uppdatering** av **0x18:**<br />- **MessageHash**: **0xFE** |
| **24-bitars längd**    | Det här fältet innehåller längden på hand skaknings meddelande data. |

10. I TLS 1,3 används inte längre ChangeCipherSpec-meddelandet, trots att det fortfarande kan skickas av kompatibilitetsinställningar, vilket innebär att meddelandet ignoreras.

11. TLS 1,3 skulle tekniskt ha värdet 0x0304 om schemat fortsatte, men protokollet ändrades till att ha den faktiska protokoll versionen i ett tillägg, så alla TLS 1,3-poster använder 0x0303 i protokoll versions fält för bakåtkompatibilitet.

### <a name="the-tls-handshake-and-tls-session"></a>TLS-handskakning och TLS-session

En typisk TLS-handskakning (version 1.0-1.2) visas i bild 3. En TLS-handskakning börjar när TLS-klienten skickar ett *sitt hälsnings* -meddelande till en TLS-server, vilket indikerar att de vill starta en TLS-session. Meddelandet innehåller information om den kryptering som klienten vill använda för sessionen, tillsammans med information som används för att generera sessionsnycklar senare i hand skakningen. Alla meddelanden i TLS-handskakningen är inte krypterade tills sessionsnycklarna har skapats. TLS 1,3 ändrar hand skakningen lite – detaljerna presenteras i nästa avsnitt.

TLS-servern svarar på sitt hälsnings med ett ServerHello-meddelande som anger ett val från de krypterings alternativ som tillhandahålls av klienten. ServerHello följs av ett certifikat meddelande där servern tillhandahåller ett digitalt certifikat för att autentisera sin identitet för klienten. Slutligen skickar servern ett ServerHelloDone-meddelande som anger att det inte finns några fler meddelanden att skicka. Servern kan eventuellt skicka andra meddelanden efter ServerHello och i vissa fall kan det inte skicka ett certifikat meddelande, och därför måste ServerHelloDone-meddelandet.

När klienten har tagit emot alla serverns meddelanden har den tillräckligt med information för att generera sessionsnycklar. TLS gör detta genom att skapa en delad bit av slumpmässiga data som kallas för *huvud hemlighet*, som är en fast storlek och som används som ett Seed för att generera alla nycklar som behövs när kryptering har Aktiver ATS. Hemligheten för huvud repliken krypteras med algoritmen för offentlig nyckel (t. ex. RSA) som anges i Hello-meddelandena (se nedan för information om algoritmer för offentliga nycklar) och den offentliga nyckel som tillhandahålls av servern i dess certifikat. En valfri TLS-funktion som kallas för delade nycklar (PSK) aktiverar krypteringssviter som inte använder ett certifikat utan använder i stället ett hemligt värde som delas mellan värdarna (vanligt vis via fysisk överföring eller annan säker metod). Den delade hemligheten används för att generera den överordnade hemligheten i stället för att använda ett krypterat meddelande för att skicka den överordnade hemligheten. Se avsnittet om i förväg delade nycklar nedan.

Den krypterade hemligheten på huvud sidan skickas till servern i ClientKeyExchange-meddelandet. Servern, vid mottagning av ClientKeyExchange-meddelandet, dekrypterar hemligheten för huvud repliken med dess privata nyckel och fortsätter att generera sessionsnycklar parallellt med TLS-klienten.

När sessionsnycklarna har genererats kan alla ytterligare meddelanden krypteras med hjälp av algoritmen för privat nyckel (t. ex. AES) som valts i Hello-meddelandena. Ett slutligt okrypterat meddelande som kallas ChangeCipherSpec skickas av både klienten och servern för att indikera att alla ytterligare meddelanden kommer att krypteras.

Det första krypterade meddelandet som skickas av både klienten och servern är också det sista TLS-handskaknings meddelandet, som kallas slutfört. Det här meddelandet innehåller en hash av alla handskaknings meddelanden som har tagits emot och skickats. Denna hash används för att kontrol lera att inget av meddelandena i hand skakningen har manipulerats eller skadats (vilket innebär att säkerheten kan brytas).

När de färdiga meddelandena tas emot och hand skaknings-hasharna har verifierats börjar TLS-sessionen och programmet börjar skicka och ta emot data. Alla data som skickas på endera sidan under TLS-sessionen hashas först med den hash-algoritm som valts i Hello-meddelandena (för att tillhandahålla meddelande integritet) och krypteras med den valda algoritmen för privat nyckel med de genererade sessionsnycklarna.

Slutligen kan en TLS-session endast avslutas om antingen klienten eller servern väljer att göra det. En trunkerad session betraktas som en säkerhets överträdelse (eftersom en angripare kan försöka förhindra att alla data som skickas tas emot) så att ett särskilt meddelande skickas när någon sida vill avsluta sessionen, som kallas en CloseNotify-avisering. Både klienten och servern måste skicka och bearbeta en CloseNotify-avisering för att en lyckad session ska kunna stängas.

![Diagram över en typisk TLS-handskakning.](media/image4.png)

Bild 3 – typisk TLS-handskakning

### <a name="tls-13-handshake"></a>TLS 1,3-handskakning

TLS 1,3 är en ganska stor översyn av TLS-protokollet. Den stora delen av ändringarna har gjorts i hand skakningen för att öka säkerheten och prestandan. En typisk TLS 1,3-handskakning visas i bild 4. Den primära skillnaden kan ses i antalet utbyten mellan servern och klienten.

I TLS 1,2 och tidigare skickar servern två flygningar<sup>12</sup> av meddelandena – först ServerHello och sedan ett ChangeCipherSpec-meddelande innan det krypterade slutförda meddelandet som avslutar hand skakningen skickas. I TLS 1,3 skickar servern allting i den första flygningen – ServerHello, tillägg, certifikat och avslutad. ChangeCipherSpec-meddelandet eliminerades och servern genererar dess sessionsnycklar och börjar kryptera hand skaknings meddelanden direkt efter ServerHello.

Den nya överenskommelsen innebär att mer av TLS-handskakningen skyddas av kryptering, vilket begränsar mängden klartext-data som en angripare kan komma åt. Dessutom innebär borttagningen av den andra server flygningen (som bara var en ChangeCipherSpec följt av en sluten) att en TLS-klient inte längre behöver vänta på att starta sändningen av program data – så snart klienten skickar ett eget slutfört meddelande till sessionen startas sessionen.

12. En flygning är bara en samling TLS-meddelanden som skickas samtidigt i en grupp.

![Diagram över en TLS 1,3-handskakning.](media/image5.png)

Bild 4 – TLS 1,3-handskakning

> [!NOTE]
> *TLS 1,3 introducerade även begreppet "tidiga data" och 0-efter namn (svars tid, ingen fördröjning), vilket innebär att vissa program data kan skickas i den första flygningen av meddelanden. Den här valfria funktionen har lagts till främst som en optimering för webbläsarens svars tid (t. ex. för att skicka tidig HTTP-huvuden för att börja återge en sida). Den här funktionen stöds inte från och med Azure återställnings tider 6,0.*

### <a name="initialization"></a>Initiering

TCP/IP-stacken NetX eller NetXDuo måste initieras innan du använder NetX Secure TLS. I användar handboken för NetX eller NetXDuo hittar du information om hur du initierar TCP/IP-stacken korrekt.

När NetX TCP/IP-stack har initierats kan TLS aktive ras. Internt hanteras all TLS-nätverkstrafik och bearbetning av NetX/NetXDuo-stacken utan att användaren behöver vidta några åtgärder. TLS har dock vissa särskilda krav som måste hanteras separat från den underliggande nätverks stacken. Dessa parametrar har tilldelats TLS Control Block som kallas ***NX_SECURE_TLS_SESSION** _ med hjälp av tjänsten _ *_nx_secure_tls_session_create_**.

TLS har två lägen, en server och en klient, som kan aktive ras i ett program (men bara ett läge per NetX-socket) och varje har sina egna specifika krav, som beskrivs nedan.

I båda läge kräver NetX Secure TLS att en TCP-socket (***NX_TCP_SOCKET** _) skapas och konfigureras för TCP-kommunikation med fjärrvärden. TCP-socketen tilldelas till en TLS-session med rollen _ *_nx_secure_tls_session_start_**, som beskrivs nedan.

### <a name="initialization--tls-server"></a>Initiering – TLS-server

Förutom en TCP-socket kräver NetX Secure TLS server mode ett *digitalt certifikat*, vilket är ett dokument som används för att identifiera TLS-servern för den anslutande TLS-klienten och certifikaten motsvarande *privata nyckel*, vanligt vis för RSA-krypteringsalgoritmen. International tele Union X. 509 standard anger det certifikat format som används av TLS och det finns flera verktyg för att skapa X. 509 digitala certifikat.

För NetX Secure TLS måste X. 509-certifikatet vara Binary-kodat med Distinguished Encoding Rules (DER)-formatet för ASN. 1. DER är standard TLS-formatet för TLS-överföring för certifikat.

Den privata nyckeln som är associerad med det tillhandahållna certifikatet måste vara i DER-Encoded PKCS # 1-format. Den privata nyckeln används bara på enheten och skickas aldrig över kabeln. Se till att privata nycklar är säkra eftersom de ger säkerhet för TLS-kommunikation!

Om du vill initiera TLS-servercertifikatet måste programmet tillhandahålla en pekare till en buffert som innehåller det DER-kodade X. 509-certifikatet och valfri DER-kodad PKCS # 1-RSA-nyckel data med hjälp av tjänsten ***nx_secure_x509_certificate_intialize** _, som fyller i *NX_SECURE_X509_CERT**-strukturen med lämpliga certifikat data som ska användas av TLS.

När Server certifikatet har initierats måste det läggas till i TLS-kontroll-blocket med hjälp av tjänsten ***nx_secure_tls_local_certificate_add*** .

När serverns certifikat har lagts till i TLS Control Block kan socketen användas för att upprätta en säker TLS-server anslutning.

### <a name="initialization--tls-client"></a>Initiering – TLS-klient

NetX Secure TLS client mode kräver ett *betrott certifikat Arkiv*, som är en samling X. 509 digitala certifikat från betrodda certifikat utfärdare (ca: er). Dessa certifikat antas av att TLS-protokollet är "betrott" och fungerar som underlag för att autentisera certifikat som tillhandahålls av TLS server-entiteter för att NetX säker TLS-klient.

Ett certifikat för betrodd certifikat utfärdare kan antingen vara *självsignerat* eller signerat av en annan certifikat utfärdare, vilket innebär att certifikatet kallas *mellanliggande ca* (ICA). I ett typiskt TLS-program tillhandahåller servern ICA-certifikat tillsammans med dess server certifikat, men det enda kravet för lyckad autentisering är att en kedja av utfärdare (certifikat som används för att signera andra certifikat) kan spåras från Server certifikatet tillbaka till ett certifikat för betrodd certifikat utfärdare i det betrodda certifikat arkivet. Den här kedjan kallas en  *kedja av förtroende* eller en *certifikat kedja*.

För att initiera en betrodd certifikat utfärdare eller ett ICA-certifikat måste programmet tillhandahålla en pekare till en buffert som innehåller det DER-kodade X. 509-certifikatet med hjälp av tjänsten ***nx_secure_x509_certificate_intialize** _, som fyller i strukturen _ *NX_SECURE_X509_CERT** med lämpliga certifikat data som ska användas av TLS.

Betrodda certifikat som har initierats läggs sedan till i TLS-kontroll-blocket med hjälp av tjänsten ***nx_secure_tls_trusted_certificate_add*** . Om du inte lägger till ett certifikat Miss lyckas TLS-klientcertifikatet eftersom det inte finns något sätt för TLS-protokollet att autentisera fjärr-TLS-serverns värdar.

TLS-klienten behöver också utrymme för att det inkommande server certifikatet ska tilldelas (förutsatt att ett i förväg delad nyckel läge inte används). Från och med NetX Secure TLS 5,12 är det inte längre nödvändigt för programmet att allokera utrymme för Fjärrcertifikatet. Men det äldre alternativet att allokera utrymme för ett Server certifikat är fortfarande tillgängligt och användare som tilldelats certifikat kommer att användas före den interna certifikat buffertens optimering <sup>13</sup> – mer information finns i ***nx_secure_tls_remote_certificate_allocates*** tjänsten.

När det betrodda certifikat arkivet har skapats och utrymmet för Server certifikatet har allokerats kan socketen användas för att upprätta en säker TLS-klient anslutning.

13. Optimeringen använder "Packet buffer" som tillhandahålls av användar programmet till TLS-sessionen med hjälp av *nx_secure_tls_session_packet_buffer_set* för att allokera X. 509-parsningsfel i stället för att använda de användar strukturer som används i tidigare versioner av netx Secure TLS. Det är osannolikt att det uppstår en certifikat kedja som överskrider storleken på paketets buffert, vilket innebär att paketets buffertstorlek kan ökas eller att *nx_secure_tls _remote_certificate_allocate* kan användas för att allokera mer utrymme för certifikat kedjan.

### <a name="application-interface-calls"></a>Program gränssnitts anrop

NetX Secure TLS-program gör vanligt vis att funktions anrop inifrån program trådar som körs under ThreadX-återställnings tider. Vissa initieringar, särskilt för underliggande nätverks protokoll för nätverks kommunikation (t. ex. TCP och IP) kan anropas från ***tx_application_define *.** Mer information om hur du initierar nätverkskommunikation finns i användar handboken för NetX/NetXDuo.

TLS utnyttjar krypterings rutiner som är processor intensiva åtgärder. De här åtgärderna utförs vanligt vis inom ramen för anrop av tråd.

### <a name="tls-session-start"></a>TLS-session-start

TLS kräver ett underliggande nätverks protokoll för transport skikt för att fungera. Protokollet används vanligt vis för TCP. För att upprätta en NetX Secure TLS-session måste en TCP-anslutning upprättas med hjälp av NetX/NetXDuo TCP API. En **NX_TCP_SOCKET** måste skapas och en anslutning upprättas med hjälp av **_nx_tcp_server_socket_listen_*_ och _*_nx_tcp_server_socket_accept_*_ tjänster (för TLS-server) eller _*_nx_tcp_client_socket_connect_** -tjänsten (för TLS-klienten).

När en TCP-anslutning har upprättats skickas TCP-socketen till ***nx_secure_tls_session_start*** tjänsten.

### <a name="tls-packet-allocation"></a>Allokering av TLS-paket

NetX Secure TLS använder samma paket struktur som NetX/NetXDuo TCP (***NX_PACKET** _), förutom att i stället för att anropa tjänsten _*_nx_packet_allocate_*_ måste tjänsten _ *_nx_secure_tls_packet_allocate_** ANROPAs så att utrymmet för TLS-huvudet kan allokeras korrekt.

### <a name="tls-session-send"></a>Sändning av TLS-session

När TLS-sessionen har startats kan programmet skicka data med hjälp av tjänsten ***nx_secure_tls_session_send** _. Sändnings tjänsten är identisk med den _*_nx_tcp_socket_send_*_ tjänsten, med en _*_NX_PACKET_*_ data struktur som innehåller de data som skickas. endast dessa data krypteras av den säkra TLS-stacken för NX innan de skickas, och paketet måste allokeras med _ *_nx_secure_tls_packet_allocate_* *.

### <a name="tls-session-receive"></a>Mottagning av TLS-session

När TLS-sessionen har startats kan programmet ta emot data med hjälp av tjänsten ***nx_secure_tls_session_receive** _. Precis som TLS-sessionen skickar, är den här tjänsten identisk med _ *_nx_tcp_socket_receive_* *, förutom att inkommande data dekrypteras och verifieras av TLS-stacken innan de returneras i paket strukturen.

### <a name="tls-session-close"></a>Sessionen stängs av TLS

När en TLS-session har slutförts måste både TLS-klienten och servern skicka en CloseNotify-avisering till den andra sidan för att stänga av sessionen. Båda sidorna måste ta emot och bearbeta aviseringen för att säkerställa att en lyckad session stängs av.

Om fjärrvärden skickar en CloseNotify avisering, bearbetar alla anrop till ***nx_secure_tls_session_receive** _-tjänsten aviseringen, skickar motsvarande avisering tillbaka till fjärrvärden och returnerar värdet _ *_NX_SECURE_TLS_SESSION_CLOSED_* *. När sessionen har stängts Miss lyckas eventuella ytterligare försök att skicka eller ta emot data med den TLS-sessionen.

Om programmet vill stänga TLS-sessionen måste tjänsten ***nx_secure_tls_session_end** _ anropas. Tjänsten kommer att skicka CloseNotify-aviseringen och bearbeta svars CloseNotify. Om svaret inte tas emot returneras ett felvärde på _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, vilket indikerar att TLS-sessionen inte stängdes på rätt sätt, vilket möjliggör en säkerhets överträdelse.

### <a name="tls-alerts"></a>TLS-aviseringar

TLS är utformat för att ge maximal säkerhet, så alla Errant beteenden i protokollet betraktas som en potentiell säkerhets överträdelse. Av den anledningen betraktas eventuella fel vid meddelande bearbetning eller kryptering/dekryptering av allvarliga fel som avslutar hand skakningen eller sessionen omedelbart.

Vid hantering av fel i ett lokalt program är det relativt enkelt att ta reda på att ett fel har inträffat för att hantera situationen på ett korrekt sätt och förhindra ytterligare eventuella säkerhets överträdelser. Därför skickar TLS ett *varnings* meddelande till fjärrvärden vid eventuella fel.

Aviseringar behandlas på samma sätt som andra TLS-meddelanden och krypteras under sessionen för att förhindra att en angripare samlar in information från den typ av avisering som tillhandahålls. Under hand skakningen är de skickade aviseringarna begränsade inom räckvidden för att begränsa den mängd information som kan erhållas av en potentiell angripare.

CloseNotify-aviseringen som används för att stänga TLS-sessionen är den enda icke-allvarliga varningen. Även om det anses vara en avisering och skickas som ett varnings meddelande, är en CloseNotify till skillnad från andra aviseringar i att det inte indikerar att ett fel har uppstått.

Avisering svärdet och "level" (nivåer är "varning" och "oåterkallelig" – de flesta TLS-aviseringar är "oåterkalleliga") definieras i TLS RFC och anger vilken typ av fel som inträffat. De flesta TLS-aviseringar än CloseNotify kan betraktas som en indikation på ett eventuellt säkerhets problem och resulterar i att TLS-sessionen eller hand skakningen avbryts. Om ett TLS API-anrop returnerar **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) kan API-tjänsten **_nx_secure_tls_session_alert_value_get_** (ny i NetX Secure TLS version 5,12) användas för att hämta TLS-aviseringens värde och nivå för det program som ska användas för alla beslut om svar på säkerhets frågor. I de flesta fall bör aviseringar som tagits emot från andra fjärrvärddatorer än CloseNotify betraktas som ett allvarligt fel, även om det finns några excptions – mer information finns i TLS-rapporterna.

### <a name="tls-session-renegotiation"></a>Omförhandling av TLS-session

TLS stöder begreppet "omförhandling" som bara är en omförhandling av TLS-sessionens parametrar inom kontexten för en befintlig TLS-session. Vad det innebär i praktiken är att de nya hand skaknings meddelandena krypteras och autentiseras med den befintliga sessionen. Omförhandling används när en TLS-värd vill generera nya sessionsnycklar (t. ex. generera nya TLS-sessionsnycklar) utan att behöva slutföra den befintliga sessionen. Till exempel kan omförhandlingen vara önskvärd när säkerhets principer för ett program dikterar att sessionsnycklar endast används under en begränsad tid, men en TLS-session förblir aktiv utanför den tiden.

Ett problem med omförhandlad session är att gör TLS sårbart för en speciell person-in-the-Middle-attack där en angripare kan övertyga en server att initiera en omförhandling med nya parametrar, vilket innebär att angriparen kan kapa TLS-sessionen. För att undvika det här problemet introducerades tillägget för säker omförhandling (se avsnitts **fel! Referens källan hittades inte.** avsnittet).

NetX Secure TLS har fullständigt stöd för omförhandlingar av sessioner och det säkra tillägget för säker omförhandling.

När du tar emot data från en fjärran sluten värd hanteras renegotations (och tillägget) automatiskt utan program interaktion. Om ett meddelande om att omförhandlingar om sessioner önskas, kan ett återhandlings återanrop tillhandahållas med *nx_secure_tls_session_renegotiate_callback_set* -tjänsten. Återanropet anropas när en omförhandling begärs av fjärrvärden, vilket gör att programmet kan vidta åtgärder om så önskas.

Starta en omförhandling från en aktiv TLS-session genom att bara anropa *nx_secure_tls_session_renegotiate* -tjänsten på den önskade TLS-sessionen.

### <a name="tls-session-resumption"></a>Återupptagande av TLS-session

Återupptagning av TLS-sessioner bör inte förväxlas med omförhandling av sessionen, trots vissa likheter. Om omstarten av *sessionen innebär att* starta en ny hand skakning inom en befintlig TLS *-session* är sessionen återupptagning en helt valfri funktion som inbegriper omstart av en stängd TLS-session utan att utföra en fullständig TLS-handskakning. För att åstadkomma detta kan en TLS-implementering cachelagra sessionens parametrar och nycklar, och associera dem med ett *sessions-ID,* en unik identifierare som anges i den ursprungliga hand skakningen. Genom att tillhandahålla ett sessions-ID till en TLS-server anger en klient att en tidigare TLS-session mellan värdarna fanns och slutförts tidigare och att klienten fortfarande har tillstånd att återupprätta sessionen med en minskad hand skakning. Eftersom sessionsnycklarna är teoretiskt fortfarande hemliga och bara känd av de två kommunicerande värdarna, kan servern starta en ny TLS-session och kringgå det mesta av den normala hand skakningen.

Återupptagande av sessionen kan vara användbart för att undvika de potentiellt dyra offentliga nyckel åtgärder som används för att dela nyckeln för huvud hemligheten och verifiera certifikat, men det kräver också att sessionsnycklarna, nycklarna och crypotgraphic tillstånd bevaras i minnet för alla möjliga sessioner (minst för en konfigurerbar tids period).

Den aktuella versionen av NetX Secure TLS har inte stöd för att återuppta sessionen – sessions-ID: t ignoreras helt av TLS-servrar och TLS-klienter anger alltid ett NULL-sessions-ID som gör att servern kan utföra en fullständig hand skakning. Bristen på återupptagande av sessionen bör inte orsaka några Operability-problem eftersom det är en helt valfri funktion och alla TLS-implementeringar måste standardvärdet för en fullständig hand skakning om sessions-ID: t måste vara NULL eller okänd.

### <a name="protocol-layering"></a>Protokoll skikt

TLS-protokollet passar nätverks stacken mellan transport lagret (t. ex. TCP) och program skiktet. TLS anses ibland vara ett transport lager protokoll (till exempel *Transport Layer* Security), men eftersom det fungerar som ett program med avseende på de underliggande nätverks protokollen (t. ex. TCP) är det ibland grupperat i program lagret.

TLS kräver ett transport lager protokoll som stöder in-och förlustfri överföring, till exempel TCP. På grund av detta krav kan TLS inte köras ovanpå UDP eftersom UDP inte garanterar leverans av datagram. Ett separat protokoll som kallas *DTLS,* som är en modifierad version av TLS, används för program som behöver TLS-TLS över ett datagram-protokoll som UDP. NetX Secure stöder DTLS, men dokumentationen för DTLS är separat från det här dokumentet.

![Diagram över ett lager med TCP/IP-och TLS-protokoll.](media/image6.png)

Bild 5 – TCP/IP-och TLS Protocol-lager

## <a name="network-communications-security"></a>Säkerhet för nätverks kommunikation

Att skydda kommunikation över offentliga nätverk och Internet är ett kritiskt viktigt ämne och ämnet för ett stort antal böcker, artiklar och lösningar. Avsnittet är en bogglingly komplex, men det kan minskas till en enkel idé: att skicka information via ett nätverk så att endast det avsedda målet kan komma åt eller ändra informationen. Detta bryts ned i tre viktiga begrepp: sekretess, integritet och autentisering. TLS-protokollet tillhandahåller lösningar för alla tre.

### <a name="secrecy"></a>Hemliga

När du skickar data via ett nätverk är det ofta viktigt att data inte kan hämtas av en skadlig entitet. Om data skickas via en TCP/IP-anslutning kommer alla med åtkomst till nätverket att kunna läsa dessa data med hjälp av enkelt tillgängliga nätverks verktyg. För att förhindra att data hämtas, måste det kodas så att det inte kan läsas med undantag av det avsedda målet – detta är *Sekretess.* I TLS tillhandahåller krypteringsalgoritmer som RSA och AES sekretess.

### <a name="integrity"></a>Integritet

Ibland är sekretessen inte tillräckligt för att skydda data i ett nätverk. I vissa fall kan det vara möjligt för en skadlig enhet att ändra innehållet i ett TCP-paket utan att behöva känna till vad paketet innehåller. Krypterade data kan ändras, åter givning av dekrypteringen är ogiltig eller ändra parametrarna i meddelandet som leder till det resultat som angriparen kan vara intresse rad av. I nätverket kan vi inte hindra en angripare från att ändra data under överföringen, men vi kan tillhandahålla en mekanism för att veta om data har ändrats eller inte. När data ändras under överföringen är det känt och data kan avvisas. Det här konceptet är *integritet*. I TLS tillhandahålls integriteten av en klass av kryptografiska rutiner som kallas *hash-funktioner*. Några exempel på hash-funktioner är MD5 och SHA-1.

### <a name="authentication"></a>Autentisering

Det tredje viktiga konceptet i säkerheten för nätverks kommunikation är tanken att data endast bör förmedlas till det avsedda målet. En angripare kan försöka att utgöra en legitim entitet för att ta emot data som är avsedda för en annan värd. Även om data skickas med hemligheter och integritets mekanismer på plats kan angriparen fortfarande uppnå det önskade resultatet (ett hot mot säker kommunikation) via den här bedrägeri. För att förhindra detta krävs en mekanism för att bevisa identiteten för en fjärrvärd innan känsliga data skickas. Processen att bevisa identiteten för en fjärrvärd är *autentisering.* I TLS tillhandahålls autentiseringen med hjälp av digitala certifikat, hash-funktioner och en mekanism som kallas *digitala signaturer* som använder en egenskap för kryptering med offentliga nycklar (beskrivs nedan). En begränsad men användbar form av autentisering kan också tillhandahållas med en i *förväg delad nyckel* (PSK).

## <a name="tls-encryption"></a>TLS-kryptering

TLS-protokollet är ett ramverk för att tillhandahålla säker nätverkskommunikation över Internet användningen av kryptering. Kryptering definieras vanligt vis som processen att koda data på ett sådant sätt att det blir svårare att hämta ursprungliga data (eller information om dessa data *).* I dator system kryptering baseras på komplex matematik, till exempel begränsade fält och kan delas in i två typer: *privat nyckel* (eller *symmetrisk kryptering*) och *offentlig nyckel* (eller *asymmetrisk kryptering*). Exempel på kryptering av privata nycklar är AES (Advanced Encryption Standard) och RC4 (Rivest chiffer 4). Exempel på kryptering med offentliga nycklar är RSA (Rivest, Shamir, Adleson) och Diffie-Hellman chiffer.

TLS-protokollet använder både privat nyckel och krypterings rutiner för offentliga nycklar för att ge en balans mellan prestanda, säkerhet och flexibilitet.

### <a name="private-key-encryption"></a>Private-Key kryptering

Kryptering med privat nyckel används för tusentals år. Grundläggande avskrifts chiffer (där en bokstav eller ett ord ersätts av en annan icke-relaterad bokstav eller ord) är de tidigaste kända krypterings exemplen, men med ankomsten av informations åldern privat nyckel kryptering har du betydligt förbättrat.

En nyckel för privata nycklar använder en "nyckel" som bara är ett värde (som kan vara ett ord, en fras eller en siffra i det allmänna fallet) som används för att på ett sätt koda vissa data så att endast en entitet som hade åtkomst till nyckeln kan avkoda data på ett meningsfullt sätt. Nyckeln används både för kryptering och dekryptering av data, och därför är det andra namnet *symmetrisk kryptering*.

Chiffer för privata nycklar är i allmänhet snabba och relativt enkla att implementera, även om matematik risken är mer komplex. Av den anledningen använder TLS kryptering av privata nycklar för den stora mängden säker kommunikation.

Kryptering av privata nycklar har dock ett problem när vi försöker tillämpa den på allmän dator nätverkskommunikation: nyckeln måste delas mellan båda datorerna som försöker kommunicera. I det allmänna fallet är det opraktiskt och ofta omöjligt att kommunicera en privat nyckel på ett säkert sätt mellan två datorer på Internet, eftersom det kan antas att nätverks trafiken kan erhållas av valfritt antal entiteter i olika hopp som data tar när de dirigeras via Internet. Om nyckeln hämtas av en skadlig entitet komprometteras alla data som krypteras med den nyckeln. Eftersom de flesta datorer på Internet bara har en nätverks anslutning och inte en annan säker kanal för kommunikation, är tantamount för att skicka data okrypterade – den ger ingen säkerhet.

Av den anledningen räcker det inte med kryptering av privata nycklar för att implementera ett allmänt nätverks kommunikations säkerhets protokoll. Det är här som kryptering av offentliga nycklar kan hjälpa dig.

NetX Secure TLS stöder kryptering med privat nyckel för AES.

### <a name="public-key-encryption"></a>Public-Key kryptering

Till skillnad från kryptering med privat nyckel är kryptering av offentliga nycklar ett ganska nytt koncept, som har utvecklats i 1970. Om du använder ett koncept som kallas "Trap-dörr funktioner" i matematik upptäcktes det att det fanns ett sätt att dela en nyckel över ett nätverk utan att kompromissa med säkerheten hos krypterade data.

Det kan vara så att kryptering av offentliga nycklar fungerar att nyckeln (i den privata nyckel krypterings metoden som beskrivs ovan) delas upp i två delar, en *privat nyckel* och en *offentlig nyckel*, från vilken kryptering med offentlig nyckel får sitt namn. Konceptet är att en av dessa nycklar (vanligt vis den offentliga nyckeln) används för kryptering, medan den andra används för dekryptering. Den här asymmetry av nycklar är orsaken till det andra namnet för kryptering av offentlig nyckel: *asymmetrisk kryptering*.

Matematik krypteringen bakom kryptering i offentliga nycklar är ganska komplex, men tanken är att den offentliga nyckeln *bara* kan användas för kryptering och att hämtning av nyckeln inte tillåter att krypterade data hämtas. Den privata nyckeln är i sin tur det enda sättet att dekryptera data som krypteras med hjälp av den offentliga nyckeln. Genom att behålla hemligheten för privata nycklar behöver vem som helst som vill kommunicera säkert med ägaren av den privata nyckeln bara kryptera sina data med motsvarande offentliga nyckel med den kunskap som bara någon som har till gång till den privata nyckeln kan hämta säkra data.

NetX Secure TLS stöder RSA-kryptering med offentliga nycklar.

> [!IMPORTANT] 
> *RSA är en mycket processor intensiv åtgärd om program-RSA-implementeringen används. Större nyckel storlekar ökar den bearbetnings kraft som krävs av en kvadratisk faktor – 4X långsammare för en 2X ökning i nyckel storleken.*

### <a name="public-key-authentication"></a>Public-Key autentisering

En intressant sido effekt av krypterings konceptet för offentliga nycklar är att det kan användas för att tillhandahålla autentisering och kryptering genom att utföra åtgärden baklänges: Kryptera med hjälp av den *privata* nyckeln och dekryptera med hjälp av den *offentliga* nyckeln. Den faktiska mekanismen för att göra detta beror på vilka algoritmer för offentlig nyckel som används, men begreppet är detsamma.

För att autentisera med autentisering med offentlig nyckel krypterar ägaren av en privat nyckel vissa data (vanligt vis en kryptografisk hash av de data som ska autentiseras) med hjälp av den privata nyckeln. Sedan kan någon som vill autentisera att data kommer från ägaren av den privata nyckeln använda den associerade offentliga nyckeln för att dekryptera data – om dekrypteringen lyckas, och förutsatt att användaren har förtroende för att den offentliga nyckeln är giltig, kan användaren vara säker på att data kommer från ägaren av den privata nyckeln.

I TLS används autentisering med offentlig nyckel för att kontrol lera giltigheten hos ett digitalt certifikat som tillhandahålls av en TLS-server (och eventuellt TLS-klienten) med hjälp av offentliga nycklar från det betrodda certifikat arkivet. Certifikatet kontrol leras mot en offentlig nyckel i arkivet och data i certifikatet används för att kontrol lera serverns identitet.

NetX Secure TLS stöder RSA-autentisering.

### <a name="cryptographic-hashing"></a>Kryptografisk hashing

Kryptering är inte den enda kryptografiska åtgärd som används i TLS. För att kunna tillhandahålla meddelande integritet under en TLS-session krävs en kontroll summa för att säkerställa att meddelande innehållet inte har manipulerats. En enkel kontroll Summa (som används i TCP) är dock inte tillräckligt för att garantera en godtagbar integritets nivå eftersom den kan vara lätt att förenkla av en kunnig angripare. Mekanismen som används av TLS för att tillhandahålla meddelande integritet kallas *kryptografisk hash*.

Kryptering är en 1:1-kodning – det vill säga att hela den ursprungliga informationen kan hämtas från krypterade data. En hash mappar dock en godtycklig mängd data till ett fast storleks värde, precis som en kontroll summa. Till skillnad från en enkel kontroll summa är en hash särskilt utformad för att minska *kollisioner*, där olika indata resulterar i samma utdata. I en enkel kontroll summa, om en bit vänds från 1 till 0 och en annan bit från 0 till 1, är kontroll summan densamma. Med en kryptografisk hash skulle utdata variera avsevärt, vilket gör det svårt för en angripare att ändra de hashade data och att hash-åtgärden för de ändrade data fortfarande resulterar i samma värde (och därmed felaktigt verifierar integriteten för dessa data).

TLS använder ett antal olika hash-algoritmer för att tillhandahålla integritet för meddelanden, både program meddelanden och TLS-kontrollmeddelanden. Dessa inkluderar MD5, SHA-1 och SHA-256.

NetX Secure TLS stöder MD5-, SHA-1-och SHA-256-hashing.

## <a name="tls-extensions"></a>TLS-tillägg

TLS tillhandahåller ett antal tillägg som ger ytterligare funktioner för vissa program. Dessa tillägg skickas vanligt vis som en del av sitt hälsnings-eller ServerHello-meddelandena, vilket indikerar att en fjärrvärd vill använda ett tillägg eller tillhandahålla ytterligare information som används för att upprätta en säker TLS-session.

I allmänhet tillhandahåller tillägg valfria parametrar till TLS i början av hand skakningen som vägleder dig om åtgärderna. Vissa tillägg kräver programinformation eller besluts fattande, medan andra hanteras automatiskt.

I följande tabell beskrivs de TLS-tillägg som för närvarande stöds av NetX Secure TLS:

| **Tilläggs namn**              | **Beskrivning**              |
| ------------------------------- |----------------------------- |
| Säker omförhandlad indikering | Det här tillägget minskar risken för en man-in-the-Middle-attack som kan uppstå under en omförhandlande hand skakning.|
| Servernamnindikator          | Med det här tillägget kan en TLS-klient tillhandahålla ett särskilt DNS-namn till en TLS-server, vilket gör att servern kan välja rätt autentiseringsuppgifter (förutsätter att servern har flera identitets certifikat och nätverks-entrypoints). |
| Algoritmer för signaturer            | Med det här tillägget kan en TLS-klient tillhandahålla en lista över acceptabel signatur och hash-algoritmer till en TLS-server. |

Översikt över TLS-tillägg som stöds

### <a name="secure-renegotiation-indication"></a>Säker omförhandlad indikering

TLS har stöd för att utföra en hand skakning i en befintlig TLS-session, och därmed använda den etablerade sessionen för att kryptera hand skaknings meddelanden. Med den här processen kan de kryptografiska sessionsnycklarna återupprättas utan att du avslutar TLS-sessionen (se avsnittet "omförhandlingar av TLS-session").

När TLS hade använt omförhandling under en viss tid upptäcktes det att det uppstod ett problem med en man-in-the-Middle-attack som utnyttjade funktionen för omförhandling. För att stänga säkerhets problemet introducerades tillägget för säker omförhandlad indikering. I huvudsak används den färdiga meddelande-hashen från den upprättade anslutningen för att verifiera att de ursprungliga värdarna deltar i hand skakningen – i princip används hashen som en Verification-token under antagandet att en angripare inte kan falska hash (som kräver åtkomst till sessionsnycklarna).

NetX Secure TLS hanterar omförhandling automatiskt och använder tillägget för säker omförhandling som standard. Ingen program interaktion krävs.

### <a name="server-name-indication"></a>Servernamnindikator

Under TLS-handskakning förväntar en TLS-klient en fjärrserver för att tillhandahålla ett identitets certifikat så att klienten kan autentisera servern. Det kan dock finnas fall där en server tillhandahåller flera olika tjänster med olika "virtuella" servrar som har unika identiteter. Om det finns en enskild server med flera identiteter kan en TLS-klient ange ett visst DNS-namn som servern ska använda för att välja rätt autentiseringsuppgifter – mekanismen för att tillhandahålla detta namn är tillägget Servernamnindikator (SNI).

För ett program som använder SNI-tillägget krävs en del interaktion. För TLS-klienter måste programmet ange ett DNS-namn som ska skickas till fjärrservern. För TLS-servrar måste programmet läsa DNS-namnet från tillägget och välja ett lämpligt certifikat för att skicka tillbaka till klienten.

I följande avsnitt finns mer information om hur du använder SNI-tillägget i NetX Secure TLS.

### <a name="sni-extension--tls-client"></a>SNI-tillägg – TLS-klient

En NetX säker TLS-klient som vill använda SNI-tillägget måste ange ett DNS-namn som TLS ska tillhandahållas under hand skakningen. Det här namnet måste initieras och anges innan en TLS-session startas eftersom tillägget skickas i sitt hälsnings-meddelandet som startar hand skaknings processen.

Följande kodfragment illustrerar användningen av tillägget. Först initieras ett NX_SECURE_X509_DNS_NAME-objekt med det önskade Server namnet. Innan TLS-sessionen startas skickas namnet till TLS med hjälp av SNI-tilläggs-API: et. När namnet har angetts krävs ingen ytterligare åtgärd. Se API-referensen i kapitel 4  
  
Beskrivning av NetX säkra tjänster för mer information om de enskilda funktionerna.

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

På TLS-server sidan kan SNI-tillägget bearbetas av programmet för att välja rätt autentiseringsuppgifter (t. ex. certifikat) för att tillhandahålla fjärrklienten under hand skakningen. För att göra detta måste programmet ange ett motanrop som anropas efter att ett sitt hälsnings-meddelande har mottagits.

Exempel koden för nx_secure_tls_session_server_callback_set-API: et (se sidan 122) visar tolkningen av ett inkommande SNI-tillägg med ett Server återanrop. I princip tar TLS-servern emot en sitt hälsnings och anropar återanropet. Sedan använder programmet *nx_secure_tls_session_sni_extension_parse* -API: et för att parsa de tilläggs data som anges för återanropet för att hitta SNI-tillägget och returnera det angivna DNS-namnet (Observera att tillägget endast stöder ett enda DNS-namn). När namnet har hämtats använder programmet det för att hitta och skicka lämpligt Server identitets certifikat (och utfärdare om det är tillämpligt).

### <a name="signature-algorithms-extension"></a>Tillägg för signaturalgoritm

Det här tillägget är särskilt för TLS 1,2 och tillåter att en TLS-klient tillhandahåller en lista över acceptabla signaturer och hash-algoritmer som godkänns för användning i att skapa och verifiera digitala signaturer. Listan genereras automatiskt av NetX Secure TLS för TLS-klienter med hjälp av tabellen cipher som anges till *nx_secure_tls_session_create*. Ingen program interaktion krävs.

## <a name="authentication-methods"></a>Autentiseringsmetoder

TLS ger ramverket för att upprätta en säker anslutning mellan två enheter över ett oskyddat nätverk, men en del av problemet är att känna till enhetens identitet i den andra änden av anslutningen. Utan en mekanism för att autentisera identiteten för fjärranslutna värdar blir det en trivial åtgärd för en angripare att utgöra en betrodd enhet.

Inlednings vis kan det verka som att använda IP-adresser, MAC-adresser för maskin vara eller DNS ger en relativt hög exakthet för att identifiera värdar i ett nätverk, men med tanke på vilken typ av TCP/IP-teknik som kan vara falska och vilka adresser som kan vara falska och DNS-poster skadas (t. ex. genom DNS-cachelagring av data), är det klart att TLS behöver ett extra skydd mot bedrägliga identiteter.

Det finns olika mekanismer som kan ge detta extra lager av autentisering för TLS, men det vanligaste är det *digitala certifikatet.* Andra mekanismer är i förväg delade nycklar (PSK) och lösen ords scheman.

### <a name="digital-cerificates"></a>Digital certifikat

Digitala certifikat är den vanligaste metoden för att autentisera en fjärran sluten värd i TLS. I stort sett är ett digitalt certifikat ett dokument med en speciell formatering som ger identitets information för en enhet i ett dator nätverk.

TLS använder normalt ett format som kallas X. 509, en standard som utvecklats av International Telecommunication union, även om andra certifikat utfärdare kan användas om TLS-värdarna kan komma överens om det format som används. X. 509 definierar ett särskilt format för certifikat och olika kodningar som kan användas för att skapa ett digitalt dokument. De flesta X. 509-certifikat som används med TLS kodas med hjälp av en variant av ASN. 1, en annan telekommunikations standard. I ASN. 1 finns olika digitala kodningar, men den vanligaste kodningen för TLS-certifikat är Distinguished Encoding Rules (DER) standard. DER är en förenklad del av de grundläggande kodnings reglerna för ASN. 1 (BER) som är utformade för att vara entydiga, vilket gör det enklare att parsa. TLS-certifikat kodas vanligt vis i binärt DER, och detta är det format som NetX säkrar för X. 509-certifikat.

Även om DER-formaterade binära certifikat används i det faktiska TLS-protokollet kan de skapas och lagras i ett antal olika kodningar, med fil namns tillägg som. PEM,. CRT och. p12. Olika varianter används av olika program från olika tillverkare, men alla kan ofta konverteras till DER med hjälp av mycket tillgängliga verktyg.

De vanligaste av de alternativa certifikat kodningarna är PEM. PEM-formatet (från Privacy-Enhanced mail) är en Base-64-kodad version av DER-kodningen som ofta används eftersom kodningen resulterar i utskrivbar text som enkelt kan skickas via e-post eller webbaserade protokoll.

Att skapa ett certifikat för ditt NetX-säkra program ligger vanligt vis utanför omfånget för den här hand boken, men kommando rads verktyget OpenSSL ([www.openssl.org](http://www.openssl.org)) är mycket tillgängligt och kan konverteras mellan de flesta format.

Beroende på ditt program kan du skapa egna certifikat, tillhandahålla certifikat av en tillverkare eller myndighets organisation eller köpa certifikat från en kommersiell certifikat utfärdare.

Om du vill använda ett digitalt certifikat i NetX-skyddat program måste du först konvertera certifikatet till ett binärformat och eventuellt konvertera den associerade privata nyckeln ("privat exponent" för RSA, till exempel) till ett binärformat, vanligt vis en PKCS # 1-formaterad, DER-kodad RSA-nyckel eller en DER-kodad ECC-nyckel. När konverteringen är klar är det upp till dig att läsa in certifikatet och den privata nyckeln på enheten. Möjliga alternativ är att använda ett Flash-baserat fil system eller skapa en C-matris från data (med ett verktyg som "XXD" från Linux) och kompilera certifikatet och nyckeln till ditt program som konstant data.

När ditt certifikat har lästs in på enheten kan TLS-API: et användas för att associera certifikatet med en TLS-session.

Mer information och exempel på hur du använder X. 509-certifikat med NetX Secure TLS finns i avsnittet "Importera X. 509-certifikat till NetX Secure".

Mer information hittar du i följande TLS-tjänster i API-referensen:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add
- nx_secure_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Certifikats information för TLS-klient

TLS-klientens implementeringar kräver vanligt vis inte att "lokalt" certifikat<sup>14</sup> ska läsas in på enheten. Undantaget till detta är när autentisering av klient certifikat är aktiverat, men detta är mycket mindre vanligt.

En TLS-klient kräver minst ett "betrott" certifikat<sup>15</sup> som ska läsas in (mer kan läsas in om det behövs) och utrymme för ett "fjärran slutet" certifikat<sup>16</sup> att allokera.

Mer information om hur du lägger till betrodda certifikat och hur du allokerar utrymme för fjärrcertifikat finns i TLS API-referensen för följande tjänster: nx_secure_tls_remote_certificate_allocate nx_secure_tls_trusted_certificate_add.

14. Ett "lokalt" certifikat är ett certifikat som identifierar den lokala enheten – det vill säga den innehåller identitets information för enheten som TLS-programmet läses in på.

15. Ett "betrott" certifikat är ett certifikat som tillhandahåller en grund för förtroende och autentisering av fjär renheten, antingen direkt eller via en PKI (Public Key Infrastructure). Roten i förtroende kedjan kallas vanligt vis för en "certifikat utfärdare" eller CA-certifikat.

16. Ett "fjärran slutet" certifikat syftar på det certifikat som skickas av fjärrvärden under TLS-handskakningen. Den ger identitet för den fjärranslutna värden och autentiseras genom att jämföra den med ett "betrott" certifikat på den lokala enheten.

### <a name="tls-server-certificate-specifics"></a>Information om TLS-servercertifikat

TLS-serverimplementeringar kräver vanligt vis inte "betrodda" certifikat att läsas in på enheten eller fjärrcertifikaten som ska allokeras. Detta undantag är att när klient certifikatets autentisering är aktiverat (detta är mindre vanligt).

En TLS-server kräver att ett "lokalt" certifikat läses in så att servern kan ge den till fjärrklienten under TLS-handskakningen för att autentisera servern för klienten.

Mer information om hur du läser in lokala certifikat för användning med NetX TLS server-program finns i API-referensen för följande tjänster: 
- nx_secure_tls_local_certificate_add, 
- nx_secure_tls_local_certificate_remove.

### <a name="pre-shared-keys-psk"></a>I förväg delade nycklar (PSK)

En alternativ mekanism för att tillhandahålla identifierings autentisering i TLS är begreppet i förväg delade nycklar (PSK). Om du använder en PSK-ciphersuite elimineras behovet av att utföra processor intensiva krypterings åtgärder för offentliga nycklar, en Boon för resurs begränsade inbäddade enheter. PSK ersätter certifikatet i TLS-handskakningen och används i stället för den krypterade huvud hemligheten för generering av TLS-sessionsnycklar.

PSK-krypteringssviter är begränsade i den mening att en delad hemlighet måste finnas på båda enheterna innan en TLS-session kan upprättas. Det innebär att enheterna måste ha lästs in med den hemligheten med hjälp av ett säkert sätt än en TLS PSK-anslutning – PSKs kan uppdateras via en TLS PSK-anslutning, men enheten måste nödvändigt vis börja med en PSK som läses in via någon annan mekanism. Till exempel kan en sensor enhet och dess gateway-enhet läsas in med PSKs i fabriken innan det levereras, eller en standard-TLS-anslutning (med ett certifikat) kan användas för att läsa in PSK.

PSK-krypteringssviter levereras i ett par formulär som beskrivs i RFC 4279. Först används RSA-eller Diffie-Hellman nycklar som används på samma sätt som de offentliga nycklar som skickas i certifikatet i standard-TLS-handskakning. Det andra formuläret, som används i en resurs begränsad miljö, använder en PSK som används för att direkt generera sessionsnycklar (för användning av AES, till exempel), så att du undviker användningen av dyra RSA-eller Diffie-Hellman-åtgärder.

NetX Secure stöder den andra formen av PSK-krypteringssviter, vilket gör det möjligt för program att ta bort all krypterings kod för offentliga nycklar och minnes användning. Själva PSK är inte en AES-nyckel, men kan anses som ett lösen ord som de faktiska nycklarna genereras från. Det finns några begränsningar för vad PSK-värdet kan vara, även om längre värden ger högre säkerhet (samma som med lösen ord).

Om du vill använda PSK med ditt NetX-säkra program måste du först definiera det globala makrot **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Detta görs vanligt vis via dina kompilator inställningar, men definitionen kan också placeras i huvud filen nx_secure_tls. h. Med det definierade makrot kommer PSK ciphersuite-stödet att kompileras till ditt NetX-säkra TLS-program.

När PSK-stödet är aktiverat kan du använda TLS API för att konfigurera PSKs för ditt program. Varje PSK kräver ett PSK-värde (den faktiska hemliga nyckeln "– Behåll det här värdet säkert), ett" Identity "-värde som används för att identifiera specifika PSK och ett" identitets tips "som används av en TLS-server för att välja ett visst PSK-värde.

Själva PSK-objektet kan vara ett binärt värde eftersom det aldrig skickas via en nätverks anslutning. PSK kan vara valfritt värde upp till 64 byte långt.

Identiteten och tipset måste vara utskrivbara sträng strängar formaterade med UTF-8. Värdena för identitet och ledtråd kan vara en valfri längd på upp till 128 byte.

Identiteten och PSK-formen bildar ett unikt par som läses in på varje enhet i nätverket som behöver kommunicera med varandra.

"Tipset" används främst för att definiera specifika program profiler för att gruppera PSKs efter funktion eller tjänst. Dessa värden måste överenskommas i förväg och är beroende av program. Som exempel använder OpenSSL kommando rads serverprogram (med PSK aktiverat) standard strängen "Client_identity", som måste tillhandahållas av en TLS-klient för att kunna fortsätta med TLS-handskakningen.

Mer information om PSKs finns i NetX Secure API-referens för följande tjänster: nx_secure_tls_client_psk_set nx_secure_tls_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importerar X. 509-certifikat till NetX Secure

Digitala certifikat krävs för de flesta TLS-anslutningar på Internet. Certifikat ger en metod för att autentisera tidigare okända värdar via Internet genom användning av betrodda mellanhänder, vanligt vis kallade *certifikat utfärdare eller certifikat* utfärdare. Om du vill ansluta din NetX-enhet till en kommersiell moln tjänst (till exempel Amazon Web Services) måste du importera certifikat till ditt program genom att läsa in dem på enheten.

Tillsammans med certifikat behöver du ibland även en *privat nyckel* som är kopplad till ditt certifikat. I vissa program (t. ex. TLS-klient när autentisering av klient certifikat används inte) är certifikatet tillräckligt, men om ditt certifikat används för att identifiera din enhet behöver du en privat nyckel. Privata nycklar skapas vanligt vis när du skapar ditt certifikat och lagras i en separat fil, ofta krypterat med ett lösen ord.

### <a name="certificate-types"></a>Typer av certifikat

Digitala certifikat används vanligt vis för att identifiera entiteter i ett nätverk, men beroende på vad deras program kommer att ha något annorlunda egenskaper.

### <a name="local-certificates"></a>Lokala certifikat

I den här dokumentationen kommer vi att referera till "lokala certifikat" som de certifikat som ger en identitet för vår lokala enhet (ett annat möjligt namn kan vara "enhets certifikat"). De här certifikaten kommer att tillhandahållas till en fjärrvärd när fjärrvärden vill autentisera den lokala enheten.

### <a name="remote-certificates"></a>Fjärrcertifikat

I den här dokumentationen avser "fjärrcertifikat" de certifikat som tillhandahålls av en fjärrvärd under TLS-handskakning när det är tillämpligt. Utrymmet för dessa certifikat måste tilldelas eller så kan NetX säkra inte parsa dem och slutföra TLS-handskakningen.

### <a name="signing-certificates"></a>Signerings certifikat

Ett "signerings certifikat" används för att digitalt signera andra certifikat eller data för autentisering. Dessa certifikat kan vara antingen mellanliggande eller rot certifikat inom en PKI (Public Key Infrastructure) och används vanligt vis inte för att identifiera enskilda enheter eller värdar.

### <a name="root-ca-certificates"></a>Certifikat från rot certifikat utfärdare

"Rot certifikat utfärdarens certifikat" är signerings certifikat som utgör grunden för en PKI och som är självsignerade, i stället för att signeras av ett annat signerings certifikat. Minst ett rot certifikat för certifikat utfärdare krävs vanligt vis för att en TLS-klient ska kunna verifiera fjärrservrar.

### <a name="certificate-formats"></a>Certifikat format

Digitala certifikat är bara filer som innehåller strukturerade data som kodas med hjälp av ASN. 1-syntaxen. Det finns dock olika format där certifikat kan lagras och det är viktigt att ha rätt format innan du läser in ett certifikat i ett NetX-säkert program.

De vanligaste formaten för certifikat är DER och PEM. DER (för *Distinguished Encoding Rules* är ett ASN. 1-format) det binära formatet som används av TLS när den första hand skakningen utförs. PEM (från *Privacy Enhanced mail*) är en base-64-kodad version av der-formatet som är lämplig för e-post eller sändning över http på webben. Olika leverantörer använder olika fil namns tillägg för certifikat, till exempel ". pem" eller ". CRT" för PEM-certifikat och ". der" för DER-certifikat. Om du har ett certifikat och det inte är oklart vilket format som används kan du använda filen i en text redigerare för att fastställa typen eftersom DER-filerna är kodade binära och PEM filer är vanliga ASCII-text som börjar med rubriken "-----BEGIN CERTIFICATe-----".

NetX Secure kräver att ditt certifikat är i binärformat, så du måste konvertera certifikatet till DER-format innan du importerar. Detta kan göras med verktyg som är lättillgängligt, till exempel OpenSSL.

Om du behöver en privat nyckel för ditt program kommer nyckel filen att kodas med hjälp av PEM eller DER i ett särskilt format (PKCS # 1 för RSA, RFC 5915 för ECC). Den privata nyckel filen måste konverteras till DER innan den kan importeras.

Följande OpenSSL-kommandon anges som ett exempel på konvertering av certifikat och RSA-nyckelfiler till DER-format som krävs av NetX Secure (ECC är liknande – se OpenSSL-dokumentationen).

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
### <a name="private-keys-and-certificates"></a>Privata nycklar och certifikat

För certifikat som identifierar en enhet måste den tillhör ande privata nyckeln läsas in tillsammans med certifikatet. Den privata nyckeln (som kan vara en av de algoritmer för offentlig nyckel som RSA, Diffie-Hellman eller Elliptic-Curve kryptografi) används av en TLS-server för att dekryptera det inkommande nyckel materialet ("huvud hemlighet") från en TLS-klient och därmed autentisera sig själv för klienten. Om ett identitets certifikat (ett certifikat med tillhör ande privat nyckel) anges för en TLS-klient och en server begär ett klient certifikat, den privata nyckeln används för att autentisera klienten, om RSA-klienten krypterar en token med hjälp av den privata nyckel som servern dekrypterar med hjälp av klientens offentliga nyckel, som anges i klient certifikatet (Diffie-Hellman och ECC-autentisering sker på liknande sätt, men informationen är lite annorlunda).

I NetX Secure används tjänsten *nx_secure_x509_certificate_initialize* för att initiera ett X. 509-certifikat (se avsnittet "läser in certifikat på enheten" för mer information) och eventuellt associera en privat nyckel med det certifikatet.

Om en privat nyckel anges markeras certifikatet som "identitets certifikat" som används för att identifiera enheten. Nyckeln skickas som en sammanhängande binär blob och en längd med en associerad nyckel typ. Nyckel typen beror på typen av nyckel (t. ex. RSA, ECC osv.) och formatet (t. ex. PKCS # 1 DER). Om ingen nyckel anges kan värdet NX_SECURE_X509_KEY_TYPE_NONE (värde 0x0) skickas för att indikera att ingen nyckel anges (en längd på 0 och en NX_NULL-pekare för data parametern kommer att uppnå samma resultat).

I följande tabell visas de nyckel typer som är kända för att NetX säkert och associerad typ identifierare som ska skickas till *nx_secure_x509_certificate_initialize*. Ytterligare nyckel typer läggs till som fler krypteringsalgoritmer läggs till i NetX Secure.

| Identifierare                              | Integritetsalgoritm | Format   | Kodning | Värde |
| --------------------------------------- | --------- | -------- | -------- | ----- |
| NX_SECURE_X509_KEY_TYPE_NONE            | Inget      | Saknas      | Saknas      | 0x0   |
| NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER   | RSA       | PKCS # 1   | DER      | 0x1   |
| NX_SECURE_X509_KEY_TYPE_EC_DER          | ECDSA     | RFC 5915 | DER      | 0x2   |

### <a name="user-defined-private-key-types"></a>Användardefinierade privata nyckel typer

Värdena för nyckel typs identifierarna för den *nx_secure_x509_certificate_initialize* tjänsten styr de åtgärder som vidtas när den privata nyckeln anges. För kända typer finns värdena i intervallet 0x0000 0000 – 0x0000 FFFF (nedersta 16 bitarna i ett 32-bitars osignerat heltal). För plattformar med anpassade nyckel typer<sup>17</sup> (som är fallet för vissa maskinvarubaserade krypterings motorer) kan en användardefinierad nyckel typ i intervallet 0x0000 1000 – 0xffff FFFF (de 16 16 bitarna som inte är noll) skickas som nyckel typ. Om någon av de översta 16 bitarna i nyckel typen har angetts skickas den privata nyckeln direkt till lämplig kryptografisk rutin (t. ex. RSA) som anges i tabellen TLS-ciphersuite. Användardefinierade nyckel typer kan inte parsas eller behandlas på annat sätt innan de skickas till den kryptografiska rutinen. Dessutom kommer den användardefinierade nyckel typen också att skickas till den kryptografiska rutinen så att lämplig bearbetning kan hanteras på den nivån.

Observera att användardefinierade nyckel typer vanligt vis används för vissa maskinvaruplattformar som använder anpassade (eventuellt krypterade) nyckel data. Det innebär vanligt vis att nyckel data genereras eller kodas med hjälp av en mekanism som är unik för den maskin varu leverantören (eller i fallet med en standard som PKCS # 11, en särskild standard). Mer information finns i dokumentationen för maskin varu plattformen.

17. Användardefinierade nyckel typer kräver en motsvarande anpassad kryptografisk rutin för att hantera det anpassade nyckel formatet. Den kryptografiska rutinen måste ha en matchande algoritm (t. ex. RSA) och skickas till TLS i ciphersuite-tabellen. 

### <a name="loading-certificates-onto-your-device"></a>Läser in certifikat på din enhet

Alla metoder för att läsa in en fil på enheten räcker till för att importera certifikaten.

Den enklaste metoden för att läsa in ett certifikat är att konvertera de binära DER-kodade data till en C-matris och kompilera den i programmet som en konstant. Detta kan enkelt göras med verktyg som "XXD" i Linux (med alternativet "-i").

Alternativt kan du läsa in ditt certifikat i ett Flash-filsystem eller andra lagrings alternativ så länge du kan skicka en pekare till certifikat data till NetX Secure API.

### <a name="certificate-files-needed-for-netx-secure"></a>Certifikatfiler som krävs för NetX Secure

De certifikatfiler du behöver importera beror på ditt program. I allmänhet kräver TLS-servrar ett certifikat för att identifiera enheten, och TLS-klienter kräver ett eller flera *betrodda certifikat* för att autentisera fjärrservrar. Följande tabell visar de certifikat som krävs för vissa olika TLS-program.

| **TLS-funktioner/alternativ**                     | **Certifikat/nycklar som krävs (minimum)**              |
| ------------------------------------------------- | --------------------------------------------------- |
| TLS-klient                                        | Rot certifikat utfärdarens certifikat                                 |
| TLS-server                                        | Lokalt certifikat, privat nyckel för certifikatet |
| TLS-server med autentisering av klient certifikat | Lokalt certifikat, privat nyckel, rot certifikat utfärdare             |
| TLS-klient med autentisering av klient certifikat | Lokalt certifikat, privat nyckel, rot certifikat utfärdare             |
| TLS-klient eller server med i förväg delade nycklar    | Ingen (PSK används i stället för certifikat)             |

De relevanta tjänsterna för inläsning av certifikat är följande:

| **API-namn**                                   | **Syfte**                                            |
| ---------------------------------------------- |------------------------------------------------------- |
| nx_secure_x509_certificate_initialize      | Måste anropas för att alla certifikat ska fylla NX_SECURE_X509_CERTs strukturen med dina certifikat data och privata nycklar. |
| nx_secure_tls_local_certificate_add       | Lägg till ett lokalt certifikat till en TLS-session för att identifiera enheten.                                                                |
| nx_secure_tls_local_certificate_remove    | Ta bort ett lokalt certifikat från en TLS-session.                                                                                   |
| nx_secure_tls_remote_certificate_allocate | Allokera utrymme för ett fjärrcertifikat (anropas med en oinitierad NX_SECURE_X509_CERT).                                   |
| nx_secure_tls_trusted_certificate_add     | Lägg till ett certifikat i en TLS-session som ett betrott certifikat för autentisering av fjärranslutna värdar.                                     |
| nx_secure_tls_trusted_certificate_remove  | Ta bort ett betrott certifikat från en TLS-session.                                                                                 |

### <a name="working-with-aws-iot-certificates"></a>Arbeta med AWS IoT-certifikat

I Amazon Web Services IoT-gränssnittet väljer du "säkerhet" på menyn i sido menyn och väljer "certifikat". Skapa ett nytt certifikat och följ anvisningarna för att hämta det nya enhets certifikatet.

När du har hämtat dina certifikat måste du konvertera dem till DER-format med hjälp av OpenSSL eller ett liknande verktyg.

Obs: AWS kommer också att tillhandahålla en offentlig nyckel fil. Den offentliga nyckeln finns i det lokala enhets certifikatet så att den inte behöver importeras till ditt program.

Till exempel är följande kommandon för att konvertera det lokala enhets certifikatet och dess privata nyckel till DER-format för användning med NetX Secure:

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
De konverterade filerna kan importeras till ditt program enligt ovanstående instruktioner.

## <a name="x509-certificate-validation-in-netx-secure"></a>Verifiering av X. 509-certifikat i NetX Secure 

När du använder TLS med X. 509-certifikat för värd identifiering och verifiering, är det viktigt att förstå hur dessa certifikat verkligen verifieras. TLS-specifikationen ger inte detaljerade instruktioner om hur du verifierar ett certifikat, det refererar till X. 509-specifikationen (RFC 5280). I allmänhet förväntas det att TLS utför minst grundläggande verifiering av inkommande certifikat (de certifikat som tillhandahålls av fjärrvärden under TLS-handskakning) och NetX Secure TLS inte är något annat.

### <a name="basic-x509-validation"></a>Basic X. 509-validering

För alla inkommande certifikat utför NetX Secure TLS Basic X. 509-sökväg validering. Processen omfattar att kontrol lera varje certifikats digitala signatur mot utfärdarens certifikat, som kan tillhandahållas av fjärrvärden eller finnas i det betrodda certifikat arkivet (se avsnittet "Importera X. 509-certifikat till NetX Secure" för mer information om att importera betrodda certifikat). Validerings processen upprepas rekursivt i utfärdarens certifikat tills ett betrott certifikat nås eller kedjan slutar (med ett självsignerat certifikat eller ett utfärdarcertifikat som saknas). Om ett betrott certifikat nås, verifieras certifikatet, annars avvisas det. Dessutom kontrol leras förfallo datumet för varje certifikat i varje steg i verifierings processen mot den tid som anges av funktionen för tidsstämpeln (se tjänsten "nx_secure_tls_session_time_function_set" för mer information).

509-specifikationen X. innehåller också en algoritm för stöd för "policies", som är identifierare som finns i ett X. 509-tillägg som kan kontrol leras under verifiering av Sök vägar. NetX säker behandlar för närvarande X. 509-certifikat som om alternativet "anyPolicy" är definierat – det vill säga att alla principer är acceptabla och att den valfria princip kontrollen inte utförs. Implementeringen NetX Secure X. 509 kan utökas med den här funktionen i en framtida version. För närvarande kan princip tillägget hämtas från ett certifikat med hjälp av *nx_secure_x509_extension_find* -API: et.

När den grundläggande Sök vägs valideringen är klar anropar TLS certifikat verifieringens återanrop som tillhandahålls av programmet med hjälp av *nx_secure_tls_session_certificate_callback_set* -API: et. Om inget motanrop anges anses certifikatet vara betrott efter verifiering av lyckade sökvägar. Om ett motanrop anges utför motringningen ytterligare verifiering av det certifikat som krävs av programmet. Returvärdet från motringningen används för att avgöra om du vill fortsätta med TLS-handskakning eller om du vill avbryta hand skakningen på grund av ett verifierings problem.

Återanropet anropas med en pekare till den relevanta TLS-sessionen och en NX_SECURE_X509_CERT pekare till certifikatet som ska verifieras. Mellan TLS-sessionen och certifikatet har programmet alla data som krävs från TLS för att utföra ytterligare verifierings kontroller.

För att få hjälp med den ytterligare verifieringen ger NetX Secure X. 509-rutiner för några vanliga verifierings åtgärder, inklusive kontroll av DNS-validering och lista över återkallade certifikat. Alla dessa rutiner är lämpliga för användning i återanrop av certifikat verifiering, men kan också användas för att utföra inaktive ring av X. 509-certifikat.

I följande tabell sammanfattas de tillgängliga hjälp funktionerna för certifikat bearbetning av X. 509. Mer detaljerade förklaringar för åtgärderna finns i följande avsnitt och API-referensen i kapitel 4  
  
Beskrivning av NetX Secure Services ger ytterligare information om de olika rutinerna.

| **API-namn**                             | **Beskrivning**                               |
| ---------------------------------------- | -------------------------------------- |
| nx_secure_x509_common_name_dns_check               | Kontrol lera namnet på det unika ämnes namnet för X. 509 och SubjectAltName mot ett förväntat DNS-namn |
| nx_secure_x509_crl_revocation_check                 | Sök efter ett återkallat certifikat i en X. 509 lista över återkallade certifikat (CRL)       |
| nx_secure_x509_extended_key_usage_extension_parse | Parsa och hitta en viss utökad nyckel användning OID i ett certifikat                   |
| nx_secure_x509_key_usage_extension_parse           | Parsa och returnera bitfield för nyckel användning i ett certifikat                            |
| nx_secure_x509_extension_find                        | Hitta och returnera RAW DER-kodade ASN. 1-data för ett särskilt tillägg.            |

X. 509 Helper-funktioner för användning i återanrop för certifikat verifiering

### <a name="x509-extensions"></a>X. 509-tillägg

I specifikationen X. 509 beskrivs ett antal "tillägg" som kan användas för att tillhandahålla ytterligare information som kan användas vid verifiering av certifikat. Dessa tillägg är valfria och behövs inte för säker verifiering av ett digitalt certifikat mot ett betrott rot certifikat. NetX Secure stöder dock vissa grundläggande tillägg. Stöd för ytterligare tillägg kan läggas till i framtida versioner.

De tillägg som stöds för närvarande visas i följande tabell:

| Tilläggs namn           | Beskrivning                                                                   | Relevant API                                             |
| ------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| Nyckelanvändning                | Ger acceptabel användning för certifikatets offentliga nyckel i en bitfield         | nx_secure_x509_key_usage_extension_parse           |
| Utökad nyckelanvändning       | Ger ytterligare acceptabel användning för certifikatets offentliga nyckel med hjälp av OID | nx_secure_x509_extended_key_usage_extension_parse |
| Alternativt namn för certifikatmottagare | Innehåller alternativa DNS-namn som också representeras av certifikatet   | nx_secure_x509_common_name_dns_check               |

### <a name="unsupported-x509-extensions"></a>X. 509-tillägg som inte stöds

NetX Secure ' X. 509 implemenation tillhandahåller en tjänst för att extrahera tillägg som inte stöds: *nx_secure_x509_extension_find*. Detta API är avsett för avancerade användare eftersom det kräver kunskap om DER-kodad ASN. 1 för att parsa de data som returneras. Den används internt för att extrahera stödda tillägg men tillhandahålls för att under lätta utveckling av anpassat stöd för X. 509-tillägg.

Om du vill använda nx_secure_x509_extension_find skickas en NX_SECURE_X509_EXTENSION, tillsammans med certifikatet och ett tilläggs-ID, som är en heltals representation av OID-strängen med variabel längd för en känd tilläggs typ. En fullständig lista över OID för X. 509-tillägg som stöds finns i API-referensen för nx_secure_x509_extension_find på sidan 178.

NX_SECURE_X509_EXTENSIONs strukturen definieras enligt följande:

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
När tjänsten återställs, fylls strukturen med relevanta data från certifikatet. Fältet nx_secure_x509_extension_id används vanligt vis för internt bruk, men kommer att fyllas i med relevant heltals representation för OID. Fältet nx_secure_x509_extension_critical visar det kritiska värdet för X. 509-kritiskt tillägg (Boolean). Fälten nx_secure_x509_extension_data och nx_secure_x509_extension_data_length innehåller en pekare till de DER-kodade ASN. 1-data för tillägget och längden på dessa data.

Den faktiska parsningen av tilläggets ASN. 1-data ligger utanför det här dokumentets omfång, men om du har åtkomst till NetX Secure TLS-källan kan du se hur parsningen utförs där nx_secure_x509_extension_find anropas för tillägg som stöds.

### <a name="x509-dns-validation"></a>DNS-validering för X. 509

En vanlig certifikat validerings åtgärd i TLS förutsätter att du kontrollerar Top-Level domän namn (topp) för en fjärrvärd mot X. 509-certifikatet som tillhandahålls av värden under TLS-handskakningen. Den här åtgärden hjälper till att säkerställa att certifikatet verkligen matchar den värd server som tillhandahöll det, förutsatt att DNS-sökningen kan vara betrodd. I NetX Secure TLS tillhandahålls den här funktionen av tjänsten **nx_secure_x509_common_name_dns_check**, som tar certifikatet och en sträng som innehåller topp delen av den URL som används för att få åtkomst till värden. Topp domänen jämförs med certifikatets eget namn-fält och om det matchar, returneras NX_SUCCESS. Om det egna namnet inte matchar, kontrollerar rutinen även om det finns en *subjectAltName* för certifikat tillägg för X. 509. Om det finns en subjectAltName, kontrol leras även eventuella DNSName-poster i tillägget mot den angivna topp domänen. Om det finns en matchning returneras NX_SUCCESS. Om ingen matchning hittas returneras ett fel som lämpar sig för att returnera från återanropet för certifikat verifiering.

### <a name="x509-key-usage-and-extended-key-usage-extensions"></a>X. 509 nyckel användning och tillägg för utökad nyckel användning

Nyckel användningen för X. 509 och utökade nyckel användnings tillägg ger information om hur ett certifikats offentliga nyckel kan användas när certifikatet autentiseras. Nyckel användningen anges av certifikat utfärdaren när certifikatet signeras och utfärdas. Nyckel användningen kan användas av en TLS-värd för att kontrol lera att certifikatet har behörighet att användas för att autentisera en fjärran sluten TLS-värd och utföra andra åtgärder.

Tillägget för nyckel användning består av en enkel bitfield där varje BITS representerar en speciell nyckel användning. En fullständig lista över dessa värden finns i API-referensen för *nx_secure_x509_key_usage_extension_parse* på sidan 183. En mer fullständig beskrivning av nyckel användnings bitarna och deras betydelser finns i RFC 5280, section 4.2.1.3.

Tillägget för utökad nyckel användning, t. ex. tillägg för nyckel användning, innehåller en acceptabel nyckel användnings information. För att kunna stödja godtycklig användning används OID i stället för en bitfield i tillägget för utökad nyckel användning. Vid parsning av ett tillägg för utökad nyckel användning i NetX Secure X. 509, anges ett heltal som representerar OID av programmet – *nx_secure_x509_extended_key_usage_extension_parse* tjänsten kommer sedan att returnera om OID finns. En fullständig lista över OID-objekt som stöds för utökad nyckel användning finns i API-referensen för *nx_secure_x509_extended_key_usage_extension_parse* på sidan 175. En mer fullständig beskrivning av OID och deras betydelser finns i RFC 5280, section 4.2.1.12.

### <a name="x509-crl-revocation-status-checking"></a>Kontroll av status för återkallade certifikat för X. 509

X. 509 innehåller en mekanism som kallas CRL ( *Certificate Revocation List* ) som tillåter en digital certifikat signerings auktoritet att återkalla giltigheten för certifikat som den har signerat. Alla program som behöver verifiera certifikat från en signerings utfärdare kan hämta en lista över återkallade certifikat och jämföra alla certifikat som har signerats av den här utfärdaren (utfärdare) mot CRL: n för att se om deras status har återkallats av någon anledning (till exempel komprometterad privat nyckel). På så sätt kan programmet undvika att använda potentiellt farliga certifikat som skickar andra verifierings kontroller för certifikat.

Hämtning av en CRL görs av ett program genom att hämta den DER-kodade listan från en fördefinierad Server eller på något annat sätt. Den faktiska installationen varierar från utfärdaren till utfärdaren så att NetX säker inte tillhandahåller en mekanism för att hämta CRL: er, men det ger en rutin för att kontrol lera ett certifikat mot en CRL, **nx_secure_x509_crl_revocation_check**.

API: et tar en DER-kodad CRL, ett certifikat arkiv (till exempel en i en TLS-session) att kontrol lera mot och det certifikat som ska kontrol leras. Rutinen validerar först själva listan över återkallade certifikat mot det betrodda arkivet (en del av det certifikat arkiv som tillhandahålls av programmet). Detta är viktigt för att skydda mot bedrägliga listor över återkallade certifikat som används för DOS-attacker (Denial-of-Service) och upprättar att listan verkligen kommer från rätt utfärdare. Efter CRL-verifieringen kontrol leras utfärdaren – om utfärdaren av listan över återkallade certifikat inte matchar certifikat utfärdarens CRL, är CRL: en inte giltig för certifikatet och ett fel returneras. Det är upp till programmet att avgöra om TLS-handskakningen kan fortsätta nu. Om utfärdarna matchar varandra genomsöks CRL: en efter serie numret för det certifikat som verifieras. Om serie numret finns i listan returneras ett fel som indikerar att certifikatet har återkallats. Om ingen matchning hittas returneras NX_SUCCESS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Autentisering av klient certifikat i NetX Secure TLS

När du använder autentisering med X. 509-certifikat kräver TLS-protokollet att TLS-serverinstansen tillhandahåller ett certifikat för identifiering, men som standard behöver TLS-klientcertifikatet inte tillhandahålla ett certifikat för autentisering med hjälp av en annan form av autentisering i stället (t. ex. en kombination av användar namn/lösen ord). Detta matchar den vanligaste användningen av TLS på Internet för webbplatser. Till exempel måste en detaljist webbplats bevisa för en potentiell kund som använder en webbläsare som servern är legitim, men användaren använder ett inloggnings-/lösen ord för att få åtkomst till ett speciellt konto.

Standard fallet är dock inte alltid önskvärt, så TLS kan alternativt tillåta att TLS-serverinstansen begär ett certifikat från fjärrklienten. När den här funktionen är aktive rad kommer TLS-servern att skicka ett CertificateRequest-meddelande till TLS-klienten under hand skakningen. Klienten måste svara med ett eget certifikat och ett CertificateVerify-meddelande som innehåller en kryptografisk token som styrker att klienten äger den matchande privata nyckeln som är kopplad till certifikatet. Om verifieringen Miss lyckas eller om certifikatet inte är anslutet till ett betrott certifikat på servern Miss lyckas TLS-handskakningen.

Det finns två separata fall för autentisering av klient certifikat i TLS – följande avsnitt beskriver båda fallen.

### <a name="client-certificate-authentication-for-tls-clients"></a>Autentisering av klient certifikat för TLS-klienter

En TLS-klient kan försöka ansluta till en server som begär ett certifikat för klientautentisering. I det här fallet måste klienten ange ett certifikat för servern och kontrol lera att den äger den matchande privata nyckeln eller att servern avslutar TLS-handskakningen.

I NetX Secure TLS finns det ingen särskild konfiguration som stöder den här funktionen, men programmet måste ange ett lokalt identifierings certifikat för TLS-klientcertifikatet med hjälp av tjänsten *nx_secure_tls_local_certificate_add* . Om inget certifikat tillhandahålls av programmet men fjärrservern använder autentisering av klient certifikat och begär ett certifikat, kommer TLS-handskakningen att Miss läge. Det certifikat som angavs för TLS-sessionen med *nx_secure_tls_local_certificate_add* måste identifieras av fjärrservern för att du ska kunna slutföra TLS-handskakningen.

### <a name="client-certificate-authentication-for-tls-servers"></a>Autentisering av klient certifikat för TLS-servrar

TLS-serverns händelse för autentisering av klient certifikat är något mer komplicerat än TLS-klientens fall på grund av att funktionen är valfri. I det här fallet måste TLS-servern uttryckligen begära ett certifikat från fjärr-TLS-klienten, sedan bearbeta CertificateVerify-meddelandet för att verifiera att den fjärranslutna klienten äger den matchande privata nyckeln och servern måste kontrol lera att det certifikat som tillhandahålls av klienten kan spåras till ett certifikat i det lokala betrodda certifikat arkivet.

I NetX Secure TLS Server-instanser styrs klient certifikat autentisering av <br>
*NX <span class="underline"> _</span> säker <span class="underline">_</span>TLS-<span class="underline"> _</span> session <span class="underline">_</span>klienten <span class="underline"> _</span> verifierar <span class="underline">_</span>aktivera* och<br>
*NX <span class="underline"> _</span> Secure <span class="underline">_</span>TLS <span class="underline"> _</span> session <span class="underline">_</span>client <span class="underline"> _</span> Verifiera <span class="underline">_</span>inaktivera* tjänster.

Om du vill aktivera autentisering av klient certifikat måste ett program anropa<br>
*NX <span class="underline"> _</span> säker <span class="underline">_</span>TLS <span class="underline"> _</span> session <span class="underline">_</span>klient <span class="underline"> _</span> verifiera <span class="underline">_</span>aktivera* med TLS-serverinstans innan du anropar *nx_secure_tls_session_start*. Observera att anropet till den här tjänsten på en TLS-session som används för TLS-klientanslutningar inte kommer att påverka.

När autentisering av klient certifikat är aktiverat begär TLS-servern ett certifikat från fjärr-TLS-klienten under TLS-handskakningen. I NetX Secure TLS-server kontrol leras klient certifikatet mot arkivet med betrodda certifikat som skapats med *nx <span class="underline"> _</span> secure_tls <span class="underline">_</span>betrodda <span class="underline"> _</span> certifikat <span class="underline">_</span>Lägg till* följande kedja i X. 509-utfärdaren. Fjärrklienten måste ange en kedja som ansluter sitt identitets certifikat till ett certifikat i det betrodda arkivet eller så Miss känner TLS-handskakningen. Även om bearbetningen av CertificateVerify-meddelanden Miss lyckas kommer TLS-handskakningen att Miss lyckas.

De autentiseringsmetoder som används för metoden CertificateVerify är fasta för TLS version 1,0 och TLS-version 1,1 och anges av TLS-servern i TLS version 1,2. Under TLS 1,2 följer de autentiseringsmetoder som stöds vanligt vis de relevanta metoder som anges i tabellen med kryptografiska metoder, men vanligt vis RSA med SHA-256 (se avsnittet "kryptografi i NetX Secure TLS" för mer information om att initiera TLS med kryptografiska metoder).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografi i NetX Secure TLS

TLS definierar ett protokoll där kryptografi kan användas för att skydda nätverkskommunikation. Därför lämnar den den faktiska kryptografin att använda ganska stor öppen för TLS-användare. För specifikationen krävs bara att en enda ciphersuite implementeras – i händelse av TLS 1,2 är ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, vilket indikerar användningen av RSA för offentliga nyckel åtgärder, AES i CBC-läge med 128-bitars nycklar för sessions kryptering och SHA-1 för hash-meddelanden för meddelandeautentisering.

Som standard är TLS 1,2-kompatibel och den obligatoriska TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite som standard, men med tanke på antalet möjliga implementeringar för var och en av de kryptografiska metoderna på grund av maskin varu funktioner och andra överväganden, är NetX Secure en allmän krypterings-API som gör att en användare kan ange vilka kryptografiska metoder som ska användas med TLS.

OBS! den allmänna kryptografiska API-mekanismen gör det också möjligt för användarna att implementera sina egna krypteringssviter, men det rekommenderas för avancerade användare som är bekanta med TLS-krypteringssviter och-tillägg. Kontakta din uttryckliga Logic-representant om du är intresse rad av att stödja din egen krypteringssviter.

### <a name="cryptographic-methods"></a>Kryptografiska metoder

NetX Secure TLS implementerar DES, 3DES, AES, MD5, HMAC-MD5, SHA-1, HMAC-SHA1, SHA-256, HMAC-SHA256, RSA och ECC (valda kurvor) i program vara med maskin varu driv rutiner för vissa maskinvaruplattformar. Ett program kan använda de kryptografiska rutiner som medföljer NetX Secure, eller använda anpassade rutiner som tillhandahålls av slutanvändaren eller tredje part.

*NX_CRYPTO_METHOD* är ett kontroll block som har utformats för ett program för att beskriva en viss implementering av en kryptografisk algoritm som ska användas med netx Secure TLS. Med *NX_CRYPTO_METHOD* kan ett program enkelt integrera sin egen krypterings implementering i netx Secure. *NX_CRYPTO_METHODs* strukturen deklareras som:

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

Nedan visas en beskrivning av varje element i *NX_CRYPTO_METHODs* strukturen:

- nx_crypto_algorithm: det här fältet identifierar algoritmen som beskrivs i variabel *metoden* vissa giltiga värden för netx Secure TLS är följande (se nx_crypto_const. h för vissa värden):
    
  - NX_CRYPTO_NONE    
  - NX_CRYPTO_ENCRYPTION_NULL    
  - NX_CRYPTO_ENCRYPTION_AES_CBC    
  - NX_CRYPTO_AUTHENTICATION_NONE    
  - TLS_HASH_SHA_1    
  - TLS_HASH_SHA_256    
  - TLS_HASH_MD5    
  - TLS_CIPHER_RSA    
  - TLS_CIPHER_NULL

- nx_crypto_key_size_in_bits: det här fältet anger storleken på den hemliga nyckel som används av metoden.

- nx_crypto_IV_size_in_bits: det här fältet anger storleken på initierings vektorn (IV). Observera att i de flesta fall används IV-blocket endast för kryptering/dekryptering av algoritmer. Autentiserings-och verifierings algoritmer använder sällan det här fältet.

- nx_crypto_ICV_size_in_bits: det här fältet anger storleken på INTEGRITETSKONTROLLVÄRDET-blocket (integritets kontroll värde). Obs! det här blocket används för IPsec-användning och används inte i TLS. Mer information finns i NetX Duo IPsec.

- nx_crypto_block_size_in_bytes: det här fältet anger storleken på det kryptografiska krypteringsalgoritm blocket för blockbaserade chiffer i byte. I de flesta fall används detta av krypterings rutiner och sällan med autentiserings-rutiner.

- nx_crypto_metadata_area_size: det här fältet anger storleken på det metadata-område som metoden kräver. Varje implementering kan kräva ett visst minne för att lagra tillståndsinformation, eller för att lagra mellanliggande data (t. ex. nyckel omvandlings material) eller använda som arbets yta. Mängden utrymme som krävs av en implementering anges i det här fältet. Programmet tillhandahåller minnes utrymmet när du skapar en TLS-session. Den kryptografiska funktionen ansvarar för att hantera det här metadata-avsnittet.

- nx_crypto_init: Detta är initierings funktionen för krypteringsalgoritmen. För en implementering som inte behöver en initierings rutin, kan det här fältet anges till NX_NULL. En typisk användning av en initierings funktion är att initiera den interna data strukturen för algoritmen. NetX Secure TLS hanterar initiering av den kryptografiska rutinen genom att anropa den här funktionen internt.

Prototypen för initierings funktionen är:

```C
UINT crypto_init_function(NX_CRYPTO_METHOD *method, 
                          UCHAR *key, 
                          UINT  key_size_in_bits, 
                          VOID  **handle, 
                          VOID  *crypto_metadata_area, 
                          ULONG crypto_metadata_area_size);
```

  - metoden är en pekare till kontroll blocket för kryptografi metoden.

  - Key är den hemliga nyckel strängen för bearbetning av data paketen.

  - key_size_in_bits definierar storleken på den hemliga nyckeln i bitar.

  - referens är ett implementations-definierat objekt som identifierar en viss kryptografisk session. Värdet genereras av initierings rutinen och skickas tillbaka till anroparen. Den efterföljande kryptografi åtgärden eller rensa rutinen Använd den här referensen för att identifiera sessionen.

  - crypto_metadata är en pekare till metadata-ytan som krävs för den här algoritmens implementering. För algoritmer som inte behöver ett område för metadata är det här fältet inställt på NX_NULL och initierings rutinen får inte komma åt området metadata.

  - crypto_metadata_size anger storleken på metadata-ytan. För SAs som skapats utan området metadata är det här fältet inställt på noll och initierings rutinen får inte komma åt området metadata.

  - Den här rutinen ska returnera *NX_SUCCESS* om initierings processen lyckas. Anroparen behandlar andra retur värden som felaktiga.

- nx_crypto_cleanup: det här är den rensnings rutin som definierats för implementeringen av en krypteringsalgoritm. Den anropas när en TLS-session tas bort eller startas om.

Prototypen för rensnings funktionen är:

```C
UINT crypto_cleanup_function(VOID *handle);
```
- referensen skickas till rensnings funktionen av anroparen. Referensen initieras av initierings rutinen för kryptografi och används för att identifiera tillstånd för kryptografisk algoritm.

- Den här rutinen ska returnera *NX_SUCCESS* om rensnings processen lyckas. Anroparen behandlar andra retur värden som felaktiga.

- nx_crypto_operation: det här är den rutin som utför den faktiska krypterings-, dekrypterings-och Autentiseringstjänsten. Funktions prototypen för åtgärds rutinen är:

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

- OP anger vilken typ av åtgärd som denna rutin förväntas utföra. Giltiga värden är:
    
    - NX_CRYPTO_ENCRYPT
    - NX_CRYPTO_DECRYPT
    - NX_CRYPTO_AUTHENTICATE
    - NX_CRYPTO_VERIFY

- referensen skickas till funktions funktionen av anroparen. Den genereras av rutinen för kryptografisk initiering.
- metoden pekar på krypterings metodens kontroll block
- nycklar pekar på den hemliga nyckel som används för den här åtgärden
- key_size_in_bits är storleken på den hemliga nyckeln i bitar
- indatamängden är en pekare till början av meddelandet som ska användas.
- input_length_in_byte skickas av anroparen för att indikera storleken på det meddelande som ska användas.
- iv_ptr konfigureras av anroparen så att den pekar mot början av ett IV-block. Observera att minnet för IV-blocket tillhandahålls av anroparen. För kryptering ska funktionen funktion skriva IV-information till det här minnes blocket. för dekryptering ska funktionen funktion hämta IV-informationen från det här minnes blocket. Algoritmer för autentiserings-och verifierings åtgärder använder vanligt vis inte initierings vektorn.
- utdata installeras av anroparen för att peka på en utdatabuffert. Observera att minnet för utdatabufferten tillhandahålls av anroparen. För kryptering ska funktionen funktion skriva cipher-texten till utdatabufferten. vid dekryptering ska åtgärden skriva den dechiffrerade texten (klartext) till utdatabufferten. för autentiseringen ska hash-värdet skrivas till utdatabufferten. För verifiering används utdatabufferten för att lagra hash-information.
- output_length_in_byte anger storleken på utdatabufferten
- crypto_metadata pekar på det metadata-fält som ska användas av den här kryptografi åtgärden. Avsnittet för krypto-metadata initieras vanligt vis av crypto_init_function.
- crypto_metadata_size anger storleken på metadata-ytan.
- Den här rutinen ska returnera *NX_SUCCESS* om åtgärds processen lyckas. Anroparen behandlar andra retur värden som felaktiga.
- packet_ptr: det paket som innehåller de data som bearbetas. OBS! den här parametern används inte av TLS och ska vara inställd på NX_NULL.
- nx_crypto_hw_process_callback: en callback-funktion som tillhandahålls av krypterings metoden. Detta används om funktionen för kryptering tillhandahålls av maskin vara och kräver en callback-rutin.

NetX Secure TLS tillhandahåller följande krypterings metoder:

- *AES*  
- *RSA*  
- *HA*

NetX Secure TLS tillhandahåller följande autentiseringsmetoder:

- *HMAC-MD5*  
- *HMAC-SHA1*  
- *HMAC-SHA256*

I följande exempel visas hur du konfigurerar *NX_CRYPTO_METHOD* -strukturen så att den använder de krypterings-och autentiseringsmetoder som tillhandahålls av netx Duo IPSec.

***AES***

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
***HA***

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
***ALTERNATIVET***

En särskild metod **NX_CRYPTO_NONE** används för att signalera IPSec-modulen som krypteringen eller Autentiseringstjänsten inte kräver. Den konfigureras på följande sätt:

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

När du har skapat dina kryptografiska rutiner som följer de signaturer för kryptografiska metoder som beskrivs i föregående avsnitt måste du skicka dem till TLS när du initierar ett NX_SECURE_TLS_SESSION kontroll block. Detta görs i TLS-tjänsten nx_secure_tls_session_create:

```C
UINT  nx_secure_tls_session_create(
              NX_SECURE_TLS_SESSION*     session_ptr,
              const NX_SECURE_TLS_CRYPTO*    tls_cipher_table,
              VOID*                encryption_metadata_area,
              ULONG                 encryption_metadata_size
);
```
- session_pointer är en pekare till NX_SECURE_TLS_SESSION kontroll blocket.
- tls_cipher_table är en pekare till ett NX_SECURE_TLS_CRYPTO kontroll block som beskrivs nedan.
- encryption_metadata_area pekar på utrymme som används av kryptografiska rutiner i TLS.
- encryption_metadata_size är storleken på metadata-ytan i byte.

### <a name="elliptic-curve-cryptography-ecc-in-netx-secure-tls"></a>Elliptic Curve Cryptography (ECC) i NetX Secure TLS

Elliptic Curve Cryptography (ECC) tillhandahåller ett krypterings schema med offentliga nycklar som kan användas i stället för RSA. ECC är normalt snabbare och använder mindre nycklar än RSA, så det kan vara ett värdefullt alternativ för inbäddad TLS. I X-version-versioner före Azure återställnings tider 6,0 levererades ECC som ett tillägg, vilket kräver att ECC-källkoden installeras i projektet. Azure återställnings tider 6,0 integrerad ECC i Mainline-kodbasen så det är inte längre nödvändigt att installera ECC-filerna. ECC kräver dock fortfarande samma initiering som tidigare versioner.

### <a name="supported-ecc-curves"></a>ECC-kurvor som stöds

NetX säkra implementerar delar av kurvorna enligt <http://www.secg.org/sec2-v2.pdf> . Thefollowing-kurvor stöds<sup>18</sup>:

  - secp256r1 
  - secp384r1 
  - secp521r1 

Om andra ECC-kurvor används returnerar rutinen *nx_secure_tls_session_start ()* fel NX_SECURE_TLS_NO_SUPPORTED_CIPHERS som anger att kurvor som inte stöds användes.

Observera att TLS-certifikat kedjan även kan krypteras av ECC-algoritmer. Även om de kurvor som tillhandahålls av TLS-klienten stöds, är det möjligt att ECC-kurvan som används i certifikat kedjan inte stöds. I det här fallet returnerar *nx_secure_tls_session_start* rutinen NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER.

Ett standard tabell exempel för ciphersuite för ECC finns i nx_crypto_generic_ciphersuites. c. Se avsnittet "TLS Cryptographic chiffer Table" för mer information om ciphersuite-tabeller.

18. Observera att implementeringar för de secp192r1 och secp224r1are som också finns för äldre program. Dessa kurvor betraktas dock som svaga och bör inte användas för utveckling av nya program.

### <a name="crypto-methods-for-ecc"></a>Krypterings metoder för ECC

Krypterings metoder för Elliptic kurv grupper:

- NX_CRYPTO_METHOD crypto_method_ec_secp192<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp224<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp256;  
- NX_CRYPTO_METHOD crypto_method_ec_secp384;  
- NX_CRYPTO_METHOD crypto_method_ec_secp521;

Krypterings metoder för ECC-kurvor definieras i nx_crypto_generic_ciphersuites. c.

Krypterings metod för ECDHE:

- NX_CRYPTO_METHOD crypto_method_ecdhe;

Krypterings metod för ECDSA:

- NX_CRYPTO_METHOD crypto_method_ecdsa;

ECDSA-och ECDHE-krypterings metoder definieras i nx_crypto_generic_ciphersuites. c.

Kombineras med andra krypterings metoder som RSA, SHA, AES, och de kan användas som bygg stenar för ciphersuite lookup-tabellen.

### <a name="enabling-ecc-support-for-tls"></a>Aktivera ECC-stöd för TLS

ECC är aktiverat som standard för TLS. För att inaktivera ECC-stöd måste symbol NX_SECURE_DISABLE_ECC_CIPHERSUITE definieras.

För att ändringen ska börja gälla måste du återskapa NetX Secure-biblioteket och alla program som använder det biblioteket.

I program koden måste API n *x_secure_tls_ecc_initialize ()* anropas när TLS-sessionen har skapats. Detta API meddelar TLS-sessionen av den typ av kurvor som ska användas för TLS-nyckelns utbytes åtgärder och certifikat verifiering. Om en ECC-algoritm har valts under fasen TLS-handskakning, kan du bestämma vilken kurva som ska användas om du väljer en ECC-algoritm för klient och server.

Följande kod segment illustrerar hur du använder API: et. Observera att argumenten (*nx_crypto_ecc_supported_groups, nx_crypto_ecc_supported_groups_size och nx_crypto_ecc_curves)* är definierade i *nx_crypto_generic_ciphersuites. c*. Dessa symboler kan därför användas direkt.

```C
status = nx_secure_tls_ecc_initialize(&tls_session,     
                    nx_crypto_ecc_supported_groups,      
                    nx_crypto_ecc_supported_groups_size,     
                    nx_crypto_ecc_curves);
```
Exempel konfigurationen i nx_crypto_generic_ciphersuites. c innehåller en uppslags tabell för ECC-ciphersuite som används när ECC är aktiverat. Om du vill använda ECC kan du bara skicka nx_crypto_tls_ciphers_ecc som tabell parameter för ciphersuite när du skapar TLS-sessioner med nx_secure_tls_session_create. Tabellen exempel innehåller både ECC-och Non-ECC-krypteringssviter.

### <a name="tls-cryptographic-cipher-table"></a>TLS-kryptografisk chiffrering tabell

NX_SECURE_TLS_CRYPTOs strukturen definieras som:

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
Tabellen skapas genom att fylla i posterna för den här strukturen i en statisk konstant som finns i NetX Secure TLS-projektet, som vanligt vis finns i de kryptografiska rutinerna och modulerna.

Det kryptografiska biblioteket ("generisk") som tillhandahålls med NetX Secure innehåller följande tabell definition (för icke-ECC ciphersuite support<sup>19</sup>):

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
Den första posten i strukturen är TLS ciphersuite-tabellen. NX_SECURE_TLS_CIPHERSUITE_INFOs strukturen mappar kryptografiska rutiner (i form av NX_CRYPTO_METHOD pekare) till särskilda krypteringssviter som definieras i TLS-specifikationerna. Det andra värdet är antalet poster i tabellen som det första fältet pekar på.

Nästa fält pekar på en tabell med rutiner som används av X. 509 vid bearbetning av digitala certifikat och struktur NX_SECURE_X509_CRYPTO liknar i formulär för att NX_SECURE_TLS_CIPHERSUITE_INFO. Följande fält är antalet poster i tabellen.

Följande uppslags tabell är ett antal rutiner som behövs för vissa versioner av TLS. Till exempel, före TLS version 1,2, har hash-rutiner för nyckel generering och hand skakning åtgärd ATS för att använda en kombination av SHA-1 och MD5 – metoderna för dessa rutiner kallas särskilt i chiffrering eftersom de inte är kopplade till specifika krypteringssviter. I TLS version 1,2 väljs ciphersuite och hashing-rutinerna av, men för krypteringssviter som inte anger vilka rutiner som ska användas används hash-metoden SHA-256, och chiffrering anropar den rutinen specifikt.

TLS 1,3 kräver några extra särskilda chiffer för olika åtgärder.

19. Observera att TLS 1,3-stöd kräver ECC – Använd nx_crypto_tls_ciphers_ecc om TLS 1,3 har Aktiver ATS.

### <a name="tls-ciphersuite-lookup-table"></a>Uppslags tabell för TLS-Ciphersuite

Om du vill fylla i tabellen Cipher för TLS, måste du också skapa en ciphersuite lookup-tabell som mappar kryptografiska rutiner till vissa ciphersuite-identifierare. Identifierarna är IANA-registrerade värden som är universella. Mer information finns i avsnittet om TLS-rapporter. Rutinerna representerar 5 separata metoder som används i varje ciphersuite (vissa krypteringssviter får inte använda alla 5): offentligt chiffer, offentlig nyckel autentisering, session-chiffer, sessions-hash-rutin och TLS-Pseudo-Random funktion (PRF). I följande tabell förklaras var och en av de fem metoderna:

| **Rutin kategori**      | **Beskrivning**                                                                                       | **Exempel på algoritmer**                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Offentligt chiffer             | Används för att byta nycklar under TLS-handskakning                                                        | RSA, Diffie-Hellman, ECC                                          |
| Offentlig nyckel autentisering | Används för att autentisera eller signera data under TLS-handskakning                                            | RSA, DSS                                                          |
| Chiffrering av session            | Algoritmer för symmetrisk nyckel som används för att kryptera program data under TLS-sessionen                       | AES, RC4                                                          |
| Sessions-hash              | Används för att bevara integriteten hos meddelanden under TLS-sessionen (säkerställer att data inte har ändrats) | SHA-1, SHA-256                                                    |
| TLS-PRF                   | Används för att generera nyckel material och i hand skaknings-hashvärdet i TLS-handskakning                          | PRF baseras på hash-rutiner – SHA-1 + MD5, SHA-256, SHA-512 |

NX_SECURE_TLS_CIPHERSUITE_INFOs strukturen definieras enligt följande:

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
Fältet nx_secure_tls_ciphersuite innehåller värdet för IANA-ciphersuite och NX_CRYPTO_METHODs pekare representerar de 5 metoder som används av ciphersuite. De skalära värdena (nx_secure_tls_iv_size, nx_secure_tls_key_size och nx_secure_tls_hash_size) är information och ger information som kanske inte är tillgänglig i NX_CRYPTO_METHOD poster.

Som exempel kommer vi att titta på standard ciphersuite för TLS, TLS_RSA_WITH_AES_128_CBC_SHA, som anger användningen av RSA-, AES-CBC med 128-bitars nycklar och SHA-1 för sessions-hashing. Ingen TLS-PRF har angetts för den här ciphersuite, så i TLSv 1.2-läge används standard SHA-256-PRF. Observera att alla krypteringssviter använder SHA-1 + MD5 PRF i TLS 1,0 och 1,1, oavsett vilken PRF som anges i tabellen.

Posten i NX_SECURE_TLS_CIPHERSUITE_INFOs tabellen i det generiska kryptografi biblioteket definieras enligt följande:

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

Observera att nyckel storleken för-sessionen avgörs av ciphersuite, men för offentliga nyckel metoder är nyckel storleken inte känd förrän TLS-handskakningen är igång sedan de offentliga nycklarna finns i de digitala certifikat som utbyts under hand skakningen.

### <a name="x509-cipher-lookup-table"></a>X. 509 chiffer-uppslags tabell

Precis som NX_SECURE_TLS_CIPHERSUITE_INFO tabell mappar NX_SECURE_X509_CRYPTOs strukturen kryptografiska rutiner till kända värden. Om det gäller X. 509 är identifierarna egentligen de OID: er som definierats av X. 509 och som registrerats med ISO-och ITU-standard-organen. OID är värden för flera byte i varierande längd som är utformade för att unikt identifiera olika uppgifter i olika telekommunikations standarder, inklusive kryptografiska rutiner som används i digitala certifikat. På grund av det faktum att OID är varierande längd mappar NetX Secure TLS de officiella OID-värdena till konstanter med fast längd som används internt (se nx_secure_x509. h). Dessa konstanter används i NX_SECURE_X509_CRYPTOs strukturen, som definieras enligt följande:

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

Det första fältet *nx_secure_x509_crypto_identifier* är den interna OID-representation som används av netx Secure.

Det andra och tredje fältet pekar på NX_CRYPTO_METHOD objekt som representerar de kryptografiska metoder som identifieras av OID: en offentlig nyckel åtgärd som kopplats till en hash-rutin. Observera att varje digitalt certifikat kan ha mer än en OID för kryptografiska rutiner.

Metod tabellen för X. 509 är konstruerad på samma sätt som ciphersuite lookup-tabellen. Som exempel kommer vi att titta på OID för RSA_SHA1. Det faktiska OID-värde för RSA_SHA1 är följande:

```C
{iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1) sha1-with-rsa-
signature(5)}
```
OID: en visas i ASN. 1-syntax och har ett numeriskt värde för 1.2.840.113549.1.1.5. Värdet kodas sedan i binärt format, vilket skapar följande byte:

```C
UCHAR RSA_SHA1_OID = { 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x05 };
```
Den faktiska konverteringen från ASN. 1 till binärformatet ligger utanför det här dokumentets omfattning. Sök efter ASN. 1-kodningar för OID: er för mer information. Den binära representationen av OID som stöds av NetX Secure finns i filen *nx_secure_x509. c*.

När vi har en mappning av den faktiska OID-identifieraren till en internt känd konstant, kan vi skapa en post för RSA_SHA1 i tabellen NX_SECURE_X509_CRYPTO:

```C
{ 
    NX_SECURE_TLS_X509_TYPE_RSA_SHA_1,    /* Internal OID constant. */
    &crypto_method_rsa,                   /* RSA method (NX_CRYPTO_METHOD). */ 
    &crypto_method_sha1                   /* SHA-1 method (NX_CRYPTO_METHOD). */
}, 
```
### <a name="default-tls-routines"></a>Standard-TLS-rutiner

Som nämnts ovan kräver TLS vissa standard rutiner för generering av nycklar och meddelande verifiering under hand skakningen. Den primära rutinen är TLS-Pseudo-Random funktion eller PRF. PRF baseras på hash-rutiner och kan användas för att generera en godtycklig mängd pseudo-slumpmässiga data<sup>20</sup> för nyckel skapande eller andra användnings sätt.

Förutom PRF använder varje version av TLS standard-hash-rutiner som också måste tillhandahållas. För TLS-versionerna 1,0 och 1,1 är dessa hash-rutiner MD5 och SHA-1. TLS version 1,2 kräver endast SHA-256.

I NX_SECURE_TLS_CRYPTOs strukturen finns NX_CRYPTO_METHOD pekare för MD5, SHA-1, SHA-256, TLS-version 1.0/1.1 PRF och standard-TLS 1,2-PRF.

TLS 1,3-stöd lägger till fält för HKDF (nyckel generering), HMAC (för vissa hash-åtgärder som används under hand skakningen) och ECDHE (krävs för TLS 1,3-funktioner).

Som tillhandahålls i det allmänna biblioteket för program varu kryptografi är program varu versioner av TLS PRF. För TLS 1.0/1.1 kallas den här funktionen *nx_crypto_tls_prf_1*. För TLS 1,2 kallas funktionen *nx_secure_tls_prf_sha256*. Suffixet "1" representerar den äldre-TLS 1,0-PRFen och "SHA256"-suffixet avser det faktum att TLS 1,2 standard PRF baseras på SHA-256. När stöd för andra PRF-rutiner behövs kommer suffixet för dessa rutiner att avspegla den hash-metod som används. Eftersom PRF-rutinerna baseras på hash-metoder kan de underliggande hash-rutinerna i maskin vara accelereras oberoende på olika plattformar.

Förutom uppslags tabellerna TLS ciphersuite och X. 509, med standard-PRF-och hash-rutiner som är fyllda i NX_SECURE_TLS_CRYPTOs strukturen, kan fyllas och användas för att initiera en TLS-session.

20. "Pseudo-slumpmässig" syftar på det faktum att PRF är deterministisk, vilket innebär att det alltid kommer att producera samma utdata med samma indata, men slumpmässigt i det faktum att utdata inte är förutsägbara. TLS använder den här egenskapen i PRF för att generera sessionsnycklar från olika offentliga data tillsammans med huvud hemligheten som utbyts under hand skakningen med hjälp av en offentlig nyckel chiffer som RSA.

### <a name="cryptographic-metadata"></a>Kryptografiska metadata

Innan vi kan initiera TLS-sessionen med NX_SECURE_TLS_CRYPTO-tabellen måste vi allokera buffertutrymme för metadata för den kryptografiska rutinen. Metadata används för att lagra all status som är kopplad till en viss rutin som representeras av kontroll blocket. *Nx_crypto_metadata_area_sizes* fältet för varje NX_CRYPTO_METHOD måste anges till storleken på den kontroll struktur som är kopplad till den rutinen eller så kan TLS-initieringen inte användas korrekt för det utrymme som behövs, vilket kan orsaka buffertöverskridning.

Innan TLS-sessionen skapas måste bufferten för metadata tilldelas. Bufferten delas automatiskt upp av nx_secure_tls_session_create och utrymmet är reserverat för var och en av de rutiner som finns i tabellen med kryptografiska metoder. Observera att eftersom endast en ciphersuite är aktiv i taget i en TLS-session, påverkar inte antalet krypteringssviter som behövs – utrymmet är reserverat för var och en av de fem ciphersuite-rutinerna med den maximala kontroll block storleken för den kategorin i tabellen ciphersuite lookup.

För att göra det enkelt att beräkna buffertstorleken utför tjänsten *nx_secure_metadata_size_calculate* samma beräkningar som nx_secure_tls_session_create men returnerar bara den sammanlagda buffertstorleken för metadata som krävs i byte.

### <a name="initializing-the-tls-session"></a>Initiera TLS-sessionen

När NX_CRYPTO_METHOD och NX_SECURE_TLS_CRYPTO objekt har skapats och metadata-ytan reserverat, kan vi initiera en TLS-session enligt följande (värden som tas från ovanstående exempel):

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
