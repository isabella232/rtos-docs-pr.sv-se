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
# <a name="chapter-10-example-project"></a><span data-ttu-id="3a00e-103">Kapitel 10: exempel projekt</span><span class="sxs-lookup"><span data-stu-id="3a00e-103">Chapter 10: Example Project</span></span>

<span data-ttu-id="3a00e-104">I det här kapitlet beskrivs hur du skapar ett exempel projekt i GUIX Studio och kör exemplet på GUIX.</span><span class="sxs-lookup"><span data-stu-id="3a00e-104">This chapter describes how to create an example project in GUIX Studio and execute the example on GUIX.</span></span>

## <a name="create-new-project"></a><span data-ttu-id="3a00e-105">Skapa nytt projekt</span><span class="sxs-lookup"><span data-stu-id="3a00e-105">Create New Project</span></span>

<span data-ttu-id="3a00e-106">Det första steget är att skapa ett nytt projekt och konfigurera de skärmar och språk som projektet ska stödja.</span><span class="sxs-lookup"><span data-stu-id="3a00e-106">The first step is creating a new project and configuring the displays and languages that the project will support.</span></span> <span data-ttu-id="3a00e-107">Första gången du startar GUIX Studio visas skärmen ***senaste projekt*** :</span><span class="sxs-lookup"><span data-stu-id="3a00e-107">When you first start GUIX Studio, you will see the ***Recent Projects*** screen:</span></span>

![Skärm bild av dialog rutan senaste projekt i GUIX Studio.](./media/guix-studio/recent_projects.png)

<span data-ttu-id="3a00e-109">**Figur 10,1**</span><span class="sxs-lookup"><span data-stu-id="3a00e-109">**Figure 10.1**</span></span>

<span data-ttu-id="3a00e-110">Klicka på \***Skapa nytt projekt** _...</span><span class="sxs-lookup"><span data-stu-id="3a00e-110">Click on the \***Create New Project** _…</span></span> <span data-ttu-id="3a00e-111">Om du vill starta ett nytt projekt.</span><span class="sxs-lookup"><span data-stu-id="3a00e-111">button to begin a new project.</span></span> <span data-ttu-id="3a00e-112">Du kommer att visas i dialog rutan _ *_nytt GUIX-projekt_*\* som visas här:</span><span class="sxs-lookup"><span data-stu-id="3a00e-112">You will be presented with the _ *_New GUIX Project_*\* dialog, shown here:</span></span>

![Skärm bild av dialog rutan skapa nytt projekt i GUIX Studio.](./media/guix-studio/create_new_project.png)

<span data-ttu-id="3a00e-114">**Figur 10,2**</span><span class="sxs-lookup"><span data-stu-id="3a00e-114">**Figure 10.2**</span></span>

<span data-ttu-id="3a00e-115">Skriv namnet "***new_example***" som projekt namn.</span><span class="sxs-lookup"><span data-stu-id="3a00e-115">Type the name "***new_example***" as the project name.</span></span> <span data-ttu-id="3a00e-116">Projekt namn bör använda standard namngivnings regler för C-variabel, det vill säga inga särskilda eller reserverade tecken.</span><span class="sxs-lookup"><span data-stu-id="3a00e-116">Project names should use standard C variable naming rules, that is, no special or reserved characters.</span></span> <span data-ttu-id="3a00e-117">Ange sökvägen till den plats där projektet ska sparas.</span><span class="sxs-lookup"><span data-stu-id="3a00e-117">Type the path to the location where the project should be saved.</span></span> <span data-ttu-id="3a00e-118">Sökvägen måste vara en giltig fil system katalog, det vill säga GUIX Studio skapar inte katalogen om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="3a00e-118">The path must be a valid file system directory, that is, GUIX Studio will not create the directory if it does not exist.</span></span> <span data-ttu-id="3a00e-119">Klicka på OK för att skapa projektet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-119">Click "OK" to create the project.</span></span>

