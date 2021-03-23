---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider NetX Duo och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 91dfd0e62cb565f677faa7d52fe22abc1f0e19a1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826223"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo

Azure återställnings tider NetX Duo är en real tids implementering av TCP/IP-standarder som utformats exklusivt för inbäddade Azure återställnings tider-ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX Duo och en beskrivning av dess program och fördelar. 

## <a name="netx-duo-unique-features"></a>NetX Duo-unika funktioner

Till skillnad från andra TCP/IP-implementeringar är NetX Duo utformat för att vara flexibelt, vilket enkelt kan skalas från små mikrokontrollantbaserade program till dem som använder kraftfulla RISC-och DSP-processorer. Detta är i skarpt kontrast i den offentliga domänen eller andra kommersiella implementeringar som ursprungligen är avsedda för arbets Stations miljöer, men som sedan är inkapslade i inbäddade modeller.

### <a name="piconettrade-architecture"></a>Piconet- &trade; arkitektur

Den förstklassiga skalbarheten och prestandan hos NetX Duo är <em>piconet</em>, en program arkitektur särskilt utformad för inbäddade system. Piconet-arkitekturen maximerar skalbarheten genom att implementera NetX Duo-tjänster som ett C-bibliotek. På så sätt kommer endast de tjänster som används av programmet att tas i den slutliga körnings avbildningen. Den faktiska storleken på NetX Duo bestäms därför av programmet. För de flesta program är instruktions avbildnings kraven för NetX Duo intervall mellan 5 KByte och 30 KByte i storlek. Med IPv6 och ICMPv6 aktiverat för IPv6-adress konfiguration och Neighbor Discovery-protokoll, NetX Duo-intervall i storlek från 30 kB till 45 kByte.

NetX Duo uppnår överlägsen nätverks prestanda genom att skikta intern komponent funktion anropar bara när det är nödvändigt. Dessutom görs mycket av NetX Duo-bearbetningen direkt i rad, vilket ger enastående prestanda för delar över arbets stationens nätverks program vara som används i inbäddade modeller tidigare.

### <a name="zero-copy-implementation"></a>Ingen kopierings implementering

NetX Duo tillhandahåller en paket-baserad, noll kopierings implementering av TCP/IP. Noll kopiering innebär att data i programmets pakettyp aldrig kopieras i NetX Duo. Detta förbättrar prestandan och frigör värdefulla processor cyklar till programmet, vilket är viktigt i inbäddade program.

### <a name="udp-fast-pathtrade-technology"></a>Snabb väg teknik för UDP &trade;

Med netx Duo i <em>UDP</em>får du den snabbaste möjliga UDP-bearbetningen. På sändnings sidan är UDP-bearbetningen, inklusive den valfria UDP-kontrollsumman, som finns i den <em>**nx_udp_socket_send**</em> tjänsten. Inga ytterligare funktions anrop görs förrän paketet är klart att skickas via den interna NetX Duo IP Send-rutinen. Den här rutinen är också platt (det vill säga dess funktions anrop är minimalt) så att paketet snabbt skickas till programmets nätverks driv rutin. När UDP-paketet tas emot placerar NetX Duo-indata-bearbetningen paketet direkt på lämplig UDP-Sockets mottagande kö eller ger den första tråden inaktive rad i väntan på ett mottagnings paket från UDP-socketens mottagande kö. Inga ytterligare kontext växlar för ThreadX krävs.

### <a name="ansi-c-source-cod"></a>ANSI C-käll post COD

NetX Duo skrivs helt och hållet i ANSI C och går direkt till praktiskt taget vilken processor arkitektur som helst som har stöd för ANSI C-kompilator och ThreadX. 

### <a name="not-a-black-box"></a>Inte en svart ruta

De flesta distributioner av NetX Duo innehåller den fullständiga C-källkoden. Detta eliminerar "svarta box"-problem som uppstår i många nätverks stackar. Genom att använda NetX Duo kan programutvecklare se exakt vad nätverks stacken gör – det finns inga Mysteries!

Med käll koden kan du också göra programspecifika ändringar. Även om det inte rekommenderas, är det fördelaktigt att ha möjlighet att ändra nätverks stacken om det behövs.

Dessa funktioner är särskilt praktiska för utvecklare som är vana vid att arbeta med interna eller offentliga nätverks stackar. De förväntar sig ha källkod och möjlighet att ändra den. NetX Duo är den ultimata nätverks program varan för sådana utvecklare.

### <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible socket

