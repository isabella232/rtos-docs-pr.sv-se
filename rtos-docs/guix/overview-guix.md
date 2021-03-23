---
title: Förstå Azure återställnings tider-GUIX och Azure återställnings tider GUIX Studio
description: Azure återställnings tider GUIX är ett högkvalitativt kvalitets paket som har skapats för att uppfylla behoven hos inbäddade system utvecklare.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827093"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="df107-103">Översikt över Azure återställnings tider GUIX och Azure återställnings tider GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="df107-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="df107-104">Azure GUIX Embedded GUI är Microsofts avancerade, industriella klassbaserade GUI-lösning som utformats specifikt för djupt inbäddade, real tids-och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="df107-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="df107-105">Microsoft tillhandahåller också ett komplett design verktyg för WYSIWYG Desktop med namnet Azure återställnings tider GUIX Studio, som gör att utvecklare kan utforma sitt användar gränssnitt på Skriv bordet och generera Azure återställnings tider-GUIX inbäddad GUI-kod som sedan kan exporteras till målet.</span><span class="sxs-lookup"><span data-stu-id="df107-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="df107-106">Azure återställnings tider GUIX är helt integrerat med Azure återställnings tider ThreadX återställnings tider och är tillgänglig för många av de processorer som stöds av Azure återställnings tider ThreadX.</span><span class="sxs-lookup"><span data-stu-id="df107-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="df107-107">Allt detta kombinerat med en mycket liten storlek, snabb körning och överlägsen enkel användning, gör Azure återställnings tider GUIX det idealiska valet för de mest krävande inbäddade IoT-programmen som kräver ett användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="df107-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="df107-108">Azure återställnings tider GUIX-API</span><span class="sxs-lookup"><span data-stu-id="df107-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="df107-109">Intuitiv och konsekvent API</span><span class="sxs-lookup"><span data-stu-id="df107-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="df107-110">Substantiv-namn konvention för verb</span><span class="sxs-lookup"><span data-stu-id="df107-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="df107-111">Alla API: er har ledande *gx_* för att enkelt identifiera som Azure återställnings tider GUIX</span><span class="sxs-lookup"><span data-stu-id="df107-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="df107-112">Händelse driven programmerings modell (API)</span><span class="sxs-lookup"><span data-stu-id="df107-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="df107-113">Fullständigt stöd för ritning av direkt arbets yta vid behov</span><span class="sxs-lookup"><span data-stu-id="df107-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="df107-114">Enkel att interagera med Azure återställnings tider GUIX Studio-genererad kod</span><span class="sxs-lookup"><span data-stu-id="df107-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="df107-115">API: er för linje, rektangel, polygon osv.</span><span class="sxs-lookup"><span data-stu-id="df107-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="df107-116">API: er för cirkel, båge, cirkel, ackord, ellips osv.</span><span class="sxs-lookup"><span data-stu-id="df107-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="df107-117">API: er för text ritning och placering</span><span class="sxs-lookup"><span data-stu-id="df107-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="df107-118">Kant utjämning, struktur fyllningar och heldragna fyllningar</span><span class="sxs-lookup"><span data-stu-id="df107-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="df107-119">API: er för att skapa och modifing skärmar och widgetar</span><span class="sxs-lookup"><span data-stu-id="df107-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="df107-120">Genererade filer för Azure återställnings tider GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="df107-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="df107-121">Automatiskt genererade ANSI C-källfiler</span><span class="sxs-lookup"><span data-stu-id="df107-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="df107-122">Isolerar program vara från layoutinformation</span><span class="sxs-lookup"><span data-stu-id="df107-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="df107-123">Innehåller teckensnitt och avbildningar som krävs av UI design</span><span class="sxs-lookup"><span data-stu-id="df107-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="df107-124">Genererade filer som kompileras med program kod</span><span class="sxs-lookup"><span data-stu-id="df107-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="df107-125">Skärmlayout kan uppdateras utan att påverka program logiken</span><span class="sxs-lookup"><span data-stu-id="df107-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="df107-126">Resurs-ID skapa språk och tema oberoende</span><span class="sxs-lookup"><span data-stu-id="df107-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="df107-127">Användardefinierade funktioner för anpassad ritning och händelse bearbetning</span><span class="sxs-lookup"><span data-stu-id="df107-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="df107-128">Bibliotek för widget</span><span class="sxs-lookup"><span data-stu-id="df107-128">Widget library</span></span>

* <span data-ttu-id="df107-129">Fördefinierad men anpassningsbar uppsättning av vanliga gränssnitts element</span><span class="sxs-lookup"><span data-stu-id="df107-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="df107-130">Mycket liten, kompakt och effektiv</span><span class="sxs-lookup"><span data-stu-id="df107-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="df107-131">Biblioteket innehåller knappar, mätare, lista, fönster, rullning, skjutreglage, förlopps indikator, prompt och många fler</span><span class="sxs-lookup"><span data-stu-id="df107-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="df107-132">Helt anpassningsbar ritning och utseende</span><span class="sxs-lookup"><span data-stu-id="df107-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="df107-133">Helt anpassningsbar åtgärd och händelse hantering</span><span class="sxs-lookup"><span data-stu-id="df107-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="df107-134">Endast widgeten som används är kopplade till program varan</span><span class="sxs-lookup"><span data-stu-id="df107-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="df107-135">Matematik och verktyg</span><span class="sxs-lookup"><span data-stu-id="df107-135">Math and utilities</span></span>

