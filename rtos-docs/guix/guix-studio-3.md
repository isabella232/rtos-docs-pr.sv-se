---
title: Beskrivning av GUIX Studio
description: Det här kapitlet innehåller en beskrivning av system analys verktyget GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826370"
---
# <a name="chapter-3-description-of-guix-studio"></a>Kapitel 3: Beskrivning av GUIX Studio

Det här kapitlet innehåller en beskrivning av system analys verktyget GUIX Studio. En beskrivning av de övergripande funktionerna i det grafiska användar gränssnittet finns i det här kapitlet. 

## <a name="guix-studio-views"></a>GUIX Studio-vyer

Det finns fem huvud områden i användar gränssnittet för GUIX Studio, nämligen ***verktygsfältet** _, _*_projektvyn_*_, _*_egenskapsvyn, vyn_*_ _*_mål_*_ och _*_vyn resurser_*_. _ *_Bild 2_** visar gränssnittet Basic GUIX Studio. Var och en av vyerna beskrivs i följande underavsnitt.

![Skärm bild av Basic GUIX Studio-ANVÄNDARGRÄNSSNITTET.](./media/guix-studio/image_10.png)

**Bild 2**

### <a name="title"></a>Rubrik

- GUIX Studio 18: ***title** _ visar versionen av GUIX Studio och det för tillfället öppna projektet, som visas överst i _ *_bild 2_** tidigare.

### <a name="toolbar"></a>Verktygsfält

I **verktygsfältet*** visas alla knappar som är tillgängliga för GUIX Studio-utvecklare, som du ser i _ *_bild 3_* *.

![Skärm bild av GUIX Studio-verktygsfältet.](./media/guix-studio/image11.jpg)

**Bild 3**

Verktygsfälts knapparna definieras enligt följande:

![Knappen Ny](./media/guix-studio/new-button.png) Skapar ett nytt GUIX Studio-projekt

![Knappen Öppna](./media/guix-studio/open-button.png) Öppnar ett befintligt GUIX Studio-projekt

![Knappen Spara](./media/guix-studio/save-button.png) Sparar projektet

![Knappen Klipp ut](./media/guix-studio/cut-button.png) Klipp ut widget markerad, inklusive underordnade

![Knappen Kopiera](./media/guix-studio/copy-button.png) Kopiera markerad widget, inklusive underordnade

![Knappen Klistra in](./media/guix-studio/paste-button.png) Klistra in widget och underordnade

![Knappen Vänsterjustera](./media/guix-studio/left-align-button.png) Vänsterjustera markerade widgetar

![Högerjustera-knapp](./media/guix-studio/right-align-button.png) Högerjustera markerade widgetar

![Knappen Justera mot överkant](./media/guix-studio/top-align-button.png) Översta justering av markerade widgetar

![Knappen Justera mot nederkant](./media/guix-studio/bottom-align-button.png) Underst-justera markerade widgetar

![Knappen lodrätt blank steg](./media/guix-studio/space-vertically-button.png) Lika mycket utrymme valda widgetar lodrätt

![Blank steg vågrätt](./media/guix-studio/space-horizontally-button.png) Lika mycket utrymme valda widgetar vågrätt

![Knappen med samma bredd](./media/guix-studio/equal-width-button.png) Gör valda widgetar lika breda

![Knappen med samma höjd](./media/guix-studio/equal-height-button.png) Gör valda widgetar lika höjd

![Flytta fram knapp](./media/guix-studio/move-front-button.png) Flytta valda widgetar längst fram

![Flytta tillbaka-knapp](./media/guix-studio/move-back-button.png) Flytta valda widgetar tillbaka

![Storleks knapp](./media/guix-studio/size-button.png) Ändra vald widget till innehåll zooma ut mål skärmen

![Knappen Zooma ut](./media/guix-studio/zoom-out-button.png) Zooma ut mål skärmen

![Knappen Zooma in](./media/guix-studio/zoom-in-button.png) Zooma in mål skärmen

![Knappen Spela in](./media/guix-studio/record-button.png) Spela in makro

![Uppspelnings knapp](./media/guix-studio/playback-button.png) Uppspelnings makro

![Knappen Kör](./media/guix-studio/run-button.png) Kör program

![Knappen om](./media/guix-studio/about-button.png) Om GUIX Studio

### <a name="project-view"></a>Projektvyn

I ***Project-vyn** _ visas den hierarkiska listan GUIX objekt som utgör det inbäddade användar gränssnittet. Du kan lägga till nya GUIX-objekt genom att klicka på det överordnade objektet och sedan välja ett objekt från _*_Infoga_*_ -menyn (eller genom att högerklicka på objektet och välja i menyn på snabb menyn). _*_Bild 4_*_ nedan visar GUIX Studio _ *_projektvyn_* *.

![Skärm bild av projektvyn i GUIX Studio.](./media/guix-studio/image_35.png)

**Bild 4**

### <a name="properties-view"></a>Egenskapsvyn

***Egenskaperna View** _ visar detaljerad egenskaps information för det markerade GUIX-objektet, som kan väljas via _*_projektvyn_*_ eller genom att klicka direkt på objektet i _*_vyn mål_*_. _*_Bild 5_*_ nedan visar _egenskapsvyn_ för GUIX Studio _ *.

![Skärm bild av egenskapsvyn för GUIX Studio.](./media/guix-studio/image36.jpg)

**Figur 5**

### <a name="target-view"></a>Mål visning

***Target-vyn** _ är design och layout i WYSIWYG-skärmen. Den här vyn är avsedd att representera den fysiska visningen eller visningen som är tillgänglig på mål maskin varan. Objekt kan markeras, flyttas, ändras och ändras med hjälp av enkla mus åtgärder. Dessutom är justerings-och Z-order-knapparna tillgängliga för valda objekt i vyn mål. Om du markerar ett objekt i vyn _*_mål_*_ så kommer egenskaperna för objektet att visas i _*_egenskapsvyn_*_. _*_Bild 6_*_ nedan visar GUIX Studio _ *_target View_* *.

