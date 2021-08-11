---
title: Enkelt exempel på Project
description: I det här kapitlet beskrivs hur du skapar ett exempelprojekt i GUIX Studio och kör exemplet på GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8981bed62d2929703e4233d6a3ee31b692226c26d046875a235bf3aca32a7573
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786659"
---
# <a name="chapter-10-example-project"></a>Kapitel 10: Exempel Project

I det här kapitlet beskrivs hur du skapar ett exempelprojekt i GUIX Studio och kör exemplet på GUIX.

## <a name="create-new-project"></a>Skapa nytt projekt

Det första steget är att skapa ett nytt projekt och konfigurera de skärmar och språk som projektet ska stödja. Första gången du startar GUIX Studio visas skärmen ***Senaste*** projekt:

![Skärmbild av dialogrutan SENASTE PROJEKT i GUIX Studio.](./media/guix-studio/recent_projects.png)

**Bild 10.1**

Klicka på ***Skapa ny Project** _... för att starta ett nytt projekt. Dialogrutan _ New *_GUIX Project_** visas här:

![Skärmbild av dialogrutan SKAPA ny Project GUIX Studio.](./media/guix-studio/create_new_project.png)

**Bild 10.2**

Skriv namnet "***new_example***" som projektnamn. Project namn ska använda standardnamnregler för C-variabler, det vill säga inga särskilda eller reserverade tecken. Ange sökvägen till den plats där projektet ska sparas. Sökvägen måste vara en giltig filsystemkatalog, det vill säga GUIX Studio skapar inte katalogen om den inte finns. Klicka på OK för att skapa projektet.

Nästa skärm som visas är Project konfigurationsskärmen, som visas här:

![Skärmbild av dialogrutan KONFIGURERA Project GUIX Studio.](./media/guix-studio/config_new_project.png)

**Bild 10.3**

I den här dialogrutan kan du ange hur många visningar projektet ska stödja och ge varje visning ett namn. Du måste ange färgformatet som stöds av varje visning och eventuellt ange ett sökvägsnamn för de utdatafiler som genereras av Studio för varje visning. Standardkatalogen för utdatafilerna är "***. \\***", vilket innebär att C-utdatafilerna skrivs till samma katalog som själva projektet.

I det här exemplet lämnar du ***Antal** skärmar _ inställt på "1", skriver namnet "_*_main_display_*_" i fältet visningsnamn och markerar "_*_allokera arbetsyteminne_*_". Lämna standardvärdena för fälten upplösning, färgformat och katalog och klicka på _*_OK_**.

Nu bör du se att projektet är öppet med Studio IDE, som du ser i bild 10.4:

![Skärmbild av ett projekt som är öppet med Studio IDE.](./media/guix-studio/initial_screen.png)

**Bild 10.4**

När du skapar ett nytt projekt skapar GUIX Studio automatiskt ett standardfönster som startpunkt för projektet. Den här grå rutan är standardfönstret som skapats åt dig, centrerat i *målvyn*.

Om det här fönstret inte är markerat klickar du på fönstret så att den streckade markeringsrutan ritas runt fönstret. I **egenskapsvyn** _ ändrar du widgetens namn, _*_widget-ID,_*_ _*_vänster,_*_ överkant, _**_ _*_bredd,_*_ _*_höjd_*_ och *___* kantlinje * så att de matchar de inställningar som visas nedan. _**_ När du gör dessa ändringar bör du se att ändringarna börjar gälla omedelbart i målvyn.

![Skärmbild av dialogrutan Egenskapsvy.](./media/guix-studio/initial_window_properties.png)

**Bild 10.5**

Nu ska vi lägga till en pixelkarta-resurs som ska användas i en ***GX_ICON** _ widget. Det finns flera ikoner i GUIX Studio-distributionen som fungerar bra i det här exemplet. Expandera din _*_Pixelmaps Vyn Resurser_*_ klicka på knappen _ *_Lägg till ny pixelkarta_** :

![Skärmbild av knappen Lägg till ny pixelkarta.](./media/guix-studio/image74.jpg)

