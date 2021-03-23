---
title: Enkelt exempel projekt
description: I det här kapitlet beskrivs hur du skapar ett exempel projekt i GUIX Studio och kör exemplet på GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826427"
---
# <a name="chapter-10-example-project"></a>Kapitel 10: exempel projekt

I det här kapitlet beskrivs hur du skapar ett exempel projekt i GUIX Studio och kör exemplet på GUIX.

## <a name="create-new-project"></a>Skapa nytt projekt

Det första steget är att skapa ett nytt projekt och konfigurera de skärmar och språk som projektet ska stödja. Första gången du startar GUIX Studio visas skärmen ***senaste projekt*** :

![Skärm bild av dialog rutan senaste projekt i GUIX Studio.](./media/guix-studio/recent_projects.png)

**Figur 10,1**

Klicka på ***Skapa nytt projekt** _... Om du vill starta ett nytt projekt. Du kommer att visas i dialog rutan _ *_nytt GUIX-projekt_** som visas här:

![Skärm bild av dialog rutan skapa nytt projekt i GUIX Studio.](./media/guix-studio/create_new_project.png)

**Figur 10,2**

Skriv namnet "***new_example***" som projekt namn. Projekt namn bör använda standard namngivnings regler för C-variabel, det vill säga inga särskilda eller reserverade tecken. Ange sökvägen till den plats där projektet ska sparas. Sökvägen måste vara en giltig fil system katalog, det vill säga GUIX Studio skapar inte katalogen om den inte finns. Klicka på OK för att skapa projektet.

Nästa skärm bild visas på skärmen projekt konfiguration, som visas här:

![Skärm bild av dialog rutan konfigurera projekt i GUIX Studio.](./media/guix-studio/config_new_project.png)

**Figur 10,3**

Med den här dialog rutan kan du ange hur många som ska visas i projektet och ge varje visning ett namn. Du måste ange färg formatet som stöds av varje bildskärm och eventuellt ange en sökväg för utdatafilerna som genereras av Studio för varje visning. Standard katalogen för utdatafilerna är "***. \\***", vilket innebär att utdatafilerna skrivs till samma katalog som själva projektet.

I det här exemplet lämnar du ***antalet skärmar** _ inställt på "1", skriver namnet "_*_main_display_*_" i fältet visnings namn och kontrollerar "_*_allokera arbets ytans minne_*_". Lämna standardvärdena för lösning, färg format och katalog och klicka på _ *_OK_* *.

Du bör nu se ditt projekt öppet med Studio IDE, som visas i bild 10,4:

![Skärm bild av ett projekt som är öppet med Studio IDE.](./media/guix-studio/initial_screen.png)

**Figur 10,4**

När du skapar ett nytt projekt skapar GUIX Studio automatiskt ett standard fönster som start punkt för projektet. Den här grå rutan är standard fönstret som skapas åt dig, centrerat i *vyn mål*.

Om fönstret inte är markerat klickar du på fönstret så att den streckade markerings rutan ritas runt fönstret. I ***Egenskaper Visa** _, ändra _*_widgeten namn_*_, _*_widgets-ID_*_, _*_vänster_*_, _*_överkant_*_, _*_Bredd_*_, _*_höjd_*_ och _ *_kant linje_** för att matcha de inställningar som visas nedan. När du gör dessa ändringar bör du se till att ändringarna börjar tillämpas i mål visningen.

![Skärm bild av dialog rutan Egenskaper för vy.](./media/guix-studio/initial_window_properties.png)

**Figur 10,5**

Nu ska vi lägga till en Pixelmap-resurs som ska användas i en ***GX_ICON** _-widget. Det finns flera ikoner i din GUIX Studio-distribution som fungerar bra för det här exemplet. Expandera din _*_Pixelmaps_*_ vyn resurser och klicka på knappen _ *_Lägg till ny Pixelmap_**:

![Skärm bild av knappen Lägg till nytt Pixelmap.](./media/guix-studio/image74.jpg)