* <span data-ttu-id="df107-136">Funktioner för sin, cos, bågarin, arccos, tangens, kvadratroten</span><span class="sxs-lookup"><span data-stu-id="df107-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="df107-137">Funktioner för att ändra skärm områden</span><span class="sxs-lookup"><span data-stu-id="df107-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="df107-138">System konfiguration och start</span><span class="sxs-lookup"><span data-stu-id="df107-138">System configuration and startup</span></span>

* <span data-ttu-id="df107-139">Minnes samlings definition (valfritt)</span><span class="sxs-lookup"><span data-stu-id="df107-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="df107-140">Timer-hantering</span><span class="sxs-lookup"><span data-stu-id="df107-140">Timer Management</span></span>

* <span data-ttu-id="df107-141">Hantering av animering</span><span class="sxs-lookup"><span data-stu-id="df107-141">Animation Management</span></span>

* <span data-ttu-id="df107-142">Underhåll av lista över skadade listor</span><span class="sxs-lookup"><span data-stu-id="df107-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="df107-143">Bearbetning av avbildning</span><span class="sxs-lookup"><span data-stu-id="df107-143">Image processing</span></span>

* <span data-ttu-id="df107-144">Funktioner för körnings avkodning av JPEG-och PNG-bilder</span><span class="sxs-lookup"><span data-stu-id="df107-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="df107-145">Tillämpa rastrering och färg områdes konvertering</span><span class="sxs-lookup"><span data-stu-id="df107-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="df107-146">Bild rotation</span><span class="sxs-lookup"><span data-stu-id="df107-146">Image rotation</span></span>

* <span data-ttu-id="df107-147">Bild skalning</span><span class="sxs-lookup"><span data-stu-id="df107-147">Image scaling</span></span>

* <span data-ttu-id="df107-148">Bild blandning</span><span class="sxs-lookup"><span data-stu-id="df107-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="df107-149">Händelse bearbetning</span><span class="sxs-lookup"><span data-stu-id="df107-149">Event processing</span></span>

* <span data-ttu-id="df107-150">Pausar automatiskt Azure återställnings tider GUIX-tråd vid inaktivitet</span><span class="sxs-lookup"><span data-stu-id="df107-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="df107-151">Händelse driven programmerings modell populär i UI-design</span><span class="sxs-lookup"><span data-stu-id="df107-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="df107-152">Isolerar inmatade driv rutiner från Azure återställnings tider GUIX-ritnings tråd</span><span class="sxs-lookup"><span data-stu-id="df107-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="df107-153">Funktioner för att skicka och ta emot händelser</span><span class="sxs-lookup"><span data-stu-id="df107-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="df107-154">Fördefinierade händelse typer för alla typer av widgetar för Azure återställnings tider-GUIX</span><span class="sxs-lookup"><span data-stu-id="df107-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="df107-155">Användardefinierade anpassade händelser stöds</span><span class="sxs-lookup"><span data-stu-id="df107-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="df107-156">Arbets ytans bearbetning</span><span class="sxs-lookup"><span data-stu-id="df107-156">Canvas processing</span></span>

* <span data-ttu-id="df107-157">Underhåll av Urklipp och Z-ordning</span><span class="sxs-lookup"><span data-stu-id="df107-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="df107-158">Isolerar bibliotek för validering från maskin varu information</span><span class="sxs-lookup"><span data-stu-id="df107-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="df107-159">Isolerar program från maskin varu information</span><span class="sxs-lookup"><span data-stu-id="df107-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="df107-160">Automatisk uppdatering av ändrade områden i bakgrunden</span><span class="sxs-lookup"><span data-stu-id="df107-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="df107-161">Flera arbets ytor med skiktning och över gång stöds</span><span class="sxs-lookup"><span data-stu-id="df107-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="df107-162">Kan anropas direkt av program varan</span><span class="sxs-lookup"><span data-stu-id="df107-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="df107-163">Driv rutin (er) för indrivmedel</span><span class="sxs-lookup"><span data-stu-id="df107-163">Input device driver(s)</span></span>

* <span data-ttu-id="df107-164">Maskin varu specifik support, Azure återställnings tider-GUIX och-program som är isolerade från maskin varu information</span><span class="sxs-lookup"><span data-stu-id="df107-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="df107-165">Motstånds touch, Anfang och knapps ATS som stöds</span><span class="sxs-lookup"><span data-stu-id="df107-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="df107-166">Inmatade händelser som skickas till Azure återställnings tider GUIX Event Queue</span><span class="sxs-lookup"><span data-stu-id="df107-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="df107-167">Visa driv rutiner</span><span class="sxs-lookup"><span data-stu-id="df107-167">Display drivers</span></span>

* <span data-ttu-id="df107-168">Maskinvaruspecifika support</span><span class="sxs-lookup"><span data-stu-id="df107-168">Hardware-specific support</span></span>

* <span data-ttu-id="df107-169">Generiska driv rutiner som tillhandahålls för alla färgdjup och format</span><span class="sxs-lookup"><span data-stu-id="df107-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="df107-170">Anpassad för att använda tillgängliga grafik acceleratorer</span><span class="sxs-lookup"><span data-stu-id="df107-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="df107-171">Mål maskin vara</span><span class="sxs-lookup"><span data-stu-id="df107-171">Target hardware</span></span>

