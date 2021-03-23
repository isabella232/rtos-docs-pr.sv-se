---
title: Kapitel 3 – Beskrivning av Azure återställnings tider TraceX
description: I det här kapitlet beskrivs de övergripande funktionerna i system analys verktyget för Azure återställnings tider-TraceX, inklusive de övergripande funktionerna i sitt användar gränssnitt.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1c974b353c92e0a3cf51c92818794197cf999582
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827624"
---
# <a name="chapter-3---description-of-azure-rtos-tracex"></a>Kapitel 3 – Beskrivning av Azure återställnings tider TraceX

I det här kapitlet beskrivs de övergripande funktionerna i system analys verktyget för Azure återställnings tider-TraceX, inklusive de övergripande funktionerna i sitt användar gränssnitt. 

## <a name="display-overview"></a>Visa översikt

**Bild 4** visar det huvudsakliga visnings fönstret i system analys verktyget TraceX. Layouten är enkel – körnings kontexterna representeras av de lodräta elementen på vänster sida. t. ex. initiering, avbrott, inaktivitet och de olika tråd posterna. De händelser som sker i varje kontext visas vågrätt på samma kontext linje. Till exempel visar **QR** -händelserna som visas nedan att **_tråd 2_*_ gör efterföljande anrop till _*_tx_queue_receive_**.

![Skärm bild av huvud fönstret för system analys verktyget TraceX.](./media/user-guide/screen_shot_10.png)


**FIGUR 5**

Kontext ändringar representeras av de lodräta svarta linjerna som ansluter kontext linjerna. Den för tillfället valda händelsen representeras av en heldragen röd lodrät linje. I det här exemplet är händelse 494 markerad.

## <a name="title-bar"></a>Namnlist

Namn listen TraceX innehåller flera delar av användbar information. Först är den aktuella versionen av TraceX. Andra är den fullständiga sökvägen till den nu öppna spårnings filen. Exemplet i **bild 6** visar **_TraceX_*_ version _*_6.0.0_*_ visar* spårnings filen _ _demo_threadx. trx_** .

![Skärm bild av TraceX namn List.](./media/user-guide/screen_shot_11.png)

**BILD 6**

## <a name="tool-bar"></a>Verktygsfältet

TraceX-verktygsfältet innehåller flera knappar för att öppna spårningsfiler och kontroll element i visningen.

![Skärm bild av TraceX-verktygsfältet.](./media/user-guide/screen_shot_12.png)


**FIGUR 7**

TraceX verktygsfälts knappar – från vänster till höger – definieras enligt följande:
                                             
| **Slutför**                         | **Funktion** |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![Knappen Öppna spårnings fil](./media/user-guide/screen_shot_13.png)      | Öppna en spårnings fil |
| ![Knappen Öppna användar guide](./media/user-guide/screen_shot_14.png)      | Öppna den här användar handboken |
| ![Knappen Skapa körnings profil](./media/user-guide/screen_shot_15.png)       | Skapa körnings profil |
| ![ Knappen generera prestanda statistik](./media/user-guide/screen_shot_16.png)       | Generera prestanda statistik |
| ![Knappen generera tråd Stacks användning](./media/user-guide/screen_shot_17.png)       | Generera användning av tråds tack |
| ![Visa markerad händelse knapp](./media/user-guide/screen_shot_18.png)       | Visa markerad händelse |
| ![Sökknapp](./media/user-guide/screen_shot_19.png)      | Sök efter händelser |
| ![Knappen Zooma in](./media/user-guide/screen_shot_20.png)      | Zooma in. |
| ![Visa zoomnings knapp](./media/user-guide/screen_shot_21.png)      | Välj procent andel av visnings zoomning, där 100% innebär att hela spårnings filen visas i den aktuella vyn. |
| ![Knappen Zooma ut](./media/user-guide/screen_shot_22.png)      | Zooma ut. |
| ![Knappen Välj första händelsen](./media/user-guide/screen_shot_23.png)      | Välj första händelsen. |
| ![Visa knappen för föregående händelse sida](./media/user-guide/screen_shot_24.png)      | Visa föregående händelse sida. |
| ![Visa föregående händelse knapp](./media/user-guide/screen_shot_25.png)      | Visa föregående händelse. |
| ![Nästa/föregående navigerings knapp](./media/user-guide/screen_shot_26.png)      | Bestäm hur nästa/föregående navigerings knappar ska användas. Om ***Event** _ är markerat görs navigeringen på nästa/föregående-händelse. Om du väljer _*_kontexten_*_ görs navigeringen på nästa/föregående-händelse i den angivna kontexten. Om _*_objektet_*_ är markerat görs navigeringen på nästa/föregående-händelse för det angivna objektet. t. ex. händelser som är associerade med en speciell kö. Om _*_växlar_*_ är markerat görs navigeringen vid nästa/föregående ändring i kontexten. Om _ *_ID_** är markerat görs navigeringen på nästa/föregående händelse av angivet händelse-ID. |
| ![Visa nästa händelse knapp](./media/user-guide/screen_shot_27.png)      | Visa nästa händelse. |
| ![Visa knappen Nästa händelse sida](./media/user-guide/screen_shot_28.png)      | Visa nästa händelse sida. |
| ![Välj knappen senaste händelse](./media/user-guide/screen_shot_29.png)      | Välj sista händelsen. |

