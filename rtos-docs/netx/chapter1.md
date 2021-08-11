---
title: Kapitel 1 – Introduktion till Azure RTOS NetX
description: Det här kapitlet innehåller en introduktion till Azure RTOS NetX och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 207aaec18f020e8cc3534a9ef55ed338df487fd95b22b5021f691ea63ba62b8b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782870"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx"></a>Kapitel 1 – Introduktion till Azure RTOS NetX

Azure RTOS NetX är en högpresterande realtidsimplementering av TCP/IP-standarderna som utformats exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX och en beskrivning av dess program och fördelar.

## <a name="netx-unique-features"></a>Unika NetX-funktioner

Till skillnad från andra TCP/IP-implementeringar är NetX utformat för att vara flexibelt – enkelt att skala från små mikrostyrprogram till de som använder kraftfulla RISC- och DSP-processorer. Detta står i stark kontrast till den offentliga domänen eller andra kommersiella implementeringar som ursprungligen var avsedda för arbetsstationsmiljöer men som sedan samlades in i inbäddade designer.

### <a name="piconettrade-architecture"></a>Piconet-arkitektur &trade;

Bakom den överordnade skalbarheten och prestandan i NetX finns *Piconet*, en programvaruarkitektur som är särskilt utformad för inbäddade system. Piconet-arkitekturen maximerar skalbarheten genom att implementera NetX-tjänster som ett C-bibliotek. På så sätt tas endast de tjänster som faktiskt används av programmet in i den slutliga körningsavbildningen. Den faktiska storleken på NetX bestäms därför helt av programmet. För de flesta program är kraven på avbildningsstorlek för NetX mellan 5 KByte och 30 KByte stora.

NetX uppnår överlägsen nätverksprestanda genom att skikta interna komponentfunktioner som bara anropar när det är absolut nödvändigt. Dessutom görs mycket av NetX-bearbetningen direkt in-line, vilket ger utestående prestandafördelar jämfört med nätverksprogramvaran för arbetsstationer som ofta användes i inbäddade designer tidigare.</th>

### <a name="zero-copy-implementation"></a>Nollkopieringsimplementering

NetX tillhandahåller en paketbaserad implementering *utan kopia* av TCP/IP. Nollkopiering innebär att data i programmets paketbuffert aldrig kopieras i NetX. Detta förbättrar prestanda avsevärt och frigör värdefulla processorcykler till programmet, vilket är mycket viktigt i inbäddade program.

### <a name="udp-fast-pathtrade-technology"></a>UDP Fast &trade; Path-teknik

Med *UDP Fast Path Technology* ger NetX den snabbaste möjliga UDP-bearbetningen. På sändningssidan finns UDP-bearbetning , inklusive den valfria UDP-kontrollsumman, helt inom ***nx_udp_socket_send tjänsten.*** Inga ytterligare funktionsanrop görs förrän paketet är redo att skickas via den interna NETX IP-sändrutinen. Den här rutinen är också plan (dvs. dess funktionsanropskapsling är minimal) så att paketet snabbt skickas till programmets nätverksdrivrutin. När UDP-paketet tas emot placerar NetX-paket-mottagningsbearbetningen paketet direkt på lämplig UDP-sockets mottagningskö eller ger det till den första tråden som pausas i väntan på ett mottagningspaket från UDP-socketens mottagningskö. Inga ytterligare ThreadX-kontextväxlar krävs.

### <a name="ansi-c-source-code"></a>ANSI C-källkod

NetX är helt skrivet i ANSI C och är portabel direkt till praktiskt taget alla processorarkitekturer som har ansi C-kompilator och ThreadX-stöd.

### <a name="not-a-black-box"></a>Inte en svart låda

De flesta distributioner av NetX innehåller den fullständiga C-källkoden. Detta eliminerar de "black-box"-problem som uppstår med många kommersiella nätverksstackar. Med hjälp av NetX kan programutvecklare se exakt vad nätverksstacken gör – det finns inga problem!
  
Källkoden möjliggör även programspecifika ändringar. Även om det inte rekommenderas är det verkligen fördelaktigt att ha möjlighet att ändra nätverksstacken om det behövs.  

Dessa funktioner är särskilt bekväma för utvecklare som är vana vid att arbeta med lokala eller offentliga domännätverksstackar. De förväntar sig att ha källkod och möjlighet att ändra den. NetX är den ultimata nätverksprogramvaran för sådana utvecklare.

### <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible Socket

För äldre program tillhandahåller NetX ett BSD-kompatibelt socketgränssnitt som gör anrop till högpresterande NetX-API under. Detta hjälper till att migrera befintlig nätverksprogramkod till NetX.

## <a name="rfcs-supported-by-netx"></a>RFC:er som stöds av NetX

