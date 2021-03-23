---
title: Kapitel 1 – Introduktion till Azure återställnings tider ThreadX SMP
description: Det här kapitlet innehåller en introduktion till produkten och en beskrivning av dess program och förmåner.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 67bdb9076272fa3671ec9321baec609b291c04b8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826571"
---
# <a name="chapter-1-introduction-to-azure-rtos-threadx-smp"></a>Kapitel 1: Introduktion till Azure återställnings tider ThreadX SMP

Azure återställnings tider ThreadX SMP är en högpresterande SMP-kernel i real tid som utformats specifikt för inbäddade program. Det här kapitlet innehåller en introduktion till produkten och en beskrivning av dess program och förmåner.

## <a name="threadx-smp-unique-features"></a>ThreadX SMP-unika funktioner

ThreadX SMP ger symmetrisk multi-Processing (SMP)-teknik till inbäddade program. ThreadX SMP-programtrådar (varierande prioritet) som är klara att köra är dynamiskt allokerade till tillgängliga processor kärnor under schemaläggning. Detta resulterar i sann SMP-bearbetning, inklusive automatisk belastnings utjämning för program tråd körningar i alla tillgängliga processor kärnor.

Till skillnad från andra kärnor i real tid har ThreadX SMP utformats för att vara flexibelt, vilket enkelt kan skalas mellan små mikrokontrollantbaserade program med hjälp av kraftfulla CISC-, RISC-och DSP-processorer.

ThreadX SMP är skalbart baserat på dess underliggande arkitektur. Eftersom ThreadX SMP-tjänster implementeras som ett C-bibliotek kommer endast de tjänster som faktiskt används av programmet att tas i kör tids avbildningen. Den faktiska storleken på ThreadX SMP bestäms därför helt av programmet. För de flesta program är instruktions bilden av ThreadX SMP-intervall mellan 5 och 20 KByte i storlek.

### <a name="picokernel-architecture"></a>picokernel™-arkitektur 
I stället för att skikta kernel-funktioner ovanpå varandra som traditionella *mikrokernel* -arkitekturer ansluter ThreadX SMP-tjänster direkt till kärnan. Detta resulterar i den snabbast möjliga kontext byten och prestanda för tjänst anrop. Vi kallar den här dislagerbaserat-utformningen av en *picokernel* -arkitektur.

### <a name="ansi-c-source-code"></a>ANSI C-källkod 
ThreadX SMP skrivs huvudsakligen i ANSI C. En liten mängd sammansättnings språk krävs för att skräddarsy kärnan till den underliggande mål processorn. Den här designen gör det möjligt att Porta ThreadX SMP till en ny processor familj på kort tid, vanligt vis inom några veckor!

### <a name="advanced-technology"></a>Avancerad teknik 
Här följer några höjd punkter för den avancerade tekniken ThreadX SMP:

  - Enkel *picokernel* -arkitektur
  - Automatisk belastnings utjämning
  - Undantag för processor per tråd
  - Automatisk skalning (små avtryck)
  - Deterministisk bearbetning
  - Snabb real tids prestanda
  - Ogiltiga och samarbets schema
  - Flexibel tråd prioritets stöd (32-1024)
  - Generering av dynamiskt system objekt
  - Obegränsat antal system objekt
  - Optimerad avbrotts hantering
  - Avstängningen – tröskel™
  - Prioritera arv
  - Händelse länknings™
  - Snabba program varu timers
  - Minnes hantering för körnings tid
  - Prestanda övervakning i körnings läge
  - Stack analys i körnings läge
  - Inbyggd system spårning
  - Omfattande processor support
  - Stöd för omfattande utvecklingsverktyg
  - Fullständig endian-neutral

### <a name="not-a-black-box"></a>Inte en svart ruta
De flesta distributioner av ThreadX SMP innehåller den fullständiga C-källkoden och processorspecific-sammansättningens språk. Detta eliminerar "svarta box"-problem som uppstår i många kommersiella kärnor. Med ThreadX SMP kan programutvecklare se exakt vad kärnan gör – det finns inga Mysteries!

Käll koden tillåter också programspecifika ändringar. Även om det inte rekommenderas, är det verkligen fördelaktigt att ha möjlighet att ändra kärnan om det är absolut nödvändigt.

