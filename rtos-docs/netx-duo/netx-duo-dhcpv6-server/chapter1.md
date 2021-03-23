---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCPv6 server
description: Det här dokumentet beskriver i detalj hur NetX Duo DHCPv6-servern tilldelar IPv6-adresser till DHCPv6-klienter.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6cf7baa91b1804876b97b1d75d1872d1120ad028
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826043"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo DHCPv6 server

I IPv6-nätverk krävs DHCPv6 för klienter för att hämta IPv6-adresser. Den ersätter inte DHCP som är begränsad till IPv4-och som inte erbjuder IPv4-adresser. DHCPv6 har liknande funktioner som både DHCP och många förbättringar. En klient som inte eller kan använda automatisk konfiguration av IPv6-tillstånd kan använda DHCPv6 för att tilldela en unik global IPv6-adress från en DHCPv6-server.

NetX Duo utvecklades för att stödja IPv6-nätverksbaserade program och nätverks protokoll som DHCPv6. Det här dokumentet beskriver i detalj hur NetX Duo DHCPv6-servern tilldelar IPv6-adresser till DHCPv6-klienter.

## <a name="dhcpv6-communication"></a>DHCPv6-kommunikation

**DHCPv6-meddelande struktur**

Meddelande innehållet är i grunden en meddelande rubrik följt av ett eller flera (oftast fler) alternativ block. Nedan visas den grundläggande strukturen där varje block representerar en byte:

![Diagram som visar en block struktur för DHCPv6-meddelanden och alternativ.](media/image2.jpg)

**Bild 1. DHCPv6-meddelande och alternativ block struktur**

I fältet 1-byte Msg-Type anges typen av DHCPv6-meddelande. Fältet 3 byte Transaction-ID anges av klienten. Den kan innehålla en sekvens med tecken, men måste vara unik för varje klient meddelande till servern (bevaras i duplicerade meddelanden som skickas av klienten). Servern använder det transaktions-ID: t för varje svar på klienten för att låta klienten matcha Server meddelanden i händelse av paket som är fördröjda eller nedbrutna i nätverket. Efter fältet transaktions-ID är ett eller flera DHCPv6-alternativ som används för att ange vad klienten begär.

Alternativ strukturen för DHCPv6 består av en alternativ kod, fältet alternativ längd, som inte innehåller fälten längd eller kod, och slutligen alternativ data som är ett eller flera alternativ kod fält i 2 byte för de data som klienten begär.

Vissa alternativ block har kapslade alternativ. Till exempel innehåller en *identitets koppling för alternativet ej tillfällig adress (IANA)* ett eller flera alternativ för *identitets associationer (AI)* för att begära IPv6-adresser. Det *IANA* -alternativ som returnerades i Server svars meddelandet innehåller samma *IA* -alternativ med IPv6-adressen och de låne tider som har beviljats av servern, samt ett *status* alternativ som anger om det finns ett fel med klient adress förfrågan.

En lista över alla alternativ block och deras beskrivning anges i **bilaga A**.

**DHCPv6-meddelande typer**

Även om DHCPv6 avsevärt förbättrar funktionerna i DHCP, används samma antal meddelanden som DHCP och stöder samma leverantörs alternativ som DHCP. Listan över DHCPv6-meddelanden är följande:

- SOLICT (1) (skickas av klienten)
- Annonsera (2) (skickas av servern)
- BEGÄRAN (3) (skickas av klienten)
- SVAR (7) (skickat av servern)
- BEKRÄFTA (4) (skickas av klienten)
- FÖRNYA (5) (skickas av klienten)
- BIND (6) (skickas av klienten)
- VERSION (8) (skickas av klienten)
- NEKA (9) (skickas av klienten)
- INFORM_REQUEST (11) (skickas av klienten)
- Konfigurera om * (10) (skickas av servern)

* Omkonfiguration stöds inte av NetX Duo DHCPv6-servern.

Den grundläggande DHCPv6-sekvensen för begäran, med motsvarande DHCPv4-meddelande typ inom parentes, är följande:

Client ***solicit** _ (_Discovery *) Server **annonsering** (* erbjudande *)-  klientbegäran*(begäran *) (* DHCPACK *)

Klient **förnyelse**(samma) Server **svar** (*DHCPACK*)

## <a name="dhcpv6-message-validation"></a>DHCPv6-meddelande validering