## <a name="display-mode-tabs"></a>Fliken visnings läge

TraceX visar system händelser på två olika sätt: *sekventiell* och *tid i förhållande* till varandra. Standard läget är sekventiellt och det är det läge som visas i **bild 8**.

Att ändra läget är lika enkelt som att välja fliken ***sekventiell vy** _ eller _*_tids visning_*_ i fönstret TraceX. _*Figur 8** visar **_sekventiell vy_*_ och _ *_Time View_** tabbar.

![Skärm bild av flikarna sekventiell vy och tids visning.](./media/user-guide/screen_shot_30.png)

**FIGUR 8**

## <a name="sequential-view-mode"></a>Sekventiellt visnings läge

Det sekventiella visnings läget väljs av ***sekventiell vy** _ TABB som visas i _ * bild 8 * *. Det är standardläget. I det här läget visas im-händelser... /mediately efter varandra, oavsett hur lång tid som förflutit. Observera också linjalen ovanför visnings ytan i **bild 8**. Det visar det relativa händelse numret från början av spåret.

Det här läget är standard läget och är användbart för att få en bra översikt över vad som händer i systemet.

## <a name="time-view-mode"></a>Tids visnings läge

Tids visnings läget väljs med knappen ***Time View** _. _ *Figur 9** visar samma händelse spårning som **figur 8** , förutom i tids visnings läge. I det här läget visas händelser i relativt tid, med det heldragna gröna fältet som används för att Visa körning mellan händelser. Det här läget är användbart för att se var bearbetningen sker i systemet, vilket kan hjälpa utvecklare att finjustera systemet för att få bättre prestanda och/eller svars tider.

![Skärm bild av fliken tids visning.](./media/user-guide/screen_shot_31.png)

**BILD 9**

Observera också linjalen ovanför händelsen som visas i **bild 9**. Den här linjalen visar relativa skal streck från början av spåret, som härletts från den tidsstämpeln som instrumenteras i händelse spårnings loggningen i ThreadX. Om tidsstämplarna är för nära (låg frekvent timer), kommer händelserna att köras tillsammans. Om tidsstämplar är för långt ifrån varandra (med hög frekvens), kommer händelserna att vara för långt ifrån varandra. Att välja rätt tidsintervall är ett viktigt övervägande för att göra tiden relativt meningsfull vy.

## <a name="system-summary-line"></a>System sammanfattnings rad

TraceX innehåller också en enda sammanfattnings rad (den övre kontexten i **Bild 10**) som innehåller alla händelser på samma rad. Detta gör det enkelt att se en översikt över ett komplext system. Sammanfattnings fältet är särskilt fördelaktigt i system som har många trådar. Utan en sådan sammanfattnings rad skulle du behöva följa komplexa system interaktioner med den lodräta rullnings listen för att följa körnings kontexten.

![Skärm bild av system sammanfattnings raden på fliken sekventiell vy.](./media/user-guide/screen_shot_32.png)


**BILD 10**

