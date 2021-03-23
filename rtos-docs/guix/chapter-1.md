---
title: Kapitel 1 – Introduktion till GUIX
description: GUIX är en real tids implementering av en (GUI) som är utformad exklusivt för inbäddade Azure återställnings tider ThreadX-baserade program.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827204"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="243b8-103">Kapitel 1 – Introduktion till Azure återställnings tider GUIX</span><span class="sxs-lookup"><span data-stu-id="243b8-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="243b8-104">Azure återställnings tider GUIX (GUIX) är en real tids implementering i real tid av ett grafiskt gränssnitts ramverk som utformats exklusivt för inbäddade ThreadX-baserade program.</span><span class="sxs-lookup"><span data-stu-id="243b8-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="243b8-105">Det här kapitlet innehåller en introduktion till GUIX och en beskrivning av dess program och fördelar.</span><span class="sxs-lookup"><span data-stu-id="243b8-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="243b8-106">Översikt över GUIX-funktioner</span><span class="sxs-lookup"><span data-stu-id="243b8-106">GUIX Feature Overview</span></span>

<span data-ttu-id="243b8-107">Till skillnad från många andra GUI-implementeringar har GUIX utformats för att vara flexibelt, vilket enkelt kan skalas från små mikrokontrollantbaserade program till dem som använder kraftfulla RISC-och DSP-processorer.</span><span class="sxs-lookup"><span data-stu-id="243b8-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="243b8-108">Detta är i skarpt kontrast i den offentliga domänen eller andra kommersiella implementeringar som ursprungligen är avsedda för arbets Stations miljöer, men som sedan är inkapslade i inbäddade modeller.</span><span class="sxs-lookup"><span data-stu-id="243b8-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="243b8-109">En översikt över GUIX-funktionerna finns här:</span><span class="sxs-lookup"><span data-stu-id="243b8-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="243b8-110">Lätt att använda med värdbaserade design verktyg GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="243b8-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="243b8-111">Win32-GUIX kör tids miljö för fullständig, värdbaserad prototyp</span><span class="sxs-lookup"><span data-stu-id="243b8-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="243b8-112">Stöder de flesta processorer som stöds av ThreadX</span><span class="sxs-lookup"><span data-stu-id="243b8-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="243b8-113">Skrivet exklusivt i ANSI C</span><span class="sxs-lookup"><span data-stu-id="243b8-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="243b8-114">Endian-neutral</span><span class="sxs-lookup"><span data-stu-id="243b8-114">Endian neutral</span></span>

- <span data-ttu-id="243b8-115">Minsta, snabba inbäddade GUI</span><span class="sxs-lookup"><span data-stu-id="243b8-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="243b8-116">Konfigurations Bart kör tid, antal objekt, skärm storlek osv.</span><span class="sxs-lookup"><span data-stu-id="243b8-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="243b8-117">Lätt att skriva visnings driv rutins gränssnitt</span><span class="sxs-lookup"><span data-stu-id="243b8-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="243b8-118">Färg (upp till 32-BPP färg djup), monokromt och stöd för gråskala</span><span class="sxs-lookup"><span data-stu-id="243b8-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="243b8-119">Flerspråkig support via UTF8-sträng kodning och sträng resurser</span><span class="sxs-lookup"><span data-stu-id="243b8-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="243b8-120">Standard teckensnitt som är standard och lätt att lägga till nya teckensnitt</span><span class="sxs-lookup"><span data-stu-id="243b8-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="243b8-121">Flera arbets ytor som stöds av olika storlekar</span><span class="sxs-lookup"><span data-stu-id="243b8-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="243b8-122">Flera skärmar av olika storlekar och färgdjup stöds</span><span class="sxs-lookup"><span data-stu-id="243b8-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="243b8-123">Stöd för skärm över gång (tona in, tona ut, svep osv.)</span><span class="sxs-lookup"><span data-stu-id="243b8-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="243b8-124">Stöd för pekskärm, gest och virtuellt tangent bord</span><span class="sxs-lookup"><span data-stu-id="243b8-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="243b8-125">Bitmapps komprimering</span><span class="sxs-lookup"><span data-stu-id="243b8-125">Bitmap compression</span></span>

