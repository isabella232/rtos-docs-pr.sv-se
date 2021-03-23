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
# <a name="chapter-3-description-of-guix-studio"></a><span data-ttu-id="ba81e-103">Kapitel 3: Beskrivning av GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="ba81e-103">Chapter 3: Description of GUIX Studio</span></span>

<span data-ttu-id="ba81e-104">Det här kapitlet innehåller en beskrivning av system analys verktyget GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="ba81e-104">This chapter contains a description of the GUIX Studio system analysis tool.</span></span> <span data-ttu-id="ba81e-105">En beskrivning av de övergripande funktionerna i det grafiska användar gränssnittet finns i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="ba81e-105">A description of the overall functionality of the GUI is found in this chapter.</span></span> 

## <a name="guix-studio-views"></a><span data-ttu-id="ba81e-106">GUIX Studio-vyer</span><span class="sxs-lookup"><span data-stu-id="ba81e-106">GUIX Studio Views</span></span>

<span data-ttu-id="ba81e-107">Det finns fem huvud områden i användar gränssnittet för GUIX Studio, nämligen ***verktygsfältet** _, _*_projektvyn_*_, _*_egenskapsvyn, vyn_*_ _*_mål_*_ och _*_vyn resurser_\*_.</span><span class="sxs-lookup"><span data-stu-id="ba81e-107">There are five principal areas of the GUIX Studio UI, namely the ***Toolbar** _, _*_Project View_*_, _*_Properties View_*_, _*_Target View_*_, and _*_Resource View_\*_.</span></span> <span data-ttu-id="ba81e-108">_ *_Bild 2_*\* visar gränssnittet Basic GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="ba81e-108">_ *_Figure 2_*\* shows the basic GUIX Studio UI.</span></span> <span data-ttu-id="ba81e-109">Var och en av vyerna beskrivs i följande underavsnitt.</span><span class="sxs-lookup"><span data-stu-id="ba81e-109">Each of the views is further discussed in the following sub-sections.</span></span>

![Skärm bild av Basic GUIX Studio-ANVÄNDARGRÄNSSNITTET.](./media/guix-studio/image_10.png)

<span data-ttu-id="ba81e-111">**Bild 2**</span><span class="sxs-lookup"><span data-stu-id="ba81e-111">**Figure 2**</span></span>

### <a name="title"></a><span data-ttu-id="ba81e-112">Rubrik</span><span class="sxs-lookup"><span data-stu-id="ba81e-112">Title</span></span>

- <span data-ttu-id="ba81e-113">GUIX Studio 18: ***title** _ visar versionen av GUIX Studio och det för tillfället öppna projektet, som visas överst i _ *_bild 2_** tidigare.</span><span class="sxs-lookup"><span data-stu-id="ba81e-113">GUIX Studio 18: The ***Title** _ displays the GUIX Studio version as well as the currently open project, as shown at the top of _ *_Figure 2_** previously.</span></span>

### <a name="toolbar"></a><span data-ttu-id="ba81e-114">Verktygsfält</span><span class="sxs-lookup"><span data-stu-id="ba81e-114">Toolbar</span></span>

<span data-ttu-id="ba81e-115">I **verktygsfältet**\* visas alla knappar som är tillgängliga för GUIX Studio-utvecklare, som du ser i _ *_bild 3_* \*.</span><span class="sxs-lookup"><span data-stu-id="ba81e-115">The ***Toolbar** _ shows the buttons available to the GUIX Studio developer, as shown in _*_Figure 3_\*\*.</span></span>

![Skärm bild av GUIX Studio-verktygsfältet.](./media/guix-studio/image11.jpg)

<span data-ttu-id="ba81e-117">**Bild 3**</span><span class="sxs-lookup"><span data-stu-id="ba81e-117">**Figure 3**</span></span>

<span data-ttu-id="ba81e-118">Verktygsfälts knapparna definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ba81e-118">The toolbar buttons are defined as follows:</span></span>

![Knappen Ny](./media/guix-studio/new-button.png) <span data-ttu-id="ba81e-120">Skapar ett nytt GUIX Studio-projekt</span><span class="sxs-lookup"><span data-stu-id="ba81e-120">Creates a new GUIX Studio project</span></span>

