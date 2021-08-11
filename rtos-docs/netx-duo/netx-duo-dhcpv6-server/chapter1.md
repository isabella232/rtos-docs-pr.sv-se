---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo DHCPv6-server
description: Det här dokumentet förklarar i detalj hur NetX Duo DHCPv6-servern tilldelar IPv6-adresser till DHCPv6-klienter.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14a9d76731d949e3556a019756caf38b4ef440abfa4cfb927c47607e5712d9ac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783664"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo DHCPv6-server

I IPv6-nätverk krävs DHCPv6is för att klienter ska kunna hämta IPv6-adresser. Det ersätter inte DHCP, som är begränsat till IPv4i det att det inte erbjuder IPv4-adresser. DHCPv6 har liknande funktioner som DHCP samt många förbättringar. En klient som inte eller inte kan använda automatisk konfiguration av IPv6-adresser kan använda DHCPv6 för att tilldelas en unik global IPv6-adress från en DHCPv6-server.

NetX Duo har utvecklats för att stödja IPv6-nätverksbaserade program och nätverksprotokoll som DHCPv6. Det här dokumentet förklarar i detalj hur NetX Duo DHCPv6-servern tilldelar IPv6-adresser till DHCPv6-klienter.

## <a name="dhcpv6-communication"></a>DHCPv6-kommunikation

**DHCPv6-meddelandestruktur**

Meddelandeinnehåll är i princip en meddelanderubrik följt av ett eller flera (vanligtvis fler) alternativblock. Nedan visas den grundläggande strukturen där varje block representerar en byte:

![Diagram som visar DHCPv6-meddelande och blockstruktur för alternativ.](media/image2.jpg)

**Bild 1. DHCPv6-meddelande och blockstruktur för alternativ**

Fältet 1 byte Msg-Type anger typen av DHCPv6-meddelande. Fältet Transaktions-ID med 3 byte anges av klienten. Det kan med valfri sekvens med tecken men måste vara unikt för varje klientmeddelande till servern (bevaras över dubblettmeddelanden som skickas av klienten). Servern använder det transaktions-ID:t för varje svar till klienten för att klienten ska kunna matcha servermeddelanden i händelse av paket som fördröjs eller tas bort i nätverket. I fältet Transaktions-ID finns ett eller flera DHCPv6-alternativ som används för att ange vad klienten begär.

DHCPv6-alternativstrukturen består av en alternativkod, ett fält för alternativlängd som inte innehåller längd- eller kodfälten och slutligen själva alternativdata som är ett eller flera fält med alternativkod på 2 byte för de data som klienten begär.

Vissa alternativblock har kapslade alternativ. Till exempel innehåller alternativet *Identity Association for Non Temporary Address (IANA)* ett eller flera *IA-alternativ (Identity Association)* för att begära IPv6-adresser. *IANA-alternativet* som returneras i serversvarsmeddelandet innehåller samma *IA-alternativ* med IPv6-adressen och lånetiderna som beviljas av servern, samt ett *statusalternativ* som anger om det finns ett fel med klientadressbegäran.

En lista över alla alternativblock och deras beskrivning finns i **bilaga A**.

**DHCPv6-meddelandetyper**

Även om DHCPv6 kraftigt förbättrar funktionerna i DHCP, använder den samma antal meddelanden som DHCP och stöder samma leverantörsalternativ som DHCP. Listan över DHCPv6-meddelanden är följande:

- SOLICT (1) (skickas av klienten)
- ANNONSERA (2) (skickas av server)
- BEGÄRAN (3) (skickas av klienten)
- REPLY (7) (skickas av server)
- CONFIRM (4) (skickas av klienten)
- RENEW (5) (skickas av klienten)
- REBIND (6) (skickas av klienten)
- VERSION (8) (skickas av klienten)
- NEKA (9) (skickas av klienten)
- INFORM_REQUEST (11) (skickas av klienten)
- RECONFIGURE* (10) (skickas av server)

*RECONFIGURE stöds inte av NetX Duo DHCPv6-servern.

Den grundläggande DHCPv6-begärandesekvensen, med motsvarande DHCPv4-meddelandetyp inom parentes, är följande:

Client ***Request** _ (_Discovery *) Server **Advertisement** (* Offer ) Client ***Request** (* Request ) Server ***Reply** (DHCPAck*)*

Klienten **förnyar**(samma) **serversvar** *(DHCPAck)*

## <a name="dhcpv6-message-validation"></a>DHCPv6-meddelandeverifiering

