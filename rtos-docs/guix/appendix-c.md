---
title: Bilaga C – GUIX widgets format
description: Lär dig mer om widgets formaten i GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827279"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="64505-103">Bilaga C – GUIX widgets format</span><span class="sxs-lookup"><span data-stu-id="64505-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="64505-104">__***Allmänna format (används med de flesta typer av widgetar):***__</span><span class="sxs-lookup"><span data-stu-id="64505-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="64505-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="64505-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="64505-106">Värde: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="64505-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="64505-107">Beskrivning: Använd det här formatet för att rita en widget utan kant linje.</span><span class="sxs-lookup"><span data-stu-id="64505-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="64505-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="64505-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="64505-109">Värde: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="64505-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="64505-110">Beskrivning: Rita widget med en upphöjd kant linje.</span><span class="sxs-lookup"><span data-stu-id="64505-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="64505-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="64505-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="64505-112">Värde: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="64505-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="64505-113">Beskrivning: Rita widget med en försänkt kant linje.</span><span class="sxs-lookup"><span data-stu-id="64505-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="64505-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="64505-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="64505-115">Värde: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="64505-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="64505-116">Beskrivning: Rita en kant linje med en bild punkts bredd.</span><span class="sxs-lookup"><span data-stu-id="64505-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="64505-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="64505-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="64505-118">Värde: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="64505-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="64505-119">Beskrivning: Rita widget med en tjock kant linje.</span><span class="sxs-lookup"><span data-stu-id="64505-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="64505-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="64505-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="64505-121">Värde: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="64505-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="64505-122">Beskrivning: mask värde som används för att bara testa format fälten i widgeten format medlem.</span><span class="sxs-lookup"><span data-stu-id="64505-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="64505-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="64505-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="64505-124">Värde: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="64505-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="64505-125">Beskrivning: skapa en widget som är minst delvis transparent.</span><span class="sxs-lookup"><span data-stu-id="64505-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="64505-126">Det här formatet bör användas när en widget inte ritar helt ogenomskinlig, inklusive widgetar som ritar en halv genomskinlig Pixelmap som widgetens bakgrund.</span><span class="sxs-lookup"><span data-stu-id="64505-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="64505-127">Den här format flaggan informerar GUIX om att widgetens överordnade widget måste ritas för att uppdatera widgetens bakgrunds områden.</span><span class="sxs-lookup"><span data-stu-id="64505-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="64505-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="64505-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="64505-129">Värde: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="64505-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="64505-130">Beskrivning: ange att widgeten ska ritas med valda tillstånds färger och teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="64505-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="64505-131">Olika typer av widgetar använder DRAW_SELECTED format på olika sätt för att indikera att widgeten är markerad.</span><span class="sxs-lookup"><span data-stu-id="64505-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="64505-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="64505-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="64505-133">Värde: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="64505-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="64505-134">Beskrivning: markera widgeten som aktive rad, vilket gör att widgeten kan ta emot indata från användaren och generera utmatnings signaler.</span><span class="sxs-lookup"><span data-stu-id="64505-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="64505-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="64505-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="64505-136">Värde: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="64505-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="64505-137">Beskrivning: anger att widgeten kontroll block minne tilldelas dynamiskt med hjälp av gx_system_memory_allocator tjänsten när widgeten skapas och kontroll Blocks minnet frigörs om widgeten förstörs.</span><span class="sxs-lookup"><span data-stu-id="64505-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="64505-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="64505-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="64505-139">Värde: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="64505-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="64505-140">Beskrivning: instruerar GUIX Drawing Functions att använda det lokala widgeten alpha-värde när widgeten ritas.</span><span class="sxs-lookup"><span data-stu-id="64505-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="64505-141">Den här flaggan används vanligt vis av den interna GUIX-logiken för att implementera tonings-animeringar.</span><span class="sxs-lookup"><span data-stu-id="64505-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="64505-142">__***Format för text justering (format som används för alla widgetar som ritar text):***__</span><span class="sxs-lookup"><span data-stu-id="64505-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="64505-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="64505-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="64505-144">Värde: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="64505-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="64505-145">Beskrivning: texten ritas vänsterjusterat i ett-widgets klient fält.</span><span class="sxs-lookup"><span data-stu-id="64505-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="64505-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="64505-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="64505-147">Värde: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="64505-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="64505-148">Beskrivning: texten ritas högerjusterat i det aktiva widgets-fältet.</span><span class="sxs-lookup"><span data-stu-id="64505-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="64505-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="64505-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="64505-150">Värde: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="64505-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="64505-151">Beskrivning: texten ritas centrerad i widgetens klient del.</span><span class="sxs-lookup"><span data-stu-id="64505-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="64505-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="64505-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="64505-153">Värde: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="64505-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="64505-154">Beskrivning: som standard behåller widgeten som ritar text bara en pekare till den text som skickas av programmet.</span><span class="sxs-lookup"><span data-stu-id="64505-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="64505-155">För statiskt definierad text som definieras i sträng tabellen finns det ingen anledning till att widgeten gör en privat kopia av den tilldelade texten.</span><span class="sxs-lookup"><span data-stu-id="64505-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="64505-156">Men om texten som är kopplad till en widget skapas dynamiskt med funktioner som Sprint () eller gx_utility_ltoa, är det ofta praktiskt att berätta för widgeten att det ska vara en egen privat kopia av en tilldelad text.</span><span class="sxs-lookup"><span data-stu-id="64505-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="64505-157">Detta gör att programmet kan använda automatiska eller tillfälliga variabler när du definierar text strängen, när programmet annars skulle behövas för att definiera statiskt definierade tecken mat ris för varje text-widget som använder dynamiskt definierad text.</span><span class="sxs-lookup"><span data-stu-id="64505-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="64505-158">När den här format flaggan har angetts använder widgeten gx_system_memory_allocator funktionen för att dynamiskt allokera det minnes block som krävs för att lagra en privat kopia av den tilldelade strängen.</span><span class="sxs-lookup"><span data-stu-id="64505-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="64505-159">Därför är det predikat att använda den här format flaggan i programmet som definierar memory_allocator och memory_deallocator funktioner.</span><span class="sxs-lookup"><span data-stu-id="64505-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="64505-160">GX_STYLE_TEXT_COPY ska inte rensas när den har angetts och om du gör det kan det orsaka oförutsägbara resultat.</span><span class="sxs-lookup"><span data-stu-id="64505-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="64505-161">__***Knapp format (gäller endast för widgeten GUIX knapp):***__</span><span class="sxs-lookup"><span data-stu-id="64505-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="64505-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="64505-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="64505-163">Värde 0x00000010</span><span class="sxs-lookup"><span data-stu-id="64505-163">Value 0x00000010</span></span>
  - <span data-ttu-id="64505-164">Beskrivning: anger att knappen är i läget pushd eller markerad.</span><span class="sxs-lookup"><span data-stu-id="64505-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="64505-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="64505-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="64505-166">Värde 0x00000020</span><span class="sxs-lookup"><span data-stu-id="64505-166">Value 0x00000020</span></span>
  - <span data-ttu-id="64505-167">Beskrivning: knappen växlar status mellan pushd och pushd vid varje klickning-händelse.</span><span class="sxs-lookup"><span data-stu-id="64505-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="64505-168">Det här formatet används ofta med knapparna "kryss ruta".</span><span class="sxs-lookup"><span data-stu-id="64505-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="64505-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="64505-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="64505-170">Värde 0x00000040</span><span class="sxs-lookup"><span data-stu-id="64505-170">Value 0x00000040</span></span>
  - <span data-ttu-id="64505-171">Beskrivning: det här formatet anger att knappen är exkluderad och avmarkerar alla knappar på samma nivå när de är markerade.</span><span class="sxs-lookup"><span data-stu-id="64505-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="64505-172">Det här formatet används ofta med format knapparna "alternativ knapp".</span><span class="sxs-lookup"><span data-stu-id="64505-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="64505-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="64505-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="64505-174">Värde: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="64505-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="64505-175">Beskrivning: anger att knappen genererar en klick händelse när den skickas från början.</span><span class="sxs-lookup"><span data-stu-id="64505-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="64505-176">Standard åtgärden är att generera en klicknings händelse när knappen släpps.</span><span class="sxs-lookup"><span data-stu-id="64505-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="64505-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="64505-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="64505-178">Värde 0x00000100</span><span class="sxs-lookup"><span data-stu-id="64505-178">Value 0x00000100</span></span>
  - <span data-ttu-id="64505-179">Beskrivning: anger att knappen ska skicka upprepade klicknings händelser till knappen överordnad när knappen hålls i läget PUSHD.</span><span class="sxs-lookup"><span data-stu-id="64505-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="64505-180">__***List format (gäller endast för GUIX List widgetar typer):***__</span><span class="sxs-lookup"><span data-stu-id="64505-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="64505-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="64505-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="64505-182">Värde: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="64505-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="64505-183">Beskrivning: reserverad</span><span class="sxs-lookup"><span data-stu-id="64505-183">Description: Reserved</span></span>

