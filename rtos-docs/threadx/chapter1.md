---
title: Kapitel 1 – Introduktion till Azure RTOS ThreadX
description: Det här kapitlet innehåller en introduktion Azure RTOS ThreadX och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 536b2d59bf9f2cf15d320b91277f0efc7bf96097329f690b0849b2145c5a3abc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802075"
---
# <a name="chapter-1---introduction-to-azure-rtos-threadx"></a>Kapitel 1 – Introduktion till Azure RTOS ThreadX

Azure RTOS ThreadX är en högpresterande realtidskärna som utformats specifikt för inbäddade program. Det här kapitlet innehåller en introduktion till produkten och en beskrivning av dess program och fördelar.

## <a name="threadx-unique-features"></a>Unika ThreadX-funktioner

Till skillnad från andra realtidskärnor är ThreadX utformat för att vara flexibelt – skalning enkelt bland små mikrostyrprogram med hjälp av de som använder kraftfulla CISC-, RISC- och DSP-processorer.

ThreadX är skalbart baserat på dess underliggande arkitektur. Eftersom ThreadX-tjänster implementeras som ett C-bibliotek, kommer endast de tjänster som faktiskt används av programmet att tas med i körningsavbildningen. Den faktiska storleken på ThreadX bestäms därför helt av programmet. För de flesta program sträcker sig instruktionsbilden av ThreadX mellan 2 KByte och 15 KByte i storlek.

### <a name="picokerneltrade-architecture"></a>*picokernel-arkitektur &trade;*

I stället för att skikta kernelfunktioner ovanpå varandra, som traditionella *mikrokernel-arkitekturer,* ansluts ThreadX-tjänster direkt till kärnan. Detta resulterar i snabbaste möjliga kontextväxling och prestanda för tjänstsamtal. Vi kallar den här icke-lagerdesignen för *en picokernel-arkitektur.*

### <a name="ansi-c-source-code"></a>ANSI C-källkod

ThreadX är främst skrivet i ANSI C. En liten mängd sammansättningsspråk krävs för att skräddarsy kerneln till den underliggande målprocessorn. Den här designen gör det möjligt att porta ThreadX till en ny processorfamilj på mycket kort tid, vanligtvis inom några veckor!

### <a name="advanced-technology"></a>Avancerad teknik

Här är några av de viktigaste teknikerna inom den avancerade ThreadX-tekniken.
- Enkel *picokernel-arkitektur*
- Automatisk skalning (litet fotavtryck)
- Deterministisk bearbetning
- Snabba prestanda i realtid
- Förebyggande och schemaläggning av schemaläggning
- Stöd för flexibel trådprioritet
- Skapa objekt med dynamiskt system
- Obegränsat antal systemobjekt
- Optimerad avbrottshantering
- Tröskelvärde för avspärrning&trade;
- Prioritetsarv
- Händelsekedja&trade;
- Snabba programvarutimer
- Hantering av körningsminne
- Prestandaövervakning av körning
- Analys av körningsstackar
- Inbyggd systemspårning
- Omfattande processorstöd
- Omfattande stöd för utvecklingsverktyg
- Helt endiansk neutral

### <a name="not-a-black-box"></a>Inte en svart låda

De flesta distributioner av ThreadX innehåller den fullständiga C-källkoden samt det processorspecifika sammansättningsspråket. Detta eliminerar de "black-box"-problem som uppstår med många kommersiella kernels. Med ThreadX kan programutvecklare se exakt vad kerneln gör – det finns inga problem!

Källkoden tillåter även programspecifika ändringar. Även om det inte rekommenderas är det verkligen fördelaktigt att ha möjlighet att ändra kerneln om det är absolut nödvändigt.

Dessa funktioner är särskilt bekväma för utvecklare som är vana vid att arbeta *med sina egna in-house kernels.* De förväntar sig att ha källkod och möjlighet att ändra kerneln. ThreadX är den ultimata kerneln för sådana utvecklare.

