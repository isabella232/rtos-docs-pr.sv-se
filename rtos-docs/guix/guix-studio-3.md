---
title: Beskrivning av GUIX Studio
description: Det här kapitlet innehåller en beskrivning av GUIX Studio-verktyget för systemanalys.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 843106aa67d2a978c7f271954e028b32ba4dd007fe35a36b7c17ba0f5f80e4a9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116787215"
---
# <a name="chapter-3-description-of-guix-studio"></a>Kapitel 3: Beskrivning av GUIX Studio

Det här kapitlet innehåller en beskrivning av GUIX Studio-verktyget för systemanalys. En beskrivning av den övergripande funktionaliteten i det grafiska användargränssnittet finns i det här kapitlet. 

## <a name="guix-studio-views"></a>GUIX Studio-vyer

Det finns fem huvudområden i GUIX Studio-användargränssnittet, nämligen ***Verktygsfältet** _, _*_Project Visa,_*_ Egenskapsvy, _*_Målvy_*_ _*_och Vyn Resurser_*_. _**_ _ *_Bild 2_** visar det grundläggande användargränssnittet för GUIX Studio. Var och en av vyerna beskrivs närmare i följande underavsnitt.

![Skärmbild av det grundläggande gränssnittet i GUIX Studio.](./media/guix-studio/image_10.png)

**Bild 2**

### <a name="title"></a>Rubrik

- GUIX Studio 18: ***Rubrik** _ visar GUIX Studio-versionen samt det för tillfället öppna projektet, som visas överst i _ *_bild 2_** tidigare.

### <a name="toolbar"></a>Verktygsfält

***Verktygsfältet** _ visar knapparna som är tillgängliga för GUIX Studio-utvecklaren, som du ser i _*_bild 3_**.

![Skärmbild av verktygsfältet GUIX Studio.](./media/guix-studio/image11.jpg)

**Bild 3**

Knapparna i verktygsfältet definieras på följande sätt:

![Knappen Ny](./media/guix-studio/new-button.png) Skapar ett nytt GUIX Studio-projekt

![Knappen Öppna](./media/guix-studio/open-button.png) Öppnar ett befintligt GUIX Studio-projekt

![Knappen Spara](./media/guix-studio/save-button.png) Sparar projektet

![Knappen Klipp ut](./media/guix-studio/cut-button.png) Klipp ut widget vald, inklusive underordnade

![Knappen Kopiera](./media/guix-studio/copy-button.png) Kopiera vald widget, inklusive underordnade

![Knappen Klistra in](./media/guix-studio/paste-button.png) Klistra in widget och underordnade

![Vänsterjusterad knapp](./media/guix-studio/left-align-button.png) Vänsterjusterade valda widgetar

![Högerjusterad knapp](./media/guix-studio/right-align-button.png) Högerjustera valda widgetar

![Knappen Justera längst upp](./media/guix-studio/top-align-button.png) Översta justerade valda widgetar

![Knappen Justera längst ned](./media/guix-studio/bottom-align-button.png) Nedersta justerade valda widgetar

![Knappen Blanksteg lodrätt](./media/guix-studio/space-vertically-button.png) Jämnt utrymme för valda widgetar lodrätt

![Knappen Blanksteg vågrätt](./media/guix-studio/space-horizontally-button.png) Vågrätt valda widgetar med lika utrymme

![Knappen Lika med bredd](./media/guix-studio/equal-width-button.png) Gör valda widgetar lika med bredd

![Knappen Lika med höjd](./media/guix-studio/equal-height-button.png) Gör de valda widgetarna lika med höjd

![Flytta framknappen](./media/guix-studio/move-front-button.png) Flytta valda widgetar framifrån

![Knappen Flytta tillbaka](./media/guix-studio/move-back-button.png) Flytta valda widgetar till bakåt

![Knappen Storlek](./media/guix-studio/size-button.png) Storleksvald widget till innehåll Zooma ut målskärm

![Knappen Zooma ut](./media/guix-studio/zoom-out-button.png) Zoom ut målskärm

![Knappen Zooma in](./media/guix-studio/zoom-in-button.png) Zooma in målskärmen

![Knappen Spela in](./media/guix-studio/record-button.png) Spela in makro

![Uppspelningsknapp](./media/guix-studio/playback-button.png) Spela upp makro

![Knappen Kör](./media/guix-studio/run-button.png) Köra program

![Knappen Om](./media/guix-studio/about-button.png) Om GUIX Studio

### <a name="project-view"></a>Project Visa

I ***Project View** _ visas guix-objekten i den hierarkiska listan som utgör det inbäddade användargränssnittet. Du kan lägga till nya GUIX-objekt genom att klicka på det överordnade objektet och sedan välja ett objekt på _*_Infoga-menyn_*_ (eller genom att högerklicka på objektet och välja från snabbmenyn). _*_Bild 4_*_ nedan visar GUIX Studio _*_Project View_**.

![Skärmbild av GUIX Studio Project View.](./media/guix-studio/image_35.png)

**Bild 4**

### <a name="properties-view"></a>Egenskapsvy

***Egenskapsvy** _ visar detaljerad egenskapsinformation för det markerade GUIX-objektet, som kan väljas via _*_Project View_*_ eller genom att klicka direkt på objektet i _*_målvyn_*_. _*_Bild 5_*_ nedan visar GUIX Studio _*_Egenskapsvy_**.

![Skärmbild av GUIX Studio-egenskapsvyn.](./media/guix-studio/image36.jpg)

**Bild 5**

### <a name="target-view"></a>Målvy

