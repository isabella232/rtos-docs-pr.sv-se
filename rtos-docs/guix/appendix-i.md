---
title: Bilaga I – GUIX informations strukturer
description: Lär dig mer om informations strukturer i GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827210"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="ab04a-103">Bilaga I – GUIX informations strukturer</span><span class="sxs-lookup"><span data-stu-id="ab04a-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="ab04a-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-105">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-106">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="ab04a-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="ab04a-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="ab04a-108">Text för att ordna om</span><span class="sxs-lookup"><span data-stu-id="ab04a-108">Text for reordering</span></span> |
| <span data-ttu-id="ab04a-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="ab04a-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="ab04a-110">Teckensnitt som används för att visa text, ange det som GX_NULL om rad brytning inte behövs</span><span class="sxs-lookup"><span data-stu-id="ab04a-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="ab04a-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="ab04a-112">Tillgänglig bredd för visning, Ställ in den på-1 om rad brytning inte behövs</span><span class="sxs-lookup"><span data-stu-id="ab04a-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="ab04a-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-114">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-115">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="ab04a-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="ab04a-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="ab04a-117">Pekare till matrisen med omordningen dubbelriktad text</span><span class="sxs-lookup"><span data-stu-id="ab04a-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="ab04a-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="ab04a-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="ab04a-119">Totalt antal rader matchad dubbelriktad text för ett stycke</span><span class="sxs-lookup"><span data-stu-id="ab04a-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="ab04a-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="ab04a-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="ab04a-121">Dubbelriktad dubbelriktad text information för nästa stycke</span><span class="sxs-lookup"><span data-stu-id="ab04a-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="ab04a-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="ab04a-123">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-123">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```
### <a name="members"></a><span data-ttu-id="ab04a-124">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="ab04a-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="ab04a-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="ab04a-126">Totalt antal steg som nål färdas genom att flytta från den aktuella nålventil till en nyligen tilldelad bänk</span><span class="sxs-lookup"><span data-stu-id="ab04a-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="ab04a-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="ab04a-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="ab04a-128">Antalet GUIX klock Tick som ska förskjutas mellan animeringssekvenser</span><span class="sxs-lookup"><span data-stu-id="ab04a-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="ab04a-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="ab04a-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="ab04a-130">Avståndet från vänster om mätar widgeten till rotations punkten för mätarens Barr</span><span class="sxs-lookup"><span data-stu-id="ab04a-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="ab04a-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="ab04a-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="ab04a-132">Avståndet från överkanten i mätar widgeten till rotations punkten för mätarens Barr</span><span class="sxs-lookup"><span data-stu-id="ab04a-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="ab04a-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="ab04a-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="ab04a-134">Avståndet från den högra delen av nålventil till rotations punkten för mätarens Barr</span><span class="sxs-lookup"><span data-stu-id="ab04a-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="ab04a-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="ab04a-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="ab04a-136">Avståndet från den översta delen av nålventil till rotations punkten för mätarens Barr</span><span class="sxs-lookup"><span data-stu-id="ab04a-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="ab04a-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="ab04a-138">Resurs-ID för Pixelmap som ska användas för att rita mätar nål.</span><span class="sxs-lookup"><span data-stu-id="ab04a-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="ab04a-139">Den här bilden roteras efter behov av mätar widgeten för att Visa mätarens barr i valfri position</span><span class="sxs-lookup"><span data-stu-id="ab04a-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="ab04a-140">Diagrammet nedan illustrerar Xpos, ypos och XCOR, ycor koordinater:</span><span class="sxs-lookup"><span data-stu-id="ab04a-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Diagram över koordinaterna för nål Y och X](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="ab04a-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="ab04a-143">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-143">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-144">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="ab04a-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="ab04a-146">Det minsta data värde som används för att beräkna skalning</span><span class="sxs-lookup"><span data-stu-id="ab04a-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="ab04a-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="ab04a-148">Maximalt data värde, som används för att beräkna skalning</span><span class="sxs-lookup"><span data-stu-id="ab04a-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="ab04a-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="ab04a-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="ab04a-150">Pekar mot en matris med heltals värden.</span><span class="sxs-lookup"><span data-stu-id="ab04a-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="ab04a-151">Detta är de heltals värden som ritas av linje diagrammets widget</span><span class="sxs-lookup"><span data-stu-id="ab04a-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="ab04a-152">**gx_line_ <side> _margin**</span><span class="sxs-lookup"><span data-stu-id="ab04a-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="ab04a-153">Förskjutningen från diagram fönstret som är yttre till det faktiska diagrammets åter givnings område.</span><span class="sxs-lookup"><span data-stu-id="ab04a-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="ab04a-154">Diagrammets axel och data linje ritas alltid inom den här inre gränsen, vilket gör att programmet kan rita etiketter och annan information i diagram fönstret, men utanför diagrammets diagram område</span><span class="sxs-lookup"><span data-stu-id="ab04a-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="ab04a-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="ab04a-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="ab04a-156">Antalet data värden som kan finnas.</span><span class="sxs-lookup"><span data-stu-id="ab04a-156">The number of data values which may be present.</span></span> <span data-ttu-id="ab04a-157">Den här parametern används för att beräkna skalningen på x-axeln eller intervall för att rita data punkter.</span><span class="sxs-lookup"><span data-stu-id="ab04a-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="ab04a-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="ab04a-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="ab04a-159">Antalet data värden som faktiskt finns i data matrisen.</span><span class="sxs-lookup"><span data-stu-id="ab04a-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="ab04a-160">Ett linje diagram kan skalas för att rita högst 100 värden (till exempel), men för en viss uppdatering kan det faktiskt finnas ett mindre antal data värden.</span><span class="sxs-lookup"><span data-stu-id="ab04a-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="ab04a-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="ab04a-162">Bredd på linjen som används för att rita den vågräta och lodräta axeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="ab04a-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="ab04a-164">Bredd på den ritade data linjen</span><span class="sxs-lookup"><span data-stu-id="ab04a-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="ab04a-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="ab04a-166">Resurs-ID för färgen som används för att rita axel linjerna</span><span class="sxs-lookup"><span data-stu-id="ab04a-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="ab04a-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="ab04a-168">Resurs-ID för den färg som används för att rita diagrammets data linje</span><span class="sxs-lookup"><span data-stu-id="ab04a-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="ab04a-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-170">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-171">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="ab04a-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="ab04a-173">Resurs-ID för mus bilden</span><span class="sxs-lookup"><span data-stu-id="ab04a-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="ab04a-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="ab04a-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="ab04a-175">Förskjutningen från vänster om musen till klickbar bild punkt</span><span class="sxs-lookup"><span data-stu-id="ab04a-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="ab04a-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="ab04a-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="ab04a-177">Förskjutningen från bildens överkant till punktens klickbara bild punkt</span><span class="sxs-lookup"><span data-stu-id="ab04a-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="ab04a-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="ab04a-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-179">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="ab04a-180">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="ab04a-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="ab04a-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="ab04a-182">Minsta drag avstånd per GUIX timer för att utlösa ett SNÄRTNING-händelse.</span><span class="sxs-lookup"><span data-stu-id="ab04a-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="ab04a-183">Anropa GX_FIXED_VAL_MAKE för att skapa ett fast punkt värde för data typen</span><span class="sxs-lookup"><span data-stu-id="ab04a-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="ab04a-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="ab04a-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="ab04a-185">Den maximala dra hastigheten i GUIX timer-Tick för att utlösa en SNÄRTNING-händelse</span><span class="sxs-lookup"><span data-stu-id="ab04a-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="ab04a-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-187">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-188">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="ab04a-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="ab04a-190">Resurs-ID för Pixelmap som fyller bakgrunden före nål.</span><span class="sxs-lookup"><span data-stu-id="ab04a-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="ab04a-191">Om den övre bakgrunds Pixelmap inte har angetts används den för att fylla bakgrunden både före och efter nål</span><span class="sxs-lookup"><span data-stu-id="ab04a-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="ab04a-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="ab04a-193">Resurs-ID för Pixelmap som fyller bakgrunden efter nål</span><span class="sxs-lookup"><span data-stu-id="ab04a-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="ab04a-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="ab04a-195">Resurs-ID för nålventil Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ab04a-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="ab04a-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-197">**Definition**</span><span class="sxs-lookup"><span data-stu-id="ab04a-197">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-198">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="ab04a-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="ab04a-200">Lägsta rapporterade värde</span><span class="sxs-lookup"><span data-stu-id="ab04a-200">Minimum reported value</span></span> |
| <span data-ttu-id="ab04a-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="ab04a-202">Maximalt rapporterat värde</span><span class="sxs-lookup"><span data-stu-id="ab04a-202">Maximum reported value</span></span> |
| <span data-ttu-id="ab04a-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="ab04a-204">Aktuellt värde</span><span class="sxs-lookup"><span data-stu-id="ab04a-204">Current value</span></span> |
| <span data-ttu-id="ab04a-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="ab04a-206">Resurs-ID för teckensnittet som används för att rita det valfria text värdet i widgeten förlopps indikator</span><span class="sxs-lookup"><span data-stu-id="ab04a-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="ab04a-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="ab04a-208">Resurs-ID för text färgen i läget normal som används för att definiera den valfria text ritningen i widgeten förlopps indikator</span><span class="sxs-lookup"><span data-stu-id="ab04a-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="ab04a-210">Resurs-ID för textfärg när widgeten får fokus, används för att definiera valfri text ritning i förlopps indikatorns widget</span><span class="sxs-lookup"><span data-stu-id="ab04a-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="ab04a-212">Resurs-ID för text färgen när GX_STYLE_ENABLED inte är aktiv, används för att definiera den valfria text ritningen i widgeten för förlopps indikatorn</span><span class="sxs-lookup"><span data-stu-id="ab04a-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="ab04a-214">Resurs-ID för Pixelmap för bakgrunds fyllning</span><span class="sxs-lookup"><span data-stu-id="ab04a-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="ab04a-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="ab04a-216">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-216">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-217">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="ab04a-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="ab04a-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="ab04a-219">Widgetens position i x-koordinaten</span><span class="sxs-lookup"><span data-stu-id="ab04a-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="ab04a-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="ab04a-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="ab04a-221">Widgetens position i y-koordinaten</span><span class="sxs-lookup"><span data-stu-id="ab04a-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="ab04a-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="ab04a-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="ab04a-223">Radien för förlopps cirkeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="ab04a-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="ab04a-225">Aktuellt värde, begränsat till intervallet [-360, 360], anger vinkeln delta mellan ankar positionen och slut punkten för den övre bågen. Negativt värde gör att bågen ritas i en medsols riktning som börjar vid ankar positionen.</span><span class="sxs-lookup"><span data-stu-id="ab04a-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="ab04a-226">Positivt värde gör att bågen ritas in i riktningen medurs med början vid ankar positionen.</span><span class="sxs-lookup"><span data-stu-id="ab04a-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="ab04a-227">Programmet måste skala det verkliga ord svärdet som anges för att tilldela ett vinkel värde till widgeten för förlopps indikatorn</span><span class="sxs-lookup"><span data-stu-id="ab04a-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="ab04a-229">Start vinkeln för den övre förlopps bågen. Värdet definieras som en heltals grad med 0 grader peka på höger och 90 grad som visar en rak position.</span><span class="sxs-lookup"><span data-stu-id="ab04a-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="ab04a-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="ab04a-231">Resurs-ID för det teckensnitt som används för att rita det valfria text värdet i widgeten förlopps indikator</span><span class="sxs-lookup"><span data-stu-id="ab04a-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="ab04a-233">Resurs-ID för text färgen i läget normal som används för att definiera den valfria text ritningen i widgeten förlopps indikator</span><span class="sxs-lookup"><span data-stu-id="ab04a-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="ab04a-235">Resurs-ID för text färgen när widgeten får fokus, används för att definiera valfri text ritning i förlopps indikatorns widget</span><span class="sxs-lookup"><span data-stu-id="ab04a-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="ab04a-237">Resurs-ID för text färgen när GX_STYLE_ENABLED inte är aktiv, används för att definiera den valfria text ritningen i widgeten för förlopps indikatorn</span><span class="sxs-lookup"><span data-stu-id="ab04a-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="ab04a-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="ab04a-239">Bredden på den nedre förlopps cirkeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="ab04a-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="ab04a-241">Bredden för den övre förloppet, den övre bågen kan vara smalare, samma som eller bredare än den nedre cirkeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="ab04a-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="ab04a-243">Resurs-ID för färgen som ska fyllas i lägre förlopps cirkel</span><span class="sxs-lookup"><span data-stu-id="ab04a-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="ab04a-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="ab04a-245">Resurs-ID för färgen som fyller mot den övre förloppet för en båge</span><span class="sxs-lookup"><span data-stu-id="ab04a-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="ab04a-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-247">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-247">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-248">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="ab04a-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="ab04a-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="ab04a-250">Avstånd från vänster om skjutreglagets widget till rotations punkten för skjutreglaget</span><span class="sxs-lookup"><span data-stu-id="ab04a-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="ab04a-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="ab04a-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="ab04a-252">Avstånd från skjutreglagets överkant till rotations punkten för skjutreglaget</span><span class="sxs-lookup"><span data-stu-id="ab04a-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="ab04a-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="ab04a-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="ab04a-254">Radien för den radiella skjutreglaget cirkel</span><span class="sxs-lookup"><span data-stu-id="ab04a-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="ab04a-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="ab04a-256">Bredd på radiellt Slider-spår</span><span class="sxs-lookup"><span data-stu-id="ab04a-256">Width of radial slider track</span></span> |
| <span data-ttu-id="ab04a-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="ab04a-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="ab04a-258">Aktuell vinkel för skjutreglage</span><span class="sxs-lookup"><span data-stu-id="ab04a-258">Current slider angle</span></span> |
| <span data-ttu-id="ab04a-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="ab04a-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="ab04a-260">Minsta skjutreglagets vinkel</span><span class="sxs-lookup"><span data-stu-id="ab04a-260">Minimum slider angle</span></span> |
| <span data-ttu-id="ab04a-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="ab04a-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="ab04a-262">Maximal skjutreglages vinkel</span><span class="sxs-lookup"><span data-stu-id="ab04a-262">Maximum slider angle</span></span> |
| <span data-ttu-id="ab04a-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="ab04a-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="ab04a-264">Vinkel värde lista, definierar fäst vinklar, om det är inställt, kan skjutreglagets vinkel bara vara en av de definierade ankar vinklarna</span><span class="sxs-lookup"><span data-stu-id="ab04a-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="ab04a-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="ab04a-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="ab04a-266">Antal ankar vinklar</span><span class="sxs-lookup"><span data-stu-id="ab04a-266">Number of anchor angles</span></span> |
| <span data-ttu-id="ab04a-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="ab04a-268">Resurs-ID för bakgrunds Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ab04a-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="ab04a-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="ab04a-270">Resurs-ID för barr Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ab04a-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="ab04a-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="ab04a-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="ab04a-272">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="ab04a-273">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="ab04a-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="ab04a-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="ab04a-275">Vänster om rektangeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="ab04a-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="ab04a-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="ab04a-277">Övre delen av rektangeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="ab04a-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="ab04a-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="ab04a-279">Rektangelns högerkant</span><span class="sxs-lookup"><span data-stu-id="ab04a-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="ab04a-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="ab04a-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="ab04a-281">Längst ned i rektangeln</span><span class="sxs-lookup"><span data-stu-id="ab04a-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="ab04a-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="ab04a-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-283">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="ab04a-284">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="ab04a-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="ab04a-286">Resurs-ID för normalt text teckensnitt</span><span class="sxs-lookup"><span data-stu-id="ab04a-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="ab04a-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="ab04a-288">Resurs-ID med fet text teckensnitt</span><span class="sxs-lookup"><span data-stu-id="ab04a-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="ab04a-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="ab04a-290">Resurs-ID för kursivt text teckensnitt</span><span class="sxs-lookup"><span data-stu-id="ab04a-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="ab04a-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="ab04a-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="ab04a-292">Resurs-ID med fet kursiv text teckensnitt</span><span class="sxs-lookup"><span data-stu-id="ab04a-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="ab04a-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="ab04a-294">**Definition**</span><span class="sxs-lookup"><span data-stu-id="ab04a-294">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-295">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="ab04a-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="ab04a-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="ab04a-297">Aktuell rullnings position</span><span class="sxs-lookup"><span data-stu-id="ab04a-297">Current scroll position</span></span>       |
| <span data-ttu-id="ab04a-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="ab04a-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="ab04a-299">Lägsta rapporterade position</span><span class="sxs-lookup"><span data-stu-id="ab04a-299">Minimum reported position</span></span>     |
| <span data-ttu-id="ab04a-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="ab04a-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="ab04a-301">Högsta rapporterade position</span><span class="sxs-lookup"><span data-stu-id="ab04a-301">Maximum reported position</span></span>     |
| <span data-ttu-id="ab04a-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="ab04a-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="ab04a-303">Synligt intervall för överordnad fönster</span><span class="sxs-lookup"><span data-stu-id="ab04a-303">Parent window visible range</span></span>   |
| <span data-ttu-id="ab04a-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="ab04a-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="ab04a-305">Minsta delta värde för rullnings List</span><span class="sxs-lookup"><span data-stu-id="ab04a-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="ab04a-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="ab04a-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="ab04a-307">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-307">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

