---
title: Förstå Azure RTOS GUIX och Azure RTOS GUIX Studio
description: Azure RTOS GUIX är ett paket av professionell kvalitet som skapats för att uppfylla behoven hos utvecklare av inbäddade system.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754938"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="73519-103">Översikt över Azure RTOS GUIX och Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="73519-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="73519-104">Azure GUIX embedded GUI är Microsofts avancerade GUI-lösning i branschklass som utformats specifikt för djupt inbäddade, realtids- och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="73519-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="73519-105">Microsoft tillhandahåller också ett komplett WYSIWYG-skrivbordsdesignverktyg med namnet Azure RTOS GUIX Studio, som gör att utvecklare kan utforma sitt GUI på skrivbordet och generera Azure RTOS GUIX-inbäddad GUI-kod som sedan kan exporteras till målet.</span><span class="sxs-lookup"><span data-stu-id="73519-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="73519-106">Azure RTOS GUIX är helt integrerat med Azure RTOS ThreadX RTOS och är tillgängligt för många av de processorer som stöds av Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="73519-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="73519-107">Allt detta i kombination med ett mycket litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS GUIX till det perfekta valet för de mest krävande inbäddade IoT-programmen som kräver ett användargränssnitt.</span><span class="sxs-lookup"><span data-stu-id="73519-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="73519-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="73519-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="73519-109">Kraftfulla API:er</span><span class="sxs-lookup"><span data-stu-id="73519-109">Powerful APIs</span></span>

* <span data-ttu-id="73519-110">Fullständigt stöd för direkt arbetsyteritning vid behov</span><span class="sxs-lookup"><span data-stu-id="73519-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="73519-111">Enkelt att interagera med Azure RTOS GUIX Studio-genererad kod</span><span class="sxs-lookup"><span data-stu-id="73519-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="73519-112">API:er för linje, rektangel, polygon osv.</span><span class="sxs-lookup"><span data-stu-id="73519-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="73519-113">API:er för cirkel, båge, cirkel, ellips osv.</span><span class="sxs-lookup"><span data-stu-id="73519-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="73519-114">API:er för textritning och placering</span><span class="sxs-lookup"><span data-stu-id="73519-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="73519-115">Antialias, strukturfyllningar och heldragna fyllningar</span><span class="sxs-lookup"><span data-stu-id="73519-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="73519-116">API:er för att skapa och ändra skärmar och widgetar</span><span class="sxs-lookup"><span data-stu-id="73519-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="73519-117">Azure RTOS GUIX Studio-genererade filer</span><span class="sxs-lookup"><span data-stu-id="73519-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="73519-118">Automatiskt genererade ANSI C-källfiler</span><span class="sxs-lookup"><span data-stu-id="73519-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="73519-119">Isolerar programprogramvara från layoutinformation</span><span class="sxs-lookup"><span data-stu-id="73519-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="73519-120">Innehåller teckensnitt och bilder som krävs av ui-designen</span><span class="sxs-lookup"><span data-stu-id="73519-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="73519-121">Genererade filer som kompilerats med programkod</span><span class="sxs-lookup"><span data-stu-id="73519-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="73519-122">Skärmlayouten kan uppdateras utan att programlogiken påverkas</span><span class="sxs-lookup"><span data-stu-id="73519-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="73519-123">Resurs-ID:er skapar språk- och temaoberoende</span><span class="sxs-lookup"><span data-stu-id="73519-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="73519-124">Anpassade funktioner för ritning och händelsebearbetning som tillhandahålls av användaren</span><span class="sxs-lookup"><span data-stu-id="73519-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="73519-125">Widgetbibliotek</span><span class="sxs-lookup"><span data-stu-id="73519-125">Widget library</span></span>

* <span data-ttu-id="73519-126">Fördefinierad men anpassningsbar uppsättning gemensamma gränssnittselement</span><span class="sxs-lookup"><span data-stu-id="73519-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="73519-127">Extremt liten, kompakt och effektiv</span><span class="sxs-lookup"><span data-stu-id="73519-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="73519-128">Biblioteket innehåller knapp, mätare, lista, fönster, rullningsreglage, skjutreglage, förloppsfält, prompt och mycket mer</span><span class="sxs-lookup"><span data-stu-id="73519-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="73519-129">Helt anpassningsbar ritning och utseende</span><span class="sxs-lookup"><span data-stu-id="73519-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="73519-130">Helt anpassningsbar åtgärd och händelsehantering</span><span class="sxs-lookup"><span data-stu-id="73519-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="73519-131">Endast de widgetar som används är länkade med programprogramvaran</span><span class="sxs-lookup"><span data-stu-id="73519-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="73519-132">Matematik och hjälpmedel</span><span class="sxs-lookup"><span data-stu-id="73519-132">Math and utilities</span></span>