Sammanfattnings raden innehåller en sammanfattning av kontexten samt motsvarande händelse Sammanfattning under. I exemplet som visas i **Bild 10** är det enkelt att se att **_tråd 2_*_ körs och avbryts. Avbrotts resultatet i avstängningen av _*_tråd 3_**, ***tråd 6** _, _*_tråd 4_*_ och _*_tråd 7_*_, efter vilken _ *_tråd 2_** återupptar körningen.

## <a name="system-contexts"></a>System kontexter

TraceX visar system kontexterna till vänster i visningen, som du ser i **Bild 11**. Händelser som inträffar i en viss kontext visas på den vågräta linjen till höger om kontexten. På så sätt kan du enkelt kontrol lera vilken kontext händelsen har inträffat samt följa den kontext linjen för att se alla händelser som inträffat i en viss kontext.

De första kopplings kontext posterna är alltid ***avbrott** _ och _*_initiera/inaktiv-_*_ kontext. _*_Avbrotts_*_ kontext representerar alla system händelser som har gjorts från IRS (Interrupt service rutiner). _*_Initiera/passiv_*_ kontext representerar två kontexter i ThreadX. Händelser som inträffar under _*_tx_application_define_*_ är _*_initiera/inaktiv_*_ kontext. Om systemet är inaktivt och inga händelser inträffar, ritas det gröna fältet som _*_körs_*_ i vyn tid på kontexten _ *_initiera/inaktiv_**.

![Skärm bild av system kontexten till vänster i visningen.](./media/user-guide/screen_shot_33.png)

**BILD 11**

I exemplet i **Bild 11** finns nio tråd kontexter, från **_system timerns tråd_*_ kontext. Ytterligare information om en enskild kontext finns tillgänglig genom att placera musen på den kontexten. Den ytterligare informationen omfattar trådens start-stack-adress, slut på stack-adress, Total storlek, procent använt, relativ körnings procent, antal avstängningar, återupptagning och den högsta och lägsta prioriteten under spårningen. _* Bild 12** visar information för **_tråd 0_**.

![Skärm bild av informationen för tråd 0.](./media/user-guide/screen_shot_34.png)


**FIGUR 12**

Kontexter kan också flyttas till grupper med större intresse. Detta åstadkommer du genom att dra och släppa kontexten eller genom att högerklicka på kontexten. Genom att högerklicka på kontexten ger du en dialog ruta för att flytta kontexten längst upp eller ned. 

Välj ***Flytta längst upp** _ resultat i _*_tråd 3_*_ -kontexten som flyttas överst i kontext listan, som visas i _ * bild 13 * *.

![Skärm bild av den kontext som flyttas överst i kontext listan.](./media/user-guide/screen_shot_35.png)


**FIGUR 13**

## <a name="thread-status-information"></a>Information om tråd status

När det här alternativet är aktiverat visar TraceX status för varje tråd via en färgad linje i trådens kontext. En grön linje indikerar att tråden är i ett klart läge, medan en linje i andra färger indikerar att tråden har pausats. För pausade trådar anger färgen på linjen den typ av ThreadX-objekt som tråden är inaktive rad för. I **figur 13** visar till exempel den gröna linjen i **_system timer-trådens_*_-kontext som börjar vid händelse 147 att*_system timer-tråden_*_ är klar. Före händelse 147 och efter händelse 154, indikerar frånvaron av den gröna linjen att*_system timerns tråd_*_ är klar. Före händelse 147 och efter händelse 154, indikerar frånvaron av den gröna linjen att*_system timer-tråden_** är pausad.

![Skärm bild av status för varje tråd via en färgad linje i trådens kontext.](./media/user-guide/screen_shot_36.png)

**BILD 14**

Det finns tre lägen för visning av tråd status, tillgängligt via menyn ***alternativ-> status rader** _. Alternativet _*_redo_*_ är bara tillgängligt (grönt) status rader, men visar inga status rader för avbrott. Detta är standard alternativet för TraceX. Alternativet _ *_all på_** aktiverar visning av alla status rader (klar och SUS pensioner).

Slutligen inaktiverar alternativet ***all*** status rader visningen.

## <a name="event-information-display"></a>Visning av händelse information