<span data-ttu-id="3a00e-120">Nästa skärm bild visas på skärmen projekt konfiguration, som visas här:</span><span class="sxs-lookup"><span data-stu-id="3a00e-120">The next screen shown is the Project Configuration screen, shown here:</span></span>

![Skärm bild av dialog rutan konfigurera projekt i GUIX Studio.](./media/guix-studio/config_new_project.png)

<span data-ttu-id="3a00e-122">**Figur 10,3**</span><span class="sxs-lookup"><span data-stu-id="3a00e-122">**Figure 10.3**</span></span>

<span data-ttu-id="3a00e-123">Med den här dialog rutan kan du ange hur många som ska visas i projektet och ge varje visning ett namn.</span><span class="sxs-lookup"><span data-stu-id="3a00e-123">This dialog allows you to specify how many displays your project will support, and give a name to each display.</span></span> <span data-ttu-id="3a00e-124">Du måste ange färg formatet som stöds av varje bildskärm och eventuellt ange en sökväg för utdatafilerna som genereras av Studio för varje visning.</span><span class="sxs-lookup"><span data-stu-id="3a00e-124">You must specify the color format supported by each display, and optionally type a pathname for the output files generated by Studio for each display.</span></span> <span data-ttu-id="3a00e-125">Standard katalogen för utdatafilerna är "***. \\***", vilket innebär att utdatafilerna skrivs till samma katalog som själva projektet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-125">The default directory for the output files is "***.\\***", meaning the C output files are written to the same directory as the project itself.</span></span>

<span data-ttu-id="3a00e-126">I det här exemplet lämnar du ***antalet skärmar** _ inställt på "1", skriver namnet "_*_main_display_*_" i fältet visnings namn och kontrollerar "_*_allokera arbets ytans minne_\*_".</span><span class="sxs-lookup"><span data-stu-id="3a00e-126">For this example, leave the ***Number of Displays** _ set to "1", type the name "_*_main_display_*_" in the display name field, and check "_*_allocate canvas memory_\*_".</span></span> <span data-ttu-id="3a00e-127">Lämna standardvärdena för lösning, färg format och katalog och klicka på _ *_OK_* \*.</span><span class="sxs-lookup"><span data-stu-id="3a00e-127">Leave the resolution, color format, and directory fields at their default values, and click _\*_OK_\*\*.</span></span>

<span data-ttu-id="3a00e-128">Du bör nu se ditt projekt öppet med Studio IDE, som visas i bild 10,4:</span><span class="sxs-lookup"><span data-stu-id="3a00e-128">You should now see your project open with the Studio IDE, as shown in figure 10.4:</span></span>

![Skärm bild av ett projekt som är öppet med Studio IDE.](./media/guix-studio/initial_screen.png)

<span data-ttu-id="3a00e-130">**Figur 10,4**</span><span class="sxs-lookup"><span data-stu-id="3a00e-130">**Figure 10.4**</span></span>

<span data-ttu-id="3a00e-131">När du skapar ett nytt projekt skapar GUIX Studio automatiskt ett standard fönster som start punkt för projektet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-131">When you create a new project, GUIX Studio automatically creates a default window as the starting point for your project.</span></span> <span data-ttu-id="3a00e-132">Den här grå rutan är standard fönstret som skapas åt dig, centrerat i *vyn mål*.</span><span class="sxs-lookup"><span data-stu-id="3a00e-132">This gray box is the default window created for you, centered within the *Target View*.</span></span>

<span data-ttu-id="3a00e-133">Om fönstret inte är markerat klickar du på fönstret så att den streckade markerings rutan ritas runt fönstret.</span><span class="sxs-lookup"><span data-stu-id="3a00e-133">If this window is not selected, click on the window so that the dashed selection box is drawn around the window.</span></span> <span data-ttu-id="3a00e-134">I ***Egenskaper Visa** _, ändra _*_widgeten namn_*_, _*_widgets-ID_*_, _*_vänster_*_, _*_överkant_*_, _*_Bredd_*_, _*_höjd_*_ och _ *_kant linje_** för att matcha de inställningar som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="3a00e-134">Now in the ***Properties View** _, change the _*_Widget Name_*_, _*_Widget Id_*_, _*_Left_*_, _*_Top_*_, _*_Width_*_, _*_Height_*_, and _ *_Border_** to match those settings shown below.</span></span> <span data-ttu-id="3a00e-135">När du gör dessa ändringar bör du se till att ändringarna börjar tillämpas i mål visningen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-135">As you make these changes, you should see your changes immediately taking effect within the Target View.</span></span>

