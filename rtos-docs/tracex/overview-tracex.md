---
title: Förstå Azure RTOS TraceX
description: Azure RTOS TraceX är Microsofts värdbaserade analysverktyg som ger utvecklare en grafisk vy över systemhändelser i realtid och gör det möjligt för dem att visualisera och bättre förstå beteendet för deras realtidssystem.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 966f3be5ebe34e006067175e422480fbf1ab664bb0ff627d7b01e71036dc5e82
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792225"
---
# <a name="overview-of-azure-rtos-tracex"></a>Översikt över Azure RTOS TraceX

Azure RTOS TraceX är Microsofts värdbaserade analysverktyg som ger utvecklare en grafisk vy över systemhändelser i realtid och gör det möjligt för dem att visualisera och bättre förstå beteendet för deras realtidssystem. Med Azure RTOS TraceX kan utvecklare tydligt se förekomsten av systemhändelser som avbrott och kontextväxlar som sker utanför standardverktygen för felsökning. Möjligheten att identifiera och studera dessa händelser och fastställa tidpunkten för deras förekomst i kontexten för det övergripande systemets drift gör det möjligt för utvecklare att lösa programmeringsproblem genom att hitta oväntat beteende och låta dem undersöka specifika områden ytterligare Spårningsinformation lagras i en buffert i målsystemet, där buffertplatsen och storleken bestäms av programmet vid körning. Azure RTOS TraceX kan bearbeta alla buffertar som konstrueras på rätt sätt, inte bara från Azure RTOS ThreadX, utan även från alla program eller RTOS. Spårningsinformationen kan laddas upp till värden för analys när som helst – antingen efter en brytning eller vid en brytpunkt. Azure RTOS ThreadX implementerar en cirkulär buffert som gör att de senaste "N"-händelserna kan inspekteras i händelse av systemfel eller andra betydande händelser.

![Azure RTOS TraceXSingle-Core visning](./media/user-guide/screen_shot_33.png)

**TraceXSingle-Core visning**

## <a name="key-capabilites"></a>Viktiga funktioner

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Azure RTOS inbyggd systemanalys för TraceX

Azure RTOS TraceX innehåller inbyggda systemanalysrapporter som är tillgängliga via ett enda knapptryck från TraceX-verktygsfältet. Dessa knappar och rapporter är:

![Generera körningsprofilrapport](./media/overview-tracex/execution-profile-report-button.jpg) Generera körningsprofilrapport

![Generera prestandastatistikrapport](./media/overview-tracex/performance-statistics-report-button.jpg) Generera prestandastatistikrapport

![Generera användningsrapport för trådstack](./media/overview-tracex/thread-stack-usage-report-button.jpg) Generera användningsrapport för trådstack

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Spårningsdata som samlas in av Azure RTOS ThreadX

Azure RTOS TraceX är utformat för att fungera med Azure RTOS ThreadX, som skapar en databas med system- och programhändelser på målsystemet under körning. Dessa händelser omfattar:

* trådkontextväxlar
* preemptions
* Suspensioner
* Avslutningar
* systemavbrott
* programspecifika händelser
* alla Azure RTOS ThreadX API-anrop
* alla Azure RTOS NetX API-anrop
* alla Azure RTOS FileX API-anrop
* alla Azure RTOS USBX API-anrop
* programdefinierade ikoner och information

Händelser loggas under programkontroll, med tidsstämplar och aktiv trådidentifiering så att de kan visas senare i rätt tidssekvens och associeras med lämplig tråd. Händelseloggning kan stoppas och startas om av programmet dynamiskt, till exempel när ett intresseområde påträffas. På så sätt undviker du oreda i databasen och använder upp målminnet när systemet fungerar som det ska.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Azure RTOS TraceX är som en logikanalys för programvara

När händelseloggen har laddats upp från målminnet till värden visar Azure RTOS TraceX händelserna grafiskt på en vågrät axel som representerar tid, med de olika programtrådar och systemrutiner som händelserna är relaterade till listade längs den lodräta axeln. Azure RTOS TraceX skapar ett "logikanalysverktyg för programvara" på värden, vilket gör systemhändelser synliga. Händelser representeras av färgkodade ikoner, som finns vid tidpunkten för händelsen längs den vågräta tidslinjen, till höger om relevant tråd eller systemrutin. När en händelseikon väljs visas motsvarande information för händelsen, samt information för de två föregående och två efterföljande händelserna. Detta ger snabb åtkomst med enkelklickning till den mest omedelbara informationen om händelsen och dess direkt omgivande händelser. Azure RTOS TraceX innehåller en "Sammanfattning"-skärm som visar alla systemhändelser på en enda vågrät linje för att förenkla analysen av system med många trådar.

### <a name="sequential-view-mode"></a>Sekventiellt visningsläge

