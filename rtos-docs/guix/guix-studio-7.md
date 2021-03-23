---
title: Definiera skärm flöde
description: GUIX Studio stöder automatisk generering och körning av en skärm över gångs logik.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1c590725281c785181bcb4c5852346bc973c24d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826298"
---
# <a name="chapter-7-defining-screen-flow"></a>Kapitel 7: definiera skärm flöde

GUIX Studio stöder automatisk generering och körning av en skärm över gångs logik. Användaren definierar skärmens över gångs logik genom att skapa och redigera ett grafiskt skärm flödes diagram. När ett skärm flödes diagram läggs till i projektet, aktiverar det två viktiga funktioner: 1) programmet kan köras inifrån Studio-miljön och 2) Studio genererar automatiskt händelse hanterare och skärm över gångs logik för att implementera det angivna skärm flödet i den genererade specifikationerna. c-filen, vilket tar bort den här belastningen från program programmet. 

Att köra programmet på Skriv bordet från Studio-miljön är en praktisk funktion som sparar tid i att du inte behöver gå igenom en kompilera/länka-cykel för att köra programmet. Det finns kurs begränsningar för vad som kan göras utan att kompilera programmet. Anpassade rit funktioner, anpassade händelse hanterare och komplex händelse hantering är inte tillgängliga när du kör programmet inifrån GUIX Studio-miljön. Den här funktionen gör det möjligt för dig att automatiskt skapa en skärm över gångs logik och programanimeringar som ska köras för över gången från en skärm till en annan. Dessa effekter och animeringar kan observeras direkt i GUIX Studio-miljön.

Observera att när du definierar skärm flöde, utlösare och åtgärder som vi ska beskriva i följande stycken, så aktiverar du inte bara körning av ditt användar gränssnitt från Studio-miljön, men du aktiverar även GUIX Studio för att generera logik i din fil med specifikationer som hanterar händelser och vidtar åtgärder baserat på dessa händelser, till exempel över gång från en skärm till en annan.

## <a name="configuring-screen-flow"></a>Konfigurera skärm flöde

Innan ett program kan köras i Studio-miljön måste några saker definieras. Först måste skärmen eller skärmarna på den översta nivån som ska visas vid program start anges genom att välja egenskapen "synlig vid start" i vyn Studio egenskaper. Den här flaggan anger att den här skärmen först ska visas när programmet startas. Mer än en skärm kan ha den här beteckningen om du vill.

När du har definierat skärm (er) som är synliga vid start kan användaren definiera hur UI-programmet ska flöda från skärmen till skärmen. GUIX Studio innehåller ett grafiskt skärm flödes diagram för att definiera en skärm över gångs logik. Välj bara meny alternativet ***Konfigurera, skärm flöde** _ för att Visa dialog rutan Redigera dialog rutan, se skärm bilden i _ *_bild 30_* *.

![Skärm bild av dialog rutan skärm flöde i GUIX Studio.](./media/guix-studio/config_screen_flow.png)

**Bild 30**

Varje bildskärm på den översta nivån som definierats i projektet visas som en ruta som visar skärm namnet. Den här rutan är en plats hållare som representerar varje toppnivå som definierats i projektet. Dessa rutor kan flyttas och storleks änd ras efter behov. När en över gång från en bildskärm på översta nivån till en annan har definierats visas en anslutnings linje med en pil mellan två skärmar som visar över gångar från en skärm till en annan.

Trädvyn i vänster sida av skärmens flödes diagram visar varje toppnivå-skärm och du kan välja vilka skärmar på den översta nivån som ska ritas i skärm flödes diagrammet.

Skärm Flow-diagrammet är rullnings Bart. Du kan dra ett skärm block nedåt och åt höger utanför det synliga området för att förstora det rullnings bara fönstret. När du har för sto rad rullnings fönstret kan du zooma ut så att det passar det synliga avsnittet genom att rulla mus hjulet nedåt. Om rullnings bara fönstret är utzoomat kan du göra det tillräckligt stort för att rymma alla block genom att rulla mus hjulet uppåt.

Om du vill definiera över gångar för en skärm högerklickar du på plats hållaren för skärmen för att öppna dialog rutan Redigera utlösare, se ***bild 31***.

![Skärm bild av dialog rutan Redigera utlösare i GUIX Studio.](./media/guix-studio/edit_trigger_list.png)

**Bild 31**

I dialog rutan för utlösare redigera visas de händelser som användaren har definierat som utlöser en skärm över gång, vilket är orsaken till att vi kallar dessa händelse utlösare. Utlösare signalerar normalt genereras av en eller flera underordnade widgetar för den valda skärmen.

Om du vill definiera en ny utlösare väljer du knappen ***Lägg till ny utlösare** _ i dialog rutan Redigera utlösare för att Visa dialog rutan Lägg till utlösare i _ *_bild 32_* *.

![Skärm bild av dialog rutan Lägg till utlösare för GUIX Studio.](./media/guix-studio/add_trigger_for.png)

**Figur 32**

Du kan definiera vilken händelse typ som ska utlösa en ny uppsättning åtgärder och definiera de åtgärder som ska utföras när utlösaren tas emot.

När du definierar den händelse typ som du vill använda för att utlösa en ny Animations skärm över gång, sparar du den nya utlösaren så visas den i dialog rutan Redigera utlösare.

Du kan ändra den här händelsen (utan att ändra de relaterade åtgärder som ska vidtas) genom att markera händelsen i dialog rutan Redigera utlösare och välja ***händelse knappen Redigera utlösare*** .

