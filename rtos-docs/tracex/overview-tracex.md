---
title: Förstå Azure återställnings tider-TraceX
description: Azure återställnings tider TraceX är Microsofts värdbaserade analys verktyg som ger utvecklare en grafisk vy över system händelser i real tid och gör det möjligt för dem att visualisera och bättre förstå hur real tids system fungerar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 9fd33eec6da69e6dda421a125a2dde5eae93b46d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828626"
---
# <a name="overview-of-azure-rtos-tracex"></a>Översikt över Azure återställnings tider-TraceX

Azure återställnings tider TraceX är Microsofts värdbaserade analys verktyg som ger utvecklare en grafisk vy över system händelser i real tid och gör det möjligt för dem att visualisera och bättre förstå hur real tids system fungerar. Med Azure återställnings tider-TraceX kan utvecklare tydligt visa förekomst av system händelser som avbrott och kontext byten som inträffar utanför vyn med standard fel söknings verktyg. Möjligheten att identifiera och studera de här händelserna, och för att precisera tidpunkten för deras förekomst i samband med det övergripande systemets funktion gör det möjligt för utvecklare att lösa programmerings problem genom att hitta oväntade beteenden och låta dem undersöka specifika områden ytterligare spårnings information lagras i en buffert i mål systemet, med den buffertstorlek och storlek som fastställs av programmet vid körning. Azure återställnings tider TraceX kan bearbeta alla buffertar som konstruerats på rätt sätt, inte bara från Azure återställnings tider-ThreadX, utan från alla program och återställnings tider. Spårnings informationen kan överföras till värden för analys när som helst, antingen efter slakt eller vid en Bryt punkt. Azure återställnings tider ThreadX implementerar en cirkulär buffert, som gör att de senaste "N" händelserna blir tillgängliga för granskning i händelse av systemfel eller andra viktiga händelser.

![Azure återställnings tider TraceX Single-Core display](./media/user-guide/screen_shot_33.png)

**TraceX Single-Core visning**

## <a name="key-capabilites"></a>Key funktioner

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Inbyggda system analyser i Azure återställnings tider TraceX

Azure återställnings tider TraceX innehåller inbyggda system analys rapporter som är tillgängliga via en enda knapp genom att klicka på TraceX-verktygsfältet. Följande knappar och rapporter innehåller:

![Skapa rapport för körnings profil](./media/overview-tracex/execution-profile-report-button.jpg) Skapa rapport för körnings profil

![Generera rapport över prestanda statistik](./media/overview-tracex/performance-statistics-report-button.jpg) Generera rapport över prestanda statistik

![Generera rapport över tråds tack användning](./media/overview-tracex/thread-stack-usage-report-button.jpg) Generera rapport över tråds tack användning

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Spårnings data som samlats in av Azure återställnings tider ThreadX

Azure återställnings tider TraceX har utformats för att fungera med Azure återställnings tider-ThreadX, som skapar en databas med system-och program händelser i mål systemet vid körning. Dessa händelser omfattar:

* tråd kontexts växlar
* preemptions
* SUS pensioner
* avslutningar
* system avbrott
* programspecifika händelser
* alla Azure återställnings tider ThreadX API-anrop
* alla Azure återställnings tider NetX API-anrop
* alla Azure återställnings tider FileX API-anrop
* alla Azure återställnings tider USBX API-anrop
* programdefinierade ikoner och information

Händelser loggas under program kontroll, med tids stämpling och identifiering av aktiva trådar så att de kan visas senare i rätt tidssekvens och associeras med lämplig tråd. Händelse loggning kan stoppas och startas om av program programmet dynamiskt, till exempel när ett intresse områden påträffas. På så sätt undviker du att databasen fylls i och att mål minnet används när systemet fungerar som det ska.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Azure återställnings tider-TraceX är som en program logik analys

När händelse loggen har laddats upp från mål minnet till värden, visar Azure återställnings tider TraceX händelserna grafiskt på en vågrät axel som representerar tid, med de olika program trådar och system rutiner som händelserna är relaterade till i listan längs den lodräta axeln. Azure återställnings tider TraceX skapar en "Software Logic Analyzer" på värden och gör system händelser som visas i klartext. Händelser representeras av färgkodade ikoner, som finns på förekomst punkten längs den vågräta tids linjen till höger om relevant tråd-eller system rutin. När en händelse ikon väljs, visas motsvarande information för händelsen, samt information om de två föregående och två efterföljande händelser. Detta ger snabb och enkel klickning till den mest omedelbara informationen om händelsen och de omedelbart omgivande händelserna. Azure återställnings tider TraceX innehåller en sammanfattnings visning som visar alla system händelser på en enda vågrät linje för att förenkla analyser av system med många trådar.

### <a name="sequential-view-mode"></a>Sekventiellt visnings läge

