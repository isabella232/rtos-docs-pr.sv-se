---
title: Kapitel 1 – Introduktion till Azure RTOS ThreadX SMP
description: Det här kapitlet innehåller en introduktion till produkten och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9b9fb7b08691930abcf57df77fff27e619bb7a554a6235d4e234889b7c80945e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802262"
---
# <a name="chapter-1-introduction-to-azure-rtos-threadx-smp"></a>Kapitel 1: Introduktion till Azure RTOS ThreadX SMP

Azure RTOS ThreadX SMP är en högpresterande SMP-kernel i realtid som utformats särskilt för inbäddade program. Det här kapitlet innehåller en introduktion till produkten och en beskrivning av dess program och fördelar.

## <a name="threadx-smp-unique-features"></a>Unika funktioner i ThreadX SMP

ThreadX SMP ger inbäddad programvara symmetrisk flerbearbetningsteknik (SMP). ThreadX SMP-programtrådar (av varierande prioritet) som är redo att köras allokeras dynamiskt till tillgängliga processorkärnor under schemaläggningen. Detta resulterar i sann SMP-bearbetning, inklusive automatisk belastningsutjämning av programtrådkörning över alla tillgängliga processorkärnor.

Till skillnad från andra realtidskärnor är ThreadX SMP utformat för att vara flexibelt – enkel skalning bland små mikrostyrenhetsbaserade program via de som använder kraftfulla CISC-, RISC- och DSP-processorer.

ThreadX SMP är skalbart baserat på dess underliggande arkitektur. Eftersom ThreadX SMP-tjänster implementeras som ett C-bibliotek, kommer endast de tjänster som faktiskt används av programmet att tas med i körningsavbildningen. Den faktiska storleken på ThreadX SMP bestäms därför helt av programmet. För de flesta program sträcker sig instruktionsbilden för ThreadX SMP mellan 5 KByte och 20 KByte i storlek.

### <a name="picokernel-architecture"></a>picokernel™arkitektur 
I stället för att skikta kernelfunktioner ovanpå varandra som traditionella *mikrokernel-arkitekturer,* ansluts ThreadX SMP-tjänster direkt till kärnan. Detta resulterar i snabbaste möjliga kontextväxling och prestanda för tjänstsamtal. Vi kallar den här icke-layeringsdesignen *för en picokernel-arkitektur.*

### <a name="ansi-c-source-code"></a>ANSI C-källkod 
ThreadX SMP är främst skrivet i ANSI C. En liten mängd sammansättningsspråk krävs för att skräddarsy kerneln till den underliggande målprocessorn. Den här designen gör det möjligt att porta ThreadX SMP till en ny processorfamilj på mycket kort tid, vanligtvis inom några veckor!

### <a name="advanced-technology"></a>Avancerad teknik 
Här är några av de viktigaste teknikerna för ThreadX SMP:

  - Enkel *picokernel-arkitektur*
  - Automatisk belastningsutjämning
  - Exkludering av processor per tråd
  - Automatisk skalning (litet fotavtryck)
  - Deterministisk bearbetning
  - Snabba prestanda i realtid
  - Förebyggande och schemaläggning av schemaläggning
  - Flexibelt trådprioritetsstöd (32–1024)
  - Skapa objekt med dynamiskt system
  - Obegränsat antal systemobjekt
  - Optimerad avbrottshantering
  - Tröskelvärde för avbrott™
  - Prioritetsarv
  - Händelsekedja™
  - Snabba programvarutimer
  - Hantering av körtidsminne
  - Prestandaövervakning av körning
  - Analys av körningsstack
  - Inbyggd systemspårning
  - Omfattande processorsupport
  - Omfattande stöd för utvecklingsverktyg
  - Helt endiansk neutral

### <a name="not-a-black-box"></a>Inte en svart låda
De flesta distributioner av ThreadX SMP innehåller den fullständiga C-källkoden samt det processorspecifika sammansättningsspråket. Detta eliminerar de "black-box"-problem som uppstår med många kommersiella kernels. Med ThreadX SMP kan programutvecklare se exakt vad kerneln gör – det finns inga problem!

Källkoden tillåter även programspecifika ändringar. Även om det inte rekommenderas är det verkligen bra att ha möjlighet att ändra kerneln om det är absolut nödvändigt.