* <span data-ttu-id="df107-172">Nästan all maskin vara som kan hantera grafiska utdata är kompatibel med GUIX</span><span class="sxs-lookup"><span data-stu-id="df107-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="df107-173">Flera fysiska skärmar stöds</span><span class="sxs-lookup"><span data-stu-id="df107-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="df107-174">Minimalt RAM-och Flash-krav</span><span class="sxs-lookup"><span data-stu-id="df107-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="df107-175">Skapa eleganta användar gränssnitt</span><span class="sxs-lookup"><span data-stu-id="df107-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="df107-176">Azure återställnings tider GUIX och Azure återställnings tider GUIX Studio innehåller alla funktioner som behövs för att skapa unika eleganta användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="df107-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="df107-177">Standard paketet för Azure återställnings tider-GUIX innehåller olika exempel användar gränssnitt, inklusive en medicinsk enhets referens, en Smart Watch-referens, en referens för start automatisering, en industriella kontroll referens, en referens för en bil och olika exempel på Sprite och animeringar.</span><span class="sxs-lookup"><span data-stu-id="df107-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="df107-178">Klicka på referens exemplen som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="df107-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="df107-179">Start automatisering</span><span class="sxs-lookup"><span data-stu-id="df107-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="df107-180">Sjukdom</span><span class="sxs-lookup"><span data-stu-id="df107-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="df107-181">Konsument</span><span class="sxs-lookup"><span data-stu-id="df107-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="df107-182">Vita varor</span><span class="sxs-lookup"><span data-stu-id="df107-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="df107-183">Fordon</span><span class="sxs-lookup"><span data-stu-id="df107-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="df107-184">Åtnjut</span><span class="sxs-lookup"><span data-stu-id="df107-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="df107-185">Varje Azure återställnings tider GUIX-referens har ett motsvarande Azure återställnings tider GUIX Studio-projekt som definierar alla grafiska element i referens designen.</span><span class="sxs-lookup"><span data-stu-id="df107-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="df107-186">Det är enkelt att ändra en referens design.</span><span class="sxs-lookup"><span data-stu-id="df107-186">Changing a reference design is easy.</span></span> <span data-ttu-id="df107-187">Öppna bara motsvarande Azure återställnings tider GUIX-projekt, gör önskade ändringar, spara projektet och välj sedan *projekt*.</span><span class="sxs-lookup"><span data-stu-id="df107-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="df107-188">Generera alla utdatafiler för att generera C-koden för Azure återställnings tider-GUIX.</span><span class="sxs-lookup"><span data-stu-id="df107-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="df107-189">Du behöver bara återskapa mål programmet och köra för att se den ändrade referens designen.</span><span class="sxs-lookup"><span data-stu-id="df107-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="df107-190">Små</span><span class="sxs-lookup"><span data-stu-id="df107-190">Small-footprint</span></span>

<span data-ttu-id="df107-191">Azure återställnings tider GUIX har ett remarkably litet minimalt utrymme på 13.2 KB av FLASH och 4KB RAM för grundläggande support, inklusive det minne som krävs för en arbets yta.</span><span class="sxs-lookup"><span data-stu-id="df107-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="df107-192">För en skärm med intern GRAM och själv uppdaterings teknik krävs inget minne på arbets ytan.</span><span class="sxs-lookup"><span data-stu-id="df107-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="df107-193">Men för att förbättra ritnings prestanda, eller för en visnings konfiguration som inte använder den lokala delen i GRAM, definieras ett minnes område för arbets ytan av programmet.</span><span class="sxs-lookup"><span data-stu-id="df107-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="df107-194">Minnes kraven för arbets ytan är en funktion i arbets ytans storlek samt färgdjup och definieras av formeln:</span><span class="sxs-lookup"><span data-stu-id="df107-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="df107-195"><i>RAM för arbets yta (byte) = (x \* y \* (BPP/8))</i></span><span class="sxs-lookup"><span data-stu-id="df107-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="df107-196">Där "x" och "y" är dimensionerna för arbets ytan (visas).</span><span class="sxs-lookup"><span data-stu-id="df107-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="df107-197">De flesta program använder sig av grafiska resurser som inte ingår i kärn lagrings kraven för Azure återställnings tider GUIX-bibliotek.</span><span class="sxs-lookup"><span data-stu-id="df107-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="df107-198">Dessa resurser innehåller teckensnitt, grafiska ikoner (pixelmaps) och statiska strängar.</span><span class="sxs-lookup"><span data-stu-id="df107-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="df107-199">Dessa data kan lagras i avsnittet CONST Memory (t. ex. FLASH).</span><span class="sxs-lookup"><span data-stu-id="df107-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="df107-200">Storleken på det här minnes området är beroende av ett antal faktorer, inklusive antalet och storleken på unika teckensnitt, antalet och storleken på de grafiska ikoner som används, utdataformatet och huruvida varje resurs använder komprimerade data, eftersom Azure återställnings tider GUIX stöder RLE-komprimering av både teckensnitts-och Pixelmap-data.</span><span class="sxs-lookup"><span data-stu-id="df107-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="df107-201">Lagrings kraven för varje resurs visas i programmet Azure återställnings tider GUIX Studio, så att användaren kan spåra och övervaka mängden Flash-minne som kommer att konsumeras av program resurserna.</span><span class="sxs-lookup"><span data-stu-id="df107-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="df107-202">Precis som Azure återställnings tider ThreadX skalas storleken på Azure återställnings tider-GUIX automatiskt utifrån de tjänster som faktiskt används av programmet.</span><span class="sxs-lookup"><span data-stu-id="df107-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="df107-203">Detta eliminerar behovet av komplicerade konfigurations-och bygg parametrar, vilket gör det enklare för utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="df107-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="df107-204">Snabb körning</span><span class="sxs-lookup"><span data-stu-id="df107-204">Fast execution</span></span>