Transaktions-ID: klienten måste generera ett transaktions-ID för varje meddelande som skickas till servern. DHCPv6-servern avvisar alla meddelanden från klienten som inte matchar detta transaktions-ID. Servern måste i sin tur använda samma transaktions-ID i sina svar till klienten.

**DHCPv6 unika identifierare (DUIDs)**

Alla Server meddelanden måste också innehålla en GUID (DHCPv6 Unique Identifier) i varje meddelande, annars bör DHCPv6-klienten inte acceptera meddelandet. Ett länk lager (lla) DUID är ett kontroll block som innehåller klientens MAC-adress, maskin varu typ och DUID-typ. Ett LLT-DUID (Link Layer Time) innehåller även ett Time-fält som minskar risken för att DUID inte är unikt i värd nätverket. Av den anledningen rekommenderar RFC 3315 LLT DUIDs över lla DUIDs. Om värd programmet inte skapar något eget unikt tids värde, kommer NetX Duo DHCPv6 att tillhandahålla ett standardvärde. DUID-typen är företagets (tilldelad) DUID som innehåller ett registrerat företags-ID (som i registrerade med IANA) och privata data som är variabel i typ och längd, t. ex. beroende på minnes storlek, typ av operativ system för annan maskin varu konfiguration. Se listan över konfigurations alternativ någon annan stans i det här dokumentet för att konfigurera server leverantörens tilldelade och privata ID-värden.

Klienten måste även inkludera sitt DUID i sina meddelanden till servern, med undantag för INFORM_REQUEST, eller så kommer servern att avvisa dem.

**DHCPv6 klient server sessioner**

DHCPv6-klienter och-servrar utbyter meddelanden över UDP. Klienten använder port 546 för att skicka och ta emot DHCPv6-meddelanden och servern använder port 547. Klienten använder den länk lokala adressen för att överföra och ta emot DHCPv6-meddelanden. Den skickar alla meddelanden till DHCPv6-servrar med hjälp av en reserverad, länkad multicast-adress som kallas *All_DHCP_Relay_Agents_and_Servers* multicast-adress *(FF02:: 01:02)*.

ForIPv6 adress tilldelnings begär Anden, DHCPv6-servern lyssnar efter *värvnings* meddelanden som skickas till *All_DHCP_Relay_Agents_and_Servers* -adressen. Klienten kan begära tilldelningen av en speciell IPv6-adress i *begär ande förfrågan* eller låta servern välja en. Den kan också begära annan information om nätverks konfigurationen från servern.

Om DHCPv6Server extraherar ett giltigt *värvnings* meddelande och kan tilldela en IPv6-adress till klienten, svarar den med ett *annonserings* meddelande som innehåller den IPv6-adress som den ska ge klienten, IPv6-adressens låne tid och eventuell ytterligare information som begärs av klienten. Om klienten accepterar Server erbjudandet svarar den *med ett meddelande* om att servern vet att den accepterar IPv6-adressen. Servern bekräftar att klienten är kopplad till IPv6-adressen med ett *svarsmeddelande* .

Om klienten DHCPv6-meddelandet är ogiltig, kommer servern att ignorera meddelandet tyst. Om servern inte kan tilldela begäran kommer den att skicka ett *svarsmeddelande* med en indikation på problemet i fältet status för alternativet IP-adress-IANA. Om duplicerade klient begär Anden tas emot, skickar servern om sitt tidigare DHCPv6-svar, förutsatt att klienten inte bara tog emot paketet.

Det är upp till klienten som kontrollerar att den tilldelade IPv6-adressen från servern inte är tilldelad till en annan värd i systemet med hjälp av olika IPv6-protokoll som dubblettidentifiering av dubbletter. Om adressen inte är unik skickar klienten servern ett meddelande om att *neka* . Servern uppdaterar sin IP-adresslån med den här informationen och registrerar att adressen redan har tilldelats. Under tiden måste klienten starta om DHCPv6-begäran med ett annat *Inbjudnings* meddelande.

Förutom en IPv6-adress måste även en klient känna till DNS-servern och eventuellt annan nätverks information, till exempel nätverks domänens namn. DHCPv6 ger möjlighet att begära den här informationen med hjälp av alternativ begär Anden *i begär Anden och* *begär* Anden, eller separat i meddelanden om *informations begär* Anden. DHCPv6-alternativen beskrivs senare i det här kapitlet.

**Varaktighet för IPv6-lån**

