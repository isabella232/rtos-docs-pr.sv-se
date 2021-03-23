---
title: Bilaga D – GUIX pensel, attribut för arbets yta och toning
description: Lär dig mer om GUIX-penseln, arbetsytans och Toningens attribut.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827276"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="72935-103">Bilaga D – GUIX pensel, attribut för arbets yta och toning</span><span class="sxs-lookup"><span data-stu-id="72935-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="72935-104">__**Pensel format:**__</span><span class="sxs-lookup"><span data-stu-id="72935-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="72935-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="72935-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="72935-106">Värde: 0x0000</span><span class="sxs-lookup"><span data-stu-id="72935-106">Value: 0x0000</span></span>
- <span data-ttu-id="72935-107">Beskrivning: det här pensel formatet gäller för form ritnings funktioner som gx_canvas_rectangle_draw eller gx_canvas_polygon_draw.</span><span class="sxs-lookup"><span data-stu-id="72935-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="72935-108">Det här formatet visar att figuren ska vara definierad, förutom att du kan fylla.</span><span class="sxs-lookup"><span data-stu-id="72935-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="72935-109">Om GX_BRUSH_OUTLINE-formatet har angetts och GX_BRSUH_SOLID_FILL är avmarkerat visas figuren bara.</span><span class="sxs-lookup"><span data-stu-id="72935-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="72935-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="72935-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="72935-111">Värde: 0x0001</span><span class="sxs-lookup"><span data-stu-id="72935-111">Value: 0x0001</span></span>
- <span data-ttu-id="72935-112">Beskrivning: det här pensel formatet används för form ritnings funktioner och anger att den begärda formen ska fyllas med en solid färg med den aktuella pensel fyllnings färgen.</span><span class="sxs-lookup"><span data-stu-id="72935-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="72935-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="72935-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="72935-114">Värde: 0x0002</span><span class="sxs-lookup"><span data-stu-id="72935-114">Value: 0x0002</span></span>
- <span data-ttu-id="72935-115">Beskrivning: det här pensel formatet används för form ritnings funktioner och anger att den önskade formen ska vara ett mönster som är ifyllt med den aktuella penseln Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="72935-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="72935-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="72935-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="72935-117">Värde: 0x0004</span><span class="sxs-lookup"><span data-stu-id="72935-117">Value: 0x0004</span></span>
- <span data-ttu-id="72935-118">Beskrivning: det här pensel formatet gäller för alla linje rit-och form konturer.</span><span class="sxs-lookup"><span data-stu-id="72935-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="72935-119">Om den här flaggan är inställd, ritas linjer och kant linjer med mer exakt, men även mer tid på att använda algoritmer för kant utjämning.</span><span class="sxs-lookup"><span data-stu-id="72935-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="72935-120">Den här format flaggan används bara för 16-BPP färgdjup och högre.</span><span class="sxs-lookup"><span data-stu-id="72935-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="72935-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="72935-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="72935-122">Värde: 0x0008</span><span class="sxs-lookup"><span data-stu-id="72935-122">Value: 0x0008</span></span>
- <span data-ttu-id="72935-123">Beskrivning: den här flaggan gäller för text ritning och anger att efterföljande text som ritas ska vara understruken.</span><span class="sxs-lookup"><span data-stu-id="72935-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="72935-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="72935-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="72935-125">Värde: 0x0010</span><span class="sxs-lookup"><span data-stu-id="72935-125">Value: 0x0010</span></span>
- <span data-ttu-id="72935-126">Beskrivning: den här flaggan gäller för linje ritning och anger att linje änd punkter ritas med en runda eller cirkulär form, i stället för standardformen.</span><span class="sxs-lookup"><span data-stu-id="72935-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="72935-127">__**Flaggor för arbets ytor:**__</span><span class="sxs-lookup"><span data-stu-id="72935-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="72935-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="72935-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="72935-129">Värde: 0x01</span><span class="sxs-lookup"><span data-stu-id="72935-129">Value: 0x01</span></span>
- <span data-ttu-id="72935-130">Beskrivning: en minnes arbets yta som används för att rita på skärmen.</span><span class="sxs-lookup"><span data-stu-id="72935-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="72935-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="72935-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="72935-132">Värde: protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="72935-132">Value: 0x02</span></span>
- <span data-ttu-id="72935-133">Beskrivning: en arbets yta som automatiskt töms på den aktiva visningen, antingen som en del av den sammansatta skapande processen eller som en del av växlings åtgärden för en enskild arbets yta.</span><span class="sxs-lookup"><span data-stu-id="72935-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="72935-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="72935-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="72935-135">Värde: 0x04</span><span class="sxs-lookup"><span data-stu-id="72935-135">Value: 0x04</span></span>
- <span data-ttu-id="72935-136">Beskrivning: den här flaggan kan användas för att aktivera och inaktivera en arbets yta utan att förlora ritnings innehållet i arbets ytan.</span><span class="sxs-lookup"><span data-stu-id="72935-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="72935-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="72935-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="72935-138">Värde: 0x08</span><span class="sxs-lookup"><span data-stu-id="72935-138">Value: 0x08</span></span>
- <span data-ttu-id="72935-139">Beskrivning: reserverad för framtida användning.</span><span class="sxs-lookup"><span data-stu-id="72935-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="72935-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="72935-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="72935-141">Värde: 0x20</span><span class="sxs-lookup"><span data-stu-id="72935-141">Value: 0x20</span></span>
- <span data-ttu-id="72935-142">Beskrivning: den här flaggan används av programmet när du konfigurerar ett system med flera arbets ytor som sammansätter flera hanterade arbets ytor i den sammansatta arbets ytan och den sammansatta enheten är driven för maskin varu Rams bufferten.</span><span class="sxs-lookup"><span data-stu-id="72935-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="72935-143">__**Tonings typer:**__</span><span class="sxs-lookup"><span data-stu-id="72935-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="72935-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="72935-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="72935-145">Värde: 0x01</span><span class="sxs-lookup"><span data-stu-id="72935-145">Value: 0x01</span></span>
- <span data-ttu-id="72935-146">Beskrivning: skapar en lodrät AlphaMap-övertoning.</span><span class="sxs-lookup"><span data-stu-id="72935-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="72935-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="72935-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="72935-148">Värde: protokollnumret 0x02</span><span class="sxs-lookup"><span data-stu-id="72935-148">Value: 0x02</span></span>
- <span data-ttu-id="72935-149">Beskrivning: utformerar en tonings toning i alpha-mappar.</span><span class="sxs-lookup"><span data-stu-id="72935-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="72935-150">Detta är för närvarande det enda stödda tonings formatet.</span><span class="sxs-lookup"><span data-stu-id="72935-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="72935-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="72935-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="72935-152">Värde: 0x04</span><span class="sxs-lookup"><span data-stu-id="72935-152">Value: 0x04</span></span>
- <span data-ttu-id="72935-153">Beskrivning: den här flaggan anger att toningen ska vara hög vid mitten av intervallet för bredd/höjd och återgå till startvärdet när den når höger/nedre kant.</span><span class="sxs-lookup"><span data-stu-id="72935-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="72935-154">Utan den här format flaggan är övertoningen en linjär övertoning från översta till nedre eller från vänster till höger, beroende på GX_GRADIENT_TYPE_VERTICAL flagga.</span><span class="sxs-lookup"><span data-stu-id="72935-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>