Bläddra till installationsmappen för GUIX Studio och i mappen ***./Graphics/icons** _ väljer du den fil som heter _*_i_history_lg.png_*_. Klicka på _*_Öppna_*_ för att lägga till den här resursen i projektet. Din _ *_Pixelmaps_** vyn resurser bör nu visa en förhands granskning av den nyligen tillagda ikon bilden:

![Skärm bild av Pixelmaps-Vyn Resurser.](./media/guix-studio/example_add_pixelmap.png)

**Figur 10,6**

Vi kommer att använda den här nya avbildnings resursen senare som en del av vår UI-design.

På samma sätt som du lägger till en Pixelmap-resurs lägger vi till en ny teckensnitts resurs i vårt verktygs låda så att vi kan använda det här teckensnittet senare i vår design. Expandera ***fonts** _ vyn resurser och klicka på knappen _*_Lägg till nytt teckensnitt_*_ . Den här åtgärden kommer att anropa dialog rutan _*_Lägg till/redigera_*_ teckensnitt. Bläddra sedan till de angivna GUIX-teckensnitten i installationsmappen för GUIX Studio _*_ . \\ teckensnitt \\ verasans_ *_, och välj TrueType-teckensnitts filen med namnet _*_VeraIt. ttf_*_. Skriv Font namnet "_*_MEDIUM_ITALIC_*_" i fältet teckensnitts namn och skriv "_*_30_* *" i fältet höjd. Din dialog ruta bör nu se ut så här:

![Skärm bild av dialog rutan Redigera teckensnitt.](./media/guix-studio/example_add_font.png)

**Figur 10,7**

Klicka på ***OK*** för att lägga till det här teckensnittet i projektet. Nu bör du se teckensnittet i Vyn Resurser:

![Skärm bild av teckensnitten i Vyn Resurser.](./media/guix-studio/example_font_added.png)

**Figur 10,8**

Vi kommer att använda det nya teckensnittet senare i vår UI-design.

Nu när vi har några nya tillgängliga resurser måste vi lägga till några underordnade widgetar på skärmen som kan använda dessa resurser. Välj det tidigare skapade fönstret med namnet "***hello_world** _" genom att högerklicka på fönstret i vyn mål. I popup-menyn som visas nu väljer du Meny kommandot _*_Infoga, text, prompt_*_ för att infoga en ny _ *_GX_PROMPT_**-widget och kopplar widgeten till bakgrunds fönstret. Fönstret bör nu se ut så här:

![Skärm bild av en popup-meny med val av prompt](./media/guix-studio/image78.jpg)

**Figur 10,9**

Klicka på teckensnittet "***MEDIUM_ITALIC** _" i _ *_fonts_** vyn resurser och dra och släpp teckensnittet i varnings widgeten. Redigera sedan egenskaperna för prompten som visas i bild 10,10 för att ändra storlek på uppvarningen, ställa in meddelandets transparens och ändra texten och formatet för prompten:

![Skärm bild av fönstret Egenskaper för prompten.](./media/guix-studio/image79.jpg)

**Figur 10,10**

Du kan behöva rulla lodrätt i egenskapsvyn för att se var och en av dessa inställningar, beroende på skärmupplösningen. När du har gjort ändringarna bör mål visningen nu se ut så här:

![Skärm bild av en popup-meny med Hello World valet.](./media/guix-studio/image80.jpg)

**Figur 10,11**

Nu ska vi placera widgeten ikon knapp format på skärmen. Välj bakgrunds fönstret genom att klicka på det och Använd antingen menyn på den översta nivån eller på popup-menyn i snabb menyn för att välja ***Infoga, knapp, knappen ikon** _ för att lägga till en ny _*_GX_ICON_BUTTON_*_ i fönstret. Klicka på ikonen med namnet _ *_I_HISTORY_LG_** som vi lade till tidigare och dra den till ikon knappen. I egenskapsvyn justerar du Ikonens placering och storlek som visas nedan:

![Skärm bild av egenskapsvyn för widgeten knapp format för ikon.](./media/guix-studio/image81.jpg)

**Figur 10,12**

Skärmen bör nu se ut så här:

