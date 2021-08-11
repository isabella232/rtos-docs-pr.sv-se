---
title: Kapitel 3 – Beskrivning Azure RTOS TraceX
description: I det här kapitlet beskrivs de övergripande funktionerna i Azure RTOS TraceX-systemanalysverktyget, inklusive den övergripande funktionaliteten i dess grafiska användargränssnitt.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: bb466427374659027bf91c7bb46c74e7d2ff561d200db9dab1a2bddbe6635ef4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789536"
---
# <a name="chapter-3---description-of-azure-rtos-tracex"></a>Kapitel 3 – Beskrivning Azure RTOS TraceX

I det här kapitlet beskrivs de övergripande funktionerna i Azure RTOS TraceX-systemanalysverktyget, inklusive den övergripande funktionaliteten i dess grafiska användargränssnitt. 

## <a name="display-overview"></a>Visa översikt

**Bild 4** visar huvudfönstret för spårningssystemets analysverktyg. Layouten är enkel – körningskontexterna representeras av de lodräta elementen till vänster. Det kan till exempel vara initiering, avbrott, inaktivitet och de olika trådposterna. De händelser som äger rum i varje kontext visas vågrätt på samma kontextlinje. QR-händelserna **nedan visar** till exempel att tråd **_2_ _ gör efterföljande *anrop till _*_tx_queue_receive_**.

![Skärmbild av huvudfönstret för traceX-systemanalysverktyget.](./media/user-guide/screen_shot_10.png)


**BILD 5**

Kontextändringar representeras av de lodräta svarta linjer som ansluter kontextlinjerna. Den markerade händelsen representeras av en heldragen röd lodrät linje. I det här exemplet väljs händelse 494.

## <a name="title-bar"></a>Namnlist

Namnlisten TraceX innehåller flera typer av användbar information. Först är den aktuella versionen av TraceX. Det andra är den fullständiga sökvägen till den spårningsfil som är öppen för tillfället. Exemplet i bild **6** visar **_TraceX_*_ version _*_6.0.0_ _ visar spårningsfilen *_*_demo_threadx.trx._**

![Skärmbild av namnlisten TraceX.](./media/user-guide/screen_shot_11.png)

**BILD 6**

## <a name="tool-bar"></a>Verktygsfält

TraceX-verktygsfältet innehåller flera knappar för att öppna spårningsfiler och kontrollelement på skärmen.

![Skärmbild av TraceX-verktygsfältet.](./media/user-guide/screen_shot_12.png)


**BILD 7**

Knapparna i TraceX-verktygsfältet, från vänster till höger, definieras på följande sätt:
                                             
| **Knappen**                         | **Funktion** |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![Knappen Öppna spårningsfil](./media/user-guide/screen_shot_13.png)      | Öppna en spårningsfil |
| ![Knappen Öppna användarhandboken](./media/user-guide/screen_shot_14.png)      | Öppna den här användarhandboken |
| ![Knappen Generera körningsprofil](./media/user-guide/screen_shot_15.png)       | Generera körningsprofil |
| ![ Knappen Generera prestandastatistik](./media/user-guide/screen_shot_16.png)       | Generera prestandastatistik |
| ![Knappen Generera användning av trådstack](./media/user-guide/screen_shot_17.png)       | Generera användning av trådstack |
| ![Knappen Visa vald händelse](./media/user-guide/screen_shot_18.png)       | Visa aktuell vald händelse |
| ![Sökknapp](./media/user-guide/screen_shot_19.png)      | Söka efter händelser |
| ![Knappen Zooma in](./media/user-guide/screen_shot_20.png)      | Zooma in. |
| ![Knappen Visa zoomning](./media/user-guide/screen_shot_21.png)      | Välj procentandel av zoomning, där 100 % innebär att hela spårningsfilen visas i den aktuella vyn. |
| ![Knappen Zooma ut](./media/user-guide/screen_shot_22.png)      | Zooma ut. |
| ![Välj knappen Första händelsen](./media/user-guide/screen_shot_23.png)      | Välj första händelsen. |
| ![Knappen Visa föregående händelsesida](./media/user-guide/screen_shot_24.png)      | Visa föregående händelsesida. |
| ![Knappen Visa föregående händelse](./media/user-guide/screen_shot_25.png)      | Visa föregående händelse. |
| ![Nästa/föregående navigeringsknapp](./media/user-guide/screen_shot_26.png)      | Fastställ hur nästa/föregående navigeringsknappar fungerar. Om ***Händelse** _ har valts, sker navigeringen vid nästa/föregående händelse. Om _*_Kontext_*_ har valts sker navigeringen vid nästa/föregående händelse i den angivna kontexten. Om _*_Objekt_*_ har valts sker navigeringen i nästa/föregående händelse för det angivna objektet. Det kan till exempel vara händelser som är associerade med en specifik kö. Om _*_Växlar har_*_ valts sker navigeringen vid nästa/föregående ändring i kontexten. Om _ *_ID_** har valts sker navigeringen vid nästa/föregående händelse för det angivna händelse-ID:t. |
| ![Knappen Visa nästa händelse](./media/user-guide/screen_shot_27.png)      | Visa nästa händelse. |
| ![Knappen Visa nästa händelsesida](./media/user-guide/screen_shot_28.png)      | Visa nästa händelsesida. |
| ![Knappen Välj senaste händelse](./media/user-guide/screen_shot_29.png)      | Välj senaste händelse. |