* <span data-ttu-id="73519-133">Funktioner för sin, cos, arcsin, arccos, tangens, kvadratrot</span><span class="sxs-lookup"><span data-stu-id="73519-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="73519-134">Funktioner för att manipulera skärmregioner</span><span class="sxs-lookup"><span data-stu-id="73519-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="73519-135">Systemkonfiguration och start</span><span class="sxs-lookup"><span data-stu-id="73519-135">System configuration and startup</span></span>
* <span data-ttu-id="73519-136">Minnespoolsdefinition (valfritt)</span><span class="sxs-lookup"><span data-stu-id="73519-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="73519-137">Timerhantering</span><span class="sxs-lookup"><span data-stu-id="73519-137">Timer Management</span></span>
* <span data-ttu-id="73519-138">Animeringshantering</span><span class="sxs-lookup"><span data-stu-id="73519-138">Animation Management</span></span>
* <span data-ttu-id="73519-139">Underhåll av en dirty-lista</span><span class="sxs-lookup"><span data-stu-id="73519-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="73519-140">Bearbetning av avbildning</span><span class="sxs-lookup"><span data-stu-id="73519-140">Image processing</span></span>

* <span data-ttu-id="73519-141">Funktioner för körningsavkodning av jpeg- och png-bilder</span><span class="sxs-lookup"><span data-stu-id="73519-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="73519-142">Använda dithering och konvertering av färgutrymme</span><span class="sxs-lookup"><span data-stu-id="73519-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="73519-143">Bildrotation</span><span class="sxs-lookup"><span data-stu-id="73519-143">Image rotation</span></span>
* <span data-ttu-id="73519-144">Avbildningsskalning</span><span class="sxs-lookup"><span data-stu-id="73519-144">Image scaling</span></span>
* <span data-ttu-id="73519-145">Bildblandning</span><span class="sxs-lookup"><span data-stu-id="73519-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="73519-146">Händelsebearbetning</span><span class="sxs-lookup"><span data-stu-id="73519-146">Event processing</span></span>

* <span data-ttu-id="73519-147">Pausar automatiskt Azure RTOS GUIX-tråd vid inaktivitet</span><span class="sxs-lookup"><span data-stu-id="73519-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="73519-148">Händelsedriven programmeringsmodell som är populär i UI-design</span><span class="sxs-lookup"><span data-stu-id="73519-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="73519-149">Isolerar indatadrivrutiner från Azure RTOS GUIX-ritningstråd</span><span class="sxs-lookup"><span data-stu-id="73519-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="73519-150">Funktioner för att skicka och ta emot händelser</span><span class="sxs-lookup"><span data-stu-id="73519-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="73519-151">Fördefinierade händelsetyper för alla typer Azure RTOS GUIX-widget</span><span class="sxs-lookup"><span data-stu-id="73519-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="73519-152">Användardefinierade anpassade händelser som stöds</span><span class="sxs-lookup"><span data-stu-id="73519-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="73519-153">Bearbetning av arbetsyta</span><span class="sxs-lookup"><span data-stu-id="73519-153">Canvas processing</span></span>

* <span data-ttu-id="73519-154">Cklippning och Z-orderunderhåll</span><span class="sxs-lookup"><span data-stu-id="73519-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="73519-155">Isolerar widgetbibliotek från maskinvaruinformation</span><span class="sxs-lookup"><span data-stu-id="73519-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="73519-156">Isolerar program från maskinvaruinformation</span><span class="sxs-lookup"><span data-stu-id="73519-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="73519-157">Automatisk bakgrundsuppdatering av dirty areas</span><span class="sxs-lookup"><span data-stu-id="73519-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="73519-158">Flera arbetsyta med skiktning och blandning som stöds</span><span class="sxs-lookup"><span data-stu-id="73519-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="73519-159">Kan anropas direkt av programprogramvaran</span><span class="sxs-lookup"><span data-stu-id="73519-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="73519-160">Inmatning av enhetsdrivrutiner</span><span class="sxs-lookup"><span data-stu-id="73519-160">Input device driver(s)</span></span>