<span data-ttu-id="df107-205">Azure återställnings tider GUIX skrivs exklusivt i C och har utformats för snabbhet.</span><span class="sxs-lookup"><span data-stu-id="df107-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="df107-206">Azure återställnings tider-GUIX har minimalt internt funktions anrops lager.</span><span class="sxs-lookup"><span data-stu-id="df107-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="df107-207">Dessutom tillhandahåller Azure återställnings tider-GUIX optimerat bortfall, ritning och händelse hantering.</span><span class="sxs-lookup"><span data-stu-id="df107-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="df107-208">Allt detta och en allmän prestanda orienterad design filosofi hjälper Azure återställnings tider GUIX att uppnå snabbast möjliga prestanda.</span><span class="sxs-lookup"><span data-stu-id="df107-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="df107-209">Förcertifierat av TUV till många säkerhets standarder</span><span class="sxs-lookup"><span data-stu-id="df107-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="df107-210">Azure återställnings tider GUIX har certifierats av SGS-TUV Saar för användning i säkerhets kritiska system, enligt IEC-61508 SIL 4, IEC-62304 SW säkerhets klass C, ISO 26262 ASIL D och EN 50128.</span><span class="sxs-lookup"><span data-stu-id="df107-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="df107-211">Certifieringen bekräftar att Azure återställnings tider GUIX kan användas i utvecklingen av säkerhetsrelaterad program vara för de högsta säkerhets integritets nivåerna IEC-61508, IEC-62304, ISO 26262 och EN 50128 för "fungerande säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system".</span><span class="sxs-lookup"><span data-stu-id="df107-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="df107-212">SGS – TUV Saar, som bildas genom ett gemensamt företag i Tyskland SGS-Group och TUV Saarland, har blivit det ledande ackrediterade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad program vara för säkerhetsrelaterade system i hela världen.</span><span class="sxs-lookup"><span data-stu-id="df107-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="df107-213">Den industriella säkerhets standarden IEC 61508 och alla standarder som är härledda från IT, inklusive IEC-62304, ISO 26262 och EN 50128, används för att säkerställa den funktionella säkerheten för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, process kontroll system, industriella maskiner, bil-och järnvägs styrnings system.</span><span class="sxs-lookup"><span data-stu-id="df107-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="df107-214">Enkel, lätt att använda</span><span class="sxs-lookup"><span data-stu-id="df107-214">Simple, easy-to-use</span></span>

<span data-ttu-id="df107-215">Azure återställnings tider GUIX är mycket enkelt att använda och Azure återställnings tider GUIX Studio gör det ännu enklare genom att låta utvecklare visuellt utforma på Skriv bordet och generera C-kod som körs på det faktiska målet.</span><span class="sxs-lookup"><span data-stu-id="df107-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="df107-216">Programmen kan sedan lägga till egna funktioner för anpassad händelse hantering och-ritning för att slutföra sitt grafiska användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="df107-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="df107-217">Det är enkelt att använda Azure återställnings tider GUIX-API: et.</span><span class="sxs-lookup"><span data-stu-id="df107-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="df107-218">Azure återställnings tider GUIX-API: et är både intuitivt och mycket funktionellt.</span><span class="sxs-lookup"><span data-stu-id="df107-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="df107-219">API-namnen består av riktiga ord och inte "alfabetet soppor" och/eller de förkortade namn som är vanliga i andra fil system produkter.</span><span class="sxs-lookup"><span data-stu-id="df107-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="df107-220">Alla Azure återställnings tider GUIX-API: er har en ledande *gx_* och följer en namn konvention för substantiv-verb.</span><span class="sxs-lookup"><span data-stu-id="df107-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="df107-221">Det finns dessutom en funktions konsekvens i hela API: et.</span><span class="sxs-lookup"><span data-stu-id="df107-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="df107-222">Till exempel kallas alla API: er som initierar ett kontroll block för widgeten &lt; widget_type &gt; _create och Create Function-parametrarna för varje widget definieras alltid i samma ordning.</span><span class="sxs-lookup"><span data-stu-id="df107-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="df107-223">Omfattande uppsättning inbyggda widgetar</span><span class="sxs-lookup"><span data-stu-id="df107-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="df107-224">Azure återställnings tider GUIX innehåller en omfattande uppsättning inbyggda widgetar, inklusive:</span><span class="sxs-lookup"><span data-stu-id="df107-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="df107-225">Drag meny</span><span class="sxs-lookup"><span data-stu-id="df107-225">Accordion Menu</span></span>

* <span data-ttu-id="df107-226">Button (Knapp)</span><span class="sxs-lookup"><span data-stu-id="df107-226">Button</span></span>

* <span data-ttu-id="df107-227">Checkbox</span><span class="sxs-lookup"><span data-stu-id="df107-227">Checkbox</span></span>

* <span data-ttu-id="df107-228">Cirkulär mätare</span><span class="sxs-lookup"><span data-stu-id="df107-228">Circular Gauge</span></span>

* <span data-ttu-id="df107-229">Nedrullningsbar listruta</span><span class="sxs-lookup"><span data-stu-id="df107-229">Drop Down List</span></span>

* <span data-ttu-id="df107-230">Vågrät lista</span><span class="sxs-lookup"><span data-stu-id="df107-230">Horizontal List</span></span>

