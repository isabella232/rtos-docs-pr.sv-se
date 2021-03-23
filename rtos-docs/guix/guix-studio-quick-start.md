---
title: ÅTERSTÄLLNINGS tider (Azure Real-Time Opera ting system) GUIX Studio Snabbstartsguide
description: Den här guiden ger en kort introduktion till användningen av Azure återställnings tider GUIX Studio-programmet, Microsoft Windows-baserade Rapid UI utvecklings miljö som är särskilt utformad för Azure återställnings tider GUIX runtime library från Microsoft.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: eedd53867b56312b53f4e9509136ee856acabfd7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827111"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Azure återställnings tider GUIX Studio Snabbstartsguide

Den här guiden ger en kort introduktion till användningen av Azure återställnings tider GUIX Studio. GUIX Studio är ett Windows-baserat GRÄNSSNITTs design program som har utformats för användning med Azure återställnings tider GUIX runtime library från Microsoft. 

Den är avsedd för den inbäddade programutvecklaren i real tid med hjälp av återställnings tider (ThreadX Real-Time Opera ting system) och kör tids biblioteket för Azure återställnings tider GUIX UI. Utvecklaren bör vara bekant med Azure återställnings tider-ThreadX och Azure återställnings tider GUIX-koncept.

## <a name="summary"></a>Sammanfattning

Azure återställnings tider GUIX Studio innehåller allt du behöver för att skapa, bygga och köra en egen grafisk gränssnitts design. Om du utvärderar GUIX Studio är utvärderings paketet utformat för att du ska kunna skapa och köra din GUIX-design som ett fristående Windows-skrivbord för testnings-och utvärderings syfte. Eftersom GUIX har utformats för att användas på nästan alla inbäddade mål som kan användas för grafiska utdata, kan det arbete du gör och de design som du skapar på Skriv bordet alltid kompileras och köras på det inbäddade målet utan att du behöver ändra något av program varan.
Installations programmet för GUIX Studio placerar flera komponenter i utvecklings systemet:

- GUIX Studio-programmet.
- Flera GUIX-exempel projekt.
- Alla grafik resurser och teckensnitt som används i exempel projekt.
- Lösningsfiler och projektfiler för att bygga i en Windows Desktop-miljö med Microsoft Visual Studio IDE.
- Färdiga GUIX-och ThreadX-bibliotek för Win32, så att du kan skapa och köra dina egna program på din dator.
- GUIX-och ThreadX API-huvudfiler.

## <a name="prerequisites"></a>Förutsättningar

Installations programmet för Azure återställnings tider GUIX Studio innehåller flera enkla exempel projekt, och vi räknar med att du börjar med att ändra, skapa och köra dessa exempel när du lär dig hur du använder programmet GUIX Studio. Du behöver en Microsoft Visual Studio-kompilator för att kunna skapa och köra exemplen på Windows-skrivbordet. Dessa verktyg kan hämtas från följande plats:

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Om du inte har installerat Microsoft Developer Tools kan du fortfarande använda däcken och använda GUIX Studio-programmet för att skapa en egen gränssnitts design och undersöka den producerade käll koden. Du kommer dock inte att kunna skapa och köra din design som ett fristående program.

## <a name="running-the-examples"></a>Köra exemplen

När du har kört installations programmet för GUIX Studio hittar du flera exempel Studio-projekt och build-filer ingår i det installerade innehållet. För att kontrol lera att dina Skriv bords verktyg är installerade och fungerar som de ska, rekommenderar vi att du börjar med att skapa och köra var och en av de tillhandahållna exemplen som de är. Vi kommer att referera till din installations katalog som \<root> . i så fall bör du använda din fil läsare och bläddra till \<root> /GUIX_Studio_6. x/exempel. I den här katalogen bör du se flera enkla exempel program som demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types och andra.

## <a name="building-an-example"></a>Skapa ett exempel