Det sekventiella visnings läget är valt genom att klicka på fliken "sekventiell vy". Detta är standard läget. I det här läget visas händelser direkt efter varandra, oavsett hur lång tid som förflutit. Observera också linjalen ovanför visnings ytan. Det visar det relativa händelse numret från början av spåret. Det här läget är standard läget och är särskilt användbart för att få en bra översikt över vad som händer i systemet.

![Sekventiellt visnings läge](./media/user-guide/screen_shot_10.png)

**Sekventiellt visnings läge**

### <a name="time-view-mode"></a>Tids visnings läge

I det här läget visas händelser i ett relativt relativt läge – med ett fyllt grönt fält som används för att Visa körning mellan händelser. Det här läget är särskilt användbart för att se var bearbetningen sker i systemet, vilket kan hjälpa utvecklare att finjustera systemet för att få bättre prestanda och/eller svars tider.

Observera också linjalen ovanför händelse visningen. Den här linjalen visar relativa skal streck från början av spåret, som härletts från den tidsstämpeln som instrumenteras i händelse spårnings loggningen i Azure återställnings tider-ThreadX. Om tidsstämplarna är för nära (låg frekvens, timer), kommer händelserna att köras tillsammans. Om tidsstämplar är för långt ifrån varandra (med hög frekvens), kommer händelserna att vara för långt ifrån varandra. Att välja rätt tidsintervall är ett viktigt övervägande för att göra tiden relativt meningsfull vy.