* <span data-ttu-id="df107-231">Vågrät rullnings fönstret</span><span class="sxs-lookup"><span data-stu-id="df107-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="df107-232">Ikon</span><span class="sxs-lookup"><span data-stu-id="df107-232">Icon</span></span>

* <span data-ttu-id="df107-233">Ikon knapp</span><span class="sxs-lookup"><span data-stu-id="df107-233">Icon Button</span></span>

* <span data-ttu-id="df107-234">Linje diagram</span><span class="sxs-lookup"><span data-stu-id="df107-234">Line Chart</span></span>

* <span data-ttu-id="df107-235">Meny</span><span class="sxs-lookup"><span data-stu-id="df107-235">Menu</span></span>

* <span data-ttu-id="df107-236">Text knapp med flera rader</span><span class="sxs-lookup"><span data-stu-id="df107-236">Multi Line Text Button</span></span>

* <span data-ttu-id="df107-237">Text indata från flera rader</span><span class="sxs-lookup"><span data-stu-id="df107-237">Multi Line Text Input</span></span>

* <span data-ttu-id="df107-238">Text visning med flera rader</span><span class="sxs-lookup"><span data-stu-id="df107-238">Multi Line Text View</span></span>

* <span data-ttu-id="df107-239">Numerisk Pixelmap-prompt</span><span class="sxs-lookup"><span data-stu-id="df107-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="df107-240">Numerisk prompt</span><span class="sxs-lookup"><span data-stu-id="df107-240">Numeric Prompt</span></span>

* <span data-ttu-id="df107-241">Numeriskt rullnings hjul</span><span class="sxs-lookup"><span data-stu-id="df107-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="df107-242">Pixelmap-knapp</span><span class="sxs-lookup"><span data-stu-id="df107-242">Pixelmap Button</span></span>

* <span data-ttu-id="df107-243">Pixelmap-prompt</span><span class="sxs-lookup"><span data-stu-id="df107-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="df107-244">Pixelmap-skjutreglage</span><span class="sxs-lookup"><span data-stu-id="df107-244">Pixelmap Slider</span></span>

* <span data-ttu-id="df107-245">Pixelmap Sprite</span><span class="sxs-lookup"><span data-stu-id="df107-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="df107-246">Förlopps indikator</span><span class="sxs-lookup"><span data-stu-id="df107-246">Progress Bar</span></span>

* <span data-ttu-id="df107-247">Prompt</span><span class="sxs-lookup"><span data-stu-id="df107-247">Prompt</span></span>

* <span data-ttu-id="df107-248">Förlopps indikator för radiell</span><span class="sxs-lookup"><span data-stu-id="df107-248">Radial Progress Bar</span></span>

* <span data-ttu-id="df107-249">Alternativ knapp</span><span class="sxs-lookup"><span data-stu-id="df107-249">Radio Button</span></span>

* <span data-ttu-id="df107-250">Rulla hjul</span><span class="sxs-lookup"><span data-stu-id="df107-250">Scroll Wheel</span></span>

* <span data-ttu-id="df107-251">Text ingång för enskild rad</span><span class="sxs-lookup"><span data-stu-id="df107-251">Single Line Text Input</span></span>

* <span data-ttu-id="df107-252">Slider</span><span class="sxs-lookup"><span data-stu-id="df107-252">Slider</span></span>

* <span data-ttu-id="df107-253">Sträng rullnings hjul</span><span class="sxs-lookup"><span data-stu-id="df107-253">String Scroll Wheel</span></span>

* <span data-ttu-id="df107-254">Text knapp</span><span class="sxs-lookup"><span data-stu-id="df107-254">Text Button</span></span>

* <span data-ttu-id="df107-255">Trädvy</span><span class="sxs-lookup"><span data-stu-id="df107-255">Tree View</span></span>

* <span data-ttu-id="df107-256">Lodrät lista</span><span class="sxs-lookup"><span data-stu-id="df107-256">Vertical List</span></span>

* <span data-ttu-id="df107-257">Lodrät rullnings List</span><span class="sxs-lookup"><span data-stu-id="df107-257">Vertical Scrollbar</span></span>

<span data-ttu-id="df107-258">Det är enkelt för programmet att skapa egna kund-widgetar.</span><span class="sxs-lookup"><span data-stu-id="df107-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="df107-259">Slutför rit-API på låg nivå</span><span class="sxs-lookup"><span data-stu-id="df107-259">Complete low-level drawing API</span></span>

<span data-ttu-id="df107-260">Azure återställnings tider GUIX innehåller ett robust Drawing-API för arbets ytor, vilket gör att programmet kan återge komplexa grafiska former.</span><span class="sxs-lookup"><span data-stu-id="df107-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="df107-261">Alla funktioner har stöd för kant utjämning på hög färg djups mål och alla former kan fyllas i vår disposition, inklusive solida och Pixelmap mönster fyllningar.</span><span class="sxs-lookup"><span data-stu-id="df107-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="df107-262">Alla ritnings primitiver stöder pensel alfa vid körning med 16 BPP och högre färgdjup.</span><span class="sxs-lookup"><span data-stu-id="df107-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="df107-263">Ritnings funktioner omfattar:</span><span class="sxs-lookup"><span data-stu-id="df107-263">Drawing functions include:</span></span>

* <span data-ttu-id="df107-264">Rita båge</span><span class="sxs-lookup"><span data-stu-id="df107-264">Arc Draw</span></span>

* <span data-ttu-id="df107-265">Cirkels rit objekt</span><span class="sxs-lookup"><span data-stu-id="df107-265">Circle Draw</span></span>