![Skärm bild av dialog rutan Egenskaper för vy.](./media/guix-studio/initial_window_properties.png)

<span data-ttu-id="3a00e-137">**Figur 10,5**</span><span class="sxs-lookup"><span data-stu-id="3a00e-137">**Figure 10.5**</span></span>

<span data-ttu-id="3a00e-138">Nu ska vi lägga till en Pixelmap-resurs som ska användas i en \***GX_ICON** _-widget.</span><span class="sxs-lookup"><span data-stu-id="3a00e-138">Next we will add a pixelmap resource to be used within a \***GX_ICON** _ widget.</span></span> <span data-ttu-id="3a00e-139">Det finns flera ikoner i din GUIX Studio-distribution som fungerar bra för det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-139">Several icons are provided with your GUIX Studio distribution that will work fine for this example.</span></span> <span data-ttu-id="3a00e-140">Expandera din _*_Pixelmaps_*_ vyn resurser och klicka på knappen _ \*_Lägg till ny Pixelmap_\*\*:</span><span class="sxs-lookup"><span data-stu-id="3a00e-140">Expand your _*_Pixelmaps_*_ Resource View and click the _ *_Add New Pixelmap_*\* button:</span></span>

![Skärm bild av knappen Lägg till nytt Pixelmap.](./media/guix-studio/image74.jpg)

<span data-ttu-id="3a00e-142">Bläddra till installationsmappen för GUIX Studio och i mappen ***./Graphics/icons** _ väljer du den fil som heter _*_i_history_lg.png_\*_.</span><span class="sxs-lookup"><span data-stu-id="3a00e-142">Browse to your GUIX Studio installation folder, and within the ***./graphics/icons** _ folder select the file named _*_i_history_lg.png_\*_.</span></span> <span data-ttu-id="3a00e-143">Klicka på _\*_Öppna_\*_ för att lägga till den här resursen i projektet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-143">Click _*_Open_*_ to add this resource to your project.</span></span> <span data-ttu-id="3a00e-144">Din _ *_Pixelmaps_*\* vyn resurser bör nu visa en förhands granskning av den nyligen tillagda ikon bilden:</span><span class="sxs-lookup"><span data-stu-id="3a00e-144">Your _ *_Pixelmaps_*\* Resource View should now show a preview of the newly added icon image:</span></span>

![Skärm bild av Pixelmaps-Vyn Resurser.](./media/guix-studio/example_add_pixelmap.png)

<span data-ttu-id="3a00e-146">**Figur 10,6**</span><span class="sxs-lookup"><span data-stu-id="3a00e-146">**Figure 10.6**</span></span>

<span data-ttu-id="3a00e-147">Vi kommer att använda den här nya avbildnings resursen senare som en del av vår UI-design.</span><span class="sxs-lookup"><span data-stu-id="3a00e-147">We will use this new image resource later as part of our UI design.</span></span>