***Målvy** _ är WYSIWYG-skärmens design- och layoutområde. Den här vyn är avsedd att representera den fysiska visningen eller visas på målmaskinvaran. Objekt kan väljas, flyttas, ändras, osv. via enkla musåtgärder. Dessutom är knappåtgärderna justering och Z-ordning tillgängliga för valda objekt i målvyn. Om du väljer ett _*_objekt i målvyn_*_ resulterar det även i egenskaperna för objektet som ska visas i _*_egenskapsvyn_*_. _*_Bild 6_*_ nedan visar GUIX Studio _*_Målvy_**.

![Skärmbild av GUIX Studio-målvyn.](./media/guix-studio/image_37.png)

**Bild 6**

### <a name="resource-view"></a>Vyn Resurser

***Vyn Resurser** _ används för att hantera de resurser (färger, teckensnitt, pixelkartor och strängar) som är tillgängliga för programskärmar som definierats för varje visning. Du kan klicka på resursvyns grupprubriker för att expandera varje grupp och granska gruppinnehållet. _*_Bild 7_*_ nedan visar GUIX Studio _*_Vyn Resurser_**.

![Skärmbild av GUIX Studio-Vyn Resurser.](./media/guix-studio/image38.jpg)

**Bild 7**

Resursgruppernas rubrik anger det aktuella temanamnet. Om flera teman är tillgängliga kan du växla mellan teman genom att klicka på uppåt- och nedåtpilen.

Varje resursgrupp i vyn ovan kan expanderas eller komprimeras genom att klicka på grupprubriken. En mer detaljerad beskrivning av varje resursgrupp finns i nästa kapitel.

## <a name="the-guix-studio-project"></a>GUIX Studio-Project

Ett GUIX Studio-projekt innehåller information om gränssnittsskärmens design och gränssnittsresurser. Projektdata sparas i en XML-formatfil med tillägget ". ***gxp***". Eftersom projektfilen är en XML-schemafil kan den versionskontrolleras och delas på samma sätt som andra källfiler.

När du börjar använda GUIX Studio måste du antingen öppna ett av de exempelprojekt som medföljer distributionen eller skapa ett nytt projekt. Allt ditt arbete sparas i projektdatafilen.

GUIX Studio skapar även ANSI C-källfiler. Dessa källfiler innehåller antingen dina programresurser eller datastrukturer som beskriver dina utformade skärmar. GUIX Studio skriver också till de genererade API-funktionerna för källfiler som använder de genererade datastrukturerna för att dynamiskt skapa programskärmar. Din programprogramvara anropar bara de tillhandahållna API-funktionerna för att skapa de skärmar som du har utformat i GUIX Studio.

När du utvecklar användargränssnittet bör du regelbundet använda GUIX Studio för att generera GUIX-kompatibla utdatafiler som gör att du kan skapa och köra gränssnittet som du har utformat. Du kan kompilera och köra de genererade källfilerna för antingen målmaskinvaran eller på ditt Windows som simulerar ThreadX och GUIX.

## <a name="guix-studio-project-organization"></a>GUIX Studio Project Organisation

Det är bra att ha viss kunskap om den grundläggande organisationen av ett GUIX Studio-projekt för att förstå hur man använder GUIX Studio effektivt och förstå informationen som presenteras i Project View of the GUIX Studio IDE. Den Project vyn är en sammanfattning av den visuella representationen av all information som finns i projektet.

Innan du beskriver projektet måste du definiera några termer. Först använder vi termen Visa **för att** betyda en fysisk visningsenhet. Det här är oftast en SKÄRM-enhet, men den kan använda annan teknik. Nästa term är **Skärm,** vilket innebär ett GUIX-objekt på den översta nivån, vanligtvis ett GUIX-fönster och alla dess associerade underordnade element. En skärm är en programvarukonstruktion som kan definieras och ändras vid körning. Slutligen är ett **tema** en samling resurser. Ett tema innehåller en tabell med färgdefinitioner, teckensnittsdefinitioner och pixelkartedefinitioner som är utformade för att fungera bra tillsammans och ge slutanvändaren ett konsekvent utseende och en konsekvent känsla.

Projektet innehåller först en uppsättning global information, till exempel projektnamn, antal skärmar som stöds, upplösning och färgformat för varje visning, antalet språk som stöds och namnet på varje språk som stöds. Projektnamnet är den första noden som visas i Project Vy.

Projektet ordnar sedan all information som krävs för upp till 4 fysiska skärmar och de skärmar och resurser som är tillgängliga för varje visning. Visningsnamnen är noderna på nästa nivå i Project visa träd.

En unik funktion i GUIX Studio-programmet är inbyggt stöd för flera fysiska skärmar, var och en med sin egen x,y-upplösning, färgformat, skärmar och resurser. Även om de allra flesta GUIX-program endast använder en fysisk skärm, är den här funktionen viktig för dem som gör en produkt som måste ha stöd för flera samtidiga fysiska skärmar.

Under varje visningsdefinition finns de fönster eller skärmar på den översta nivån som definierats för visningen. Skärmdefinitionerna kan kapslas till valfri nivå beroende på antalet och kapsling av underordnade widgetar på varje skärm.

Den här skärmen och den underordnade widgetorganisationen visas på ett grafiskt sätt i Project vy.

De teman som stöds av visningen och resursinnehållet som utgör varje tema är också associerade med varje visning. Om ditt projekt innehåller flera visningar ser du att Vyn Resurser ändrar dess innehåll när du väljer en visning och sedan en annan. Det beror på att resursinnehållet är länkat till varje visning. Färgformatet kan inte bara vara olika, utan de pixelkartor, färger och teckensnitt som du väljer att använda kan variera från en fysisk skärm till en annan.

Den sista komponenten som underhålls av projektet är strängtabelldata som är associerade med varje visning. Eftersom displayer kan ha mycket olika x,y-upplösningar underhålls strängdata oberoende av varandra för varje visning som definieras i projektet.