![Skärm bild av en popup-meny med ikonen Hello World och Urklipp.](./media/guix-studio/image82.jpg)

**Figur 10,13**

Vi kommer att anropa den här åtgärden för den enkla exempel skärm designen. Dina faktiska program skärmar är förmodligen mycket mer sofistikerade, men det räcker med att visa hur du använder GUIX Studio för att skapa dina egna program skärmar.

## <a name="generate-resource-and-application-code"></a>Generera resurs-och program kod

Nästa steg är att generera resurs filen och Specifikations filen som definierar det inbäddade GUIX för körnings gränssnittet. Om du vill generera dina utdatafiler måste du högerklicka på noden ***main_display** _ i projektvyn och välja kommandot _ *_generera resursfiler_**. Du kommer att se ett informations fönster som visar att dina resursfiler har skapats, som du ser i bild 10,14:

![Skärm bild av en meddelande dialog ruta.](./media/guix-studio/image83.jpg)

**Figur 10,14**

Klicka på ***OK** _ för att stänga meddelandet och Använd samma procedur för att högerklicka på _*_main_display_*_ -noden och välj kommandot _ *_generate Specification Files_**. Observera ett liknande meddelande fönster. Nu har du genererat dina enkla UI-programfiler.

## <a name="create-user-supplied-code"></a>Skapa användare angiven kod

Nästa steg är att skapa en egen program fil som kommer att anropa skärm designen GUIX Studio-genererad. Använd önskat redigerings program, skapa en källfil med namnet ***new_example. c*** och ange följande käll kod i den här filen:

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

Käll koden ovan skapar en typisk ThreadX-tråd med namnet `GUIX New Example Thread` med en stack storlek på 4K-byte. Det intressanta arbetet börjar med funktionen som heter ***new_example_thread_entry***. Den här funktionen är den GUIX-angivna tråden börjar köras.

Det första anropet är till funktionen som heter ***gx_system_initialize***. Det här anropet krävs alltid innan andra GUIX-API: er anropas för att förbereda GUIX-biblioteket för första användning.

Sedan anropar exemplet funktionen ***gx_studio_display_configure***. Den här funktionen skapar GUIX-visnings instansen, installerar det begärda språket i program Strängs tabellen, installerar det begärda temat från visnings resurserna och returnerar en pekare till rot fönstret som har skapats för den här visningen. Rot fönstret används som överordnat alla skärmar på den översta nivån som programmet kommer att visa.

Nästa exempel samtal ***gx_studio_named_widget_create** _ för att skapa en instans av vår _ *_hello_world_**-skärm. Den här funktionen använder data strukturerna och resursen som skapas av GUIX Studio för att skapa en instans av skärmen som vi har definierat den. Vi skickar rot fönster pekaren som den andra parametern till det här funktions anropet, vilket innebär att vi vill att skärmen genast ska kopplas till rot fönstret. Den sista parametern är en valfri retur pekare som kan användas om vi vill behålla en pekare till den skapade skärmen.

Nästa ***gx_widget_show** _ anropas, vilket gör rot fönstret och alla dess underordnade, inklusive skärmen _ *_hello_world_** synligt.

Slutligen anropar exemplet ***gx_system_start***. Den här funktionen börjar köra GUIX i system händelse bearbetning.

## <a name="build-and-run-the-example"></a>Skapa och kör exemplet

Att skapa och köra exemplet är särskilt för dina build-verktyg och-miljöer. Vi kan dock definiera den allmänna processen:

1. Skapa ett nytt katalog-och program projekt
1. Lägg till de här filerna i projektet:

    **new_example_resources. c**

    **new_example_specification. c**

    **new_example. c**

1. Lägg till Win32-stöd för körning av filer från installations Sök vägen för GUIX Studio ***./win32_runtime***. Detta inkluderar Win32-sidhuvudet ThreadX och GUIX för körning av filer.
1. Lägg till GUIX Win32-biblioteket (***GX. lib***) i projektet
1. Lägg till ThreadX Win32 Library (***TX. lib***) i projektet
1. Kompilera, länka och kör programmet!