Transaktions-ID: Klienten måste generera ett transaktions-ID för varje meddelande som skickas till servern. DHCPv6-servern avvisar alla meddelanden från klienten som inte matchar detta transaktions-ID. Servern måste i sin tur använda samma transaktions-ID i sina svar tillbaka till klienten.

**Unika DHCPv6-identifierare (DUID: er)**

Alla servermeddelanden måste också innehålla en unik DHCPv6-identifierare (DUID) i varje meddelande, annars bör DHCPv6-klienten inte acceptera meddelandet. DUID för ett länklager (LL) är ett kontrollblock som innehåller klientens MAC-adress, maskinvarutyp och DUID-typ. En LLT-DUID (Link Layer Time) innehåller dessutom ett tidsfält som minskar risken för att DUID inte är unikt i värdnätverket. Därför rekommenderar RFC 3315 LLT DUID över LL DUIDs. Om värdprogrammet inte skapar ett eget unikt tidsvärde tillhandahåller NetX Duo DHCPv6 ett standardvärde. Den tredje typen av DUID är DuID för företag (leverantör) som innehåller ett registrerat enterprise-ID (som registrerats med IANA) och privata data som är variabel i typ och längd, t.ex. baserat på minnesstorlek, operativsystemtyp för annan maskinvarukonfiguration. Se listan över konfigurationsalternativ någon annanstans i det här dokumentet för att konfigurera värden för tilldelade serverleverantörer och privata ID:n.

Klienten måste också inkludera sitt DUID i sina meddelanden till servern förutom INFORM_REQUEST, annars avvisar servern dem.

**DHCPv6-klientserversessioner**

DHCPv6-klienter och servrar utbyter meddelanden via UDP. Klienten använder port 546 för att skicka och ta emot DHCPv6-meddelanden och servern använder port 547. Klienten använder initialt sin länk-lokala adress för att överföra och ta emot DHCPv6-meddelanden. Den skickar alla *meddelanden* till DHCPv6-servrar med hjälp av en reserverad multicast-adress med länkomfång som kallas All_DHCP_Relay_Agents_and_Servers multicast-adress *(FF02::01:02).*

FörIPv6-adresstilldelningsbegäranden lyssnar DHCPv6-servern efter begärda *meddelanden* som skickas till All_DHCP_Relay_Agents_and_Servers adressen.  I begäran *om* begäran om begäran kan klienten begära tilldelningen av en specifik IPv6-adress eller låta servern välja en. Den kan också begära annan information om nätverkskonfigurationen från servern.

Om DHCPv6Server extraherar  ett giltigt begärandemeddelande och kan tilldela en IPv6-adress till klienten, svarar den med ett meddelande om annonsering som innehåller den IPv6-adress som den beviljar klienten, IPv6-adressens lånetid och eventuell ytterligare information som begärs av klienten.  Om klienten accepterar servererbjudandet svarar den  med ett meddelande om begäran så att servern vet att den accepterar IPv6-adressen. Servern bekräftar att klienten är bunden till IPv6-adressen med ett *svarsmeddelande.*

Om DHCPv6-klientens meddelande är ogiltigt ignorerar servern meddelandet tyst. Om servern inte kan bevilja begäran skickas  ett svarsmeddelande med en indikation om problemet i statusfältet för alternativet IP-adress-IANA. Om duplicerade klientbegäranden tas emot skickar servern sitt tidigare DHCPv6-svar igen, förutsatt att klienten helt enkelt inte tog emot paketet.

Det är upp till klienten att kontrollera att dess tilldelade IPv6-adress från servern inte är tilldelad till en annan värd i systemet med hjälp av olika IPv6-protokoll, till exempel dubblettadressidentifiering. Om adressen inte är unik skickar klienten ett neka-meddelande *till* servern. Servern uppdaterar sin IP-lånetabell med den här informationen och registrerar att adressen redan har tilldelats. Under tiden måste klienten starta om DHCPv6-begäran med ett annat *meddelande om begäran.*

Förutom en IPv6-adress behöver en klient troligen också känna till DNS-servern och eventuellt annan nätverksinformation, till exempel nätverksdomännamnet. DHCPv6 ger möjlighet att begära den här informationen genom  att  antingen använda alternativbegäranden i meddelanden om begäran och begäran eller separat i *meddelanden om informationsbegäran.* DHCPv6-alternativ beskrivs senare i det här kapitlet.

**Varaktighet för IPv6-lån**

