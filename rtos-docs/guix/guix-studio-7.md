---
title: Definiera Flow
description: GUIX Studio stöder automatisk generering och körning av logik för skärmövergång.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1df90acd86b4446d96a66ab3ee21545afcd9824e28efb40204c2966cb075c501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785617"
---
# <a name="chapter-7-defining-screen-flow"></a>Kapitel 7: Definiera Flow

GUIX Studio stöder automatisk generering och körning av logik för skärmövergång. Användaren definierar logiken för skärmövergång genom att skapa och redigera ett grafiskt skärmflödesdiagram. När ett skärmflödesdiagram läggs till i projektet möjliggör det två viktiga funktioner: 1) Programmet kan köras inifrån Studio-miljön och 2) Studio genererar automatiskt händelsehanterare och skärmövergångslogik för att implementera det avsedda skärmflödet i den genererade filen specifications.c, vilket tar bort den här belastningen från programmet. 

Att köra programmet på skrivbordet från Studio-miljön är en praktisk funktion som sparar tid eftersom du inte behöver gå igenom en cykel för kompilering/länk för att köra programmet. Det finns naturligtvis begränsningar för vad som kan göras utan att kompilera programmet. Anpassade ritningsfunktioner, anpassade händelsehanterare och komplex händelsehantering är inte tillgängliga när du kör programmet inifrån GUIX Studio-miljön. Med den här funktionen kan du fortfarande automatiskt generera logik för skärmövergång och programanimeringar som ska köras för att övergå från en skärm till en annan. Dessa effekter och animeringar kan observeras direkt från GUIX Studio-miljön.

Observera att när du definierar skärmflöde, utlösare och åtgärder som beskrivs i följande stycken aktiverar du inte bara körningen av användargränssnittet inifrån Studio-miljön, utan du aktiverar även GUIX Studio för att generera logik i din specifikationsfil som hanterar händelser och vidta åtgärder baserat på dessa händelser,  som att övergå från en skärm till en annan.

## <a name="configuring-screen-flow"></a>Konfigurera Flow

Innan ett program kan köras inifrån Studio-miljön måste några saker definieras. För det första måste skärmen eller skärmarna på den översta nivån som ska visas vid programstart anges genom att välja egenskapen "Synlig vid start" i studioegenskaperna. Den här flaggan anger att den här skärmen först ska visas när programmet startar. Mer än en skärm kan ha den här benämningen om du vill.

När du har definierat de skärmar som visas vid start kan användaren definiera hur UI-programmet ska flöda från skärm till skärm. GUIX Studio innehåller ett grafiskt skärmflödesdiagram för att definiera logik för skärmövergång. Välj bara menyvalet ***Konfigurera, Skärm Flow** _ för att öppna dialogrutan för redigering av skärmflöde, se skärmbilden i _*_bild 30_**.

![Skärmbild av dialogrutan GUIX Studio Screen Flow.](./media/guix-studio/config_screen_flow.png)

**Bild 30**

Varje skärm på den översta nivån som definieras i projektet visas som en ruta som visar skärmnamnet. Den här rutan är en platshållare som representerar varje skärm på den översta nivån som definierats i projektet. Dessa rutor kan flyttas och ändras efter behov. När en övergång från en skärm på den översta nivån till en annan har definierats visas en anslutningslinje med ett pilhuvud mellan två skärmar för att indikera övergångar från en skärm till en annan.

Trädvyn till vänster i skärmflödesdiagrammet visar varje skärm på den översta nivån och du kan välja vilka skärmar på den översta nivån som ska ritas i skärmflödesdiagrammet.

Skärmflödesdiagrammet är rullningsbart. Du kan dra alla skärmblock nedåt och precis utanför det synliga området för att förstora det rullningsbara fönstret. När det rullningsbara fönstret har förstorats kan du zooma ut så att det passar det synliga området genom att rulla ned mushjulet. Om det rullningsbara fönstret zoomas ut kan du göra det tillräckligt stort för att rymma alla block genom att rulla upp mushjulet.

Om du vill definiera övergångar för en skärm högerklickar du på platshållaren för skärmen för att öppna dialogrutan Redigera utlösarlista. Se ***bild 31.***

![Skärmbild av dialogrutan Redigera utlösarlista i GUIX Studio.](./media/guix-studio/edit_trigger_list.png)

**Bild 31**

Dialogrutan för att redigera utlösare visar de händelser som användaren har definierat och som utlöser en skärmövergång, vilket är anledningen till att vi anropar dessa händelseutlösare. Utlösare är vanligtvis signaler som genereras av en eller flera underordnade widgetar på den valda skärmen.

Om du vill definiera en ny utlösare väljer du **knappen*** Lägg till ny utlösare _ i dialogrutan Redigera utlösarlista för att öppna dialogrutan Lägg till utlösare som visas i _*_bild 32_**.

![Skärmbild av dialogrutan Lägg till utlösare i GUIX Studio.](./media/guix-studio/add_trigger_for.png)

**Bild 32**

Du kan definiera händelsetypen som utlöser en ny uppsättning åtgärder och definiera de åtgärder som ska köras när utlösarhändelsen tas emot.

När du har definierat den händelsetyp som du vill använda för att utlösa en ny animeringsskärmövergång sparar du den nya utlösaren så visas den i dialogrutan Redigera utlösarlista.

Du kan ändra den här händelsen (utan att ändra de relaterade åtgärder som ska vidtas) genom att välja händelsen i dialogrutan Redigera utlösarlista och välja ***knappen Redigera utlösarhändelse.***