![Knappen Öppna](./media/guix-studio/open-button.png) <span data-ttu-id="ba81e-122">Öppnar ett befintligt GUIX Studio-projekt</span><span class="sxs-lookup"><span data-stu-id="ba81e-122">Opens an existing GUIX Studio project</span></span>

![Knappen Spara](./media/guix-studio/save-button.png) <span data-ttu-id="ba81e-124">Sparar projektet</span><span class="sxs-lookup"><span data-stu-id="ba81e-124">Saves the project</span></span>

![Knappen Klipp ut](./media/guix-studio/cut-button.png) <span data-ttu-id="ba81e-126">Klipp ut widget markerad, inklusive underordnade</span><span class="sxs-lookup"><span data-stu-id="ba81e-126">Cut widget selected, including children</span></span>

![Knappen Kopiera](./media/guix-studio/copy-button.png) <span data-ttu-id="ba81e-128">Kopiera markerad widget, inklusive underordnade</span><span class="sxs-lookup"><span data-stu-id="ba81e-128">Copy selected widget, including children</span></span>

![Knappen Klistra in](./media/guix-studio/paste-button.png) <span data-ttu-id="ba81e-130">Klistra in widget och underordnade</span><span class="sxs-lookup"><span data-stu-id="ba81e-130">Paste widget and children</span></span>

![Knappen Vänsterjustera](./media/guix-studio/left-align-button.png) <span data-ttu-id="ba81e-132">Vänsterjustera markerade widgetar</span><span class="sxs-lookup"><span data-stu-id="ba81e-132">Left-align selected widgets</span></span>

![Högerjustera-knapp](./media/guix-studio/right-align-button.png) <span data-ttu-id="ba81e-134">Högerjustera markerade widgetar</span><span class="sxs-lookup"><span data-stu-id="ba81e-134">Right-align selected widgets</span></span>

![Knappen Justera mot överkant](./media/guix-studio/top-align-button.png) <span data-ttu-id="ba81e-136">Översta justering av markerade widgetar</span><span class="sxs-lookup"><span data-stu-id="ba81e-136">Top-align selected widgets</span></span>

![Knappen Justera mot nederkant](./media/guix-studio/bottom-align-button.png) <span data-ttu-id="ba81e-138">Underst-justera markerade widgetar</span><span class="sxs-lookup"><span data-stu-id="ba81e-138">Bottom-align selected widgets</span></span>

![Knappen lodrätt blank steg](./media/guix-studio/space-vertically-button.png) <span data-ttu-id="ba81e-140">Lika mycket utrymme valda widgetar lodrätt</span><span class="sxs-lookup"><span data-stu-id="ba81e-140">Equally space selected widgets vertically</span></span>

![Blank steg vågrätt](./media/guix-studio/space-horizontally-button.png) <span data-ttu-id="ba81e-142">Lika mycket utrymme valda widgetar vågrätt</span><span class="sxs-lookup"><span data-stu-id="ba81e-142">Equally space selected widgets horizontally</span></span>

![Knappen med samma bredd](./media/guix-studio/equal-width-button.png) <span data-ttu-id="ba81e-144">Gör valda widgetar lika breda</span><span class="sxs-lookup"><span data-stu-id="ba81e-144">Make selected widgets equal width</span></span>

![Knappen med samma höjd](./media/guix-studio/equal-height-button.png) <span data-ttu-id="ba81e-146">Gör valda widgetar lika höjd</span><span class="sxs-lookup"><span data-stu-id="ba81e-146">Make selected widgets equal height</span></span>

![Flytta fram knapp](./media/guix-studio/move-front-button.png) <span data-ttu-id="ba81e-148">Flytta valda widgetar längst fram</span><span class="sxs-lookup"><span data-stu-id="ba81e-148">Move selected widgets to front</span></span>

![Flytta tillbaka-knapp](./media/guix-studio/move-back-button.png) <span data-ttu-id="ba81e-150">Flytta valda widgetar tillbaka</span><span class="sxs-lookup"><span data-stu-id="ba81e-150">Move selected widgets to back</span></span>

![Storleks knapp](./media/guix-studio/size-button.png) <span data-ttu-id="ba81e-152">Ändra vald widget till innehåll zooma ut mål skärmen</span><span class="sxs-lookup"><span data-stu-id="ba81e-152">Size selected widget to content Zoom out target screen</span></span>