<span data-ttu-id="3a00e-148">På samma sätt som du lägger till en Pixelmap-resurs lägger vi till en ny teckensnitts resurs i vårt verktygs låda så att vi kan använda det här teckensnittet senare i vår design.</span><span class="sxs-lookup"><span data-stu-id="3a00e-148">Similar to adding a pixelmap resource, we will add a new font resource to our toolbox so that we can use this font later in our design.</span></span> <span data-ttu-id="3a00e-149">Expandera ***fonts** _ vyn resurser och klicka på knappen _*_Lägg till nytt teckensnitt_\*_ .</span><span class="sxs-lookup"><span data-stu-id="3a00e-149">Expand the ***Fonts** _ Resource View and click on the _*_Add New Font_\*_ button.</span></span> <span data-ttu-id="3a00e-150">Den här åtgärden kommer att anropa dialog rutan _*_Lägg till/redigera_*_ teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="3a00e-150">This action will invoke the _*_Add/Edit_*_ font dialog.</span></span> <span data-ttu-id="3a00e-151">Bläddra sedan till de angivna GUIX-teckensnitten i installationsmappen för GUIX Studio _\*_ . \\ teckensnitt \\ verasans_ *_, och välj TrueType-teckensnitts filen med namnet _*_VeraIt. ttf_*_. Skriv Font namnet "_*_MEDIUM_ITALIC_*_" i fältet teckensnitts namn och skriv "_*_30_\* \*" i fältet höjd.</span><span class="sxs-lookup"><span data-stu-id="3a00e-151">Next, browse to the supplied GUIX fonts in the GUIX Studio installation folder, _\*_.\\fonts\\verasans_ *_, and select the TrueType font file named _*_VeraIt.ttf_*_. Type font the font name "_*_MEDIUM_ITALIC_*_" in the font name field, and type "_*_30_\*\*" in the height field.</span></span> <span data-ttu-id="3a00e-152">Din dialog ruta bör nu se ut så här:</span><span class="sxs-lookup"><span data-stu-id="3a00e-152">Your dialog should now look like this:</span></span>

![Skärm bild av dialog rutan Redigera teckensnitt.](./media/guix-studio/example_add_font.png)

<span data-ttu-id="3a00e-154">**Figur 10,7**</span><span class="sxs-lookup"><span data-stu-id="3a00e-154">**Figure 10.7**</span></span>

<span data-ttu-id="3a00e-155">Klicka på ***OK*** för att lägga till det här teckensnittet i projektet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-155">Click ***OK*** to add this font to your project.</span></span> <span data-ttu-id="3a00e-156">Nu bör du se teckensnittet i Vyn Resurser:</span><span class="sxs-lookup"><span data-stu-id="3a00e-156">You should now see the font in your Resource View:</span></span>

![Skärm bild av teckensnitten i Vyn Resurser.](./media/guix-studio/example_font_added.png)

<span data-ttu-id="3a00e-158">**Figur 10,8**</span><span class="sxs-lookup"><span data-stu-id="3a00e-158">**Figure 10.8**</span></span>

<span data-ttu-id="3a00e-159">Vi kommer att använda det nya teckensnittet senare i vår UI-design.</span><span class="sxs-lookup"><span data-stu-id="3a00e-159">We will use this new font later in our UI design.</span></span>

<span data-ttu-id="3a00e-160">Nu när vi har några nya tillgängliga resurser måste vi lägga till några underordnade widgetar på skärmen som kan använda dessa resurser.</span><span class="sxs-lookup"><span data-stu-id="3a00e-160">Now that we have some new resources available, we need to add some child widgets to our screen that can utilize these resources.</span></span> <span data-ttu-id="3a00e-161">Välj det tidigare skapade fönstret med namnet "\***hello_world** _" genom att högerklicka på fönstret i vyn mål.</span><span class="sxs-lookup"><span data-stu-id="3a00e-161">Select the previously created window named "\***hello_world** _" by right-clicking on the window in the Target View.</span></span> <span data-ttu-id="3a00e-162">I popup-menyn som visas nu väljer du Meny kommandot _*_Infoga, text, prompt_*_ för att infoga en ny _ \*_GX_PROMPT_\*\*-widget och kopplar widgeten till bakgrunds fönstret.</span><span class="sxs-lookup"><span data-stu-id="3a00e-162">In the pop-up menu that is now displayed, select the menu command _*_Insert, Text, Prompt_*_ to insert a new _ *_GX_PROMPT_*\* widget and attach the widget to the background window.</span></span> <span data-ttu-id="3a00e-163">Fönstret bör nu se ut så här:</span><span class="sxs-lookup"><span data-stu-id="3a00e-163">Your window should now look like this:</span></span>