<span data-ttu-id="64505-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="64505-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="64505-185">Värde 0x00000020</span><span class="sxs-lookup"><span data-stu-id="64505-185">Value 0x00000020</span></span>
  - <span data-ttu-id="64505-186">Beskrivning: listan underordnade visas från början till slut när listan dras eller rullas förbi början eller slutet av list indexet.</span><span class="sxs-lookup"><span data-stu-id="64505-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="64505-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="64505-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="64505-188">Värde: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="64505-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="64505-189">Beskrivning: reserverad</span><span class="sxs-lookup"><span data-stu-id="64505-189">Description: Reserved</span></span>

<span data-ttu-id="64505-190">__***Pixelmap-knapp och knapp format för ikon:***__</span><span class="sxs-lookup"><span data-stu-id="64505-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="64505-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="64505-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="64505-192">Värde: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="64505-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="64505-193">Beskrivning: knappens Pixelmap ska centreras i den vågräta axelns knapp gränser.</span><span class="sxs-lookup"><span data-stu-id="64505-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="64505-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="64505-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="64505-195">Värde: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="64505-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="64505-196">Beskrivning: knappens Pixelmap ska vara vänsterjusterad inom den vågräta axelns knapp gränser.</span><span class="sxs-lookup"><span data-stu-id="64505-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="64505-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="64505-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="64505-198">Värde 0x00040000</span><span class="sxs-lookup"><span data-stu-id="64505-198">Value 0x00040000</span></span>
  - <span data-ttu-id="64505-199">Beskrivning: knappens Pixelmap ska vara högerjusterad inom den vågräta axelns knapp gränser.</span><span class="sxs-lookup"><span data-stu-id="64505-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="64505-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="64505-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="64505-201">Värde 0x00080000</span><span class="sxs-lookup"><span data-stu-id="64505-201">Value 0x00080000</span></span>
  - <span data-ttu-id="64505-202">Beskrivning: knappens Pixelmap ska vara centrerad inom knapp kanten på den lodräta axeln.</span><span class="sxs-lookup"><span data-stu-id="64505-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="64505-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="64505-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="64505-204">Värde: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="64505-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="64505-205">Beskrivning: knappens Pixelmap ska justeras mot överkant i den lodräta axelns knapp gränser.</span><span class="sxs-lookup"><span data-stu-id="64505-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="64505-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="64505-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="64505-207">Värde: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="64505-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="64505-208">Beskrivning: knappens Pixelmap ska ligga längst ned i knapp kanten på den lodräta vågräta axeln.</span><span class="sxs-lookup"><span data-stu-id="64505-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="64505-209">__***Skjutreglage (endast appy till GX_SLIDER och härledda typer av widgetar):***__</span><span class="sxs-lookup"><span data-stu-id="64505-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="64505-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="64505-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="64505-211">Värde: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="64505-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="64505-212">Beskrivning: det här formatet måste ingå i skjutreglaget för att rita en nål.</span><span class="sxs-lookup"><span data-stu-id="64505-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="64505-213">Det här formatet kan inaktive ras om programmet vill inaktivera skjutreglaget eller rita en anpassad nål.</span><span class="sxs-lookup"><span data-stu-id="64505-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="64505-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="64505-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="64505-215">Värde: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="64505-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="64505-216">Beskrivning: widgeten skjutreglage kommer att göra program ritning av streckade skal streck linjer när det här formatet är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="64505-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="64505-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="64505-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="64505-218">Värde 0x00000800</span><span class="sxs-lookup"><span data-stu-id="64505-218">Value 0x00000800</span></span>
  - <span data-ttu-id="64505-219">Beskrivning: Ange den här format flaggan för att skapa ett lodrätt skjutreglage och ta bort den här format flaggan om du vill skapa ett vågrätt skjutreglage.</span><span class="sxs-lookup"><span data-stu-id="64505-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="64505-220">__***Sprite-format (gäller endast för GX_SPRITE widgetar typer):***__</span><span class="sxs-lookup"><span data-stu-id="64505-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="64505-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="64505-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="64505-222">Värde: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="64505-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="64505-223">Beskrivning: anger att Sprite-animeringen ska köras automatiskt när widgeten Sprite mottagit GX_EVENT_SHOW-händelsen.</span><span class="sxs-lookup"><span data-stu-id="64505-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="64505-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="64505-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="64505-225">Värde: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="64505-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="64505-226">Beskrivning: med det här formatet kommer widgeten Sprite att upprepas genom Sprite-animeringsbildrutor tills spriten stoppas av programmet.</span><span class="sxs-lookup"><span data-stu-id="64505-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="64505-227">__***Pixelmap för skjutreglage:***__</span><span class="sxs-lookup"><span data-stu-id="64505-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="64505-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="64505-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="64505-229">Värde 0x00001000</span><span class="sxs-lookup"><span data-stu-id="64505-229">Value 0x00001000</span></span>
  - <span data-ttu-id="64505-230">Beskrivning: skjutreglagets bakgrunds bild visas sida vid sida för att fylla den sprite-rektangeln.</span><span class="sxs-lookup"><span data-stu-id="64505-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="64505-231">Detta gör att en liten lodrät eller vågrät rand bild kan användas för att fylla skjutreglagets bakgrund.</span><span class="sxs-lookup"><span data-stu-id="64505-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="64505-232">__***Ytterligare förlopps indikator format:***__</span><span class="sxs-lookup"><span data-stu-id="64505-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="64505-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="64505-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="64505-234">Värde: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="64505-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="64505-235">Beskrivning: när det här formatet anges ritas stapelns värde som en procent andel i stället för ett oformaterat värde.</span><span class="sxs-lookup"><span data-stu-id="64505-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="64505-236">Texten centreras i den förlopps indikatorns rektangel.</span><span class="sxs-lookup"><span data-stu-id="64505-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="64505-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="64505-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="64505-238">Värde: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="64505-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="64505-239">Beskrivning: Rita aktuellt förlopps indikator värde som decimal text centrerad i förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="64505-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="64505-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="64505-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="64505-241">Värde: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="64505-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="64505-242">Beskrivning: anger att förloppet är lodrätt orienterad.</span><span class="sxs-lookup"><span data-stu-id="64505-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="64505-243">Standardvärdet är vågrät orientering.</span><span class="sxs-lookup"><span data-stu-id="64505-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="64505-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span><span class="sxs-lookup"><span data-stu-id="64505-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="64505-245">**Värde**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="64505-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="64505-246">Beskrivning: förlopps indikatorns värde anges med segmenterade fyllda rektanglar i stället för en solid fyllning.</span><span class="sxs-lookup"><span data-stu-id="64505-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="64505-247">__***Fler format för radiell förlopps indikator:***__</span><span class="sxs-lookup"><span data-stu-id="64505-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="64505-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="64505-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="64505-249">Värde: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="64505-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="64505-250">Beskrivning: Rita den radiella förlopps indikatorn med hjälp av färgmarkerade pensel format.</span><span class="sxs-lookup"><span data-stu-id="64505-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="64505-251">Detta kräver mer processor bandbredd men ger också ett nicer utseende.</span><span class="sxs-lookup"><span data-stu-id="64505-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="64505-252">Om du tar bort den här typen av processor mål ger det snabbare ritnings hastighet.</span><span class="sxs-lookup"><span data-stu-id="64505-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="64505-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="64505-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="64505-254">Värde: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="64505-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="64505-255">Beskrivning: Använd en rundad linje slut pensel stil när du ritar den radiella förlopps indikatorns båge. Standardvärdet är en fyrkantig linje slutar.</span><span class="sxs-lookup"><span data-stu-id="64505-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="64505-256">__***Ytterligare text ingångs format:***__</span><span class="sxs-lookup"><span data-stu-id="64505-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="64505-257">**GX_STYLE_ CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="64505-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="64505-258">Värde: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="64505-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="64505-259">Beskrivning: markören för text inmatade widgeten blinkar i stället för att vara konstant.</span><span class="sxs-lookup"><span data-stu-id="64505-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="64505-260">**GX_STYLE_ CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="64505-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="64505-261">Värde: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="64505-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="64505-262">Beskrivning.</span><span class="sxs-lookup"><span data-stu-id="64505-262">Description.</span></span> <span data-ttu-id="64505-263">Markören för text inmatade widget visas vanligt vis bara när widgeten äger indatamängds fokus.</span><span class="sxs-lookup"><span data-stu-id="64505-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="64505-264">Den här format flaggan gör att markören alltid är synlig oavsett infokus.</span><span class="sxs-lookup"><span data-stu-id="64505-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="64505-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="64505-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="64505-266">Värde: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="64505-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="64505-267">Beskrivning: med den här format flaggan anger händelsen GX_EVENT_TEXT_EDITED händelse varje gång en nyckel händelsen tas emot av widgeten för text inflöde.</span><span class="sxs-lookup"><span data-stu-id="64505-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="64505-268">__***Ytterligare fönster format:***__</span><span class="sxs-lookup"><span data-stu-id="64505-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="64505-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="64505-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="64505-270">Värde: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="64505-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="64505-271">Beskrivning: fönstret visas med en tilldelad bakgrunds bild för att fylla fönstrets klient-rektangel.</span><span class="sxs-lookup"><span data-stu-id="64505-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="64505-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="64505-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="64505-273">Värde: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="64505-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="64505-274">Beskrivning: reserverad för framtida användning.</span><span class="sxs-lookup"><span data-stu-id="64505-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="64505-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="64505-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="64505-276">Värde: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="64505-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="64505-277">Beskrivning: reserverad för framtida användning.</span><span class="sxs-lookup"><span data-stu-id="64505-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="64505-278">__***Ytterligare meny format:***__</span><span class="sxs-lookup"><span data-stu-id="64505-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="64505-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="64505-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="64505-280">Värde: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="64505-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="64505-281">Beskrivning: widgeten för dragspelswidget är inlednings vis i expanderat läge.</span><span class="sxs-lookup"><span data-stu-id="64505-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="64505-282">__***Ytterligare träd format:***__</span><span class="sxs-lookup"><span data-stu-id="64505-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="64505-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="64505-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="64505-284">Värde: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="64505-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="64505-285">Beskrivning: trädvyn i trädvyn ska rita rader från Node-ikonen till rotnoden.</span><span class="sxs-lookup"><span data-stu-id="64505-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="64505-286">__***Ytterligare rullnings List format:***__</span><span class="sxs-lookup"><span data-stu-id="64505-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="64505-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="64505-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="64505-288">Värde: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="64505-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="64505-289">Beskrivning: reserverad för framtida användning.</span><span class="sxs-lookup"><span data-stu-id="64505-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="64505-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="64505-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="64505-291">Värde: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="64505-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="64505-292">Beskrivning: rullnings listens bredd (för en vågrät rullnings List) eller höjd (för en lodrät rullnings List) beräknas baserat på förhållandet för det synliga området i det överordnade fönstret till det minsta och högsta rullnings intervallet.</span><span class="sxs-lookup"><span data-stu-id="64505-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="64505-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="64505-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="64505-294">Värde: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="64505-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="64505-295">Beskrivning: rullnings listen skapar och lägger automatiskt till knappar i slutet av området rullnings List.</span><span class="sxs-lookup"><span data-stu-id="64505-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="64505-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="64505-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="64505-297">Värde: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="64505-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="64505-298">Beskrivning: rullnings listen är lodrätt orienterad.</span><span class="sxs-lookup"><span data-stu-id="64505-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="64505-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="64505-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="64505-300">Värde: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="64505-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="64505-301">Beskrivning: rullnings listen är vågrätt orienterad.</span><span class="sxs-lookup"><span data-stu-id="64505-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="64505-302">__***Hjul format för text rullning:***__</span><span class="sxs-lookup"><span data-stu-id="64505-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="64505-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="64505-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="64505-304">Värde: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="64505-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="64505-305">Beskrivning: rullnings hjulet använder en Sinusoidal-algoritm som gör att rullnings hjulet visas med en rundad form.</span><span class="sxs-lookup"><span data-stu-id="64505-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="64505-306">Den här format flaggan kan förbättra prestandan för widgeten rullnings hjul, men det kan också ge hjulet ett 3D realistiskt utseende.</span><span class="sxs-lookup"><span data-stu-id="64505-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>