![Skärm bild av vyn GUIX Studio Target.](./media/guix-studio/image_37.png)

**Bild 6**

### <a name="resource-view"></a>Vyn Resurser

***Vyn resurser** _ används för att hantera resurserna (färger, teckensnitt, pixelmaps och strängar) som är tillgängliga för program skärmar som definierats för varje bildskärm. Du kan klicka på grupp rubrikerna för resurs visning för att expandera varje grupp och granska grupp innehållet. _*_Bild 7_*_ nedan visar GUIX Studio _ *_vyn resurser_* *.

![Skärm bild av GUIX Studio-Vyn Resurser.](./media/guix-studio/image38.jpg)

**Figur 7**

Namnet på resurs grupperna visar det aktuella temanamn. Om flera teman är tillgängliga kan du växla mellan teman genom att klicka på upp-och nedpilen.

Varje resurs grupp i vyn ovan kan utökas eller komprimeras genom att klicka på grupp rubriken. En mer detaljerad beskrivning av varje resurs grupp följer i nästa kapitel.

## <a name="the-guix-studio-project"></a>GUIX Studio-projektet

Ett GUIX Studio-projekt innehåller information om design för GRÄNSSNITTs skärmen och användar gränssnitts resurser. Projekt data sparas i en XML-formaterad fil med tillägget. ***GXP***". Eftersom projekt filen är en XML-schemafil, kan den vara versions kontrollerad och delas ungefär som andra källfiler.

Första gången du börjar använda GUIX Studio måste du antingen öppna ett av de exempel projekt som medföljer distributionen eller skapa ett nytt projekt. Allt ditt arbete sparas i projekt data filen.

GUIX Studio producerar också ANSI C-källfiler. Dessa källfiler innehåller antingen dina program resurser eller data strukturer som beskriver de utformade skärmarna. GUIX Studio skriver också till dessa genererade API-funktioner för källfiler som används för att använda de genererade data strukturerna för att skapa dina program skärmar dynamiskt. Program varan kommer bara att anropa de tillhandahållna API-funktionerna för att skapa de skärmar som du har utformat i GUIX Studio.

När du arbetar med att designa ditt användar gränssnitt vill du regelbundet använda GUIX Studio för att generera GUIX-kompatibla utdatafiler som gör att du kan skapa och köra gränssnittet som du har utformat. Du kan kompilera och köra de genererade källfilerna för antingen din mål maskin vara eller på Windows-skrivbordet som simulerar ThreadX och GUIX.

## <a name="guix-studio-project-organization"></a>Projekt organisation för GUIX Studio

Det är bra att ha lite kunskap om den grundläggande organisationen av ett GUIX Studio-projekt för att förstå hur du använder GUIX Studio effektivt och för att förstå den information som visas i projektvyn för GUIX Studio IDE. Projektvyn är en sammanfattande visuell representation av all information som finns i ditt projekt.

Innan du kan beskriva projektet är det nödvändigt att definiera några villkor. Först använder vi termen **visning** för att betyda en fysisk visnings enhet. Detta är oftast en LCD-bildskärms enhet, men den kan använda andra tekniker. Nästa term är **skärm**, vilket innebär ett GUIX-objekt på översta nivån, vanligt vis ett GUIX-fönster och alla tillhör ande underordnade element. En skärm är en program varu konstruktion som kan definieras och ändras vid körning. Slutligen är ett **tema** en samling resurser. Ett tema innehåller en tabell med färg definitioner, teckensnitts definitioner och Pixelmap-definitioner som är utformade för att fungera bra tillsammans och presentera slutanvändaren med ett enhetligt utseende och känsla.

Projektet innehåller först en uppsättning global information, till exempel projekt namnet, antalet skärmar som stöds, upplösnings-och färg formatet för varje visning, antalet språk som stöds, namnet på varje språk som stöds. Projekt namnet är den första noden som visas i projektvyn.

Projektet innehåller information om all information som krävs för upp till 4 fysiska skärmar och de skärmar och resurser som är tillgängliga för varje bildskärm. Visnings namnen är noder på nästa nivå i trädvyn projekt.

En unik funktion i GUIX Studio-programmet är inbyggt stöd för flera fysiska skärmar, var och en med sin egen x-, y-upplösning, färg format, skärmar och resurser. Den stora delen av GUIX-program använder bara en fysisk skärm, men den här funktionen är viktig för de som gör en produkt som måste ha stöd för flera samtidiga fysiska skärmar.

Under varje visnings definition är de översta fönster eller skärmar som definierats för den skärmen. Skärm definitionerna kan kapslas till vilken nivå som helst, beroende på antalet och kapslade underordnade widgetar på varje skärm.

Den här skärmen och den underordnade widgets organisationen visas på ett grafiskt sätt i projektvyn.

Även om de är kopplade till varje bildskärm är de teman som stöds av visningen och resurs innehållet som skriver varje tema. Om projektet innehåller flera bildskärmar ser du att Vyn Resurser ändrar innehållet när du väljer en bildskärm och sedan en annan. Detta beror på att resurs innehållet är länkat till varje bildskärm. Inte bara färg formatet kan vara annorlunda, men pixelmaps, färger och teckensnitt som du väljer att använda kan variera beroende på en fysisk visning till en annan.

Den sista komponenten som underhålls av projektet är sträng tabell data som är associerade med varje visning. Eftersom visningen kan vara mycket olika x, y-upplösningar underhålls sträng data oberoende för varje bildskärm som definierats i projektet.