* <span data-ttu-id="73519-161">Maskinvaruspecifikt stöd, Azure RTOS GUIX och program som isolerats från maskinvaruinformation</span><span class="sxs-lookup"><span data-stu-id="73519-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="73519-162">Stöd för Resistive Touch, Cap Touch och keypad</span><span class="sxs-lookup"><span data-stu-id="73519-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="73519-163">Indatahändelser som skickas Azure RTOS GUIX-händelsekö</span><span class="sxs-lookup"><span data-stu-id="73519-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="73519-164">Visa drivrutiner</span><span class="sxs-lookup"><span data-stu-id="73519-164">Display drivers</span></span>

* <span data-ttu-id="73519-165">Maskinvaruspecifikt stöd</span><span class="sxs-lookup"><span data-stu-id="73519-165">Hardware-specific support</span></span>
* <span data-ttu-id="73519-166">Allmänna drivrutiner för alla färgdjup och format</span><span class="sxs-lookup"><span data-stu-id="73519-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="73519-167">Anpassad för att använda tillgängliga grafikacceleratorer</span><span class="sxs-lookup"><span data-stu-id="73519-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="73519-168">Målmaskinvara</span><span class="sxs-lookup"><span data-stu-id="73519-168">Target hardware</span></span>

* <span data-ttu-id="73519-169">Nästan vilken maskinvara som helst som kan grafisk utdata är kompatibel med GUIX</span><span class="sxs-lookup"><span data-stu-id="73519-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="73519-170">Flera fysiska skärmar stöds</span><span class="sxs-lookup"><span data-stu-id="73519-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="73519-171">Minimala krav för RAM och Flash</span><span class="sxs-lookup"><span data-stu-id="73519-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="73519-172">Skapa elegant användargränssnitt</span><span class="sxs-lookup"><span data-stu-id="73519-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="73519-173">Azure RTOS GUIX och Azure RTOS GUIX Studio innehåller alla funktioner som behövs för att skapa unikt elegant användargränssnitt.</span><span class="sxs-lookup"><span data-stu-id="73519-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="73519-174">STANDARD-AZURE RTOS GUIX-paketet innehåller olika exempelanvändargränssnitt, inklusive en referens för medicinska enheter, en referens för smart klocka, en referens för hemautomatisering, en referens för industriell kontroll, en fordonsreferens och olika exempel på personer och animering.</span><span class="sxs-lookup"><span data-stu-id="73519-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="73519-175">Klicka på de referensexempel som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="73519-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="73519-176">Hemautomatisering</span><span class="sxs-lookup"><span data-stu-id="73519-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="73519-177">Medicinsk</span><span class="sxs-lookup"><span data-stu-id="73519-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="73519-178">Konsument</span><span class="sxs-lookup"><span data-stu-id="73519-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="73519-179">Vitvaror</span><span class="sxs-lookup"><span data-stu-id="73519-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="73519-180">Fordon</span><span class="sxs-lookup"><span data-stu-id="73519-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="73519-181">Industriella</span><span class="sxs-lookup"><span data-stu-id="73519-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="73519-182">Varje Azure RTOS GUIX-referens har ett Azure RTOS GUIX Studio-projekt som definierar alla grafiska element i referensdesignen.</span><span class="sxs-lookup"><span data-stu-id="73519-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="73519-183">Det är enkelt att ändra en referensdesign.</span><span class="sxs-lookup"><span data-stu-id="73519-183">Changing a reference design is easy.</span></span> <span data-ttu-id="73519-184">Öppna bara motsvarande AZURE RTOS GUIX-projekt, gör önskade ändringar, spara projektet och välj sedan *Project*.</span><span class="sxs-lookup"><span data-stu-id="73519-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="73519-185">Generera Alla utdatafiler för att generera C-koden för Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="73519-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="73519-186">Återskapa sedan målprogrammet och kör för att observera den ändrade referensdesignen.</span><span class="sxs-lookup"><span data-stu-id="73519-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="guix-memory-footprint"></a><span data-ttu-id="73519-187">GUIX-minnesfotavtryck</span><span class="sxs-lookup"><span data-stu-id="73519-187">GUIX Memory footprint</span></span>