![Knappen Zooma ut](./media/guix-studio/zoom-out-button.png) <span data-ttu-id="ba81e-154">Zooma ut mål skärmen</span><span class="sxs-lookup"><span data-stu-id="ba81e-154">Zoom out target screen</span></span>

![Knappen Zooma in](./media/guix-studio/zoom-in-button.png) <span data-ttu-id="ba81e-156">Zooma in mål skärmen</span><span class="sxs-lookup"><span data-stu-id="ba81e-156">Zoom in target screen</span></span>

![Knappen Spela in](./media/guix-studio/record-button.png) <span data-ttu-id="ba81e-158">Spela in makro</span><span class="sxs-lookup"><span data-stu-id="ba81e-158">Record Macro</span></span>

![Uppspelnings knapp](./media/guix-studio/playback-button.png) <span data-ttu-id="ba81e-160">Uppspelnings makro</span><span class="sxs-lookup"><span data-stu-id="ba81e-160">Playback Macro</span></span>

![Knappen Kör](./media/guix-studio/run-button.png) <span data-ttu-id="ba81e-162">Kör program</span><span class="sxs-lookup"><span data-stu-id="ba81e-162">Run Application</span></span>

![Knappen om](./media/guix-studio/about-button.png) <span data-ttu-id="ba81e-164">Om GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="ba81e-164">About GUIX Studio</span></span>

### <a name="project-view"></a><span data-ttu-id="ba81e-165">Projektvyn</span><span class="sxs-lookup"><span data-stu-id="ba81e-165">Project View</span></span>

<span data-ttu-id="ba81e-166">I \***Project-vyn** _ visas den hierarkiska listan GUIX objekt som utgör det inbäddade användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ba81e-166">The \***Project View** _ shows the hierarchical list GUIX objects that comprise the embedded UI.</span></span> <span data-ttu-id="ba81e-167">Du kan lägga till nya GUIX-objekt genom att klicka på det överordnade objektet och sedan välja ett objekt från _*_Infoga_*_ -menyn (eller genom att högerklicka på objektet och välja i menyn på snabb menyn).</span><span class="sxs-lookup"><span data-stu-id="ba81e-167">New GUIX objects can be added by clicking on the parent object and then selecting an object from the _*_Insert_*_ menu (or by right-clicking on the object and selecting from the right-click menu).</span></span> <span data-ttu-id="ba81e-168">_*_Bild 4_*_ nedan visar GUIX Studio _ *_projektvyn_* \*.</span><span class="sxs-lookup"><span data-stu-id="ba81e-168">_*_Figure 4_*_ below shows the GUIX Studio _\*_Project View_\*\*.</span></span>

![Skärm bild av projektvyn i GUIX Studio.](./media/guix-studio/image_35.png)

<span data-ttu-id="ba81e-170">**Bild 4**</span><span class="sxs-lookup"><span data-stu-id="ba81e-170">**Figure 4**</span></span>

### <a name="properties-view"></a><span data-ttu-id="ba81e-171">Egenskapsvyn</span><span class="sxs-lookup"><span data-stu-id="ba81e-171">Properties View</span></span>

<span data-ttu-id="ba81e-172">***Egenskaperna View** _ visar detaljerad egenskaps information för det markerade GUIX-objektet, som kan väljas via _*_projektvyn_*_ eller genom att klicka direkt på objektet i _*_vyn mål_\*_.</span><span class="sxs-lookup"><span data-stu-id="ba81e-172">The ***Properties View** _ shows detailed property information of the currently selected GUIX object, which can be selected via the _*_Project View_*_ or by clicking directly on the object in the _*_Target View_\*_.</span></span> <span data-ttu-id="ba81e-173">_*_Bild 5_*_ nedan visar _egenskapsvyn_ för GUIX Studio _ \*.</span><span class="sxs-lookup"><span data-stu-id="ba81e-173">_*_Figure 5_*_ below shows the GUIX Studio _\*_Properties View_\*\*.</span></span>

![Skärm bild av egenskapsvyn för GUIX Studio.](./media/guix-studio/image36.jpg)