Dessa funktioner är särskilt praktiska för utvecklare som är vana vid att arbeta med sina egna *inhusiga kärnor*. De förväntar sig ha källkod och möjligheten att ändra kärnan. ThreadX SMP är den ultimata kärnan för sådana utvecklare.

### <a name="the-rtos-standard"></a>ÅTERSTÄLLNINGS tider-standarden
På grund av dess mångsidighet, högpresterande *picokernel* arkitektur, avancerad teknik och demonstrerad portabilitet, distribueras ThreadX SMP på över 2 000 000 000 enheter idag. Detta gör att ThreadX SMP återställnings tider standard för djupt inbäddade program.

## <a name="safety-certifications"></a>Säkerhets certifieringar

### <a name="tv-certification"></a>TÜV-certifiering  
ThreadX SMP har certifierats av SGS-TÜV Saar för användning i säkerhets kritiska system, enligt IEC61508 och IEC-62304. Certifieringen bekräftar att ThreadX SMP kan användas i utvecklingen av säkerhetsrelaterad program vara för de högsta säkerhets integritets nivåerna för International Electrotechnical Commission (IEC) 61508 och IEC 62304 för "den funktionella säkerheten i elektriska, elektroniska och programmerbara elektroniskt säkerhetsrelaterade system." SGS – TÜV Saar, som bildas genom ett gemensamt venture i Tyskland SGS-Group och TÜV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC 62304, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner och järnvägs kontroll system.

SGS-TÜV Saar har certifierat ThreadX SMP som ska användas i säkerhets kritiska motor system enligt ISO 26262-standarden. Dessutom är ThreadX SMP certifierat för ASIL (biosäkerhet Integrity Level) D som representerar den högsta nivån av ISO 26262-certifiering.

Dessutom har SGS-TÜV Saar certifierat ThreadX SMP som ska användas i säkerhets kritiska järnvägs program, vilket motsvarar en 50128-standard upp till SW-SIL 4.

![TÜV-certifiering](media/image2.png)

IEC 61508 upp till SIL 4  
IEC 62304 upp till SW säkerhets klass C  
ISO 26262 ASIL D  
EN 50128 SW-SIL 4  

> [!IMPORTANT]
> Kontakta [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) om du vill ha mer information om vilka versioner av THREADX SMP som har certifierats av TÜV eller om du vill ha till gång till test rapporter, certifikat och tillhör ande dokumentation.

### <a name="misra-c-compliant"></a>MISRA C-kompatibel 
MISRA C är en uppsättning programmerings rikt linjer för kritiska system med hjälp av programmeringsspråket C. De ursprungliga MISRA C-rikt linjerna var främst riktade mot fordonsbaserade program. men MISRA C är nu allmänt erkänd som giltig för alla säkerhets kritiska program. ThreadX SMP är kompatibelt med alla "obligatoriska" och "obligatoriska" regler för MISRA-C:2004 och MISRA C:2012. ThreadX SMP är också kompatibelt med alla utom tre "Advisory"-regler. Mer information finns i ***ThreadX_MISRA_Compliance.pdf*** -dokumentet.

### <a name="ul-certification"></a>UL-certifiering 
ThreadX SMP har certifierats av UL för efterlevnad med UL 60730-1 bilaga H, CSA E607301 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "kontroller som använder program vara" i bilaga H, innehåller IEC 60335-1-standarden kraven för "programmerbara elektroniska kretsar" i bilaga R. IEC 60730 bilaga H och IEC 60335-1 Bilaga R MCU av maskin vara och program vara som används i anordningar som tvätt maskiner, disk maskiner, Dryers, kyl skåp, frysar och ugnar.

![UL-certifiering](media/image3.png) 

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
> Kontakta [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) om du vill ha mer information om vilka versioner av THREADX SMP som har certifierats av TÜV eller om du vill ha till gång till test rapporter, certifikat och tillhör ande dokumentation.

### <a name="certification-pack"></a>Certifierings paket