![Skärm bild av en popup-meny med val av prompt](./media/guix-studio/image78.jpg)

<span data-ttu-id="3a00e-165">**Figur 10,9**</span><span class="sxs-lookup"><span data-stu-id="3a00e-165">**Figure 10.9**</span></span>

<span data-ttu-id="3a00e-166">Klicka på teckensnittet "***MEDIUM_ITALIC** _" i _ *_fonts_** vyn resurser och dra och släpp teckensnittet i varnings widgeten.</span><span class="sxs-lookup"><span data-stu-id="3a00e-166">Click on the font named "***MEDIUM_ITALIC** _" in the _ *_Fonts_** Resource View, and drag and drop the font on the prompt widget.</span></span> <span data-ttu-id="3a00e-167">Redigera sedan egenskaperna för prompten som visas i bild 10,10 för att ändra storlek på uppvarningen, ställa in meddelandets transparens och ändra texten och formatet för prompten:</span><span class="sxs-lookup"><span data-stu-id="3a00e-167">Next, edit the prompt properties as shown in figure 10.10 to resize the prompt, set the prompt transparency, and change the prompt text and style:</span></span>

![Skärm bild av fönstret Egenskaper för prompten.](./media/guix-studio/image79.jpg)

<span data-ttu-id="3a00e-169">**Figur 10,10**</span><span class="sxs-lookup"><span data-stu-id="3a00e-169">**Figure 10.10**</span></span>

<span data-ttu-id="3a00e-170">Du kan behöva rulla lodrätt i egenskapsvyn för att se var och en av dessa inställningar, beroende på skärmupplösningen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-170">You may need to scroll vertically in the Properties View to see each of these settings depending on your screen resolution.</span></span> <span data-ttu-id="3a00e-171">När du har gjort ändringarna bör mål visningen nu se ut så här:</span><span class="sxs-lookup"><span data-stu-id="3a00e-171">After making these changes, your Target View should now look like this:</span></span>

![Skärm bild av en popup-meny med Hello World valet.](./media/guix-studio/image80.jpg)

<span data-ttu-id="3a00e-173">**Figur 10,11**</span><span class="sxs-lookup"><span data-stu-id="3a00e-173">**Figure 10.11**</span></span>

<span data-ttu-id="3a00e-174">Nu ska vi placera widgeten ikon knapp format på skärmen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-174">Next we will place an Icon Button style widget on the screen.</span></span> <span data-ttu-id="3a00e-175">Välj bakgrunds fönstret genom att klicka på det och Använd antingen menyn på den översta nivån eller på popup-menyn i snabb menyn för att välja ***Infoga, knapp, knappen ikon** _ för att lägga till en ny _*_GX_ICON_BUTTON_\*_ i fönstret.</span><span class="sxs-lookup"><span data-stu-id="3a00e-175">Select the background window by clicking on it, and use either the top-level menu or the right-click pop-up menu to select ***Insert, Button, Icon Button** _ to add a new _*_GX_ICON_BUTTON_\*_ to the window.</span></span> <span data-ttu-id="3a00e-176">Klicka på ikonen med namnet _ *_I_HISTORY_LG_*\* som vi lade till tidigare och dra den till ikon knappen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-176">Click on the Icon named _ *_I_HISTORY_LG_*\* that we added earlier and drag it to the icon button.</span></span> <span data-ttu-id="3a00e-177">I egenskapsvyn justerar du Ikonens placering och storlek som visas nedan:</span><span class="sxs-lookup"><span data-stu-id="3a00e-177">Using the properties view, adjust the icon position and size as show below:</span></span>

![Skärm bild av egenskapsvyn för widgeten knapp format för ikon.](./media/guix-studio/image81.jpg)

<span data-ttu-id="3a00e-179">**Figur 10,12**</span><span class="sxs-lookup"><span data-stu-id="3a00e-179">**Figure 10.12**</span></span>