Du bör hitta en under katalog med namnet *build* i varje exempel-mapp. I den här riktningen ingår förkonfigurerade projekt för varje verktygskedjan som stöds. Du kan till exempel Bläddra till \<root> /GUIX_Studio_6. x/exempel/termometer/build/vs_2019 och du hittar en förkonfigurerad Microsoft Visual Studio-lösnings fil och en projekt fil som är redo att laddas och köras i Visual Studio IDE. Om du vill använda en annan verktygskedjan kontaktar du [azure_rtos_support](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request).

Vi rekommenderar att du startar Microsoft Visual C++ IDE och öppnar minst ett av följande exempel. Tryck på knappen \<F7> för att skapa exempel projektet och tryck på \<F5> nyckeln för att köra programmet när det har skapats. Nu bör du se ett GUIX-användargränssnitt som körs i ett Microsoft Windows-fönster.

## <a name="designing-and-running-your-own-user-interface"></a>Designa och köra ditt eget användar gränssnitt

Den här snabb starts guiden är inte en ersättning för användar handboken för GUIX Studio eller användar handboken GUIX, men vi kommer att visa dig tillräckligt för att komma igång och uppmana dig att fortsätta med att hänvisa till användar handboken för GUIX Studio för mer detaljerad information.

Det finns två sätt att skapa och ändra ditt eget användar gränssnitt. Du kan studera programmerings hand boken för GUIX-biblioteket och använda GUIX-API: et direkt inifrån program varan för att implementera din design fullständigt. Oftast använder du GUIX Studio-programmet för att utföra de flesta av dina skärm Elements design och layout och slutför sedan händelse hanteringen och annan program logik som krävs för att göra ditt användar gränssnitt till verkligt arbete.

Vart och ett av de tillhandahållna exemplen skapades med GUIX Studio interface design Application. Du bör ha en ikon på Skriv bordet för GUIX Studio 6. x. x när du har kört installations programmet för GUIX Studio.  Starta GUIX Studio nu och öppna projektet med namnet "demo_guix_widget_types \ guix_widget_types. GXP". *Widget_types* demonstration är ett exempel projekt som visar flera varianter av de vanligaste typerna av GUIX-widget.

Nu när du har öppnat ett projekt klickar du på "+" för att öppna trädnoden med namnet "primär" i projektvyn i det övre vänstra hörnet av IDE-fönstret och klickar på den översta nivån i den här mappen med namnet "Menu_Screen". Projektet bör inte visas på det sätt som visas nedan:

![Skärm bild av Studio med projekt öppen.](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>GUIX Studio-vyer

GUIX Studio IDE består av flera ***vyer***. Varje vy är utformad för att hjälpa dig att navigera genom din design och göra ändringar i den designen.

### <a name="project-view"></a>Projektvyn

Den övre vänstra vyn kallas projektvyn. I den här vyn visas var och en av de fysiska skärmar som ingår i ditt projekt (de flesta projekt har bara en visning) och de skärmar och underordnade widgetar som har utformats för att köras på den skärmen.

### <a name="properties-view"></a>Egenskapsvyn

Under projektvyn visas egenskapsvyn. I egenskaps visningen för namn betyder det att du kan ändra widgetar genom att ändra olika egenskaper som är kopplade till dem.

### <a name="target-view"></a>Mål visning

Den centrala visnings ytan kallas för mål visning. Den här vyn är en WYSIWYG visning av ditt användar gränssnitt. Eftersom GUIX-biblioteket är ritat i vyn mål, är den här vyn en pixel korrekt representation av hur din design kommer att se ut när den körs på det inbäddade målet. Om du klickar på olika widgetar, antingen i projektvyn eller i vyn för central mål, visas värdena som visas i vyn egenskaper Visa för att visa egenskaperna för den widget som du har valt.

### <a name="resource-view"></a>Vyn Resurser

Till höger kommer du att se vad som kallas för Vyn Resurser. Med den här vyn kan du välja, lägga till, ta bort och ändra de färger, teckensnitt, pixelmaps och strängar som ingår i projektet.

## <a name="modifying-the-example"></a>Ändra exemplet

GUIX Studio är utformat för att vara intuitivt. Om du vill flytta en av widgetarna som visas ovan klickar du bara på widgeten i vyn mål och drar den till en ny plats. Om du vill ändra färgerna i widgeten klickar du på önskad widget och ändrar de färger som visas i egenskapsvyn. Om du vill ändra teckensnittet som används av widgeten text visning, klickar du bara på det önskade teckensnittet i Vyn Resurser och drar och släpper teckensnittet på den önskade mål-widgeten. Sväva musen längs verktygsfälts knapparna för att se snabb hjälp om den åtgärd som varje knapp utför.

Experimentera själv och gör några mindre ändringar i exemplet. Du kan till exempel dra en widget till en ny plats, ändra ett fönsters bakgrunds färg eller ändra storlek på en knapp. Vi rekommenderar inte att du tar bort några widgetar från exemplet förrän du får mer erfarenhet av att arbeta med GUIX eftersom du kan behöva associerade ändringar i program käll koden för att ta bort widgetar.

## <a name="running-the-application-within-studio"></a>Köra programmet i Studio

Du kan använda redigera | Kör program meny kommandot (eller knappen Kör program i knapp fältet) för att köra programmet direkt i ett nytt Skriv bords fönster. Anpassade ritnings funktioner och annan program kod anropas inte med den här metoden, men det gör att du snabbt kan navigera i användar gränssnitts utformningen och få en övergripande uppfattning om programmets utseende, inklusive navigering från en skärm till nästa.

## <a name="generating-source-files"></a>Genererar källfiler

När du har gjort dina ändringar måste du anropa meny kommandona för GUIX Studio för att generera nya källfiler för projektet. Sedan kan du återskapa exempel programmet för att se hur dina ändringar fungerar. Om du vill generera källfiler, använder du GUIX Studio-Meny kommandon projektet | Generera resursfiler och projekt | Skapa principfiler (du kan också högerklicka på vyn i projektvyn för att köra dessa kommandon).

När du genererar dessa nya källfiler bör du se ett bekräftelse meddelande om att de källfiler som är kopplade till projektet har uppdaterats. Om du inte ser det här bekräftelse meddelandet, kontrol lera att du har Skriv behörighet till katalogen där projektet finns. Nu kan du stänga programmet GUIX Studio. Om du har gjort ändringar i projektet får du en fråga om du vill spara ändringarna i GUIX Studio. Gå vidare och spara dina ändringar. de här exemplen är avsedda att du ska använda och experimentera med när du lär dig att använda GUIX Studio.

### <a name="building-and-running-the-application"></a>Skapa och köra programmet

Nu när GUIX Studio har genererat dina projektfiler kan du kompilera och länka för att skapa en fristående Win32-körbar fil. För att kunna inkludera anpassad ritning eller händelse hantering som du har definierat i ditt program måste du dessutom kompilera och länka utdatafilerna som genereras av GUIX Studio med ditt eget program program. Vi använder Microsoft Visual C++-verktygskedjan som exempel, men exakt samma procedur används om du skapar och kör för det avsedda målet.

- Starta MSVC IDE och öppna lösningen \<root> /GUIX_Studio_5. x/exempel/demo_guix_widget_types/build/vs_2019/guix_widget_types. SLN.

- Använd \<F7> nyckeln för att återskapa lösningen.
- Använd \<F5> nyckeln för att köra programmet.
 
Du bör nu se det program som körs, med de ändringar som du har gjort i Studio!

### <a name="learning-more"></a>Mer information

**Användar handboken för GUIX Studio** finns på [azrtos-GUIX-Studio-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio). Användar handboken för GUIX Studio är en mycket mer grundlig guide för att använda GUIX Studio.

**Användar handboken för GUIX** finns dessutom i [azrtos-GUIX-User-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix).  Den här guiden ger dig mycket mer detaljerad information om vad som händer "under huven" när ditt GUIX-program körs. Du måste referera till båda dessa guider för att kunna använda funktionerna i GUIX runtime library och GUIX Studio.

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

- En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och hur det kan reproduceras tillförlitligt.
- Bifoga spårnings filen som orsakar problemet.
- Den version av Azure återställnings tider GUIX Studio som du använder (visas längst upp till vänster i visningen).
- Den version av Azure återställnings tider-GUIX som du använder, inklusive **_gx_version_idstring** och **_gx_build_options** variabel.
