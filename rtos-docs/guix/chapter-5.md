---
title: Kapitel 5 – GUIX visnings driv rutiner
description: GUIX-bildskärms driv rutiner definierar program gränssnittet mellan den sammanfattade arbets ytan och den fysiska skärm maskin varan.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c8f509aee1892693c22f8cfba3207158de4a1e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827174"
---
# <a name="chapter-5---guix-display-drivers"></a>Kapitel 5 – GUIX visnings driv rutiner

GUIX-bildskärms driv rutiner definierar program gränssnittet mellan den sammanfattade arbets ytan och den fysiska skärm maskin varan. GUIX-bildskärms driv rutinen implementerar ritnings funktionerna på den lägsta nivån som faktiskt ändrar pixel färg information i arbets ytans minne och överför arbets ytans minne till den fysiska bufferten för bildskärms ramar i datorer med dubbel buffert.

GUIX-bildskärms driv rutiner definieras av en struktur som innehåller de fysiska visnings parametrarna och en uppsättning funktions pekare till driv rutins funktionerna för låg nivå. Med hjälp av dessa indirekta funktions pekare skapas de ritade funktionerna för arbets ytan och widgeten helt oberoende av maskin varu informationen.

GUIX innehåller en komplett, fullständigt fungerande standard uppsättning rit funktioner för varje färg djup och färg format som stöds. När du implementerar en bildskärms driv rutin utan specifika funktioner för maskin varu acceleration eller andra maskin varu specifika överväganden är dessa standard rit funktioner vanligt vis tillräckliga för den slutgiltiga driv rutins implementeringen. För de här enkla driv rutinerna är den enda funktionen som normalt måste implementeras i driv rutins program vara en funktion för att konfigurera maskin varu enheten. Detta omfattar ofta att initiera olika maskin varu register för att definiera skärmens klocka, Visa dimensioner osv. För alla andra funktioner initierar driv rutins implementeringen bara GX_DISPLAY funktions pekare till standard implementeringar av funktioner för det önskade färg djupet och formatet.

När du implementerar en anpassad bildskärms driv rutin är det bästa sättet att först initiera bildskärms funktionen för bildskärms driv rutinen med standard program varu implementeringen för det färgdjup som du vill stödja, och sedan ersätta de funktions pekare där du vill anropa dina anpassade funktions implementeringar (om det finns några). För att hjälpa med detta finns en standard inställnings funktion för varje färg djup och format som stöds. Om du till exempel skriver en 16-bitars 5:6:5 format RGB-bildskärms driv rutin, är det första som den anpassade driv rutinen vanligt vis att anropa den allmänna installations rutinen för det här färg djupet:

UINT my_custom_565_display_driver (GX_DISPLAY * display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

Parametern my_buffer_toggle ovan är en pekare till en växlings bar bildskärms driv rutins funktion (som kan vara GX_NULL om driv rutinen är enkel buffert och rita direkt till maskin varans buffert).

Om du skriver en anpassad bildskärms driv rutin måste du ta med huvud filen gx_display. h i den anpassade driv rutins källan, som är en intern användnings rubrik fil som inte är tillgänglig för program nivå program.

Ritnings funktionerna på GUIX visas som inmatade en pekare till en **GX_DRAW_CONTEXT** -struktur. **GX_DRAW_CONTEXTs** strukturen definierar urklipps koordinaterna för den aktuella rit åtgärden tillsammans med de pensel och färger som används. Varje ritnings funktion tar emot ytterligare parametrar som är särskilda för funktions kraven.

Signaturen för den **GX_DISPLAY** driv Rutinens start punkt definieras som

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

Även om namnet på den här funktionen är helt upp till Implementeraren, är konventionen för driv rutinerna som medföljer GUIX att använda ett maskin varu särskilt enhets namn i <device> fältet och färg formatet för <format> fältet ovan.

Den här funktionen måste initiera **GX_DISPLAYs** strukturen som angetts som indata och utföra eventuella maskin varu inställningar som krävs. **GX_DISPLAYs** strukturen innehåller följande fält.

| &nbsp; |
| --- | --- |
| ULONG gx_display_id <br/> Det här är ett fält som används av programmet, i de fall där fler än en instans av en viss driv rutin skapas. |
| CHAR * gx_display_name <br/> Ett valfritt namn som används för att identifiera driv rutinen. |
| GX_DISPLAY * gx_display_created_next <br/> Det här fältet initieras av GUIX och används för att skapa och underhålla en lista över alla GX_DISPLAY instanser. |
| GX_DISPLAY * gx_display_created_previous <br/> Det här fältet initieras av GUIX och används för att skapa och underhålla en lista över alla GX_DISPLAY instanser. |
| GX_VALUE gx_display_color_format <br/> Det här fältet ska återspegla grafik data formatet som stöds av den här driv rutinen. Färg format typerna definieras i huvud filen gx_api. h. |
| GX_VALUE gx_display_width <br/> Det här fältet ska initieras för att innehålla den fysiska visnings bredden i bild punkter. |
| GX_VALUE gx_display_height <br/> Det här fältet ska initieras för att innehålla den fysiska visnings höjden i bild punkter. |
| GX_COLOR * gx_display_color_table <br/> Detta är en pekare till en tabell som används för att konvertera färg-ID-värden till färg format för vissa färg värden. |
| GX_PIXELMAP * gx_display_pixelmap_table <br/> Det här är en pekare till den aktiva Pixelmap-tabellen för den här visningen. |
| GX_FONT * gx_display_font_table <br/> Det här är en pekare till den aktiva teckensnitts tabellen för den här visningen. |
| GX_COLOR * gx_display_palette <br/> För driv rutiner för palettfärger är det här en pekare till den aktiva färgpaletten. För driv rutiner som inte använder en färgpalett är den här pekaren GX_NULL. |
| UINT gx_display_pixelmap_table_size <br/> Antal poster i den aktiva Pixelmap-tabellen. |
| UINT gx_display_font_table_size <br/> Antal poster i den aktiva teckensnitts tabellen. |
| UINT gx_display_palette_size <br/> Antal poster i färgpalett (om sådana finns). |
| ULONG gx_display_handle <br/> En unik identifierare eller *referens* som anger visningen.
| UINT gx_display_driver_ready <br/> Det här fältet används för att signalera till GUIX när driv rutinen är klar för drift. I vissa fall kan driv rutinen kräva flera nivåer av initiering och konfiguration, under vilken tid GUIX inte får försöka använda driv rutinen. Den här flaggan ska vara inställd på 1 när driv rutinen är klar för att betjäna begär Anden. |
| VOID * gx_display_driver_data <br/> Det här fältet används av driv rutins implementeringen. Om driv rutinen behöver skapa och referera till ytterligare information som inte är tillgänglig i GX_DISPLAYs strukturen, ska driv rutinen allokera utrymme för och peka på ytterligare data med det här struktur fältet. Ett exempel på driv rutins särskilda extra data kan omfatta den DMA-kanal som används av driv rutinen eller SPI-kanalen som bildskärmens buffert är ansluten till. |
| VOID (* gx_display_driver_drawing_initiate) (struct GX_DISPLAY_STRUCT * display, struct GX_CANVAS_STRUCT * arbets yta) <br/> Detta är en funktions pekare som, om NOT NULL, anropas av funktionen gx_canvas_drawing_initiate. Den här funktionen kan användas för att starta en ny visnings lista för att Visa driv rutiner som använder en grafik accelerator eller visnings lista för maskin varu bilder. Den här funktions pekaren kan vara NULL. |
| VOID (* gx_display_driver_palette_set) (struct GX_DISPLAY_STRUCT * display, GX_COLOR * palett, INT Count) <br/> Det här är en pekare till en funktion för att installera en färgpalett. Den här funktionen är NULL om inte driv rutinen körs i paletten (även kallat färg uppslags tabell eller CLUT). |
| VOID (* gx_display_driver_simple_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INTy1, INT x2, INT Y2) <br/> Det här är en pekare till en funktion för att implementera allmän linje ritning, ingen kant utjämning. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_simple_wide_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INTy1, INT x2, INT Y2) <br/> Det här är en pekare till en funktion för att implementera allmän bred linje ritning, ingen kant utjämning. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INTy1, INT x2, INT Y2) <br/> Det här är en pekare till en funktion för att implementera generisk linje ritning med ett alias. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_wide_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INTy1, INT x2, INT Y2) <br/> Det här är en pekare till en funktion för att implementera allmän kant linje ritning med ett alias. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_horizonal_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INT x2, INT y) <br/> Det här är en pekare till en funktion för att implementera det särskilda fallet för vågrät linje ritning. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_horizonal_pixelmap_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INT x2, INT y, GX_PIXELMAP * karta) <br/> Det här är en pekare till en funktion för att implementera ritning på en enskild Pixelmap-rad. Den här funktionen används internt för mönster fyllnings former. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_vertical_line_draw) (GX_DRAW_CONTECT * kontext, INT Y1, INT Y2, INT x) <br/> Det här är en pekare till en funktion för att implementera det särskilda fallet för vågrät linje ritning. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_horizonal_pattern_line_draw) (GX_DRAW_CONTECT * kontext, INT x1, INT x2, INT y) <br/> Det här är en pekare till en funktion för att implementera vågrät mönster linje ritning. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_vertical_pattern_line_draw) (GX_DRAW_CONTECT * kontext, INT Y1, INT Y2, INT x) <br/> Det här är en pekare till en funktion för att implementera lodrät mönster linje ritning. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_canvas_copy) (struct GX_CANVAS_STRUCT * Source, struct GX_CANVAS_STRUCT * mål) <br/> Det här är en pekare till en funktion för att kopiera arbets ytans data från en arbets yta till en annan. Käll arbets ytan ogiltig rektangel används för att definiera kopierings området. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_canvas_blend) (struct GX_CANVAS_STRUCT * Source, struct GX_CANVAS_STRUCT * mål) <br/> Det här är en pekare till en funktion för att alpha-blanda arbets ytans data från käll arbets ytan med befintliga data på mål arbets ytan. Käll arbets ytan ogiltig rektangel används för att definiera blandnings området. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_pixelmap_blend) (GX_DRAW_CONTEXT * kontext, INT Xpos, INT ypos, GX_PIXELMAP * PMP, GX_UBYTE alpha) <br/> Det här är en pekare till en funktion för att blanda en Pixelmap på bakgrunds arbets ytan som definieras av rit kontexten. Det angivna alpha-värdet kan vara ett tillägg till en alfa kanal som finns i Pixelmap-data. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_pixelmap_draw) (GX_DRAW_CONTEXT * kontext, INT Xpos, INT ypos, GX_PIXELMAP * PMP) <br/> Det här är en pekare till en funktion för att rita en Pixelmap i arbets ytan som definieras av rit kontexten. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_jpeg_draw) (GX_DRAW_CONTEXT * kontext, INT Xpos, INT ypos, GX_PIXELMAP * PMP) <br/> Det här är en pekare till en funktion för att avkoda en JPG-bild och återge den direkt på arbets ytan. Den här funktionen anges endast om GX_SOFTWARE_DECODER_SUPPORT har definierats. Den här funktions pekaren måste vara NULL. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_png_draw) (GX_DRAW_CONTEXT * kontext, INT Xpos, INT ypos, GX_PIXELMAP * PMP) <br/> Det här är en pekare till en funktion för att avkoda en PNG-bild och återge den direkt på arbets ytan. Den här funktionen anges endast om GX_SOFTWARE_DECODER_SUPPORT har definierats. Den här funktions pekaren måste vara NULL. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_pixelmap_rotate) (GX_DRAW_CONTEXT * kontext, INT Xpos, INT ypos, GX_PIXELMAP * PMP INT-vinkel, INT rot_cx, INT rot_cy) <br/> Det här är en pekare till en funktion för att rotera en pixemap och återge resultatet direkt på arbets ytan. Den här funktionen anropas av gx_canvas_pixelmap_rotate APIDefault-implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID * gx_display_driver_pixel_write) (GX_DRAW_CONTEXT * kontext, INT x, INT y, GX_COLOR färg) <br/> Det här är en pekare till en funktion för att skriva en bild punkt i arbets ytans minne. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. <br/>
| VOID * gx_display_driver_block_move) (GX_DRAW_CONTEXT * kontext, GX_RECTANGLE * block, INT xshift, INT yshift) <br/> Det här är en pekare till en funktion för att flytta eller flytta ett block med pixlar på en arbets yta. Den här funktionen används främst för att snabbt rulla ett fönster innehåll. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_pixel_blend) (GX_DRAW_CONTEXT * kontext, INT x, INT y, GX_COLOR färg, GX_UBYTE alpha) <br/> Den här funktionen används för att blanda den inkommande pixelns färg värde med det befintliga färg värdet i arbets ytans minne på position x, y. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| GX_COLOR (* gx_display_driver_native_color_get) (GX_COLOR rawcolor) <br/> Den här funktionen konverterar en färg från formatet 32-bit A:R: G:B som används internt av GUIX till det interna färg formatet på arbets ytan och visas. Viss förlust av färg information förväntas för bildskärms driv rutiner som körs med lägre färgdjup. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| USHORT (* gx_display_driver_row_pitch_get) (USHORT bredd) <br/> Returnerar antalet byte eller klivet i en rad med grafik data som har fått den begärda arbets ytans bredd. Den här funktionen används för att beräkna storleken på det minnes område som krävs för att skapa en arbets yta. Rad bredd och bredd är inte alltid detsamma på grund av begränsningar i maskin varu skannings linjen. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_buffer_toggle) (struct GX_CANVAS_STRUCT * arbets yta, GX_RECTANGLE * dirty_area) <br/> Det här är en pekare till en funktion för att växla mellan arbets-och synliga bildruteproportioner för datorer med dubbelt buffrat minne. Den här funktionen måste först instruera maskin varan att börja använda den nya bufferten och sedan kopiera den ändrade delen av den nya synliga bufferten till Companion-bufferten för att se till att de två buffertarna stannar i synch. | 
| VOID (* gx_display_driver_polygon_draw) (GX_DRAW_CONTEXT * Context, INT num_points, GX_POINT * formhörn <br/> Pekare till en funktion för att rita en polygon. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_polygon_fill) (GX_DRAW_CONTEXT * Context, INT num_points, GX_POINT * formhörn <br/> Pekare till en funktion för att rita en fylld polygon. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_circle_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r) <br/> Pekare till en funktion för att rita en cirkel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r) <br/> Pekar till en funktion för att rita en kantad cirkel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_wide_circle_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r) <br/> Pekare till en funktion för att rita en cirkel med en bred disposition. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r) <br/> Visar en funktion för att rita en anti-aliasad cirkel med en bred disposition. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_circle_fill) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r) <br/> Pekar till en funktion för att rita en fylld cirkel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_arc_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Pekare till en funktion för att rita en båge. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_arc_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r, INT start_angle, INTend_angle) <br/> Pekar till en funktion för att rita en överliggande båge. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_wide_arc_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Pekar till en funktion för att rita en båge med en bred disposition. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_wide_arc_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r, INT start_angle, INTend_angle) <br/> Pekar till en funktion för att rita en överliggande båge. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_arc_fill) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Pekare till en funktion för att rita en fylld båge. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_pie_fill) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Pekare till en funktion för att rita en fylld cirkel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_ellipse_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, INT a, INT b) <br/> Pekare till en funktion för att rita en ellips. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_ellipse_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, INT a, INT b) <br/> Pekare till en funktion för att rita en ellips. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_wide_ellipse_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, INT a, INT b) <br/> Pekar till en funktion för att rita en ellips med en bred disposition. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_anti_aliased_wide_ellipse_draw) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, INT a, INT b) <br/> Pekar till en funktion för att rita en ellips med en bred disposition. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_ellipse_fill) (GX_DRAW_CONTEXT * kontext, INT xcenter, INT YCenter, INT a, INT b) <br/> Pekar till en funktion för att rita en fylld ellips. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_8bit_glyph_draw) (GX_DRAW_CONTEXT * Context, GX_RECTANGLE * draw_area, GX_POINT * map_offset, constGX_GLYPH * glyf) <br/> Pekare för att rita 1 8-bit aliased text-glyf till arbets ytan med hjälp av den aktuella rit kontextens pensel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_4bit_glyph_draw) (GX_DRAW_CONTEXT * Context, GX_RECTANGLE * draw_area, GX_POINT * map_offset, CONST GX_GLYPH * glyf) <br/> Pekare för att rita 1 4-bit aliased text-glyf till arbets ytan med hjälp av den aktuella rit kontextens pensel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |
| VOID (* gx_display_driver_1bit_glyph_draw) (GX_DRAW_CONTEXT * Context, GX_RECTANGLE * draw_area, GX_POINT * map_offset, CONST GX_GLYPH * glyf) <br/> Pekare för att rita 1 1-bitars monokromt text tecken till arbets ytan med hjälp av den aktuella rit kontextens pensel. Standard implementeringar av den här funktionen tillhandahålls för varje färg djup och färg format som stöds. |