## <a name="display-mode-tabs"></a>Flikar i visningsläge

TraceX visar systemhändelser på två olika sätt: *sekventiell och* *relativ tid.* Standardläget är sekventiellt och det är det läge som visas **i bild 8.**

Att ändra läget är lika enkelt som att välja flikarna ***Sekventiell** vy _ _*_eller Tidsvy_*_ i TraceX-fönstret. _*Bild 8** visar flikarna **_Sekventiell_*_ vy och _ *_Tidsvy_** .

![Skärmbild av flikarna Sekventiell vy och Tidsvy.](./media/user-guide/screen_shot_30.png)

**BILD 8**

## <a name="sequential-view-mode"></a>Läge för sekventiell vy

Det sekventiella visningsläget väljs av fliken ***Sekventiell** vy _ som visas i _*bild 8**. Det är standardläget. I det här läget visas händelser im.. /mediately följa varandra, oavsett förfluten tid mellan dem. Observera även linjalen ovanför visningsområdet i **bild 8.** Det visar det relativa händelsenumret från början av spårningen.

Det här läget är standardläget och är användbart för att få en bra översikt över vad som händer i systemet.

## <a name="time-view-mode"></a>Tidsvisningsläge

Tidsvisningsläget väljs med knappen ***Tidsvy** _ . _ *Bild 9** visar samma händelsespårning som **bild 8 förutom** i tidsvisningsläge. I det här läget visas händelser på ett relativt tids relativt sätt, där den heldragna gröna stapeln används för att visa körningen mellan händelser. Det här läget är användbart för att se var den största delen av bearbetningen sker i systemet, vilket kan hjälpa utvecklare att finjustera sina system för bättre prestanda och/eller svarstider.

![Skärmbild av fliken Tidsvy.](./media/user-guide/screen_shot_31.png)

**BILD 9**

Observera även linjalen ovanför händelsevisningen i **bild 9.** Den här linjalen visar relativa tick från början av spårningen, som härleds från tidsstämpeln som instrumenterades i händelsespårningsloggningen i ThreadX. Om tidsstämplarna är för nära varandra (timer med låg frekvens) körs händelserna tillsammans. Om tidsstämplarna däremot är för långt ifrån varandra (timern med hög frekvens) är händelserna för långt ifrån varandra. Det är viktigt att välja rätt tidsstämpel för frekvens när det gäller att göra den relativa vyn meningsfull.

## <a name="system-summary-line"></a>Systemsammanfattningsrad

TraceX tillhandahåller också en enda sammanfattningsrad (den översta kontexten i bild **10**) som innehåller alla händelser på samma rad. Detta gör det enkelt att se en översikt över ett komplext system. Sammanfattningsfältet är särskilt användbart i system som har många trådar. Utan en sådan sammanfattningsrad skulle du behöva följa komplexa systeminteraktioner med hjälp av den lodräta rullningslisten för att följa körningskontexten.

![Skärmbild av systemsammanfattningsraden på fliken Sekventiell vy.](./media/user-guide/screen_shot_32.png)