Det sekventiella visningsläget väljs genom att klicka på fliken Sekventiell vy. Det här är standardläget. I det här läget visas händelser direkt efter varandra, oavsett tiden mellan dem. Observera även linjalen ovanför visningsområdet. Det visar det relativa händelsenumret från början av spårningen. Det här läget är standardläget och är särskilt användbart för att få en bra översikt över vad som händer i systemet.

![Sekventiellt visningsläge](./media/user-guide/screen_shot_10.png)

**Sekventiellt visningsläge**

### <a name="time-view-mode"></a>Tidsvisningsläge

I det här läget visas händelser i ett relativt tidsläge, där en heldragen grön stapel används för att visa körning mellan händelser. Det här läget är särskilt användbart för att se var den största delen av bearbetningen sker i systemet, vilket kan hjälpa utvecklare att finjustera systemet för bättre prestanda och/eller svarstider.

Observera även linjalen ovanför händelsevisningen. Den här linjalen visar relativa tick från början av spårningen, som härleds från tidsstämpeln som instrumenterades i händelsespårningsloggningen inuti Azure RTOS ThreadX. Om tidsstämplarna är för nära varandra (timer med låg frekvens) körs händelserna tillsammans. Om tidsstämplarna däremot är för långt ifrån varandra (timer med hög frekvens) är händelserna för långt ifrån varandra. Att välja rätt tidsstämpel för frekvens är viktigt när det gäller att göra tidsre relativa vyn meningsfull.