När servern beviljar en IPv6-adress till en klient tilldelar den också låne tiden (livs längd) i alternativet IANA för när den rekommenderar att klienten startar förnyelse (T1) eller OMBINDNING (T2) dess IPv6-adress med hjälp av *förnya* och *BIND* meddelanden. Skillnaden mellan de två är att klienten dirigerar *förnyelse* meddelandet till servern genom att inkludera serverns DUID i *förnyelse* förfrågan. Den anger dock ingen server och tar därför inte med en server-DUID, i *återbind* -meddelandet till *All_DHCP_Relay_Agents_and_Servers* -adressen. Alternativet IA som innehåller den faktiska IPv6-adressen som servern beviljar klienten, innehåller även de önskade och giltiga livs längderna när den lånade IPv6-adressen blir föråldrad eller föråldrad (ogiltig).

NetX Duo DHCPv6-servern har en tids gräns för sessioner för varje klient att spåra tiden mellan klient meddelanden. Detta är nödvändigt om en klient värd förlorar anslutning eller nätverket fungerar. När tids gränsen för sessionen upphör att gälla, antas det att klienten inte längre är intresse rad eller kan göra DHCPv6-begäranden på servern. Servern tar bort klient posten och returnerar alla preliminärt tilldelade IPv6-adresser tillbaka till den tillgängliga poolen. Timeout för session är ett alternativ för användare som kan konfigureras.

Om klienten vill frigöra sin IPv6-adress eller upptäcker att den IPv6-adress som tilldelats den av DHCPv6-servern redan används, skickar den en *version* eller *avböjer* meddelandet. Om det finns ett *release* -meddelande, returnerar servern att IPv6-adressens status tillbaka till den tillgängliga poolen. Om meddelandet *nekas* uppdaterar den IP-adresslån för att indikera att denna IPv6-adress inte är tillgänglig (ägs av en annan entitet någon annan stans i nätverket).

**IPv6-låne-och klient post data**

När DHCPv6-servern börjar acceptera klient begär Anden, upprätthålls en lista över aktiva klienter som begär eller har tilldelats IPv6-adresser. Servern kontrollerar att IP-lånet upphör att gälla med en låne timer som regelbundet uppdaterar klientens låne tid. När giltighets tiden överskrider den giltiga livs längden rensar servern klient posten och returnerar IPv6-adressen tillbaka till den tillgängliga poolen. Det är upp till klienten som startar förnyelse/OMBINDNINGS processen innan detta händer!

NetX Duo DHCPv6 server Client Record-tabellen innehåller information för att identifiera klienter och "State"-information för att verifiera DHCPv6-klient begär Anden och tilldela eller omtilldela IPv6-adresser. Sådan information omfattar:

- Klientens DHCPv6-unika identifierare (DUID) som unikt definierar varje klient värd i ett nätverk. Klienten måste alltid använda samma DUID för alla DHCPv6-meddelanden.

- Klient identitets associationen för icke-temporära adresser (IANA) och identitets associationens IPv6-adress (IA) ackumuleras i ackumulerad, som definierar parametrar för klientens IPv6-adress tilldelning.

- Klient alternativ begär Anden (DNS-server, domän namn osv.).

- Klientens IPv6-källkod (om den är angiven) och mål adress (om inte multicast) av den senaste DHCPv6-begäran.

- Klientens senaste meddelande typ och DHCPv6 ' State '.

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>NetX Duo DHCPv6-server krav och begränsningar

NetX Duo DHCPv6 server-API kräver ThreadX 5,1 eller senare, och NetX Duo 5,5 eller senare.

**Krav**

***Konfiguration av IP-tråds aktivitet***

NetX Duo DHCPv6-servern kräver att en IP-instans skapas för att skicka och ta emot meddelanden till DHCPv6 på dess nätverks länk. Detta görs med hjälp av tjänsten *nx_ip_create* . Du måste skapa en NetX Duo DHCPv6-server. Detta görs med hjälp av tjänsten *nx_dhcpv6_server_create* .

DHCPv6 använder NetX Duo, ICMPv6 och UDP. Därför måste IPv6 först aktive ras innan du använder DHCPv6-servern genom att anropa följande NetX Duo-tjänster:

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

Innan DHCPv6-servern kan startas finns det ett antal konfigurations åtgärder som du kan utföra:

- Skapa och verifiera dess globala och globala IPv6-adresser. Adress verifiering utförs automatiskt av NetX Duo med hjälp av dubblettidentifiering om den är aktive rad. I *användar handboken för netx Duo* finns mer information om hur du länkar lokala och globala IP-adresser verifierar.