**BILD 10**

Sammanfattningsraden innehåller en sammanfattning av kontexten samt motsvarande händelsesammanfattning under. I exemplet som visas **i bild 10** är det enkelt att se att **_tråd 2_*_ körs och avbryts. Avbrottet resulterar i avfasning av _*_tråd 3_**, ***tråd 6** _, tråd _*_4_*_ och _*_tråd 7_*_, varför _ *_tråd 2_** återupptar körningen.

## <a name="system-contexts"></a>Systemkontext

TraceX visar systemkontexterna till vänster på skärmen, som du ser i **bild 11**. Händelser som inträffar i en viss kontext visas på den vågräta linjen till höger om den kontexten. På så sätt kan du enkelt fastställa vilken kontext händelsen inträffade samt följa den kontextraden för att se alla händelser som inträffade i en viss kontext.

De första kontextposterna för tow är alltid **kontexterna*** Interrupt _ _*_och Initialize/Idle._*_ _*_Avbrottskontext_*_ representerar alla systemhändelser som görs från IRS (Interrupt Service Routines). _*_Initiera/inaktiv kontext_*_ representerar två kontexter i ThreadX. Händelser som inträffar _*_under tx_application_define_*_, är _*_Initialize/Idle context (Initiera/inaktiv_*_ kontext). Om systemet är inaktivt och därför inte inträffar, ritas den gröna stapeln som representerar Körs i tidsvyn i kontexten _ *_Initiera/inaktiv_** . _**_

![Skärmbild av systemkontexterna till vänster på skärmen.](./media/user-guide/screen_shot_33.png)

**BILD 11**

I exemplet i bild **11** finns det nio trådkontexter, med början från **_systemtimertråden_*_ kontexten. Ytterligare information om en enskild kontext är tillgänglig genom att placera musen på den kontexten. Den ytterligare informationen omfattar trådens startstackadress, sista stackadress, total storlek, procent som används, relativ körningsprocent, antal stängningar, återupptaganden och högsta och lägsta prioritet under spårningen. _* Bild 12** visar information för **_tråd 0_**.

![Skärmbild av informationen för tråd 0.](./media/user-guide/screen_shot_34.png)


**BILD 12**

Kontexter kan också flyttas för att gruppera dem av större intresse. Detta åstadkoms genom att dra och släppa kontexten eller högerklicka på kontexten. Om du högerklickar på kontexten visas en dialogruta för att flytta kontexten högst upp eller längst ned. 

Om du väljer ***Flytta till** början _ så flyttas tråd _*_3-kontexten_*_ överst i kontextlistan, som du ser i _*bild 13**.

![Skärmbild av kontexten som flyttas överst i kontextlistan.](./media/user-guide/screen_shot_35.png)


**BILD 13**

## <a name="thread-status-information"></a>Information om trådstatus

När det här alternativet är aktiverat visar TraceX status för varje tråd via en färgad linje i trådens kontext. En grön linje indikerar att tråden är i tillståndet "klar", medan en linje med en annan färg indikerar att tråden har pausats. För pausade trådar anger färgen på raden vilken typ av ThreadX-objekt som tråden pausas på. I bild **13** visar till exempel den gröna linjen på systemtimertrådens _ kontext som börjar vid händelse ***147* att _ _System Timer Thread_ _ är *klar. Före händelse 147* och efter händelse 154 indikerar frånvaron av den gröna linjen att _ _System Timer Thread_ _ är *klar. Före händelse 147*** och efter händelse 154 indikerar frånvaron av den gröna linjen att systemtimertråden är pausad.

![Skärmbild av status för varje tråd via en färgad linje i trådens kontext.](./media/user-guide/screen_shot_36.png)

**BILD 14**

Det finns tre lägen för visning av trådstatus, som är tillgängliga via menyn ***Alternativ - > Statusrader** _ . Alternativet _*_Endast klar_*_ visar endast de redo (gröna) statusraderna, men inga statusrader för stängning visas. Det här är standardalternativet för TraceX. Med alternativet *__ Alla på_** kan du visa alla statusrader (redo och inaktiv).

Slutligen ***inaktiverar alternativet*** Alla av visningen av alla statusrader.

## <a name="event-information-display"></a>Visning av händelseinformation