ThreadX SMP-certifierings paketet™ är 100% klart, nyckel färdiga, branschspecifika, fristående paket som tillhandahåller all ThreadX SMP-bevis som krävs för att certifiera eller skicka en ThreadX SMP-baserad produkt till högsta pålitlighet och kritiska nivåer som krävs för säkerhets kritiska flyg-, medicinska och industriella system. De certifieringar som stöds är 178B, ED-12B, utför-278, FDA510 (k), IEC-62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 och 49CFR236. Kontakta sales@expresslogic.com om du vill ha mer information om certifierings paketet.

## <a name="embedded-applications"></a>Inbäddade program

Inbäddade program körs på mikroprocessorer som är täckta i produkter som trådlösa kommunikations enheter, bilbilar, laser skrivare, medicinska enheter osv. En annan åtskillnad mellan inbäddade program är att deras program vara och maskin vara har ett dedikerat syfte.

### <a name="real-time-software"></a>Real tids program 
När tids begränsningar införs i program varan kallas den för program vara i *real tid* . Program vara som måste utföra bearbetningen inom en exakt tids period kallas i princip program vara i *real tid* . Inbäddade program är nästan alltid i real tid på grund av deras inbyggda interaktion med externa händelser.

### <a name="multitasking"></a>Multitasking  
Som nämnts har inbäddade program ett dedikerat syfte. För att uppfylla det här ändamålet måste program vara utföra en rad olika *uppgifter*. En uppgift är en delvis oberoende del av programmet som utför en viss avgift. Det är också fallet att vissa uppgifter är viktigare än andra. Ett av de största svårigheterna i ett inbäddat program är allokeringen av processor mellan olika program aktiviteter. Den här allokeringen av bearbetning mellan konkurrerande uppgifter är det primära syftet med ThreadX SMP.

### <a name="tasks-vs-threads"></a>Aktiviteter eller trådar 
En annan skillnad om uppgifter måste göras. Termen uppgift används på flera olika sätt. Det innebär ibland ett separat belastnings program. I andra fall kan det hänvisa till ett internt program segment.

I modern operativ Systems diskussion finns det två villkor för att ersätta användningen av uppgift: *process* och *tråd*. En *process* är ett helt oberoende program som har sitt eget adress utrymme, medan en *tråd* är ett halv oberoende program segment som körs i en process. Trådar delar samma process adress utrymme. Den overhead som är kopplad till tråd hantering är minimal.

De flesta inbäddade program kan inte ge till gång (både minne och prestanda) som är kopplade till ett fullständigt operativ system med process-orienterad. Dessutom har mindre mikroprocessorer inte maskin varu arkitekturen som stöder ett äkta process orienterat operativ system. Av dessa skäl implementerar ThreadX SMP en tråd modell, som är både extremt effektiv och praktisk för de flesta inbäddade program i real tid.

För att undvika förvirring använder ThreadX SMP inte termen *uppgift*. I stället används den mer beskrivande och modern namn *tråden* .

## <a name="threadx-smp-benefits"></a>ThreadX SMP-förmåner

Användning av ThreadX SMP ger många fördelar med inbäddade program. Den främsta fördelen är naturligtvis i hur inbäddade program trådar allokeras bearbetnings tid.

### <a name="automatic-load-balancing"></a>Automatisk belastnings utjämning  
ThreadX SMP ger automatisk belastnings utjämning (tråd körning över tillgängliga kärnor), vilket gör det möjligt att använda processorer med flera kärnor så enkelt som möjligt. 

### <a name="improved-responsiveness"></a>Förbättrad svars tid  
Före real tids kärnor som ThreadX SMP, är de flesta inbäddade program tilldelade bearbetnings tid med en enkel kontroll slinga, vanligt vis inifrån C *main* -funktionen. Den här metoden används fortfarande i mycket små eller enkla program. I stora eller komplexa program är det dock inte praktiskt eftersom svars tiden för en händelse är en funktion i worstcase bearbetnings tid för ett pass genom kontroll slingan.

När ändringar görs i kontroll slingan kan du göra saken sämre, samtidigt som ändringen av programmet ändras. Detta gör programmet instabilt och svårt att underhålla och förbättra det.