### <a name="the-rtos-standard"></a>The RTOS Standard

På grund av sin flexibilitet, högpresterande *picokernel-arkitektur,* avancerade teknik och demonstrerad portabilitet, distribueras ThreadX i mer än två miljarder enheter i dag. Detta gör i praktiken ThreadX till RTOS-standarden för djupt inbäddade program.

## <a name="safety-certifications"></a>Säkerhetscertifieringar

### <a name="tv-certification"></a>TÜV-certifiering

ThreadX har certifierats av SGS-TÜV Saar för användning i säkerhetskritiska system enligt IEC61508 och IEC-62304. Certifieringen bekräftar att ThreadX kan användas i utvecklingen av säkerhetsrelaterad programvara för högsta säkerhetsintegritetsnivåer för International Electrotechnical Commission (IEC) 61508 och IEC 62304, för "funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system". SGS-TÜV Saar, som bildas tillsammans med Tysklands SGSGroup och TÜV Saarland, har blivit det ledande auktoriserade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad programvara för säkerhetsrelaterade system över hela världen. Den industriella säkerhetsstandarden IEC 61508 och alla standarder som härleds från den, inklusive IEC 62304, används för att garantera funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, processkontrollsystem, industriella maskiner och system för kontroll av djur.

SGS-TÜV Saar har certifierat ThreadX för användning i säkerhetskritiska fordonssystem enligt ISO 26262-standarden. ThreadX är dessutom certifierat till ASIL (Bilsäkerhetsintegritetsnivå) D, som representerar den högsta nivån av ISO 26262-certifiering.

SGS-TÜV Saar har dessutom certifierat ThreadX för användning i säkerhetskritiska program, som uppfyller STANDARDEN EN 50128 upp till SW-SIL 4.

![TÜV-certifiering](./media/overview-threadx/partener-logo-sgs-tuv-saar-2.png)

* IEC 61508 upp till SIL 4

* IEC 62304 upp till SW-säkerhetsklass C

* ISO 26262 ASIL D

* EN 50128 SW-SIL 4

> [!NOTE]
> *Kontakta oss om du vill ha mer information om vilka versioner av ThreadX som har certifierats av TÜV eller för att få tillgång till testrapporter, certifikat och tillhörande dokumentation.*

### <a name="misra-c-compliant"></a>MISRA C-kompatibel

MISRA C är en uppsättning programmeringsriktlinjer för kritiska system som använder programmeringsspråket C. De ursprungliga riktlinjerna för MISRA C var främst riktade mot biltillämpningar. MEN MISRA C är nu allmänt känt som tillämpligt för alla säkerhetskritiska program. ThreadX är kompatibelt med alla "obligatoriska" och "obligatoriska" regler för MISRA-C:2004 och MISRA C:2012. ThreadX är också kompatibelt med alla utom tre "rådgivande" regler. Se dokumentet ***ThreadX_MISRA_Compliance.pdf*** för mer information.

### <a name="ul-certification"></a>UL-certifiering

ThreadX har certifierats av UL för kompatibilitet med UL 60730-1Uppdateringar H, CSA E60730-1Uppdateringar H, IEC 60730-1 Ul 60335-1× R, IEC 60335-1 – 1– 1998- och UL 1998-säkerhetsstandarder för programvara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav för "Kontroller med hjälp av programvara" i sin Klass H, beskriver IEC 60335-1-standarden kraven för "Programmerbara elektroniska kretsar" i sin iEC 60730 60330 IEC 60335-1 Vis R tar upp säkerheten för MCU-maskinvara och programvara som används i maskiner som t.ex. maskiner, reglage, torktumlare, kylskåp, skunderar och hjälpmedel.

![UL-certifiering](./media/overview-threadx/partener-logo-c-ru-us-2.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!NOTE]
> *Kontakta Microsoft för mer information om vilka versioner av ThreadX som har certifierats av TÜV eller för att få tillgång till testrapporter, certifikat och tillhörande dokumentation.*