TraceX innehåller detaljerad information om några 600 körningshändelser, inklusive ThreadX, FileX, NetX, NetX Duo och USBX API-anrop och interna händelser. TraceX stöder också upp till ytterligare 61 439 unika användardefinierade händelser.

Oavsett om sekventiellt läge eller tidsvisningsläge har valts, resulterar en muspekar över en händelse i visningsområdet i detaljerad händelseinformation som visas nära händelsen. Muspekaren över händelse 143 i demonstrationen ***demo_threadx.trx** _ trace-filen visas i _*bild 15**:

![Skärmbild av muspekaren över händelse 143 i en exempelspårningsfil](./media/user-guide/screen_shot_37.png)

**BILD 15**

Varje händelse som visas innehåller standardinformation om ***Context** _ och både den relativa _*_tids- och_*_ _*_tidsstämpeln_*_. Fältet Kontext visar vilken kontext händelsen ägde rum i. Det finns exakt fyra kontexter: tråd, inaktivitet, ISR och initiering. När en händelse äger rum i en trådkontext samlas trådnamnet och dess prioritet vid den tidpunkten in och visas enligt ovan. Relativ _*_tid visar_*_ det relativa antalet timer tick från början av spårningen. _ *_Raw-tidsstämpeln_** visar raw-tidskällan för händelsen. Slutligen visas all händelsespecifik information. Den här informationen beskrivs i resten av det här kapitlet.

Detaljerad händelseinformation är också tillgänglig genom att dubbelklicka på en händelse. Dubbelklicka på händelse 143 på **bild 16:**

![Skärmbild av detaljerad händelseinformation när en händelse dubbelklickas.](./media/user-guide/screen_shot_38.png)

**BILD 16**

Att kunna visa flera händelser samtidigt ger användaren en mycket mer omfattande bild av vad som hände. Det är ganska användbart att se dem sida vid sida eftersom många händelser är relaterade till varandra. Detta åstadkoms genom att dubbelklicka på flera händelser.

## <a name="current-event-display"></a>Aktuell händelsevisning

TraceX visar den aktuella händelsen, i ett separat fönster, när den väljs av användaren via ***Visa -> Aktuell händelse*** eller genom att klicka på den aktuella händelseknappen i verktygsfältet. När du har valt det här alternativet visar TraceX den valda händelsen i ett fristående fönster och uppdaterar det här fönstret när en annan händelse väljs.

## <a name="event-searching"></a>Händelsesökning

TraceX har en omfattande sökfunktion för händelser. Händelse-ID:t och informationsfälten för varje händelse är de primära sökparametrarna. Om du inte anger ett värde för en sökparameter innebär det att parametern effektivt tar bort parametern från sökningen. Dessutom kan sökningen göras så att alla parametrar som hittas uppfyller sökningen, eller så måste alla parametrar hittas för att uppfylla sökningen. Sökningen kan också begränsas till en viss kontext eller omfatta alla kontexter i spårningen. Du kan använda händelsesökningen genom att välja knappen ***Sök** efter värde _ i verktygsfältet, som du ser _i *bild 17**. När du väljer sökdialogrutan visas, som anger alla parametrar för sökningen. Knapparna **_Nästa_*_ _*_och Föregående_*_ i sökdialogrutan kan sedan användas för att hitta nästa och tidigare händelser som matchar de angivna sökvillkoren. _ *Bild 17** visar sökdialogrutan.

![Skärmbild av händelsesökningen.](./media/user-guide/screen_shot_39.png)

**BILD 17**

![Skärmbild av sökdialogrutan.](./media/user-guide/screen_shot_40.png)

**BILD 18**

## <a name="zooming-in-and-out"></a>Zooma in och ut

Som standard visar TraceX händelserna i full storlek. Du kan zooma in eller zooma ut efter behov. Att zooma ut är användbart för att se de övergripande händelserna som fångas in i spårningen, medan zoomning är användbart i förhållanden där händelserna överlappar på grund av tidsstämpelkällans upplösning. **Bild 19** visar **_demo_threadx.trx-filen_** zoomas ut så att 100 % av spårningsfilen visas.

![Skärmbild av en exempelfil som zoomats ut så att 100 % av spårningsfilen visas.](./media/user-guide/screen_shot_41.png)