<span data-ttu-id="73519-188">Azure RTOS GUIX har ett mycket litet minimalt fotavtryck på 13,2 kB FLASH och 4 kB RAM för grundläggande stöd, inte det minne som krävs för en arbetsyta.</span><span class="sxs-lookup"><span data-stu-id="73519-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="73519-189">För en visning med intern GRAM och självuppdateringsteknik krävs inget arbetsyteminne.</span><span class="sxs-lookup"><span data-stu-id="73519-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="73519-190">Men för att förbättra ritningsprestanda eller för en visningskonfiguration som inte använder GRAM lokalt på skärmen definieras ett arbetsyteminne av programmet.</span><span class="sxs-lookup"><span data-stu-id="73519-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="73519-191">Minneskrav för arbetsyta är en funktion av arbetsytans storlek samt färgdjupet och definieras av formeln:</span><span class="sxs-lookup"><span data-stu-id="73519-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="73519-192"><i>RAM för arbetsyta (byte) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="73519-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="73519-193">Där "x" och "y" är arbetsytans dimensioner (visning).</span><span class="sxs-lookup"><span data-stu-id="73519-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="73519-194">De flesta program använder också grafiska resurser, som inte ingår i Azure RTOS krav för GUIX-bibliotekslagring.</span><span class="sxs-lookup"><span data-stu-id="73519-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="73519-195">Dessa resurser omfattar teckensnitt, grafiska ikoner (pixelkartor) och statiska strängar.</span><span class="sxs-lookup"><span data-stu-id="73519-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="73519-196">Dessa data kan lagras i avsnittet const memory (t.ex. FLASH).</span><span class="sxs-lookup"><span data-stu-id="73519-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="73519-197">Storleken på det här minnesområdet beror på ett antal faktorer, inklusive antalet och storleken på de unika teckensnitt som används, antalet och storleken på de grafiska ikoner som används, utdatafärgformatet och huruvida varje resurs använder komprimerade data, eftersom Azure RTOS GUIX stöder RLE-komprimering av både teckensnitts- och pixelkarta-data.</span><span class="sxs-lookup"><span data-stu-id="73519-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="73519-198">Lagringskraven för varje resurs visas i Azure RTOS GUIX Studio-programmet, så att användaren kan spåra och övervaka mängden flashminne som kommer att förbrukas av programresurserna.</span><span class="sxs-lookup"><span data-stu-id="73519-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="73519-199">Precis Azure RTOS ThreadX skalas storleken på Azure RTOS GUIX automatiskt baserat på de tjänster som faktiskt används av programmet.</span><span class="sxs-lookup"><span data-stu-id="73519-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="73519-200">Detta eliminerar praktiskt taget behovet av komplicerad konfiguration och byggparametrar, vilket gör det enklare för utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="73519-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="73519-201">Enkelt och lätt att använda</span><span class="sxs-lookup"><span data-stu-id="73519-201">Simple, easy-to-use</span></span>