- <span data-ttu-id="243b8-126">Stöd för alpha-mixer</span><span class="sxs-lookup"><span data-stu-id="243b8-126">Alpha Blending Support</span></span>

- <span data-ttu-id="243b8-127">Stöd för rastrering</span><span class="sxs-lookup"><span data-stu-id="243b8-127">Dither Support</span></span>

- <span data-ttu-id="243b8-128">Stöd för kant utjämning</span><span class="sxs-lookup"><span data-stu-id="243b8-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="243b8-129">Skalning och teman</span><span class="sxs-lookup"><span data-stu-id="243b8-129">Skinning and Themes</span></span>

- <span data-ttu-id="243b8-130">Kombination av arbets yta</span><span class="sxs-lookup"><span data-stu-id="243b8-130">Canvas Blending</span></span>

- <span data-ttu-id="243b8-131">Slutför fönster hantering</span><span class="sxs-lookup"><span data-stu-id="243b8-131">Complete Window Management</span></span>

  - <span data-ttu-id="243b8-132">Överordnad/underordnad relation</span><span class="sxs-lookup"><span data-stu-id="243b8-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="243b8-133">Dynamisk generering, borttagning, storleks ändring, flyttning</span><span class="sxs-lookup"><span data-stu-id="243b8-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="243b8-134">Separat hantering och ritning av händelser</span><span class="sxs-lookup"><span data-stu-id="243b8-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="243b8-135">Z-ordning</span><span class="sxs-lookup"><span data-stu-id="243b8-135">Z-order</span></span>
  - <span data-ttu-id="243b8-136">Urklipp och vyer</span><span class="sxs-lookup"><span data-stu-id="243b8-136">Clipping and views</span></span>

- <span data-ttu-id="243b8-137">Omfattande uppsättning widgetar</span><span class="sxs-lookup"><span data-stu-id="243b8-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="243b8-138">Olika knapp typer, skjutreglage och uppringningar</span><span class="sxs-lookup"><span data-stu-id="243b8-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="243b8-139">Nedrullningsbar listruta</span><span class="sxs-lookup"><span data-stu-id="243b8-139">Drop Down List</span></span>
  
  - <span data-ttu-id="243b8-140">Prompt</span><span class="sxs-lookup"><span data-stu-id="243b8-140">Prompt</span></span>

  - <span data-ttu-id="243b8-141">Vy med flera rader</span><span class="sxs-lookup"><span data-stu-id="243b8-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="243b8-142">Enkel text inspelning med flera rader</span><span class="sxs-lookup"><span data-stu-id="243b8-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="243b8-143">Tal-och text rullnings hjul</span><span class="sxs-lookup"><span data-stu-id="243b8-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="243b8-144">Fönster och rullnings lister</span><span class="sxs-lookup"><span data-stu-id="243b8-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="243b8-145">Förlopps indikator för radiell</span><span class="sxs-lookup"><span data-stu-id="243b8-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="243b8-146">Sprit</span><span class="sxs-lookup"><span data-stu-id="243b8-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="243b8-147">ANSI C-källkod</span><span class="sxs-lookup"><span data-stu-id="243b8-147">ANSI C Source Code</span></span>

<span data-ttu-id="243b8-148">GUIX skrivs helt i ANSI C och är direkt portabel till praktiskt taget vilken processor arkitektur som helst som har stöd för ANSI C-kompilator och ThreadX.</span><span class="sxs-lookup"><span data-stu-id="243b8-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="243b8-149">Även om det är skrivet i ANSI C, använder GUIX en objektorienterad modell och arv.</span><span class="sxs-lookup"><span data-stu-id="243b8-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="243b8-150">Inte en svart ruta</span><span class="sxs-lookup"><span data-stu-id="243b8-150">Not A Black Box</span></span>

