---
title: Kapitel 1 – Introduktion till Azure återställnings tider ThreadX
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider ThreadX och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83718ddf5469238e2429855908be2ea5d405f874
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826580"
---
# <a name="chapter-1---introduction-to-azure-rtos-threadx"></a>Kapitel 1 – Introduktion till Azure återställnings tider ThreadX

Azure återställnings tider ThreadX är en högpresterande kernel i real tid som utformats specifikt för inbäddade program. Det här kapitlet innehåller en introduktion till produkten och en beskrivning av dess program och förmåner.

## <a name="threadx-unique-features"></a>ThreadX-unika funktioner

Till skillnad från andra kärnor i real tid har ThreadX utformats för att vara flexibelt, vilket enkelt kan skalas mellan små mikrostyrenhet program via de som använder kraftfulla CISC-, RISC-och DSP-processorer.

ThreadX är skalbart baserat på dess underliggande arkitektur. Eftersom ThreadX Services implementeras som ett C-bibliotek kommer endast de tjänster som faktiskt används av programmet att tas i kör tids avbildningen. Därför bestäms den faktiska storleken för ThreadX helt av programmet. För de flesta program är instruktions bilden av ThreadX intervall mellan 2 KByte och 15 KB stor.

### <a name="picokerneltrade-architecture"></a>*picokernel- &trade; arkitektur*

I stället för att skikta kernel-funktioner ovanpå varandra som traditionella *mikrokernel* -arkitekturer, ansluter ThreadX Services direkt till kärnan. Detta resulterar i den snabbast möjliga kontext byten och prestanda för tjänst anrop. Vi kallar denna icke-skikts design en *picokernel* -arkitektur.

### <a name="ansi-c-source-code"></a>ANSI C-källkod

ThreadX skrivs främst i ANSI C. En liten mängd sammansättnings språk krävs för att skräddarsy kärnan till den underliggande mål processorn. Den här designen gör det möjligt att Porta ThreadX till en ny processor familj på kort tid, vanligt vis inom några veckor!

### <a name="advanced-technology"></a>Avancerad teknik

Här följer en beskrivning av den avancerade ThreadX-tekniken.
- Enkel *picokernel* -arkitektur
- Automatisk skalning (små avtryck)
- Deterministisk bearbetning
- Snabb real tids prestanda
- Ogiltiga och samarbets schema
- Flexibel tråd prioritets stöd
- Generering av dynamiskt system objekt
- Obegränsat antal system objekt
- Optimerad avbrotts hantering
- Avstängningen – tröskel&trade;
- Prioritera arv
- Händelse länkning&trade;
- Snabba program varu timers
- Minnes hantering för körnings tid
- Prestanda övervakning i körnings läge
- Stack analys i körnings läge
- Inbyggd system spårning
- Omfattande processor support
- Stöd för omfattande utvecklingsverktyg
- Fullständig endian-neutral

### <a name="not-a-black-box"></a>Inte en svart ruta

De flesta distributioner av ThreadX inkluderar den fullständiga C-källkoden och det processorbaserade sammansättnings språket. Detta eliminerar "svarta box"-problem som uppstår i många kommersiella kärnor. Med ThreadX kan programutvecklare se exakt vad kerneln gör – det finns inga Mysteries!

Käll koden tillåter också programspecifika ändringar. Även om det inte rekommenderas, är det verkligen fördelaktigt att ha möjlighet att ändra kärnan om det är absolut nödvändigt.

Dessa funktioner är särskilt praktiska för utvecklare som är vana vid att arbeta med sina egna *interna kärnor*. De förväntar sig ha källkod och möjligheten att ändra kärnan. ThreadX är den ultimata kärnan för sådana utvecklare.

### <a name="the-rtos-standard"></a>ÅTERSTÄLLNINGS tider-standarden

På grund av dess mångsidighet, högpresterande *picokernel* arkitektur, avancerad teknik och demonstrerad portabilitet, distribueras ThreadX på över 2 000 000 000 enheter idag. Detta gör att ThreadX återställnings tider-standarden för djupt inbäddade program blir effektivare.

## <a name="safety-certifications"></a>Säkerhets certifieringar

### <a name="tv-certification"></a>TÜV-certifiering

ThreadX har certifierats av SGS-TÜV Saar för användning i säkerhets kritiska system, enligt IEC61508 och IEC-62304. Certifieringen bekräftar att ThreadX kan användas i utvecklingen av säkerhetsrelaterad program vara för den högsta säkerhets integritets nivån för International Electrotechnical Commission (IEC) 61508 och IEC 62304, för "den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system." SGS – TÜV Saar, som bildas genom ett gemensamt företag i Tyskland SGSGroup och TÜV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen. Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC 62304, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner och järnvägs kontroll system.

SGS – TÜV Saar har certifierat ThreadX som ska användas i säkerhetskritiska bil system, enligt ISO 26262-standarden. Dessutom är ThreadX certifierat för att ASIL () D, som motsvarar den högsta nivån av ISO 26262-certifiering.