<span data-ttu-id="ba81e-175">**Figur 5**</span><span class="sxs-lookup"><span data-stu-id="ba81e-175">**Figure 5**</span></span>

### <a name="target-view"></a><span data-ttu-id="ba81e-176">Mål visning</span><span class="sxs-lookup"><span data-stu-id="ba81e-176">Target View</span></span>

<span data-ttu-id="ba81e-177">\***Target-vyn** _ är design och layout i WYSIWYG-skärmen.</span><span class="sxs-lookup"><span data-stu-id="ba81e-177">The \***Target View** _ is the WYSIWYG screen design and layout area.</span></span> <span data-ttu-id="ba81e-178">Den här vyn är avsedd att representera den fysiska visningen eller visningen som är tillgänglig på mål maskin varan.</span><span class="sxs-lookup"><span data-stu-id="ba81e-178">This view is meant to represent the physical display or displays available on your target hardware.</span></span> <span data-ttu-id="ba81e-179">Objekt kan markeras, flyttas, ändras och ändras med hjälp av enkla mus åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ba81e-179">Objects can be selected, moved, resized, etc. via simple mouse operations.</span></span> <span data-ttu-id="ba81e-180">Dessutom är justerings-och Z-order-knapparna tillgängliga för valda objekt i vyn mål.</span><span class="sxs-lookup"><span data-stu-id="ba81e-180">In addition, alignment and Z-order button operations are available on selected objects in the Target View.</span></span> <span data-ttu-id="ba81e-181">Om du markerar ett objekt i vyn _*_mål_*_ så kommer egenskaperna för objektet att visas i _*_egenskapsvyn_*_.</span><span class="sxs-lookup"><span data-stu-id="ba81e-181">Selecting an object in the _*_Target View_*_ will also result in the properties for that object to be displayed in the _*_Properties View_*_.</span></span> <span data-ttu-id="ba81e-182">_*_Bild 6_*_ nedan visar GUIX Studio _ *_target View_* \*.</span><span class="sxs-lookup"><span data-stu-id="ba81e-182">_*_Figure 6_*_ below shows the GUIX Studio _\*_Target View_\*\*.</span></span>

![Skärm bild av vyn GUIX Studio Target.](./media/guix-studio/image_37.png)

<span data-ttu-id="ba81e-184">**Bild 6**</span><span class="sxs-lookup"><span data-stu-id="ba81e-184">**Figure 6**</span></span>

### <a name="resource-view"></a><span data-ttu-id="ba81e-185">Vyn Resurser</span><span class="sxs-lookup"><span data-stu-id="ba81e-185">Resource View</span></span>

<span data-ttu-id="ba81e-186">\***Vyn resurser** _ används för att hantera resurserna (färger, teckensnitt, pixelmaps och strängar) som är tillgängliga för program skärmar som definierats för varje bildskärm.</span><span class="sxs-lookup"><span data-stu-id="ba81e-186">The \***Resource View** _ is used to manage the resources (colors, fonts, pixelmaps, and strings) available to applications screens defined for each display.</span></span> <span data-ttu-id="ba81e-187">Du kan klicka på grupp rubrikerna för resurs visning för att expandera varje grupp och granska grupp innehållet.</span><span class="sxs-lookup"><span data-stu-id="ba81e-187">You can click on the resource view group headers to expand each group and examine the group contents.</span></span> <span data-ttu-id="ba81e-188">_*_Bild 7_*_ nedan visar GUIX Studio _ *_vyn resurser_* \*.</span><span class="sxs-lookup"><span data-stu-id="ba81e-188">_*_Figure 7_*_ below shows the GUIX Studio _\*_Resource View_\*\*.</span></span>

![Skärm bild av GUIX Studio-Vyn Resurser.](./media/guix-studio/image38.jpg)

<span data-ttu-id="ba81e-190">**Figur 7**</span><span class="sxs-lookup"><span data-stu-id="ba81e-190">**Figure 7**</span></span>

<span data-ttu-id="ba81e-191">Namnet på resurs grupperna visar det aktuella temanamn.</span><span class="sxs-lookup"><span data-stu-id="ba81e-191">The title of the resource groups indicates current theme name.</span></span> <span data-ttu-id="ba81e-192">Om flera teman är tillgängliga kan du växla mellan teman genom att klicka på upp-och nedpilen.</span><span class="sxs-lookup"><span data-stu-id="ba81e-192">If multi themes available, you are able to switch between themes by clicking on the up and down arrow.</span></span>