![Tids visnings läge](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>System sammanfattnings rad

Azure återställnings tider TraceX innehåller också en enda sammanfattnings rad som innehåller alla händelser på samma rad. Sammanfattnings raden innehåller en sammanfattning av kontexten samt motsvarande händelse Sammanfattning under. Detta gör det enkelt att se en översikt över ett komplext system. Sammanfattnings fältet är särskilt fördelaktigt i system som har ett stort antal trådar. Utan en sådan sammanfattnings rad skulle användaren behöva följa komplexa system interaktioner med den lodräta rullnings listen för att följa körnings kontexten.

Azure återställnings tider-TraceX visar en lista över system kontexterna till vänster i visningen.
Händelser som inträffar i en viss kontext visas på den vågräta linjen till höger om kontexten. På så sätt kan användaren enkelt se vilken kontext händelsen har inträffat samt följa den kontext linjen för att se alla händelser som inträffat i en viss kontext.

![System sammanfattnings rad](./media/user-guide/screen_shot_32.png)

**System sammanfattnings rad**

De första två kontext posterna är alltid "avbrotts" och "initiera/inaktive"-kontexter. Kontexten "avbrott" representerar alla system händelser som har gjorts från avbrotts tjänst rutiner (ISR: er). Kontexten "initiera/passiv" representerar två kontexter i Azure återställnings tider ThreadX. Händelser som inträffar under tx_application_define är "initiera" händelser och visas i kontexten "initiera/inaktiv". Om systemet är inaktivt och inga händelser inträffar, visas det gröna fältet som representerar "körs" i vyn tid på kontexten "initiera/inaktiv".

## <a name="methods-of-navigation"></a>Navigerings metoder

Med Azure återställnings tider TraceX kan utvecklaren ange hur navigerings knapparna "Nästa" och "föregående" ska användas.

![Navigerings knappar](./media/user-guide/event.png)

Om "event" är markerat görs navigeringen på nästa/föregående händelse. Om "context" är markerat görs navigeringen på nästa/föregående-händelse i samma kontext. Om du väljer "objekt" görs navigering på nästa/föregående händelse av det aktuella objektet, t. ex. händelser som är associerade med en viss kö. Om "växlar" är markerat görs navigeringen på nästa/föregående kontext växel. Om du väljer samma ID görs navigeringen på nästa/föregående händelse för samma händelse-ID.

### <a name="event-information-display"></a>Visning av händelse information

Azure återställnings tider TraceX innehåller detaljerad information om vissa 300-händelser. Dessa omfattar sex interna Azure återställnings tider ThreadX-händelser, två ISR-händelser (retur och exit), 14 interna Azure återställnings tider FileX-händelser, 42 interna Azure återställnings tider NetX-händelser och en användardefinierad händelse. Återstående händelser motsvarar direkt till Azure återställnings tider-ThreadX, Azure återställnings tider-FileX och Azure återställnings tider NetX API-tjänster.
Oavsett om visnings läget sekventiellt eller tiden är markerat visas detaljerad händelse information i händelse av en mus på valfri händelse i visnings ytan. Mus för händelse 494 i demonstrationen demo_threadx. trx spårnings fil visas här:

![Mouse-Over visar mer information](./media/user-guide/screen_shot_37.png)

**Mus över visar mer information**

Varje händelse som visas innehåller standard information om kontext och både relativ tid och tidstämpel. Kontext fältet visar vilken kontext händelsen ägde rum i. Det finns exakt fyra kontexter: tråd, inaktivitet, ISR och initiering. När en händelse inträffar i en tråd kontext samlas tråd namnet och dess prioritet vid tidpunkten och visas som ovan. Den relativa tiden visar det relativa antalet timer-Tick från början av spårningen. Tidsstämpeln för rå data visar händelsens råa tids källa. Slutligen visas all information som är speciell för händelsen.

### <a name="zooming-in-and-out"></a>Zooma in och ut

Som standard visar Azure återställnings tider TraceX händelser i en lättläst storlek med en 1:1 pixel: Tick-mappning. Användaren kan zooma in eller ut efter behov. Att zooma ut till 100% är användbart för att se hela spårningen i den aktuella visnings vyn, medan zoomning i är användbart i villkor där händelserna överlappar på grund av upplösningen för tids stämplings källan.

![Zoom-Out till 100% Visa eller zooma in för mer information](./media/user-guide/screen_shot_41.png)

**Zooma ut till 100% Visa eller zooma in för mer information**

När du zoomar ut med 100% – visar hela spårningen på den aktuella visnings sidan – det är enkelt att se all kontext körning som fångats in i spårningen samt de allmänna händelser som inträffar i dessa sammanhang. Observera att "tråd 1" och "tråd 2" körs oftast. De blå färgning för deras händelser innebär också att de här trådarna gör Queue Service-anrop (köa händelser är blå i färg).

Att återställa till en hel ikonvy är lika enkelt. Antingen kan du välja knappen Zooma in flera gånger eller så kan en viss faktor på 100 anges.

### <a name="delta-ticks-between-events"></a>Delta-Tick mellan händelser

Det är enkelt att fastställa antalet Tick mellan olika händelser i Azure återställnings tider TraceX genom att klicka på Start händelsen och dra musen till avslutande händelse.
Delta antalet Tick mellan händelserna visas i det övre högra hörnet av skärmen.

![Delta-Tick](./media/user-guide/screen_shot_42.png)

**Delta-Tick**

Delta-skalstrecken visar att 5032 Tick har förflutit mellan händelse 494 och händelse 496. Detta kan också beräknas manuellt genom att titta på de relativa tidsstämplar i varje händelse och subtraktion, men det är enkelt och momentant att använda det grafiska användar gränssnittet.

### <a name="priority-inversions"></a>Prioritets version

Azure återställnings tider TraceX visar automatiskt de prioritets versioner som identifieras i spårnings filen. Prioritets versioner definieras som villkor där en tråd med högre prioritet blockeras försöker erhålla en mutex som för närvarande ägs av en tråd med lägre prioritet. Det här villkoret kallas "deterministisk", eftersom systemet var konfigurerat för att köras på det här sättet. För att informera användaren visar Azure återställnings tider TraceX "deterministiska" prioritets versions intervall som en ljus lax färg.

Azure återställnings tider TraceX visar också "icke-deterministisk" prioritets versioner. De här prioritets versionerna skiljer sig från de "deterministiska" prioritets versionerna i att en annan tråd av en annan prioritets nivå har körts i mitten av vad som var en "deterministisk" prioritets version, vilket gör tiden inom prioriteten inversion lite "icke-deterministisk". Det här tillståndet är ofta okänt för användaren och kan vara mycket allvarligt. För att varna användaren om detta villkor visar Azure återställnings tider TraceX "icke-deterministisk" prioritets version som en lysande lax-färg.

![Inversion av deterministisk och icke-deterministisk prioritet](./media/user-guide/screen_shot_43.png)

**Inversion av deterministisk och icke-deterministisk prioritet**

### <a name="execution-profile"></a>Körnings profil

Azure återställnings tider TraceX innehåller en inbyggd körnings profil rapport för alla körnings kontexter inom den aktuella inlästa spårnings filen.

![Körnings profil](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Prestanda statistik

Azure återställnings tider TraceX innehåller en inbyggd prestanda statistik rapport för den aktuella inlästa spårnings filen.

![Prestanda statistik](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>Användning av tråds Tacken

Azure återställnings tider TraceX innehåller en inbyggd stack användnings rapport för alla trådar som körs i den aktuella inlästa spårnings filen.

![Stack användning](./media/user-guide/thread_stack_usage.png)

Azure återställnings tider TraceX visar Azure-återställnings tider FileX prestanda statistik för den aktuella inlästa spårnings filen. Den här informationen visas för hela systemet – på alla öppna medie objekt.

![FileX-statistik](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Statistik för Azure återställnings tider-NetX

Azure återställnings tider-TraceX visar också NetX prestanda statistik för den aktuella inlästa spårnings filen. Den här informationen visas för hela systemet.

![NetX-statistik](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>Rå stackdump

Azure återställnings tider TraceX kan bygga en spårnings fil i text format och starta anteckningar för att visa den.

![Rå stackdump](./media/user-guide/raw_trace_dump.png)

Observera att alla tids gränser och storleks värden i listan är uppskattningar och kan skilja sig från din utvecklings plattform.