Dessutom har SGS-TÜV Saar certifierat ThreadX som ska användas i verksamhets kritiska järnvägs program, vilket motsvarar en 50128-standard upp till SW-SIL 4.

![TÜV-certifiering](./media/overview-threadx/partener-logo-sgs-tuv-saar-2.png)

* IEC 61508 upp till SIL 4

* IEC 62304 upp till SW säkerhets klass C

* ISO 26262 ASIL D

* EN 50128 SW-SIL 4

> [!NOTE]
> *Kontakta oss om du vill ha mer information om vilka versioner av ThreadX som har certifierats av TÜV eller om du vill ha till gång till test rapporter, certifikat och tillhör ande dokumentation.*

### <a name="misra-c-compliant"></a>MISRA C-kompatibel

MISRA C är en uppsättning programmerings rikt linjer för kritiska system med hjälp av programmeringsspråket C. De ursprungliga MISRA C-rikt linjerna var främst riktade mot fordonsbaserade program. men MISRA C är nu allmänt erkänd som giltig för alla säkerhets kritiska program. ThreadX är kompatibel med alla "obligatoriska" och "obligatoriska" regler för MISRA-C:2004 och MISRA C:2012. ThreadX är också kompatibelt med alla utom tre "Advisory"-regler. Mer information finns i ***ThreadX_MISRA_Compliance.pdf*** -dokumentet.

### <a name="ul-certification"></a>UL-certifiering

ThreadX har certifierats av UL för efterlevnad med UL 60730-1 bilaga H, CSA E60730-1 bilaga H, IEC 60730-1 bilaga H, UL 60335-1 Bilaga R, IEC 60335-1 Bilaga R och UL 1998 säkerhets standarder för program vara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "kontroller som använder program vara" i bilaga H, innehåller IEC 60335-1-standarden kraven för "programmerbara elektroniska kretsar" i bilaga R. IEC 60730 bilaga H och IEC 60335-1 Bilaga R MCU av maskin vara och program vara som används i anordningar som tvätt maskiner, disk maskiner, Dryers, kyl skåp, frysar och ugnar.

![UL-certifiering](./media/overview-threadx/partener-logo-c-ru-us-2.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!NOTE]
> *Kontakta Microsoft om du vill ha mer information om vilka versioner av ThreadX som har certifierats av TÜV eller om du vill ha till gång till test rapporter, certifikat och tillhör ande dokumentation.*

### <a name="certification-pack"></a>Certifierings paket

Certifierings paketet för ThreadX &trade; är 100% klart, nyckel färdiga, branschspecifika, fristående paket som tillhandahåller all ThreadX-bevis som krävs för att certifiera eller skicka den ThreadX produkten till den högsta Tillförlitlighets nivån och de kritiska nivåer som krävs för säkerhets kritiska luftfart, medicinska och industriella system. Certifieringar som stöds är 178B, ED-12B, göra-278, FDA510 (k), IEC62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 och 49CFR236. Kontakta Microsoft om du vill ha mer information om certifierings paketet.

## <a name="embedded-applications"></a>Inbäddade program

Inbäddade program körs på mikroprocessorer som är täckta i produkter som trådlösa kommunikations enheter, bilbilar, laser skrivare, medicinska enheter osv. En annan åtskillnad mellan inbäddade program är att deras program vara och maskin vara har ett dedikerat syfte.

### <a name="real-time-software"></a>Real tids program

När tids begränsningar införs i program varan kallas den för program vara i *real tid* . Inbäddade program är nästan alltid i real tid på grund av deras inbyggda interaktion med externa händelser.

### <a name="multitasking"></a>Multitasking

Som nämnts har inbäddade program ett dedikerat syfte. För att uppfylla det här ändamålet måste program vara utföra en rad olika *uppgifter*. En uppgift är en delvis oberoende del av programmet som utför en viss avgift. Det är också fallet att vissa uppgifter är viktigare än andra. Ett av de största svårigheterna i ett inbäddat program är allokeringen av processor mellan olika program aktiviteter. Den här allokeringen av bearbetning mellan konkurrerande uppgifter är det primära syftet med ThreadX.

### <a name="tasks-vs-threads"></a>Aktiviteter eller trådar

En annan skillnad om aktiviteter är att termen *uppgift* används på flera olika sätt. Det innebär ibland ett separat belastnings program. I andra fall kan det hänvisa till ett internt program segment. I modern operativ system finns det därför två villkor för att ersätta användningen av uppgift: *process* och *tråd*. En *process* är ett helt oberoende program som har sitt eget adress utrymme, medan en *tråd* är ett halv oberoende program segment som körs i en process. Trådar delar samma process adress utrymme. Den overhead som är kopplad till tråd hantering är minimal.

De flesta inbäddade program kan inte ge till gång (både minne och prestanda) som är kopplade till ett fullständigt operativ system med process-orienterad. Dessutom har mindre mikroprocessorer inte maskin varu arkitekturen som stöder ett äkta process orienterat operativ system. Av dessa skäl implementerar ThreadX en tråd modell, som är både extremt effektiv och praktisk för de flesta inbäddade program i real tid.