<span data-ttu-id="ba81e-193">Varje resurs grupp i vyn ovan kan utökas eller komprimeras genom att klicka på grupp rubriken.</span><span class="sxs-lookup"><span data-stu-id="ba81e-193">Each resource group in the view above can be expanded or collapsed by clicking on the group header.</span></span> <span data-ttu-id="ba81e-194">En mer detaljerad beskrivning av varje resurs grupp följer i nästa kapitel.</span><span class="sxs-lookup"><span data-stu-id="ba81e-194">A more detailed description of each resource groups follows in the next chapter.</span></span>

## <a name="the-guix-studio-project"></a><span data-ttu-id="ba81e-195">GUIX Studio-projektet</span><span class="sxs-lookup"><span data-stu-id="ba81e-195">The GUIX Studio Project</span></span>

<span data-ttu-id="ba81e-196">Ett GUIX Studio-projekt innehåller information om design för GRÄNSSNITTs skärmen och användar gränssnitts resurser.</span><span class="sxs-lookup"><span data-stu-id="ba81e-196">A GUIX Studio project maintains information about your UI screen design and UI resources.</span></span> <span data-ttu-id="ba81e-197">Projekt data sparas i en XML-formaterad fil med tillägget. ***GXP***".</span><span class="sxs-lookup"><span data-stu-id="ba81e-197">The project data is saved to an XML format file with the extension ".***gxp***".</span></span> <span data-ttu-id="ba81e-198">Eftersom projekt filen är en XML-schemafil, kan den vara versions kontrollerad och delas ungefär som andra källfiler.</span><span class="sxs-lookup"><span data-stu-id="ba81e-198">Since the project file is an XML schema file, it can be versioned controlled and shared similar to any other source file.</span></span>

<span data-ttu-id="ba81e-199">Första gången du börjar använda GUIX Studio måste du antingen öppna ett av de exempel projekt som medföljer distributionen eller skapa ett nytt projekt.</span><span class="sxs-lookup"><span data-stu-id="ba81e-199">When you first start using GUIX Studio, you will need to either open one of the example projects provided with the distribution or create a new project.</span></span> <span data-ttu-id="ba81e-200">Allt ditt arbete sparas i projekt data filen.</span><span class="sxs-lookup"><span data-stu-id="ba81e-200">All of your work is saved to the project data file.</span></span>

<span data-ttu-id="ba81e-201">GUIX Studio producerar också ANSI C-källfiler.</span><span class="sxs-lookup"><span data-stu-id="ba81e-201">GUIX Studio also produces ANSI C source files.</span></span> <span data-ttu-id="ba81e-202">Dessa källfiler innehåller antingen dina program resurser eller data strukturer som beskriver de utformade skärmarna.</span><span class="sxs-lookup"><span data-stu-id="ba81e-202">These source files contain either your application resources or data structures describing your designed screens.</span></span> <span data-ttu-id="ba81e-203">GUIX Studio skriver också till dessa genererade API-funktioner för källfiler som används för att använda de genererade data strukturerna för att skapa dina program skärmar dynamiskt.</span><span class="sxs-lookup"><span data-stu-id="ba81e-203">GUIX Studio also writes to these generated source files API functions that know to utilize the generated data structures to dynamically create your application screens.</span></span> <span data-ttu-id="ba81e-204">Program varan kommer bara att anropa de tillhandahållna API-funktionerna för att skapa de skärmar som du har utformat i GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="ba81e-204">Your application software will simply invoke the provided API functions to create the screens you have designed within GUIX Studio.</span></span>

<span data-ttu-id="ba81e-205">När du arbetar med att designa ditt användar gränssnitt vill du regelbundet använda GUIX Studio för att generera GUIX-kompatibla utdatafiler som gör att du kan skapa och köra gränssnittet som du har utformat.</span><span class="sxs-lookup"><span data-stu-id="ba81e-205">As you progress in designing your user interface, you will periodically want to use GUIX Studio to generate the GUIX compatible output files that will allow you to build and run the interface you have designed.</span></span> <span data-ttu-id="ba81e-206">Du kan kompilera och köra de genererade källfilerna för antingen din mål maskin vara eller på Windows-skrivbordet som simulerar ThreadX och GUIX.</span><span class="sxs-lookup"><span data-stu-id="ba81e-206">You can compile and run the generated source files for either your target hardware or on your Windows desktop that simulates ThreadX and GUIX.</span></span>