![Tidsvisningsläge](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>Systemsammanfattningsrad

Azure RTOS TraceX innehåller också en enda sammanfattningsrad som innehåller alla händelser på samma rad. Sammanfattningsraden innehåller en sammanfattning av kontexten samt motsvarande händelsesammanfattning under. Detta gör det enkelt att se en översikt över ett komplext system. Sammanfattningsfältet är särskilt användbart i system som har ett stort antal trådar. Utan en sådan sammanfattningsrad skulle användaren behöva följa komplexa systeminteraktioner med hjälp av den lodräta rullningslisten för att följa körningskontexten.

Azure RTOS TraceX visar en lista över systemkontexterna till vänster på skärmen.
Händelser som inträffar i en viss kontext visas på den vågräta linjen till höger om den kontexten. På så sätt kan användaren enkelt fastställa vilken kontext händelsen inträffade och följa den kontextraden för att se alla händelser som inträffade i en viss kontext.

![Systemsammanfattningsrad](./media/user-guide/screen_shot_32.png)

**Systemsammanfattningsrad**

De första två kontextposterna är alltid kontexterna "Avbrott" och "Initiera/inaktiv". Kontexten "Avbrott" representerar alla systemhändelser som görs från ISR(Interrupt Service Routines). Kontexten "Initiera/inaktiv" representerar två kontexter i Azure RTOS ThreadX. Händelser som inträffar tx_application_define, är "Initiera" händelser och visas i kontexten "Initiera/inaktiv". Om systemet är inaktivt och därför inte inträffar ritas den gröna stapeln som representerar "Körs" i tidsvyn i kontexten "Initiera/inaktiv".

## <a name="methods-of-navigation"></a>Navigeringsmetoder

Azure RTOS TraceX gör att utvecklaren kan ange hur navigeringsknapparna "Nästa" och "Föregående" fungerar.

![Navigeringsknappar](./media/user-guide/event.png)

Om "Händelse" har valts görs navigeringen vid nästa/föregående händelse. Om "Kontext" har valts görs navigeringen i nästa/föregående händelse i samma kontext. Om "Objekt" har valts görs navigeringen vid nästa/föregående händelse för det aktuella objektet, t.ex. händelser som är associerade med en specifik kö. Om "Växlar" är markerat görs navigeringen på nästa/föregående kontextväxel. Om "Samma ID" har valts görs navigeringen i nästa/föregående händelse för samma händelse-ID.

### <a name="event-information-display"></a>Visning av händelseinformation

Azure RTOS TraceX innehåller detaljerad information om cirka 300 händelser. Dessa omfattar sex interna Azure RTOS ThreadX-händelser, två ISR-händelser (enter och exit), 14 interna Azure RTOS FileX-händelser, 42 interna Azure RTOS NetX-händelser och en användardefinierad händelse. De återstående händelserna motsvarar direkt Azure RTOS ThreadX, Azure RTOS FileX och Azure RTOS NetX API-tjänster.
Oavsett om sekventiellt läge eller tidsvisningsläge har valts, resulterar en muspekar över en händelse i visningsområdet i detaljerad händelseinformation som visas nära händelsen. Muspekaren över händelse 494 i demonstrationsfilen demo_threadx.trx visas här:

![Mouse-Over visar mer information](./media/user-guide/screen_shot_37.png)

**Muspekaren visar mer information**

Varje händelse som visas innehåller standardinformation om Kontext och både relativ tid och tidsstämpel. Fältet Kontext visar vilken kontext händelsen ägde rum i. Det finns exakt fyra kontexter: tråd, inaktivitet, ISR och initiering. När en händelse äger rum i en trådkontext samlas trådnamnet och dess prioritet vid den tidpunkten in och visas enligt ovan. Relativ tid visar det relativa antalet timer tick från början av spårningen. Råtidsstämpeln visar raw-tidskällan för händelsen. Slutligen visas all händelsespecifik information.

### <a name="zooming-in-and-out"></a>Zooma in och ut

Som standard Azure RTOS TraceX händelserna i en storlek som är enkel att visa, med mappningen 1:1 pixel:tick. Användaren kan zooma in eller zooma ut efter behov. Att zooma ut till 100 % är användbart för att se hela spårningen i den aktuella visningsvyn, medan zoomning är användbart i förhållanden där händelserna överlappar på grund av tidsstämpelkällans upplösning.

![Zoom-Out till 100 % visa eller zooma in för information](./media/user-guide/screen_shot_41.png)

**Zooma ut till 100 % vy eller zooma in för mer information**

När du zoomar ut med 100 % – visar hela spårningen på den aktuella visningssidan – är det enkelt att se alla kontextkörningar som fångats in i spårningen samt de allmänna händelser som inträffar i dessa kontexter. Observera att "tråd 1" och "tråd 2" körs oftast. Den blå färgen för deras händelser tyder också på att dessa trådar gör kötjänstanrop (köhändelser är blå i färg).

Det är lika enkelt att återställa till en fullständig ikonvy. Zoomningsknappen kan antingen väljas upprepade gånger eller så kan någon faktor på 100 anges.

### <a name="delta-ticks-between-events"></a>Delta tickar mellan händelser

Det är enkelt att fastställa antalet tick mellan olika händelser Azure RTOS TraceX. Klicka bara på starthändelsen och dra musen till sluthändelsen.
Deltaantalet tick mellan händelserna visas i det övre högra hörnet på skärmen.

![Delta tick](./media/user-guide/screen_shot_42.png)

**Delta tick**

Delta tick visar att 5032 tick har förflutit mellan händelse 494 och händelse 496. Detta kan också beräknas manuellt genom att titta på de relativa tidsstämplarna i varje händelse och subtrahera, men det är enkelt och omedelbart att använda det grafiska användargränssnittet.

### <a name="priority-inversions"></a>Prioritetsinversioner

Azure RTOS TraceX visar automatiskt prioritetsinversioner som identifierats i spårningsfilen. Prioritetsinversioner definieras som villkor där en tråd med högre prioritet blockeras och försöker hämta en mutex som för närvarande ägs av en tråd med lägre prioritet. Det här villkoret kallas "deterministiskt" eftersom systemet konfigurerades för att fungera på det här sättet. För att informera användaren visar Azure RTOS TraceX "deterministiska" prioritetsintervall för inversion som en ljus färg.

Azure RTOS TraceX visar även "icke-deterministiska" prioritetsinversioner. Dessa prioritetsinversioner skiljer sig från de "deterministiska" prioritetsinversionerna på så sätt att en annan tråd på en annan prioritetsnivå har körts mitt i det som var en "deterministisk" prioritetsinversion, vilket gör tiden inom prioritetsinversionen något "o deterministisk". Det här tillståndet är ofta okänt för användaren och kan vara mycket allvarligt. För att varna användaren om det här villkoret visar Azure RTOS TraceX "icke-deterministiska" prioritetsinversioner som en ljusare färg.

![Deterministisk och icke-deterministisk prioritetsinversion](./media/user-guide/screen_shot_43.png)

**Deterministisk och icke-deterministisk prioritetsinversion**

### <a name="execution-profile"></a>Körningsprofil

Azure RTOS TraceX innehåller en inbyggd körningsprofilrapport för alla körningskontexter i den för tillfället inlästa spårningsfilen.

![Körningsprofil](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Prestandastatistik

Azure RTOS TraceX innehåller en inbyggd prestandastatistikrapport för den aktuella inlästa spårningsfilen.

![Prestandastatistik](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>Användning av trådstack

Azure RTOS TraceX innehåller en inbyggd stackanvändningsrapport för alla trådar som körs i den inlästa spårningsfilen.

![Stackanvändning](./media/user-guide/thread_stack_usage.png)

Azure RTOS TraceX visar prestandastatistik Azure RTOS FileX för den aktuella inlästa spårningsfilen. Den här informationen visas för hela systemet – för alla medieobjekt som har öppnats.

![FileX-statistik](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Azure RTOS NetX-statistik

Azure RTOS TraceX visar även NetX-prestandastatistik för den aktuella inlästa spårningsfilen. Den här informationen visas för hela systemet.

![NetX-statistik](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>Råspårningsdump

Azure RTOS TraceX kan skapa en råspårningsfil i textformat och starta Anteckningar för att visa den.

![Råspårningsdump](./media/user-guide/raw_trace_dump.png)

Observera att alla siffror för tidsinställning och storlek som anges är uppskattningar och kan vara olika på din utvecklingsplattform
