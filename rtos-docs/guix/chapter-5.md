---
title: Kapitel 5 – GUIX-visningsdrivrutiner
description: GUIX-visningsdrivrutiner definierar programvarugränssnittet mellan den abstrakta arbetsytan för ritning och den fysiska visningsmaskinvaran.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 804187ce8562e274205e97448da77d29f99016072c137cb3c4f1f42dac58c432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788549"
---
# <a name="chapter-5---guix-display-drivers"></a>Kapitel 5 – GUIX-visningsdrivrutiner

GUIX-visningsdrivrutiner definierar programvarugränssnittet mellan den abstrakta arbetsytan för ritning och den fysiska visningsmaskinvaran. GUIX-visningsdrivrutinen implementerar de ritningsfunktioner på lägsta nivå som faktiskt ändrar bildpunktsfärginformation i arbetsytans minne och överför arbetsytans minne till bufferten för den fysiska visningsramen i dubbelbufferterade system.

GUIX-visningsdrivrutiner definieras av en struktur som innehåller de fysiska visningsparametrarna och en uppsättning funktionspekare till drivrutinsfunktionerna på låg nivå. Genom att använda dessa indirekta funktionspekare görs de abstrakta arbetsyte- och widgetritningsfunktionerna helt oberoende av maskinvaruinformationen.

GUIX tillhandahåller en komplett, fullt funktionell standarduppsättning med ritningsfunktioner för varje färgdjup- och färgformat som stöds. När du implementerar en visningsdrivrutin utan någon specifik maskinvaruaccelerationskapacitet eller andra maskinvaruspecifika överväganden räcker dessa standardritningsfunktioner normalt för den slutliga drivrutinsimplementering. För dessa enklaste drivrutiner är den enda funktion som normalt behöver implementeras i drivrutinsprogramvaran en funktion för att konfigurera maskinvaruenheten. Detta innebär ofta att olika maskinvaruregister initieras för att definiera SKÄRM-klockan, visningsdimensioner osv. För alla andra funktioner initierar drivrutinsimplementering helt enkelt GX_DISPLAY pekare till standardfunktionsimplementeringarna för önskat färgdjup och format.

När du implementerar en anpassad visningsdrivrutin är det bästa sättet att först initiera pekarna för ritningsfunktionen för visningsdrivrutiner med standardprogramimplementering för det färgdjup som du vill stödja och sedan ersätta de funktions pekare där du vill anropa dina anpassade funktionsimplementeringar (om det finns några). För att underlätta detta finns det en standardinställningsfunktion tillgänglig för varje färgdjup och format som stöds. Om du till exempel skriver en RGB-visningsdrivrutin i 16-bitars 5:6:5-format är det första som din anpassade drivrutin normalt gör att anropa den allmänna installationsrutinen för det här färgdjupet:

UINT my_custom_565_display_driver(GX_DISPLAY *display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

Parametern my_buffer_toggle ovan är en pekare till växlingsfunktionen för visningsdrivrutinsbufferten (som kan vara GX_NULL om drivrutinen är enkelbuffertad och ritas direkt till maskinvarurambufferten).

Om du skriver en anpassad visningsdrivrutin måste du inkludera gx_display.h-huvudfilen i din anpassade drivrutinskälla, som är en intern huvudfil för användning som inte är tillgänglig för programvara på programnivå.

Ritningsfunktionerna på GUIX-visningsnivå tar emot som indata en pekare **till en GX_DRAW_CONTEXT** struktur. Den **GX_DRAW_CONTEXT** strukturen definierar urklippskoordinaterna för den aktuella ritningsåtgärden tillsammans med penseln och färgerna som används. Varje ritningsfunktion tar emot ytterligare parametrar som är specifika för funktionskraven som indata.

Signaturen för **GX_DISPLAY** för drivrutinen definieras som

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

Även om namnet på den här funktionen är helt upp till implementeraren är konventionen för drivrutiner som medföljer GUIX att använda ett maskinvaruspecifikt enhetsnamn i fältet och <device> färgformatet för <format> fältet ovan.

Den här funktionen måste initiera **GX_DISPLAY** som anges som indata och utföra maskinvaruinställningar som krävs. Den **GX_DISPLAY** strukturen innehåller följande fält.

| &nbsp; |
| --- | --- |
| ULONG-gx_display_id <br/> Det här är ett fält som ska användas av programmet, i de fall där fler än en instans av en viss drivrutin skapas. |
| CHAR *gx_display_name <br/> Ett valfritt namn som används för att identifiera drivrutinen. |
| GX_DISPLAY *gx_display_created_next <br/> Det här fältet initieras av GUIX och används för att skapa och underhålla en lista över alla GX_DISPLAY instanser. |
| GX_DISPLAY *gx_display_created_previous <br/> Det här fältet initieras av GUIX och används för att skapa och underhålla en lista över alla GX_DISPLAY instanser. |
| GX_VALUE gx_display_color_format <br/> Det här fältet bör återspegla det grafikdataformat som stöds av drivrutinen. Färgformattyperna definieras i gx_api.h-huvudfilen. |
| GX_VALUE gx_display_width <br/> Det här fältet ska initieras för att innehålla den fysiska visningsbredden, i bildpunkter. |
| GX_VALUE gx_display_height <br/> Det här fältet ska initieras för att innehålla den fysiska visningshöjden i bildpunkter. |
| GX_COLOR *gx_display_color_table <br/> Det här är en pekare till en tabell som används för att konvertera färg-ID-värden till färgformateringsspecifika färgvärden. |
| GX_PIXELMAP *gx_display_pixelmap_table <br/> Det här är en pekare till den aktiva pixelkarta-tabellen för den här visningen. |
| GX_FONT *gx_display_font_table <br/> Det här är en pekare till den aktiva teckensnittstabellen för den här visningen. |
| GX_COLOR *gx_display_palette <br/> För drivrutiner i paletteläge är detta en pekare till den aktiva färgpaletten. För drivrutiner som inte använder en färgpalett visas pekaren GX_NULL. |
| UINT-gx_display_pixelmap_table_size <br/> Antal poster i den aktiva pixelkarta-tabellen. |
| UINT-gx_display_font_table_size <br/> Antal poster i den aktiva teckensnittstabellen. |
| UINT-gx_display_palette_size <br/> Antal poster i färgpaletten (om det finns några). |
| ULONG-gx_display_handle <br/> En unik identifierare, *eller* referens, som anger visningen.
| UINT-gx_display_driver_ready <br/> Det här fältet används för att signalera till GUIX när drivrutinen är redo för drift. I vissa fall kan drivrutinen kräva flera nivåer av initiering och konfiguration, under vilken GUIX inte får försöka använda drivrutinen. Den här flaggan ska anges till 1 när drivrutinen är redo att bearbeta ritningsbegäranden. |
| VOID *gx_display_driver_data <br/> Det här fältet används av drivrutinsimplementering. Om drivrutinen behöver skapa och referera till ytterligare information som inte är tillgänglig i GX_DISPLAY-strukturen ska drivrutinen allokera utrymme för och peka på dessa ytterligare data med hjälp av det här strukturfältet. Ett exempel på drivrutinsspecifika extradata kan vara DMA-kanalen som används av drivrutinen eller DEN KANAL-kanal som bufferten för visningsramen är ansluten till. |
| VOID (*gx_display_driver_drawing_initiate)(struct GX_DISPLAY_STRUCT *display, struct GX_CANVAS_STRUCT *canvas) <br/> Det här är en funktionspekare som, om inte NULL, anropas av gx_canvas_drawing_initiate funktionen. För visningsdrivrutiner som använder en grafikaccelerator eller maskinvarugrafikvisningslista kan den här funktionen användas för att starta en ny visningslista. Den här funktionspekaren kan vara NULL. |
| VOID (*gx_display_driver_palette_set)(struct GX_DISPLAY_STRUCT *display, GX_COLOR *palette, INT count) <br/> Det här är en pekare till en funktion för att installera en färgpalett. Den här funktionen är NULL såvida inte drivrutinen fungerar i paletteläge (kallas även för färguppslagstabell eller CLUT). |
| VOID (*gx_display_driver_simple_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Det här är en pekare till en funktion för att implementera allmän linjeritning, utan antialias. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_simple_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Det här är en pekare till en funktion för att implementera allmän bred linjeritning, utan antialias. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Det här är en pekare till en funktion för att implementera allmän antialiaslinjeritning. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Det här är en pekare till en funktion för att implementera allmän antialias vid linjeritning. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_horizonal_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> Det här är en pekare till en funktion för att implementera specialfallet för vågrät linjeritning. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_horizonal_pixelmap_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y, GX_PIXELMAP *map) <br/> Det här är en pekare till en funktion för att implementera ritning av en enda pixelkarta-rad. Den här funktionen används internt för mönsterfyllningsformer. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_vertical_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> Det här är en pekare till en funktion för att implementera specialfallet för vågrät linjeritning. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_horizonal_pattern_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> Det här är en pekare till en funktion för att implementera vågrät mönsterlinjeritning. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_vertical_pattern_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> Det här är en pekare till en funktion för att implementera lodrät mönsterlinjeritning. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_canvas_copy)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> Det här är en pekare till en funktion för att kopiera arbetsytedata från en arbetsyta till en annan. Den ogiltiga rektangeln för källarbetsytan används för att definiera kopieringsområdet. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_canvas_blend)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> Det här är en pekare till en funktion för att alfa-blanda arbetsytedata från källarbetsytan med befintliga data på målarbetsytan. Den ogiltiga rektangeln för källarbetsytan används för att definiera blandningsområdet. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_pixelmap_blend)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp, GX_UBYTE alpha) <br/> Det här är en pekare till en funktion för att blanda en pixelkarta på bakgrundsarbetsytan som definieras av rita-kontexten. Det angivna alfavärdet kan vara utöver en alfakanal som finns i pixelkartans data. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_pixelmap_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Det här är en pekare till en funktion för att rita en pixelkarta i arbetsytan som definieras av rita-kontexten. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_jpeg_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Det här är en pekare till en funktion för att avkoda en jpg-bild och rendera den direkt på arbetsytan. Den här funktionen tillhandahålls endast om GX_SOFTWARE_DECODER_SUPPORT har definierats. Den här funktionspekaren är NULL. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_png_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Det här är en pekare till en funktion för att avkoda en png-bild och rendera den direkt på arbetsytan. Den här funktionen tillhandahålls endast om GX_SOFTWARE_DECODER_SUPPORT har definierats. Den här funktionspekaren är NULL. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_pixelmap_rotate)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp INT angle, INT rot_cx, INT rot_cy) <br/> Det här är en pekare till en funktion för att rotera en pixemap och rendera resultatet direkt till arbetsytan. Den här funktionen anropas av gx_canvas_pixelmap_rotate APIDefault-implementeringar av den här funktionen tillhandahålls för varje färgdjup- och färgformat som stöds. |
| VOID *gx_display_driver_pixel_write)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color) <br/> Det här är en pekare till en funktion för att skriva en pixel i arbetsytans minne. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. <br/>
| VOID *gx_display_driver_block_move)(GX_DRAW_CONTEXT *context,GX_RECTANGLE *block, INT xshift, INT yshift) <br/> Det här är en pekare till en funktion för att flytta eller flytta ett block med bildpunkter i en arbetsyta. Den här funktionen används främst för att snabbt rulla ett fönsterinnehåll. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_pixel_blend)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color, GX_UBYTE alpha) <br/> Den här funktionen används för att alfa-blanda det inkommande pixelfärgvärdet med det befintliga färgvärdet i arbetsytans minne vid position x,y. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| GX_COLOR (*gx_display_driver_native_color_get)(GX_COLOR rawcolor) <br/> Den här funktionen konverterar en färg från färgformatet 32-bitars A:R:G:B som används internt av GUIX till arbetsytans och visningens ursprungliga färgformat. Viss förlust av färginformation förväntas för visningsdrivrutiner som körs på lägre färgdjup. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| USHORT (*gx_display_driver_row_pitch_get)(USHORT width) <br/> Returnerar byteantalet eller steget för en rad med grafikdata givet den begärda arbetsytans bredd. Den här funktionen används för att beräkna storleken på det minnesområde som behövs för att skapa en arbetsyta. Radhöjden och bredden är inte alltid samma på grund av justeringsbegränsningar för genomsökningslinjen för maskinvara. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_buffer_toggle)(struct GX_CANVAS_STRUCT *canvas, GX_RECTANGLE *dirty_area) <br/> Det här är en pekare till en funktion för att växla mellan fungerande och synliga rambuffertar för dubbelbuffertade minnessystem. Den här funktionen måste först instruera maskinvaran att börja använda den nya rambufferten och sedan kopiera den ändrade delen av den nya synliga bufferten till den tillhörande bufferten för att försäkra att de två buffertarna ligger inom synk. | 
| VOID (*gx_display_driver_polygon_draw)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> Pekar på en funktion för att rita en polygon. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_polygon_fill)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> Pekar på en funktion för att rita en fylld polygon. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Pekare till en funktion för att rita en cirkel. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Pekar på en funktion för att rita en cirkel med ett antialias. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_wide_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Pekare till en funktion för att rita en cirkel med en bred kontur. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Pekar på en funktion för att rita en cirkel med ett antialias med en bred kontur. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_circle_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Pekar på en funktion för att rita en fylld cirkel. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Pekare till en funktion för att rita en båge. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> Pekare till en funktion för att rita en antialias arc. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Pekare till en funktion för att rita en båge med en bred kontur. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> Pekare till en funktion för att rita en antialias arc. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_arc_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Pekare till en funktion för att rita en fylld båge. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_pie_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Pekar på en funktion för att rita en fylld cirkel. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Pekar på en funktion för att rita en ellips. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Pekar på en funktion för att rita en ellips. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Pekare till en funktion för att rita en ellips med en bred kontur. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_anti_aliased_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Pekare till en funktion för att rita en ellips med en bred kontur. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_ellipse_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Pekar på en funktion för att rita en fylld ellips. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup och färgformat som stöds. |
| VOID (*gx_display_driver_8bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, constGX_GLYPH *glyph) <br/> Pekare till funktion för att rita en 8-bitars aliastext glyph till arbetsytan med penseln i den aktuella ritningskontexten. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup- och färgformat som stöds. |
| VOID (*gx_display_driver_4bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> Pekare till funktion för att rita en 4-bitars aliastextglyf till arbetsytan med penseln i den aktuella ritningskontexten. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup- och färgformat som stöds. |
| VOID (*gx_display_driver_1bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> Pekare till funktion för att rita en 1-bitars betningstextsglyf till arbetsytan med penseln i den aktuella ritningskontexten. Standardimplementeringarna av den här funktionen tillhandahålls för varje färgdjup- och färgformat som stöds. |