### <a name="members"></a><span data-ttu-id="ab04a-308">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="ab04a-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="ab04a-310">Bredd på widgeten rullnings List, i bild punkter</span><span class="sxs-lookup"><span data-stu-id="ab04a-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="ab04a-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="ab04a-312">Bredden på knapp tummen som bilder på rullnings listen visas i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="ab04a-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="ab04a-313">Det här värdet är vanligt vis ett antal pixlar som är mindre än den totala rullnings listens bredd</span><span class="sxs-lookup"><span data-stu-id="ab04a-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="ab04a-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="ab04a-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="ab04a-315">Förskjutning från slutet av rullnings listen till den minsta skjutreglaget för knapp resans slut punkt.</span><span class="sxs-lookup"><span data-stu-id="ab04a-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="ab04a-316">Den här gränsen kan användas för att förhindra att knappen för tummen reser till en ytterst ände av rullnings listen</span><span class="sxs-lookup"><span data-stu-id="ab04a-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="ab04a-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="ab04a-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="ab04a-318">Förskjutning från slutet av rullnings listen till max knappens knapp för skjutreglaget.</span><span class="sxs-lookup"><span data-stu-id="ab04a-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="ab04a-319">Den här gränsen kan användas för att förhindra att knappen för tummen reser till en ytterst ände av rullnings listen</span><span class="sxs-lookup"><span data-stu-id="ab04a-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="ab04a-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="ab04a-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="ab04a-321">Kant linje format för knapp för tumm</span><span class="sxs-lookup"><span data-stu-id="ab04a-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="ab04a-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="ab04a-323">Valfritt Pixelmap-ID.</span><span class="sxs-lookup"><span data-stu-id="ab04a-323">Optional pixelmap ID.</span></span> <span data-ttu-id="ab04a-324">Om detta Pixelmap-ID inte är noll använder rullnings listen den här Pixelmap för att rita rullnings List bakgrunden</span><span class="sxs-lookup"><span data-stu-id="ab04a-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="ab04a-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="ab04a-326">Valfritt Pixelmap-ID.</span><span class="sxs-lookup"><span data-stu-id="ab04a-326">Optional pixelmap ID.</span></span> <span data-ttu-id="ab04a-327">Om detta Pixelmap-ID inte är noll, använder knapp rullnings knappen den här Pixelmap för att rita sig själv</span><span class="sxs-lookup"><span data-stu-id="ab04a-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="ab04a-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="ab04a-329">Valfritt Pixelmap-ID.</span><span class="sxs-lookup"><span data-stu-id="ab04a-329">Optional pixelmap ID.</span></span> <span data-ttu-id="ab04a-330">Om detta Pixelmap-ID inte är noll, använder rullnings listen det här Pixelmap-ID: t för att rita rullnings listen till vänster/uppåt</span><span class="sxs-lookup"><span data-stu-id="ab04a-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="ab04a-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="ab04a-332">Valfritt Pixelmap-ID.</span><span class="sxs-lookup"><span data-stu-id="ab04a-332">Optional pixelmap ID.</span></span> <span data-ttu-id="ab04a-333">Om detta Pixelmap-ID inte är noll använder rullnings listen det här Pixelmap-ID: t för att rita rullnings listen för rullnings listen</span><span class="sxs-lookup"><span data-stu-id="ab04a-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="ab04a-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="ab04a-335">Resurs-ID för färg som används för att fylla skjutreglaget</span><span class="sxs-lookup"><span data-stu-id="ab04a-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="ab04a-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="ab04a-337">Resurs-ID för den färg som används för att rita knappens kant linje</span><span class="sxs-lookup"><span data-stu-id="ab04a-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="ab04a-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="ab04a-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="ab04a-339">Resurs-ID för färg som används för att fylla rullnings List slut knappar</span><span class="sxs-lookup"><span data-stu-id="ab04a-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="ab04a-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="ab04a-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="ab04a-341">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-341">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="ab04a-342">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="ab04a-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="ab04a-344">Lägsta rapporterade värde</span><span class="sxs-lookup"><span data-stu-id="ab04a-344">Minimum reported value</span></span> |
| <span data-ttu-id="ab04a-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="ab04a-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="ab04a-346">Maximalt rapporterat värde</span><span class="sxs-lookup"><span data-stu-id="ab04a-346">Maximum reported value</span></span> |
| <span data-ttu-id="ab04a-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="ab04a-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="ab04a-348">Aktuellt värde</span><span class="sxs-lookup"><span data-stu-id="ab04a-348">Current value</span></span> |
| <span data-ttu-id="ab04a-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="ab04a-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="ab04a-350">Nålans rese gräns</span><span class="sxs-lookup"><span data-stu-id="ab04a-350">Needle travel limit</span></span> |
| <span data-ttu-id="ab04a-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="ab04a-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="ab04a-352">Nålans rese gräns</span><span class="sxs-lookup"><span data-stu-id="ab04a-352">Needle travel limit</span></span> |
| <span data-ttu-id="ab04a-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="ab04a-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="ab04a-354">Bredd för barr i bild punkt</span><span class="sxs-lookup"><span data-stu-id="ab04a-354">Needle width in pixel</span></span> |
| <span data-ttu-id="ab04a-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="ab04a-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="ab04a-356">Nål höjden i bild punkter</span><span class="sxs-lookup"><span data-stu-id="ab04a-356">Needle height in pixel</span></span> |
|<span data-ttu-id="ab04a-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="ab04a-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="ab04a-358">Nålans rit position.</span><span class="sxs-lookup"><span data-stu-id="ab04a-358">Needle draw position.</span></span> <span data-ttu-id="ab04a-359">Om GX_STYLE_SLIDER_VERTICAL anges används för att ange förskjutningen från start positionen för nålventil till skjutreglaget till vänster.</span><span class="sxs-lookup"><span data-stu-id="ab04a-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="ab04a-360">Else, används för att ange förskjutningen från start positionen för nålventil till skjutreglaget överst.</span><span class="sxs-lookup"><span data-stu-id="ab04a-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="ab04a-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="ab04a-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="ab04a-362">Nål hotpot_offset som används för att ange förskjutningen från start positionen för Barrets start punkt till det aktiva skjutreglaget.</span><span class="sxs-lookup"><span data-stu-id="ab04a-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="ab04a-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="ab04a-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="ab04a-364">Definition</span><span class="sxs-lookup"><span data-stu-id="ab04a-364">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