TraceX innehåller detaljerad information om vissa 600 körnings händelser, inklusive ThreadX, FileX, NetX, NetX Duo och USBX API-anrop och interna händelser. TraceX har även stöd för upp till ytterligare 61 439 unika användardefinierade händelser.

Oavsett om visnings läget sekventiellt eller tiden är markerat visas detaljerad händelse information i händelse av en mus på valfri händelse i visnings ytan. Mus för händelse 143 i filen demonstration ***demo_threadx. trx** _ spår visas i _ * bild 15 * *:

![Skärm bild av mus över händelse 143 i ett exempel på en spårnings fil](./media/user-guide/screen_shot_37.png)

**BILD 15**

Varje händelse som visas innehåller standard information om ***context** _ och både _*_relativ tid_*_ och _*_tidstämpel._*_ Kontext fältet visar vilken kontext händelsen ägde rum i. Det finns exakt fyra kontexter: tråd, inaktivitet, ISR och initiering. När en händelse inträffar i en tråd kontext samlas tråd namnet och dess prioritet vid tidpunkten och visas som ovan. Den _*_relativa tiden_*_ visar det relativa antalet timer-Tick från början av spårningen. RAW-*_tidsstämpeln_** visar rå data källan för händelsen. Slutligen visas all information som är speciell för händelsen. Den här informationen beskrivs i resten av det här kapitlet.

Detaljerad händelse information är också tillgänglig genom att dubbelklicka på vilken händelse som helst. Dubbel klickning på händelse 143 visas i **bild 16**:

![Skärm bild av detaljerad händelse information när en händelse dubbelklickas.](./media/user-guide/screen_shot_38.png)

**BILD 16**

Att kunna visa flera händelser samtidigt ger användaren en mycket rikare vy av vad som hände. Det är mycket användbart att se dem sida vid sida eftersom många händelser är beroende av varandra. Detta åstadkommer du genom att dubbelklicka på flera händelser.

## <a name="current-event-display"></a>Aktuell händelse visning

TraceX visar den aktuella händelsen – i ett separat fönster – när det valts av användaren via ***visa > aktuella händelsen*** eller om du klickar på knappen Aktuell händelse i verktygsfältet. När du har valt TraceX visar den markerade händelsen i ett fristående fönster och uppdaterar det här fönstret när en annan händelse har valts.

## <a name="event-searching"></a>Händelses ökning

TraceX tillhandahåller en omfattande Sök funktion för händelser. Händelse-ID och informations fält för varje händelse är de primära Sök parametrarna. Att inte ange ett värde för en Sök parameter anger att parametern tar bort en effektiv parameter från sökningen. Dessutom kan sökningen göras så att alla parametrar som hittas uppfyller sökningen eller att alla parametrar måste hittas för att uppfylla sökningen. Sökningen kan också begränsas till en viss kontext eller avse alla sammanhang i spårningen. När du anropar händelse sökningen görs genom att välja ***Sök efter värde** _ i verktygsfältet, som du ser i _* bild 17 * *. När du väljer dialog rutan Sök visas som anger alla parametrar för sökningen. Knapparna **_Nästa_*_ och _*_föregående_*_ i dialog rutan Sök kan sedan användas för att hitta nästa och föregående händelser som matchar de angivna Sök kriterierna. _ *Bild 17** visar dialog rutan Sök.

![Skärm bild av händelse sökningen.](./media/user-guide/screen_shot_39.png)

**BILD 17**

![Skärm bild av dialog rutan Sök.](./media/user-guide/screen_shot_40.png)

**BILD 18**

## <a name="zooming-in-and-out"></a>Zooma in och ut

Som standard visar TraceX händelser i sin fulla storlek. Du kan zooma in eller ut efter behov. Att zooma ut är användbart för att se de övergripande händelser som har registrerats i spårningen, medan zoomning i är användbart i villkor där händelserna överlappar på grund av upplösningen av tids stämplings källan. **Bild 19** visar filen **_demo_threadx. trx_** som är zoomad så att 100% av spårnings filen visas.

![Skärm bild av en exempel fil som zoomas ut så att 100% av spårnings filen visas.](./media/user-guide/screen_shot_41.png)