De här funktionerna är särskilt bekväma för utvecklare som är vana vid att arbeta med sina *egna inhouse-kernels.* De förväntar sig källkod och möjlighet att ändra kerneln. ThreadX SMP är den ultimata kärnan för sådana utvecklare.

### <a name="the-rtos-standard"></a>The RTOS Standard
På grund av sin flexibilitet, högpresterande *picokernel-arkitektur,* avancerade teknik och demonstrerad portabilitet, distribueras ThreadX SMP på fler än två miljarder enheter i dag. Detta gör i praktiken ThreadX SMP till RTOS-standarden för djupt inbäddade program.

## <a name="safety-certifications"></a>Säkerhetscertifieringar

### <a name="tv-certification"></a>TÜV-certifiering  
ThreadX SMP har certifierats av SGS-TÜV Saar för användning i säkerhetskritiska system, enligt IEC61508 och IEC-62304. Certifieringen bekräftar att ThreadX SMP kan användas i utvecklingen av säkerhetsrelaterad programvara för högsta säkerhetsintegritetsnivåer för International Electrotechnical Commission (IEC) 61508 och IEC 62304, för "funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system." SGS-TÜV Saar, som bildas genom ett gemensamt program av Tysklands SGS-Group och TÜV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad programvara för säkerhetsrelaterade system över hela världen. Den industriella säkerhetsstandarden IEC 61508, och alla standarder som härleds från den, inklusive IEC 62304, används för att garantera funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, processkontrollsystem, industriella maskiner och system för kontroll av djur.

SGS-TÜV Saar har certifierat ThreadX SMP för användning i säkerhetskritiska fordonssystem enligt ISO 26262-standarden. Dessutom är ThreadX SMP certifierat för Bilsäkerhetsintegritetsnivå (ASIL) D, som representerar den högsta nivån av ISO 26262-certifiering.

Dessutom har SGS-TÜV Saar certifierat ThreadX SMP för användning i säkerhetskritiska program, som uppfyller STANDARDEN EN 50128 upp till SW-SIL 4.

![TÜV-certifiering](media/image2.png)

IEC 61508 upp till SIL 4  
IEC 62304 upp till SW-säkerhetsklass C  
ISO 26262 ASIL D  
EN 50128 SW-SIL 4  

> [!IMPORTANT]
> Kontakta för mer information om vilka versioner av ThreadX SMP som har certifierats av TÜV eller för tillgängligheten av [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) testrapporter, certifikat och tillhörande dokumentation.

### <a name="misra-c-compliant"></a>MISRA C-kompatibel 
MISRA C är en uppsättning programmeringsriktlinjer för kritiska system som använder programmeringsspråket C. De ursprungliga riktlinjerna för MISRA C var främst avsedda för fordonstillämpningar. MEN MISRA C är nu allmänt känt som tillämpligt för alla säkerhetskritiska program. ThreadX SMP är kompatibel med alla "obligatoriska" och "obligatoriska" regler för MISRA-C:2004 och MISRA C:2012. ThreadX SMP är också kompatibelt med alla utom tre "rådgivningsregler". Se dokumentet ***ThreadX_MISRA_Compliance.pdf*** för mer information.

### <a name="ul-certification"></a>UL-certifiering 
ThreadX SMP har certifierats av UL för efterlevnad med UL 60730-1 H, CSA E607301 Både H, IEC 60730-1 H, UL 60335-1Villkoren R, IEC 60335-1 – 1 – 1998- och Ul 1998-säkerhetsstandarder för programvara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "Kontroller med hjälp av programvara" i sin 1 H, beskriver IEC 60335-1-standarden kraven för "Programmerbara elektroniska kretsar" i sin IEC 60730 Års-H och IEC 60335-1 Vis R tar upp säkerheten för MCU-maskinvara och -programvara som används i apparater, t.ex. maskiner, reglage, torktumlare, kylskåp, apparater och apparat.

![UL-certifiering](media/image3.png) 

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
> Kontakta för mer information om vilka versioner av ThreadX SMP som har certifierats av TÜV eller för tillgängligheten av [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) testrapporter, certifikat och tillhörande dokumentation.

### <a name="certification-pack"></a>Certifieringspaket