<span data-ttu-id="3a00e-180">Skärmen bör nu se ut så här:</span><span class="sxs-lookup"><span data-stu-id="3a00e-180">Your screen should now look like this:</span></span>

![Skärm bild av en popup-meny med ikonen Hello World och Urklipp.](./media/guix-studio/image82.jpg)

<span data-ttu-id="3a00e-182">**Figur 10,13**</span><span class="sxs-lookup"><span data-stu-id="3a00e-182">**Figure 10.13**</span></span>

<span data-ttu-id="3a00e-183">Vi kommer att anropa den här åtgärden för den enkla exempel skärm designen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-183">We will call this complete for the simple example screen design.</span></span> <span data-ttu-id="3a00e-184">Dina faktiska program skärmar är förmodligen mycket mer sofistikerade, men det räcker med att visa hur du använder GUIX Studio för att skapa dina egna program skärmar.</span><span class="sxs-lookup"><span data-stu-id="3a00e-184">Your actual application screens will likely be much more sophisticated, but this is enough to show you how to use GUIX Studio to create your own application screens.</span></span>

## <a name="generate-resource-and-application-code"></a><span data-ttu-id="3a00e-185">Generera resurs-och program kod</span><span class="sxs-lookup"><span data-stu-id="3a00e-185">Generate Resource and Application Code</span></span>

<span data-ttu-id="3a00e-186">Nästa steg är att generera resurs filen och Specifikations filen som definierar det inbäddade GUIX för körnings gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="3a00e-186">The next step is to generate the resource file and specification file that define the embedded GUIX run-time UI.</span></span> <span data-ttu-id="3a00e-187">Om du vill generera dina utdatafiler måste du högerklicka på noden \***main_display** _ i projektvyn och välja kommandot _ \*_generera resursfiler_\*\*.</span><span class="sxs-lookup"><span data-stu-id="3a00e-187">To generate your output files you will need right-click on the ***main_display** _ node in the Project View, and select the _ *_Generate Resource Files_** command.</span></span> <span data-ttu-id="3a00e-188">Du kommer att se ett informations fönster som visar att dina resursfiler har skapats, som du ser i bild 10,14:</span><span class="sxs-lookup"><span data-stu-id="3a00e-188">You will observe an information window that indicates your resource files have been generated, as shown in figure 10.14:</span></span>

![Skärm bild av en meddelande dialog ruta.](./media/guix-studio/image83.jpg)

<span data-ttu-id="3a00e-190">**Figur 10,14**</span><span class="sxs-lookup"><span data-stu-id="3a00e-190">**Figure 10.14**</span></span>

<span data-ttu-id="3a00e-191">Klicka på ***OK** _ för att stänga meddelandet och Använd samma procedur för att högerklicka på _*_main_display_\*_ -noden och välj kommandot _ \*_generate Specification Files_\*\*.</span><span class="sxs-lookup"><span data-stu-id="3a00e-191">Click ***OK** _ to dismiss this notification, and use the same procedure to right-click on the _*_main_display_*_ node and select the _ *_Generate Specification Files_** command.</span></span> <span data-ttu-id="3a00e-192">Observera ett liknande meddelande fönster.</span><span class="sxs-lookup"><span data-stu-id="3a00e-192">You should observe a similar notification window.</span></span> <span data-ttu-id="3a00e-193">Nu har du genererat dina enkla UI-programfiler.</span><span class="sxs-lookup"><span data-stu-id="3a00e-193">You have now generated your simple UI application files.</span></span>

## <a name="create-user-supplied-code"></a><span data-ttu-id="3a00e-194">Skapa användare angiven kod</span><span class="sxs-lookup"><span data-stu-id="3a00e-194">Create User Supplied Code</span></span>

<span data-ttu-id="3a00e-195">Nästa steg är att skapa en egen program fil som kommer att anropa skärm designen GUIX Studio-genererad.</span><span class="sxs-lookup"><span data-stu-id="3a00e-195">The next step is to create your own application file that will invoke the GUIX Studio-generated screen design.</span></span> <span data-ttu-id="3a00e-196">Använd önskat redigerings program, skapa en källfil med namnet ***new_example. c*** och ange följande käll kod i den här filen:</span><span class="sxs-lookup"><span data-stu-id="3a00e-196">Using your preferred editor, create a source file named ***new_example.c***, and enter the following source code into this file:</span></span>

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