<span data-ttu-id="73519-202">Azure RTOS GUIX är mycket enkelt att använda och Azure RTOS GUIX Studio gör det ännu enklare för utvecklare att designa visuellt på skrivbordet och generera C-kod som körs på det faktiska målet.</span><span class="sxs-lookup"><span data-stu-id="73519-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="73519-203">Program kan sedan lägga till egna anpassade händelsehanterings- och ritningsfunktioner för att slutföra det grafiska användargränssnittet.</span><span class="sxs-lookup"><span data-stu-id="73519-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="73519-204">Det är enkelt Azure RTOS GUIX-API:et.</span><span class="sxs-lookup"><span data-stu-id="73519-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="73519-205">DET Azure RTOS GUIX-API:et är både intuitivt och mycket funktionellt.</span><span class="sxs-lookup"><span data-stu-id="73519-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="73519-206">API-namnen består av verkliga ord och inte "alfabetet" och/eller de mycket förkortade namn som är så vanliga i andra filsystemprodukter.</span><span class="sxs-lookup"><span data-stu-id="73519-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="73519-207">Alla Azure RTOS GUIX-API:er *har en gx_* och följer en namngivningskonvention med substantivverb.</span><span class="sxs-lookup"><span data-stu-id="73519-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="73519-208">Dessutom finns det en funktionell konsekvens i hela API:et.</span><span class="sxs-lookup"><span data-stu-id="73519-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="73519-209">Till exempel har alla API:er som initierar ett widgetkontrollblock namnet widget_type _create, och funktionsparametrarna create för varje widgettyp definieras alltid i &lt; &gt; samma ordning.</span><span class="sxs-lookup"><span data-stu-id="73519-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="73519-210">Omfattande uppsättning inbyggda widgetar</span><span class="sxs-lookup"><span data-stu-id="73519-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="73519-211">Azure RTOS GUIX innehåller en omfattande uppsättning inbyggda widgetar, inklusive:</span><span class="sxs-lookup"><span data-stu-id="73519-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="73519-212">Överensstämmelsemeny</span><span class="sxs-lookup"><span data-stu-id="73519-212">Accordion Menu</span></span>
* <span data-ttu-id="73519-213">Button (Knapp)</span><span class="sxs-lookup"><span data-stu-id="73519-213">Button</span></span>
* <span data-ttu-id="73519-214">Checkbox</span><span class="sxs-lookup"><span data-stu-id="73519-214">Checkbox</span></span>
* <span data-ttu-id="73519-215">Cirkelmätare</span><span class="sxs-lookup"><span data-stu-id="73519-215">Circular Gauge</span></span>
* <span data-ttu-id="73519-216">Rullgardinsmenyn</span><span class="sxs-lookup"><span data-stu-id="73519-216">Drop Down List</span></span>
* <span data-ttu-id="73519-217">Vågrät lista</span><span class="sxs-lookup"><span data-stu-id="73519-217">Horizontal List</span></span>
* <span data-ttu-id="73519-218">Vågrätt rullningslistfönster</span><span class="sxs-lookup"><span data-stu-id="73519-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="73519-219">Ikon</span><span class="sxs-lookup"><span data-stu-id="73519-219">Icon</span></span>
* <span data-ttu-id="73519-220">Ikonknapp</span><span class="sxs-lookup"><span data-stu-id="73519-220">Icon Button</span></span>
* <span data-ttu-id="73519-221">Linjediagram</span><span class="sxs-lookup"><span data-stu-id="73519-221">Line Chart</span></span>
* <span data-ttu-id="73519-222">Meny</span><span class="sxs-lookup"><span data-stu-id="73519-222">Menu</span></span>
* <span data-ttu-id="73519-223">Knappen Flerradstext</span><span class="sxs-lookup"><span data-stu-id="73519-223">Multi Line Text Button</span></span>
* <span data-ttu-id="73519-224">Textinmatning med flera linjer</span><span class="sxs-lookup"><span data-stu-id="73519-224">Multi Line Text Input</span></span>
* <span data-ttu-id="73519-225">Textvy med flera linjer</span><span class="sxs-lookup"><span data-stu-id="73519-225">Multi Line Text View</span></span>
* <span data-ttu-id="73519-226">Fråga om numerisk pixelkarta</span><span class="sxs-lookup"><span data-stu-id="73519-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="73519-227">Numerisk prompt</span><span class="sxs-lookup"><span data-stu-id="73519-227">Numeric Prompt</span></span>
* <span data-ttu-id="73519-228">Numeriskt rullningshjul</span><span class="sxs-lookup"><span data-stu-id="73519-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="73519-229">Knappen Pixelkarta</span><span class="sxs-lookup"><span data-stu-id="73519-229">Pixelmap Button</span></span>
* <span data-ttu-id="73519-230">Uppmaning om pixelkarta</span><span class="sxs-lookup"><span data-stu-id="73519-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="73519-231">Skjutreglage för bildpunktskarta</span><span class="sxs-lookup"><span data-stu-id="73519-231">Pixelmap Slider</span></span>
* <span data-ttu-id="73519-232">Pixelkarta Företr</span><span class="sxs-lookup"><span data-stu-id="73519-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="73519-233">Förloppsindikator</span><span class="sxs-lookup"><span data-stu-id="73519-233">Progress Bar</span></span>
* <span data-ttu-id="73519-234">Prompt</span><span class="sxs-lookup"><span data-stu-id="73519-234">Prompt</span></span>
* <span data-ttu-id="73519-235">Radiell förloppsstapel</span><span class="sxs-lookup"><span data-stu-id="73519-235">Radial Progress Bar</span></span>
* <span data-ttu-id="73519-236">Alternativknapp</span><span class="sxs-lookup"><span data-stu-id="73519-236">Radio Button</span></span>
* <span data-ttu-id="73519-237">Rullningshjul</span><span class="sxs-lookup"><span data-stu-id="73519-237">Scroll Wheel</span></span>
* <span data-ttu-id="73519-238">Textinmatning med en rad</span><span class="sxs-lookup"><span data-stu-id="73519-238">Single Line Text Input</span></span>
* <span data-ttu-id="73519-239">Slider</span><span class="sxs-lookup"><span data-stu-id="73519-239">Slider</span></span>
* <span data-ttu-id="73519-240">Rullningshjul för strängar</span><span class="sxs-lookup"><span data-stu-id="73519-240">String Scroll Wheel</span></span>
* <span data-ttu-id="73519-241">Textknapp</span><span class="sxs-lookup"><span data-stu-id="73519-241">Text Button</span></span>
* <span data-ttu-id="73519-242">Trädvy</span><span class="sxs-lookup"><span data-stu-id="73519-242">Tree View</span></span>
* <span data-ttu-id="73519-243">Lodrät lista</span><span class="sxs-lookup"><span data-stu-id="73519-243">Vertical List</span></span>
* <span data-ttu-id="73519-244">Lodrät rullningslist</span><span class="sxs-lookup"><span data-stu-id="73519-244">Vertical Scrollbar</span></span>