<span data-ttu-id="243b8-151">De flesta distributioner av GUIX innehåller den fullständiga C-källkoden.</span><span class="sxs-lookup"><span data-stu-id="243b8-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="243b8-152">Detta eliminerar "svarta box"-problem som uppstår med många kommersiella GUI-implementeringar.</span><span class="sxs-lookup"><span data-stu-id="243b8-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="243b8-153">Genom att använda GUIX kan programutvecklare se exakt vad användar gränssnittet gör – det finns inga Mysteries!</span><span class="sxs-lookup"><span data-stu-id="243b8-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="243b8-154">Med käll koden kan du också göra programspecifika ändringar.</span><span class="sxs-lookup"><span data-stu-id="243b8-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="243b8-155">Även om det inte rekommenderas, är det verkligen fördelaktigt att ha möjlighet att ändra GUI om det behövs.</span><span class="sxs-lookup"><span data-stu-id="243b8-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="243b8-156">Dessa funktioner är särskilt praktiska för utvecklare som är vana vid att arbeta med interna eller offentliga domän produkter.</span><span class="sxs-lookup"><span data-stu-id="243b8-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="243b8-157">De förväntar sig ha källkod och möjlighet att ändra den.</span><span class="sxs-lookup"><span data-stu-id="243b8-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="243b8-158">GUIX är den ultimata GUI-programvaran för sådana utvecklare.</span><span class="sxs-lookup"><span data-stu-id="243b8-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="243b8-159">Inbäddade GUI-program</span><span class="sxs-lookup"><span data-stu-id="243b8-159">Embedded GUI Applications</span></span>

<span data-ttu-id="243b8-160">Inbäddade GUI-program är program som har ett användar gränssnitts krav och körs på mikroprocessorer som är dolda i produkter som mobil telefoner, kommunikations utrustning, fordons motorer, laser skrivare, medicinska enheter och så vidare.</span><span class="sxs-lookup"><span data-stu-id="243b8-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="243b8-161">Sådana program har nästan alltid vissa minnes-och prestanda begränsningar.</span><span class="sxs-lookup"><span data-stu-id="243b8-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="243b8-162">En annan skillnad på inbäddat GUI är att deras program vara och maskin vara har ett dedikerat syfte.</span><span class="sxs-lookup"><span data-stu-id="243b8-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="243b8-163">GUI-programvara i real tid</span><span class="sxs-lookup"><span data-stu-id="243b8-163">Real-time GUI Software</span></span>

<span data-ttu-id="243b8-164">I princip kallas GUI-programvara som måste utföra bearbetningen inom en exakt tids period. i *real tid kallas GUI-programvara i real tid* och när tids begränsningar införs i GUI-program klassificeras de som real tids program.</span><span class="sxs-lookup"><span data-stu-id="243b8-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="243b8-165">Inbäddade GUI-program är nästan alltid real tids på grund av deras inbyggda interaktion med den externa världen.</span><span class="sxs-lookup"><span data-stu-id="243b8-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="243b8-166">GUIX-förmåner</span><span class="sxs-lookup"><span data-stu-id="243b8-166">GUIX Benefits</span></span>

<span data-ttu-id="243b8-167">De främsta fördelarna med att använda GUIX för inbäddade program är högpresterande, funktions rika och mycket små minnes krav.</span><span class="sxs-lookup"><span data-stu-id="243b8-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="243b8-168">GUIX är också helt integrerat med högpresterande, multitasking Azure återställnings tider ThreadXs operativ system i real tid.</span><span class="sxs-lookup"><span data-stu-id="243b8-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="243b8-169">Förbättrad svars tid</span><span class="sxs-lookup"><span data-stu-id="243b8-169">Improved Responsiveness</span></span>

<span data-ttu-id="243b8-170">Med den GUIX produkten med höga prestanda kan program svara snabbare än någonsin tidigare.</span><span class="sxs-lookup"><span data-stu-id="243b8-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="243b8-171">Detta är särskilt viktigt för inbäddade program som antingen har en betydande mängd visuell information eller strikt tids krav för att visa sådan information.</span><span class="sxs-lookup"><span data-stu-id="243b8-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="243b8-172">Program varu underhåll</span><span class="sxs-lookup"><span data-stu-id="243b8-172">Software Maintenance</span></span>