* <span data-ttu-id="df107-266">Linje rit</span><span class="sxs-lookup"><span data-stu-id="df107-266">Line Draw</span></span>

* <span data-ttu-id="df107-267">Cirkel diagram</span><span class="sxs-lookup"><span data-stu-id="df107-267">Pie Draw</span></span>

* <span data-ttu-id="df107-268">Pixelmap-mix</span><span class="sxs-lookup"><span data-stu-id="df107-268">Pixelmap Blend</span></span>

* <span data-ttu-id="df107-269">Pixelmap-panel</span><span class="sxs-lookup"><span data-stu-id="df107-269">Pixelmap Tile</span></span>

* <span data-ttu-id="df107-270">Rita polygon</span><span class="sxs-lookup"><span data-stu-id="df107-270">Polygon Draw</span></span>

* <span data-ttu-id="df107-271">Rita text</span><span class="sxs-lookup"><span data-stu-id="df107-271">Text Draw</span></span>

* <span data-ttu-id="df107-272">Ackord Draw</span><span class="sxs-lookup"><span data-stu-id="df107-272">Chord Draw</span></span>

* <span data-ttu-id="df107-273">Ellips, rita</span><span class="sxs-lookup"><span data-stu-id="df107-273">Ellipse Draw</span></span>

* <span data-ttu-id="df107-274">Pixel rit</span><span class="sxs-lookup"><span data-stu-id="df107-274">Pixel Draw</span></span>

* <span data-ttu-id="df107-275">Pixelmap Draw</span><span class="sxs-lookup"><span data-stu-id="df107-275">Pixelmap Draw</span></span>

* <span data-ttu-id="df107-276">Pixelmap rotera</span><span class="sxs-lookup"><span data-stu-id="df107-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="df107-277">Rektangel-rit</span><span class="sxs-lookup"><span data-stu-id="df107-277">Rectangle Draw</span></span>

* <span data-ttu-id="df107-278">Text blandning</span><span class="sxs-lookup"><span data-stu-id="df107-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="df107-279">Standard teckensnitt som är standard och lätt att lägga till</span><span class="sxs-lookup"><span data-stu-id="df107-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="df107-280">Azure återställnings tider-GUIX innehåller en kostnads fri uppsättning TrueType-teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="df107-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="df107-281">Utvecklare kan lägga till ytterligare TrueType-teckensnitt som du vill.</span><span class="sxs-lookup"><span data-stu-id="df107-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="df107-282">Teckensnitts formatet för Azure återställnings tider-GUIX stöder 8bpp anti-aliasing, 4bpp kant utjämning och 1bpp monokroma teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="df107-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="df107-283">För de flesta resurs begränsade program återger Azure återställnings tider GUIX TrueType-teckensnitten till ett komprimerat bitmappsformat med hjälp av vårt GUIX Studio Desktop-verktyg.</span><span class="sxs-lookup"><span data-stu-id="df107-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="df107-284">Implementering av anpassad JPG-och PNG-avkodare</span><span class="sxs-lookup"><span data-stu-id="df107-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="df107-285">Anpassad JPG-och PNG-avkodare implementering av JPG-och PNG-filavkodare.</span><span class="sxs-lookup"><span data-stu-id="df107-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="df107-286">Den här implementeringen stöder konvertering av färg område, rastrering och körning av Azure återställnings tider GUIX-kompatibla Pixelmap format-bilder.</span><span class="sxs-lookup"><span data-stu-id="df107-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="df107-287">Omfattande skärm-och pekskärm-stöd</span><span class="sxs-lookup"><span data-stu-id="df107-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="df107-288">Azure återställnings tider GUIX innehåller allmänna visnings driv rutiner för nästan alla färg format, inklusive 1bpp monokrom, 8 BPP-palett, 8 BPP 3:3:2-format,</span><span class="sxs-lookup"><span data-stu-id="df107-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="df107-289">16 BPP 565 RGB-format, 16 BPP 4:4:4:4-format, 32 BPP x:r: g:b-format och 32 BPP a:r: g:b-format.</span><span class="sxs-lookup"><span data-stu-id="df107-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="df107-290">Dessutom är Azure återställnings tider-GUIX integrerat med många av de mest populära LCD-styrenheterna och maskin varu acceleratorer (ST ChromeArt, Renesas-synergieffekter osv.).</span><span class="sxs-lookup"><span data-stu-id="df107-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="df107-291">Azure återställnings tider GUIX har fullt stöd för pekskärm (inklusive stöd för gester), pennor och virtuella tangent bords enheter.</span><span class="sxs-lookup"><span data-stu-id="df107-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="df107-292">Verktyget Azure återställnings tider GUIX Studio Desktop WYSIWYG</span><span class="sxs-lookup"><span data-stu-id="df107-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="df107-293">Azure återställnings tider GUIX Studio innehåller en komplett design miljö för WYSIWYG-skärmen som gör det möjligt för användaren att dra och släppa grafiska element som används för att skapa GUI-skärmar.</span><span class="sxs-lookup"><span data-stu-id="df107-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="df107-294">Azure återställnings tider GUIX Studio genererar automatiskt C-kod som är kompatibel med Azure återställnings tider GUIX-biblioteket, som är redo att kompileras och köras på målet.</span><span class="sxs-lookup"><span data-stu-id="df107-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="df107-295">Utvecklare kan skapa förrenderade teckensnitt för användning i ett program med hjälp av det integrerade verktyget för teckensnitts generering i Azure återställnings tider-GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="df107-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="df107-296">Teckensnitt kan skapas i svartvita format eller i ett kant bara alias och är optimerade för att spara utrymme på målet.</span><span class="sxs-lookup"><span data-stu-id="df107-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="df107-297">Teckensnitt kan innehålla valfri uppsättning tecken, inklusive Unicode-tecken för flerspråkiga program.</span><span class="sxs-lookup"><span data-stu-id="df107-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="df107-298">Azure återställnings tider GUIX Studio fören klar importen av grafik från PNG-eller JPG-filer med konvertering till komprimerade Azure återställnings tider GUIX-Pixelmaps för användning i mål systemet.</span><span class="sxs-lookup"><span data-stu-id="df107-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="df107-299">Många av widgetarna för Azure återställnings tider-GUIX är utformade för att införliva användar grafik för ett anpassat utseende och känsla.</span><span class="sxs-lookup"><span data-stu-id="df107-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="df107-300">Dessutom tillåter Azure återställnings tider GUIX Studio anpassning av standard färger och rit format som används av Azure återställnings tider GUIX-widgetar, vilket gör att utvecklare kan justera utseendet på Azure återställnings tider GUIX mycket enkelt.</span><span class="sxs-lookup"><span data-stu-id="df107-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="df107-301">Generering och underhåll av program strängar är en annan inbyggd funktion i Azure återställnings tider GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="df107-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="df107-302">Detta gör det möjligt för utvecklare att utforma ett program med ett språk för utveckling och snabbt och enkelt lägga till stöd för ytterligare språk när produkten har släppts.</span><span class="sxs-lookup"><span data-stu-id="df107-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="df107-303">Ett fullständigt Azure återställnings tider GUIX-program kan köras på ett dator skriv bord i Azure återställnings tider GUIX Studio-miljön, vilket gör det möjligt att snabbt och enkelt skapa och demonstrera användar koncept, testning av skärm flöden och observation av skärm över gångar och animeringar.</span><span class="sxs-lookup"><span data-stu-id="df107-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="df107-304">När du är klar kan en design exporteras som mål klara C-datastrukturer som är redo att kompileras och länkas till Azure återställnings tider-GUIX och Azure återställnings tider ThreadX-bibliotek.</span><span class="sxs-lookup"><span data-stu-id="df107-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="df107-305">Azure återställnings tider GUIX och Azure återställnings tider GUIX Studio stöder flera resurs teman, vilket gör att ett program enkelt kan omväxlas i körnings läge.</span><span class="sxs-lookup"><span data-stu-id="df107-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="df107-306">Teckensnitt, färger och pixelmaps kan ändras vid körning med ett enkelt API.</span><span class="sxs-lookup"><span data-stu-id="df107-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="df107-307">Läs mer om GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="df107-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="df107-308">Slutför Win32-simulering</span><span class="sxs-lookup"><span data-stu-id="df107-308">Complete Win32 simulation</span></span>