NetX-stöd för RFC:er som beskriver grundläggande nätverksprotokoll omfattar men är inte begränsat till följande nätverksprotokoll. NetX följer alla allmänna rekommendationer och grundläggande krav inom begränsningarna i ett realtidsoperativsystemet med litet minnesfotavtryck och effektiv körning.

| RFC      | Description                                            |
|----------|--------------------------------------------------------|
| RFC 1112 | Värdtillägg för IP Multicasting (IGMPv1)           |
| RFC 1122 | Krav för Internetvärdar – kommunikationslager |
| RFC 2236 | Internet Group Management Protocol, version 2          |
| RFC 768  | UDP (User Datagram Protocol)                           |
| RFC 791  | Internet Protocol (IP)                                 |
| RFC 792  | Internet Control Message Protocol (ICMP)               |
| RFC 793  | Transmission Control Protocol (TCP)                    |
| RFC 826  | Ethernet Address Resolution Protocol (ARP)             |
| RFC 903  | Reverse Address Resolution Protocol (RARP)             |
|          |                                                        |

## <a name="embedded-network-applications"></a>Inbäddade nätverksprogram

Inbäddade nätverksprogram är program som behöver nätverksåtkomst och körs på mikroprocessorer som är dolda i produkter som mobiltelefoner, kommunikationsutrustning, bilmotorer, skrivare för bärbara datorer, medicinska enheter och så vidare. Sådana program har nästan alltid vissa minnes- och prestandabegränsningar. En annan skillnad mellan inbäddade nätverksprogram är att deras programvara och maskinvara har ett särskilt syfte.

### <a name="real-time-network-software"></a>Realtidsnätverksprogramvara  

I princip kallas nätverksprogram som måste utföra bearbetningen   inom en exakt tidsperiod nätverksprogramvara i realtid, och när tidsbegränsningar tillämpas på nätverksprogram klassificeras de som realtidsprogram. Inbäddade nätverksprogram är nästan alltid realtidsbaserade på grund av deras inbyggda interaktion med den externa världen.

## <a name="netx-benefits"></a>NetX-förmåner

De främsta fördelarna med att använda NetX för inbäddade program är snabb Internetanslutning och mycket små minneskrav. NetX är också helt integrerat med det högpresterande ThreadX-realtidsoperativsystemet ThreadX med flera uppgifter.

### <a name="improved-responsiveness"></a>Förbättrad svarstid  

NetX-protokollstacken med höga prestanda gör att inbäddade nätverksprogram kan svara snabbare än någonsin tidigare. Detta är särskilt viktigt för inbäddade program som antingen har en betydande mängd nätverkstrafik eller stränga bearbetningskrav på ett enda paket.

### <a name="software-maintenance"></a>Programvaruunderhåll

Med NetX kan utvecklare enkelt partitionera nätverksaspekterna i det inbäddade programmet. Den här partitionering gör hela utvecklingsprocessen enkel och förbättrar avsevärt framtida programvaruunderhåll.

### <a name="increased-throughput"></a>Ökat dataflöde

NetX ger tillgång till nätverk med högsta möjliga prestanda, vilket uppnås med minimala omkostnader för paketbearbetning. Detta möjliggör också ökat dataflöde.

### <a name="processor-isolation"></a>Processorisolering

NetX ger ett robust, processoroberoende gränssnitt mellan programmet och den underliggande processor- och nätverksmaskinvaran. På så sätt kan utvecklare koncentrera sig på nätverksaspekterna i programmet i stället för att ägna extra tid åt att hantera maskinvaruproblem som direkt påverkar nätverket.

### <a name="ease-of-use"></a>Användarvänlighet

NetX är utformat med programutvecklaren i åtanke. NetX-arkitekturen och gränssnittet för tjänstanrop är lätta att förstå. Därför kan NetX-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknad

De kraftfulla funktionerna i NetX påskyndar programutvecklingsprocessen. NetX abstraherar de flesta problem med processor- och nätverksmaskinvara, vilket tar bort dessa problem från de flesta programnätverksspecifika områden. Detta, tillsammans med den lättanvända och avancerade funktionsuppsättningen, resulterar i en snabbare tid till marknaden.

### <a name="protecting-the-software-investment"></a>Skydda programvaruinvesteringen

NetX är endast skrivet i ANSI C och är helt integrerat med ThreadX-operativsystemet i realtid. Det innebär att NetX-program är direkt portabla till alla ThreadX-processorer som stöds. Ännu bättre är att en helt ny processorarkitektur kan stödjas med ThreadX på bara några veckor. Därför säkerställer användningen av NetX programmets migreringsväg och skyddar den ursprungliga utvecklingsinvesteringen.