- Ange Nätverks gränssnittets index för DHCPv6-gränssnittet.

- Skapa ett IP-adressintervall för tilldelnings bara IPv6-adresser. Eller, om det finns data från en tidigare Server-DHCPv6-session, måste IPv6-låne tabell och klient poster från den sessionen laddas upp från icke-flyktigt minne till DHCPv6-servern. Det lilla exempel systemet i det här dokumentet visar DHCPv6-server tjänsterna för att uppnå detta krav.

- Ange serverns DUID. Om servern har skapat ett DUID i en tidigare session måste den använda samma data för att skapa samma DUID för meddelanden till sina klienter. Det lilla exempel systemet i det här dokumentet visar hur detta krav uppnås.

DHCPv6-servern är nu klar att köras. Internt NetX Duo DHCPv6-servern skapar en UDP-socket som är kopplad till port 547 och börjar lyssna efter klient begär Anden.

***Krav för paket pool***

NetX Duo DHCPv6-servern kräver en modempool för att skicka DHCPv6-meddelanden. Storleken på modempoolen när det gäller paketets nytto last och antalet tillgängliga paket är att användaren kan konfigureras och är beroende av den förväntade volymen av DHCPv6-meddelanden och andra sändningar som värd programmet kommer att skicka.

Ett typiskt DHCPv6-meddelande är ungefär 200-300 byte beroende på antalet ytterligare alternativ som begärs av klienten och information som är tillgänglig från servern.

***Ange DHCPv6-server gränssnittet***

DHCPv6-servern som standard är det primära nätverks gränssnittet som gränssnitt som tar emot klient begär Anden på. Värd programmet måste dock fortfarande ange det globala adress index som det använde för att skapa serverns globala adress. DHCPv6-gränssnittets index och globala adress index anges med tjänsten *nx_dhcpv6_server_interface_set* . Detta visas också i det "små exemplet" i det här dokumentet.

***Spara DHCPv6 DUID för omstart av Server***

DHCPv6-protokollet kräver att servern använder samma DUID i flera omstarter. Alla data som används för att skapa DUID måste därför lagras och hämtas från ej beständigt minne för detta krav. För värdar som använder länk skiktet plus tids DUID som kräver åtkomst till en real tids klocka. NetX Duo DHCPv6-värd programmet ska innehålla real tids data åtkomst för att generera ett tids värde för att skapa ett tids värde för den första servern för att skapa DUID och lagra dessa data för åter användning på efterföljande Server sessioner. *Nx_dhcpv6_set_server_duid* tar sedan DUID-data som argument, samt konfigurations alternativ beroende på DUID-typ, för att producera (eller återskapa) sitt eget DUID.

***Skapa tilldelnings bara IPv6-adress lista***

När DHCPv6-servern har skapats måste Server värd programmet skapa ett intervall med globala IPv6-adresser för tilldelning om det inte finns några tidigare lagrade IP-adress list data. Detta görs med hjälp av tjänsten *nx_dhcpv6_create_ip_address_range* som tar sig in som en inledande och avslutande IPv6-adress.

***Sparar DHCPv6 tilldelnings bara adresser och klient data***

DHCPv6-protokollet kräver att DHCPv6-servern sparar sina klient-och IPv6-Datadata i beständigt lagrings utrymme i händelse av omstart av servern. NetX Duo DHCPv6-servern har flera API: er för att ladda upp och ladda ned klient-och IPv6-adress data till och från DHCPv6-servern:

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

Överföring av data till servern måste göras innan servern startas om. Hämtning av data bör bara utföras efter att DHCPv6-servern har stoppats (eller skjutits upp). Tjänsterna för att göra detta beskrivs i detalj senare i det här dokumentet. Men NetX Duo DHCPv6 ger ingen åtkomst till icke-flyktig lagring. Detta måste hanteras av värd programmet. Det lilla exemplet visar hur värd programmet gör detta.

***Serverns DHCP-unika identifierare (DUID)***

Serverns DUID definierar unikt DHCPv6-server värden i nätverket. Om en server inte har skapat sitt DUID tidigare kan den använda *nx_dhcpv6_server_set_duid* för att skapa en. Som enligt RFC 3315 måste DHCPv6-servern Spara DUID till ett beständigt minne för att kunna hämta det efter att servern har startats om. DHCPv6-servern har stöd för länk skiktet, länk skikt tid och företags (tilldelad) DUID-typer. Observera att klienten måste skicka ett DUID för leverantörs typ direkt. Alternativet för leverantörs typen DUIDs (17) stöds inte direkt av NetX Duo DHPv6-servern.

