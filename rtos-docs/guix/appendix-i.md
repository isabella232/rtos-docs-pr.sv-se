---
title: Bilaga I – GUIX-informationsstrukturer
description: Lär dig mer om GUIX-informationsstrukturer.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8730dbfc49ed51716f32c118a25ebffc907b19a54d98d83ede4155f87fbecb7b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784174"
---
# <a name="appendix-i---guix-information-structures"></a>Bilaga I – GUIX-informationsstrukturer 

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
| Medlemmar | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | Text för att ändra ordning |
| **gx_bidi_text_info_font**               | Teckensnitt som används för att visa text, ange det till GX_NULL radbrytning inte behövs |
| **gx_bidi_text_info_display_width**      | Tillgänglig bredd för visning, ställ in den på -1 om radbrytning inte behövs |

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

| Medlemmar | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | Pekare till matrisen med omsorterad bidi-text |
| **gx_bidi_resolved_text_info_total_lines**      | Totalt antal rader med lösta bidi-text för ett stycke |
| **gx_bidi_resolved_text_info_next**             | Löst information om offerttext för nästa stycke |

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

| Medlemmar | Description |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | Totalt antal steg som nålen färdas genom när den flyttas från den aktuella nålvinkeln till en nyligen tilldelad nålvinkel |
| **gx_circular_gauge_info_animation_delay**       | Antalet GUIX-klockan tickar för att fördröja mellan animeringsstegen |
| **gx_circular_gauge_info_needle_xpos**           | Avståndet från vänster om mätarwidgeten till mitten av rotationen på mätarnålen |
| **gx_circular_gauge_info_needle_ypos**           | Avståndet från överdelen av mätarwidgeten till mitten av rotationen på mätarnålen |
| **gx_circular_gauge_info_needle_xcor**           | Avståndet från vänster om nålbilden till mitten av rotationen på mätarnålen |
| **gx_circular_gauge_info_needle_ycor**           | Avståndet från nålens övre del till mitten av rotationen på mätarnålen |
| **gx_circular_gauge_info_needle_pixelmap**       | Resurs-ID för pixelkartan som ska användas för att rita mätarnålen. Den här bilden roteras efter behov av mätarwidgeten för att visa mätarnålen på valfri plats |

Diagrammet nedan visar koordinaterna xpos, ypos och xcor, ycor:

![Diagram över nål Y- och X-koordinaterna](./media/guix/image8.png)

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

| Medlemmar | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | Det minsta datavärdet som används för att beräkna skalning
| **gx_line_chart_max_val**          | Det maximala datavärdet, som används för att beräkna skalning |
| **gx_line_chart_data**             | Pekare till en matris med heltalsvärden. Det här är heltalsvärdena som ritas av linjediagramswidgeten |
| **gx_line_ <side> _margin**          | Förskjutningen från diagramfönstrets yttre bundna till det faktiska diagramåtergivningsområdet. Diagramaxeln och datalinjen ritas alltid inom den här inre gränsen, vilket gör att programmet kan rita etiketter och annan information i diagramfönstret men utanför teckendiagrammet |
| **gx_line_chart_max_data_count**   | Antalet datavärden som kan finnas. Den här parametern används för att beräkna x-axelns skalning eller intervallet för att rita datapunkter. |
| **gx_line_active_data_count**      | Antalet datavärden som faktiskt finns i datamatrisen. Ett linjediagram kan skalas för att rita högst 100 värden (till exempel), men vid en viss uppdatering kan det faktiskt finnas ett mindre antal datavärden. |
| **gx_line_axis_line_width**        | Bredden på den linje som används för att rita den vågräta och lodräta axeln |
| **gx_line_data_line_width**        | Bredden på den ritade datalinjen |
| **gx_line_chart_axis_color**       | Resurs-ID för den färg som används för att rita axellinjerna |
| **gx_line_chart_line_color**       | Resurs-ID för den färg som används för att rita diagrammets datalinje |

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

| Medlemmar | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | Resurs-ID för musavbildningen |
| **gx_mouse_cursor_hotspot_x**      | Förskjutningen från vänster om musbilden till musens bildpunkt |
| **gx_mouse_cursor_hotspot_y**      | Förskjutningen från överst i musbilden till musbildens hotspot |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>Definition

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| Medlemmar | Description |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | Det minsta dra avståndet per GUIX-timer tick för att utlösa en EVENT. Anropa GX_FIXED_VAL_MAKE för att skapa ett datatypvärde för fast punkt |
| **gx_pen_configuration_max_pen_speed_ticks** | Den maximala dra-hastigheten i GUIX-timern tickar för att utlösa en TRIGGER-händelse | 

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

| Medlemmar | Description |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Resurs-ID för pixelkartan för att fylla i bakgrunden före nålen. Om den övre pixelkartan i bakgrunden inte har angetts används den för att fylla i bakgrunden både före och efter nålen |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | Resurs-ID för pixelkartan för att fylla i bakgrunden efter nålen |
| **gx_pixelmap_slider_info_needle_pixelmap**           | Resurs-ID för pixelkartan med nål |

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