ThreadX SMP-certifieringspaketet™ är ett komplett, nyckelfärdigt, branschspecifikt, fristående paket som innehåller alla ThreadX SMP-bevis som krävs för att certifiera eller skicka threadX SMP-baserade produkter till de högsta tillförlitlighets- och allvarlighetsnivåerna som krävs för säkerhetskritiska system för flyg, sjukvård och industri. Certifieringar som stöds är DO-178B, ED-12B, DO-278, CONTAINRAR510(k), IEC-62304, IEC-60601, ISO- 14971, UL-1998, IEC-61508, CEN ALIAS EN50128, BS50128 och 49CFR236. Kontakta om sales@expresslogic.com du vill ha mer information om certifieringspaket.

## <a name="embedded-applications"></a>Inbäddade program

Inbäddade program körs på mikroprocessorer som finns i produkter som trådlösa kommunikationsenheter, bilmotorer,laserskrivare, medicinska enheter osv. En annan skillnad mellan inbäddade program är att deras programvara och maskinvara har ett särskilt syfte.

### <a name="real-time-software"></a>Realtidsprogramvara 
När tidsbegränsningar tillämpas på programmet kallas det *för realtidsprogramvaran.* I princip kallas programvara som måste utföra bearbetningen inom en exakt tidsperiod *realtidsprogramvara.* Inbäddade program är nästan alltid i realtid på grund av deras interaktion med externa händelser.

### <a name="multitasking"></a>Multitasking  
Som tidigare nämnts har inbäddade program ett dedikerat syfte. För att uppfylla det här syftet måste programvaran utföra en mängd olika *uppgifter.* En uppgift är en halvoberoende del av programmet som utför en viss uppgift. Det är också så att vissa uppgifter är viktigare än andra. En av de största problemen i ett inbäddat program är allokeringen av processorn mellan de olika programuppgifterna. Den här allokeringen av bearbetning mellan konkurrerande uppgifter är det primära syftet med ThreadX SMP.

### <a name="tasks-vs-threads"></a>Uppgifter kontra trådar 
En annan skillnad om uppgifter måste göras. Termen uppgift används på flera olika sätt. Det innebär ibland ett separat inläsningsbart program. I andra fall kan det referera till ett internt programsegment.

I en bra beskrivning av operativsystemet finns det två termer som mer eller mindre ersätter användningen av uppgiften: *process* och *tråd*. En *process* är ett helt oberoende program som  har ett eget adressutrymme, medan en tråd är ett halvoberoende programsegment som körs i en process. Trådar delar samma processadressutrymme. Arbetet med trådhantering är minimalt.

De flesta inbäddade program har inte råd med omkostnaderna (både minne och prestanda) som är associerade med ett fullständigt processorienterat operativsystem. Dessutom har inte mindre mikroprocessorer maskinvaruarkitektur för att stödja ett verkligt processorienterat operativsystem. Av dessa skäl implementerar ThreadX SMP en trådmodell, vilket är både mycket effektivt och praktiskt för de flesta inbäddade realtidsprogram.

För att undvika förvirring använder ThreadX SMP inte termen *task*. I stället används den mer beskrivande och *beskrivande* namntråden.

## <a name="threadx-smp-benefits"></a>ThreadX SMP-fördelar

Att använda ThreadX SMP ger många fördelar med inbäddade program. Den främsta fördelen ligger naturligtvis i hur inbäddade programtrådar allokeras bearbetningstid.

### <a name="automatic-load-balancing"></a>Automatisk belastningsutjämning  
ThreadX SMP ger automatisk belastningsutjämning (trådkörning över tillgängliga kärnor), vilket gör det så enkelt att använda processorer med flera kärnor som möjligt. 

### <a name="improved-responsiveness"></a>Förbättrad svarstid  
Före realtidskärnor som ThreadX SMP allokerade de flesta inbäddade program bearbetningstid med en enkel kontrollloop, vanligtvis inifrån *C-huvudfunktionen.* Den här metoden används fortfarande i mycket små eller enkla program. I stora eller komplexa program är det dock inte praktiskt eftersom svarstiden för en händelse är en funktion av den sämsta bearbetningstiden för en genom kontrollloopen.

Det är ännu värre att tidsegenskaperna för programmet ändras när ändringar görs i kontrollloopen. Detta gör programmet i sig instabilt och svårt att underhålla och förbättra.