<span data-ttu-id="243b8-173">Med hjälp av GUIX kan utvecklare enkelt partitionera GUI-aspekterna av sina inbäddade program.</span><span class="sxs-lookup"><span data-stu-id="243b8-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="243b8-174">Den här partitionerings processen gör hela utvecklings processen enkel och förbättrar det framtida program varu underhållet.</span><span class="sxs-lookup"><span data-stu-id="243b8-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="243b8-175">Ökat data flöde</span><span class="sxs-lookup"><span data-stu-id="243b8-175">Increased Throughput</span></span>

<span data-ttu-id="243b8-176">GUIX tillhandahåller det högsta tillgängliga användar gränssnittet, som direkt överför till det inbäddade programmet.</span><span class="sxs-lookup"><span data-stu-id="243b8-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="243b8-177">GUIX-program kan bearbeta användar gränssnitts information snabbare än icke-GUIX program!</span><span class="sxs-lookup"><span data-stu-id="243b8-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="243b8-178">Processor isolering</span><span class="sxs-lookup"><span data-stu-id="243b8-178">Processor Isolation</span></span>

<span data-ttu-id="243b8-179">GUIX tillhandahåller ett robust, processor oberoende gränssnitt mellan programmet och den underliggande processor-och visnings maskin varan.</span><span class="sxs-lookup"><span data-stu-id="243b8-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="243b8-180">På så sätt kan utvecklare koncentrera sig på högnivå aspekterna i användar gränssnittet i stället för att ägna extra tid åt att hantera maskin varu problem.</span><span class="sxs-lookup"><span data-stu-id="243b8-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="243b8-181">Lätt att använda</span><span class="sxs-lookup"><span data-stu-id="243b8-181">Ease of Use</span></span>

<span data-ttu-id="243b8-182">GUIX är utformad med program utvecklaren i åtanke.</span><span class="sxs-lookup"><span data-stu-id="243b8-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="243b8-183">GUIX-arkitekturen och tjänst anrops gränssnittet är lätta att förstå.</span><span class="sxs-lookup"><span data-stu-id="243b8-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="243b8-184">Därför kan GUIX-utvecklare snabbt använda sina avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="243b8-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="243b8-185">Förbättra tiden till marknaden</span><span class="sxs-lookup"><span data-stu-id="243b8-185">Improve Time to Market</span></span>

<span data-ttu-id="243b8-186">De kraftfulla funktionerna i GUIX påskyndar program utvecklings processen.</span><span class="sxs-lookup"><span data-stu-id="243b8-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="243b8-187">GUIX sammanfattar de flesta processor problem och visar maskin varu problem och tar därmed bort dessa problem från en majoritet av program användar gränssnittets implementering.</span><span class="sxs-lookup"><span data-stu-id="243b8-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="243b8-188">Den här funktionen, tillsammans med funktionen för enkel användning och avancerad funktion, resulterar i en snabbare tid till marknaden!</span><span class="sxs-lookup"><span data-stu-id="243b8-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="243b8-189">Skydda program investeringen</span><span class="sxs-lookup"><span data-stu-id="243b8-189">Protecting the Software Investment</span></span>

<span data-ttu-id="243b8-190">GUIX skrivs exklusivt i ANSI C och är helt integrerad med Azure återställnings tider-ThreadX operativ systemet i real tid.</span><span class="sxs-lookup"><span data-stu-id="243b8-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="243b8-191">Det innebär att GUIX-program är direkt bärbara till alla ThreadX-processorer som stöds.</span><span class="sxs-lookup"><span data-stu-id="243b8-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="243b8-192">Ännu bättre kan en helt ny processor arkitektur stödjas med ThreadX på bara några veckor.</span><span class="sxs-lookup"><span data-stu-id="243b8-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="243b8-193">Det innebär att du kan använda GUIX för att säkerställa programmets migrations Sök väg och skyddar den ursprungliga utvecklings investeringen.</span><span class="sxs-lookup"><span data-stu-id="243b8-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