ThreadX SMP ger snabba och deterministiska svars tider för viktiga externa händelser. ThreadX SMP utför detta genom sin ogiltiga, prioriterad schemaläggning, vilket gör att en tråd med högre prioritet åsidosätter en körning av en process med lägre prioritet. Det innebär att svars tiden för sämsta fall närmar sig den tid som krävs för att utföra en kontext växel. Detta är inte bara deterministisk, men det är också mycket snabbt.

### <a name="software-maintenance"></a>Program varu underhåll  
ThreadX SMP-kernel gör det möjligt för programutvecklare att koncentrera sig på specifika krav på sina program trådar utan att behöva oroa sig för att ändra tids inställningen för andra delar av programmet. Den här funktionen gör det också mycket enklare att reparera eller förbättra ett program som använder ThreadX SMP.

### <a name="increased-throughput"></a>Ökat data flöde  
Ett möjligt sätt att lösa problemet med svars tiden för kontroll av svar är att lägga till fler avsökningar. Detta förbättrar svars tiderna, men det garanterar fortfarande inte en konstant svars tid för värsta fall och gör inget för att förbättra den framtida modifieringen av programmet. Dessutom utför processorn nu ännu mer onödig bearbetning på grund av den extra avsökningen. All den här onödig bearbetningen minskar systemets totala data flöde.

En intressant punkt kring kostnader är att många utvecklare antar att flera trådbaserade miljöer som ThreadX SMP ökar kostnaderna och har en negativ inverkan på det totala system data flödet. Men i vissa fall minskar multitrådarna i själva verket behovet av att eliminera all redundant avsökning som inträffar i miljöer med kontroll slingor. Den overhead som är kopplad till flertrådiga kärnor är vanligt vis en funktion av den tid som krävs för kontext växling. Om kontext växlings tiden är mindre än avsöknings processen tillhandahåller ThreadX SMP en lösning med potentialen mindre omkostnader och mer data flöde. Detta gör ThreadX SMP till ett självklart val för program som har en viss komplexitet eller storlek.

### <a name="processor-isolation"></a>Processor isolering  
ThreadX SMP ger ett robust processorindependent-gränssnitt mellan programmet och den underliggande processorn. Detta gör det möjligt för utvecklare att koncentrera sig på programmet i stället för att ägna mycket tid åt att lära sig maskin varu information. 

### <a name="dividing-the-application"></a>Dela programmet  
I Control loop-baserade program måste varje utvecklare ha Intimate kunskaper om hela programmets körnings beteende och krav. Detta beror på att processor tilldelnings logiken är utspridd i hela programmet. När ett program ökar i storlek eller komplexitet blir det omöjligt för alla utvecklare att komma ihåg de exakta bearbetnings kraven för hela programmet.

ThreadX SMP frigör varje utvecklare från de bekymmer som är kopplade till processor tilldelningen och gör att de kan koncentrera sig på sina specifika delar av det inbäddade programmet. Dessutom tvingar ThreadX SMP programmet att delas upp i klart definierade trådar. Den här indelningen av programmet i trådar gör det mycket enklare att utveckla.

### <a name="ease-of-use"></a>Lätt att använda  
ThreadX SMP är utformad med program utvecklaren i åtanke. ThreadX SMP-arkitekturen och service Call-gränssnittet är utformade för att enkelt förstå. Därför kan ThreadX SMP-utvecklare snabbt använda sina avancerade funktioner.  

### <a name="improve-time-to-market"></a>Förbättra tiden till marknaden  
Alla fördelar med ThreadX SMP påskyndar program utvecklings processen. ThreadX SMP tar hand om de flesta processor problem och de vanligaste säkerhets certifieringarna, vilket tar bort den här ansträngningen från utvecklings planen. Allt detta resulterar i en snabbare tid till marknaden!  

### <a name="protecting-the-software-investment"></a>Skydda program investeringen  
På grund av sin arkitektur är ThreadX SMP enkelt att Portas till nya processorer och/eller utvecklings verktyg miljöer. Detta, tillsammans med det faktum att ThreadX SMP isolerar program från information från de underliggande processorerna, gör ThreadX SMP-program mycket bärbara. Därför garanteras programmets migrations Sök väg och den ursprungliga utvecklings investeringen är skyddad.