ThreadX SMP ger snabba och deterministiska svarstider för viktiga externa händelser. ThreadX SMP åstadkommer detta genom sin förebyggande, prioritetsbaserade schemaläggningsalgoritm, vilket gör att en tråd med högre prioritet kan avinstallera en tråd med lägre prioritet. Därför närmar sig svarstiden i värsta fall den tid som krävs för att utföra en kontextväxel. Detta är inte bara deterministiskt, utan även mycket snabbt.

### <a name="software-maintenance"></a>Programvaruunderhåll  
ThreadX SMP-kerneln gör det möjligt för programutvecklare att koncentrera sig på specifika krav för sina programtrådar utan att behöva bekymra sig om att ändra tidpunkten för andra delar av programmet. Den här funktionen gör det också mycket enklare att reparera eller förbättra ett program som använder ThreadX SMP.

### <a name="increased-throughput"></a>Ökat dataflöde  
En möjlig lösning på problemet med svarstiden för kontrollloopen är att lägga till mer avsökning. Detta förbättrar svarstiderna, men det garanterar fortfarande inte en konstant svarstid för värsta fall och gör ingenting för att förbättra framtida ändringar av programmet. Dessutom utför processorn nu ännu mer onödig bearbetning på grund av den extra avsökning. All denna onödiga bearbetning minskar systemets totala dataflöde.

En intressant punkt när det gäller omkostnader är att många utvecklare förutsätter att flertrådade miljöer som ThreadX SMP ökar omkostnaderna och har en negativ inverkan på det totala systemets dataflöde. Men i vissa fall minskar multitrådning faktiskt omkostnaderna genom att eliminera all redundant avsökning som sker i kontrollloopmiljöer. Omkostnaderna för flertrådade kernels är vanligtvis en funktion av den tid som krävs för kontextväxling. Om kontextväxelns tid är mindre än avsökningsprocessen tillhandahåller ThreadX SMP en lösning med potentialen mindre omkostnader och större dataflöde. Detta gör ThreadX SMP till ett uppenbart val för program som har någon grad av komplexitet eller storlek.

### <a name="processor-isolation"></a>Processorisolering  
ThreadX SMP ger ett robust processoroberoende gränssnitt mellan programmet och den underliggande processorn. På så sätt kan utvecklare koncentrera sig på programmet i stället för att ägna mycket tid åt att lära sig maskinvaruinformation. 

### <a name="dividing-the-application"></a>Dividera programmet  
I kontrollloopbaserade program måste varje utvecklare ha en nära kunskap om hela programmets körningsbeteende och krav. Det beror på att processorallokeringslogiken sprids i hela programmet. När ett program ökar i storlek eller komplexitet blir det omöjligt för alla utvecklare att komma ihåg de exakta bearbetningskraven för hela programmet.

ThreadX SMP frigör varje utvecklare från de problem som är associerade med processorallokering och gör att de kan koncentrera sig på sin specifika del av det inbäddade programmet. Dessutom tvingar ThreadX SMP programmet att delas upp i tydligt definierade trådar. Den här uppdelningen av programmet i trådar gör utvecklingen mycket enklare.

### <a name="ease-of-use"></a>Användarvänlighet  
ThreadX SMP är utformat med programutvecklaren i åtanke. ThreadX SMP-arkitekturen och gränssnittet för tjänstanrop är utformade för att vara lätta att förstå. Därför kan ThreadX SMP-utvecklare snabbt använda sina avancerade funktioner.  

### <a name="improve-time-to-market"></a>Förbättra tiden till marknad  
Alla fördelar med ThreadX SMP påskyndar programutvecklingsprocessen. ThreadX SMP tar hand om de flesta processorproblem och de vanligaste säkerhetscertifieringarna, vilket tar bort detta arbete från utvecklingsschemat. Allt detta resulterar i en snabbare tid till marknad!  

### <a name="protecting-the-software-investment"></a>Skydda programvaruinvesteringen  
På grund av sin arkitektur portas ThreadX SMP enkelt till nya processor- och/eller utvecklingsverktygsmiljöer. Detta tillsammans med det faktum att ThreadX SMP isolerar program från information om de underliggande processorerna gör ThreadX SMP-program mycket portabla. Därför garanteras programmets migreringsväg och den ursprungliga utvecklingsinvesteringen skyddas.