DHCPv6-serverns värd program har standardvärden för IPv6-adress tilldelning, inklusive låne tids gräns. Mer information om hur du ställer in dessa alternativ finns i alternativ för att konfigurera senare i det här dokumentet. :

*IANA* -kontroll blocket innehåller T1-och T2-fälten. *IA* -blocket i *IANA* -kontroll blocket innehåller de önskade och giltiga livstids fälten. Värd programmet har konfigurerbara alternativ som definierats någon annan stans i det här dokumentet för att ställa in dessa alternativ. De tilldelas alla klienters IPv6-adress begär Anden.

Dessa parametrar för DHCPv6 IP-leasing definieras nedan.

T1 – tid i sekunder när klienten måste påbörja förnyelse av sin IPv6-adress från den server som tilldelade den.

T2 – tiden i sekunder när klienten måste starta ombindningen av IPv6-adressen, om förnyelsen misslyckades, med valfri server på dess länk.

Önskad livs längd – tiden i sekunder då klient adressen blir föråldrad om klienten inte har förnyat eller kopplat från den. Klienten kan fortfarande använda den här adressen.

Giltig livstid – tiden i sekunder när klientens IP-adress har upphört att gälla och får inte använda den här adressen i dess nätverks överföring.

RFC rekommenderar T1-och T2-tider som är 0,5 respektive 0,8 för den önskade livs längden i alternativet klient- *IANA* . Om servern inte har någon inställning bör den ställa in dessa tider på noll. Om ett Server svar innehåller T1 och T2-tider har angetts till noll, låter klienten ange sina egna T1-och T2-tider.

**Restriktioner**

NetX Duo DHCPv6-servern stöder inte följande DHCPv6-alternativ:

  - Snabbt inchecknings alternativ som optimerar DHCPv6-adressens begär ande process till enbart Inbjudnings-och svars meddelande utbytet

  - Konfigurera om alternativet som gör att servern kan initiera ändringar i klientens IP-adress status.

  - Unicast-alternativ; alla klient meddelanden måste skickas till *All_DHCP_Relay_Agents_and_Servers* multicast-adress i stället för till DHCPv6-servern direkt.

  - Identitets Association för alternativet temporära adresser (IA_TA) som är en tillfällig IP-adress som beviljas till en klient.

  - Alternativ för flera IA (IPv6-adresser) per klient förfrågan

  - Relä värden mellan DHCPv6-klienten och-servern, t. ex. klienten och servern måste finnas i samma nätverk.

  - IPSec och autentisering stöds inte i DHCPv6-meddelanden. IP-instansen kan dock vara IPSec-aktiverad beroende på vilken version av NetX Duo som används.

  - NetX Duo DHCPv6-servern stöder direkt endast DNS-Server Option-begäran. Detta kan ändras i framtida versioner.

  - Alternativet för att delegera prefix stöds inte.

  - Autentisering av DHCPv6-meddelanden även om IPSec kan aktive ras i den underliggande NetX Duo-miljön. Varken NetX Duo DHCPv6-servern stöder relä anslutningar till klienterna. Det förutsätts att alla klient begär Anden kommer från värdar i Server nätverket.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>NetX Duo DHCPv6-serverns återanrops funktioner

*nx_dhcpv6_IP_address_declined_handler*

När DHCPv6-klienten skickar ett neka-meddelande, markerar NetX Duo DHCPv6-servern adressen som inte tillgänglig i dess IPv6-adress tabeller. För att kunna anpassa Server hanteringen av det här meddelandet tillhandahålls *nx_dhcpv6_IP_address_declined_handler* *.* Detta återanrop är dock inte implementerat för närvarande.

*nx_dhcpv6_server_option_request_handler*

När DHCPv6-klient meddelandet innehåller alternativ begär ande data, vidarebefordrar NetX Duo DHCPv6-servern varje alternativ kod för alternativ begär Ande till den här användaren, om den har definierats. Detta ger NetX Duo-servern möjlighet att låta användardefinierad motringning fylla i data. Den här funktionen är dock inte implementerad för närvarande.

## <a name="supported-dhcpv6-rfcs"></a>DHCPv6-RFC: er som stöds

NetX Duo DHCPv6 är kompatibelt med RFC3315, RFC3646 och relaterade RFC: er.