**BILD 19**

När du zoomar ut med 100% för att visa hela spårningen på den aktuella visnings sidan, är det enkelt att se alla kontext körningar som fångats i spårningen samt de allmänna händelser som inträffar i dessa sammanhang. Observera i **bild 16** att **_tråd 1_*_ och _*_tråd 2_** körs oftast. De blå färgning för deras händelser innebär också att de här trådarna gör Queue Service-anrop (köa händelser är blå i färg).

Att återställa till en hel ikonvy är lika enkelt. Antingen kan du välja knappen Zooma in flera gånger eller så kan en viss faktor på 100 anges.

## <a name="delta-ticks-between-events"></a>Delta-Tick mellan händelser

Att fastställa antalet Tick mellan olika händelser i TraceX är enkelt – klicka på Start händelsen och dra musen till avslutande händelse. Delta antalet Tick mellan händelserna visas i det övre högra hörnet av visningen, som du ser i **bild 17**.

![Skärm bild av delta antalet Tick mellan händelserna.](./media/user-guide/screen_shot_42.png)

**BILD 17**

Delta ticken som visas i **bild 17** visar att 5032 Tick har förflutit mellan händelse 125 och händelse 154. Detta kan också beräknas manuellt genom att titta på de relativa tidsstämplar i varje händelse och subtraktion, men det är enkelt och momentant att använda det grafiska användar gränssnittet.

## <a name="actual-time-display"></a>Faktisk tids visning

När det här alternativet är aktiverat visar TraceX den faktiska tiden i mikrosekunder i ***Time View** _ och för de olika delta tids uppgifter som visas av TraceX. Som standard är den faktiska tids visningen inaktive rad. Om du vill aktivera den faktiska tids visningen måste antalet Tick per mikrosekund anges via *_alternativen _ alternativ-> Tick per mikrosekund_** på Meny val (värdet som ska anges bestäms av den maskinvaru-timer-källa som används för TraceX-händelseloggen på målet).

## <a name="priority-inversions"></a>Prioritets version

TraceX visar automatiskt de prioritets versioner som identifieras i spårnings filen. Prioritets versioner definieras som villkor där en tråd med högre prioritet blockeras försöker erhålla en mutex som för närvarande ägs av en tråd med lägre prioritet. Detta villkor kallas *deterministiskt*, eftersom systemet har kon figurer ATS för att användas på det här sättet. För att informera användaren visar TraceX *deterministiska* prioritets värden som en ljus lax färg.

TraceX visar även *Icke-deterministiska* prioritets versioner. De här prioritets versionerna skiljer sig från de *deterministiska* prioritets versionerna i att en annan tråd av en annan prioritets nivå har körts i mitten av vad som var en *deterministisk* prioritets version, vilket gör tiden inom prioritets versionen något *icke-deterministisk*. Det här tillståndet är ofta okänt för användaren och kan vara mycket allvarligt. För att varna användaren om detta villkor, visar TraceX *Icke-deterministiska* prioritets versioner som en lysande lax färg. **Bild 18** visar både *deterministiska* och *Icke-deterministiska* prioritets versioner.

![Skärm bild av prioritets versionen i en spårnings fil.](./media/user-guide/screen_shot_43.png)

**BILD 18**

**Bild 18** visar en *deterministisk* prioritets version från händelse 398 via händelse 402. I det här intervallet är den högre prioriteten ***Thread 0** _ block på en mutex som ägs av en tråd med lägre prioritet _*_1_*_. Vid händelse 402, kommer _ *_tråd 1_** att lansera mutex och därmed avslutas prioritets versionen.

Det ljusare skuggade avsnittet visar en *icke-deterministisk* prioritets version mellan händelse 408 och händelse 420. Det som gör denna *icke-deterministisk* är att när ***tråd 1** _ innehåller mutexen att _*_tråd 0_*_ för högre prioritet är blockerad, uppstår ett avbrott som återupptar _ *_tråd 2_* *, som sedan körs och förlänger den tid som systemet är i prioritets version. Det här tillståndet kan vara ganska allvarligt och svårt att identifiera. men med TraceX identifieras det enkelt.