### <a name="certification-pack"></a>Certifieringspaket

ThreadX-certifieringspaketet är ett 100 % komplett, nyckelfärdigt, branschspecifikt, fristående paket som tillhandahåller alla ThreadX-bevis som behövs för att certifiera eller skicka den ThreadX-baserade produkten till de högsta tillförlitlighets- och allvarlighetsnivåerna som krävs för säkerhetskritiska system inom flyg, medicin och &trade; industri. Certifieringar som stöds omfattar DO-178B, ED-12B, DO-278, VAR510(k), IEC62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENSELECT EN50128, BS50128 och 49CFR236. Kontakta Microsoft för mer information om certifieringspaket.

## <a name="embedded-applications"></a>Inbäddade program

Inbäddade program körs på mikroprocessorer som finns besökt i produkter som trådlösa kommunikationsenheter, bilmotorer,laserskrivare, medicinska enheter osv. En annan skillnad mellan inbäddade program är att deras programvara och maskinvara har ett särskilt syfte.

### <a name="real-time-software"></a>Realtidsprogramvara

När tidsbegränsningar tillämpas på programmet kallas det *för realtidsprogramvaran.* Inbäddade program är nästan alltid i realtid på grund av deras inbyggda interaktion med externa händelser.

### <a name="multitasking"></a>Multitasking

Som tidigare nämnts har inbäddade program ett dedikerat syfte. För att uppfylla det här syftet måste programvaran utföra en mängd olika *uppgifter.* En uppgift är en halvoberoende del av programmet som utför en viss uppgift. Det är också fallet att vissa uppgifter är viktigare än andra. En av de största problemen i ett inbäddat program är allokeringen av processorn mellan de olika programuppgifterna. Den här allokeringen av bearbetning mellan konkurrerande uppgifter är det primära syftet med ThreadX.

### <a name="tasks-vs-threads"></a>Uppgifter kontra trådar

En annan skillnad vad gäller uppgifter är *att termen* uppgift används på flera olika sätt. Det innebär ibland ett separat belastningsbart program. I andra fall kan det referera till ett internt programsegment. I moderna operativsystem finns det därför två termer som mer eller mindre ersätter användningen av aktivitet: *process* och *tråd*. En *process* är ett helt oberoende program som  har ett eget adressutrymme, medan en tråd är ett halvoberoende programsegment som körs inom en process. Trådar delar samma processadressutrymme. Arbetet som är associerat med trådhantering är minimalt.

De flesta inbäddade program har inte råd med de kostnader (både minne och prestanda) som är associerade med ett fullständigt processorienterat operativsystem. Dessutom har mindre mikroprocessorer inte maskinvaruarkitektur för att stödja ett verkligt processorienterat operativsystem. Av dessa skäl implementerar ThreadX en trådmodell, vilket är både mycket effektivt och praktiskt för de flesta inbäddade realtidsprogram.

ThreadX använder inte termen aktivitet för att undvika *förvirring.* I stället används den mer beskrivande och *beskrivande* namntråden.

## <a name="threadx-benefits"></a>ThreadX-fördelar

Att använda ThreadX ger många fördelar med inbäddade program. Den främsta fördelen ligger förstås i hur inbäddade programtrådar allokeras bearbetningstid.

### <a name="improved-responsiveness"></a>Förbättrad svarstid

Före realtidskärnor som ThreadX allokerade de flesta inbäddade program bearbetningstid med en enkel kontrollloop, vanligtvis inifrån *C-huvudfunktionen.* Den här metoden används fortfarande i mycket små eller enkla program. I stora eller komplexa program är det dock inte praktiskt eftersom svarstiden för en händelse är en funktion av den sämsta bearbetningstiden för ett fall som passerar genom kontrollloopen. 

Det är ännu värre att tidsegenskaperna för programmet ändras när ändringar görs i kontrollloopen. Detta gör programmet i sig instabilt och svårt att underhålla och förbättra.