Bläddra till installationsmappen för GUIX Studio och i mappen ***./graphics/icons** _ väljer du filen med _*_namneti_history_lg.png_*_. Klicka _*_på Öppna_*_ för att lägga till den här resursen i projektet. Din _ *_Pixelmaps_** Vyn Resurser nu visa en förhandsgranskning av den nyligen tillagda ikonbilden:

![Skärmbild av pixelkartor Vyn Resurser.](./media/guix-studio/example_add_pixelmap.png)

**Bild 10.6**

Vi kommer att använda den här nya avbildningsresursen senare som en del av vår ui-design.

På samma sätt som vi lägger till en pixelkarta-resurs lägger vi till en ny teckensnittsresurs i vår verktygslåda så att vi kan använda det här teckensnittet senare i vår design. Expandera knappen ***Teckensnitt** _ Vyn Resurser och klicka på knappen _*_Lägg till nytt_*_ teckensnitt. Den här åtgärden anropar _*_dialogrutan Lägg till/redigera_*_ teckensnitt. Bläddra sedan till de angivna GUIX-teckensnitten i GUIX Studio-installationsmappen, _*_ . \\ font \\ verasans_ *_, och välj TrueType-teckensnittsfilen med namnet _*_VeraIt.ttf_*_. Skriv teckensnitt teckensnittsnamnet "_*_MEDIUM_ITALIC_" i fältet *_teckensnittsnamn_* och skriv "_30_**" i fältet height. Dialogrutan bör nu se ut så här:

![Skärmbild av dialogrutan Redigera teckensnitt.](./media/guix-studio/example_add_font.png)

**Bild 10.7**

Klicka ***på OK*** för att lägga till teckensnittet i projektet. Du bör nu se teckensnittet i Vyn Resurser:

![Skärmbild av Teckensnitt i Vyn Resurser.](./media/guix-studio/example_font_added.png)

**Bild 10.8**

Vi kommer att använda det här nya teckensnittet senare i vår ui-design.

Nu när vi har några nya resurser tillgängliga måste vi lägga till några underordnade widgetar på skärmen som kan använda dessa resurser. Välj det tidigare skapade fönstret med namnet "***hello_world** _" genom att högerklicka på fönstret i målvyn. I popup-menyn som nu visas väljer du menykommandot _*_Infoga, Text, Fråga_*_ för att infoga en ny _ *_GX_PROMPT_** widget och koppla widgeten till bakgrundsfönstret. Fönstret bör nu se ut så här:

![Skärmbild av en popup-meny med valet Fråga](./media/guix-studio/image78.jpg)

**Bild 10.9**

Klicka på teckensnittet med namnet "***MEDIUM_ITALIC** _" i _ *_Teckensnitt_** Vyn Resurser och dra och släpp teckensnittet i widgeten för prompten. Redigera sedan promptegenskaperna enligt bild 10.10 för att ändra storlek på prompten, ange promptens transparens och ändra text och stil för prompten:

![Skärmbild av egenskapsvyn för prompten.](./media/guix-studio/image79.jpg)

**Bild 10.10**

Du kan behöva rulla lodrätt i egenskapsvyn för att se var och en av dessa inställningar beroende på skärmupplösningen. När du har gjort dessa ändringar bör målvyn nu se ut så här:

![Skärmbild av en popup-meny med Hello World val.](./media/guix-studio/image80.jpg)

**Bild 10.11**

Nu ska vi placera en widget för ikonknappstil på skärmen. Välj bakgrundsfönstret genom att klicka på det och använd antingen menyn på den översta nivån eller snabbmenyn genom att högerklicka för att välja ***Infoga, Knapp, Ikonknapp** _ för att lägga till _*_en ny GX_ICON_BUTTON_*_ i fönstret. Klicka på ikonen med namnet _ *_I_HISTORY_LG_** som vi lade till tidigare och dra den till ikonknappen. Använd egenskapsvyn och justera ikonens position och storlek enligt nedan:

![Skärmbild av egenskapsvyn för widgeten för ikonknappstil.](./media/guix-studio/image81.jpg)

**Bild 10.12**

Skärmen bör nu se ut så här:

![Skärmbild av en popup-meny med ikonen Hello World och Urklipp.](./media/guix-studio/image82.jpg)