På samma sätt kan du ta bort en utlösarhändelse från listan genom att välja händelsen och klicka på ***knappen Ta bort vald*** utlösare.

Om du vill ange animeringen eller skärmövergången som ska ske baserat på en viss utlösarhändelse väljer du utlösarhändelsen och klickar på ***knappen Redigera*** åtgärd. Observera att du kan utlösa fler än en åtgärd baserat på varje definierad utlösare.

Knappen **Redigera åtgärd(er)** visar dialogrutan Redigera åtgärder för utlösare, som visas i bild 33: 

![Skärmbild av dialogrutan GUIX Studio Redigera åtgärder för utlösare.](./media/guix-studio/edit_actions_for_trigger.png)

**Bild 33**

I den här dialogrutan kan du definiera val av åtgärder som ska implementeras baserat på den här utlösarhändelsen. Du kan ge varje åtgärd ett beskrivande namn som hjälper dig att associera varje åtgärdsdefinition med en visuell animering eller övergång. I exemplet ovan definierade vi två åtgärder med namnet "fade_in_text_screen" och "fade_out_button_screen".

Definiera en ny åtgärd att implementera och klicka på knappen Lägg till ny åtgärd, som visar dialogrutan Välj åtgärd, bild 34:

![Skärmbild av dialogrutan Välj åtgärd i GUIX Studio.](./media/guix-studio/select_action.png)

**Bild 34**

Tillgängliga åtgärdstyper är:

- **Animering:** Starta en animering med angiven information.
- **Anslut:** Anslut målskärmen till den överordnade skärmen. Om den överordnade skärmen inte har angetts ansluts målskärmen till rotfönstret.
- **Koppla från:** Koppla från målskärmen från dess överordnade skärm.
- **Dölj:** Dölj målskärmen.
- **Skärmstackspop:** Pop a screen from the internal screen stack (Pop-pop i en skärm från den interna skärmstacken).
- **Push-push för skärmstack:** Skicka en skärm pekare till den interna skärmstacken.
- **Återställning av skärmstack:** Ta bort alla skärmpekare från den interna skärmstacken.
- **Visa:** Visa målskärmen.
- **Växla:** Koppla målskärmen till den aktuella skärmens överordnade skärm och koppla bort den aktuella skärmen från dess överordnade skärm.
- **Kör fönster:** Kör målskärmen modally.
- **Window Execute Stop**:Exit modally execution of the current screen.

När du har definierat en åtgärd som ska vidtas baserat på den valda utlösarhändelsen visas åtgärden i dialogrutan Redigera åtgärder för utlösare. Du kan välja den här åtgärden om du vill ändra parametrarna för åtgärden enligt bild 35.

![Skärmbild av dialogrutan GUIX Studio Redigera åtgärder för utlösare.](./media/guix-studio/edit_actions_for_trigger.png)

**Bild 35**

Om åtgärdstypen är en animering visas en uppsättning animeringsparametrar till höger så att du kan definiera en animering av bild- och/eller toningstyp som ska köras. När en animeringsåtgärd har slutförts kan du också avgöra om animeringen ska tas bort automatiskt från den överordnade och/eller push-skickas till den interna skärmstacken, vilket ofta är användbart när du definierar menysystem med flera lager.

För animeringar med dra och toning kan du också definiera den easing-funktion som ska användas genom att välja knappen Easing Func Select (Underlätta func-val). Easing-funktioner är olika kurvor som är utformade för att närmare efterlikna verkliga rörelsehändelser. Om du väljer den här knappen **öppnas dialogrutan Välj easing-funktion,** bild 36:

![Skärmbild av dialogrutan Välj easingfunktion i GUIX Studio.](./media/guix-studio/easing_function_select.png)

**Bild 36**

Om du definierar flera åtgärder som ska associeras med en utlösarhändelse kan det vara praktiskt att tilldela varje åtgärd ett beskrivande namn. Åtgärdsnamn måste följa namngivningsreglerna för C-syntax, eftersom dessa namn kommer att användas i den genererade specifikationsfilen för att definiera händelse- och åtgärdstabeller.

När du definierar utlösarhändelser och åtgärder i GUIX Studio genereras automatiserade händelsehanterare i filen med projektspecifikationer för att hantera dessa händelser och köra de angivna åtgärderna. Det innebär att du INTE behöver hantera dessa händelser i din programkod, även om utlösarhändelserna fortfarande skickas till anpassade händelsehanterare som du har definierat. Med andra ord utökar studiogenererade händelsehanterare dina egna anpassade händelsehanterare i stället för att ersätta dem.

## <a name="running-the-application"></a>Köra programmet

När startskärmarna och ett skärmflödesdiagram har skapats kan du köra programmet i Studio genom att välja "Kör program"

![Skärmbild av knappen Kör program.](./media/guix-studio/image68.jpg)

i verktygsfältet och väljer Redigera | Kör Program från projektmenyn eller genom att välja knappen Kör längst ned i dialogrutan Redigera Flow skärm.

När du kör programmet visas de skärmar som du har angett som "Synlig vid start" i ett nytt fönster. De underordnade widgetarna på den här skärmen fungerar fullt ut. Du kan klicka på knappar, använda skjutreglage och rullningshjul osv. Om du har definierat anpassade ritningsfunktioner eller kundhändelsehantering för någon av dessa widgetar ser du förstås INTE detta när du kör programmet i det här läget. Men om du har definierat ett skärmflödesdiagram med utlösarhändelser och åtgärder kommer dessa utlösare att fungera och dina skärmar övergår som du har definierat, inklusive animeringar som du har definierat.