## <a name="guix-studio-project-organization"></a><span data-ttu-id="ba81e-207">Projekt organisation för GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="ba81e-207">GUIX Studio Project Organization</span></span>

<span data-ttu-id="ba81e-208">Det är bra att ha lite kunskap om den grundläggande organisationen av ett GUIX Studio-projekt för att förstå hur du använder GUIX Studio effektivt och för att förstå den information som visas i projektvyn för GUIX Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="ba81e-208">It is helpful to have some knowledge of the basic organization of a GUIX Studio project to understand how to use GUIX Studio effectively and to understand the information presented in the Project View of the GUIX Studio IDE.</span></span> <span data-ttu-id="ba81e-209">Projektvyn är en sammanfattande visuell representation av all information som finns i ditt projekt.</span><span class="sxs-lookup"><span data-stu-id="ba81e-209">The Project View is a summary visual representation of all of the information contained in your project.</span></span>

<span data-ttu-id="ba81e-210">Innan du kan beskriva projektet är det nödvändigt att definiera några villkor.</span><span class="sxs-lookup"><span data-stu-id="ba81e-210">Before describing the project, it is necessary to define few terms.</span></span> <span data-ttu-id="ba81e-211">Först använder vi termen **visning** för att betyda en fysisk visnings enhet.</span><span class="sxs-lookup"><span data-stu-id="ba81e-211">First, we use the term **Display** to mean a physical display device.</span></span> <span data-ttu-id="ba81e-212">Detta är oftast en LCD-bildskärms enhet, men den kan använda andra tekniker.</span><span class="sxs-lookup"><span data-stu-id="ba81e-212">This is most often an LCD display device but it could be using other technology.</span></span> <span data-ttu-id="ba81e-213">Nästa term är **skärm**, vilket innebär ett GUIX-objekt på översta nivån, vanligt vis ett GUIX-fönster och alla tillhör ande underordnade element.</span><span class="sxs-lookup"><span data-stu-id="ba81e-213">The next term is **Screen**, which mean a top-level GUIX object, usually a GUIX Window, and all of its associated child elements.</span></span> <span data-ttu-id="ba81e-214">En skärm är en program varu konstruktion som kan definieras och ändras vid körning.</span><span class="sxs-lookup"><span data-stu-id="ba81e-214">A Screen is a software construct that can be defined and modified at runtime.</span></span> <span data-ttu-id="ba81e-215">Slutligen är ett **tema** en samling resurser.</span><span class="sxs-lookup"><span data-stu-id="ba81e-215">Finally, a **Theme** is a collection of resources.</span></span> <span data-ttu-id="ba81e-216">Ett tema innehåller en tabell med färg definitioner, teckensnitts definitioner och Pixelmap-definitioner som är utformade för att fungera bra tillsammans och presentera slutanvändaren med ett enhetligt utseende och känsla.</span><span class="sxs-lookup"><span data-stu-id="ba81e-216">A theme includes a table of color definitions, font definitions, and pixelmap definitions that are designed to work well together and present your end user with a consistent look and feel.</span></span>

<span data-ttu-id="ba81e-217">Projektet innehåller först en uppsättning global information, till exempel projekt namnet, antalet skärmar som stöds, upplösnings-och färg formatet för varje visning, antalet språk som stöds, namnet på varje språk som stöds.</span><span class="sxs-lookup"><span data-stu-id="ba81e-217">The project first includes a set of global information such as the project name, number of displays supported, the resolution and color format of each display, the number of languages supported, the name of each supported language.</span></span> <span data-ttu-id="ba81e-218">Projekt namnet är den första noden som visas i projektvyn.</span><span class="sxs-lookup"><span data-stu-id="ba81e-218">The project name is the first node displayed in the Project View.</span></span>