**Bild 10.13**

Vi kallar detta fullständigt för den enkla exempelskärmsdesignen. Dina faktiska programskärmar kommer förmodligen att vara mycket mer avancerade, men det är tillräckligt för att visa dig hur du använder GUIX Studio för att skapa egna programskärmar.

## <a name="generate-resource-and-application-code"></a>Generera resurs- och programkod

Nästa steg är att generera resursfilen och specifikationsfilen som definierar det inbäddade GUIX-körningsgränssnittet. För att generera dina utdatafiler måste du högerklicka på noden ***main_display** _ i Project View och välja kommandot _ *_Generate Resource Files_** (Skapa resursfiler). Du ser ett informationsfönster som anger att dina resursfiler har genererats, som du ser i bild 10.14:

![Skärmbild av en meddelandedialogruta.](./media/guix-studio/image83.jpg)

**Bild 10.14**

Klicka på ***OK** _ för att stänga det här meddelandet och använd samma procedur för att högerklicka på _*_noden main_display_*_ och välj kommandot _ Generate Specification Files * (Skapa *_specifikationsfiler)._* Du bör se ett liknande meddelandefönster. Nu har du genererat dina enkla UI-programfiler.

## <a name="create-user-supplied-code"></a>Skapa kod som anges av användaren

Nästa steg är att skapa en egen programfil som anropar den GUIX Studio-genererade skärmdesignen. Skapa en källfil med namnet ***new_example.c*** med önskat redigeringsprogram och ange följande källkod i den här filen:

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

Källkoden ovan skapar en typisk ThreadX-tråd med `GUIX New Example Thread` namnet med en stackstorlek på 4 000 byte. Det intressanta arbetet börjar i funktionen med namnet ***new_example_thread_entry***. Den här funktionen är den plats där den GUIX-specifika tråden börjar köras.

Det första anropet är till funktionen med ***namnet gx_system_initialize***. Det här anropet krävs alltid innan andra GUIX-API:er anropas för att förbereda GUIX-biblioteket för första användning.

Sedan anropar exemplet funktionen ***gx_studio_display_configure***. Den här funktionen skapar GUIX-visningsinstansen, installerar det begärda språket i programsträngtabellen, installerar det begärda temat från visningsresurserna och returnerar en pekare till rotfönstret som har skapats för den här visningen. Rotfönstret används som överordnat till alla toppnivåskärmar som vårt program kommer att visa.

I exemplet anropas ***gx_studio_named_widget_create** _ för att skapa en instans av skärmen _ *_hello_world_** . Den här funktionen använder de datastrukturer och resurser som skapas av GUIX Studio för att skapa en instans av skärmen som vi har definierat den. Vi skickar pekaren för rotfönstret som den andra parametern till det här funktionsanropet, vilket innebär att vi vill att skärmen ska kopplas direkt till rotfönstret. Den sista parametern är en valfri returpekare som kan användas om vi vill behålla en pekare till den skapade skärmen.

Nästa ***gx_widget_show** _ anropas, vilket gör rotfönstret och alla underordnade fönster, inklusive skärmen _ *_hello_world_** synlig.

Slutligen anropar exemplet ***gx_system_start***. Den här funktionen börjar köra GUIX-systemhändelsebearbetningsloopen.

## <a name="build-and-run-the-example"></a>Skapa och kör exemplet

Att skapa och köra exemplet är specifikt för dina byggverktyg och din miljö. Vi kan dock definiera den allmänna processen:

1. Skapa en ny katalog och ett nytt programprojekt
1. Lägg till de här filerna i projektet:

    **new_example_resources.c**

    **new_example_specification.c**

    **new_example.c**

1. Lägg till Win32-körningsstödfilerna från GUIX Studio-installationssökvägen ***./win32_runtime***. Detta inkluderar ThreadX- och GUIX Win32-huvudet och körningsbiblioteksfilerna.
1. Lägg till GUIX Win32-biblioteket (***gx.lib***) i projektet
1. Lägga till ThreadX Win32-biblioteket (***tx.lib***) i projektet
1. Kompilera, länka och kör programmet!