<span data-ttu-id="3a00e-197">Käll koden ovan skapar en typisk ThreadX-tråd med namnet `GUIX New Example Thread` med en stack storlek på 4K-byte.</span><span class="sxs-lookup"><span data-stu-id="3a00e-197">The source code above creates a typical ThreadX thread named `GUIX New Example Thread` with a stack size of 4K bytes.</span></span> <span data-ttu-id="3a00e-198">Det intressanta arbetet börjar med funktionen som heter ***new_example_thread_entry***.</span><span class="sxs-lookup"><span data-stu-id="3a00e-198">The interesting work begins in the function named ***new_example_thread_entry***.</span></span> <span data-ttu-id="3a00e-199">Den här funktionen är den GUIX-angivna tråden börjar köras.</span><span class="sxs-lookup"><span data-stu-id="3a00e-199">This function is where the GUIX specific thread begins to run.</span></span>

<span data-ttu-id="3a00e-200">Det första anropet är till funktionen som heter ***gx_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="3a00e-200">The first call is to the function named ***gx_system_initialize***.</span></span> <span data-ttu-id="3a00e-201">Det här anropet krävs alltid innan andra GUIX-API: er anropas för att förbereda GUIX-biblioteket för första användning.</span><span class="sxs-lookup"><span data-stu-id="3a00e-201">This call is always required before any other GUIX APIs are invoked to prepare the GUIX library for first use.</span></span>

<span data-ttu-id="3a00e-202">Sedan anropar exemplet funktionen ***gx_studio_display_configure***.</span><span class="sxs-lookup"><span data-stu-id="3a00e-202">Next, the example calls the function ***gx_studio_display_configure***.</span></span> <span data-ttu-id="3a00e-203">Den här funktionen skapar GUIX-visnings instansen, installerar det begärda språket i program Strängs tabellen, installerar det begärda temat från visnings resurserna och returnerar en pekare till rot fönstret som har skapats för den här visningen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-203">This function creates the GUIX display instance, installs the requested language of the application string table, installs the requested theme from the display resources, and returns a pointer to the root window that has been created for this display.</span></span> <span data-ttu-id="3a00e-204">Rot fönstret används som överordnat alla skärmar på den översta nivån som programmet kommer att visa.</span><span class="sxs-lookup"><span data-stu-id="3a00e-204">The root window is used as the parent of all top-level screens that our application will display.</span></span>

<span data-ttu-id="3a00e-205">Nästa exempel samtal \***gx_studio_named_widget_create** _ för att skapa en instans av vår _ \*_hello_world_\*\*-skärm.</span><span class="sxs-lookup"><span data-stu-id="3a00e-205">Next the example calls ***gx_studio_named_widget_create** _ to create an instance of our _ *_hello_world_** screen.</span></span> <span data-ttu-id="3a00e-206">Den här funktionen använder data strukturerna och resursen som skapas av GUIX Studio för att skapa en instans av skärmen som vi har definierat den.</span><span class="sxs-lookup"><span data-stu-id="3a00e-206">This function uses the data structures and resource produces by GUIX Studio to create an instance of the screen as we have defined it.</span></span> <span data-ttu-id="3a00e-207">Vi skickar rot fönster pekaren som den andra parametern till det här funktions anropet, vilket innebär att vi vill att skärmen genast ska kopplas till rot fönstret.</span><span class="sxs-lookup"><span data-stu-id="3a00e-207">We pass the root window pointer as the second parameter to this function call, meaning we want the screen to be immediately attached to the root window.</span></span> <span data-ttu-id="3a00e-208">Den sista parametern är en valfri retur pekare som kan användas om vi vill behålla en pekare till den skapade skärmen.</span><span class="sxs-lookup"><span data-stu-id="3a00e-208">The last parameter is an optional return pointer that can be used if we want to keep a pointer to the created screen.</span></span>