För att undvika förvirring använder ThreadX inte termen *uppgift*. I stället används den mer beskrivande och modern namn *tråden* .

## <a name="threadx-benefits"></a>ThreadX-förmåner

Användning av ThreadX ger många fördelar med inbäddade program. Den främsta fördelen är naturligtvis i hur inbäddade program trådar allokeras bearbetnings tid.

### <a name="improved-responsiveness"></a>Förbättrad svars tid

Innan real tids kärnor som ThreadX, har de flesta inbäddade program allokerat bearbetnings tid med en enkel kontroll slinga, vanligt vis inifrån C *main* -funktionen. Den här metoden används fortfarande i mycket små eller enkla program. I stora eller komplexa program är det dock inte praktiskt eftersom svars tiden för en händelse är en funktion av den värsta fall bearbetnings tiden för ett pass genom kontroll slingan. 

När ändringar görs i kontroll slingan kan du göra saken sämre, samtidigt som ändringen av programmet ändras. Detta gör programmet instabilt och svårt att underhålla och förbättra det.

ThreadX tillhandahåller snabba och deterministiska svars tider för viktiga externa händelser. ThreadX uppnår detta genom sin ogiltiga, prioriterad schemaläggning, som tillåter en tråd med högre prioritet att åsidosätta en körning av en tråd med lägre prioritet. Det innebär att svars tiden för sämsta fall närmar sig den tid som krävs för att utföra en kontext växel. Detta är inte bara deterministisk, men det är också mycket snabbt.

### <a name="software-maintenance"></a>Program varu underhåll

ThreadX-kärnan gör det möjligt för programutvecklare att koncentrera sig på specifika krav på sina program trådar utan att behöva oroa sig för att ändra tids inställningen för andra delar av programmet. Den här funktionen gör det också mycket enklare att reparera eller förbättra ett program som använder ThreadX.

### <a name="increased-throughput"></a>Ökat data flöde

Ett möjligt sätt att lösa problemet med svars tiden för kontroll av svar är att lägga till fler avsökningar. Detta förbättrar svars tiderna, men det garanterar fortfarande inte en konstant svars tid för värsta fall och gör inget för att förbättra den framtida modifieringen av programmet. Dessutom utför processorn nu ännu mer onödig bearbetning på grund av den extra avsökningen. All den här onödig bearbetningen minskar systemets totala data flöde.

En intressant punkt kring kostnader är att många utvecklare antar att flera trådbaserade miljöer, t. ex. ThreadX, ökar kostnaderna och har negativ inverkan på totala system data flöde. Men i vissa fall minskar multitrådarna i själva verket behovet av att eliminera all redundant avsökning som inträffar i miljöer med kontroll slingor. Den overhead som är kopplad till flertrådiga kärnor är vanligt vis en funktion av den tid som krävs för kontext växling. Om kontext växlings tiden är mindre än avsöknings processen ger ThreadX en lösning med potentialen mindre omkostnader och mer data flöde. Detta gör ThreadX till ett tydligt val för program som har viss komplexitet eller storlek.

### <a name="processor-isolation"></a>Processor isolering

ThreadX tillhandahåller ett robust processor oberoende gränssnitt mellan programmet och den underliggande processorn. Detta gör det möjligt för utvecklare att koncentrera sig på programmet i stället för att ägna mycket tid åt att lära sig maskin varu information.

### <a name="dividing-the-application"></a>Dela programmet

I Control loop-baserade program måste varje utvecklare ha Intimate kunskaper om hela programmets körnings beteende och krav. Detta beror på att processor tilldelnings logiken är utspridd i hela programmet. När ett program ökar i storlek eller komplexitet blir det omöjligt för alla utvecklare att komma ihåg de exakta bearbetnings kraven för hela programmet.

ThreadX frigör varje utvecklare från de bekymmer som är kopplade till processor tilldelningen och gör det möjligt för dem att koncentrera sig på sina specifika delar av det inbäddade programmet. Dessutom tvingar ThreadX programmet att delas upp i klart definierade trådar. Den här indelningen av programmet i trådar gör det mycket enklare att utveckla.

### <a name="ease-of-use"></a>Lätt att använda

ThreadX är utformad med program utvecklaren i åtanke. ThreadX-arkitekturen och tjänst anrops gränssnittet är utformade för att enkelt förstås. Därför kan ThreadX-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknaden

Alla fördelarna med ThreadX påskyndar program utvecklings processen. ThreadX tar hand om de flesta processor problem och de vanligaste säkerhets certifieringarna, vilket tar bort den här ansträngningen från utvecklings planen. Allt detta resulterar i en snabbare tid till marknaden!

### <a name="protecting-the-software-investment"></a>Skydda program investeringen

På grund av sin arkitektur är ThreadX enkelt att Portas till nya processorer och/eller utvecklings verktyg miljöer. Detta, tillsammans med det faktum att ThreadX isolerar program från information från de underliggande processorerna, gör ThreadX-program mycket portabla. Därför garanteras programmets migrations Sök väg och den ursprungliga utvecklings investeringen är skyddad.