För äldre program tillhandahåller NetX Duo också ett BSD-kompatibelt socket-gränssnitt som gör anrop till NetX Duo-API: et med höga prestanda under. Detta hjälper till att migrera befintlig kod för nätverks program till NetX Duo.

## <a name="rfcs-supported-by-netx-duo"></a>RFC: er som stöds av NetX Duo

NetX Duo-stöd för RFC: er som beskriver grundläggande nätverks protokoll omfattar men är inte begränsat till följande nätverks protokoll. NetX Duo följer alla allmänna rekommendationer och grundläggande krav inom begränsningar i ett operativ system i real tid med liten minnes storlek och effektiv körning.

| **RFC**  | **Beskrivning**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | Värd tillägg för IP-multicasting (IGMPv1)           |
|RFC 1122 | Krav för Internet värdar – kommunikations lager |
|RFC 2236 | Internet Group Management Protocol, version 2          |
|RFC 768  | UDP (User Datagram Protocol)                           |
|RFC 791  | Internet Protocol (IP)                                 |
|RFC 792  | Internet Control Message Protocol (ICMP)               |
|RFC 793  | Transmission Control Protocol (TCP)                    |
|RFC 826  | ARP (Ethernet Address Resolution Protocol) |
|RFC 903  | RARP (reversed Address Resolution Protocol) |
|RFC 5681 | TCP-överbelastnings kontroll                     |

Nedan visas IPv6-relaterade RFC: er som stöds av NetX Duo.

|**RFC** |**Beskrivning**|
-------- | ------------------------------------------ |
|RFC 1981 |Sökvägs-MTU-identifiering för Internet Protocol V6 (IPv6)|
|RFC 2460 | Specifikation för Internet Protocol V6 (IPv6)|
|RFC 2464 |Överföring av IPv6-paket över Ethernet-nätverk|
|RFC 4291 |Arkitektur för Internet Protocol V6-adress (IPv6)|
|RFC 4443 |Internet Control Message Protocol (ICMPv6) för Internet Protocol V6-specifikation (IPv6)|
|RFC 4861 |Identifiering av grannar för IP V6|
|RFC 4862 |Automatisk konfiguration av IPv6-tillstånds lös adress|

## <a name="embedded-network-applications"></a>Inbäddade nätverks program

Inbäddade nätverks program är program som behöver nätverks åtkomst och som körs på mikroprocessorer som är dolda i produkter som mobil telefoner, kommunikations utrustning, fordons motorer, laser skrivare, medicinska enheter och så vidare. Sådana program har nästan alltid vissa minnes-och prestanda begränsningar. En annan åtskillnad mellan inbäddade nätverks program är att deras program vara och maskin vara har ett dedikerat syfte.

Nätverks program vara som måste utföra bearbetningen inom en exakt tids period kallas för *nätverks* program vara i *real tid* och när tids begränsningar införs på nätverks program klassificeras de som program i real tid. Inbäddade nätverks program är nästan alltid real tid på grund av deras inbyggda interaktion med den externa världen.

## <a name="netx-duo-benefits"></a>NetX Duo-förmåner

De främsta fördelarna med att använda NetX Duo för inbäddade program är snabb Internet anslutning och små minnes krav. NetX Duo är också integrerat med hög prestanda, multitasking ThreadX real tids operativ system.

### <a name="improved-responsiveness"></a>Förbättrad svars tid

Med NetX Duo-protokollstacken med höga prestanda kan inbäddade nätverks program svara snabbare än någonsin tidigare. Detta är särskilt viktigt för inbäddade program som antingen har en stor mängd nätverks trafik eller stränga bearbetnings krav i ett enda paket.

### <a name="software-maintenance"></a>Program varu underhåll

Med NetX Duo kan utvecklare enkelt partitionera nätverks aspekterna av sina inbäddade program. Den här partitionerings processen gör hela utvecklings processen enkel och förbättrar det framtida program varu underhållet.

### <a name="increased-throughput"></a>Ökat data flöde

NetX Duo ger högsta möjliga prestanda för nätverk som uppnås genom minimal belastning på paket bearbetning. Detta möjliggör även ökat data flöde.

### <a name="processor-isolation"></a>Processor isolering

NetX Duo tillhandahåller ett robust, processor oberoende gränssnitt mellan programmet och den underliggande maskin varan för processorn och nätverket. Detta gör det möjligt för utvecklare att koncentrera sig på nätverks aspekter i programmet i stället för att ägna extra tid åt att hantera maskin varu problem direkt påverkar nätverk.

### <a name="ease-of-use"></a>Lätt att använda