| Medlemmar | Description |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | Minsta rapporterade värde |
| **gx_progress_bar_info_max_val**             | Maximalt rapporterat värde |
| **gx_progress_bar_info_current_val**         | Aktuellt värde |
| **gx_progress_bar_info_font_id**             | Resurs-ID för teckensnittet som används för att rita det valfria textvärdet i förloppsfältets widget      |
| **gx_progress_bar_normal_text_color**        | Resurs-ID för textfärgen i normalt tillstånd som används för att definiera den valfria textritningen i förloppsfältets widget |
| **gx_progress_bar_selected_text_color**      | Resurs-ID för textfärgen när widgeten får fokus, används för att definiera den valfria textritningen i förloppsfältets widget |
| **gx_progress_bar_disabled_text_color**      | Resurs-ID för textfärgen när GX_STYLE_ENABLED inte är aktiv, används för att definiera den valfria textritningen i förloppsfältets widget |
| **gx_progress_bar_fill_pixelmap**            | Resurs-ID för pixelkartan för bakgrundsfyllning|

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

| Medlemmar | Description |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | Widgetposition i x koordinat |
| **gx_radial_progress_bar_info_ycenter**           | Widgetposition i y-koordinat  |
| **gx_radial_progress_bar_info_radius**            | Radien för förloppskretsen |
| **gx_radial_progress_bar_info_current_val**       | Det aktuella värdet, begränsat till intervallet [-360, 360], anger angular-delta mellan fästpunkten och slutpunkten för den övre båge. Negativt värde gör att båge ritas i en medurs riktning med början vid fästpunktspositionen. Positivt värde gör att båge ritas i en moturs riktning med början vid fästpunktspositionen. Programmet måste skala det verkliga ordvärdet som anges för att tilldela ett angularvärde till förloppsfältets widget |
| **gx_radial_progress_bar_anchor_val**             | Start vinkel för den övre förlopps arc. Värdet definieras i termer av heltalsgrad med 0 grader som pekar åt höger och 90 grader som visar en rät upp-position. |
| **gx_radial_progress_bar_font_id**                | Resurs-ID för teckensnittet som används för att rita det valfria textvärdet i förloppsfältets widget |
| **gx_radial_progress_bar_normal_text_color**      | Resurs-ID för textfärgen i normalt tillstånd som används för att definiera den valfria textritningen i förloppsfältets widget |
| **gx_radial_progress_bar_selected_text_color**    |Resurs-ID för textfärgen när widgeten får fokus, används för att definiera den valfria textritningen i förloppsfältets widget |
| **gx_radial_progress_bar_disabled_text_color**    | Resurs-ID för textfärgen när GX_STYLE_ENABLED inte är aktiv, används för att definiera den valfria textritningen i förloppsfältets widget |
| **gx_radial_progress_bar_normal_brush_width**     | Bredden på den nedre förloppskretsen |
| **gx_radial_progress_bar_selected_brush_width**   | Bredden på den övre förloppsbåge, den övre båge kan vara smalare, samma som eller bredare än den nedre cirkeln |
| **gx_radial_progress_bar_normal_brush_color**     | Resurs-ID för färgen som ska fylla cirkeln med lägre förlopp |
| **gx_radial_progress_bar_selected_brush_color**   | Resurs-ID för färgen som ska fylla den övre förlopps arc |

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

| Medlemmar | Description |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | Avstånd från vänster om skjutreglagets widget till mitten av rotationen på skjutreglagets nål |
| **gx_radial_slider_info_ycenter**             | Avstånd från upptill i skjutreglagets widget till mitten av rotationen på skjutreglagets nål |
| **gx_radial_slider_info_radius**              | Radie för cirkel med radiellt skjutreglage |
| **gx_radial_slider_info_track_width**         | Bredden på det radiella skjutreglaget |
| **gx_radial_slider_info_current_angle**       | Aktuell skjutreglagevinkel |
| **gx_radial_slider_info_min_angle**           | Minsta skjutreglagets vinkel |
| **gx_radial_slider_info_max_angle**           | Maximal skjutreglagevinkel |
| **gx_radial_slider_info_angle_list**          | Vinkelvärdelista, definierar fästpunktsvinklar. Om skjutreglagets vinkel är inställd kan den bara vara en av de definierade fästpunktsvinklarna |
| **gx_radial_slider_info_list_count**          | Antal fästpunktsvinklar |
| **gx_radial_slider_info_background_pixelmap** | Resurs-ID för pixelkarta i bakgrunden |
| **gx_radial_slider_info_needle_pixelmap**     | Resurs-ID för pixelkarta med nål |

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

| Medlemmar | Description |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | Vänster om rektangeln   |  
| **gx_rectangle_top**             | Överst i rektangeln    | 
| **gx_rectangle_right**           | Höger om rektangeln  |
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

