---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider NetX och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48be6a7ecddc53b36b3cc1a9ecfb50a11e285881
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826892"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX

Azure återställnings tider NetX är en real tids implementering av TCP/IP-standarden som är utformad exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX och en beskrivning av dess program och fördelar.

## <a name="netx-unique-features"></a>NetX-unika funktioner

Till skillnad från andra TCP/IP-implementeringar är NetX utformat för att vara flexibelt, vilket enkelt kan skalas från små mikrostyrenhet program till dem som använder kraftfulla RISC-och DSP-processorer. Detta är i skarpt kontrast i den offentliga domänen eller andra kommersiella implementeringar som ursprungligen är avsedda för arbets Stations miljöer, men som sedan är inkapslade i inbäddade modeller.

### <a name="piconettrade-architecture"></a>Piconet- &trade; arkitektur

Den förstklassiga skalbarheten och prestandan hos NetX är *piconet*, en program arkitektur särskilt utformad för inbäddade system. Piconet-arkitekturen maximerar skalbarheten genom att implementera NetX-tjänster som ett C-bibliotek. På så sätt hämtas bara de tjänster som faktiskt används av programmet till den slutliga körnings avbildningen. Därför bestäms den faktiska storleken för NetX helt av programmet. För de flesta program är avbildnings storleks kraven för NetX intervall mellan 5 och 30 kB stora.

NetX uppnår överlägsen nätverks prestanda genom att skikta intern komponent funktion anropar endast när det är absolut nödvändigt. Dessutom görs mycket av NetX-bearbetning direkt i rad, vilket ger enastående prestanda för delar över arbets stationens nätverks program vara som ofta används i inbäddade modeller tidigare.</th>

### <a name="zero-copy-implementation"></a>Ingen kopierings implementering

NetX tillhandahåller en paket-baserad, *noll kopierings* implementering av TCP/IP. Noll kopiering innebär att data i programmets pakettyp aldrig kopieras i NetX. Detta förbättrar prestandan och frigör värdefulla processor cyklar till programmet, vilket är mycket viktigt i inbäddade program.

### <a name="udp-fast-pathtrade-technology"></a>Snabb väg teknik för UDP &trade;

Med en *snabb Sök vägs teknik för UDP* ger netx snabbast möjlig UDP-bearbetning. På sändnings sidan ingår UDP-bearbetningen, inklusive den valfria UDP-kontrollsumman, som är helt i ***nx_udp_socket_send*** tjänsten. Inga ytterligare funktions anrop görs förrän paketet är klart att skickas via den interna NetX IP Send-rutinen. Den här rutinen är också platt (d.v.s. dess funktions anrop är minimalt) så att paketet snabbt skickas till programmets nätverks driv rutin. När UDP-paketet tas emot placerar NetX-indata-bearbetningen paketet direkt på lämplig UDP-Sockets mottagande kö eller ger den första tråden inaktive rad i väntan på ett mottagnings paket från UDP-socketens mottagande kö. Inga ytterligare kontext växlar för ThreadX krävs.

### <a name="ansi-c-source-code"></a>ANSI C-källkod

NetX skrivs helt i ANSI C och är direkt portabel till praktiskt taget vilken processor arkitektur som helst som har stöd för ANSI C-kompilator och ThreadX.

### <a name="not-a-black-box"></a>Inte en svart ruta

De flesta distributioner av NetX innehåller den fullständiga C-källkoden. Detta eliminerar "svarta box"-problem som uppstår i många nätverks stackar. Genom att använda NetX kan program utvecklare se exakt vad nätverks stacken gör – det finns inga Mysteries!
  
Med käll koden kan du också göra programspecifika ändringar. Även om det inte rekommenderas, är det verkligen fördelaktigt att ha möjlighet att ändra nätverks stacken om det behövs.  

Dessa funktioner är särskilt praktiska för utvecklare som är vana vid att arbeta med interna eller offentliga nätverks stackar. De förväntar sig ha källkod och möjlighet att ändra den. NetX är den ultimata nätverks program varan för sådana utvecklare.

### <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible socket

För äldre program tillhandahåller NetX ett BSD-kompatibelt socket-gränssnitt som gör anrop till NetX-API: t med höga prestanda under. Detta hjälper till att migrera befintlig kod för nätverks program till NetX.

## <a name="rfcs-supported-by-netx"></a>RFC: er som stöds av NetX