ThreadX ger snabba och deterministiska svarstider för viktiga externa händelser. ThreadX åstadkommer detta genom sin förebyggande, prioritetsbaserade schemaläggningsalgoritm, vilket gör att en tråd med högre prioritet kan avinstallera en tråd med lägre prioritet. Det innebär att svarstiden i värsta fall närmar sig den tid som krävs för att utföra en kontextväxel. Detta är inte bara deterministiskt, utan även mycket snabbt.

### <a name="software-maintenance"></a>Programvaruunderhåll

ThreadX-kerneln gör det möjligt för programutvecklare att koncentrera sig på specifika krav för sina programtrådar utan att behöva bekymra sig om att ändra tidpunkten för andra delar av programmet. Den här funktionen gör det också mycket enklare att reparera eller förbättra ett program som använder ThreadX.

### <a name="increased-throughput"></a>Ökat dataflöde

En möjlig lösning på problemet med svarstiden för kontrollloopen är att lägga till fler avsökning. Detta förbättrar svarstiderna, men garanterar fortfarande inte en konstant svarstid i värsta fall och gör ingenting för att förbättra framtida ändringar av programmet. Dessutom utför processorn nu ännu mer onödig bearbetning på grund av den extra avsökning. All denna onödiga bearbetning minskar systemets totala dataflöde.

En intressant punkt när det gäller omkostnader är att många utvecklare förutsätter att flertrådade miljöer som ThreadX ökar omkostnaderna och har en negativ inverkan på det totala systemets dataflöde. Men i vissa fall minskar multitrådning faktiskt omkostnaderna genom att eliminera all redundant avsökning som sker i kontrollloopmiljöer. Omkostnaderna för flertrådade kernels är vanligtvis en funktion för den tid som krävs för kontextväxling. Om kontextväxeltiden är mindre än avsökningsprocessen tillhandahåller ThreadX en lösning med potentialen mindre omkostnader och större dataflöde. Detta gör ThreadX till ett uppenbart val för program som har någon grad av komplexitet eller storlek.

### <a name="processor-isolation"></a>Processorisolering

ThreadX ger ett robust processoroberoende gränssnitt mellan programmet och den underliggande processorn. På så sätt kan utvecklare koncentrera sig på programmet i stället för att ägna mycket tid åt att lära sig maskinvaruinformation.

### <a name="dividing-the-application"></a>Dela upp programmet

I kontrollloopbaserade program måste varje utvecklare ha en nära kunskap om hela programmets körningsbeteende och krav. Det beror på att processorallokeringslogiken är utspridd i hela programmet. När ett program ökar i storlek eller komplexitet blir det omöjligt för alla utvecklare att komma ihåg de exakta bearbetningskraven för hela programmet.

ThreadX frigör varje utvecklare från problem som är associerade med processorallokering och gör att de kan koncentrera sig på den specifika delen av det inbäddade programmet. Dessutom tvingar ThreadX programmet att delas in i tydligt definierade trådar. Den här uppdelningen av programmet i trådar gör utvecklingen mycket enklare.

### <a name="ease-of-use"></a>Användarvänlighet

ThreadX är utformat med programutvecklaren i åtanke. ThreadX-arkitekturen och tjänstanropsgränssnittet är utformade för att vara lätta att förstå. Därför kan ThreadX-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknad

Alla fördelar med ThreadX påskyndar programutvecklingsprocessen. ThreadX tar hand om de flesta processorproblem och de vanligaste säkerhetscertifieringarna, vilket tar bort detta arbete från utvecklingsschemat. Allt detta resulterar i en snabbare tid till marknad!

### <a name="protecting-the-software-investment"></a>Skydda programvaruinvesteringen

På grund av arkitekturen portas ThreadX enkelt till nya processor- och/eller utvecklingsverktygsmiljöer. Detta, tillsammans med det faktum att ThreadX isolerar program från detaljer om de underliggande processorerna, gör ThreadX-program mycket portabla. Därför garanteras programmets migreringsväg och den ursprungliga utvecklingsinvesteringen skyddas.