NetX Duo är utformad med programutvecklaren i åtanke. NetX Duo-arkitekturen och tjänst anrops gränssnittet är lätta att förstå. Därför kan NetX Duo-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknaden

De kraftfulla funktionerna i NetX Duo påskyndar program utvecklings processen. NetX Duo sammanfattar de flesta problem med processor och nätverks maskin vara, och tar därmed bort dessa problem från en majoritet av programnätverkets specifika områden. Detta, tillsammans med funktionen för enkel användning och avancerad funktion, resulterar i en snabbare tid till marknaden!

### <a name="protecting-the-software-investment"></a>Skydda program investeringen

NetX Duo är skrivet exklusivt i ANSI C och är helt integrerat med ThreadX Real-Time-operativsystem. Det innebär att NetX Duo-program är direkt bärbara till alla ThreadX-processorer som stöds. En ny processor arkitektur kan ännu bättre användas med ThreadX på några veckor. Det innebär att användning av NetX Duo säkerställer programmets migrations Sök väg och skyddar den ursprungliga utvecklings investeringen.

## <a name="ipv6-ready-logo-certification"></a>Certifiering av IPv6-klar logo typ

NetX Duo "IPv6 Ready"-certifiering erhölls via "protokollet" IPv6 Core Protocol (fas 2) self test "tillgängligt från den färdiga IPv6-organisationen. Se följande IPv6-Ready projekt webbplatser för mer information om test plattformen och test fall:[**https://www.ipv6ready.org/**](https://www.ipv6ready.org/)

Fasen 2 IPv6 Core Protocol self test Suite verifierar att en IPv6-stack iakttar kraven i följande RFC: er med omfattande tester:  
Avsnitt 1: RFC 2460  
Avsnitt 2: RFC 4861  
Avsnitt 3: RFC 4862  
Avsnitt 4: RFC 1981  
Avsnitt 5: RFC 4443  

## <a name="ixanvl-test"></a>IxANVL-test

NetX Duo testas med IxANVL från IXIA. IxANVL är bransch standard för automatisk verifiering av nätverk och protokoll. Mer information om IxANVL finns på: [**https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)

I synnerhet är följande NetX Duo-moduler testade med IxANVL:

|**Modul** | **Standard** |
| --------- | ------------ |
|IP-adress | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Core| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Advanced| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Performance| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>Säkerhets certifieringar

### <a name="tv-certification"></a>TÜV-certifiering  

NetX Duo har certifierats av SGS-TÜV Saar för användning i säkerhets kritiska system, enligt IEC61508 och IEC-62304. Certifieringen bekräftar att NetX Duo kan användas i utvecklingen av säkerhetsrelaterad program vara för den högsta säkerhets integritets nivån för International Electrotechnical Commission (IEC) 61508 och IEC 62304 för "den funktionella säkerheten i elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system." SGS – TÜV Saar, som bildas genom ett gemensamt företag i Tyskland SGSGroup och TÜV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC 62304, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner och järnvägs kontroll system. 

SGS – TÜV Saar har certifierat NetX Duo som ska användas i säkerhets kritiska motor system enligt ISO 26262-standarden. Dessutom är NetX Duo certifierat för att ASIL () D, som motsvarar den högsta nivån av ISO 26262-certifiering. 

Dessutom har SGS-TÜV Saar certifierat NetX Duo som ska användas i verksamhets kritiska järnvägs program, vilket motsvarar en 50128-standard upp till SW-SIL 4.

![Diagram över SGS-TÜV Saar-certifierings logo typ.](./media/user-guide/sgs-tuv-saar-logo.png)

IEC 61508 upp till SIL 4  
IEC 62304 upp till SW säkerhets klass C ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> *Kontakta Microsoft om du vill ha mer information om vilka versioner av NetX Duo som har certifierats av TÜV eller om du vill ha till gång till test rapporter, certifikat och tillhör ande dokumentation.*

### <a name="ul-certification"></a>UL-certifiering

NetX Duo har certifierats av UL för att följa UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "kontroller som använder program vara" i bilaga H, innehåller IEC 60335-1-standarden kraven för "programmerbara elektroniska kretsar" i bilaga R. IEC 60730 bilaga H och IEC 60335-1 Bilaga R MCU av maskin vara och program vara som används i anordningar som tvätt maskiner, disk maskiner, Dryers, kyl skåp, frysar och ugnar.

![Diagram över UL-certifierings logo typ.](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]  
> *Kontakta Microsoft om du vill ha mer information om vilka versioner av NetX Duo som har certifierats av UL eller för att få till gång till test rapporter, certifikat och tillhör ande dokumentation.*