På samma sätt kan du ta bort eventuella Utlös ande händelser från listan genom att markera händelsen och klicka på knappen ***ta bort vald utlösare*** .

Om du vill ange vilken animering eller skärm bilds över gång som ska ske baserat på en viss Utlös ande händelse väljer du den Utlös ande händelsen och klickar på knappen ***Redigera åtgärd (er)*** . Observera att du kan starta mer än en åtgärd baserat på varje definierad utlösare.

Med knappen **Redigera åtgärd (n)** kan du se dialog rutan Redigera åtgärder för utlösare, som visas i bild 33: 

![Skärm bild av dialog rutan Redigera åtgärder för utlösare i GUIX Studio.](./media/guix-studio/edit_actions_for_trigger.png)

**Figur 33**

Med den här dialog rutan kan du definiera hur många åtgärder som ska implementeras baserat på den här utlösnings händelsen. Du kan ge varje åtgärd ett beskrivande namn som hjälper dig att associera varje åtgärds definition med en visuell animering eller över gång. I exemplet ovan definierade vi två åtgärder med namnet "fade_in_text_screen" och "fade_out_button_screen".

Definiera en ny åtgärd att implementera genom att klicka på knappen Lägg till ny åtgärd, som öppnar dialog rutan Välj åtgärd, bild 34:

![Skärm bild av dialog rutan Välj åtgärd i GUIX Studio.](./media/guix-studio/select_action.png)

**Figur 34**

Tillgängliga åtgärds typer är:

- **Animering**: starta en animering med angiven information.
- **Bifoga**: koppla mål skärmen till den överordnade skärmen, om den överordnade skärmen inte anges, kopplas mål skärmen till rot fönstret.
- **Koppla** från: koppla från mål skärmen från dess överordnade plats.
- **Dölj**: Dölj mål skärmen.
- **Skärms tack pop**: pop a Screen från den interna stacken.
- **Push**-överföring av skärm: skicka en skärm pekare till den interna stacken.
- **Återställ skärms stack**: ta bort alla skärm pekare från den interna stacken.
- **Visa**: Visa mål skärmen.
- **Växla**: koppla mål skärmen till den aktuella skärmens överordnade och koppla bort den aktuella skärmen från dess överordnade plats.
- **Fönster körning**: kör på mål skärmen.
- **Fönster körnings stopp**: avsluta körning av den aktuella skärmen.

När du har definierat en åtgärd som ska utföras baserat på den valda utlösnings händelsen visas åtgärden i dialog rutan Redigera åtgärder för utlösare. Du kan välja den här åtgärden för att ändra parametrarna för åtgärden som visas i bild 35.

![Skärm bild av dialog rutan Redigera åtgärder för utlösare i GUIX Studio.](./media/guix-studio/edit_actions_for_trigger.png)

**Figur 35**

Om åtgärds typen är en animering visas en uppsättning animeringssymboler till höger så att du kan definiera en animering av bild och/eller toning som ska köras. När en animeringseffekt har slutförts kan du också avgöra om animeringen ska kopplas från automatiskt från den överordnade och/eller skickas till den interna skärm bilden, vilket ofta är användbart när du definierar meny system på flera lager.

För animeringar av bild och toning kan du också definiera den över gångs funktion som ska användas genom att välja knappen över gångs val. Över gångar är olika kurvor som har utformats för att bättre efterlikna faktiska händelser för livs längds rörelser. Om du markerar den här knappen visas dialog rutan Välj över gångs **funktion** , bild 36:

![Skärm bild av GUIX Studio Välj över gångs funktion dialog ruta.](./media/guix-studio/easing_function_select.png)

**Figur 36**

Om du definierar flera åtgärder som ska associeras med en Utlös ande händelse kan det vara praktiskt att tilldela varje åtgärd ett meningsfullt namn. Åtgärds namn måste följa namngivnings regler för C-syntax, eftersom dessa namn används i den genererade Specifikations filen för att definiera händelse-och åtgärds tabeller.

När du definierar Utlös ande händelser och åtgärder i GUIX Studio genereras automatiska händelse hanterare i filen med projekt specifikationer för att hantera dessa händelser och köra de angivna åtgärderna. Det innebär att du inte behöver hantera dessa händelser i program koden, även om utlösarens händelser fortfarande skickas till eventuella anpassade händelse hanterare som du har definierat. Med andra ord ökar Studio-genererade händelse hanterare, i stället för att ersätta, dina egna anpassade händelse hanterare.

## <a name="running-the-application"></a>Köra programmet

När Start skärmar och ett skärm flödes diagram har skapats kan du köra programmet i Studio genom att välja alternativet Kör program

![Skärm bild av knappen Kör program.](./media/guix-studio/image68.jpg)

-knapp i verktygsfältet och väljer Redigera | Kör programmet från projekt-menyn eller genom att klicka på knappen Kör längst ned i dialog rutan Redigera skärm flöde.

När du kör programmet visas skärmarna som du har angivit som "synlig vid start" i ett nytt fönster. De underordnade widgetarna på dessa skärmar är helt operativa. Du kan klicka på knappar, använda skjutreglagen och rulla hjul osv. Om du har definierat anpassade ritnings funktioner eller kund händelse hantering för någon av dessa widgetar, kommer du naturligtvis inte att se detta när du kör programmet i det här läget. Men om du har definierat ett skärm flödes diagram med Utlös ande händelser och åtgärder, kommer dessa utlösare att fungera och dina skärmar kommer att överföras när du har definierat, inklusive eventuella animeringar som du kan ha definierat.