<span data-ttu-id="df107-309">Azure återställnings tider-GUIX körs på en Windows-dator med exakt samma ritnings bibliotek som körs på mål tavlan.</span><span class="sxs-lookup"><span data-stu-id="df107-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="df107-310">Med Azure återställnings tider GUIX kan du skapa och köra ett GUI-program på datorn och använda samma program kod på målet för fel sökning, snabb prototyper, demonstration och WYSIWYG mål operation.</span><span class="sxs-lookup"><span data-stu-id="df107-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="df107-311">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="df107-311">Advanced technology</span></span>

* <span data-ttu-id="df107-312">Azure återställnings tider-GUIX Advanced Technology Incorporated:</span><span class="sxs-lookup"><span data-stu-id="df107-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="df107-313">Alpha-blandning</span><span class="sxs-lookup"><span data-stu-id="df107-313">Alpha blending</span></span>

* <span data-ttu-id="df107-314">Kant utjämning</span><span class="sxs-lookup"><span data-stu-id="df107-314">Anti-Aliasing</span></span>

* <span data-ttu-id="df107-315">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="df107-315">Automatic scaling</span></span>

* <span data-ttu-id="df107-316">Bitmapps komprimering</span><span class="sxs-lookup"><span data-stu-id="df107-316">Bitmap compression</span></span>

* <span data-ttu-id="df107-317">Kombination av arbets yta</span><span class="sxs-lookup"><span data-stu-id="df107-317">Canvas blending</span></span>

* <span data-ttu-id="df107-318">Stöd för anpassad widget</span><span class="sxs-lookup"><span data-stu-id="df107-318">Custom widget support</span></span>

* <span data-ttu-id="df107-319">Stöd för uppskjuten ritning</span><span class="sxs-lookup"><span data-stu-id="df107-319">Deferred drawing support</span></span>

* <span data-ttu-id="df107-320">Stöd för gitter</span><span class="sxs-lookup"><span data-stu-id="df107-320">Dithering support</span></span>

* <span data-ttu-id="df107-321">Endian-neutral programmering</span><span class="sxs-lookup"><span data-stu-id="df107-321">Endian neutral programming</span></span>

* <span data-ttu-id="df107-322">Support för maskin varu Accelerator</span><span class="sxs-lookup"><span data-stu-id="df107-322">Hardware accelerator support</span></span>