<span data-ttu-id="3a00e-209">Nästa ***gx_widget_show** _ anropas, vilket gör rot fönstret och alla dess underordnade, inklusive skärmen _ *_hello_world_** synligt.</span><span class="sxs-lookup"><span data-stu-id="3a00e-209">Next ***gx_widget_show** _ is called, which makes the root window and all of its children, including the _ *_hello_world_** screen, visible.</span></span>

<span data-ttu-id="3a00e-210">Slutligen anropar exemplet ***gx_system_start***.</span><span class="sxs-lookup"><span data-stu-id="3a00e-210">Finally, the example calls ***gx_system_start***.</span></span> <span data-ttu-id="3a00e-211">Den här funktionen börjar köra GUIX i system händelse bearbetning.</span><span class="sxs-lookup"><span data-stu-id="3a00e-211">This function begins executing the GUIX system event processing loop.</span></span>

## <a name="build-and-run-the-example"></a><span data-ttu-id="3a00e-212">Skapa och kör exemplet</span><span class="sxs-lookup"><span data-stu-id="3a00e-212">Build and Run the Example</span></span>

<span data-ttu-id="3a00e-213">Att skapa och köra exemplet är särskilt för dina build-verktyg och-miljöer.</span><span class="sxs-lookup"><span data-stu-id="3a00e-213">Building and running the example is specific to your build tools and environment.</span></span> <span data-ttu-id="3a00e-214">Vi kan dock definiera den allmänna processen:</span><span class="sxs-lookup"><span data-stu-id="3a00e-214">However we can define the general process:</span></span>

1. <span data-ttu-id="3a00e-215">Skapa ett nytt katalog-och program projekt</span><span class="sxs-lookup"><span data-stu-id="3a00e-215">Create a new directory and application project</span></span>
1. <span data-ttu-id="3a00e-216">Lägg till de här filerna i projektet:</span><span class="sxs-lookup"><span data-stu-id="3a00e-216">Add these files to the project:</span></span>

    <span data-ttu-id="3a00e-217">**new_example_resources. c**</span><span class="sxs-lookup"><span data-stu-id="3a00e-217">**new_example_resources.c**</span></span>

    <span data-ttu-id="3a00e-218">**new_example_specification. c**</span><span class="sxs-lookup"><span data-stu-id="3a00e-218">**new_example_specification.c**</span></span>

    <span data-ttu-id="3a00e-219">**new_example. c**</span><span class="sxs-lookup"><span data-stu-id="3a00e-219">**new_example.c**</span></span>

1. <span data-ttu-id="3a00e-220">Lägg till Win32-stöd för körning av filer från installations Sök vägen för GUIX Studio ***./win32_runtime***.</span><span class="sxs-lookup"><span data-stu-id="3a00e-220">Add the Win32 run-time support files from the GUIX Studio installation path ***./win32_runtime***.</span></span> <span data-ttu-id="3a00e-221">Detta inkluderar Win32-sidhuvudet ThreadX och GUIX för körning av filer.</span><span class="sxs-lookup"><span data-stu-id="3a00e-221">This includes the ThreadX and GUIX Win32 header and run-time library files.</span></span>
1. <span data-ttu-id="3a00e-222">Lägg till GUIX Win32-biblioteket (***GX. lib***) i projektet</span><span class="sxs-lookup"><span data-stu-id="3a00e-222">Add the GUIX Win32 library (***gx.lib***) to the project</span></span>
1. <span data-ttu-id="3a00e-223">Lägg till ThreadX Win32 Library (***TX. lib***) i projektet</span><span class="sxs-lookup"><span data-stu-id="3a00e-223">Add the ThreadX Win32 library (***tx.lib***) to the project</span></span>
1. <span data-ttu-id="3a00e-224">Kompilera, länka och kör programmet!</span><span class="sxs-lookup"><span data-stu-id="3a00e-224">Compile, Link, and Run the application!</span></span>