| Medlemmar | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | Resurs-ID för normalt textteckensnitt |
| **gx_rich_text_fonts_bold_id**     | Resurs-ID för fetstil |
| **gx_rich_text_fonts_italic_id**   | Resurs-ID för kursiv textteckensnitt |
| **gx_rich_text_fonts_bold_italic_id** | Resurs-ID för fet kursiv text |

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

| Medlemmar | Description |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | Aktuell rullningsposition       |
| **gx_scroll_minimum**   | Minsta rapporterade position     |
| **gx_scroll_maximum**   | Maximal rapporterad position     |
| **gx_scroll_visible**   | Synligt intervall för överordnat fönster   |
| **gx_scroll_increment** | Minsta deltavärde för rullningslist |

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

| Medlemmar | Description |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | Bredden på widgeten för rullningslisten, i bildpunkter |
| **gx_scroll_thumb_width**                | Bredden på tumknappen som bilder i rullningslisten, i bildpunkter. Det här värdet är vanligtvis ett visst antal bildpunkter som är mindre än den totala rullningslistens bredd |
| **gx_scroll_thumb_travel_min**           | Förskjut från slutet av rullningslisten till minsta tumknapps respunkt. Den här gränsen kan användas för att förhindra att tumknappen kommer till slutet av rullningslisten |
| **gx_scroll_thumb_travel_max**           | Förskjut från slutet av rullningslisten till den maximala respunkten för tumknappen. Den här gränsen kan användas för att förhindra att tumknappen kommer till slutet av rullningslisten |
| **gx_scroll_thumb_border_style**         | Tumknapp för kantlinjeformat |
| **gx_scroll_fill_pixelmap**              | Valfritt pixelkarta-ID. Om det här pixelkartans ID inte är noll använder rullningslisten den här pixelkartan för att rita rullningslistsbakgrunden |
| **gx_scroll_thumb_pixelmap**             | Valfritt pixelkarta-ID. Om det här pixelkartans ID inte är noll använder rullningslisten tumknappen den här pixelkartan för att rita sig själv |
| **gx_scroll_up_pixelmap**                | Valfritt pixelkarta-ID. Om det här pixelkartans ID inte är noll använder rullningslisten det här pixelkarta-ID:t för att rita rullningslisten till vänster/uppåt-knappen |
| **gx_scroll_down_pixelmap**              | Valfritt pixelkarta-ID. Om det här pixelkartans ID inte är noll använder rullningslisten det här pixelkarta-ID:t för att rita rullningslisten till höger/ned-knappen |
| **gx_scroll_thumb_color**                | Resurs-ID för färg som används för att fylla tumknappen |
| **gx_scroll_thumb_border_color**         | Resurs-ID för färg som används för att rita tumknappens kantlinje | 
| **gx_scroll_button_color**               | Resurs-ID för färg som används för att fylla rullningslistens slutknappar |

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

| Medlemmar | Description |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | Minsta rapporterade värde |
| **gx_slider_info_max_val**              | Maximalt rapporterat värde |
| **gx_slider_info_current_value**        | Aktuellt värde |
| **gx_slider_info_min_travel**           | Nålens resgräns |
| **gx_slider_info_max_travel**           | Nålens resgräns |
| **gx_slider_info_needle_width**         | Nålbredd i pixel |
| **gx_slider_info_needle_height**        | Nålhöjd i pixel |
|**gx_slider_info_needle_inset**          | Nåldragningsposition. Om GX_STYLE_SLIDER_VERTICAL har angetts används för att ange förskjutningen från nålens startposition till skjutreglaget till vänster. Annars används för att ange förskjutningen från nålens startposition till skjutreglagets övre del. |
| **gx_slider_info_needle_hotspot_offset** | Nål hotpot_offset används för att ange förskjutningen från nålens startposition till skjutreglagets hotspot. |

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

| Medlemmar | Description |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | Resurs-ID för pixelkartan som ska visas för den här ramen. ID:t kan vara 0. |
| **gx_sprite_frame_x_offset**             | Förskjutning från den grafiska widgeten till vänster för att visa pixelkartan |
| **gx_sprite_frame_y_offset**             | Förskjut från widgetens övre del för att visa pixelkartan |
| **gx_sprite_frame_delay**                | Fördröjningsvärdet i GUIX-timern tickar efter att den här bildrutan har visas innan du går vidare till nästa grafiska bildruta |
| **gx_sprite_frame_background_operation** | Definiera hur bakgrunden ska raderas. Möjliga värden för det här fältet är:<br />GX_SPRITE_BACKGROUND_NO_ACTION: Ingen fyllning mellan bildrutor<br />GX_SPRITE_BACKGROUND_SOLID_FILL: Rita om bakgrund<br />GX_SPRITE_BACKGROUND_RESTORE: Återställa föregående pixelkarta |
| **gx_sprite_frame_alpha**                | Alfavärde som ska läggas till i den pixelkarta som visas. Värdet 255 anger att inget extra alfavärde ska införas. Om pixelkartan innehåller en alfakanal läggs den här alfakanalen till i bildrutans alfavärde. |