<span data-ttu-id="73519-245">Det är enkelt för programmet att skapa sina egna kundwidgetar också.</span><span class="sxs-lookup"><span data-stu-id="73519-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="73519-246">Slutföra api för lågnivåritning</span><span class="sxs-lookup"><span data-stu-id="73519-246">Complete low-level drawing API</span></span>

<span data-ttu-id="73519-247">Azure RTOS GUIX ger ett robust API för arbetsyteritning, så att programmet kan rendera komplexa grafiska former.</span><span class="sxs-lookup"><span data-stu-id="73519-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="73519-248">Alla funktioner stöder antialias för högfärgsdjupmål, och alla former kan fyllas i våra konturer, inklusive heldragen fyllning och pixelkarta.</span><span class="sxs-lookup"><span data-stu-id="73519-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="73519-249">Alla ritningsprimititit har stöd för pensel-alfa vid körning med 16 bpp och högre färgdjup.</span><span class="sxs-lookup"><span data-stu-id="73519-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="73519-250">Ritningsfunktioner är:</span><span class="sxs-lookup"><span data-stu-id="73519-250">Drawing functions include:</span></span>

* <span data-ttu-id="73519-251">Arc-rita</span><span class="sxs-lookup"><span data-stu-id="73519-251">Arc Draw</span></span>
* <span data-ttu-id="73519-252">Cirkeldrag</span><span class="sxs-lookup"><span data-stu-id="73519-252">Circle Draw</span></span>
* <span data-ttu-id="73519-253">Linjedragning</span><span class="sxs-lookup"><span data-stu-id="73519-253">Line Draw</span></span>
* <span data-ttu-id="73519-254">Cirkeldiagram</span><span class="sxs-lookup"><span data-stu-id="73519-254">Pie Draw</span></span>
* <span data-ttu-id="73519-255">Pixelkarta med blandning</span><span class="sxs-lookup"><span data-stu-id="73519-255">Pixelmap Blend</span></span>
* <span data-ttu-id="73519-256">Bildpunktskarta-panel</span><span class="sxs-lookup"><span data-stu-id="73519-256">Pixelmap Tile</span></span>
* <span data-ttu-id="73519-257">Polygon Draw</span><span class="sxs-lookup"><span data-stu-id="73519-257">Polygon Draw</span></span>
* <span data-ttu-id="73519-258">Text Draw</span><span class="sxs-lookup"><span data-stu-id="73519-258">Text Draw</span></span>
* <span data-ttu-id="73519-259">Draw -et-et-</span><span class="sxs-lookup"><span data-stu-id="73519-259">Chord Draw</span></span>
* <span data-ttu-id="73519-260">Ellips draw</span><span class="sxs-lookup"><span data-stu-id="73519-260">Ellipse Draw</span></span>
* <span data-ttu-id="73519-261">Pixel Draw</span><span class="sxs-lookup"><span data-stu-id="73519-261">Pixel Draw</span></span>
* <span data-ttu-id="73519-262">Bildpunktskarta</span><span class="sxs-lookup"><span data-stu-id="73519-262">Pixelmap Draw</span></span>
* <span data-ttu-id="73519-263">Pixelkarta – rotera</span><span class="sxs-lookup"><span data-stu-id="73519-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="73519-264">Rektangeldrag</span><span class="sxs-lookup"><span data-stu-id="73519-264">Rectangle Draw</span></span>
* <span data-ttu-id="73519-265">Text Blend</span><span class="sxs-lookup"><span data-stu-id="73519-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="73519-266">Standardfria teckensnitt och enkelt att lägga till fler</span><span class="sxs-lookup"><span data-stu-id="73519-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="73519-267">Azure RTOS GUIX innehåller en kostnadsfri uppsättning TrueType-teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="73519-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="73519-268">Utvecklare kan lägga till ytterligare TrueType-teckensnitt efter behov.</span><span class="sxs-lookup"><span data-stu-id="73519-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="73519-269">Teckensnittsformatet Azure RTOS GUIX stöder 8bpp-antialias, 4bpp-antialias och 1bpp teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="73519-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="73519-270">För de mest resursbegränsade programmen återger GUIX Azure RTOS TrueType-teckensnitten i ett komprimerat format med hjälp av vårt GUIX Studio-skrivbordsverktyg.</span><span class="sxs-lookup"><span data-stu-id="73519-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="73519-271">Anpassad implementering av JPG- och PNG-avkodare</span><span class="sxs-lookup"><span data-stu-id="73519-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="73519-272">Anpassad implementering av JPG- och PNG-avkodare för JPG- och PNG-filavkodare.</span><span class="sxs-lookup"><span data-stu-id="73519-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="73519-273">Den här implementeringen stöder konvertering av färgutrymme, dithering och körning av Azure RTOS GUIX-kompatibla bildpunktskarteformatbilder.</span><span class="sxs-lookup"><span data-stu-id="73519-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="73519-274">Omfattande stöd för visning och pekskärm</span><span class="sxs-lookup"><span data-stu-id="73519-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="73519-275">Azure RTOS GUIX innehåller allmänna visningsdrivrutiner för nästan alla färgformat, inklusive 1bpp-färgad, 8 bpp-palette, 8 bpp 3:3:2-format,</span><span class="sxs-lookup"><span data-stu-id="73519-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="73519-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format och 32 bpp a:r:g:b format.</span><span class="sxs-lookup"><span data-stu-id="73519-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="73519-277">Dessutom är Azure RTOS GUIX integrerat med många av de mest populäraSTYRENHETs- och maskinvaruacceleratorerna (ST ChromeArt, Renesas Controller osv.).</span><span class="sxs-lookup"><span data-stu-id="73519-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="73519-278">Azure RTOS GUIX har fullständigt stöd för pekskärm (inklusive gesterstöd), pennenheter och indataenheter för virtuella tangentbord.</span><span class="sxs-lookup"><span data-stu-id="73519-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="73519-279">Azure RTOS GUIX Studio-skrivbordsverktyget WYSIWYG</span><span class="sxs-lookup"><span data-stu-id="73519-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="73519-280">Azure RTOS GUIX Studio har en komplett WYSIWYG-skärmdesignmiljö där användaren kan dra och släppa grafiska element som används för att skapa GUI-skärmarna.</span><span class="sxs-lookup"><span data-stu-id="73519-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="73519-281">Azure RTOS GUIX Studio genererar automatiskt C-kod som är kompatibel med Azure RTOS GUIX-biblioteket, redo att kompileras och köras på målet.</span><span class="sxs-lookup"><span data-stu-id="73519-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="73519-282">Utvecklare kan skapa för renderade teckensnitt för användning i ett program med hjälp av det integrerade Azure RTOS GUIX Studio-verktyget för teckengenerering.</span><span class="sxs-lookup"><span data-stu-id="73519-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="73519-283">Teckensnitt kan genereras i oreda eller antialiasformat och optimeras för att spara utrymme på målet.</span><span class="sxs-lookup"><span data-stu-id="73519-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="73519-284">Teckensnitt kan innehålla valfri uppsättning tecken, inklusive Unicode-tecken för flerspråkiga program.</span><span class="sxs-lookup"><span data-stu-id="73519-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="73519-285">Azure RTOS GUIX Studio underlättar import av grafik från PNG- eller JPG-filer med konvertering till komprimerade Azure RTOS GUIX Pixelmaps för användning i målsystemet.</span><span class="sxs-lookup"><span data-stu-id="73519-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="73519-286">Många av de Azure RTOS GUIX-widgettyperna är utformade för att införliva användargrafik för ett anpassat utseende.</span><span class="sxs-lookup"><span data-stu-id="73519-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="73519-287">Dessutom tillåter Azure RTOS GUIX Studio anpassning av standardfärger och ritningsformat som används av Azure RTOS GUIX-widgetar, vilket gör det enkelt för utvecklare att finjustera utseendet på Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="73519-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="73519-288">Generering och underhåll av programsträngar är en annan inbyggd funktion Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="73519-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="73519-289">På så sätt kan utvecklare utforma ett program med ett språk för utveckling och snabbt och enkelt lägga till stöd för ytterligare språk när produkten har släppts.</span><span class="sxs-lookup"><span data-stu-id="73519-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="73519-290">Ett komplett Azure RTOS GUIX-program kan köras på en stationär dator i Azure RTOS GUIX Studio-miljön, vilket möjliggör en snabb och enkel generering och demonstration av GUI-begrepp, testning av skärmflöden och visning av skärmövergångar och animeringar.</span><span class="sxs-lookup"><span data-stu-id="73519-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="73519-291">När det är klart kan en design exporteras som målklara C-datastrukturer som är redo att kompileras och länkas till Azure RTOS GUIX- och Azure RTOS ThreadX-biblioteken.</span><span class="sxs-lookup"><span data-stu-id="73519-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="73519-292">Azure RTOS GUIX och Azure RTOS GUIX Studio har stöd för flera resursteman, så att ett program enkelt kan installeras om vid körning.</span><span class="sxs-lookup"><span data-stu-id="73519-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="73519-293">Teckensnitt, färger och pixelkartor kan ändras vid körning med ett enkelt API.</span><span class="sxs-lookup"><span data-stu-id="73519-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="73519-294">Läs mer om GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="73519-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="73519-295">Slutför Win32-simulering</span><span class="sxs-lookup"><span data-stu-id="73519-295">Complete Win32 simulation</span></span>