### <a name="members"></a><span data-ttu-id="ab04a-365">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="ab04a-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="ab04a-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="ab04a-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="ab04a-367">Resurs-ID för Pixelmap som ska visas för den här ramen.</span><span class="sxs-lookup"><span data-stu-id="ab04a-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="ab04a-368">ID: t kan vara 0.</span><span class="sxs-lookup"><span data-stu-id="ab04a-368">The ID can be 0.</span></span> |
| <span data-ttu-id="ab04a-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="ab04a-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="ab04a-370">Förskjut från widgeten Sprite till vänster för att Visa Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ab04a-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="ab04a-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="ab04a-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="ab04a-372">Förskjutning från widgeten Sprite överst för att Visa Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ab04a-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="ab04a-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="ab04a-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="ab04a-374">Fördröjnings värde, i GUIX timer-Tick när den här ramen visas innan den går vidare till nästa Sprite-ram</span><span class="sxs-lookup"><span data-stu-id="ab04a-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="ab04a-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="ab04a-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="ab04a-376">Definiera hur bakgrunden ska raderas.</span><span class="sxs-lookup"><span data-stu-id="ab04a-376">Define how the background should be erased.</span></span> <span data-ttu-id="ab04a-377">Möjliga värden för det här fältet är:</span><span class="sxs-lookup"><span data-stu-id="ab04a-377">Possible values for this field are:</span></span><br /><span data-ttu-id="ab04a-378">GX_SPRITE_BACKGROUND_NO_ACTION: Ingen fyllning mellan ramar</span><span class="sxs-lookup"><span data-stu-id="ab04a-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="ab04a-379">GX_SPRITE_BACKGROUND_SOLID_FILL: rita om Sprite-bakgrund</span><span class="sxs-lookup"><span data-stu-id="ab04a-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="ab04a-380">GX_SPRITE_BACKGROUND_RESTORE: Återställ tidigare Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ab04a-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="ab04a-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="ab04a-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="ab04a-382">Alfa värde som ska läggas till i den visade Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="ab04a-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="ab04a-383">Värdet 255 anger att inget extra alfa värde ska införas.</span><span class="sxs-lookup"><span data-stu-id="ab04a-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="ab04a-384">Om Pixelmap innehåller en alfa kanal läggs denna alfa kanal till i ramens alfa värde.</span><span class="sxs-lookup"><span data-stu-id="ab04a-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