<span data-ttu-id="ba81e-219">Projektet innehåller information om all information som krävs för upp till 4 fysiska skärmar och de skärmar och resurser som är tillgängliga för varje bildskärm.</span><span class="sxs-lookup"><span data-stu-id="ba81e-219">The project next organizes all of the information required for up to 4 physical displays and the screens and resources available to each display.</span></span> <span data-ttu-id="ba81e-220">Visnings namnen är noder på nästa nivå i trädvyn projekt.</span><span class="sxs-lookup"><span data-stu-id="ba81e-220">The display names are the next level nodes in the Project View tree.</span></span>

<span data-ttu-id="ba81e-221">En unik funktion i GUIX Studio-programmet är inbyggt stöd för flera fysiska skärmar, var och en med sin egen x-, y-upplösning, färg format, skärmar och resurser.</span><span class="sxs-lookup"><span data-stu-id="ba81e-221">A unique feature of the GUIX Studio application is built-in support for multiple physical displays, each with its own x,y resolution, color format, screens, and resources.</span></span> <span data-ttu-id="ba81e-222">Den stora delen av GUIX-program använder bara en fysisk skärm, men den här funktionen är viktig för de som gör en produkt som måste ha stöd för flera samtidiga fysiska skärmar.</span><span class="sxs-lookup"><span data-stu-id="ba81e-222">While the vast majority of GUIX applications utilize only one physical display, this capability is important for those making a product that must support multiple simultaneous physical displays.</span></span>

<span data-ttu-id="ba81e-223">Under varje visnings definition är de översta fönster eller skärmar som definierats för den skärmen.</span><span class="sxs-lookup"><span data-stu-id="ba81e-223">Beneath each display definition are the top-level windows or screens defined for that display.</span></span> <span data-ttu-id="ba81e-224">Skärm definitionerna kan kapslas till vilken nivå som helst, beroende på antalet och kapslade underordnade widgetar på varje skärm.</span><span class="sxs-lookup"><span data-stu-id="ba81e-224">The screen definitions can be nested to any level depending on the number and nesting of child widgets on each screen.</span></span>

<span data-ttu-id="ba81e-225">Den här skärmen och den underordnade widgets organisationen visas på ett grafiskt sätt i projektvyn.</span><span class="sxs-lookup"><span data-stu-id="ba81e-225">This screen and child widget organization is displayed in a graphical manner in the Project View.</span></span>

<span data-ttu-id="ba81e-226">Även om de är kopplade till varje bildskärm är de teman som stöds av visningen och resurs innehållet som skriver varje tema.</span><span class="sxs-lookup"><span data-stu-id="ba81e-226">Also associated with each display are the Themes supported by the display and the resource content composing each Theme.</span></span> <span data-ttu-id="ba81e-227">Om projektet innehåller flera bildskärmar ser du att Vyn Resurser ändrar innehållet när du väljer en bildskärm och sedan en annan.</span><span class="sxs-lookup"><span data-stu-id="ba81e-227">If your project includes multiple displays, you will notice that the Resource View changes its content when you select one display and then another.</span></span> <span data-ttu-id="ba81e-228">Detta beror på att resurs innehållet är länkat till varje bildskärm.</span><span class="sxs-lookup"><span data-stu-id="ba81e-228">This is because the resource content is linked to each display.</span></span> <span data-ttu-id="ba81e-229">Inte bara färg formatet kan vara annorlunda, men pixelmaps, färger och teckensnitt som du väljer att använda kan variera beroende på en fysisk visning till en annan.</span><span class="sxs-lookup"><span data-stu-id="ba81e-229">Not only the color format may be different, but the pixelmaps, colors, and fonts you choose to use may vary from one physical display to another.</span></span>

<span data-ttu-id="ba81e-230">Den sista komponenten som underhålls av projektet är sträng tabell data som är associerade med varje visning.</span><span class="sxs-lookup"><span data-stu-id="ba81e-230">The final component maintained by the project is the string table data associated with each display.</span></span> <span data-ttu-id="ba81e-231">Eftersom visningen kan vara mycket olika x, y-upplösningar underhålls sträng data oberoende för varje bildskärm som definierats i projektet.</span><span class="sxs-lookup"><span data-stu-id="ba81e-231">Since displays can be of very different x,y resolutions, the string data is maintained independently for each display defined in the project.</span></span>