<span data-ttu-id="73519-296">Azure RTOS GUIX körs på Windows dator med exakt samma ritningsbibliotek som körs på måltavlan.</span><span class="sxs-lookup"><span data-stu-id="73519-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="73519-297">Med Azure RTOS GUIX kan du skapa och köra ett GUI-program på datorn och använda samma programkod på målet för felsökning, snabba prototyper, demonstration och WYSIWYG-målåtgärd.</span><span class="sxs-lookup"><span data-stu-id="73519-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="73519-298">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="73519-298">Advanced technology</span></span>

* <span data-ttu-id="73519-299">Azure RTOS GUIX avancerade teknik omfattar:</span><span class="sxs-lookup"><span data-stu-id="73519-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="73519-300">Alfablandning</span><span class="sxs-lookup"><span data-stu-id="73519-300">Alpha blending</span></span>
* <span data-ttu-id="73519-301">Antialias</span><span class="sxs-lookup"><span data-stu-id="73519-301">Anti-Aliasing</span></span>
* <span data-ttu-id="73519-302">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="73519-302">Automatic scaling</span></span>
* <span data-ttu-id="73519-303">Bitmappkomprimering</span><span class="sxs-lookup"><span data-stu-id="73519-303">Bitmap compression</span></span>
* <span data-ttu-id="73519-304">Blandning av arbetsyta</span><span class="sxs-lookup"><span data-stu-id="73519-304">Canvas blending</span></span>
* <span data-ttu-id="73519-305">Stöd för anpassad widget</span><span class="sxs-lookup"><span data-stu-id="73519-305">Custom widget support</span></span>
* <span data-ttu-id="73519-306">Stöd för uppskjuten ritning</span><span class="sxs-lookup"><span data-stu-id="73519-306">Deferred drawing support</span></span>
* <span data-ttu-id="73519-307">Stöd för dithering</span><span class="sxs-lookup"><span data-stu-id="73519-307">Dithering support</span></span>
* <span data-ttu-id="73519-308">Endiansk neutral programmering</span><span class="sxs-lookup"><span data-stu-id="73519-308">Endian neutral programming</span></span>
* <span data-ttu-id="73519-309">Stöd för maskinvaruacceleratorer</span><span class="sxs-lookup"><span data-stu-id="73519-309">Hardware accelerator support</span></span>
* <span data-ttu-id="73519-310">Stöd för flera språk och UTF-8-kodning</span><span class="sxs-lookup"><span data-stu-id="73519-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="73519-311">Stöd för flera skärmar och arbetsyta</span><span class="sxs-lookup"><span data-stu-id="73519-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="73519-312">Optimerad urklippning, ritning och händelsehantering</span><span class="sxs-lookup"><span data-stu-id="73519-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="73519-313">Runtime JPEG- och PNG-avkodare</span><span class="sxs-lookup"><span data-stu-id="73519-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="73519-314">Hudning och teman</span><span class="sxs-lookup"><span data-stu-id="73519-314">Skinning and Themes</span></span>
* <span data-ttu-id="73519-315">Har stöd för 32-bitars true-color med alfagrafikformat</span><span class="sxs-lookup"><span data-stu-id="73519-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="73519-316">Stöd för övergångar, figurer och animering</span><span class="sxs-lookup"><span data-stu-id="73519-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="73519-317">Win32-simulering</span><span class="sxs-lookup"><span data-stu-id="73519-317">Win32 simulation</span></span>
* <span data-ttu-id="73519-318">Fönsterhantering inklusive viewports- och Z-orderunderhåll</span><span class="sxs-lookup"><span data-stu-id="73519-318">Window management including Viewports and Z-order maintenance</span></span>