När servern beviljar en IPv6-adress till en klient tilldelar den även lånetid (livslängd) i IANA-alternativet för när den rekommenderar klienten att börja förnya  (T1) eller binda om (T2) sin IPv6-adress med hjälp av förnya och *binda* om meddelanden. Skillnaden mellan de två är att Klienten dirigerar meddelandet *Förnya* till servern genom att inkludera Server DUID i *förnyelsebegäran.* Den anger dock ingen server och inkluderar därför inte server-DUID i meddelandet *Rebind* till All_DHCP_Relay_Agents_and_Servers adressen.  IA-alternativet som innehåller den faktiska IPv6-adressen som servern beviljar klienten innehåller också önskad och giltig livslängd när den hyrda IPv6-adressen blir inaktuell eller föråldrad (ogiltig).

NetX Duo DHCPv6-servern upprätthåller en sessions-timeout för varje klient för att spåra tiden mellan klientmeddelanden. Detta är nödvändigt om en klientvärd förlorar anslutningen eller om nätverket ligger nere. När tidsgränsen för sessionen går ut antas det att klienten antingen inte längre är intresserad eller kan göra DHCPv6-begäranden från servern. Servern tar bort klientposten och returnerar eventuellt tilldelad IPv6-adress tillbaka till den tillgängliga poolen. Väntetiden för sessionen är ett alternativ som kan konfigureras av användaren.

Om klienten vill frigöra sin IPv6-adress, eller upptäcker att den IPv6-adress som tilldelats den av DHCPv6-servern redan används, skickar den meddelandet *Release* (Version) eller *Decline (Neka).* När det gäller ett *lanseringsmeddelande* returnerar servern denna IPv6-adressstatus tillbaka till den tillgängliga poolen. När det gäller  meddelandet Neka uppdateras ip-lånetabellen för att indikera att den här IPv6-adressen inte är tillgänglig (ägs av en annan entitet någon annanstans i nätverket).

**IPv6-lån och klientpostdata**

När DHCPv6-servern börjar acceptera klientbegäranden finns en lista över aktiva klienter som begär eller har tilldelats IPv6-adresser. Servern söker efter IP-lånets upphörande med hjälp av en lånetimer som regelbundet uppdaterar klientens lånetid. När varaktigheten överskrider den giltiga livslängden rensar servern klientposten och returnerar sin IPv6-adress tillbaka till den tillgängliga poolen. Det är upp till klienten att starta förnyelsen/återbindningsprocessen innan detta sker!

NetX Duo DHCPv6 Server-klientposttabellen innehåller information för att identifiera klienter och "tillstånd"-information för att verifiera DHCPv6-klientbegäranden och tilldela eller om tilldelar IPv6-adresser. Sådan information omfattar:

- Klientens unika DHCPv6-identifierare (DUID) som unikt definierar varje klientvärd i ett nätverk. Klienten måste alltid använda samma DUID för alla sina DHCPv6-meddelanden.

- Klientidentitetsassociaten för icke-tillfälliga adresser (IANA) och IPv6-adress (Identity Association IPv6) kumulativt som definierar tilldelningsparametrarna för klientens IPv6-adress.

- Begäranden om klientalternativ (DNS-server, domännamn osv.).

- Klientens IPv6-källadress (om den har angetts) och måladressen (om inte multicast) för den senaste DHCPv6-begäran.

- Klientens senaste meddelandetyp och DHCPv6 -tillstånd.

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>Krav och begränsningar för NetX Duo DHCPv6-servern

NetX Duo DHCPv6 Server API kräver ThreadX 5.1 eller senare och NetX Duo 5.5 eller senare.

**Krav**

***Konfigurera IP-trådaktivitet***

NetX Duo DHCPv6-servern kräver att en IP-instans skapas för att skicka och ta emot meddelanden till DHCPv6 på dess nätverkslänk. Detta görs med  hjälp av nx_ip_create tjänsten. Själva NetX Duo DHCPv6-servern måste skapas. Detta görs med  hjälp av nx_dhcpv6_server_create tjänsten.

DHCPv6 använder NetX Duo, ICMPv6 och UDP. Därför måste IPv6 först aktiveras innan du använder DHCPv6-servern genom att anropa följande NetX Duo-tjänster:

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

Innan DHCPv6-servern kan startas har den dessutom ett antal konfigurerade uppgifter att utföra:

- Skapa och verifiera dess lokala och globala IPv6-adresser. Adressverifieringen utförs automatiskt av NetX Duo med identifiering av dubblettadresser om det är aktiverat. Mer information om länk för lokal och global IP-adressverifiering finns i Användarhandbok för *NetX Duo.*