NetX-stöd för RFC: er som beskriver grundläggande nätverks protokoll omfattar men är inte begränsat till följande nätverks protokoll. NetX följer alla allmänna rekommendationer och grundläggande krav inom begränsningarna i ett operativ system i real tid med liten minnes storlek och effektiv körning.

| RFC      | Beskrivning                                            |
|----------|--------------------------------------------------------|
| RFC 1112 | Värd tillägg för IP-multicasting (IGMPv1)           |
| RFC 1122 | Krav för Internet värdar – kommunikations lager |
| RFC 2236 | Internet Group Management Protocol, version 2          |
| RFC 768  | UDP (User Datagram Protocol)                           |
| RFC 791  | Internet Protocol (IP)                                 |
| RFC 792  | Internet Control Message Protocol (ICMP)               |
| RFC 793  | Transmission Control Protocol (TCP)                    |
| RFC 826  | ARP (Ethernet Address Resolution Protocol)             |
| RFC 903  | RARP (reversed Address Resolution Protocol)             |
|          |                                                        |

## <a name="embedded-network-applications"></a>Inbäddade nätverks program

Inbäddade nätverks program är program som behöver nätverks åtkomst och som körs på mikroprocessorer som är dolda i produkter som mobil telefoner, kommunikations utrustning, fordons motorer, laser skrivare, medicinska enheter och så vidare. Sådana program har nästan alltid vissa minnes-och prestanda begränsningar. En annan åtskillnad mellan inbäddade nätverks program är att deras program vara och maskin vara har ett dedikerat syfte.

### <a name="real-time-network-software"></a>Nätverks program vara i real tid  

I princip kallas att nätverks program vara som måste utföra bearbetningen inom en exakt tids period kallas för *nätverks* program vara i *real tid* och när tids begränsningar införs på nätverks program klassificeras de som program i real tid. Inbäddade nätverks program är nästan alltid i real tid på grund av deras inbyggda interaktion med den externa världen.

## <a name="netx-benefits"></a>NetX-förmåner

De främsta fördelarna med att använda NetX för inbäddade program är snabb Internet anslutning och mycket små minnes krav. NetX är också helt integrerat med högpresterande, ThreadX real tids operativ system.

### <a name="improved-responsiveness"></a>Förbättrad svars tid  

NetX-protokollstacken med höga prestanda gör att inbäddade nätverks program kan svara snabbare än någonsin tidigare. Detta är särskilt viktigt för inbäddade program som antingen har en stor mängd nätverks trafik eller stränga bearbetnings krav i ett enda paket.

### <a name="software-maintenance"></a>Program varu underhåll

Med NetX kan utvecklare enkelt partitionera nätverks aspekterna av sina inbäddade program. Den här partitionerings processen gör hela utvecklings processen enkel och förbättrar det framtida program varu underhållet.

### <a name="increased-throughput"></a>Ökat data flöde

NetX tillhandahåller nätverk med högsta prestanda, vilket uppnås genom minimal belastning på paket bearbetning. Detta möjliggör även ökat data flöde.

### <a name="processor-isolation"></a>Processor isolering

NetX tillhandahåller ett robust, processor oberoende gränssnitt mellan programmet och den underliggande maskin varan för processorn och nätverket. Detta gör det möjligt för utvecklare att koncentrera sig på nätverks aspekter i programmet i stället för att ägna extra tid åt att hantera maskin varu problem direkt påverkar nätverk.

### <a name="ease-of-use"></a>Lätt att använda

NetX är utformad med program utvecklaren i åtanke. NetX-arkitekturen och tjänst anrops gränssnittet är lätta att förstå. Därför kan NetX-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknaden

De kraftfulla funktionerna i NetX påskyndar program utvecklings processen. NetX sammanfattar de flesta problem med processor och nätverks maskin vara, och tar därmed bort dessa problem från en majoritet av programnätverkets specifika områden. Detta, tillsammans med funktionen för enkel användning och avancerad funktion, resulterar i en snabbare tid till marknaden.

### <a name="protecting-the-software-investment"></a>Skydda program investeringen

NetX skrivs exklusivt i ANSI C och är helt integrerad med ThreadX real tids operativ system. Det innebär att NetX-program är direkt bärbara till alla ThreadX-processorer som stöds. Dessutom kan en helt ny processor arkitektur stödjas med ThreadX på bara några veckor. Det innebär att du kan använda NetX för att säkerställa programmets migrations Sök väg och skyddar den ursprungliga utvecklings investeringen.