* <span data-ttu-id="df107-323">Flerspråkig support och UTF-8-kodning</span><span class="sxs-lookup"><span data-stu-id="df107-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="df107-324">Stöd för flera skärmar och arbets ytor</span><span class="sxs-lookup"><span data-stu-id="df107-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="df107-325">Optimerad klippning, ritning och händelse hantering</span><span class="sxs-lookup"><span data-stu-id="df107-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="df107-326">Körnings-JPEG-och PNG-avkodare</span><span class="sxs-lookup"><span data-stu-id="df107-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="df107-327">Skalning och teman</span><span class="sxs-lookup"><span data-stu-id="df107-327">Skinning and Themes</span></span>

* <span data-ttu-id="df107-328">Stöder monokrom till 32-bitars True-Color med alpha Graphics-format</span><span class="sxs-lookup"><span data-stu-id="df107-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="df107-329">Stöd för över gångar, Sprite och animering</span><span class="sxs-lookup"><span data-stu-id="df107-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="df107-330">Win32-simulering</span><span class="sxs-lookup"><span data-stu-id="df107-330">Win32 simulation</span></span>

* <span data-ttu-id="df107-331">Fönster hantering inklusive visnings fönster och Z-ordning underhåll</span><span class="sxs-lookup"><span data-stu-id="df107-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="df107-332">Snabbast tid till marknad</span><span class="sxs-lookup"><span data-stu-id="df107-332">Fastest time-to-market</span></span>

<span data-ttu-id="df107-333">Azure återställnings tider GUIX är enkelt att installera, lära sig, använda, felsöka, verifiera, certifiera och underhålla.</span><span class="sxs-lookup"><span data-stu-id="df107-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="df107-334">Azure återställnings tider GUIX Studio hjälper också till att göra inbäddade GUI-design och implementering enklare.</span><span class="sxs-lookup"><span data-stu-id="df107-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="df107-335">Därför är Azure återställnings tider-GUIX en av de mest populära GUI-lösningarna för inbäddade IoT-enheter.</span><span class="sxs-lookup"><span data-stu-id="df107-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="df107-336">Vår konsekventa tid till marknads fördelen bygger på:</span><span class="sxs-lookup"><span data-stu-id="df107-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="df107-337">Kvalitets dokumentation – Läs vår [Användar handbok för Azure återställnings tider GUIX](about-guix.md) och se själv!</span><span class="sxs-lookup"><span data-stu-id="df107-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="df107-338">Fullständig käll kods tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="df107-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="df107-339">Lätt att använda API</span><span class="sxs-lookup"><span data-stu-id="df107-339">Easy-to-use API</span></span>

* <span data-ttu-id="df107-340">Omfattande och avancerad funktions uppsättning</span><span class="sxs-lookup"><span data-stu-id="df107-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="df107-341">En enkel licens</span><span class="sxs-lookup"><span data-stu-id="df107-341">One Simple License</span></span>

<span data-ttu-id="df107-342">Det kostar inget att använda och testa käll koden och ingen kostnad för produktions licenser när de distribueras till förinstallerade enheter, men alla andra enheter behöver en enkel årlig licens.</span><span class="sxs-lookup"><span data-stu-id="df107-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="df107-343">Fullständig käll kod med högsta kvalitet</span><span class="sxs-lookup"><span data-stu-id="df107-343">Full, highest-quality source code</span></span>

<span data-ttu-id="df107-344">Under åren har Azure återställnings tider NetX-källkoden ställt in kvalitet och enkel förståelse.</span><span class="sxs-lookup"><span data-stu-id="df107-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="df107-345">Dessutom tillhandahåller konventionen om en funktion per fil för enkel käll navigering.</span><span class="sxs-lookup"><span data-stu-id="df107-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="df107-346">Har stöd för de flesta populära arkitekturerna</span><span class="sxs-lookup"><span data-stu-id="df107-346">Supports most popular architectures</span></span>

<span data-ttu-id="df107-347">Azure återställnings tider-GUIX körs på de flesta populära 32/64-bitars mikroprocessorer, färdiga, fullständigt testade och fullt stödda, inklusive följande:</span><span class="sxs-lookup"><span data-stu-id="df107-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="df107-348">Avancerade arkitekturer:</span><span class="sxs-lookup"><span data-stu-id="df107-348">Advanced Architectures:</span></span>

<span data-ttu-id="df107-349">**Analoga enheter**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="df107-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="df107-350">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="df107-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="df107-351">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="df107-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="df107-352">**Arm**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitars/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="df107-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="df107-353">**Takt**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="df107-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="df107-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="df107-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="df107-355">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="df107-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="df107-356">**Kiseldioxid**: ESI – RISC</span><span class="sxs-lookup"><span data-stu-id="df107-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="df107-357">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="df107-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="df107-358">**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="df107-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="df107-359">**Mikrochip**: avr32, ARM7, ARM9, cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/sa, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="df107-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="df107-360">**Mikrohalv**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="df107-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="df107-361">**NXP**: LPC, ARM7, ARM9, powerpc, 68K, I.MX, coldfire, Kinetis cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="df107-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="df107-362">**Renesas**: SH, HS, V850, RX, RZ, synergieffekt</span><span class="sxs-lookup"><span data-stu-id="df107-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="df107-363">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="df107-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="df107-364">**Sammanfattning**: båge 600, 700, båge EM, båg HS</span><span class="sxs-lookup"><span data-stu-id="df107-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="df107-365">**St**: STM32, ARM7, ARM9, cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="df107-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="df107-366">**TL**: C5xxx, C6xxx, Stellaris, Sitara, tiva-C</span><span class="sxs-lookup"><span data-stu-id="df107-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="df107-367">**Wave-bearbetning**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="df107-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="df107-368">**Xilinx**: mikroblixt, powerpc 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="df107-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
