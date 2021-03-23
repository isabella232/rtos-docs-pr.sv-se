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
# <a name="appendix-i---guix-information-structures"></a>Bilaga I – GUIX informations strukturer 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>Definition

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a>Medlemmar

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | Text för att ordna om |
| **gx_bidi_text_info_font**               | Teckensnitt som används för att visa text, ange det som GX_NULL om rad brytning inte behövs |
| **gx_bidi_text_info_display_width**      | Tillgänglig bredd för visning, Ställ in den på-1 om rad brytning inte behövs |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>Definition

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a>Medlemmar

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | Pekare till matrisen med omordningen dubbelriktad text |
| **gx_bidi_resolved_text_info_total_lines**      | Totalt antal rader matchad dubbelriktad text för ett stycke |
| **gx_bidi_resolved_text_info_next**             | Dubbelriktad dubbelriktad text information för nästa stycke |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>Definition

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
### <a name="members"></a>Medlemmar

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | Totalt antal steg som nål färdas genom att flytta från den aktuella nålventil till en nyligen tilldelad bänk |
| **gx_circular_gauge_info_animation_delay**       | Antalet GUIX klock Tick som ska förskjutas mellan animeringssekvenser |
| **gx_circular_gauge_info_needle_xpos**           | Avståndet från vänster om mätar widgeten till rotations punkten för mätarens Barr |
| **gx_circular_gauge_info_needle_ypos**           | Avståndet från överkanten i mätar widgeten till rotations punkten för mätarens Barr |
| **gx_circular_gauge_info_needle_xcor**           | Avståndet från den högra delen av nålventil till rotations punkten för mätarens Barr |
| **gx_circular_gauge_info_needle_ycor**           | Avståndet från den översta delen av nålventil till rotations punkten för mätarens Barr |
| **gx_circular_gauge_info_needle_pixelmap**       | Resurs-ID för Pixelmap som ska användas för att rita mätar nål. Den här bilden roteras efter behov av mätar widgeten för att Visa mätarens barr i valfri position |

Diagrammet nedan illustrerar Xpos, ypos och XCOR, ycor koordinater:

![Diagram över koordinaterna för nål Y och X](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>Definition

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

### <a name="members"></a>Medlemmar

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | Det minsta data värde som används för att beräkna skalning
| **gx_line_chart_max_val**          | Maximalt data värde, som används för att beräkna skalning |
| **gx_line_chart_data**             | Pekar mot en matris med heltals värden. Detta är de heltals värden som ritas av linje diagrammets widget |
| **gx_line_ <side> _margin**          | Förskjutningen från diagram fönstret som är yttre till det faktiska diagrammets åter givnings område. Diagrammets axel och data linje ritas alltid inom den här inre gränsen, vilket gör att programmet kan rita etiketter och annan information i diagram fönstret, men utanför diagrammets diagram område |
| **gx_line_chart_max_data_count**   | Antalet data värden som kan finnas. Den här parametern används för att beräkna skalningen på x-axeln eller intervall för att rita data punkter. |
| **gx_line_active_data_count**      | Antalet data värden som faktiskt finns i data matrisen. Ett linje diagram kan skalas för att rita högst 100 värden (till exempel), men för en viss uppdatering kan det faktiskt finnas ett mindre antal data värden. |
| **gx_line_axis_line_width**        | Bredd på linjen som används för att rita den vågräta och lodräta axeln |
| **gx_line_data_line_width**        | Bredd på den ritade data linjen |
| **gx_line_chart_axis_color**       | Resurs-ID för färgen som används för att rita axel linjerna |
| **gx_line_chart_line_color**       | Resurs-ID för den färg som används för att rita diagrammets data linje |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>Definition

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a>Medlemmar

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | Resurs-ID för mus bilden |
| **gx_mouse_cursor_hotspot_x**      | Förskjutningen från vänster om musen till klickbar bild punkt |
| **gx_mouse_cursor_hotspot_y**      | Förskjutningen från bildens överkant till punktens klickbara bild punkt |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>Definition

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a>Medlemmar

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | Minsta drag avstånd per GUIX timer för att utlösa ett SNÄRTNING-händelse. Anropa GX_FIXED_VAL_MAKE för att skapa ett fast punkt värde för data typen |
| **gx_pen_configuration_max_pen_speed_ticks** | Den maximala dra hastigheten i GUIX timer-Tick för att utlösa en SNÄRTNING-händelse | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>Definition

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a>Medlemmar

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Resurs-ID för Pixelmap som fyller bakgrunden före nål. Om den övre bakgrunds Pixelmap inte har angetts används den för att fylla bakgrunden både före och efter nål |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | Resurs-ID för Pixelmap som fyller bakgrunden efter nål |
| **gx_pixelmap_slider_info_needle_pixelmap**           | Resurs-ID för nålventil Pixelmap |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**Definition**

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

### <a name="members"></a>Medlemmar

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | Lägsta rapporterade värde |
| **gx_progress_bar_info_max_val**             | Maximalt rapporterat värde |
| **gx_progress_bar_info_current_val**         | Aktuellt värde |
| **gx_progress_bar_info_font_id**             | Resurs-ID för teckensnittet som används för att rita det valfria text värdet i widgeten förlopps indikator      |
| **gx_progress_bar_normal_text_color**        | Resurs-ID för text färgen i läget normal som används för att definiera den valfria text ritningen i widgeten förlopps indikator |
| **gx_progress_bar_selected_text_color**      | Resurs-ID för textfärg när widgeten får fokus, används för att definiera valfri text ritning i förlopps indikatorns widget |
| **gx_progress_bar_disabled_text_color**      | Resurs-ID för text färgen när GX_STYLE_ENABLED inte är aktiv, används för att definiera den valfria text ritningen i widgeten för förlopps indikatorn |
| **gx_progress_bar_fill_pixelmap**            | Resurs-ID för Pixelmap för bakgrunds fyllning|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>Definition

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

### <a name="members"></a>Medlemmar

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | Widgetens position i x-koordinaten |
| **gx_radial_progress_bar_info_ycenter**           | Widgetens position i y-koordinaten  |
| **gx_radial_progress_bar_info_radius**            | Radien för förlopps cirkeln |
| **gx_radial_progress_bar_info_current_val**       | Aktuellt värde, begränsat till intervallet [-360, 360], anger vinkeln delta mellan ankar positionen och slut punkten för den övre bågen. Negativt värde gör att bågen ritas i en medsols riktning som börjar vid ankar positionen. Positivt värde gör att bågen ritas in i riktningen medurs med början vid ankar positionen. Programmet måste skala det verkliga ord svärdet som anges för att tilldela ett vinkel värde till widgeten för förlopps indikatorn |
| **gx_radial_progress_bar_anchor_val**             | Start vinkeln för den övre förlopps bågen. Värdet definieras som en heltals grad med 0 grader peka på höger och 90 grad som visar en rak position. |
| **gx_radial_progress_bar_font_id**                | Resurs-ID för det teckensnitt som används för att rita det valfria text värdet i widgeten förlopps indikator |
| **gx_radial_progress_bar_normal_text_color**      | Resurs-ID för text färgen i läget normal som används för att definiera den valfria text ritningen i widgeten förlopps indikator |
| **gx_radial_progress_bar_selected_text_color**    |Resurs-ID för text färgen när widgeten får fokus, används för att definiera valfri text ritning i förlopps indikatorns widget |
| **gx_radial_progress_bar_disabled_text_color**    | Resurs-ID för text färgen när GX_STYLE_ENABLED inte är aktiv, används för att definiera den valfria text ritningen i widgeten för förlopps indikatorn |
| **gx_radial_progress_bar_normal_brush_width**     | Bredden på den nedre förlopps cirkeln |
| **gx_radial_progress_bar_selected_brush_width**   | Bredden för den övre förloppet, den övre bågen kan vara smalare, samma som eller bredare än den nedre cirkeln |
| **gx_radial_progress_bar_normal_brush_color**     | Resurs-ID för färgen som ska fyllas i lägre förlopps cirkel |
| **gx_radial_progress_bar_selected_brush_color**   | Resurs-ID för färgen som fyller mot den övre förloppet för en båge |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>Definition

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

### <a name="members"></a>Medlemmar

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | Avstånd från vänster om skjutreglagets widget till rotations punkten för skjutreglaget |
| **gx_radial_slider_info_ycenter**             | Avstånd från skjutreglagets överkant till rotations punkten för skjutreglaget |
| **gx_radial_slider_info_radius**              | Radien för den radiella skjutreglaget cirkel |
| **gx_radial_slider_info_track_width**         | Bredd på radiellt Slider-spår |
| **gx_radial_slider_info_current_angle**       | Aktuell vinkel för skjutreglage |
| **gx_radial_slider_info_min_angle**           | Minsta skjutreglagets vinkel |
| **gx_radial_slider_info_max_angle**           | Maximal skjutreglages vinkel |
| **gx_radial_slider_info_angle_list**          | Vinkel värde lista, definierar fäst vinklar, om det är inställt, kan skjutreglagets vinkel bara vara en av de definierade ankar vinklarna |
| **gx_radial_slider_info_list_count**          | Antal ankar vinklar |
| **gx_radial_slider_info_background_pixelmap** | Resurs-ID för bakgrunds Pixelmap |
| **gx_radial_slider_info_needle_pixelmap**     | Resurs-ID för barr Pixelmap |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>Definition

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a>Medlemmar

|                                  |                         |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | Vänster om rektangeln   |  
| **gx_rectangle_top**             | Övre delen av rektangeln    | 
| **gx_rectangle_right**           | Rektangelns högerkant  |
| **gx_rectangle_bottom**          | Längst ned i rektangeln |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>Definition

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a>Medlemmar

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | Resurs-ID för normalt text teckensnitt |
| **gx_rich_text_fonts_bold_id**     | Resurs-ID med fet text teckensnitt |
| **gx_rich_text_fonts_italic_id**   | Resurs-ID för kursivt text teckensnitt |
| **gx_rich_text_fonts_bold_italic_id** | Resurs-ID med fet kursiv text teckensnitt |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**Definition**

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

### <a name="members"></a>Medlemmar

|                         |                               |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | Aktuell rullnings position       |
| **gx_scroll_minimum**   | Lägsta rapporterade position     |
| **gx_scroll_maximum**   | Högsta rapporterade position     |
| **gx_scroll_visible**   | Synligt intervall för överordnad fönster   |
| **gx_scroll_increment** | Minsta delta värde för rullnings List |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>Definition

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

### <a name="members"></a>Medlemmar

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | Bredd på widgeten rullnings List, i bild punkter |
| **gx_scroll_thumb_width**                | Bredden på knapp tummen som bilder på rullnings listen visas i bild punkter. Det här värdet är vanligt vis ett antal pixlar som är mindre än den totala rullnings listens bredd |
| **gx_scroll_thumb_travel_min**           | Förskjutning från slutet av rullnings listen till den minsta skjutreglaget för knapp resans slut punkt. Den här gränsen kan användas för att förhindra att knappen för tummen reser till en ytterst ände av rullnings listen |
| **gx_scroll_thumb_travel_max**           | Förskjutning från slutet av rullnings listen till max knappens knapp för skjutreglaget. Den här gränsen kan användas för att förhindra att knappen för tummen reser till en ytterst ände av rullnings listen |
| **gx_scroll_thumb_border_style**         | Kant linje format för knapp för tumm |
| **gx_scroll_fill_pixelmap**              | Valfritt Pixelmap-ID. Om detta Pixelmap-ID inte är noll använder rullnings listen den här Pixelmap för att rita rullnings List bakgrunden |
| **gx_scroll_thumb_pixelmap**             | Valfritt Pixelmap-ID. Om detta Pixelmap-ID inte är noll, använder knapp rullnings knappen den här Pixelmap för att rita sig själv |
| **gx_scroll_up_pixelmap**                | Valfritt Pixelmap-ID. Om detta Pixelmap-ID inte är noll, använder rullnings listen det här Pixelmap-ID: t för att rita rullnings listen till vänster/uppåt |
| **gx_scroll_down_pixelmap**              | Valfritt Pixelmap-ID. Om detta Pixelmap-ID inte är noll använder rullnings listen det här Pixelmap-ID: t för att rita rullnings listen för rullnings listen |
| **gx_scroll_thumb_color**                | Resurs-ID för färg som används för att fylla skjutreglaget |
| **gx_scroll_thumb_border_color**         | Resurs-ID för den färg som används för att rita knappens kant linje | 
| **gx_scroll_button_color**               | Resurs-ID för färg som används för att fylla rullnings List slut knappar |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>Definition

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

### <a name="members"></a>Medlemmar

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | Lägsta rapporterade värde |
| **gx_slider_info_max_val**              | Maximalt rapporterat värde |
| **gx_slider_info_current_value**        | Aktuellt värde |
| **gx_slider_info_min_travel**           | Nålans rese gräns |
| **gx_slider_info_max_travel**           | Nålans rese gräns |
| **gx_slider_info_needle_width**         | Bredd för barr i bild punkt |
| **gx_slider_info_needle_height**        | Nål höjden i bild punkter |
|**gx_slider_info_needle_inset**          | Nålans rit position. Om GX_STYLE_SLIDER_VERTICAL anges används för att ange förskjutningen från start positionen för nålventil till skjutreglaget till vänster. Else, används för att ange förskjutningen från start positionen för nålventil till skjutreglaget överst. |
| **gx_slider_info_needle_hotspot_offset** | Nål hotpot_offset som används för att ange förskjutningen från start positionen för Barrets start punkt till det aktiva skjutreglaget. |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>Definition

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

### <a name="members"></a>Medlemmar

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | Resurs-ID för Pixelmap som ska visas för den här ramen. ID: t kan vara 0. |
| **gx_sprite_frame_x_offset**             | Förskjut från widgeten Sprite till vänster för att Visa Pixelmap |
| **gx_sprite_frame_y_offset**             | Förskjutning från widgeten Sprite överst för att Visa Pixelmap |
| **gx_sprite_frame_delay**                | Fördröjnings värde, i GUIX timer-Tick när den här ramen visas innan den går vidare till nästa Sprite-ram |
| **gx_sprite_frame_background_operation** | Definiera hur bakgrunden ska raderas. Möjliga värden för det här fältet är:<br />GX_SPRITE_BACKGROUND_NO_ACTION: Ingen fyllning mellan ramar<br />GX_SPRITE_BACKGROUND_SOLID_FILL: rita om Sprite-bakgrund<br />GX_SPRITE_BACKGROUND_RESTORE: Återställ tidigare Pixelmap |
| **gx_sprite_frame_alpha**                | Alfa värde som ska läggas till i den visade Pixelmap. Värdet 255 anger att inget extra alfa värde ska införas. Om Pixelmap innehåller en alfa kanal läggs denna alfa kanal till i ramens alfa värde. |