**BILD 19**

När du har zoomat ut 100 % för att visa hela spårningen på den aktuella visningssidan är det enkelt att se all kontextkörning som fångats in i spårningen samt de allmänna händelser som inträffar i dessa kontexter. Observera i **bild 16** **_att tråd 1_*_ och _*_tråd 2_** körs oftast. Den blå färgen för deras händelser tyder också på att dessa trådar gör kötjänstanrop (köhändelser är blå i färg).

Det är lika enkelt att återställa till en fullständig ikonvy. Zoomningsknappen kan väljas upprepade gånger eller så kan du ange någon faktor på 100.

## <a name="delta-ticks-between-events"></a>Delta tick mellan händelser

Det är enkelt att fastställa antalet tick mellan olika händelser i TraceX – klicka på starthändelsen och dra musen till sluthändelsen. Deltaantalet tick mellan händelserna visas i det övre högra hörnet på skärmen, som du ser **i bild 17**.

![Skärmbild av deltaantalet tick mellan händelserna.](./media/user-guide/screen_shot_42.png)

**BILD 17**

Deltat tick som visas i bild **17** visar att 5032 tick har förflutit mellan händelse 125 och händelse 154. Detta kan också beräknas manuellt genom att titta på relativa tidsstämplar i varje händelse och subtrahera, men det är enkelt och omedelbart att använda det grafiska användargränssnittet.

## <a name="actual-time-display"></a>Visning av faktisk tid

När det här alternativet är aktiverat visar TraceX den faktiska tiden i mikrosekunder i ***** Tidsvy _ och för den olika deltatidsinformation som visas av TraceX. Som standard är den faktiska tidsvisningen inaktiverad. För att aktivera den faktiska tidsvisningen måste antalet tick per mikrosekunder anges via menyvalet _ *_Options -> Ticks per Microsecond_** (värdet som ska anges bestäms av den maskinvarutimerkälla som används för TraceX-händelseloggning på målet).

## <a name="priority-inversions"></a>Prioritetsinversioner

TraceX visar automatiskt prioritetsinversioner som identifierats i spårningsfilen. Prioritetsinversioner definieras som villkor där en tråd med högre prioritet blockeras och försöker hämta en mutex som för närvarande ägs av en tråd med lägre prioritet. Det här villkoret kallas *deterministiskt* eftersom systemet har ställts in för att fungera på det här sättet. För att informera användaren visar TraceX *deterministiska prioritetsintervall* för inversion som en ljus färg.

TraceX visar även *icke-deterministiska* prioritetsinversioner. Dessa prioritetsinversioner skiljer sig från *deterministiska* prioritetsinversioner på så sätt att en annan tråd på en annan prioritetsnivå har körts mitt i det som var en *deterministisk* prioritetsinversion, vilket gör tiden inom prioritetsinversion något *icke-deterministisk*. Det här tillståndet är ofta okänt för användaren och kan vara mycket allvarligt. För att varna användaren om det här villkoret visar TraceX *icke-deterministiska* prioritetsinversioner som en ljusare färg. **Bild 18 visar** både *deterministiska och* *icke-deterministiska* prioritetsinversioner.

![Skärmbild av prioritetsinversion i en spårningsfil.](./media/user-guide/screen_shot_43.png)

**BILD 18**

**Bild 18 visar** en *deterministisk* prioritetsinversion från händelse 398 till händelse 402. I det här intervallet är blocken med högre prioritet ***0** _ på en mutex som ägs av en tråd med lägre _*_prioritet 1_*_. Vid händelse 402 släpper _ *_tråd 1_** mutex och avslutar därför prioritetsinversionen.

Det ljusare skuggade området visar en *icke-deterministisk* prioritetsinversion mellan händelse 408 till händelse 420. Det som gör detta *icke-deterministiskt* är att även om * tråd **1** _ innehåller mutex som tråd med högre prioritet _*_0_*_ blockeras på, inträffar ett avbrott som återupptar _*_tråd 2_**, som sedan kör och förlänger tiden som systemet är i prioritetsinversion. Det här tillståndet kan vara ganska allvarligt och svårt att identifiera. Men med TraceX är det enkelt att identifiera.
