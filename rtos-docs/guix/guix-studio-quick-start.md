---
title: GUIX Studio Real-Time (RTOS) i Azure Snabbstartsguide
description: Den här guiden ger en kort introduktion till användningen av Azure RTOS GUIX Studio-programmet, Microsoft Windows-baserad snabb UI-utvecklingsmiljö som är särskilt utformad för Azure RTOS GUIX-körningsbiblioteket från Microsoft.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ab4dfb2edd8990692ee3dc134207f43e4c757538dbc738f6f406bf40864bfb3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785432"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Azure RTOS GUIX Studio Snabbstartsguide

Den här guiden ger en kort introduktion till användningen av Azure RTOS GUIX Studio. GUIX Studio är ett Windows-baserat användargränssnittsdesignprogram som utformats för användning med Azure RTOS GUIX-körningsbiblioteket från Microsoft. 

Den är avsedd för den inbäddade realtidsutvecklaren med hjälp av ThreadX Real-Time Operating System (RTOS) och Azure RTOS GUIX UI-körningsbiblioteket. Utvecklaren bör känna till standardkoncepten ThreadX Azure RTOS och Azure RTOS GUIX.

## <a name="summary"></a>Sammanfattning

Azure RTOS GUIX Studio innehåller allt du behöver för att skapa, skapa och köra en egen grafisk gränssnittsdesign. Om du utvärderar GUIX Studio är utvärderingspaketet utformat så att du kan skapa och köra GUIX-designen som ett fristående Windows-skrivbordsprogram i test- och utvärderingssyfte. Eftersom GUIX är utformat för användning på nästan alla inbäddade mål som kan grafisk utdata, kan det arbete du gör och de designer som du skapar på skrivbordet alltid kompileras och köras på ditt inbäddade mål utan att ändra någon av dina programprogramvara.
Installationsprogrammet för GUIX Studio placerar flera komponenter i ditt utvecklingssystem:

- GUIX Studio-programmet.
- Flera GUIX-exempelprojekt.
- Alla grafikresurser och teckensnitt som används i exempelprojekten.
- Lösningsfiler och projektfiler för att skapa i en Windows skrivbordsmiljö med Microsoft Visual Studio IDE.
- Förbyggda GUIX- och ThreadX-bibliotek för Win32, så att du kan skapa och köra egna program på datorn.
- GUIX- och ThreadX API-huvudfiler.

## <a name="prerequisites"></a>Förutsättningar

Installationsprogrammet Azure RTOS GUIX Studio innehåller flera enkla exempelprojekt och vi förväntar oss att du börjar med att ändra, skapa och köra de här exemplen när du lär dig hur du använder GUIX Studio-programmet. För att kunna skapa och köra exemplen på Windows desktop behöver du en Microsoft Visual Studio-kompilator. Dessa verktyg kan laddas ned från följande plats:

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Om du inte har Microsoft-utvecklarverktygen installerade kan du fortfarande sätta igång och använda GUIX Studio-programmet för att skapa en egen gränssnittsdesign och undersöka källkoden som skapas. Du kommer dock inte att kunna skapa och köra din design som ett fristående program.

## <a name="running-the-examples"></a>Köra exemplen

När du har kört installationsprogrammet för GUIX Studio hittar du flera exempelprojekt i Studio och byggfiler ingår i det installerade innehållet. För att kontrollera att dina skrivbordsverktyg är installerade och fungerar som de ska rekommenderar vi att du börjar med att skapa och köra vart och ett av de angivna exemplen i dess ordning. Vi refererar till installationskatalogen som . I så fall bör du använda filwebbläsaren och \<root> \<root> bläddra till /GUIX_Studio_6.x/examples. I den här katalogen bör du se flera enkla exempelprogram som demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types och andra.

## <a name="building-an-example"></a>Skapa ett exempel

Du bör hitta en underkatalog med namnet *build i* varje exempelmapp. Den här riktningen omfattar förkonfigurerade projekt för varje verktygskedja som stöds. Du kan till exempel bläddra till /GUIX_Studio_6.x/examples/termmeter/build/vs_2019 så hittar du en förkonfigurerad Microsoft Visual Studio-lösningsfil och projektfil som är redo att läsas in och köras \<root> i Visual Studio IDE. Om du vill använda en annan verktygskedja kontaktar du [azure_rtos_support](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request).