- Ange nätverksgränssnittsindexet för dess DHCPv6-gränssnitt.

- Skapa ett IP-adressintervall för tilldelningsbara IPv6-adresser. Eller, om data finns från en tidigare Server DHCPv6-session, måste IPv6-lånetabellen och klientposter från den sessionen överföras från ej beständigt minne till DHCPv6-servern. Det lilla exempelsystemet någon annanstans i det här dokumentet visar DHCPv6-servertjänsterna för att åstadkomma detta krav.

- Ange Server DUID. Om servern har skapat sitt DUID i en tidigare session måste den använda samma data för att skapa samma DUID för meddelanden till sina klienter. Det lilla exempelsystemet någon annanstans i det här dokumentet visar hur detta krav uppnås.

Nu är DHCPv6-servern redo att köras. Internt skapar NetX Duo DHCPv6-servern en UDP-socket som är bunden till port 547 och börjar lyssna efter klientbegäranden.

***Krav för paketpool***

NetX Duo DHCPv6-servern kräver en paketpool för att skicka DHCPv6-meddelanden. Storleken på paketpoolen vad gäller paketnyttolast och antal paket som är tillgängliga är användarkonfigurerbar och beror på den förväntade volymen av DHCPv6-meddelanden och andra överföringar som värdprogrammet kommer att skicka.

Ett typiskt DHCPv6-meddelande är cirka 200–300 byte beroende på antalet ytterligare alternativ som begärs av klienten och information som är tillgänglig från servern.

***Ange DHCPv6-servergränssnittet***

DHCPv6-servern använder som standard det primära nätverksgränssnittet som det gränssnitt som den accepterar klientbegäranden på. Värdprogrammet måste dock fortfarande ange det globala adressindex som användes för att skapa den globala serverns adress. DHCPv6-gränssnittsindexet och det globala adressindexet anges med *hjälp nx_dhcpv6_server_interface_set* tjänsten. Detta visas också i det "lilla exemplet" i det här dokumentet.

***Spara DHCPv6 DUID vid omstarter av servern***

DHCPv6-protokollet kräver att servern använder samma DUID vid flera omstarter. Alla data som används för att skapa DUID måste därför lagras och hämtas från icke-volatilt minne för detta krav. För värdar som använder DUID för länkskikt plus tid som kräver åtkomst till en realtidsklocka. NetX Duo DHCPv6-värdprogrammet bör innehålla dataåtkomst i realtid för att generera ett tidsvärde för den första server-DUID-genereringen och lagra dessa data för återanvändning vid efterföljande serversessioner. Den *nx_dhcpv6_set_server_duid* tar sedan DUID-data som argument, samt konfigurationsalternativ beroende på DUID-typ, för att skapa (eller återskapa) sitt eget DUID.

***Skapande av tilldelningsbar IPv6-adresslista***

När DHCPv6-servern har skapats måste servervärdprogrammet skapa ett intervall med tilldelningsbara globala IPv6-adresser om det inte finns några tidigare lagrade listdata för IP-adresser. Detta görs med hjälp av *nx_dhcpv6_create_ip_address_range* som tar som indata en start- och slutadress för IPv6.

***Spara DHCPv6-adresser och klientdata***

DHCPv6-protokollet kräver att DHCPv6-servern sparar sina klient- och IPv6-adressdata i icke-volatil lagring vid omstart av servern. NetX Duo DHCPv6-servern har flera API:er för att ladda upp och ladda ned klient- och IPv6-adressdata till respektive från DHCPv6-servern:

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

Du måste ladda upp data till servern innan du startar om servern. Nedladdning av data ska endast göras efter att DHCPv6-servern har stoppats (eller pausats). Tjänsterna för att göra detta beskrivs i detalj senare i det här dokumentet. NetX Duo DHCPv6 tillhandahåller dock inte någon åtkomst till icke-volatil lagring. Detta måste hanteras av värdprogrammet. Det lilla exemplet visar hur värdprogrammet gör detta.

***Server DHCP Unik identifierare (DUID)***

Server-DUID definierar unikt DHCPv6-servervärden i nätverket. Om en server inte har skapat sitt DUID tidigare kan den använda nx_dhcpv6_server_set_duid *för* att skapa ett. Enligt RFC 3315 måste DHCPv6-servern spara DUID till icke-volatilt minne för att kunna hämta den efter omstart av servern. DHCPv6-servern har stöd för DUID-typerna Länkskikt, Tid för länklager och Företag (leverantör tilldelad). Observera att klienten måste skicka i leverantörstypen DUID direkt. Alternativet för DUID:er av leverantörstyp (17) stöds inte direkt av NetX Duo DHPv6-servern.