Vi rekommenderar att du startar Microsoft Visual C++ IDE och öppnar minst ett av dessa exempel. Tryck på \<F7> tangenten för att skapa exempelprojektet och tryck på \<F5> tangenten för att köra programmet när det har skapats. Nu bör du se ett GUIX-användargränssnitt som körs i ett Microsoft Windows-fönster.

## <a name="designing-and-running-your-own-user-interface"></a>Utforma och köra egna Användargränssnitt

Den här snabbstartsguiden ersätter inte GUIX Studio-användarhandboken eller GUIX-användarhandboken, men vi visar dig tillräckligt för att komma igång och uppmuntrar dig att fortsätta genom att referera till ANVÄNDARhandboken för GUIX Studio för mer detaljerad information.

Det finns två metoder för att skapa och ändra ditt eget användargränssnitt. Du kan studera programmeringshandboken för GUIX-biblioteket och använda GUIX-API:et direkt från din programprogramvara för att implementera din design fullt ut. Oftare använder du GUIX Studio-programmet för att utföra det mesta av design- och layoutarbetet för dina skärmelement och sedan slutföra händelsehanteringen och annan programlogik som krävs för att användargränssnittet ska fungera.

Vart och ett av de angivna exemplen har skapats med hjälp av GUIX Studio-gränssnittets designprogram. Du bör ha en ikon på skrivbordet för GUIX Studio 6.x.x.x när du har kört installationsprogrammet för GUIX Studio.  Starta GUIX Studio nu och öppna projektet med namnet "demo_guix_widget_types\guix_widget_types.gxp". Demonstrationen *widget_types* är ett exempelprojekt som visar flera varianter av de vanligaste GUIX-widgettyperna.

Nu när projektet är öppet klickar du på "+" för att öppna trädnoden med namnet "Primary" i Project View i det övre vänstra hörnet av IDE och klickar på det översta fönstret i den här mappen med namnet "Menu_Screen". Projektet bör inte visas enligt nedan:

![Skärmbild av Studio med projektet öppet.](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>GUIX Studio-vyer

GUIX Studio IDE består av flera ***vyer.*** Varje vy är utformad för att hjälpa dig att navigera genom din design och göra ändringar i den designen.

### <a name="project-view"></a>Project Visa

Den övre vänstra vyn kallas för Project Vy. Den här vyn visar var och en av de fysiska skärmarna som ingår i projektet (de flesta projekt har bara en visning) och skärmarna och underordnade widgetar som har utformats för att köras på den visningen.

### <a name="properties-view"></a>Egenskapsvy

Under Project vy visas egenskapsvyn. Som namnet Egenskapsvy antyder kan du med den här vyn ändra widgetar genom att ändra olika egenskaper som är associerade med dem.

### <a name="target-view"></a>Målvy

Det centrala visningsområdet kallas målvyn. Den här vyn är en WYSIWYG-visning av användargränssnittet. Eftersom GUIX-biblioteket ritas i målvyn är den här vyn en pixelrepresentation av hur din design kommer att se ut när den körs på det inbäddade målet. Om du klickar på olika widgetar antingen i Project-vyn eller den centrala målvyn visas värdena som visas i egenskapsvyn för att visa egenskaperna för den widget som du har valt.

### <a name="resource-view"></a>Vyn Resurser

Till höger ser du slutligen vad som kallas för Vyn Resurser. I den här vyn kan du välja, lägga till, ta bort och ändra färger, teckensnitt, pixelkartor och strängar som ingår i projektet.

## <a name="modifying-the-example"></a>Ändra exemplet

GUIX Studio är utformat för att vara intuitivt. Om du vill flytta en av widgetarna som visas ovan klickar du bara på widgeten i målvyn och drar den till en ny plats. Om du vill ändra widgetens färger klickar du på önskad widget och ändrar färgerna som visas i egenskapsvyn. Om du vill ändra teckensnittet som används av en textvisningswidget klickar du bara på önskat teckensnitt i Vyn Resurser och drar och släpper teckensnittet till önskad målwidget. Flytta musen längs knapparna i verktygsfältet för att se snabb hjälp om den åtgärd som varje knapp utför.

Experimentera själv och gör några mindre ändringar i exemplet. Du kan till exempel dra en widget till en ny plats, ändra en fönsterbakgrundsfärg eller ändra storlek på en knapp. Vi rekommenderar inte att du tar bort några widgetar från exemplet förrän du får mer erfarenhet av att arbeta med GUIX eftersom det kan krävas associerade ändringar i programmets källkod för att ta bort widgetar.

## <a name="running-the-application-within-studio"></a>Köra programmet i Studio

Du kan använda redigera-| Kör menykommandot Program (eller knappen Kör program i knappfältet) för att köra programmet direkt i ett nytt skrivbordsfönstret. Anpassade ritningsfunktioner och annan programkod anropas inte med den här metoden, men det gör att du snabbt kan navigera i användargränssnittets design och få en övergripande uppfattning om programmets utseende och känsla, inklusive navigering från en skärm till nästa.

## <a name="generating-source-files"></a>Generera källfiler

När du har gjort ändringarna måste du anropa GUIX Studio-menykommandon för att generera nya källfiler för projektet. Du kan sedan återskapa exempelprogrammet för att se hur ändringarna fungerar. Om du vill generera källfiler använder du GUIX Studio-menykommandona Project| Generera resursfiler och Project| Generera specifikationsfiler (du kan också högerklicka på skärmen i Project för att köra dessa kommandon).

När du genererar dessa nya källfiler bör du se ett bekräftelsemeddelande som talar om att källfilerna som är associerade med projektet har uppdaterats. Om du inte ser det här bekräftelsemeddelandet kontrollerar du att du har skrivbehörighet till katalogen där projektet finns. Nu kan du stänga GUIX Studio-programmet. Om du har gjort ändringar i projektet frågar GUIX Studio dig om du vill spara ändringarna. Spara ändringarna. De här exemplen är avsedda att användas och experimentera med när du lär dig att använda GUIX Studio.

### <a name="building-and-running-the-application"></a>Skapa och köra programmet

Nu när GUIX Studio har genererat dina projektutdatafiler kan du kompilera och länka för att skapa en fristående körbar Win32-fil. För att införliva anpassad ritning eller händelsehantering som du har definierat i ditt program måste du dessutom kompilera och länka utdatafilerna som genereras av GUIX Studio med din egen programprogramvara. Vi använder Microsoft Visual C++-verktygskedja som exempel, men exakt samma procedur används om du skapar och kör för det avsedda målet.

- Starta MSVC IDE och öppna lösningen \<root> /GUIX_Studio_5.x/examples/demo_guix_widget_types/build/vs_2019/guix_widget_types.sln.

- Använd nyckeln \<F7> för att återskapa lösningen.
- Använd nyckeln \<F5> för att köra programmet.
 
Du bör nu se det program som körs med de ändringar du har gjort i Studio!

### <a name="learning-more"></a>Mer information

**Användarhandboken för GUIX Studio** finns på [azrtos-guix-studio-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio). Användarhandboken för GUIX Studio är en mycket mer omfattande guide för att använda GUIX Studio.

Dessutom finns **GUIX-användarhandboken** på [azrtos-guix-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix).  Den här guiden ger dig mycket mer detaljerad information om vad som händer "Under huven" när ditt GUIX-program körs. Du måste referera till båda dessa guider för att kunna utnyttja funktionerna i GUIX-körningsbiblioteket och GUIX Studio fullt ut.

## <a name="customer-support-center"></a>Kundsupport

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

- En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och hur det kan återskapas på ett tillförlitligt sätt.
- Bifoga den spårningsfil som orsakar problemet.
- Den version Azure RTOS GUIX Studio som du använder (visas längst upp till vänster på skärmen).
- Den version av Azure RTOS GUIX som du använder, inklusive **variabeln _gx_version_idstring** **och _gx_build_options.**