DHCPv6-serverns värdprogram har standardvärden för IPv6-adresstilldelning, inklusive timeout för lån. Se Konfigurerbara alternativ senare i det här dokumentet för information om hur du anger dessa alternativ. :

*IANA-kontrollblocket* innehåller fälten T1 och T2. *IA-blocket* i *IANA-kontrollblocket* innehåller de önskade och giltiga livslängdsfälten. Värdprogrammet har konfigurerbara alternativ som definierats någon annanstans i det här dokumentet för att ange dessa alternativ. De tilldelas till alla klient-IPv6-adressbegäranden.

Dessa parametrar för DHCPv6 IP-lån definieras nedan.

T1 – Tiden i sekunder när klienten måste börja förnya sin IPv6-adress från den server som tilldelade den.

T2 – Tiden i sekunder då klienten måste börja binda om IPv6-adressen, om förnyelsen misslyckades, med någon server på sin länk.

Önskad livslängd – tiden i sekunder när klientadressen blir inaktuell om klienten inte har förnyat eller omgående. Klienten kan fortfarande använda den här adressen.

Giltig livslängd – tid i sekunder när klientens IP-adress har upphört att gälla och får inte använda den här adressen i dess nätverksöverföringar.

RFC rekommenderar T1 och T2 gånger som är 0,5 respektive 0,8 för önskad livslängd i alternativet *Klient-IANA.* Om servern inte har några inställningar bör dessa tider anges till noll. Om ett serversvar innehåller T1 och T2 gånger inställda på noll, låter den klienten ange sina egna T1- och T2-tider.

**Restriktioner**

NetX Duo DHCPv6-servern stöder inte följande DHCPv6-alternativ:

  - Alternativet För snabb förfrågning som optimerar DHCPv6-adressbegärandeprocessen till att endast begära och svara på meddelandeutbyte

  - Konfigurera om alternativet som gör att servern kan initiera ändringar av klientens IP-adressstatus.

  - Unicast-alternativ; alla klientmeddelanden måste skickas till den *All_DHCP_Relay_Agents_and_Servers* multicast-adressen i stället för direkt till DHCPv6-servern.

  - Identity Association för alternativet Temporary Addresses (IA_TA)), som är en tillfällig IP-adress som beviljas till en klient.

  - Flera IA-alternativ (IPv6-adresser) per klientbegäran

  - Relävärd mellan DHCPv6-klienten och servern, t.ex. klient och server måste finnas i samma nätverk.

  - IPSec och autentisering stöds inte i DHCPv6-meddelanden. IP-instansen kan dock vara IPSec-aktiverad beroende på vilken version av NetX Duo som används.

  - NetX Duo DHCPv6-servern har direkt stöd för begäran om DNS-serveralternativ. Detta kan komma att ändras i framtida versioner.

  - Alternativet Prefixdelegering stöds inte.

  - Autentisering av DHCPv6-meddelanden även om IPSec kan aktiveras i den underliggande NetX Duo-miljön. NetX Duo DHCPv6-servern stöder inte heller vidarebefordran av anslutningar till klienterna. Det förutsätts att alla klientbegäranden kommer från värdar i servernätverket.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>Återanropsfunktioner för NetX Duo DHCPv6-server

*nx_dhcpv6_IP_address_declined_handler*

När DHCPv6-klienten skickar ett neka-meddelande markerar NetX Duo DHCPv6-servern adressen som inte tillgänglig i dess IPv6-adresstabeller. För att kunna anpassa serverhanteringen av det här meddelandet tillhandahålls *nx_dhcpv6_IP_address_declined_handler* *.* Återanropet är dock inte implementerat för närvarande.

*nx_dhcpv6_server_option_request_handler*

När DHCPv6-klientens meddelande innehåller data om alternativbegäran vidarebefordrar NetX Duo DHCPv6-servern varje alternativkod för begäran till användarens återanrop, om sådan har definierats. Detta ger NetX Duo-servern möjlighet att låta den användardefinierade återanropet fylla i data. Den här funktionen är dock inte implementerad för närvarande.

## <a name="supported-dhcpv6-rfcs"></a>DHCPv6-RFC:er som stöds

NetX Duo DHCPv6 är kompatibel med RFC3315, RFC3646 och relaterade RFC: er.