---
title: Kapitel 4 – Beskrivning av GUIX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla GUIX-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7a17ab0d2500d021bb9397dbf673427362c45173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826451"
---
# <a name="chapter-4---description-of-guix-services"></a>Kapitel 4 – Beskrivning av GUIX-tjänster

Det här kapitlet innehåller en beskrivning av alla GUIX-tjänster (visas nedan) i alfabetisk ordning.  

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **GX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade. 

| **GUIX-tjänst**                      | **Beskrivning**                                                                             |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| gx_accordion_menu_create            | Skapa drag meny                                                                        |
| gx_accordion_menu_draw              | Menyn Rita drag                                                                          |
| gx_accordion_menu_event_process    | Händelse för processens bedrags meny                                                                 |
| gx_accordion_menu_position          | Placera meny objekt                                                                          |
| gx_animation_canvas_define          | Ange minne för en animeringssekvens för en arbets yta som ska användas för efterföljande animeringar. |
| gx_animation_create                  | Skapa en animering                                                               |
| gx_animation_delete                  | Ta bort en animering                                                               |
| gx_animation_drag_disable           | Inaktivera skärm dra Animations-Hook                                                           |
| gx_animation_drag_enable            | Aktivera skärm dra animation-Hook                                                            |
| gx_animation_landing_speed_set     | Ange landnings hastighet för animering av skärms dragning                                                  |
| gx_animation_start                   | Starta en animeringssekvens                                                               |
| gx_animation_stop                    | Pausa en animeringssekvens                                                                |
| gx_binres_language_count_get      |  Hämta språk antal från en binär resurs fil                                          |
| gx_binres_language_info_load      |  Läsa språk namn och storleks information från den binära resurs filen.                           |
| gx_binres_language_table_load      | föråldrad Läs in en språk tabell från bufferten för binär resurs data                          |
| gx_binres_language_table_load_ext | Läs in en språk tabell från bufferten för binär resurs data                                       |
| gx_binres_theme_load                | Läs in ett tema från buffert för binär resurs data                                                |
| gx_brush_default                     | Initiera aktuell pensel till standardvärden                                                         |
| gx_brush_define                      | Definiera pensel                                                                                 |
| gx_button_background_draw           | Knapp bakgrund för Draw                                                                       |
| gx_button_create                     | Knappen Skapa                                                                                |
| gx_button_deselect                   | Knappen avmarkera                                                                              |
| gx_button_draw                       | Knappen Rita                                                                                  |
| gx_button_event_process            | Händelse för process knapp                              |
| gx_button_select                    | Knappen Välj                                     |
| gx_canvas_alpha_set                | Ange alfa-Blend-värde för arbets yta                  |
| gx_canvas_arc_draw                 | Rita cirkel båge                                   |
| gx_canvas_block_move               | Flytta block                                        |
| gx_canvas_circle_draw              | Rita cirkel                                       |
| gx_canvas_create                    | Skapa en arbets yta                                   |
| gx_canvas_delete                    | Ta bort en arbets yta                                   |
| gx_canvas_drawing_complete         | Slutför ritning av arbets yta                           |
| gx_canvas_drawing_initiate         | Starta ritning på arbets ytan                        |
| gx_canvas_ellipse_draw             | Rita en ellips                                   |
| gx_canvas_hardware_layer_bind     | Binda arbets ytan till grafik lager                     |
| gx_canvas_hide                      | Gör en arbets yta osynlig                           |
| gx_canvas_line_draw                | Rita linje                                         |
| gx_canvas_memory_define            | Tilldela minnes adress till arbets ytan                      |
| gx_canvas_offset_set               | Tilldela arbets yta x, y Visa förskjutning                  |
| gx_canvas_pie_draw                 | Rita en cirkel form (Kil)                          |
| gx_canvas_pixel_draw               | Rita en enskild bild punkt                               |
| gx_canvas_pixelmap_blend           | Blanda en Pixelmap med bakgrund                  |
| gx_canvas_pixelmap_get             | Få en Pixelmap som pekar på data från arbets ytan            |
| gx_canvas_pixelmap_draw            | Rita Pixelmap                                     |
| gx_canvas_pixelmap_rotate          | Rotera Pixelmap                                   |
| gx_canvas_pixelmap_tile            | Panel Pixelmap                                     |
| gx_canvas_polygon_draw             | Rita polygon                                      |
| gx_canvas_rectangle_draw           | Rita rektangel                                    |
| gx_canvas_rotated_text_draw       | föråldrad Rita text roterad om mitt punkt |
| gx_canvas_rotated_text_draw_ext  | Rita text roterad om mitt punkt              |
| gx_canvas_shift                     | Shift-arbetsyta med x, y                               |
| gx_canvas_show                      | Gör en arbets yta synlig                             |
| gx_canvas_text_draw                | föråldrad Rita text                            |
| gx_canvas_text_draw_ext           | Rita text                                         |
| gx_checkbox_create                  | Skapa en kryss ruta                                 |
| gx_checkbox_draw                    | Rita en kryss ruta                                   |
| gx_checkbox_event_process          | Händelse process funktion för kryss ruta                   |
| gx_checkbox_pixelmap_set           | Tilldela kryss rutan Pixelmap                          |
| gx_checkbox_select                  | Markera kryss ruta                                   |
| gx_circular_gauge_angle_get       | Hämta Barr vinkel för mätar widget                |
| gx_circular_gauge_angle_set       | Tilldela nålventil för mätar widget                  |
| gx_circular_gauge_animation_set   | Definiera animering av cirkulär mätare                   |
| gx_circular_gauge_background_draw | Rita en cirkulär mätar bakgrund                    |
| gx_circular_gauge_create           | Skapa en cirkulär mätar widget                    |
| gx_circular_gauge_draw             | Rita en cirkulär mätar widget                      |
| gx_circular_gauge_event_process   | Bearbeta cirkulär mätar händelse                      |
| gx_context_brush_default            | Ange pensel för aktuell kontext                                      |
| gx_context_brush_define             | Definiera pensel för aktuell kontext                                       |
| gx_context_brush_get                | Hämta pensel för aktuell kontext                                          |
| gx_context_brush_pattern_set       | Ange mönster för den aktuella kontextens pensel                           |
| gx_context_brush_set                | Ange pensel för aktuell kontext                                          |
| gx_context_brush_style_set         | Ange pensel typ för aktuell kontext                                    |
| gx_context_brush_width_set         | Ange pensel bredd för aktuell ontext                                     |
| gx_context_color_get                | Matcha ett färg-ID till färg värde                                     |
| gx_context_fill_color_set          | Ange fyllnings färg för aktuell kontext                                     |
| gx_context_font_get                 | Matcha ett teckensnitts-ID till tecken pekaren värde                               |
| gx_context_font_set                 | Ange teckensnitt för aktuell kontext                                           |
| gx_context_line_color_set          | Ange linje färg för aktuell kontext                                     |
| gx_context_pixelmap_get             | Matcha ett Pixelmap-ID till Pixelmap-pekverktyget                       |
| gx_context_pixelmap_set             | Tilldela pensel Pixelmap, som används för områden som fylls i                            |
| gx_context_raw_brush_define        | Definiera rå pensel för aktuell kontext                                   |
| gx_context_raw_fill_color_set     | Ange rå fyllnings färg för aktuellt sammanhang                                 |
| gx_context_raw_line_color_set     | Ange rå linje färg för aktuell kontext                                 |
| gx_context_string_get               | Hämta strängen som är associerad med den aktuella ritnings kontexten (inaktuell). |
| gx_context_string_get_ext          | Hämta strängen som är associerad med den aktuella ritnings kontexten (inaktuell). |
| gx_display_active_language_set     | Tilldela aktivt språk                                                |
| gx_display_color_set                | Ersätt ett färg värde i tabellen med visnings färger.                       |
| gx_display_color_table_set         | Tilldela den färg tabell som används av en bildskärm                              |
| gx_display_create                    | Skapa bildskärm                                                        |
| gx_display_delete                    | Ta bort visning                                                        |
| gx_display_font_table_set          | Tilldela teckensnitts tabellen som används av en bildskärm                               |
| gx_display_language_table_get      | Hämta den språk tabell som är associerad med en bildskärm (inaktuell)    |
| gx_display_language_table_get_ext | Hämta den språk tabell som är associerad med en bildskärm                 |
| gx_display_language_table_set      | Tilldela språk tabellen till angiven visning (inaktuell)           |
| gx_display_language_table_set_ext | Tilldela språk tabellen till angiven visning.                       |
| gx_display_pixelmap_table_set      | Tilldela Pixelmap-tabellen som används av en visning                           |
| gx_display_string_get               | Hämta strängen som är associerad med sträng-ID (inaktuell)                |
| gx_display_string_get_ext          | Hämta sträng kopplad till sträng-ID                             |
| gx_display_string_table_get             | Hämta sträng tabell som är associerad med angiven visning (inaktuell). |
| gx_display_string_table_get_ext        | Hämta sträng tabell som är associerad med angiven visning               |
| gx_display_theme_install                 | Installera teman på den angivna visningen                               |
| gx_drop_list_close                       | Stäng List rutan                                                       |
| gx_drop_list_create                      | Skapa Drop List                                                      |
| gx_drop_list_event_process               | Händelse bearbetning för Drop List                                            |
| gx_drop_list_open                        | Öppna Drop List                                                        |
| gx_drop_list_pixelmap_set               | Ange Pixelmap till Drop List                                             |
| gx_drop_list_popup_set                  | Ange popup för att släppa listan                                                |
| gx_horizontal_list_children_position    | Placera underordnade widgetar i vågrät lista                          |
| gx_horizontal_list_create                | Skapa vågrät lista                                                |
| gx_horizontal_list_event_process        | Process händelse i vågrät lista                                      |
| gx_horizontal_list_page_index_set      | Tilldela vågrät List Page-index                                     |
| gx_horizontal_list_selected_index_get  | Hämta det valda objekt indexet                                           |
| gx_horizontal_list_selected_widget_get | Hämta det valda objektets widget                                          |
| gx_horizontal_list_selected_set         | Ange det valda objektet                                                 |
| gx_horizontal_list_total_columns_set   | Ändra antalet List kolumner efter skapandet                          |
| gx_horizontal_scrollbar_create           | Skapa vågrät rullnings List                                           |
| gx_icon_button_create                    | Knappen Skapa ikon                                                    |
| gx_icon_button_draw                      | Knappen Rita en ikon                                                   |
| gx_icon_button_pixelmap_set             | Ange Pixelmap i ikon knappen                                           |
| gx_icon_background_draw                  | Rita ikon bakgrund                                                  |
| gx_icon_create                            | Ikonen Skapa                                                           |
| gx_icon_draw                              | Rita-ikonen                                                             |
| gx_icon_event_process                    | Funktion för händelse bearbetning av ikon                                        |
| gx_icon_pixelmap_set                     | Ange Pixelmap som ikon                                                 |
| gx_image_reader_create                   | Skapa en instans av image Reader-modul                                   |
| gx_image_reader_palette_set             | Definiera bildreader-paletten                                           |
| gx_image_reader_start                    | Starta dekomprimerings-och konverterings processen                           |
| gx_line_chart_axis_draw                 | Rita linje diagram x, y-axel                                              |
| gx_line_chart_create                     | Skapa GX_LINE_CHART instans                                       |
| gx_line_chart_data_draw                 | Rita linje diagram data linje                                             |
| gx_line_chart_draw                       | Standard ritning för linje diagram                                            |
| gx_line_chart_update                     | Framtvinga uppdatering av linje diagram data                                       |
| gx_line_chart_y_scale_calculate        | Beräkna skalning av y-axelns data värden till pixel koordinater.           |
| gx_menu_create                            | Skapa meny                                                           |
| gx_menu_draw                              | Rita-menyn                                                             |
| gx_menu_event_process                     | Händelse för process-menyn                                                    |
| gx_menu_insert                                | Infoga ett nytt objekt                                                               |
| gx_menu_remove                                | Ta bort ett objekt                                                                  |
| gx_menu_text_draw                            | Text i Draw-menyn                                                                  |
| gx_menu_text_offset_set                     | Ange meny text Rita förskjutning                                                       |
| gx_multi_line_text_button_create           | Skapa flerradig text-knapp                                                   |
| gx_multi_line_text_button_draw             | Knapp för att rita flerradig text                                                     |
| gx_multi_line_text_button_event_process   | Knappen Ange teckensnitt för flerradig text                                             |
| gx_multi_line_text_button_text_draw       | Text ritnings delen av ritningen                                                 |
| gx_multi_line_text_button_text_id_set    | Knappen Ange system sträng till text                                                |
| gx_multi_line_text_button_text_set        | Tilldela en användardefinierad sträng till text knappen (inaktuell)                          |
| gx_multi_line_text_button_text_set_ext   | Tilldela en användardefinierad sträng till text knappen                                       |
| gx_multi_line_text_input_backspace         | Ta bort tecken innan markörens position i flera rader text               |
| gx_multi_line_text_input_buffer_get       | Hämtar information om buffer för text indata-widget                               |
| gx_multi_line_text_input_buffer_clear     | Tar bort alla tecken från bufferten för inmatade filer                               |
| gx_multi_line_text_input_char_insert      | Infoga UTF8-format sträng vid text markör position i flera rader (inaktuell) |
| gx_multi_line_text_input_char_insert_ext | Infoga UTF8-format sträng i text markör position i flera rader              |
| gx_multi_line_text_input_create            | Skapa text indata från flera rader                                                    |
| gx_multi_line_text_input_cursor_pos_get  | Hämta text markör position för flera rader                                  |
| gx_multi_line_text_input_delete            | Ta bort tecken efter text markörens position i flera text                 |
| gx_multi_line_text_input_down_arrow       | Flytta text markören för flera rader till nästa rad                              |
| gx_multi_line_text_input_end               | Flytta text ingångs markören i flera rader till slutet av den aktuella raden                |
| gx_multi_line_text_input_event_process    | Bearbeta text indata från flera rader                                              |
| gx_multi_line_text_input_fill_color_set  | Ange fyllnings färger för text indata från flera rader                                       |
| gx_multi_line_text_input_home              | Flytta text insättnings markören i flera rader till början av den aktuella raden              |
| gx_multi_line_text_input_left_arrow       | Flytta text markör för flera rader till vänster med ett tecken                         |
| gx_multi_line_text_input_right_arrow      | Flytta text markör för flera rader direkt med ett tecken                        |
| gx_multi_line_text_input_style_add        | Lägg till text stils flaggor med flera rader                                                 |
| gx_multi_line_text_input_style_remove     | Ta bort text stils flaggor med flera rader                                              |
| gx_multi_line_text_input_style_set        | Tilldela text stils flaggor med flera rader                                              |
| gx_multi_line_text_input_text_color_set  | Tilldela text färger för text indata från flera rader                                    |
| gx_multi_line_text_input_text_select      | Välj text inmatare med flera rader                                               |
| gx_multi_line_text_input_text_set         | Tilldela text till text indata från flera rader (inaktuella)                               |
| gx_multi_line_text_input_text_set_ext          | Tilldela text till text i flera rader                         |
| gx_multi_line_text_input_up_arrow               | Flytta text insättnings markören i flera rader till föregående rad       |
| gx_multi_line_text_view_create                   | Skapa flerradig text-vy                                  |
| gx_multi_line_text_view_event_process           | Bearbeta händelse för text visning i flera rader                           |
| gx_multi_line_text_view_font_set                | Ange teckensnitt som används i text visning med flera rader                        |
| gx_multi_line_text_view_line_space_set         | Ange rad avstånd för flerradig text                          |
| gx_multi_line_text_view_scroll_info_get        | Hämta text rullnings information i flera rader                         |
| gx_multi_line_text_view_text_color_set         | Ange text färg i mulit för linje                       |
| gx_multi_line_text_view_text_id_set            | Ange system text sträng i text visning med flera rader               |
| gx_multi_line_text_view_text_set                | Ange användardefinierad sträng till text visning med flera rader (inaktuell) |
| gx_multi_line_text_view_text_set_ext           | Ange användardefinierad sträng till text visning med flera rader              |
| gx_multi_line_text_view_whitespace_set          | Ange blank steg för text visning på flera rader                          |
| gx_numeric_pixelmap_prompt_create                 | Skapa numerisk Pixelmap-prompt                               |
| gx_numeric_pixelmap_prompt_format_ function_set | Åsidosätt format funktion för numerisk Pixelmap-prompt          |
| gx_numeric_pixelmap_prompt_value_set             | Ange numeriskt prompt-värde                                     |
| gx_numeric_prompt_create                           | Skapa numerisk prompt                                        |
| gx_numeric_prompt_format_function_set            | Åsidosätt format funktion för numerisk prompt                   |
| gx_numeric_prompt_value_set                       | Ange numeriskt prompt-värde                                     |
| gx_numeric_scroll_wheel_create                    | Skapa numerisk rullnings hjuls widget                           |
| gx_numeric_scroll_wheel_range_set                | Tilldela värde intervall för rullnings hjul                              |
| gx_pixelmap_button_create                          | Knappen Skapa Pixelmap                                       |
| gx_pixelmap_button_draw                            | Knappen Rita Pixelmap                                         |
| gx_pixelmap_button_event_process                  | Händelse bearbetning för Pixelmap knapp                             |
| gx_pixelmap_button_pixelmap_set                   | Ange Pixelmap i Pixelmap-knappen                              |
| gx_pixelmap_prompt_create                          | Skapa Pixelmap-prompt                                       |
| gx_pixelmap_prompt_draw                            | Prompten Draw Pixelmap                                         |
| gx_pixelmap_prompt_pixelmap_set                   | Ange Pixelmap i Pixelmap-prompten                              |
| gx_pixelmap_slider_create                          | Skapa Pixelmap-skjutreglage                                       |
| gx_pixelmap_slider_draw                            | Skjutreglage för Drawing Pixelmap                                         |
| gx_pixelmap_slider_event_process        | Händelse bearbetning för Pixelmap-skjutreglage       |
| gx_pixelmap_slider_pixelmap_set         | Ange Pixelmap i Pixelmap-skjutreglaget        |
| gx_progress_bar_background_draw         | Rita förlopps indikatorns bakgrund           |
| gx_progress_bar_create                   | Skapa en förlopps indikator                  |
| gx_progress_bar_draw                     | Rita en förlopps indikator                    |
| gx_progress_bar_event_process           | Bearbeta en händelse i förlopps indikatorn           |
| gx_progress_bar_font_set                | Ange teckensnitt för förlopps fältets text          |
| gx_progress_bar_info_set                | Ange informations struktur för förlopps indikatorn |
| gx_progress_bar_pixelmap_set            | Ange Pixelmap som används för att rita förlopps indikator |
| gx_progress_bar_range_set               | Ange värde intervall för förlopps indikatorn        |
| gx_progress_bar_text_color_set         | Ange text färg för förlopps indikator            |
| gx_progress_bar_text_draw               | Rita förlopps indikator text                 |
| gx_progress_bar_value_set               | Ange värde för förlopps indikator                 |
| gx_prompt_create                          | Skapa prompt                          |
| gx_prompt_draw                            | Draw-prompt                            |
| gx_prompt_event_process                   | Process-prompt-händelse                   |
| gx_prompt_font_set                       | Ange teckensnitt för prompt                        |
| gx_prompt_text_color_set                | Ange text färg för prompt                  |
| gx_prompt_text_draw                      | Text ritnings del i prompten Draw    |
| gx_prompt_text_get                       | Hämta prompt-text (inaktuell)           |
| gx_prompt_text_get_ext                  | Hämta frågetext                        |
| gx_prompt_text_id_set                   | Ange prompt med system text sträng     |
| gx_prompt_text_set                       | Ange frågetext (inaktuell)           |
| gx_prompt_text_set_ext                  | Ange frågetext                        |
| gx_radial_progress_bar_anchor_set      | Ange start vinkel                     |
| gx_radial_progress_bar_background_draw | Rita radiell förlopps indikator bakgrund    |
| gx_radial_progress_bar_create           | Skapa en radiell förlopps indikator           |
| gx_radial_progress_bar_draw             | Rita en radiell förlopps indikator             |
| gx_radial_progress_bar_event_process   | Händelse för process radiell förlopps indikator      |
| gx_radial_progress_bar_font_set        | Ange teckensnitt för radiellt förlopps indikator           |
| gx_radial_progress_bar_info_set        | Ange information om radiell förlopps indikator    |
| gx_radial_progress_bar_text_color_set | Ange textfärg för radiellt förlopps indikator     |
| gx_radial_progress_bar_text_draw       | Text för att rita radiell förlopps indikator          |
| gx_radial_progress_bar_value_set       | Ange värde för radiell förlopps indikator          |
| gx_radio_button_create                   | Knappen Skapa alternativ                    |
| gx_radio_button_draw                     | Knappen Rita alternativ                      |
| gx_radio_button_pixelmap_set            | Ange Pixelmap i alternativ knapp           |
| gx_radial_slider_anchor_angles_set     | Ange vinkel lista för radiella skjutreglage    |
| gx_radial_slider_angle_set              | Ange vinkel för radiella skjutreglage                |
| gx_radial_slider_animation_set          | Ange animerings information för radiellt skjutreglage       |
| gx_radial_slider_animation_start               | Ställ in vinkel för radiell Slider med animering                      |
| gx_radial_slider_create                         | Skapa ett radiellt skjutreglage                                      |
| gx_radial_slider_draw                           | Rita ett radiellt skjutreglage                                        |
| gx_radial_slider_event_process                 | Bearbeta en händelse i ett radiellt skjutreglage                               |
| gx_radial_slider_info_get                      | Hämta information pekare för radiell Slider                  |
| gx_radial_slider_info_set                      | Ange information om radiellt skjutreglage                               |
| gx_radial_slider_pixelmap_set                  | Ange pixelmaps för radiellt skjutreglage                                 |
| gx_rich_text_view_create                       | Skapa en RTF-vy                                     |
| gx_rich_text_view_draw                         | Rita RTF-vy                                         |
| gx_rich_text_view_set_fonts                    | Ange teckensnitt för Rich text-vy                                    |
| gx_rich_text_view_text_draw                    | Rita RTF-text                                    |
| gx_screen_stack_create                          | Skapa GUIX-skärmens kontroll block och minnes området. |
| gx_screen_stack_pop                             | Popup-skärmen i skärm bilden.                   |
| gx_screen_stack_push                            | Push-överför den aktuella skärmen till skärm bilden.                |
| gx_screen_stack_reset                           | Återställa skärms Tacken                                      |
| gx_scroll_wheel_create                          | Skapa bas rullnings hjulets widget                             |
| gx_scroll_wheel_event_process                  | Händelse bearbetning för rullhjul                               |
| gx_scroll_wheel_gradient_alpha_set            | Ändra övertoning av rullnings hjul                        |
| gx_scroll_wheel_row_height_set                | Tilldela radhöjd för rullnings hjul                              |
| gx_scroll_wheel_selected_background_set       | Tilldela bakgrunds bild för markerad rad                    |
| gx_scroll_wheel_selected_get                   | Hämta markerat rad index                                 |
| gx_scroll_wheel_selected_set                   | Tilldela markerat rad index                                   |
| gx_scroll_wheel_speed_set                      | Tilldela rullnings hastighet                                      |
| gx_scroll_wheel_total_rows_set                | Tilldela det totala antalet tillgängliga rader                       |
| gx_scrollbar_draw                                | Rita rullnings List                                              |
| gx_scrollbar_event_process                      | Process rullnings händelse                                     |
| gx_scrollbar_limit_check                        | Kontrol lera rullnings List gräns                                       |
| gx_scrollbar_reset                               | Återställ rullnings List                                             |
| gx_scrollbar_value_set                          | Tilldela ScrollBar-värde                                      |
| gx_single_line_text_input_backspace           | Hantera Backsteg-tecken                                  |
| gx_single_line_text_input_buffer_clear       | Rensa teckenformateringen                                  |
| gx_single_line_text_input_buffer_get         | Hämta buffert pekare                                     |
| gx_single_line_text_input_character_delete   | Ta bort tecknen                                            |
| gx_single_line_text_input_character_insert   | Infoga Character                                            |
| gx_single_line_text_input_create              | Skapa text ingångar med en rad                               |
| gx_single_line_text_input_draw                | Rita en widget för text inmatningar                          |
| gx_single_line_text_input_draw_position_get | Hämta start position för text ritning                           |
| gx_single_line_text_input_end                 | Flytta markören till slutet                                          |
| gx_single_line_text_input_event_process      | Bearbetning av text indata-händelse                                 |
| gx_single_line_text_input_fill_color_set    | Ange fyllnings färger för text ingången i en rad                  |
| gx_single_line_text_input_home                | Flytta markören till start sidan                                         |
| gx_single_line_text_input_left_arrow         | Hantera vänsterpil                                       |
| gx_single_line_text_input_position_get       | Hämta markör position                                         |
| gx_single_line_text_input_right_arrow        | Referens HÖGERPIL                                      |
| gx_single_line_text_input_style_add          | Lägg till stil flaggor                                             |
| gx_single_line_text_input_style_remove       | Ta bort stil flaggor                                          |
| gx_single_line_text_input_style_set          | Tilldela stil flaggor                                          |
| gx_single_line_text_input_text_color_set  | Ange text färger för text ingången i en rad                      |
| gx_single_line_text_input_text_select     | Välj text för text med enkel rad text                              |
| gx_single_line_text_input_text_set        | Ange text inmatad text text (inaktuell)                    |
| gx_single_line_text_input_text_set_ext    | Ange text för text i enradig text                                 |
| gx_slider_create                          | Skapa skjutreglage                                                   |
| gx_slider_draw                            | Skjutreglage för rit objekt                                                     |
| gx_slider_event_process                   | Händelse för process Slider                                            |
| gx_slider_info_set                        | Ange block för Slider-information                                    |
| gx_slider_needle_draw                     | Nål för Rita-skjutreglage                                              |
| gx_slider_needle_position_get             | Hämta Slider-position                                      |
| gx_slider_tickmarks_draw                  | Kal streck för skjutreglage                                           |
| gx_slider_travel_get                      | Hämta skjutreglaget                                               |
| gx_slider_value_calculate                 | Beräkna Slider-värde                                          |
| gx_slider_value_set                       | Ange skjutreglagets värde                                                |
| gx_sprite_create                          | Skapa GX_SPRITE widget                                         |
| gx_sprite_current_frame_set               | Tilldela widgeten aktuell visnings bild för Sprite                  |
| gx_sprite_frame_list_set                  | Tilldela eller ändra en sprite-bildruta-lista                            |
| gx_sprite_start                           | Starta en sprite-sekvens                                         |
| gx_sprite_stop                            | Stoppa en sprite-sekvens                                          |
| gx_string_scroll_wheel_create             | Skapa `GX_STRING_SCROLL_WHEEL` widget                          |
| gx_string_scroll_wheel_event_process      | Händelse vid rullnings hjul i process sträng                               |
| gx_string_scroll_wheel_string_id_list_set | Tilldela matris med sträng-ID: n                                      |
| gx_string_scroll_wheel_string_list_set    | Ändra visad sträng mat ris                                   |
| gx_string_scroll_wheel_text_get           | Hämta text för rullnings hjuls rad                              |
| gx_studio_widget_create                   | Skapa widget definierad i Studio                             |
| gx_studio_named_widget_create             | Skapa skärmen som definierats i Studio                             |
| gx_studio_display_configure               | Skapa och initiera `GX_DISPLAY` , `GX_CANVAS` och `GX_WINDOW_ROOT` |
| gx_system_active_language_set             | Tilldela aktivt språk-ID                                       |
| gx_system_canvas_refresh                  | Tvinga uppdatering (ritning) av skadade arbets ytor                       |
| gx_system_dirty_mark                      | Felaktigt markerat fält                                                 |
| gx_system_dirty_partial_add               | Markera ofullständigt arean som felaktig                                         |
| gx_system_draw_context_get                | Hämta rit kontext                                             |
| gx_system_event_fold                      | Foldevent                                                       |
| gx_system_event_send                      | Skicka händelse                                                      |
| gx_system_focus_claim                     | Fokusera på anspråk                                                     |
| gx_system_initialize                      | Initiera GUIX                                                 |
| gx_system_language_table_get              | Hämta språk tabell                                         |
| gx_system_language_table_set              | Tilldela språk tabell                                           |
| gx_system_memory_allocator_set            | Tilldela minnesallokering/inallokering av minne                            |
| gx_system_pen_configure                  | Ange Pen-konfiguration                                  |
| gx_system_screen_stack_create           | Skapa skärms tack kontroll                            |
| gx_system_screen_stack_get              | Hämta skärm Stacks pekare                         |
| gx_system_screen_stack_pop              | Popup-skärm från skärm bild                       |
| gx_system_screen_stack_push             | Sänd skärmen till skärm bilden              |
| gx_system_screen_stack_reset            | Återställa skärms Tacken                                 |
| gx_system_scroll_appearance_get         | Hämta rullnings utseende                                  |
| gx_system_scroll_appearance_set         | Ange rullnings utseende                                  |
| gx_system_start                           | Starta GUIX                                             |
| gx_system_string_get                     | Hämta sträng                                             |
| gx_system_string_table_get              | Hämta sträng tabell                                       |
| gx_system_string_table_set              | Ange sträng tabell                                       |
| gx_system_string_width_get              | Hämta sträng bredd (inaktuellt)                          |
| gx_system_string_width_get_ext         | Hämta sträng bredd                                       |
| gx_system_theme_install                  | Installera teckensnitt/färg-/Pixelmap-tabeller                     |
| gx_system_timer_start                    | Starta timer                                            |
| gx_system_timer_stop                     | Stoppa timer                                             |
| gx_system_version_string_get            | Hämta GUIX-bibliotekets versions sträng (inaktuell)      |
| gx_system_version_string_get_ext       | Hämta GUIX-bibliotekets versions sträng                   |
| gx_system_widget_find                    | Hitta widget                                            |
| gx_text_button_create                    | Knappen Skapa text                                     |
| gx_text_button_draw                      | Knapp för att rita text                                       |
| gx_text_button_event_process             | Händelse för process text knapp                              |
| gx_text_button_font_set                 | Knappen Ange teckensnitt för text                               |
| gx_text_button_text_color_set          | Ange text knapps färg                                  |
| gx_text_button_text_draw                | Text ritnings del av knapp ritning                 |
| gx_text_button_text_get                 | Hämta text som används i text knappen (inaktuell)              |
| gx_text_button_text_get_ext            | Hämta text som används i text knappen                           |
| gx_text_button_text_id_set             | Knappen tilldela system sträng till text                    |
| gx_text_button_text_set                 | Tilldela en användardefinierad sträng till text knappen (inaktuell) |
| gx_text_button_text_set_ext            | Tilldela en användardefinierad sträng till text knappen              |
| gx_text_scroll_wheel_callback_set      | Tilldela motringning för sträng hämtning (inaktuell)          |
| gx_text_scroll_wheel_callback_set_ext | Tilldela motringning för sträng hämtning                       |
| gx_text_scroll_wheel_create             | Skapa bas text rullnings hjul                          |
| gx_text_scroll_wheel_draw               | Ritnings funktion för text rullnings hjul                  |
| gx_text_scroll_wheel_event_process      | Process text rullnings hjul, händelse                        |
| gx_text_scroll_wheel_font_set          | Tilldela teckensnitt för text rullnings hjul                         |
| gx_text_scroll_wheel_text_color_set   | Tilldela text rullnings hjulets text färger                   |
| gx_tree_view_create                    | Cretae en trädvy                          |
| gx_tree_view_draw                      | Rita trädvy                              |
| gx_tree_view_event_process            | Händelse för process träds visning                     |
| gx_tree-view_indentation_set           | Ange indrag för trädvy                   |
| gx_tree_view_position                  | Positions träd, Visa objekt                    |
| gx_tree_view_root_line_color_set    | Ange rot linje färg för trädvy               |
| gx_tree_view_root_pixelmap_set       | Ange rot-pixelmaps för träd visning                |
| gx_tree_view_selected_get             | Hämta markerat objekt                      |
| gx_tree_view_selected_set             | Ange valt objekt                           |
| gx_utility_canvas_to_bmp              | Konvertera arbets ytans minne till bitmappsformat      |
| gx_utility_circle_point_get           | Beräknings punkt på en cirkel               |
| gx_utility_gradient_create             | Skapa en tonings Pixelmap                  |
| gx_utility_gradient_delete              | Ta bort en övertoning Pixelmap                  |
| gx_utility_ltoa                         | Konvertera långt heltal till ASCII               |
| gx_utility_math_acos                   | Beräkna arcus cosinus                          |
| gx_utility_math_asin                   | Beräkna arcus sinus                             |
| gx_utility_math_cos                    | Beräknings-cosinus                              |
| gx_utility_math_sin                    | Compute-sinus                                |
| gx_utility_math_sqrt                   | Compute, kvadratrot                         |
| gx_utility_bidi_paragraph_reorder         | Ändra ordning på dubbelriktad text till visnings ordningen|
| gx_utility_bidi_resolved_text_info_delete | Ta bort omordningen dubbelriktad text               |
| gx_utility_pixelmap_resize             | Ändra storlek på Pixelmap                             |
| gx_utility_pixelmap_rotate             | Rotera Pixelmap efter valfri vinkel          |
| gx_utility_pixelmap_simple_rotate      | Rotera Pixelmap med 90, 180, 270 grader     |
| gx_utility_rectangle_center            | Centrera rektangeln i en annan rektangel   |
| gx_utility_rectangle_center_find      | Hitta mitten av rektangeln                    |
| gx_utility_rectangle_combine           | Kombinera två rektanglar till första           |
| gx_utility_rectangle_compare           | Jämför två rektanglar                      |
| gx_utility_rectangle_define            | Definiera rektangel                            |
| gx_utility_rectangle_resize            | Ändra storlek på rektangel                            |
| gx_utility_rectangle_overlap_detect   | Identifiera överlappande av rektanglar                |
| gx_utility_rectangle_point_detect     | Identifiera om punkten finns i rektangeln        |
| gx_utility_rectangle_shift             | Shift-rektangel                             |
| gx_utility_string_to_alphamap         | Återge text strängen till AlphaMap (inaktuell) |
| gx_utility_string_to_alphamap_ext    | Återge text sträng till AlphaMap              |
| gx_vertical_list_children_position    | Placera underordnade i lodrät lista          |
| gx_vertical_list_create                | Skapa lodrät lista                        |
| gx_vertical_list_event_process        | Bearbeta lodrät lista-händelse                 |
| gx_vertical_list_selected_index_get  | Hämta markerat objekt index                     |
| gx_vertical_list_selected_widget_get | Hämta vald widget                         |
| gx_vertical_list_selected_set         | Ange inmatning i lodrät lista                  |
| gx_vertical_list_total_rows_set      | Ändra antal List rader efter skapande   |
| gx_vertical_scrollbar_create           | Skapa lodrät rullnings List                   |
| gx_widget_allocate                      | Allokera en widget dynamiskt               |
| gx_widget_attach                        | Koppla widget till överordnad                     |
| gx_widget_background_draw              | Bakgrund för Draw-widget                      |
| gx_widget_back_attach                  | Koppla widgeten bakåt                       |
| gx_widget_back_move                    | Flytta widgeten bakåt                         |
| gx_widget_block_move                   | Flytta block med pixlar                        |
| gx_widget_border_draw                  | Rita widget-kantlinje                          |
| gx_widget_border_style_set            | Ange kant linje format för widget                     |
| gx_widget_border_width_get            | Ange kant linje bredd för widget                     |
| gx_widget_canvas_get               | Hämta arbets ytan för widget                                                         |
| gx_widget_child_detect             | Identifiera underordnad widget                                                       |
| gx_widget_children_draw            | Rita widget underordnade                                                      |
| gx_widget_client_get               | Hämta widgets klient områden                                                    |
| gx_widget_color_get                | Matcha färg-ID till färg värde för en synlig widget                      |
| gx_widget_create                    | Skapa widget                                                             |
| gx_widget_created_test             | Testa om widgeten har skapats                                                    |
| gx_widget_delete                    | Ta bort widget                                                             |
| gx_widget_detach                    | Koppla från widget från överordnad                                                 |
| gx_widget_draw                      | Rita widget                                                               |
| gx_widget_draw_set                 | Ställ in funktionen Draw of widget                                               |
| gx_widget_event_generate           | Skapa widgets händelse                                                     |
| gx_widget_event_process            | Händelse för process-widget                                                      |
| gx_widget_event_process_set       | Ställ in händelse bearbetnings funktion i widget                                   |
| gx_widget_event_to_parent         | Skicka händelse till widgetens överordnade                                             |
| gx_widget_fill_color_set          | Tilldela fyllnings färg för widget                                                  |
| gx_widget_find                      | Hitta widget                                                               |
| gx_widget_first_child_get         | Returnera pekare till första underordnade                                             |
| gx_widget_focus_next               | Flytta fokus till nästa widget                                           |
| gx_widget_focus_previous           | Flytta fokus till föregående widget                                       |
| gx_widget_font_get                 | Matcha teckensnitts-ID till en teckensnitts pekare för en synlig widget                    |
| gx_widget_free                      | Fri widget för kontroll block minne                                          |
| gx_widget_front_move               | Flytta widgeten till fram sidan                                                      |
| gx_widget_height_get               | Hämta widgetens höjd                                                         |
| gx_widget_hide                      | Dölj widget                                                               |
| gx_widget_last_child_get          | Returnera pekare till senaste underordnade                                              |
| gx_widget_next_sibling_get        | Retur pekare till nästa syskon                                            |
| gx_widget_parent_get               | Returnera pekare till överordnad widget                                           |
| gx_widget_pixelmap_get             | Matcha Pixelmap-ID till en Pixelmap-pekare för en synlig widget            |
| gx_widget_previous_sibling_get    | Returnera pekare till föregående syskon                                        |
| gx_widget_resize                    | Ändra storlek på widget                                                             |
| gx_widget_shift                     | Shift-widget                                                              |
| gx_widget_show                      | Visa widget                                                               |
| gx_widget_status_add               | Lägg till widgets status                                                         |
| gx_widget_status_get               | Hämta status flaggor för widget                                              |
| gx_widget_status_remove            | Ta bort widgets status                                                      |
| gx_widget_string_get               | Hämta strängen som är associerad med sträng-ID för synlig widget (inaktuell) |
| gx_widget_string_get_ext          | Hämta strängen som är associerad med sträng-ID för synlig widget.             |
| gx_widget_status_test              | Testa widgeten status                                                        |
| gx_widget_style_add                | Lägg till format för widget                                                          |
| gx_widget_style_get                | Hämta widgets stil flaggor                                               |
| gx_widget_style_remove             | Ta bort widget                                                       |
| gx_widget_style_set                | Ange format för widget                                                          |
| gx_widget_text_blend               | Återge blandade text över widgeten (inaktuell)                              |
| gx_widget_text_blend_ext          | Återge blandade text över widgeten                                           |
| gx_widget_text_draw                | Rendera text över widget (inaktuell)                                      |
| gx_widget_text_draw_ext           | Rendera text över widget                                            |
| gx_widget_text_id_draw            | Återge text som identifieras av sträng-ID över widgeten                           |
| gx_widget_top_visible_child_find | Retur pekare till synligt barn som ritas överst i Z-ordningen   |
| gx_widget_type_find                | Hitta widgets typ                                                          |
| gx_widget_width_get                | Hämta widgetens bredd                                                          |
| gx_window_canvas_set               | Ange fönster arbets yta                                                         |
| gx_window_client_height_get       | Hämta fönster klientens höjd                                                  |
| gx_window_client_scroll            | Rulla fönster klienter                                                     |
| gx_window_client_width_get        | Hämta fönstrets klient bredd                                                   |
| gx_window_close                     | Avsluta körning av modal fönster                                          |
| gx_window_create                    | Skapa fönster                                                             |
| gx_window_draw                      | Rita fönster                                                               |
| gx_window_event_process            | Händelse för process fönster                                                      |
| gx_window_execute                   | Körning av modal fönster                                                    |
| gx_window_root_create              | Skapa rot fönster                                                        |
| gx_window_root_delete              | Förstör rot fönster                                                       |
| gx_window_root_event_process      | Process händelse för rot fönster                                             |
| gx_window_root_find                | Hitta rot fönstret                                                          |
| gx_window_scroll_info_get         | Hämta fönstrets rullnings information                                                    |
| gx_window_scrollbar_find           | Hitta fönster rullnings List                                                     |
| gx_window_wallpaper_get            | Hämta fönstrets Skriv bords underlägg                                                      |
| gx_window_wallpaper_set            | Ange fönster Skriv bords underlägg                                                      |

## <a name="gx_accordion_menu_create"></a>gx_accordion_menu_create

Skapa en drag meny

### <a name="prototype"></a>Prototyp

```C
UINT gx_accordion_menu_create(
    GX_ACCORDION_MENU *accordion,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style ,
    USHORT accordion_menu_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en dragspelswidget som anges och kopplar den till den angivna överordnade widgeten. En dragspelswidget-meny är anexpanding/komprimerar menyn Visa widgeten. Den accepterar alla typer av widget som underordnade meny alternativ. Drag menyer kan kapslas, vilket innebär att flera nivåer av meny djup kan skapas.

Om du vill infoga ett underordnat objekt i ett meny objekts widget, rekommenderar vi att touse GX_MENU typ widget som ett överordnat meny objekt.

Tips för att skapa en List meny för en nivå:

1.  Skapa en drag meny.

2.  Bifoga GX_MENU typ-widgetar till drag menyn.

3.  Bifoga underordnade widgetar till GX_MENU typen parent. Typen av underordnad objekt kan vara vilken typ av widget som helst GUIX.

Tips för att skapa en dragspelswidget på flera nivåer:

1.  Skapa en drag meny.

2.  Bifoga GX_MENU typ-widgetar till drag menyn.

3.  Koppla GX_ACCORDION_MENU typ widget till GX_MENU typen parent.

4.  Koppla meny alternativ till GX_ACCORDION_MENU typ överordnad enligt beskrivningen i skapa meny för att skapa en enda nivå.

### <a name="parameters"></a>Parametrar

- **drag** Pekare till kontroll blocket för menyn
- **namn** Namnet på drag spels menyn
- **överordnad** Pekare till överordnad widget
- **stil** Widgetens format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **accordion_menu_id** Programdefinierat ID för spel menyn
- **storlek** Storlek på drag spels menyn

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) framgångs meny för att skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ACCORDION_MENU my_accordion;
GX_MENU menu_1;
GX_MENU item_1;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 100, 100, 300, 150);

status = gx_accordion_menu_create(&my_accordion, “my_accordion”,
                                  parent, GX_STYLE_ENABLED,
                                  MY_ACCORDION_ID, &size);

gx_menu_create(&menu_1, “menu_1”, &my_accordion,
               GX_STRING_ID_MENU_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_TYLE_BORDER_THIN, 0, &size);

gx_menu_create(&item_1, “item_1”, &my_accordion,
               GX_STRING_ID_ITEM_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_STYLE_BORDER_THIN, 0, &size);

gx_text_offset_set(&item_1, 30, 0);

gx_menu_insert(&menu_1, &item_1);

/* If status is GX_SUCCESS the accordion menu was successfully created. */

```

Demo programmet demo_guix_widget_types, som ingår i GUIX Studio-installationen, innehåller ett komplett exempel på hur du använder widgeten för dragspelswidgeten.

### <a name="see-also"></a>Se även

- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_draw"></a>gx_accordion_menu_draw

Menyn Rita drag

### <a name="prototype"></a>Prototyp

```C
VOID gx_accordion_menu_draw(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna drag menyn. Den här tjänsten kallas vanligt vis internt av GUIX-funktionen för uppdatering av arbets ytan, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade dragspelswidgeten.

### <a name="parameters"></a>Parametrar

- **drag** Pekare till kontroll blocket för menyn

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Define a custom accordion menu draw function */

VOID my_accordion_menu_draw(GX_ACCORDION_MENU *accordion)
{
    /* Call default accordion menu draw. */
    gx_accordion_menu_draw(accordion);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_event_process"></a>gx_accordion_menu_event_process

Händelse för processens bedrags meny

### <a name="prototype"></a>Prototyp

```C
UINT gx_accordion_menu_event_process(
    GX_ACCORDION_MENU *accordion, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna drag menyn. Den här tjänsten ska anropas som standard händelse hanterare med en anpassad funktion för händelse bearbetning av spel meny händelser.

Den här tjänsten hanterar GX_EVENT_PEN_DOWN och GX_EVENT_PEN_UP händelser för att expandera/komprimera ett meny alternativ.

### <a name="parameters"></a>Parametrar

- **drag** Pekare till kontroll blocket för menyn
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- Händelse processen för att **GX_SUCCESS** (0X00) lyckades
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic accordion menu event processing as part of custom event processing function. */

UINT custom_accordion_event_process( 
    GX_ACCORDION_MENU *accordion,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default accordion menu
            event processing */
        status =
        gx_accordion_menu_event_process(accordion, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_position"></a>gx_accordion_menu_position

Placera meny objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_accordion_menu_position(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar meny alternativen för spel menyn. Den här funktionen kallas vanligt vis internt när drag menyn blir synlig. Om du vill lägga till/ta bort objekt i/från en dragspelswidget eller ändra utöknings formatet för det underordnade objektet, ska funktionen anropas för att flytta underordnade objekt.

### <a name="parameters"></a>Parametrar

- **drag** Pekare till kontroll blocket för menyn

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) placering av placerings menyn
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Position menu items in the accordion menu “my_accordion” */
status = gx_accordion_menu_position (&my_accordion);

/* If status is GX_SUCCESS the children in the accordion menu
“my_accordion” are positioned. */

```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_animation_canvas_define"></a>gx_animation_canvas_define

Ange arbets ytans minne till en styrenhet för animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_canvas_define(
    GX_ANIMATION *animation, 
    GX_CANVAS *canvas);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tillhandahåller en minnes arbets yta för en animeringssekvens som används för att implementera animeringssekvensen. Den angivna arbets ytan bör vara tillräckligt stor för att rymma widgeten för animerings mål.

När en bildruteanimering definieras ritas mål-widgeten en gång till den här animeringen och skärm bilden eller tonings effekten görs genom att ändra arbets ytans förskjutning och/eller arbets ytans alfa värde. När maskin varu stöd för flera grafik lager tillhandahålls kan du förbättra prestandan för bild-och tonings lager ***genom att definiera*** en animering som är kopplad till ett maskin varu lager som överlägg.

Animeringen kräver en bildruteanimering för att köra tonings-och tonings typer om de körs på ett färgdjup som är mindre än 16 BPP.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block
- **arbets yta** Minnes arbets yta som används för att implementera översättnings-animeringen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har definierat animeringsbildrutor
- **GX_INVALID_STATUS** (0X10) ogiltig status för animering
- **GX_INVALID_MEMORY_SIZE** (0X29) det tillhandahållna minnes blocket är inte tillräckligt stort för att skapa arbets ytan
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION animation;
GX_CANVAS animation_canvas;
GX_ROOT_WINDOW animation_root;
/* Create animation canvas. */
status = gx_canvas_create(
        &animation_canvas, /* Canvas control block. */
        “animation_canvas”, /* Name of canvas. */
        display, /* Display control block. */
        GX_ANIMATION_MANAGED, /* Type of canvas. */
        width, /* Width of canvas. */
        height, /* Height of canvas. */
        memory_area, /* Memory area of canvas. */
        memory_size /* Size of canvas memory. */
        );
if (status == GX_SUCCESS)
{
    /* Create the root window for the canvas. */
    status = gx_window_root_create(
        &animation_root, /* Root window control block. */
        “animation_root”, /* Name of root window. */
        &animation_canvas, /* Canvas of the root window. */ GX_STYLE_NONE, /* Style of the window. */
        GX_ID_NONE, /* Root window ID. */
        &root_size /* Window size. */
        );
}
if (status == GX_SUCCESS)
{
    /* Define canvas for the animation. */
    status = gx_animation_canvas_define(&animation,
                &animation_canvas);
}
/* If status is GX_SUCCESS the new canvas was successfully set to the animation manager. */

```

### <a name="see-also"></a>Se även

- gx_animation_create,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx_animation_start
- gx_animation_stop

## <a name="gx_animation_create"></a>gx_animation_create

Skapa en animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_create(GX_ANIMATION *animation);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en animeringssekvens. Kontrollanten initieras till inaktivt läge. Det går inte att starta en animering om den inte är i inaktivt läge. GX_ANIMATION kontroll block pekare kan hämtas med hjälp av gx_system_animation_get (), eller så kan det vara ett statiskt definierat kontroll block.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block


### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skapat en animeringssekvens
- Kontroll block för **GX_ALREADY_CREATED** (0x13) har redan initierats
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

/* Initialize the control block */

if (animation)
{
    status = gx_animation_create(&animation);
}

/* If status is GX_SUCCESS the new animation controller was successfully created and initialized. */

```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set,
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_disable"></a>gx_animation_drag_disable

Inaktivera skärm dra Animations-Hook

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_drag_disable(
    GX_ANIMATION *animation, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den skärm som drar animeringen hook-procedur från widgetens standard händelse process funktion och stoppar animeringssekvensen. Skärmen dra animering av hook-procedur hanterar händelser för en skärm som drar animering.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block
- **widget** Pekare till kontroll block för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION animation;
GX_WIDGET *animation_parent;

/* Disable screen drag animation of “animation_parent”. */
status = gx_animation_drag_disable(&animation, animation_parent);

/* If status is GX_SUCCESS the screen drag hook has been removed
    from the event process of “animation_parent”. */

```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx__animation_start
- gx_animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_drag_enable"></a>gx_animation_drag_enable

Aktivera skärm dra animation-Hook

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_drag_enable(
    GX_ANIMATION *animation,
    GX_WIDGET *widget, 
    GX_ANIMATION_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den internt definierade skärmen dra animering händelse process som en hook-procedur i en widgets standard händelse process funktion. Funktionen dra animering av händelse process hanterar händelser för en skärm som drar animering.

Skärmen dra hook-procedur blir standard hanterare för Penn ingångs händelser som skickas till mål-widgeten. Funktionen för händelse bearbetning i den ursprungliga widgeten anropas i en seriekopplade när du har kontrollerat skärm för att dra indata.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block
- **widget** Pekare till kontroll block för widget
- **information** Information om animering

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_STATUS** (0X26) ogiltig status för animering
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt värde
- **GX_INVALID_WIDGET** (0X12) bild skärms listan har inte angetts

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION animation;
GX_ANIMATION_INFO info;
GX_WIDGET *animation_parent;
GX_WIDGET *screen_list[] = {
    screen_1,
    screen_2,
    screen_3,
    GX_NULL
}

memset(&info, 0, sizeof(GX_ANIMATION_INFO);
info.gx_animation_parent = animation_parent;

/* If GX_STYLE_ANIMATION_WRAP is set, the screen list will wrap itself. */
info.gx_animation_style = GX_ANIMATION_SCREEN_DRAG |
                          GX_ANIMATION_HORIZONTAL |
                          GX_STYLE_ANIMATION_WRAP;
info.gx_animation_frame_interval = 1;
info.gx_animation_slide_screen_list = screen_list;

status = gx_animation_drag_enable(&animation, animation_parent,
                                  info);

/* If status is GX_SUCCESS the screen slide animinatin event
    process function has been set as a hook procedure of
    “animation_parent”. */
```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_landing_speed_set
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_landing_speed_set"></a>gx_animation_landing_speed_set

Ange landnings hastighet för animering av skärms dragning

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_landing_speed_set(
    GX_ANIMATION *animation, 
    USHORT shift_per_step);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger landnings hastigheten för animering av skärmens dra.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block
- **shift_per_step** Skift avstånd för varje steg

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_VALUE** (0X22) ogiltig parameter

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set landing speed of “my_animation” to 20. */
status = gx_animation_landing_peed_set(&my_animation, 20);

/* If status is GX_SUCCESS the landing speed is successfully set to 20. */
```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_start"></a>gx_animation_start

Starta en timer-driven animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_start(
    GX_ANIMATION *animation, 
    GX_ANIMATION_INFO *params);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en animeringssekvens med en tidigare skapad animering och en ny uppsättning med parametrar för animering. Den här funktionen gör en lokal kopia av parametrarna, vilket innebär att parameter strukturen inte behöver definieras statiskt.

GX_ANIMATION kontroll strukturen kan definieras statiskt av programmet, eller så kan den hämtas med hjälp av API: et för gx_system_animation_get ().

GX_ANIMATION_INFOs strukturen definierar parametrarna för den animering som ska köras. En fullständig beskrivning av den här strukturen och betydelsen av varje fält finns i avsnittet GUIX-animering i kapitel 3 i den här hand boken.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block
- **parametrar** Pekare till parameter struktur

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_VALUE** (0X22) ogiltig parameter
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltigt mål för animering
- **GX_INVALID_STATUS** (0X26) ogiltig status för animering
- **GX_INVALID_CANVAS** (0X20) ogiltigt animerings arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION_INFO params;
GX_ANIMATION *animation;

/* obtain an animation control block pointer */
gx_system_animation_get(&animation);
if (animation)
{
    /* define a slide down and to the right */
    params.gx_animation_start_position.gx_point_x = 0;
    params.gx_animation_start_position.gx_point_y = 0;
    params.gx_animation_end_position.gx_point_x = 100;
    params.gx_animation_end_position.gx_point_y = 200;
    params.gx_animation_style= GX_ANIMATION_TRANSLATE;
    params.gx_animation_target = &my_window;
    params.gx_animation_parent = root_window;
    params.gx_animation_start_alpha = 255;
    params.gx_animation_end_alpha = 255;

    params.gx_animation_delay_before = 0;
    params.gx_animation_steps = 10;
    params.gx_animation_tick_rate = 2;

    status = gx_animation_start(&animation, &params);
}

/* If status is GX_SUCCESS the animation is initiated. */
```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_landing_speed_set,
- gx__animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_stop"></a>gx_animation_stop

Stoppa en aktiv timer-driven animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_stop(GX_ANIMATION *animation);
```

### <a name="description"></a>Beskrivning

Stoppa en tidigare startad animering. Om kontroll Blocks pekaren för animering har allokerats med gx_system_animation_get kan programmet återanvända kontroll blocket eller återställa det till systempoolen med hjälp av gx_system_animation_free ().

### <a name="parameters"></a>Parametrar

- **animering** Pekare till animerat kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades GX_PTR_ERROR (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_STATUS** (0X26) ogiltig status för styrenhet

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION animation;

status = gx_animation_stop(&animation);

/* If status is GX_SUCCESS the animation is stopped */

```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_drag_enable
- gx_animation_start,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_binres_language_count_get"></a>gx_binres_language_count_get

Returnera antalet språk som finns i binära resurs data

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_count_get(
    GX_UBYTE *root_address, 
    GX_VALUE *returned_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tolkar ett binärt resurs data huvud för att returnera antalet språk som finns i binära data. Detta är användbart för program som måste visa en urvals lista till användaren, så att användaren kan välja mellan olika språk.

### <a name="parameters"></a>Parametrar

- **root_address** Adress till binära resurs data i minnet
- **return_count** Plats för att lagra returnerat språk antal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_FORMAT** (0X24) ogiltig binär resurs
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE language_count = 0;

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_count_get(root_address,
    &language_count);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Se även

- gx_binres_language_info_load

## <a name="gx_binres_language_info_load"></a>gx_binres_language_info_load

Läsa in språk tabell information

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_info_load(
    GX_UBYTE *root_address, 
    GX_LANGUAGE_HEDAER *put_info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tolkar en binär resurs data-BLOB för att fylla i en matris med GX_LANGUAGE_HEADER strukturer, som informerar programmet om språk namn och sträng tabell storlek för varje språk som ingår i binära data. Programmet bör först anropa gx_binres_language_count_get () för att fastställa antalet språk i binära data och kontrol lera att put_infos pekaren som skickades till den här funktionen pekar till en matris med language_count GX_LANGUAGE_HEADER strukturer.

Den här tjänsten används av programmet för att fastställa vid körning av innehållet i ett binärt resurs data segment.

GX_LANGUAGE_HEADERs strukturen definieras som:

```c
typedef struct GX_LANGUAGE_HEADER_STRUCT{
    USHORT gx_language_header_magic_number;
    USHORT gx_language_header_index;
    UCHAR gx_language_header_name[GX_LANGUAGE_HEADER_NAME_SIZE];
    ULONG  gx_language_header_data_size;
} GX_LANGUAGE_HEADER;
```

- Fältet *magic_number* används för intern verifiering av data formatet Binary-resurs.
- I fältet *header_index* anges i vilken ordning språken definieras i binära data.
- Fältet *header_name* innehåller språk namnet.
- Fältet *header_data_size* innehåller data storleken för språk sträng tabellen.

### <a name="parameters"></a>Parametrar

- **root_address** Adress till binära resurs data i minnet
- **put_info** Pekare till matrisen med GX_LANGUAGE_HEADER strukturer

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_FORMAT** (0X24) ogiltig binär resurs
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_LANGUAGE_HEADER language_info[4];

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_info_load(root_address,
    language_info);
/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Se även

- gx_binres_language_count_get

## <a name="gx_binres_language_table_load"></a>gx_binres_language_table_load

Läs in språk tabell resurs (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_table_load(
    GX_UBYTE *root_address, 
    GX_UBYTE **returned_language_table);
```

### <a name="description"></a>Beskrivning

Detta inaktuella API gör det möjligt för program att läsa in sträng tabell data från äldre (före version 5,6) av data för binärfiler för binärfiler.

Nya program bör använda gx_binres_language_table_load_ext ().

Den här tjänsten bygger upp en språk tabell struktur som innehåller pekare till tabell resurser, de genererade data strukturerna pekar på resurs data "på plats" och kopierar inte resurs data. Resurs data måste placeras på en allmän åtkomst till minnes platsen och bas adressen för den här minnes platsen skickas till detta API.

Den här tjänsten kräver ett runtime-allokerat minnes block som är tillräckligt stort för att rymma språk tabell strukturen, och därför måste gx_system_memory_allocator_set-API: et anropas en gång innan tjänsten begärs.

Den returnerade språk tabellen definierar en eller flera sträng tabeller, varje sträng tabell som innehåller pekare till sträng resurser i resurs data minnet.

### <a name="parameters"></a>Parametrar

- **root_address** Adress till binära resurs data i minnet
- **returnerade _language_table** Pekare till inläst språk tabell

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_FORMAT** (0X24) ogiltig binär resurs
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_SYSTEM_MEMPRY_ERROR** (0X30) minnes uppallokerare eller kostnads fri funktion har inte definierats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_UBYTE ***language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load(root_address,
                                        &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Se även

- gx_binres_language_table_load_ext

## <a name="gx_binres_language_table_load_ext"></a>gx_binres_language_table_load_ext

Läs in språk tabell resurs

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_table_load_ext(
    GX_UBYTE *root_address, 
    GX_STRING **returned_language_table);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bygger upp en språk tabell struktur som innehåller pekare till tabell resurser, de genererade data strukturerna pekar på resurs data "på plats" och kopierar inte resurs data. Resurs data måste placeras på en allmän åtkomst till minnes platsen och bas adressen för den här minnes platsen skickas till detta API.

Den här tjänsten kräver ett runtime-allokerat minnes block som är tillräckligt stort för att rymma språk tabell strukturen, och därför måste gx_system_memory_allocator_set-API: et anropas en gång innan tjänsten begärs.

Den returnerade språk tabellen definierar en eller flera sträng tabeller, varje sträng tabell som innehåller pekare till sträng resurser i resurs data minnet.

### <a name="parameters"></a>Parametrar

- **root_address** Adress till binära resurs data i minnet
- **returnerade _language_table** Pekare till inläst språk tabell

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_FORMAT** (0X24) ogiltig binär resurs
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_SYSTEM_MEMPRY_ERROR** (0X30) minnes uppallokerare eller kostnads fri funktion har inte definierats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING **language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load_ext(root_address,
                                            &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Se även

- gx_binres_theme_load

## <a name="gx_binres_theme_load"></a>gx_binres_theme_load

Läs in tema resurs

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_theme_load(
    GX_UBYTE *root_address, 
    INT theme_id, GX_THEME **returned_theme);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bygger upp en GX_THEME-struktur som innehåller pekare till resurs tabellerna för det begärda temat. De skapade data strukturerna pekar på resurs data "på plats", den kopierar inte resurs data. Resurs data måste placeras på en allmän åtkomst till minnes platsen och bas adressen för den här minnes platsen skickas till detta API.

Den här tjänsten kräver ett runtime-allokerat minnes block som är tillräckligt stort för att rymma tema tabell strukturen, och därför måste gx_system_memory_allocator_set-API: et anropas en gång innan tjänsten begärs.

### <a name="parameters"></a>Parametrar

- **root_address** Adress till binära resurs data i minnet
- **theme_id** Identifieraren för temat
- **returned_theme** Pekare till inläst tema

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades
- **GX_INVALID_FORMAT** (0X24) ogiltig binär resurs
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt tema-ID
- **GX_SYSTEM_MEMORY_ERROR** (0X30) minnes uppallokerare eller kostnads fri funktion har inte definierats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *theme = GX_NULL;
GX_UBYTE *root_address = 0x60000000;
INT theme_id = 0;

status = gx_binres_theme_load(root_address, theme_id, &theme);

/* If status is GX_SUCCESS, the theme was successfully loaded. */
```

### <a name="see-also"></a>Se även

- gx_binres_language_table_read

## <a name="gx_brush_default"></a>gx_brush_default
Ange standard penseln

### <a name="prototype"></a>Prototyp

```C
UINT gx_brush_default(GX_BRUSH *brush);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger penseln för den aktuella kontexten till systemets standardvärde.

### <a name="parameters"></a>Parametrar
- **pensel** Pekare till pensel kontroll block.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) pensel definition
- **GX_PTR_ERROR** (0X07) ogiltig pensel pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/*Reset the brush to its default value. */
status = gx_brush_default(&my_brush);

/* If status is GX_SUCCESS the brush was successfully reset to its default value. */

```

### <a name="see-also"></a>Se även

- gx_brush_define


## <a name="gx_brush_define"></a>gx_brush_define
Definiera pensel

### <a name="prototype"></a>Prototyp

```C
UINT gx_brush_define(
    GX_BRUSH *brush, 
    GX_COLOR line_color, 
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar en pensel med den angivna linje färgen, fyllnings färg och format.

### <a name="parameters"></a>Parametrar

- **pensel** Pekare till pensel kontroll block
- **line_color** Färg på pensel linje. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **fill_color** Färg på pensel fyllning. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **stil** Pensel format. **Bilaga D** beskriver de pensel format som stöds. Pensel format kan kombineras till en variabel med hjälp av bitvis OR operation.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) pensel definition
- **GX_PTR_ERROR** (0X07) ogiltig pensel pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define a brush. */
status = gx_brush_define(&my_brush, GX_COLOR_BLACK, GX_COLOR_BLACK,
                         GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush was successfully created. */
```

### <a name="see-also"></a>Se även

- gx_brush_default

## <a name="gx_button_background_draw"></a>gx_button_background_draw

 Knapp bakgrund för Draw

###<a name="prototype"></a>Prototyp

```C
VOID gx_button_background_draw(GX_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar knapp bakgrunden. Den här funktionen anropas vanligt vis internt av funktionen gx_button_draw, men exponeras för programmet för att hjälpa till med att skriva anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knapp kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Draw button background. */
    gx_button_background_draw(button);

    /* Add custom drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)button);
}
```

### <a name="see-also"></a>Se även

- gx_button_create,
- gx__button_deselect,
- gx__button_draw
- gx_button_event_process,
- gx__button_select
- gx_icon_button_create,
- gx__pixelmap_button_create
- gx_pixelmap_button_draw,
- gx__radio_button_create
- gx_radio_button_draw,
- gx__text_button_create
- gx_text_button_color_set,
- gx__text_button_draw

## <a name="gx_button_create"></a>gx_button_create

Knappen Skapa

### <a name="prototype"></a>Prototyp

```C
UINT gx_button_create(
    GX_BUTTON *button, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style, 
    USHORT button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en knapp som anges och associerar knappen med den angivna överordnade widgeten.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knapp kontroll block
- **namn** Knappens logiska namn
- **överordnad** Pekare till överordnad widget för knappen
- **stil** Knapp format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **button_id** Programdefinierat ID för knappen
- **storlek** Knappens storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) knappen har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BUTTON my_top_button;

/* Create a stop button. */
status = gx_button_create(&my_stop_button, "my stop button",
                            &my_parent_window,
                            GX_STYLE_BUTTON_TOGGLE,
                            MY_STOP_BUTTON_ID, &size);

/* If status is GX_SUCCESS the stop button was successfully created. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw,
- gx_button_deselect,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_deselect"></a>gx_button_deselect


Knappen avmarkera

### <a name="prototype"></a>Prototyp

```C
UINT gx_button_deselect(
    GX_BUTTON *button, 
    GX_BOOL gen_event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten avmarkerar den angivna knappen och genererar en signal händelse beroende på knapp format.


| Knapp format              | Signal                     |
|---------------------------|----------------------------|
| Inget                      | GX_EVENT_CLICKED         |
| GX_STYLE_BUTTON_RADIO  | GX_EVENT_RADIO_DESELECT |
| GX_STYLE_BUTTON_TOGGLE | GX_EVENT_TOGGLE_OFF     |



### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knapp kontroll block
- **gen_event** Om GX_TRUE skapas en GX_EVENT_CLICKED, GX_EVENT_DESELECT eller GX_EVENT_TOGGLE_OFFSET händelse beroende på knapp formatet. Om GX_FALSE kommer knappen inte att generera händelser på högre nivå, även om den skulle göra det vanligt.

### <a name="return-values"></a>Retur värden

- Avmarkera knappen **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Deselect button. */
status = gx_button_deselect(&my_stop_button, GX_TRUE);

/* If status is GX_SUCCESS the stop button was successfully deselected. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw,
- gx_button_create,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_button_draw"></a>gx_button_draw

Knappen Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_button_draw(GX_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna knappen. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för widgetar anpassade knappar.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knapp kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom button draw function. */
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Call default button draw. */
    gx_button_draw(button);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>Se även

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_event_process"></a>gx_button_event_process


Händelse för process knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_button_event_process(
    GX_BUTTON *button, 
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna knappen.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knapp kontroll block
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) knapp händelse process
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic button event processing as part of custom event processing function. */

UINT custom_button_event_process(GX_BUTTON *button,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default button
            event processing */
        status = gx_button_event_process(button, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_select"></a>gx_button_select

Knappen Välj

### <a name="prototype"></a>Prototyp

```C
UINT gx_button_select(GX_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten väljer den angivna knappen och genererar en signal händelse beroende på knapp format.

Avmarkerar på samma nivå för en alternativ knapps grupp.

| Knapp format                       | Signal                   |
|------------------------------------|--------------------------|
| GX_STYLE_BUTTON_RADIO           | GX_EVENT_RADIO_SELECT |
| GX_STYLE_BUTTON_EVENT_ON_PUSH | GX_EVENT_CLICKED       |
| GX_STYLE_BUTTON_TOGGLE          | GX_EVENT_TOGGLE_ON    |


### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knapp kontroll block

### <a name="return-values"></a>Retur värden

- Klicka på knappen **GX_SUCCESS** (0X00) lyckades
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Select button. */
status = gx_button_select(&my_stop_button);

/* If status is GX_SUCCESS the stop button was successfully selected. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_event_process
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_canvas_alpha_set"></a>gx_canvas_alpha_set

Ange alfa-Blend-värde för arbets yta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_alpha_set(
    GX_CANVAS *canvas, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger alfa-Blend-värdet för den angivna arbets ytan. Arbets ytans alfa värden kan vara mellan 0 (transparent) och 255 (helt ogenomskinlig).

För att blanda överlägg arbets ytor krävs antingen maskinvaru-eller program varu stöd genom att skapa en sammansatt arbets yta.

Maskin varu stöd för kombination av arbets ytor är aktiverat genom att anropa API: et för gx_canvas_hardware_layer_bind () innan du anger arbets ytans alfa värde. När en arbets yta är kopplad till ett maskin varu lager, anropar API: et för gx_canvas_alpha_set () direkt maskin varans grafik lagers blandnings tjänster.

För att kunna använda program varu stöd för arbets ytans blandning måste programmet skapa en arbets yta med GX_CANVAS_COMPOSITE format där alla andra hanterade arbets ytor kombineras före den slutliga visningen. Program varu stöd för arbets ytans blandning tillhandahålls endast när det körs med en visnings driv rutin med 16 BPP eller högre färgdjup.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **alpha** Alfa-Blend-värde, sträcker sig från 0 (transparent) till 255 (ogenomskinligt).

### <a name="return--values"></a>Retur värden

- **GX_SUCCESS** (0X00) godkänd alpha-Blend-värde uppsättning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_ERROR** (0X20) ogiltig arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the alpha-blend value of “my_canvas”. */
status = gx_canvas_alpha_set(&my_canvas, GX_ALPHA_VALUE_OPAQUE);

/* If status is GX_SUCCESS the alpha-blend value was successfully set. */
```

### <a name="see-also"></a>Se även

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_arc_draw"></a>gx_canvas_arc_draw

Rita båge

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_arc_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r,
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en cirkel båge på arbets ytan med den aktuella penseln. Cirkel bågen klipps till arbets ytans ogiltiga region. Den här tjänsten kräver att GX_ARC_DRAWING_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-position för cirkel båge
- **YCenter** y-position för cirkel båge
- **r** -radien för cirkelns båge
- **start_angle** Cirkel bågens start vinkel
- **end_angle** Cirkel bågens slut vinkel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ritad båge
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0X22) ogiltigt värde
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Draw a circle arc from 0 degree to 90 degree in clockwise. */
status = gx_canvas_arc_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the arc has been drawn on “my_canvas”. */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move,
- gx_canvas_circle_draw
- gx_display_create,
- gx_canvas_ellipse_draw
- gx_canvas_line_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_block_move"></a>gx_canvas_block_move

Flytta block med arbets ytans pixlar

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_block_move(GX_RECTANGLE *block,
    GX_VALUE x_shift, GX_VALUE y_shift, GX_RECTANGLE *dirty);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar ett block med pixel data för arbets ytor i den angivna riktningen. Den här tjänsten används internt av GUIX för att utföra snabb rullning, men kan även användas av program varan.

### <a name="parameters"></a>Parametrar

- **blockera** Koordinater för området som ska flyttas
- **x_shift** Antal pixlar att flytta till x-axeln
- **y_shift** Antal pixlar att flytta längs y-axeln
- **smutsig** Om block flyttningen lyckas returnerar den här funktionen den del av käll rektangeln som fortfarande är smutsig till anroparen i den här parametern.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd block flyttning
- **GX_FAILURE** (0X10) Det gick inte att flytta blocket
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
GX_RECTANGLE invalid;
GX_RECTANGLE move;

/* define 100 x 100 pixel rectangle */
gx_utility_rectangle_define(&move, 0, 0, 99, 99);

/* Move this rectangle 10 pixels to the right”. */
status = gx_canvas_block_move(&move, 10, 0, &invalid);

/* If status is GX_SUCCESS, then ‘invalid’ marks the area that needs to be redrawn after the block move. */

```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_circle_draw"></a>gx_canvas_circle_draw

Rita cirkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_circle_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en cirkel på arbets ytan med hjälp av den aktuella penseln. Cirkeln klipps till arbets ytans ogiltiga region. Den här tjänsten kräver att GX_ARC_DRAWING_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-Coord i mitten av cirkeln
- **YCenter** y – Coord i mitten av cirlce
- **r** -radien för cirkeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) cirkel rit
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0X22) ogiltig cirkel-radie
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C

/* Draw a circle of radius 10 centered at (100, 100). */
status = gx_canvas_circle_draw(100, 100, 50);

/* If status is GX_SUCCESS the circle has been drawn on “my_canvas”. */

```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw


## <a name="gx_canvas_create"></a>gx_canvas_create

Skapa arbets yta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_create(
    GX_CANVAS *canvas, 
    GX_CONST GX_CHAR *name,
    GX_DISPLAY *display, 
    UINT type, 
    UINT width, 
    UINT height,
    GX_COLOR *memory_area, 
    ULONG memory_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar arbets ytan med de angivna egenskaperna och det tillhör ande minnet.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **namn** Logiskt namn för arbets ytan
- **Visa** Pekare till visning som skapats tidigare
- **typ** Typ av canvasThe arbets ytans typer är:
- **GX_CANVAS_SIMPLE:** En minnes arbets yta som används för att rita på skärmen.
- **GX_CANVAS_MANAGED:** En arbets yta som automatiskt töms på den aktiva visningen, antingen som en del av den sammansatta skapande processen eller som en del av växlings åtgärden för en enskild arbets yta.
- **GX_CANVAS_VISIBLE:** Den här flaggan kan användas för att aktivera och inaktivera en arbets yta utan att förlora ritnings innehållet i arbets ytan.
- **GX_CANVAS_MODIFIED:** Reserverad för framtida användning.
- **GX_CANVAS_COMPOSITE:** Den här flaggan används av programmet när du konfigurerar ett system med flera arbets ytor som sammanfattar flera hanterade arbets ytor i den sammansatta arbets ytan och den sammansatta enheten är driven för maskin varu Rams bufferten.
- **Bredd** Bredd i bild punkter
- **höjd** Höjd i bild punkter
- **memory_area** Minnes område för arbets yta. Det här värdet kan
- **GX_NULL** när arbets ytan skapas
- **och** senare initieras med hjälp av gx_canvas_memory_define
- **memory_size** Storleken på minnes området i byte, eller 0 om arbets ytans minne ska definieras efter att arbets ytan har skapats.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) skapa arbets yta skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_CANVAS_SIZE** (0X1C) ogiltig block storlek för kontroll av arbets yta
- **GX_INVALID_TYPE** (0X1B) ogiltig typ av arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define global canvas memory area. */
GX_COLOR my_canvas_memory[272*480];

…

/* Create “my_canvas”. */
status = gx_canvas_create(&my_canvas, "my canvas", &my_display,
                    (GX_CANVAS_MANAGED | GX_CANVAS_VISIBLE),
                    272, 480,
                    my_canvas_memory,
                    sizeof(default_canvas_memory));

/* If status is GX_SUCCESS the 272 x 480 canvas was successfully created. */
```

### <a name="see-also"></a>Se även

- gx_canvas_delete,
- gx_canvas_hardware_layer_bind
- gx_canvas_memory_define

## <a name="gx_canvas_delete"></a>gx_canvas_delete

Ta bort arbets yta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_delete(GX_CANVAS *canvas);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort arbets ytan. Arbets ytan tas bort från den interna länkade listan över arbets ytor som underhålls av GUIX.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) skapa arbets yta skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete “my_canvas”. */
status = gx_canvas_delete (&my_canvas);

/* If status is GX_SUCCESS my_canvas was deleted. */
```

### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_drawing_complete"></a>gx_canvas_drawing_complete

Slutför ritning av arbets yta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_drawing_complete(
    GX_CANVAS *canvas, 
    GX_BOOL flush);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör att GUIX vet att programmets ritning på den angivna arbets ytan är klar.

Programmet kan använda den här tjänsten för att tvinga fram en omedelbar ritning till en arbets yta. Detta tömmer arbets ytan till den synliga inramade bufferten och/eller utlöser en Bugger växlings åtgärd, beroende på system minnes arkitektur.

Den här tjänsten ska endast anropas av programmet för att stänga en ritnings sekvens som påbörjades med gx_canvas_drawing_initiate ().

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **Rensa** Om **_GX_TRUE_** rensas arbets ytans ändringar till visningen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) slutfördes ritningen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Complete drawing on “my_canvas” and flush to display. */
status = gx_canvas_drawing_complete(&my_canvas, GX_TRUE);

/* If status is GX_SUCCESS the canvas drawing was successfully completed. */
```


### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift

## <a name="gx_canvas_drawing_initiate"></a>gx_canvas_drawing_initiate

Starta arbets ytans ritning

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_drawing_initiate(
    GX_CANVAS *canvas,
    GX_WIDGET *who, 
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar ritningen på den angivna arbets ytan. Den här tjänsten kallas internt som en del av den uppskjutna ritnings åtgärden som utförs automatiskt av GUIX när en arbets yta måste uppdateras. Programmet tillåts dock inte kringgå GUIX och utföra omedelbar och direkt ritning på en arbets yta genom att först anropa gx_canvas_drawing_inititate och sedan anropa de önskade rit funktionerna och sedan anropa gx_canvas_drawing_complete ().

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **vem som** Pekare till kontroll block för widgeten för anroparen. Den här parametern används för att initiera rit urklippet och Visa parametrar för efterföljande ritnings åtgärder.
- **dirty_area** Yta att rita inom. Den här parametern skickas av anroparen för att ange det utrymme som anroparen vill att alla ritnings åtgärder ska ha. Detta är vanligt vis det områden som tidigare marker ATS som smutsig, men anroparen är kostnads fri att expandera eller dra samman det.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad ritnings initiering
- **GX_DRAW_NESTING_EXCEEDED** (0X05) överskrider maximalt antal kapslingar
- **GX_NO_VIEW** (0X03) inga visnings område för anroparen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Initiate drawing on “my_canvas”, my_widget.gx_widget_size
specify the area the application wants GUIX to redraw. */
status = gx_canvas_drawing_initiate(&my_canvas, &my_widget,
    &my_widget.gx_widget_size);

/* If status is GX_SUCCESS the canvas drawing was successfully initiated. */
```

### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_offset_set
- gx_canvas_shift


## <a name="gx_canvas_ellipse_draw"></a>gx_canvas_ellipse_draw

Rita ellips

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_ellipse_draw(
    INT xcenter, 
    INT ycenter, 
    INT a, 
    dINT b);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en ellips på arbets ytan med den aktuella penseln. Ellipsen klipps till arbets ytans ogiltiga region. Den här tjänsten kräver att GX_ARC_DRAWING_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-Coord i mitten av ellipsen
- **YCenter** y-Coord i mitten av ellipsen
- **en** längd på halv huvud axeln
- **b:s** längd på halv dels axeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) cirkel rit
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0X22) ogiltigt värde
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Draw an ellipse of semi-major radius 100, semi-minor radius 50
    and centered at (200, 200). */
status = gx_canvas_ellipse_draw(200, 200, 100, 50);

/* If status is GX_SUCCESS the ellipse has been drawn on
    “my_canvas”. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_hardware_layer_bind"></a>gx_canvas_hardware_layer_bind

Binda arbets ytan till maskin varu grafik lagret

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_hardware_layer_bind(
    GX_CANVAS *canvas, 
    INT layer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten binder en GUIX arbets yta till ett maskin varu grafik lager. Den här tjänsten krävs bara för maskin varu enheter som stöder flera maskinvarubaserade grafik lager.

Att binda en arbets yta till ett maskin varu grafik lager resulterar i att API: erna gx_canvas_show (), gx_canvas_hide (), gx_canvas_alpha_set () och gx_canvas_offset_set () implementeras direkt av maskin varans visnings driv rutins tjänster.

Om maskin varans bildskärms driv rutin inte stöder flera grafik lager kommer den här tjänsten inte att returnera GX_INVALID_DISPLAY.

### <a name="parameters"></a>Parametrar

- **arbets** ytans arbets yta som ska implementeras i maskin vara
- **lager** för maskin varu grafik

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd bindning
- Visnings skikts tjänsten för **GX_INVALID_DISPLAY** (0x1D) har inte definierats
- **GX_PTR_ERROR** (0X17) ogiltiga pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta
- **GX_NOT_SUPPORTED** (0x28) stöds inte

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Binds the canvas to the hardware graphics layer 1. */
status = gx_canvas_hardware_layer_bind(&my_canvas, 1);

/* If status is GX_SUCCESS, the drawing canvas is bound to the
    hardware graphics. */
```

### <a name="see-also"></a>Se även

- gx_canvas_create,
- gx_canvas_memory_define

## <a name="gx_canvas_hide"></a>gx_canvas_hide

Dölja en arbets yta, vilket gör den osynlig

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Beskrivning

Den här tjänsten döljer en GUIX-arbetsyta. Om arbets ytan har bundits till ett maskin varu grafik lager med hjälp av gx_canvas_hardware_layer_bind () implementeras tjänsten med hjälp av maskin varu support.

### <a name="parameters"></a>Parametrar

- **arbets** ytan som ska döljas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades dölja
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta
- **GX_PTR_ERROR** (0X17) ogiltiga pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Make my_canvas invisible. */
status = gx_canvas_hide(&my_canvas);

/* If status is GX_SUCCESS, the canvas has been hidden. */

```

### <a name="see-also"></a>Se även

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_line_draw"></a>gx_canvas_line_draw

Rita linje

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_line_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_VALUE x_end, 
    GX_VALUE y_end);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en linje på arbets ytan med hjälp av den aktuella penseln. Raden klipps till arbets ytans ogiltiga region.

### <a name="parameters"></a>Parametrar

- **x_start** Start x – position för raden
- **y_end** Start y-position för raden
- **x_start** Slut på x-position för raden
- **y_end** Avslutande y-position för raden

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) linje rit
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten
- **GX_INVALID_WIDTH** (0X1E) ogiltig pensel bredd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Draw line on canvas. */
status = gx_canvas_line_draw(0, 1, 320, 480);

/* If status is GX_SUCCESS, the line has been drawn to canvas. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_memory_define"></a>gx_canvas_memory_define

Definiera arbets ytans minne

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_memory_define(
    GX_CANVAS *canvas, 
    GX_COLOR *memory,
    ULONG memsize);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kan användas för att tilldela arbets ytans minnes adress när arbets ytan har skapats.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till en tidigare skapad arbets yta
- **minne** Minnes adress för arbets ytan
- **memsize** Storlek på arbets ytans minnes block i byte

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd tilldelning
- **GX_INVALID_CANVAS** (0X20) ogiltigt kontroll block
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assign canvas memory block. */
status = gx_canvas_memory_define(canvas,
    (GX_COLOR *) DRAM_MEMORY,
    (640 * 480 * 2));

/* If status is GX_SUCCESS, the canvas memory pointer has be
reassigned. */

```

### <a name="see-also"></a>Se även

- gx_canvas_create,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_mouse_define"></a>gx_canvas_mouse_define

Definiera mus markörens bild

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_mouse_define(GX_CANVAS *canvas,
    GX_MOUSE_CURSOR_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar mus information för den angivna arbets ytan. Den här tjänsten kräver att GX_MOUSE_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **information** Pekare till mus markör information. **Bilaga i** innehåller en definition för GX_MOUSE_CURSOR_INFO-strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) konfigurations information för lyckad mus
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set mouse cursor info. */
GX_MOUSE_CURSOR_INFO mouse_cursor;
mouse_cursor.gx_mouse_cursor_image_id = GX_PIXELMAP_ID_MOUSE;
mouse_cursor.gx_mouse_cursor_hotspot_x = 0;
mouse_cursor.gx_mouse_cursor_hotspot_y = 0;

status = gx_canvas_mouse_define(&my_canvas, &mouse_cursor);

/* If status is GX_SUCCESS the mouse info of “my_canvas” has been
set successfully. */

```

### <a name="see-also"></a>Se även

- gx_canvas_mouse_show,
- gx_canvas_mouse_hide

## <a name="gx_canvas_mouse_hide"></a>gx_canvas_mouse_hide


Inaktivera mus markören

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_mouse_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör mus markören dold från den angivna arbets ytan. Den här tjänsten kräver att GX_MOUSE_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) mus markören är dold
- **GX_FAILURE** (0X10) Det gick inte att dölja mus markören
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen


### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Hide the mouse cursor. */
status = gx_canvas_mouse_hide(&my_canvas);

/* If status is GX_SUCCESS the mouse cursor of “my_canvas” has been
hidden successfully. */

```

### <a name="see-also"></a>Se även

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_mouse_show"></a>gx_canvas_mouse_show


Aktivera mus markören

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_mouse_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör mus markören synlig för den angivna arbets ytan. Den här tjänsten kräver att GX_MOUSE_SUPPORT definieras. Gx_canvas_mouse_define API ska anropas för att definiera markörens bild innan den begärda tjänsten begärs.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) konfigurations information för lyckad mus
- **GX_FAILURE** (0X10) Det gick inte att Visa mus markören
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Make mouse cursor hidden ”. */
status = gx_canvas_mouse_show(&my_canvas);

/* If status is GX_SUCCESS the mouse of “my_canvas” has been
hidden successfully. */
```

### <a name="see-also"></a>Se även

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_offset_set"></a>gx_canvas_offset_set


Tilldela arbets yta x, y Visa förskjutning

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_offset_set(
    GX_CANVAS *canvas,
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en förskjutning i x-y-skärmen för den angivna arbets ytan. Detta styr den position där arbets ytan sammansatts i den synliga inramade bufferten och används ofta när arbets ytan är mindre än den fysiska visningen.

Om arbets ytan har bundits till ett maskin varu grafik lager med hjälp av API: et gx_canvas_hardware_layer_bind () implementeras tjänsten gx_canvas_offset_set direkt med hjälp av maskin varu support.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **x** x-koordinat för förskjutning
- **y** y-koordinat för förskjutning

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) tilldelning av förskjutning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set display offset for “my_canvas”. */
status = gx_canvas_offset_set(&my_canvas, 20, 30);

/* If status is GX_SUCCESS the canvas drawing is now offset from
position 20,30. */
```

### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift
- gx_canvas_show,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_pie_draw"></a>gx_canvas_pie_draw


Rita cirkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pie_draw(
    INT xcenter, 
    INT ycenter,
    UINT r, 
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar ett cirkel diagram i arbets ytan med den aktuella rit kontextens pensel. Cirkeln klipps till arbets ytans ogiltiga region. Den här tjänsten kräver att konfigurations alternativet GX_ARC_DRAWING_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-position för cirkeln
- **YCenter** y-position i cirkelns mitt punkt
- **r** -radien för cirkeln
- **start_angle** Cirkelns start vinkel
- **end_angle** Cirkelns slut vinkel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ritad båge
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0X22) ogiltigt värde
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw a pie from 0 degree to 90 degree in clockwise. */
status = gx_canvas_pie_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the pie has been drawn to canvas. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_pixel_draw"></a>gx_canvas_pixel_draw


Rita bild punkt

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixel_draw(GX_POINT position);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en pixel på arbets ytan med linje färgen för den aktuella rit kontextens pensel. Om konfigurations alternativet GX_BRUSH_ALPHA_SUPPORT definierats, ska du blanda pixeln med annars ritar du pixeln som helt ogenomskinlig.

- **punkt** x, y position för bild punkt att rita

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Pixelmap Draw
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_POINT point; /* the x,y position you want to draw to */
GX_RECTANGLE drawto; /* the rectangle bounding your drawing */
GX_CANVAS *mycanvas; /* the canvas you want to draw to */

/* calculate 1x1 pixel drawing area: */
gx_utility_rectangle_define(&drawto,
    point.gx_point_x, point.gx_point_y,
    point.gx_point_x, point.gx_point_y);

/* get my canvas: */
gx_widget_canvas_get(win, &mycanvas);

/* open my canvas for drawing: */
gx_canvas_drawing_initiate(mycanvas, win, &drawto);

/* setup my brush colors. Use any color ID in your resources: */
gx_context_line_color_set(GX_COLOR_ID_WINDOW_BORDER);

/* draw a pixel: */
status = gx_canvas_pixel_draw(point);

/* close the canvas: */
gx_canvas_drawing_complete(mycanvas, GX_TRUE);

/* If status is GX_SUCCESS, the pixel was successfully drawn to mycanvas. */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_blend"></a>gx_canvas_pixelmap_blend

Blanda Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_blend(
    GX_VALUE x_position,
    GX_VALUE y_position, 
    GX_PIXELMAP *pixelmap, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Beskrivning

Den här tjänsten blandar en Pixelmap med arbets ytans bakgrund. Blandnings förhållandet anges av anroparen. Alfa värdet kan vara från 0 (helt transparent) till 255 (helt ogenomskinligt). Pixelmap kan också innehålla en intern alfa kanal, som kombineras med det inkommande blandning svärdet. Den här tjänsten stöds endast av visnings driv rutiner som körs med 16-BPP färgdjup och högre.

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-position för Pixelmap
- **y_end** Start y-position för Pixelmap
- **Pixelmap** Pekare till Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Pixelmap Draw
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_NOT_SUPPORTED** (0x28) stöds inte
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;
gx_system_pixelmap_get(ID_MY_PIXELMAP, &map);

status = gx_canvas_pixelmap_blend(10, 20, map, 128);

/* If status is GX_SUCCESS the pixelmap has been blended onto the current canvas. */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_draw"></a>gx_canvas_pixelmap_draw

Rita Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_draw(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en Pixelmap på arbets ytan.

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-position för Pixelmap
- **y_end** Start y-position för Pixelmap
- **Pixelmap** Pekare till Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Pixelmap Draw
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw pixelmap on canvas. */
status = gx_canvas_pixelmap_draw(10, 20, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_get"></a>gx_canvas_pixelmap_get

Hämta arbets ytans Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_get(GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar en GX_PIXELMAP-struktur som pekar på arbets ytans data. Pixelmap-formatet anges till det aktuella visnings färg formatet.

### <a name="parameters"></a>Parametrar

- **Pixelmap** Returnerade Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Pixelmap get
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;

status = gx_canvas_pixelmap_get(map);

/* If status is GX_SUCCESS the pixelmap has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_rotate"></a>gx_canvas_pixelmap_rotate


Rita roterat Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_rotate(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap, 
    INT angle,
    INT rot_cx, 
    INT rot_cy);
```

### <a name="description"></a>Beskrivning

Den här tjänsten roterar en Pixelmap vid den angivna vinkeln och återger Pixelmap till arbets ytan direkt när rotationen utförs. Den här tjänsten skiljer sig från gx_utility_pixelmap_rotate i att resultatet av rotationen direkt återges till arbets ytans minne och det roterade Pixelmap inte returneras till anroparen.

Fördelen med den här tjänsten över gx_utility_pixelmap_rotate är att det inte krävs ytterligare minne för att rymma det roterade Pixelmap. Nack delen är att rotations koden måste köras varje gången Pixelmap ritas.

Verifiering av Urklipp och visnings område framtvingas under åter givning av roterade Pixelmap.

### <a name="parameters"></a>Parametrar

- **x_position** Starta x-position för Pixelmap
- **y_position** Start y-position för Pixelmap
- **Pixelmap** Pekare till Pixelmap
- **vinkel** Vinkel för rotation
- **rot_cx** X – Coord av rotations centrum. Om det här värdet är inställt på-1 används mitten av bilden som rotations Center.
- **rot_cy** Y-Coord av rotations centrum. Om det här värdet är inställt på-1 används mitten av bilden som rotations centrum.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Pixelmap Draw
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* rotate “src_pixelmap” by 30 degree in clockwise direction and draw in on canvas. */
status = gx_canvas_pixelmap_rotate(10, 20, &my_pixelmap, 30,
    -1, -1);

/* If status is GX_SUCCESS the rotated pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile,
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_tile"></a>gx_canvas_pixelmap_tile

Panel Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_tile(
    GX_RECTANGLE *fill,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten fyller en rektangel på en arbets yta med den begärda Pixelmap.

### <a name="parameters"></a>Parametrar

- **Fyll** Yta som ska panelas med Pixelmap
- **Pixelmap** Pekare till Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap-panel
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten
- **GX_INVALID_VALUE** (0X22) ogiltig fyllnings storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Tile pixelmap on canvas */
status = gx_canvas_pixelmap_tile(&tile_area, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been tiled on canvas */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_polygon_draw"></a>gx_canvas_polygon_draw


Rita polygon

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_polygon_draw(
    GX_POINT *point_array,
    INT number_of_points);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en polygon på arbets ytan med den aktuella rit kontextens pensel.

### <a name="parameters"></a>Parametrar

- **point_array** Matris med punkter i polygonen
- **number_of_points** Antal punkter i polygonen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ritad polygon
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_POINT my_polygon[4] =
{
    { 208, 63 },
    { 274, 63 },
    { 274, 163 },
    { 208, 163 }
};

/* Draw polygon “my_polygon” on canvas. */
status = gx_canvas_polygon_draw(&my_polygon, 4);

/* If status is GX_SUCCESS the polygon “my_polygon” has been drawn. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rectangle_draw"></a>gx_canvas_rectangle_draw


Rita rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_rectangle_draw(GX_RECTANGLE *rectangle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en rektangel på arbets ytan.

### <a name="parameters"></a>Parametrar

- **rektangel** Rektangel att rita

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ritad rektangel
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw rectangle “my_rectangle” on canvas. */
status = gx_canvas_rectangle_draw(&my_rectangle);

/* If status is GX_SUCCESS the rectangle “my_rectangle” has been drawn. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rotated_text_draw"></a>gx_canvas_rotated_text_draw


Rita text roterad om en mitt punkt (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_rotated_text_draw(
    const GX_CHAR *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Beskrivning

Detta API har ersatts av prioriterad eller gx_canvas_rotated_text_draw_ext (). Även om det fortfarande stöds bör nya program inte använda detta API och bör istället använda gx_canvas_rotated_text_draw_ext ().

Den här tjänsten ritar text till arbets ytan. Texten roteras om den begärda mitt punkten. Det aktuella rit kontexts teckensnittet och den ritade kontext linje färgen används för att återge texten.

Den här tjänsten använder funktionen gx_utility_string_to_alphamap för att rendera text strängen till en tillfällig 8bpp-Pixelmap som bara innehåller ett alfa värde. Tjänsten roterar sedan AlphaMap med hjälp av funktionen gx_utility_pixelmap_rotate. När den sista AlphaMap har Render ATS till arbets ytan, frigör tjänsten den temporära AlphaMap och det tillhör ande minnet.

Eftersom en tillfällig AlphaMap krävs för att återge roterad text måste programmet Konfigurera gx_system_memory_allocator av anrops gx_system_memory_allocator_set ()-API: et innan du försöker Rita roterad text.

Den här tjänsten bör endast användas för att rendera roterad text "en tid". Om samma text sträng ska ritas flera gånger på olika platser eller olika rotations vinklar, är det mer effektivt att använda-funktionen gx_utility_string_to_alphamap () för att skapa texten AlphaMap en gång, och sedan använda gx_utility_pixelmap_rotate flera gånger för att rotera den resulterande AlphaMap upprepade gånger.

### <a name="parameters"></a>Parametrar

- **text** Text sträng som ska ritas
- **xCenter** Centrera positon runt vilken text som ska roteras.
- **yCenter** Mitt position runt vilken text som ska roteras.
- **vinkel** Den önskade text rotations vinkeln i grader.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text åter givning
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_SYSTEM_MEMORY_ERROR** (0X30) det finns inte tillräckligt med minne tillgängligt eller så har gx_system_memory_allocator inte tilldelats
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw(dynamic_text, xpos, ypos, 45);
}
```

### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_rotated_text_draw_ext"></a>gx_canvas_rotated_text_draw_ext


Rita text roterad om en mitt punkt

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_rotated_text_draw_ext(
    GX_CONST GX_STRING *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar text till arbets ytan. Texten roteras om den begärda mitt punkten. Det aktuella rit kontexts teckensnittet och den ritade kontext linje färgen används för att återge texten.

Den här tjänsten använder funktionen gx_utility_string_to_alphamap för att rendera text strängen till en tillfällig 8bpp-Pixelmap som bara innehåller ett alfa värde. Tjänsten roterar sedan AlphaMap med hjälp av funktionen gx_utility_pixelmap_rotate. När den sista AlphaMap har Render ATS till arbets ytan, frigör tjänsten den temporära AlphaMap och det tillhör ande minnet.

Eftersom en tillfällig AlphaMap krävs för att återge roterad text måste programmet Konfigurera gx_system_memory_allocator av anrops ***gx_system_memory_allocator_set*** -API: et innan du försöker Rita roterad text.

Den här tjänsten bör endast användas för att rendera roterad text "en tid". Om samma text sträng ska ritas flera gånger på olika platser eller olika rotations vinklar, är det mer effektivt att använda-funktionen gx_utility_string_to_alphamap () för att skapa texten AlphaMap en gång, och sedan använda gx_utility_pixelmap_rotate flera gånger för att rotera den resulterande AlphaMap upprepade gånger.

### <a name="parameters"></a>Parametrar

- **text** Text sträng som ska ritas
- **xCenter** Centrera positon runt vilken text som ska roteras.
- **yCenter** Mitt position runt vilken text som ska roteras.
- **vinkel** Den önskade text rotations vinkeln i grader.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text åter givning
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0X06) ogiltig rit kontext
- **GX_SYSTEM_MEMORY_ERROR** (0X30) det finns inte tillräckligt med minne tillgängligt eller så har gx_system_memory_allocator inte tilldelats.
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];
    GX_STRING string;

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    string.gx_string_ptr = dynamic_text;
    string.gx_string_length = strlen(dynamic_text);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw_ext(&string, xpos, ypos, 45);
}
```

### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_shift"></a>gx_canvas_shift


Shift-arbetsyta med x, y

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_shift(
    GX_CANVAS *canvas, 
    GX_VALUE x, GX_VALUE y);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skiftar den angivna arbets ytans förskjutning med den angivna mängden. Detta påverkar den position där arbets ytan återges inom den synliga bildens buffert.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket
- **x** pixlar till skift på x-axeln
- **y** -pixlar till skift på y-axeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) arbets ytans Skift
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Shift canvas “my_canvas”. */
status = gx_canvas_shift(&my_canvas, 10, 15);

/* If status is GX_SUCCESS the canvas has been shifted by 10 pixels
    on the X axis and 15 on the Y axis. */
```

### <a name="see-also"></a>Se även

- gx_canvas_drawing_complete,
- gx_canvas_initiate
- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_offset_set

## <a name="gx_canvas_show"></a>gx_canvas_show


Gör en arbets yta synlig

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör en arbets yta synlig. Om arbets ytan tidigare har bundits till ett maskin varu grafik lager med hjälp av API: et för gx_canvas_hardware_layer_bind () implementeras tjänsten gx_canvas_show () direkt med hjälp av maskin varu support.

### <a name="parameters"></a>Parametrar

- **arbets yta** Pekare till kontroll blocket

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) tilldelning av förskjutning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CANVAS** (0X20) ogiltig arbets yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Make this canvas visible. */
status = gx_canvas_show(&my_canvas);

/* If status is GX_SUCCESS the canvas drawing is now visible */
```

### <a name="see-also"></a>Se även

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_text_draw"></a>gx_canvas_text_draw

Rita text (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_text_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_CHAR *string, 
    INT length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar text på arbets ytan. Detta API, men stöds fortfarande, är föråldrat och nya program bör istället använda gx_canvas_text_draw_ext ().

### <a name="parameters"></a>Parametrar

- **x_start** Börjar x-koordinaten för text
- **y_start** Börjar y-koordinaten för text
- **sträng** Pekare till sträng att rita
- **längd** Om längden >= 0, begränsas antalet tecken som ritats till längd. Om längden < 0, ritas hela strängen fram till NULL-avslutning.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text rit
- **GX_FAILURE** (0X1E) misslyckades med att rita text
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw(10, 20, “example”, 7);

/* Draw all of a string of unknown length on the current canvas */
status = gx_canvas_text_draw(10, 40, string_ptr, -1);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_canvas_text_draw_ext"></a>gx_canvas_text_draw_ext


Rita text

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_text_draw_ext(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar text på arbets ytan.

### <a name="parameters"></a>Parametrar

- **x_start** Börjar x-koordinaten för text
- **y_start** Börjar y-koordinaten för text
- **sträng** Pekare till sträng att rita

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text rit
- **GX_FAILURE** (0X1E) misslyckades med att rita text
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Det går inte att öppna rit kontexten
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd
- **GX_INVALID_FONT** (0X16) ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING string;
string.gx_string_ptr = “example”;
string.gx_string_length = 7;

/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw_ext(10, 20, &string);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>Se även

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_checkbox_create"></a>gx_checkbox_create


Skapa kryss ruta

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_create(
    GX_CHECKBOX *checkbox, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT checkbox_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en CheckBox-widget med de angivna egenskaperna. GX_CHECKBOX härleds från GX_TEXT_BUTTON och alla gx_text_button tjänster kan användas med GX_CHECKBOX widgetar.

### <a name="parameters"></a>Parametrar

- **kryss ruta** Pekare till kryss rutan kontroll block namn logiskt namn för CheckBox-widget
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för kryss Rute text
- **stil** Typ av kryss ruta. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **checkbox_id** Programdefinierat ID för kryss ruta
- **storlek** Kryss rutans dimensioner

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00)-slutförd kryss ruta skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_checkbox”. */
status = gx_checkbox_create(&my_checkbox, “my_checkbox”,
    &my_parent,
    MY_CHECKBOX_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_CHECKBOX_ID,
    &size);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been created. */
```
### <a name="see-also"></a>Se även

- gx_checkbox_draw,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_draw"></a>gx_checkbox_draw

Rita kryss ruta

### <a name="prototype"></a>Prototyp

```C
VOID gx_checkbox_draw(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna kryss rutan. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för widgetar anpassade kryss rutor.

### <a name="parameters"></a>Parametrar

- **kryss ruta** Pekare för kontroll av kryss ruta

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom checkbox draw function. */
VOID custom_checkbox_draw(GX_CHECKBOX *checkbox)
{
    /* Call default checkbox draw. */
    gx_checkbox_draw(checkbox);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_checkbox_create,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_event_process"></a>gx_checkbox_event_process


Händelse för process kryss ruta

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_event_process(
    GX_CHECKBOX *checkbox, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna kryss rutan. Den här tjänsten ska anropas som standard händelse hanterare med en anpassad händelse bearbetnings funktion för kryss rutor.

### <a name="parameters"></a>Parametrar

- **kryss ruta** Pekare för kontroll av kryss ruta
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- Händelse process för **GX_SUCCESS** (0X00) slutförd kryss ruta
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic checkbox event processing as part of custom event processing function. */

UINT custom_checkbox_event_process(GX_CHECKBOX *checkbox,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default checkbox
            event processing */
        status = gx_checkbox_event_process(checkbox, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_select

## <a name="gx_checkbox_pixelmap_set"></a>gx_checkbox_pixelmap_set


Ange Pixelmap för kryss ruta

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_pixelmap_set(
    GX_CHECKBOX *checkbox,
    GX_RESOURCE_ID unchecked_id, 
    GX_RESOURCE_ID checked_id,
    GX_RESOURCE_ID unchecked_disabled_id, 
    GX_RESOURCE_ID checked_disabled_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar pixelmaps som ska visas av den angivna kryss rutan för varje kryss rutas tillstånd. Resurs-ID: n kan dupliceras.

### <a name="parameters"></a>Parametrar

- **kryss ruta** Pekare för kontroll av kryss ruta
- **unchecked_id** Pixelmap som används för avmarkerat tillstånd
- **checked_id** Pixelmap som används för markerat tillstånd
- **unchecked_disabled_id** Pixelmap som används för en inaktive rad och avmarkerad kryss ruta
- **checked_disabled_id** Pixelmap som används för en inaktive rad och markerad kryss ruta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kryss ruta har valt
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Select “my_checkbox”. */
status = gx_checkbox_pixelmap_set(&my_checkbox,
    PIXELMAP_UNCHECKED_ID,
    PIXELMAP_CHECKED_ID, PIXELMAP_UNCHECKED_DISABLED_ID,
    PIXELMAP_CHECKED_SIABLED_ID));

/* If status is GX_SUCCESS the pixelmaps are assigned to the checkbox “my_checkbox” */
```

### <a name="see-also"></a>Se även

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_checkbox_select"></a>gx_checkbox_select


Markera kryss ruta

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_select(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tvingar en CheckBox till det valda läget.

### <a name="parameters"></a>Parametrar

- **kryss ruta** Pekare för kontroll av kryss ruta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kryss ruta har valt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Select “my_checkbox”. */
status = gx_checkbox_select(&my_checkbox);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been toggled. */
```

### <a name="see-also"></a>Se även

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_circular_gauge_angle_get"></a>gx_circular_gauge_angle_get


Hämta aktuell vinkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_angle_get(
    GX_CIRCULAR_GAUGE *gauge, 
    INT *angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den aktuella Barr vinkeln för widgeten cirkulär mätare.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot cirkulär mätar kontroll block
- **vinkel** Aktuell nålventil som ska hämtas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades cirkulär mätar vinkeln get
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
INT current_angle;

/* Retrieve the current needle angle of “my_gauge”. */
status = gx_circular_gauge_angle_get(&my_gauge, &current_angle);

/* If status is GX_SUCCESS the current needle angle of “my_gauge” has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_set,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_angle_set"></a>gx_circular_gauge_angle_set


Ange mål vinkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_angle_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger mål vinkeln för en cirkulär mätar widget.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot cirkulär mätar kontroll block
- **vinkel** Mål träd vinkel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) angiven vinkel uppsättning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set target angle of “my_gauge” to 180. */
status = gx_circular_gauge_angle_set(&my_gauge, 180);

/* If status is GX_SUCCESS the circular gauge of “my_gauge” has been set. */
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_get,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_animation_set"></a>gx_circular_gauge_animation_set


Ange parametrar för animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_animation_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT steps, 
    INT delay);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger animerings steg och fördröjnings tid för en cirkulär mätare.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot cirkulär mätar kontroll block
- **steg** Totalt antal steg för en rotation
- **fördröjning** Fördröjnings tid för varje steg

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kryss ruta har valt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt värde

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set animation steps and delay time of circular gauge “my_gauge”
    to 30 and 1, the needle of “my_gauge” will rotate from
    current angle to target angle by 30 steps with 1 tick delay between every step. */
status = gx_circular_gauge_animation_set(&my_gauge, 30, 1);

/* If status is GX_SUCCESS the steps and delay time of “my_gauge” has been set. */
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_background_draw"></a>gx_circular_gauge_background_draw


Rita en cirkulär mätar bakgrund

### <a name="prototype"></a>Prototyp

```C
VOID gx_circular_gauge_background_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar bakgrunden för den angivna cirkel mätaren. Den här tjänsten kallas vanligt vis internt av funktionen gx_circular_gauge_draw, men exponeras för programmet för att hjälpa till med att skriva anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot cirkulär mätar kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Draw circular gauge background. */
gx_circular_gauge_background_draw(&my_circular_gauge);
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_create"></a>gx_circular_gauge_create


Skapa cirkulär mätare

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_create(
    GX_CIRCULAR_GAUGE *gauge,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_CIRCULAR_GAUGE_INFO *info,
    GX_RESOURCE_ID background_id,
    ULONG style,
    USHORT circular_gauge_id,
    GX_VALUE xpos,
    GX_VALUE ypos);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en cirkulär mätar widget med de angivna egenskaperna.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot cirkulär mätar kontroll block
- **namn** Logiskt namn för cirkulär mätar widget
- **överordnad** Pekare till överordnad widget
- **information** Pekare till mätar informations strukturen. **Bilaga i** innehåller definition som GX_CIRCULAR_GAUGE_INFO struktur
- **background_id** Resurs-ID för cirkulär mätar bakgrunds Pixelmap
- **stil** Format för cirkulär mätare. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **circular_gauge_id** Programdefinierat ID för cirkulär mätare
- **Xpos** Mätar x-koordinatens position
- **ypos** Mätar y-koordinatens position

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kryss ruta har valt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_SIZE** (0X19) ogiltig kontroll block storlek
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CIRCULAR_GAUGE gauge_info;

gauge_info.gx_circular_gauge_info_animation_steps = 30;
gauge_info.gx_circular_gauge_info_animation_delay = 1;
gauge_info.gx_circular_gauge_info_needle_xpos = 140;
gauge_info.gx_circular_gauge_info_needle_ypos = 140;
gauge_info.gx_circular_gauge_info_neelde_xcor = 20;
gauge_info.gx_circular_gauge_info_neelde_ycor = 88;
gauge_info.gx_circular_gauge_info_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Create “my_gauge”. */
status = gx_circular_gauge_create(&my_gauge, “my_gauge”,
            &my_parent,
            &gauge_info, MY_PIXELMAP_RESOURCE_ID, GX_NULL,
            MY_ICON_ID, 5, 30);

/* If status is GX_SUCCESS the circular gauge “my_gauge” has been created. */
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_draw
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_draw"></a>gx_circular_gauge_draw

Rita cirkulär mätare

### <a name="prototype"></a>Prototyp

```C
VOID gx_circular_gauge_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna cirkel mätaren. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade mätar widgetar.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot cirkulär mätar kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom circular gauge draw function. */
VOID custom_gauge_draw(GX_CIRCULAR_GAUGE *gauge)
{
    /* Call default circular gauge draw. */
    gx_circular_gauge_draw(gauge);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw
- gx_circular_gauge_create,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_event_process"></a>gx_circular_gauge_event_process


Bearbeta cirkulär mätar händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_event_process(
    GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna cirkulära mätaren.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare mot mätar kontroll block
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för godkänd mätare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic circular gauge event processing as part of custom event processing function. */
UINT custom_gauge_event_process(GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default circular gauge
             event processing */
        status = gx_circular_gauge_event_process(gauge, event);
        break;
}
return status;
```

### <a name="see-also"></a>Se även

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw

## <a name="gx_context_brush_default"></a>gx_context_brush_default


Ange pensel för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_default(GX_DRAW_CONTEXT *context);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger penseln för den angivna rit kontexten till standard.

### <a name="parameters"></a>Parametrar

- **kontext** Pekare till Sammanhangs kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) har skapats
- **GX_PTR_ERROR** (0X07) ogiltig kontext pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the brush of “my_context” to default. */
status = gx_context_brush_default(&my_context);

/* If status is GX_SUCCESS the brush of “my_context” has been set to default. */

```

### <a name="see-also"></a>Se även

- gx_context_brush_define,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_define"></a>gx_context_brush_define


Definiera pensel för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_define(
    GX_RESOURCE_ID line_color_id,
    GX_RESOURCE_ID fill_color_id, 
    UINT style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar penseln för den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **line_color_id** Resurs-ID för linje färg. **Bilaga B** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **fill_color_id** Resurs-ID för fyllnings färg. **Bilaga B** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **stil** Pensel typ. **Bilaga D** beskriver de pensel format som stöds. Pensel format kan kombineras till en variabel med hjälp av bitvis OR operation.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00)-slutförd kontext pensel definiera
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) ingen aktiv rit kontext definiera
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define the brush of the current context. */
status = gx_context_brush_define(GX_COLOR_BLACK_ID,
    GX_COLOR_BLACK_ID,
    GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush of the current context has been defined. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_get"></a>gx_context_brush_get


Hämta pensel för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_get(GX_BRUSH **return_brush);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar en pekare till den aktiva penseln i den aktuella rit kontexten. Om det inte finns någon aktiv rit kontext, Miss lyckas tjänsten och returnerar en NULL-pekare.

### <a name="parameters"></a>Parametrar

- **return_brush** Pekare till målet för penseln.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat kontext penseln
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BRUSH *my_brush;

/* Get the brush of the current context. */
status = gx_context_brush_get(&my_brush);

/* If status is GX_SUCCESS the brush of the current context has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_pattern_set"></a>gx_context_brush_pattern_set


Ange pensel mönster för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_pattern_set(ULONG pattern);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger pensel mönstret för den aktuella rit kontexten.

Pensel mönstret används för att rita streckade vågräta och streckade lodräta linjer. När gx_canvas_line_draw () anropas och linjen är vågrät eller lodrät, och fältet brush.gx_brush_line_pattern inte är noll, ritas en mönster linje.

Pensel mönster masken stöds för närvarande endast för vågräta och lodräta linjer.

### <a name="parameters"></a>Parametrar

- **mönster** Mönster som ska användas för penseln. Detta är ett enkelt hexadecimalt mönster som används för mönster linje ritning.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kontext pensel uppsättning har slutförts
- **GX_INVALID_CONTEXT** (0X06) ogiltigt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the brush pattern for the current contex. */
status = gx_context_brush_pattern_set(0x80808080);

/* If status is GX_SUCCESS the brush pattern of the current context
has been set to the specified pattern. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_style_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_set"></a>gx_context_brush_set


Ange pensel för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_set(GX_BRUSH *brush);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger penseln för den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **pensel** Pekare som används för den aktuella kontexten.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kontext pensel uppsättning har slutförts
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BRSUH my_brush;
GX_FONT *font;
GX_COLOR fill_color;
GX_COLOR line_color;

/* Retrieve the font that associated with the specified font ID. */
gx_context_font_get(MY_FONT_ID, &font);

/* Retrieve the color that associated with the specified color ID. */
gx_context_color_get(MY_FILL_COLOR_ID, &fill_color);
gx_context_color_get(MY_LINE_COLOR, &line_color);

my_brush.gx_brush_pixelmap = MY_PIXELMAP_ID;
my_brush.gx_brush_font = font;
my_brush.gx_brush_line_pattern = 0x80808080;
my_brush.gx_brush_pattern_mask = 0x80000000;
my_brush.gx_brush_fill_color = fill_color;
my_brush.gx_brush_line_color = line_color;
my_brush.gx_brush_style = GX_BRSUH_SOLID_FILL | GX_BRUSH_ALIAS |
                          GX_BRUSH_PIXELMAP_FILL | GX_BRUSH_ROUND
my_brush.gx_brush_width = 2;
my_brush.gx_brush_alpha = 255;

/* Set the brush of the current context. */
status = gx_context_brush_set(my_brush);

/* If status is GX_SUCCESS the brush of the current context has been set. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_style_set"></a>gx_context_brush_style_set


Ange pensel typ för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_style_set(UINT style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger pensel formatet för den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **stil** Pensel typ för aktuell kontext. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kontextens pensel format uppsättning har slutförts
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the brush style of the current context. */
status = gx_context_brush_style_set(GX_BRUSH_ALIAS);

/* If status is GX_SUCCESS the brush style of the current context has been set. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_width_set"></a>gx_context_brush_width_set


Ange pensel bredd för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_width_set(UINT width);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger bredden på den aktiva penseln i den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

**Bredd** Pensel bredd i bild punkter för aktuellt sammanhang

### <a name="return-values"></a>Retur värden

**GX_SUCCESS** (0x00) den slutförda kontext penselns bredd har angetts

**GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the brush width of the current context to 10 pixels. */
status = gx_context_brush_width_set(10); /*

If status is GX_SUCCESS the brush width of the current context has been set to 10. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_color_get"></a>gx_context_color_get


Hämta färg värde kopplat till färg-ID i den aktuella Draw-kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_color_get(
    GX_RESOURCE_ID color_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det färg värde som är associerat med det angivna färg-ID: t. Färgvärdet returneras i färg formatet för den aktiva Sammanhangs visningen. Den här tjänsten ska endast anropas inifrån en aktiv ritnings åtgärd.

### <a name="parameters"></a>Parametrar

**color_id** Resurs-ID för den begärda färgen.

**return_color** Adress till variabel som ska innehålla returnerat färg värde.

### <a name="return-values"></a>Retur värden

**GX_SUCCESS** (0X00) klart färg värdes get

**GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID

**GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

**GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_COLOR color_value;

/* Get the color vaue. */
status = gx_context_color_get(MY_BLACK_COLOR_ID, &color_value);
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_fill_color_set"></a>gx_context_fill_color_set

Ange fyllnings färg för aktuellt rit sammanhang

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_fill_color_set(GX_RESOURCE_ID fill_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger fyllnings färgen för den aktiva penseln i den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **fill_color_id** Resurs-ID för fyllnings färgen för den aktuella kontexten. **Bilaga B** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kontext fyllnings färg uppsättning har slutförts
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the fill color of the current context to black. */
status = gx_context_fill_color_set(MY_BLACK_COLOR_ID);

/* If status is GX_SUCCESS the fill color of the current context has been set to black. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_get"></a>gx_context_font_get

Hämta teckensnitt som är kopplat till teckensnitts-ID i den aktuella Draw-kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_font_get(
    GX_RESOURCE_ID font_id,
    GX_FONT **return_font);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar teckensnitts pekaren som är associerad med det angivna teckensnitts-ID: t. Den här tjänsten ska endast anropas inifrån en aktiv ritnings åtgärd.

### <a name="parameters"></a>Parametrar

- **font_id** Resurs-ID för begärt teckensnitt.
- **return_font** Adress till den variabel som ska innehålla returnerad teckensnitts pekare.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat teckensnitt
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_FONT *my_font;

/* Get the font pointer. */
status = gx_context_font_get(MY_MIDSIZE_FONT, &my_font);

/* If status is GX_SUCCESS, the font that indicated with MY_MIDSIZE_FONT has been successfully retrieved. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_set"></a>gx_context_font_set

Ange teckensnitt för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_font_set(GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger teckensnittet i den aktiva penseln i den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **font_id** Teckensnitts resurs-ID för aktuell kontext

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kontexten har angetts
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the font of the current context to MY_FONT_ID. */
status = gx_context_font_set(MY_FONT_ID);

/* If status is GX_SUCCESS the font of the current context has been set. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_line_color_set"></a>gx_context_line_color_set

Ange linje färg för aktuell ritnings kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_line_color_set(GX_RESOURCE_ID line_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger linje färgen för den aktiva penseln i den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **line_color_id** Linje färg för aktuell kontext. **Bilaga B** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd kontext linje färg uppsättning
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the line color of the current context to black. */
status = gx_context_line_color_set(GX_COLOR_BLACK_ID);

/* If status is GX_SUCCESS the line color of the current context has been set to black. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_get"></a>gx_context_pixelmap_get

Hämta Pixelmap som är associerade med Pixelmap-ID i den aktuella Draw-kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_pixelmap_get(
    GX_RESOURCE_ID pixelmap_id,
    GX_PIXELMAP **return_map);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar Pixelmap-pekaren som är associerad med det angivna Pixelmap-ID: t.

### <a name="parameters"></a>Parametrar

- **pixelmap_id** Resurs-ID för Pixelmap begärdes.
- **return_map** Adress till variabel att lagra returnerad Pixelmap-adress.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat Pixelmap
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang
- **GX_PTR_ERROR** (0X07) ogiltig Pixelmap-pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PIXELMAP *map;

/* Get the pixelmap pointer. */
status = gx_context_pixelmap_get(MY_PIXELMAP_ID, &map);

/* If status is GX_SUCCESS, the pixelmap was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_set"></a>gx_context_pixelmap_set

Ange Pixelmap för den aktuella Draw-kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_pixelmap_set(GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar Pixelmap för den aktiva penseln i den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **pixelmap_id** Resurs-ID för Pixelmap som ska användas för den aktuella kontexten

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad kontext Pixelmap set
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVLAID_CONTEXT** (0X06) ogiltig kontext

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set pixelmap of the current context to MY_PIXELMAP_ID. */
status = gx_context_pixelmap_set(MY_PIXELMAP_ID);

/* If status is GX_SUCCESS the pixelmap of the current context has been set. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_brush_define"></a>gx_context_raw_brush_define

Definiera rå pensel för aktuell Draw-kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_raw_brush_define(
    GX_COLOR line_color,
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar den obearbetade penseln för den aktuella skärm kontexten. RAW-definitioner används när 32-bitars ARGB färg värden ska överföras till penseln i stället för färg-ID: n. Råa färg definitioner är användbara när den önskade färgen inte finns i den aktuella system färg tabellen eller när RGB-färgvärdet beräknas vid körning.

### <a name="parameters"></a>Parametrar

- **line_color** Färg på linje i 32-bitars RAW ARGB färg format. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **fill_color** Färg för fyllning i 32-bitars RAW ARGB färg format. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **stil** Pensel typ. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad kontext för RAW-pensel definiera
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define the raw brush of the current context. */
status = gx_context_raw_brush_define(GX_COLOR_BLACK,
    GX_COLOR_BLACK, GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the raw brush of the current context has been defined. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_fill_color_set"></a>gx_context_raw_fill_color_set

Ange rå fyllnings färg för den aktuella rit kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_raw_fill_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den råa fyllnings färgen för den aktuella skärm kontexten. Parametern line_color är ett oformaterat färg värde för 32-bitars ARGB-format i stället för ett färg-ID-värde. Råa färg definitioner är användbara när den önskade färgen inte finns i den aktuella system färg tabellen eller när RGB-färgvärdet beräknas vid körning.

### <a name="parameters"></a>Parametrar

- **line_color** Färg på linje. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad kontext för oformaterad fyllnings färg uppsättning
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the raw fill color of the current context. */
status = gx_context_raw_fill_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw fill color of the current context has been set. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_line_color_set

## <a name="gx_context_raw_line_color_set"></a>gx_context_raw_line_color_set

Ange rå linje färg för den aktuella rit kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_raw_line_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger linje färgen för den aktiva penseln i den aktuella rit kontexten. Parametern line_color är ett oformaterat färg värde för 32-bitars ARGB-format i stället för ett färg-ID-värde. Råa färg definitioner är användbara när den önskade färgen inte finns i den aktuella system färg tabellen eller när RGB-färgvärdet beräknas vid körning.

### <a name="parameters"></a>Parametrar

- **line_color** Färg på linje värde. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd kontext RAW linje färg uppsättning
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

```C
/* Set the raw line color of the current context. */
status = gx_context_raw_line_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw line color of the current context has been set. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_context_string_get"></a>gx_context_string_get

Hämta strängen som är associerad med sträng-ID (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_string_get(GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **return_string);
```

### <a name="description"></a>Beskrivning

Detta föråldrade API returnerar den sträng som är associerad med angivet sträng-ID. Nya program bör använda gx_context_string_get_ext ().

### <a name="parameters"></a>Parametrar

- **string_id** Sträng-ID som genereras av GUIX Studio-programmet.
- **return_string** Adress till variabel att returnera sträng pekare.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd kontext RAW linje färg uppsättning
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *text;

status = gx_context_string_get(GX_ID_ERROR, &text);

/* If status is GX_SUCCESS the string pointer has been returned. */
```

### <a name="see-also"></a>Se även

- gx_context_string_get_ext

## <a name="gx_context_string_get_ext"></a>gx_context_string_get_ext

Hämta strängen som är associerad med angivet sträng-ID.

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_string_get_ext(
    GX_RESOURCE_ID string_id, 
    GX_STRING *return_string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar strängen som är associerad med ett angivet sträng-ID. Den här tjänsten kan bara anropas när det finns en aktiv rit kontext, dvs. inifrån ritnings funktionen i en widget. Den här tjänsten identifierar den aktiva arbets ytan och visar och hämtar strängen från den placerade visnings instansen.

### <a name="parameters"></a>Parametrar

- **string_id** Sträng-ID som används för att identifiera strängen, som genereras av GUIX Studio i program resursens huvud fil.
- **return_string** Adressen till GX_STRING variabel där sträng pekaren och sträng längden ska returneras.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd kontext RAW linje färg uppsättning
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0X06) inget aktivt rit sammanhang

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel


```C
GX_STRING string;

/* Set the raw line color of the current context. */
status = gx_context_string_get_ext(ID_ERROR, &string);

/* If status is GX_SUCCESS the string.gx_string_ptr and
string.gx_string_length values have been returned. */
```

### <a name="see-also"></a>Se även

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_display_active_language_set"></a>gx_display_active_language_set

Tilldela visnings aktivt språk

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_active_language_set(
    GX_DISPLAY *display, 
    GX_UBYTE language);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar det aktuella aktiva språket för den angivna visningen. Språk indexet motsvarar de språk som definierats i tabellen visnings språk och är inte en ANSI-språkidentifierare.

Olika skärmar i flera visnings system kan båda köra olika aktiva språk. Tabellen visnings språk ska tilldelas innan detta API används. När en visning initieras med hjälp av gx_studio_display_configure installeras språk tabellen automatiskt och programmet skickas i det aktiva språk indexet.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **språk** Aktivt språk index

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutfört språk tilldelning
- **GX_PTR_ERROR** (0X07) ogiltig visnings pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt språk index

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_active_language_set(&my_display,
    LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>Se även

- gx_display_language_table_set
- gx_studio_display_configure

## <a name="gx_display_color_set"></a>gx_display_color_set

Tilldela ett färg värde igen

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_color_set(
    GX_DISPLAY *display,
    GX_RESOURCE_ID color_id, 
    GX_COLOR new_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar om det färg värde som är associerat med det angivna färg-ID: t. Detta kan användas för att ändra färg tabellen för en visning utan att en helt ny färg tabell skapas. Det angivna färg värdet måste vara i det inbyggda formatet som stöds av visningen.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **color_id** Färg-ID att omtilldela
- **new_color** Färg värde som ska tilldelas till den här color_ids platsen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00)-omtilldelning av färg har slutförts
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt färg-ID
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_DISPLAY** (0X1D) ogiltig visning

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_color_set(&my_display, MY_COLOR_ID, 0x5454);

/* If status is GX_SUCCESS the color has been reassigned. */
```

### <a name="see-also"></a>Se även

- gx_display_color_table_set

## <a name="gx_display_color_table_set"></a>gx_display_color_table_set

Tilldela visnings färg tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_color_table_set(
    GX_DISPLAY *display,
    GX_COLOR *color_table, 
    INT color_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den färg tabell som ska användas av visningen igen. Den här tjänsten anropas vanligt vis av den genererade visnings konfigurations funktionen i GUIX Studio, men kan också anropas av program varan.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **color_table** Matris med färg värden i enhetligt visnings format.
- **color_count** Anger antalet poster i färg tabellen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad färg tabell uppsättning
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_DISPLAY** (0X1D) ogiltig visning

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_COLOR default_table[32] = { … };

/* Change the color table */
status = gx_display_color_table_set(&my_display, default_table, 32);

/* If status is GX_SUCCESS the color table has been reassigned. */
```

### <a name="see-also"></a>Se även

- gx_display_color_set

## <a name="gx_display_create"></a>gx_display_create

Skapa bildskärm

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_create(
    GX_DISPLAY *display, 
    GX_CONST CHAR *name,
    UINT (*display_driver_setup)(GX_DISPLAY *),
    GX_VALUE width, 
    GX_VALUE height);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en skärm och anropar installations funktionen för visnings driv rutin. GUIX tar den här skärmen och lägger till den i den interna listan över skärmar.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **namn** Namn på visningen
- **display_driver_setup** Pekare för att Visa installations funktionen för driv rutiner
- **optional_driver_info** Pekare till valfri driv rutins information
- **color_format** Färg format, enligt definitionen i **bilaga C**
- **Bredd** Antal bild punkter på x-axeln
- **höjd** Antal bild punkter på y-axeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Visa skapa
- **GX_SYSTEM_ERROR** (0xFE) Det gick inte att konfigurera visning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_SIZE** (0X23) ogiltig storlek för visnings kontroll block

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_DISPLAY my_display;

UINT my_driver_setup_callback(GX_DISPLAY *display)
{
    …
}

/* Create screen “my_display”. */
status = gx_display_create(&my_display, “my display”,
    my_driver_setup_callback, 320, 480);

/* If status is GX_SUCCESS, the screen “my_display” has been created. */
```

### <a name="see-also"></a>Se även

- gx_display_delete

## <a name="gx_display_delete"></a>gx_display_delete


Förstör visning

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_delete(
    GX_DISPLAY *display,
    VOID (*display_driver_cleanup)(GX_DISPLAY *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger av en visning och rensar allokerade resurser.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **display_driver_cleanup** Pekare som visar rensnings funktionen för driv rutiner

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) visnings borttagning har slutförts
- **GX_FAILURE** (0X10) skapade visnings listan är null
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
VOID driver_cleanup_callback(GX_DISPLAY *display)
{
    …
}

/* Delete a display “my_display”. */
status = gx_display_delete(&my_display, driver_cleanup_callback);

/* If status is GX_SUCCESS the screen “my_display” has been destroyed. */
```

### <a name="see-also"></a>Se även

- gx_canvas_block_move
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_text_draw
- gx_display_create

## <a name="gx_display_font_table_set"></a>gx_display_font_table_set

Tilldela Visa teckensnitts tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_font_table_set(
    GX_DISPLAY *display,
    GX_FONT **font_table, 
    INT table_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar om teckensnitts tabellen som ska användas av visningen. Den här tjänsten anropas vanligt vis av den genererade visnings konfigurations funktionen i GUIX Studio, men kan också anropas av program varan.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **font_table** Matris med GX_FONT pekare.
- **table_size** Antal teckensnitt i tabellen

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_FONT *font_table[32] = { … };

/* Assign font table */
status = gx_display_font_table_set(&my_display, font_table, 32);

/* If status is GX_SUCCESS, the font table has been reassigned. */
```

### <a name="see-also"></a>Se även

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_language_table_get"></a>gx_display_language_table_get

Hämta visnings språk tabellen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_get(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE *language_count,
    UINT *string_table_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar språk tabellen från den angivna visningen. Den här tjänsten kan användas av ett program för att ändra visnings språk tabellen, vid körning, med dynamiskt definierade strängar.

Detta API är inaktuellt och stöds endast för program som använder den gamla format språk tabellen (dvs. den Studio-genererade resurs filen genereras för biblioteks version före version 5,6). Nya program bör använda gx_display_language_table_get_ext ().

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **tabell** Adress för att ta emot tabell pekare
- **language_count** Adress för att ta emot antal språk
- **string_table_size** Adress för att ta emot sträng tabell storlek

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get(&my_display,
        &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved.
```

### <a name="see-also"></a>Se även

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get
- gx_display_language_table_get_ext

## <a name="gx_display_language_table_get_ext"></a>gx_display_language_table_get_ext

Hämta visnings språk tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_get_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE *language_count, 
    UINT *string_table_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar språk tabellen från den angivna visningen. Den här tjänsten kan användas av ett program för att ändra visnings språk tabellen, vid körning, med dynamiskt definierade strängar.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **tabell** Adress för att ta emot tabell pekare
- **language_count** Adress för att ta emot antal språk
- **string_table_size** Adress för att ta emot sträng tabell storlek

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get_ext(&my_display,
    &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_display_language_table_set_ext
- gx_display_active_langauge_set
- gx_display_string_get_ext

## <a name="gx_display_language_table_set"></a>gx_display_language_table_set

Tilldela visnings språk tabell (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_set(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE number_of_languages, 
    UINT number_of_strings);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad och nya program bör använda gx_display_language_table_set_ext (). Den här tjänsten stöds bara för kompatibilitet med Studio-genererade resurser som mål biblioteks versioner före version 5,6.

Den här tjänsten tilldelar språk tabellen som ska användas av visningen. Den här tjänsten anropas vanligt vis av den genererade GUIX Studio-funktionen gx_studio_display_configure, men kan också anropas av program varan.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **tabell** Språk tabell
- **number_of_languages** Antal kolumner i den angivna tabellen
- **number_of_strings** Antal strängar i varje tabell kolumn

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR ***language_table= my_app_language_table;

/* Assign language table */
status = gx_display_language_table_set(&my_display, language_table,
5, 232);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>Se även

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_language_table_set_ext"></a>gx_display_language_table_set_ext

Tilldela visnings språk tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_set_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE number_of_languages,
    UINT number_of_strings);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar språk tabellen som ska användas av visningen. Den här tjänsten anropas vanligt vis av den genererade GUIX Studio-funktionen gx_studio_display_configure, men kan också anropas av program varan.

Tabell tilldelning för körnings språk utförs vanligt vis när språk läses in från en binär resurs fil med hjälp av gx_binres_language_table_load ().

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **tabell** Språk tabell
- **number_of_languages** Antal kolumner i den angivna tabellen
- **number_of_strings** Antal strängar i varje tabell kolumn

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING **language_table = my_app_language_table;

/* Assign the language table */
status = gx_display_language_table_set_ext(&my_display,
    language_table, 5, 132);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>Se även

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_pixelmap_table_set"></a>gx_display_pixelmap_table_set

Tilldela Visa teckensnitts tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_pixelmap_table_set(
    GX_DISPLAY *display,
    GX_PIXELMAP **pixelmap_table, 
    INT table_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar Pixelmap-tabellen som ska användas av visningen igen. Den här tjänsten anropas vanligt vis av den Studio-genererade visnings konfigurations funktionen, men kan också anropas av program varan.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **pixelmap_table** Matris med GX_PIXELMAP pekare.
- **table_size** Antal pixelmaps i tabellen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ange Pixelmap-tabell
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Assign pixelmap table */
status = gx_display_pixelmap_table_set(&my_display, pixelmap_table, 32);

/* If status is GX_SUCCESS the pixelmap table has been reassigned. */
```

### <a name="see-also"></a>Se även

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_display_string_get"></a>gx_display_string_get

Hämta en sträng från den aktiva sträng tabellen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_get(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id, 
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_display_string_get_ext ().

Den här tjänsten hämtar en sträng från den aktiva sträng tabellen för den angivna visningen. Det aktiva språket används för att välja den sträng från den språk tabell som är kopplad till visningen.

Sträng-ID genereras av GUIX Studio och finns i huvud filen för program resurser. h.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **string_id** Sträng-ID, genererat av GUIX Studio.
- **sträng** Adress till sträng pekare, variabel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) sträng hämtning har slutförts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt sträng-ID
- **GX_PTR_ERROR** (0X07) ogiltig visnings pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *string;

/* Retrieve string value */
status = gx_display_string_get(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```


### <a name="see-also"></a>Se även

- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_display_string_get_ext"></a>gx_display_string_get_ext

Hämta en sträng från den aktiva sträng tabellen

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_get_ext(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id,
    GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar en sträng från den aktiva sträng tabellen för den angivna visningen. Det aktiva språket används för att välja den sträng från den språk tabell som är kopplad till visningen.

Sträng-ID genereras av GUIX Studio och finns i huvud filen för program resurser. h.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **string_id** Sträng-ID, genererat av GUIX Studio.
- **sträng** Adress till GX_STRING-variabel i
- **vilken** String.gx_string_ptr och
- **String.gx_string_length** kommer att returneras.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) sträng hämtning har slutförts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt sträng-ID
- **GX_PTR_ERROR** (0X07) ogiltig visnings pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING string;

/* Retrieve string value */
status = gx_display_string_get_ext(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_display_active_language_set
- gx_display_language_table_set


## <a name="gx_display_string_table_get"></a>gx_display_string_table_get


Hämta den aktiva sträng tabellen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_CHAR ***table,
    UINT *table_size);
```

### <a name="description"></a>Beskrivning

Tjänsten är föråldrad och ersätts av gx_display_string_table_get_ext ().

Den här tjänsten hämtar den sträng tabell som är kopplad till det aktiva språket. Den här tjänsten används inte ofta, men den tillhandahålls för att vara fullständig för de program som kan behöva göra körnings ändringar i sträng tabellen.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **språk** Tabell kolumn som ska hämtas.
- **tabell** Adress till variabel att returnera pekare.
- **table_size** Variabel adress att returnera tabell storlek

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_NOT_FOUND** (0X09) ogiltigt språk index
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR **string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get(&my_display, LANGUAGE_ENGLISH,
    &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_string_table_get_ext"></a>gx_display_string_table_get_ext


Hämta den aktiva sträng tabellen

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_STRING **table, 
    UINT *table_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den sträng tabell som är kopplad till det aktiva språket. Den här tjänsten används inte ofta, men den tillhandahålls för att vara fullständig för de program som kan behöva göra körnings ändringar i sträng tabellen.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **språk** Tabell kolumn som ska hämtas.
- **tabell** Adress till variabel att returnera pekare.
- **table_size** Variabel adress att returnera tabell storlek

### <a name="return-values"></a>Retur värden

- En teckensnitts tabell uppsättning har **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_NOT_FOUND** (0X09) ogiltigt språk index
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING *string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get_ext(&my_display,
    LANGUAGE_ENGLISH, &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_theme_install"></a>gx_display_theme_install


Installera teman på den angivna visningen

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_theme_install(
    GX_DISPLAY *display, 
    GX_THEME *theme_table);
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar teman på den angivna visningen. Den här tjänsten anropas vanligt vis av den Studio-genererade visnings konfigurations funktionen, men kan också anropas av program varan.

### <a name="parameters"></a>Parametrar

- **Visa** Pekare som visar kontroll block
- **theme_table** Tema tabell som ska installeras

### <a name="return-values"></a>Retur värden

- Tema tabellen har installerats för **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig tema tabell pekare
- **GX_INVALID_DISPLAY** (0X1D) ogiltig visning

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_THEME theme_1;

&theme_table[1] = {
    &theme_1,
    …
}

/* Define resource tables. */
GX_COLOR color_table[32] = {…};
GX_FONT *font_table[32] = {…};
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Define scroll appearance. */
GX_SCROLLBAR_APPEARANCE scroll_appearance;

memset(&scroll_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

scroll_appearance.gx_scroll_width = 20;
scroll_appearance.gx_scroll_thumb_width = 18;
scroll_appearance.gx_scroll_thumb_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_border_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_button_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_travel_min = 20;
scroll_appearance.gx_scroll_thumb_travel_max = 20;
scroll appearance.gx_scroll_thumb_border_style =
    GX_STYLE_BORDER_THIN;

theme_1.theme_color_table = color_table;
theme_1.theme_font_table = font_table;
theme_1.theme_pixlemap_table = pixelmap_table;
theme_1.theme_palette = GX_NULL;
theme_1.theme_vertical_scrollbar_appearance = scroll_appearance;
theme_1.theme_horizontal_scrollbar_appearance = scroll_appearance;
theme_1.theme_vertical_scroll_style = GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_horizontal_scroll_style =
    GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_color_table_size = 32;
theme_1.theme_font_table_size = 32;
theme_1.theme_pixelmap_table_size = 32;
theme_1.theme_palette_size = 0;

/* Install theme table. */
status = gx_display_theme_install(&my_display, theme_table);

/* If status is GX_SUCCESS the theme table has been installed. */
```

### <a name="see-also"></a>Se även

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_drop_list_close"></a>gx_drop_list_close


Stänga en drop List

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_close(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger popup-listan för den angivna Drop-listan.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontroll blocket för List rutan

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) stängde Drop List
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Close a drop list. */
status = gx_drop_list_close(&drop_list);

/* If status is GX_SUCCESS, the drop list is closed. */
```

### <a name="see-also"></a>Se även

- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open

gx_drop_list_pixelmap_set gx_drop_list_popup_get

## <a name="gx_drop_list_create"></a>gx_drop_list_create


Skapa en drop List

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_create(
    GX_DROP_LIST *drop_list, 
    GX_CONST
    GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_rows, 
    INT open_height,
    VOID (*callback)(GX_VERTICAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT drop_list_id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en drop-lista. En drop List är en kombination av widgeten Drop list och en lodrät lista med popup-fönster som visas när den nedrullningsbara listan öppnas. Den lodräta List rutan skapas automatiskt när widgeten för List rutan skapas och visas eller döljs när widgeten för List menyn öppnas eller stängs.

Widgeten Drop List stöder två associerade pixelmaps. Det första, som beskrivs som "lista Skriv bords underlägg" i egenskapsvyn för Studio är det valfria Skriv bords Pixelmap som visas som bakgrund i den lodräta listan som visas när widgeten List List öppnas. Den andra Pixelmap, som beskrivs som "bakgrunds bild" i vyn Studio egenskaper, är en valfri bild som visas som bakgrund i själva List listan.

En widget för List List kan ha (men måste inte ha) en underordnad widget som används för att öppna och stänga Drop-listan. Detta är normalt en ikon eller knapp-widget, men även en anpassad widget kan användas som öppen/Close-växel för den överordnade Drop-listan. Den nyckel inställning som gör att den här underordnade widgeten använder list rutan är att denna underordnade widget måste ha det fördefinierade widgets-ID: t ID_DROP_LIST_BUTTON.

Så här definierar du en underordnad widget som öppnar och stänger List rutan, firstadd och underordnade widgeten till den nedrullningsbara listan och placerar den underordnade i list rutan som du vill:

![Skärm bild av den nedrullningsbara listan.](./media/guix/image6.jpg)

Använd sedan vyn Studio egenskaper för att tilldela denna underordnade widget ID-värdet ID_DROP_LIST_BUTTON, vilket är ett internt definierat ID-värde som identifieras av den överordnade Drop-listan:

![Skärm bild av vyn Studio-egenskaper.](./media/guix/image7.jpg)

### <a name="parameters"></a>Parametrar
- **drop_list** Pekare till kontroll blocket för List rutan
- **namn** Namn på Drop List
- **överordnad** Pekare till överordnad widget
- **total_rows** Totalt antal rader i släpp listan
- **open_height** Höjden på den lodräta listan som visas när den nedrullningsbara listan öppnas.
- **motringning** Funktionen anropas av den lodräta listan när listan rullas. Mer information hittar du i dokumentationen för GX_VERTICAL_LIST.
- **stil** Kant linje formatet för den nedrullningsbara listan.
- **drop_list_id** Programdefinierat ID för Drop List
- **storlek** Den släpp listans dimensioner

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Drop List har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_DROP_LIST my_drop_list;
VOID list_row_create(GX_VERTICAL_LIST *list,
                     GX_WIDGET *row, INT index);
{
    …
}

GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 10, 10, 80, 40);

status = gx_drop_list_create(&my_drop_list,
    "my drop list", GX_NULL,
    10, 100, list_row_create,
    GX_STYLE_BORDER_RECESSED | GX_STYLE_ENABLED,
    ID_DROP_LIST, &size)

/* Is status is GX_SUCCESS, the drop list was successfully created. */
```

### <a name="see-also"></a>Se även:

- gx_drop_list_close
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_event_process"></a>gx_drop_list_event_process


Händelse för process Drop List

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_event_process(
    GX_DROP_LIST *list, 
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för Drop-listan.

### <a name="parameters"></a>Parametrar

- **drop_list** Släpp List widget kontroll block
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bearbetade händelse för Drop List
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic drop list event processing as part of custom event processing function. */

UINT custom_drop_list_event_process(GX_DROP_LIST *drop_list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default drop list
            event processing */
        status = gx_drop_list_event_process(drop_list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_open"></a>gx_drop_list_open


Öppna en drop List

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_open(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Beskrivning

Den här tjänsten öppnar en tidigare skapad Drop-lista.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontroll blocket för List rutan

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Drop List har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_DROP_LIST mylist;

/* Open the popup list of “mylist”. */
status = gx_drop_list_open(&mylist);

/* If status == GX_SUCCESS, the popup list of “mylist” has been displayed. */
```

### <a name="see-also"></a>Se även

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_pixelmap_set"></a>gx_drop_list_pixelmap_set


Tilldela en bakgrunds bild till den nedrullningsbara listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_pixelmap_set(
    GX_DROP_LIST *drop_list,
    GX_RESOURCE_ID id);
```

### <a name="description"></a>Beskrivning

Tilldela en bakgrunds bild till den nedrullningsbara listan. Den här Pixelmap används som bakgrund för själva widgeten List meny, och inte för den lodräta List rutan som visas när listan öppnas. Om du vill tilldela en Pixelmap till popup-menyn för List rutan måste du först anropa gx_drop_list_popup_get för att hämta en pekare till popup-listan och sedan använda gx_window_wallpaper_set () för att tilldela en Pixelmap till den här popup-listan.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontroll blocket för List rutan
- **ID-** resurs-ID till pixlemap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Drop List Pixelmap set
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt pixlemap-ID

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_DROP_LIST mylist;

/* create the drop list here */

/* Assign a pixelmap id, which will turn on the list button */
status = gx_drop_list_pixelmap_set(&mylist,
    GX_PIXELMAP_ID_DROP_LIST_BACKGROND);

/* If status is GX_SUCCESS, the pixelmap was successfully set. */
```

### <a name="see-also"></a>Se även:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_popup_get

## <a name="gx_drop_list_popup_get"></a>gx_drop_list_popup_get


Hämta pekare för att popup-lista lodrätt

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_popup_get(
    GX_DROP_LIST *drop_list,
    GX_VERTICAL_LIST **return_list);
```

### <a name="description"></a>Beskrivning

En widget för List List består av själva widgeten List List, och en lodrät lista med popup-fönster som visas när widgeten List List öppnas. Den här tjänsten hämtar en pekare till den vertikala List komponenten i list rutan, så att programmet kan anropa API-tjänster direkt på den här lodräta listan.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontroll blocket för List rutan
- **return_list** Pekare till den lodräta listan som lagras i den nedrullningsbara listan

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat popup-lodrät lista
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_DROP_LIST drop_list;
GX_VERTICAL_LIST *vertical_list;

/* Retrieve the popup list of “drop_list”. */
status = gx_drop_list_popup_get(&drop_list, &vertical_list)

/* If status is GX_SUCCESS, the popup list was successfully retrieved. */
```

### <a name="see-also"></a>Se även:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set

## <a name="gx_horizontal_list_children_position"></a>gx_horizontal_list_children_position


Placera underordnade i den vågräta listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_children_position(GX_HORIZONTAL_LIST *horizontal_list);
```

### <a name="description"></a>Beskrivning

Den här funktionen placerar underordnade objekt i den vågräta listan. Den här funktionen anropas automatiskt när listan får GX_EVENT_SHOW händelsen, men ska anropas direkt om listan ändras efter att den har gjorts synlig.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Pekare till kontroll blocket vågrät List

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) placerade underordnade för den vågräta listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Position children in the horizontal list */
status = gx_horizontal_list_children_position (&horizontal_list);

/* If status is GX_SUCCESS the children in the horizontal list are positioned. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_create"></a>gx_horizontal_list_create


Skapa vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_create(
    GX_HORIZONTAL_LIST *horizontal_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_columns,
    VOID (*callback)(GX_HORIZONTAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT horizontal_list_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en vågrät lista.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontroll block för widgeten vågrät List
- **namn** Namn på vågrät lista
- **överordnad** Pekare till överordnad widget
- **total_columns** Totalt antal comumns i vågrät lista
- **motringning** Detta är en pekare till en callback-funktion som tillhandahålls av programmet. Motringningsfunktionen anropas när den vågräta listan rullas för att skapa de objekt som visas nyligen. På så sätt kan den vågräta listan Visa en användardefinierad widget som List objekt.
- **stil** Typ av widget för rullnings List. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **horizontal_list_id** Programdefinierat ID för vågrät lista
- **storlek** Mått i horitzonal-listan

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) skapade den vågräta listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_VALUE** (0X22) antal kolumner som inte är giltiga

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create horizontal list “my_list” with 5 columns. */
status = gx_horizontal_list_create(&my_list, “my_list”, &my_parent,
    5, callback, GX_STYLE_WRAP, MY_LIST_ID, &size);

/* If status is GX_SUCCESS the horizontal list “my_list” has been created. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_event_process"></a>gx_horizontal_list_event_process


Händelse för bearbeta vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den vågräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontroll block för widgeten vågrät List
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bearbetade vågrät lista-händelse
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Call generic horizontal list event processing as part of custom event processing function. */

UINT custom_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default horizontal
        list event processing */
        status =
        gx_horizontal_list_event_process(list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_page_index_set"></a>gx_horizontal_list_page_index_set


Ange start sid index

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_page_index_set(
    GX_HORIZONTAL_LIST *list,
    INT *index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger start indexet för den vågräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontroll block för widgeten vågrät List
- **index** Det nya översta indexet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) angav start sid indexet för den vågräta listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt värde

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Sets the starting page index of horizontal list “my_list” as 1. */
status = gx_horizontal_list_page_index_set(&my_list, 1);

/* If status is GX_SUCCESS the starting page index of “my_list” has been set. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_index_get"></a>gx_horizontal_list_selected_index_get


Hämta markerat indexord från vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_selected_index_get(
    GX_horizobntal_LIST *horizontal_list,
    INT *return_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar den markerade List post indexet för den vågräta listan.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontroll block för widgeten vågrät List
- **return_index** Mål för Return List index

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades hämta den vågräta List posten
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
INT current_index_entry;

/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_index_get(&my_list,
    &current_index_entry);

/* If status is GX_SUCCESS, “current_index_entry” contains the current list selection index. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_set"></a>gx_horizontal_list_selected_set


Tilldela den markerade posten i en vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_selected_set(
    GX_HORIZONATAL_LIST *horizontal_list,
    INT index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den valda posten i en vågrät lista. Om det behövs kommer den vågräta listan att rullas för att göra den markerade posten synlig.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontroll block för widgeten vågrät List
- **index** Indexerad position för ny List post

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett den vågräta List posten
- **GX_FAILURE** (0X10) indexet är inte inom ett ogiltigt intervall
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_horizontal_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_widget_get"></a>gx_horizontal_list_selected_widget_get


Hämta vald post från vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_selected_widget_get(
    GX_horizobntal_LIST *horizontal_list,
    GX_WIDGET **return_list_entry);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar den markerade List posten i den vågräta listan. Observera att om den vågräta listan har fler rader än underordnade widgetar, och den valda posten har bläddrats från vyn, returnerar detta API GX_NULL eftersom de underordnade widgetarna används igen när List innehållet rullas. Funktionen gx_horizontal_list_selected_index_get returnerar tillförlitligt index för det valda objektet, även om objektet har bläddrats från vyn.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontroll block för widgeten vågrät List
- **return_list_entry** Mål för widgeten Return List post

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades hämta den vågräta List posten
- **GX_FAILURE** (0X10) vald widgeten har bläddrats från vyn i en lista med fler rader än klientens underordnade.
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_widget_get(&my_list, &current_list_entry);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */

    
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_total_columns_set"></a>gx_horizontal_list_total_columns_set


Tilldela det totala antalet List kolumner

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_total_columns_set(
    GX_HORIZONTAL_LIST *horizontal_list,
    INT count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar det totala antalet kolumner som ska visas i den vågräta listan.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontroll block för widgeten vågrät List
- **antal** Antal kolumner som ska visas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) antal tilldelade kolumner
- **GX_CALLER_ERROR** (0X10) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt Count-värde

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Tell my list to display 20 total columns. */
status = gx_horizontal_list_total_columns_set(&my_list, 20);

/* If status is GX_SUCCESS, the total colums of “my_list” was successfully set to 20. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set

## <a name="gx_horizontal_scrollbar_create"></a>gx_horizontal_scrollbar_create


Skapa vågrät rullnings List

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name,
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en vågrät rullnings List. ID: t för en vågrät rullnings List är fördefinierat (eftersom ett fönster måste veta hur man fångar in händelser från det) och storleken är automatisk (eftersom det måste fylla det överordnade fönstrets klient bredd). Om vi beslutar att tillåta rullnings lister för kund områden måste vi lägga till en annan Create-funktion med parametrarna ID och storlek.

### <a name="parameters"></a>Parametrar

- **rullnings List** Kontroll block för rullnings List
- **namn** Namn på rullnings List
- **överordnad** Pekare till överordnad widget
- **utseende** I utseende strukturen definieras utseendet på rullnings listen. Om det här värdet är GX_NULL använder rullnings listen standard rullnings listen som definieras av gx_system_scroll_appearance_get. Se **bilaga i** för definitionen av GX_SCROLLBAR_APPEARANCEs strukturen.
- **Stil** Typ av widget för rullnings List. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) vågrät rullnings List har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create horizontal scrollbar “my_scrollbar”. */
status = gx_horizontal_scrollbar_create(&my_scrollbar,
    “my_horizontal_scrollbar”, &my_parent, GX_NULL,
    GX_STYLE_SCROLLBAR_END_BUTTONS);

/* If status is GX_SUCCESS the horizontal scrollbar “my_scrollbar” has been created. */
```

### <a name="see-also"></a>Se även

- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_icon_button_create"></a>gx_icon_button_create


Knappen Skapa ikon

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_button_create(
    GX_ICON_BUTTON *button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID icon_id,
    ULONG style,
    USHORT icon_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar den angivna widgeten knapp ikon.

GX_ICON_BUTTON härleds från GX_BUTTON och stöder alla gx_button API-tjänster.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare på knapp kontroll block för ikon
- **namn** Logiskt namn för widgeten ikon knapp
- **överordnad** Pekare till överordnad widget
- **icon_id** Resurs-ID för ikon
- **stil** Ikon format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **icon_button_id** Programdefinierat ID för ikon knapp
- **storlek** Ikon knappen dimensioner

### <a name="return-values"></a>Retur värden

- Ikon knappen **GX_SUCCESS** (0X00) har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_icon_button”. */
status = gx_icon_button_create(&my_icon_button, “my_icon_button”,
    &my_parent,
    MY_ICON_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the icon button “my_icon_button” has been created. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_draw"></a>gx_icon_button_draw


Knappen Rita en ikon

### <a name="prototype"></a>Prototyp

```C
VOID gx_icon_button_draw(GX_ICON_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar ikon knappen. Den här funktionen kallas vanligt vis internt av GUIX som en del av en uppdaterings åtgärd på arbets ytan, men den exponeras även för det program som kanske vill tillhandahålla en anpassad ritnings funktion och anropa standard knapp ritningen som en anpassad ritnings bas.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare på knapp kontroll block för ikon

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_icon_button_draw(button);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_pixelmap_set"></a>gx_icon_button_pixelmap_set


Ange Pixelmap till widgeten ikon knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_button_pixelmap_set(
    GX_ICON_BUTTON *button,
    GX_RESOURCE_ID icon_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en ny Pixelmap till widgeten ikon knapp.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare på knapp kontroll block för ikon
- **icon_id** Resurs-ID för Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett ikon knappen Pixelmap
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set pixelmap for “my_icon_button”. */
status = gx_icon_button_pixelmap_set(&my_icon_button,
    GX_PIXELMAP_ID_ICON);

/* If status is GX_SUCCESS, the pixelmap of the icon button “my_icon_button” has been set. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_background_draw"></a>gx_icon_background_draw


Rita ikon bakgrund

### <a name="prototype"></a>Prototyp

```C
VOID gx_icon_background_draw(GX_ICON *icon);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar bakgrund för den angivna widgeten ikon. Den här tjänsten kallas vanligt vis internt av funktionen gx_icon_button_draw, men exponeras för programmet för att hjälpa till med att skriva anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **ikonen** Kontroll block för pekare till Icon-widget

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON *icon)
{
    /* Call icon background draw. */
    gx_icon_background_draw(icon);

    /* Add custom drawing here */

    /* Draw child widgets. */
    gx_widget_children_draw(icon);
}
```

### <a name="see-also"></a>Se även

- gx_icon_create
- gx_icon_draw
- gx_icon_event_process
- gx_icon_pixelmap_set

## <a name="gx_icon_create"></a>gx_icon_create


Ikonen Skapa

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_create(
    GX_ICON *icon, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID pixelmap_id, 
    ULONG style,
    USHORT icon_id, 
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar den angivna widgeten ikon.

### <a name="parameters"></a>Parametrar

- **ikonen** Pekare mot ikon kontroll block
- **namn** Logiskt namn på ikon för widget
- **överordnad** Pekare till överordnad widget
- **pixelmap_id** Resurs-ID för Pixelmap
- **stil** Ikon format
- **icon_id** Programdefinierat ID för ikon
- **x** start x-koordinatens position
- **y** start y-koordinat position

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ikon som skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_icon”. */
status = gx_icon_create(&my_icon, “my_icon”, &my_parent,
    MY_PIXELMAP_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_ID,
    5, 30);

/* If status is GX_SUCCESS the icon “my_icon” has been created. */
```

### <a name="see-also"></a>Se även

- gx_icon_button_create
- gx_icon_draw
- gx_icon_pixelmap_set

## <a name="gx_icon_draw"></a>gx_icon_draw


Rita-ikonen

### <a name="prototype"></a>Prototyp

```C
VOID gx_icon_draw(GX_ICON *icon);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna widgeten ikon. Den här tjänsten kallas vanligt vis internt av GUIX som en del av en uppdaterings åtgärd på arbets ytan, men den exponeras också för programmet som kanske vill tillhandahålla en anpassad ritnings funktion och anropa standard ikon ritningen som en anpassad ritnings bas.

### <a name="parameters"></a>Parametrar

- **ikonen** Kontroll block för pekare till Icon-widget

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom icon drawing function. */

VOID my_icon_draw(GX_MENU *menu)
{
    /* Call default icon draw. */
    gx_icon_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_event_process"></a>gx_icon_event_process

Händelse bearbetning för Icon-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_event_process(
    GX_ICON *icon, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hanterar händelser som skickas till en GX_ICON widget.

### <a name="parameters"></a>Parametrar

- **ikonen** Kontroll block för pekare till Icon-widget
- **event_ptr** Pekare till GX_EVENT-struktur

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse för bearbetad ikon
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
switch(event_ptr->gx_event_type)
{
case GX_EVENT_SHOW:
    /* Do default handling. */
    status = gx_icon_event_process(icon, event_ptr);

    /* add your own handling here */
    break;
}
```

### <a name="see-also"></a>Se även

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_pixelmap_set"></a>gx_icon_pixelmap_set


Ange Pixelmap som ikon

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_pixelmap_set(
    GX_ICON *icon, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger Pixelmap för den angivna ikon-widgeten.

### <a name="parameters"></a>Parametrar

- **ikonen** Kontroll block för pekare till Icon-widget
- **normal_id** Resurs-ID för normal tillstånd
- **selected_id** Resurs-ID för vald tillstånd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap-ikonen har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set pixelmap for “my_icon”. */
status = gx_icon_pixelmap_set(&my_icon,
    MY_NOT_SELECTED_RESOURCE_ID,
    MY_SELECTED_ID);

/* If status is GX_SUCCESS, the icon “my_icon” has a pixelmap set. */
```

### <a name="see-also"></a>Se även

- gx_icon_button_create
- gx_icon_create
- gx_icon_draw

## <a name="gx_image_reader_create"></a>gx_image_reader_create


Skapa en instans av image Reader-modul

### <a name="prototype"></a>Prototyp

```C
UINT gx_image_reader_create(
    GX_IMAGE_READER *image_reader,
    GX_CONST GX_UBYTE *data, 
    INT data_size,
    GX_UBYTE color_format, 
    GX_UBYTE mode);
```

### <a name="description"></a>Beskrivning

Den här funktionen skapar en RAW-avbildnings läsare/avkodare för körning. För närvarande stöds endast bild typerna JPEG och PNG RAW. Den här tjänsten kräver att GX_SOFTWARE_DECODER_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **image_reader** Bild läsarens kontroll block
- **data** Pekare till rå data i indata.
- **data_size** Storlek på rå indata.
- **color_format** Formatet för den begärda utmatnings färgen.
- **läge** Flaggorna komprimera, rastrering och alfa.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bild läsaren har skapats
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltig data storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_IMAGE_READER my_image_reader;

“color format” could be set to:
    GX_COLOR_FORMAT_32ARGB
    GX_COLOR_FORMAT_24RGB
    GX_COLOR_FORMAT_565RGB
    GX_COLOR_FORMAT_8BIT_PALETTE

/* Create image reader “my_image_reader”. */
status = gx_image_reader_create(&my_image_reader, decoder_data,
    decoder_data_size,
    GX_COLOR_FORMAT_32ARGB,
    GX_IMAGE_READER_MODE_COMPRESS)

/* If status is GX_SUCCESS, “my_image_reader” has been successfully created. */
```

### <a name="see-also"></a>Se även

- gx_image_reader_start
- gx_image_reader_palette_set

## <a name="gx_image_reader_palette_set"></a>gx_image_reader_palette_set


Definiera bildreader-paletten

### <a name="prototype"></a>Prototyp

```C
UINT gx_image_reader_palette_set(
    GX_IMAGE_READER *image_reader,
    GX_COLOR *pal,
    UINT palsize);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in paletten för bild läsar kontroll block. Den här tjänsten kräver att GX_SOFTWARE_DECODER_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **image_reader** Bild läsarens kontroll block
- **PAL** Pekare till Palette
- **palsize** Storleken på paletten

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bildreader-paletten har angetts
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltig palett storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set “my_palette” as the palette of “my_image_reader”. */
status = gx_image_reader_palette_set(&my_image_reader, my_palette,
    my_palette_size);

/* If status is GX_SUCCESS the palette of “my_image_reader” has been set to “my_palette”. */
```

### <a name="see-also"></a>Se även

- gx_image_reader_create
- gx_image_reader_start

## <a name="gx_image_reader_start"></a>gx_image_reader_start

Starta dekomprimerings-och konverterings processen

### <a name="prototype"></a>Prototyp

```C
UINT gx_image_reader_start(
    GX_IMAGE_READER *image_reader, 
    GX_PIXELMAP *outmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten avkodar en RAW-avbildning till ett angivet färg format. För närvarande stöds endast bild typerna JPEG och PNG RAW. Detta kräver att GX_SOFTWARE_DECODER_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **image_reader** Bild läsarens kontroll block
- **Pixelmap** Utgående Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bild avkodning
- **GX_SYSTEM_MEMORY_ERROR** (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen
- **GX_NOT_SUPPORTED** (0x28) inmatnings avbildnings typ eller utmatnings färg format stöds inte
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_IMAGE_READER my_image_reader;
GX_PIXELMAP output_map;

/* Create my_image_reader here. */

/* Decoding a raw image according to the settings of “my_image_reader”. */
status = gx_image_reader_start(&my_image_reader, output_map)

/* If status is GX_SUCCESS “output_map” have been loaded with the requested pixelmap. */
```

### <a name="see-also"></a>Se även

- gx_image_reader_create
- gx_image_reader_palette_set

## <a name="gx_line_chart_axis_draw"></a>gx_line_chart_axis_draw


Rita linje diagram x, y-axel

### <a name="prototype"></a>Prototyp

```C
VOID gx_line_chart_axis_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar x-och y-axeln i ett linje diagram. Axel färgerna och linje bredds parametrarna hämtas från linje diagrammets informations struktur.

Den här tjänsten kallas vanligt vis internt av funktionen gx_line_chart_draw, men exponeras för programmet för att hjälpa till med att skriva anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **diagram** Linje diagram kontroll block.

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(&chart->gx_line_chart_info);

    /* Draw the data line */
    gx_line_chart_data_draw(&chart->gx_line_chart_info);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_create"></a>gx_line_chart_create


Skapa GX_LINE_CHART widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_create(
    GX_LINE_CHART *chart,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_LINE_CHART_INFO *info,
    ULONG style,
    USHORT chart_id, GX_RECTANGLE *size)
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett linje diagram fönster. Diagrammets ritnings parametrar och diagram data skickas via GX_LINE_CHART_INFO-strukturen.

GX_LINE_CHART baseras på GX_WINDOW och stöder alla GX_WINDOW-API: er.

### <a name="parameters"></a>Parametrar

- **diagram** Pekar på GX_LINE_CHART kontroll blocket.
- **namn** Valfritt linje diagram namn
- **överordnad** Överordnad widget eller GX_NULL
- **information** Struktur som definierar ritnings parametrar för linje diagrammet. **Bilaga i** innehåller en definition för GX_LINE_CHART_INFO-strukturen.
- **stil** Format flaggor för widget
- **chart_id** Diagrammets logiska ID-värde
- **storlek** Rektangel för kant linje för diagram fönster

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckat linje diagram skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create a line chart */
GX_LINE_CHART chart;
GX_RECTANGLE chart_size;
GX_LINE_CHART_INFO gx_chart_info;
GX_WINDOW_ROOT *root_window;

chart_size = root_window->gx_widget_size;

/* Initialize params for the GUIX base chart. */
gx_chart_info.gx_line_chart_min_val = DATA_MIN_VAL;
gx_chart_info.gx_line_chart_max_val = DATA_MAX_VAL;
gx_chart_info.gx_line_chart_max_data_count = MAX_DATA_COUNT;
gx_chart_info.gx_line_chart_active_data_count = 0;
gx_chart_info.gx_line_chart_axis_line_width = AXIS_LINE_WIDTH;
gx_chart_info.gx_line_chart_data_line_width = DATA_LINE_WIDTH;
gx_chart_info.gx_line_chart_data = chart_data;
gx_chart_info.gx_line_chart_line_color = GX_COLOR_ID_DATA_LINE;
gx_chart_info.gx_line_chart_axis_color = GX_COLOR_ID_AXIS_LINE;

/* Leave room for labels on bottom and right. */
gx_chart_info.gx_line_chart_left_margin = 0;
gx_chart_info.gx_line_chart_top_margin = 0;
gx_chart_info.gx_line_chart_right_margin = 80;
gx_chart_info.gx_line_chart_bottom_margin = 32;

status = gx_line_chart_create(&chart, “Line Chart”, root_window,
    &gx_chart_info, GX_STYLE_NONE, &chart_size);

/* If status is GX_SUCCESS, the “chart” has been successfully created. */
```

### <a name="see-also"></a>Se även

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_data_draw"></a>gx_line_chart_data_draw


Rita linje diagram data linje

### <a name="prototype"></a>Prototyp

```C
VOID gx_line_chart_data_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar linje diagrammets data linje. Egenskaperna för linje färg och linje bredd hämtas från linje diagramets informations struktur.

Den här tjänsten kallas vanligt vis internt av funktionen gx_line_chart_draw, men exponeras för programmet för att hjälpa till med att skriva anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **diagram** Linje diagram kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(chart);

    /* Draw the data line. */
    gx_line_chart_data_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_draw"></a>gx_line_chart_draw


Rita linje diagrammet

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Beskrivning

Det här är standard ritnings funktionen för linje diagram, som ritar diagrammets axel och data linje. Program tillhandahåller vanligt vis en anpassad ritnings funktion som ersätter standard ritningen för att lägga till saker som Kal streck, skala eller annan information till diagram axeln och data linjen som ritas av widgeten för bas linje diagrammet.

### <a name="parameters"></a>Parametrar

- **diagram** Pekar mot kontroll blocket för linje diagrammet.

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default line chart draw. */
    gx_line_chart_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_update"></a>gx_line_chart_update


Uppdatera linje diagram data linje

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_update(
    GX_LINE_CHART *chart, 
    INT *data,
    INT data_count)
```

### <a name="description"></a>Beskrivning

Den här tjänsten uppdaterar data matrisen som ritats av linje diagram fönstret och tvingar fram fönstret att rita om.

### <a name="parameters"></a>Parametrar

- **diagram** Linje diagram kontroll block
- **data** Data mat ris som ska ritas
- **data_count** Storlek på data mat ris

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text knappen har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
INT chart_data[100];
GX_LINE_CHART chart;

/* Update the data array associated with “chart”. */
status = gx_line_chart_update(&chart, chart_data, 100);

/* If status is GX_SUCCESS, the line chart data has been updated. */
```

### <a name="see-also"></a>Se även

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_y_scale_calculate"></a>gx_line_chart_y_scale_calculate


Beräkna skalnings värde för y-axel på den fasta punkten

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_y_scale_calculate(
    GX_LINE_CHART *chart,
    INT *return_val);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar skalning svärdet för den fasta punkten som används för att rita data värden på diagrammets Y-axel. Chart_info parametrar och diagram markerings ram används för att beräkna det här skalning svärdet.

### <a name="parameters"></a>Parametrar

- **diagram** Linje diagram kontroll block
- **return_val** Adress till värdet som ska innehålla det fasta punkt returvärdet.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) beräkning av värde för slutförd y-skalning
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_LINE_CHART chart;
INT y_scale;

/* Caluclate y scale value of “chart”. */
status = gx_line_chart_y_scale_calculate(&chart, &y_scale);

/* If status is GX_SUCCESS, y scale value of “chart” has been calculated. */
```

### <a name="see-also"></a>Se även

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update

## <a name="gx_menu_create"></a>gx_menu_create


Skapa en meny

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_create(
    GX_MENU *menu,GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_id, 
    ULONG style, 
    USHORT menu_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en meny som anges och associerar menyn med den angivna överordnade widgeten. Den accepterar alla typer av widget som underordnat meny alternativ. Om du vill infoga en widget som ett underordnat meny objekt, anropa **gx_menu_insert**.

GX_MENU härleds från GX_PIXELMAP_PROMPT och stöder alla gx_pixelmap_prompt API-tjänster.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block
- **namn** Namnet på menyn
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för text
- **fill_id** Resurs-ID för fyllning
- **stil** Widgetens format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **menu_id** Programdefinierat ID för menyn
- **storlek** Storlek på menyn

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad meny skapande
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_MENU my_menu;

/* Create “my_menu”. */
status = gx_menu_create(&my_menu, “my_menu”, parent, MY_TEXT_ID,
    MY_FILL_ID, GX_STYLE_ENABLED, MY_MENU_ID,
    &size);

/* If status is GX_SUCCESS, the menu was successfully created. */
```

### <a name="see-also"></a>Se även

- gx_accordion_meu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_draw"></a>gx_menu_draw


Rita-menyn

### <a name="prototype"></a>Prototyp

```C
VOID gx_menu_draw(GX_MENU *menu);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna menyn. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade meny-widgetar.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu draw. */
    gx_menu_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_event_process"></a>gx_menu_event_process

Händelse för process-menyn

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_event_process(GX_MENU *menu, GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna menyn. Den här tjänsten ska anropas som standard händelse hanterare av en anpassad meny händelse bearbetnings funktioner.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) för lyckad meny händelse process
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x23)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic menu event processing as part of custom event processing function. */

UINT custom_menu_event_process(GX_MENU *menu, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */

        /* Call default event process if this is a system event such as GX_EVENT_SHOW. */
        status = gx_menu_event_process(menu, event);
        break;

    default:
        /* Pass all other events to the default menu
           event processing */
        status = gx_menu_event_process(menu, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>Se även

- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_insert"></a>gx_menu_insert


Infoga ett nytt objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_insert(
    GX_MENU *menu, 
    GX_WIDGET *insert);
```

### <a name="description"></a>Beskrivning

Den här tjänsten infogar ett nytt objekt i menyn.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block
- **widget** Pekare till widgeten som ska infogas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har infogat ett nytt objekt i menyn
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Insert new item “my_widget” to the menu “my_menu”. */
status = gx_menu_insert(&my_menu, &my_widget);

/* If status is GX_SUCCESS the new item “my_widget” has been inserted to the menu “my_menu”. */
```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_remove"></a>gx_menu_remove


Ta bort ett objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_remvoe(
    GX_MENU *menu, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett objekt från menyn.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block
- **widget** Pekare till widget som ska tas bort

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har tagit bort meny alternativet
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Remove item “my_widget” from menu “my_menu” */
status = gx_menu_remove(&my_menu, &my_widget);

/* If status is GX_SUCCESS the item “my_widget” has been removed from menu “my_menu”. */
```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_text_draw"></a>gx_menu_text_draw


Text i Draw-menyn

### <a name="prototype"></a>Prototyp

```C
VOID gx_menu_text_draw(GX_MENU *menu);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar texten på en meny. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade meny-widgetar.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu background draw. */
    gx_pixelmap_prompt_background_draw(
                            (GX_PIXELMAP_PROMPT *)menu);

    /* Draw menu text. */
    gx_menu_text_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_offset_set

## <a name="gx_menu_text_offset_set"></a>gx_menu_text_offset_set


Ange meny text Rita förskjutning

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_text_offset_set(
    GX_MENU *menu, 
    GX_VALUE x_offset,
    GX_VALUE y_offset);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger x, y-förskjutning för meny text.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till Meny kontroll block
- **x_offset** X-koordinat för förskjutning
- **y_offset** Y-koordinat för förskjutning

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ange meny text Rita förskjutning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set text draw offset of menu “my_menu” to (20, 10). */
status = gx_menu_text_offset_set(&my_menu, 20, 10);

/* If status is GX_SUCCESS the text draw offset of menu “my_menu” has been set to (20, 10). */
```

### <a name="see-also"></a>Se även

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw

## <a name="gx_multi_line_text_button_create"></a>gx_multi_line_text_button_create


Text knappen Skapa flerradig linje

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_button_create(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för text knappar med flera rader. En flerradig text knapp visar knapp texten över 1-n rader. Det maximala antalet rader definieras av konstant GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES, vilket är standardvärdet 4. Rad brytningarna anges genom vagn retur och/eller vagn retur + rad matpar i text strängen som har tilldelats till text-knappen med flera rader.

GX_MULTI_LINE_TEXT_BUTTON härleds från GX_TEXT_BUTTON och stöder alla gx_text_button API-tjänster.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till kontroll block för text knapp
- **namn** Text knappens logiska namn
- **överordnad** Pekare till överordnad widget för knappen
- **text_id** Resurs-ID för text
- **stil** Text knapp format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **text_button_id** Programdefinierat ID för text knappen
- **storlek** Knappens storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text knappen har skapats med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create multi-line text button “my_text_button”. */
status = gx_multi_line_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS, the multi-line text button “my_text_button” was created. */
```

### <a name="see-also"></a>Se även

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_draw"></a>gx_multi_line_text_button_draw


Knapp för att rita flerradig text

### <a name="prototype"></a>Prototyp

```C
VOID gx_multi_line_text_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar text knappen med flera rader. Den här funktionen kallas vanligt vis internt av GUIX som en del av en uppdaterings åtgärd på arbets ytan, men den exponeras även för det program som kanske vill tillhandahålla en anpassad ritnings funktion och anropa standardvärdet för multi-line text-knappen som en anpassad ritnings bas.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till kontroll block för text knapp

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Draw the text button “my_text_button”. */
void MyButtonDraw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_multi_line_text_button_draw(&my_text_button);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_event_process"></a>gx_multi_line_text_button_event_process


Standard händelse hantering för text knappar med flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_button_event_process(
    GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är standard funktionen för händelse hantering för widgeten text knapp i flera rader. Den här funktionen görs tillgänglig för program som vill tillhandahålla anpassad händelse hantering för widgeten text knapp.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till kontroll block för text knapp
- **event_ptr** Händelse som ska bearbetas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hanterat händelse
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_button_event_process(button, event_ptr);
        /* add custom actions here */
        break;
    default:
        gx_multi_line_text_button_event_process(button, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Se även

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_draw"></a>gx_multi_line_text_button_text_draw


Stöd för ritnings funktion

### <a name="prototype"></a>Prototyp

```C
VOID gx_multi_line_text_button_text_draw(GX_MULTI_LINE_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Beskrivning

Den här stöd funktionen ritar text delen av en flerradig text-knapp. Den här funktionen anropas internt av gx_multi_line_text_button_draw (), och tillhandahålls som en separat API som bekvämlighet för program som definierar en anpassad ritnings funktion för flerradig text. Program som vill anpassa knappens bakgrunds ritning kan ge sin anpassade ritnings funktion och anropa multi_line_text_button_text_draw-tjänsten som en del av den anpassade ritningen för att rita knapp texten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till kontroll block för text knapp

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define a custom drawing function */
VOID my_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* insert code here to draw button background */

    /* call support function to do text drawing */
    gx_multi_line_text_button_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>Se även

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set


## <a name="gx_multi_line_text_button_text_id_set"></a>gx_multi_line_text_button_text_id_set


Ange text resurs-ID: t för text knappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_button_text_id_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id)
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger angivet sträng resurs-ID till text knappen. Strängen får innehålla tecken för ny rad som fungerar för att visa texten på flera rader i knapp fältet.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till kontroll block för text knapp
- **string_id** Resurs-ID för strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett sträng resurs-ID till text knappen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the string ID ”MY_STRING_ID” to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_id_set(
    &my_text_button, MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to “my_text_button”. */
```

### <a name="see-also"></a>Se även

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set"></a>gx_multi_line_text_button_text_set


Tilldela text knappen text (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_button_text_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_multi_line_text_button_text_set_ext ().

Den här tjänsten tilldelar den angivna strängen till text knappen. Om widgeten text_button skapades med Style GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen och därför måste gx_system_memmory_allocate_set-API: et anropas en gång innan tjänsten begärs. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till kontroll block för text knapp
- **text** pekare till den null-avslutade strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett texten till knappen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_MEMORY_ERROR** (0x30) allokerat minne har inte definierats
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
static GX_CHAR text[] = “myrstring”;

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set(&my_text_button, text);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>Se även

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set_ext"></a>gx_multi_line_text_button_text_set_ext


Tilldela text knappen text

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_button_text_set_ext(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_STRING *string)
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den angivna strängen till text knappen. Om widgeten text_button skapades med Style GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen och därför måste gx_system_memmory_allocate_set-API: et anropas en gång innan tjänsten begärs. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till kontroll block för text knapp
- **sträng** pekare till GX_STRING variabel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett texten till knappen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_MEMORY_ERROR** (0x30) allokerat minne har inte definierats
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
static GX_CHAR text[] = “myrstring”;
GX_STRING string;

string.gx_string_ptr = text;
string.gx_string_length = strlen(text);

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set_ext(&my_text_button, string);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_input_backspace"></a>gx_multi_line_text_input_backspace


Ta bort ett tecken före text markör position i flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_backspace(
    GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort det här meddelandet innan text markörens position i flera rader. Den här tjänsten kallas internt när en nyckel för Backsteg-händelsen tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) det framgångs rika text utrymmet i flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x23)
- **GX_FAILURE** (0X10) ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_multi_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_clear"></a>gx_multi_line_text_input_buffer_clear


Tar bort alla tecken från bufferten för inmatade filer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_buffer_clear(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla tecken från bufferten för inmatade filer.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) klar text buffert för flera rader rensad
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* clear input buffer of “my_text_input”. */
status = gx_multi_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_get"></a>gx_multi_line_text_input_buffer_get


Hämtar information om buffer för text indata-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_buffer_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    GX_CHAR **buffer_address,
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar buffertstorleken för en widget för text indata i flera rader.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **buffer_address** Adressen för indatabufferten
- **content_size** Antalet byte för indata
- **buffer_size** Storleken på indatabufferten

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad text hämtning med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *buffer_address;
UINT context_size;
UINT buffer_size;

/* Retrieves buffer information of “my_text_input” widget. */
status = gx_multi_line_text_input_buffer_get(&my_text_input,
    &buffer_address, &string_size,
    &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_char_insert"></a>gx_multi_line_text_input_char_insert


Infoga en tecken sträng vid aktuell markör position för text i flera rader (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_char_insert(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Beskrivning

Detta API är föråldrat och ersätts av gx_multi_line_text_input_char_insert_ext ().

Den här tjänsten infogar en tecken sträng i bufferten för text indata i flera rader vid den aktuella pekar positionen. Den här tjänsten kallas internt när en specifik nyckel händelsen tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **insert_str** Tecken sträng i UTF-8-format som ska infogas
- **insert_size** Antal byte som ska infogas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har infogat tecken strängen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) ogiltig sträng storlek
- **GX_FAILURE** (0X10) ogiltigt tecken eller är i storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
status = gx_multi_line_text_input_char_insert(&my_text_input,
    insert_text,
    GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the multi line text input widget has successfully insert the string. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_char_insert_ext

## <a name="gx_multi_line_text_input_char_insert_ext"></a>gx_multi_line_text_input_char_insert_ext


Infoga en tecken sträng vid aktuell markör position för text i flera rader (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_char_insert_ext(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten infogar en tecken sträng i bufferten för text indata i flera rader vid den aktuella pekar positionen. Den här tjänsten kallas internt när specifika Key Down-händelser tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **sträng** UTF-8-kodad tecken sträng som ska infogas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har infogat tecken strängen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) ogiltig sträng storlek
- **GX_FAILURE** (0X10) ogiltigt tecken eller är i storlek
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
GX_STRING string;

string.gx_string_ptr = insert_text;
string.gx_string_length = strlen(insert_text);

status = gx_multi_line_text_input_char_insert_ext(&my_text_input, &string);

/* If status is GX_SUCCESS the multi line text input widget has successfully inserted the string. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_create"></a>gx_multi_line_text_input_create


Skapa text indata från flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_create(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WINDOW *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    ULONG style, USHORT text_input_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för text indata i flera rader.

GX_MULTI_LINE_TEXT_INPUT härleds från GX_MULTI_LINE_TEXT_VIEW och stöder alla gx_multi_line_text_view-tjänster.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **namn** Namn på widgeten text inspelning
- **överordnad** Pekare till överordnad widget
- **input_buffer** Pekare till text-indatabufferten
- **buffer_size** Storlek på buffert för text ingång i byte
- **stil** Typ av widget för text inflöde. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **text_input_id** Programdefinierat ID för text inmatare
- **storlek** Mått för widgeten text inflöde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) data skapande av multi-line text har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_MULTI_LINE_TEXT_INPUT my_text_input;
GX_CHAR my_buffer[100];
GX_RECTANGLE size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 100, 200);

/* Create multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_create(&my_text_input,
    “my_text_input”, &my_parent,
    my_buffer, 100, GX_STYLE_BORDER_RAISED,
    MY_TEXT_INPUT_ID, &size);

/* If status is GX_SUCCESS, the text input “my_text_input” has been created. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_cursor_pos_get"></a>gx_multi_line_text_input_cursor_pos_get


Hämta text markör position för flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_cursor_pos_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_POINT cursor_pos);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar markörens position för mult text.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **cursor_pos** Markör position har hämtats

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat markörens position
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Retrieve the cursor position of “my_text_input”. */
GX_POINT cursor_pos;
status = gx_multi_line_text_input_cursor_pos_get(&my_text_input,
    &cursor_pos);

/* If status is GX_SUCCESS the cursor position has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_delete"></a>gx_multi_line_text_input_delete


Ta bort specialtecknet i text markörens position med flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_delete(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort specialtecknet efter text markörens position i flera rader. Den här tjänsten anropas internt när händelsen ta bort nyckel tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) tog bort ett blank steg efter markören
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_FAILURE** (0X10) ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_multi_line_text_input_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_down_arrow"></a>gx_multi_line_text_input_down_arrow


Flytta markören för text indata från flera rader till nästa rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_down_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar markören för text indata i flera rader till nästa rad. Den här tjänsten anropas internt när en NEDPIL-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat text ingångs markören till nästa rad
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_FAILURE** (0X10) ogiltig tecken-eller radhöjd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move input cursor to the next line. */
status = gx_multi_line_text_input_down_arrow(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to the next line. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_end"></a>gx_multi_line_text_input_end


Flytta text indata-markören för flera rader till slutet av den aktuella raden

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_end(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar widgeten text för text indata i slutet av den aktuella sträng raden. Den här tjänsten anropas internt när en end Key Down-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat text ingångs markören till slutet av den aktuella raden
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move input cursor to the end of current line. */
status = gx_multi_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, the multi line text input cursor has been moved to the end of the current line. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_event_process"></a>gx_multi_line_text_input_event_process


Standard händelse hantering för text indata från flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_event_process(
    GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är standard funktionen för händelse hantering för widgeten text indata i flera rader. Den här funktionen är tillgänglig för program som vill tillhandahålla anpassad händelse hantering för widgeten text indata i flera rader.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till kontroll block för text indata i flera rader
- **event_ptr** Händelse som ska bearbetas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hanterat händelse
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic multi line text
            input event processing */
        gx_multi_line_text_input_event_process(input, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_fill_color_set"></a>gx_multi_line_text_input_fill_color_set


Ange bakgrunds färg för text i flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_fill_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar fyllnings färger för widgeten text indata i flera rader.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **normal_fill_color_id** Resurs-ID för den normala fyllnings färgen som används i normalt läge
- **selected_fill_color_id** Resurs-ID för den valda fyllnings färgen som användes när widgeten får fokus
- **disabled_fill_color_id** Resurs-ID för den inaktiverade fyllnings färgen som användes när GX_STYLE_ENABLED inte är aktiv
- **readonly_fill_color_id** Resurs-ID för den skrivskyddade fyllnings färgen som användes när både GX_STYLE_ENABLED och GX_STYLE_INPUT_READONLY är aktiva.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett färger för multi-line text-indata
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set fill colors for the multi-line text input widget “my_text_input”. */

status = gx_multi_line_text_input_fill_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_FILL,
    GX_COLOR_ID_SELECTED_FILL,
    GX_COLOR_ID_DISABLED_FILL,
    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” has been successfully set. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_home"></a>gx_multi_line_text_input_home


Flytta text inmatade markören till början av den aktuella raden

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_home(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar markörens position för text insättning till början av den aktuella raden. Den här tjänsten anropas internt när en händelse för start nyckel tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till början av den aktuella raden
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move cursor to the start of the current line. */
status = gx_multi_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the start of the current line. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_left_arrow"></a>gx_multi_line_text_input_left_arrow


Flytta text indata från flera rader ett tecken till vänster

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_left_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Med den här tjänsten flyttas text indata för flera rader ett tecken till vänster. Den här tjänsten anropas internt när en vänster Key Down-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till vänster
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_FAILURE** (0X10) ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move the cursor one character to the left. */
status = gx_multi_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved one character to the left. */

```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_right_arrow"></a>gx_multi_line_text_input_right_arrow


Flytta mult med text markören ett tecken till höger

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_right_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Med den här tjänsten flyttas text indata för flera rader ett tecken till höger. Den här tjänsten anropas internt när en höger nyckel händelsen tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till höger
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move cursor one character to the right. */
status = gx_multi_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_add"></a>gx_multi_line_text_input_style_add


Lägg till text ingångs format med flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_style_add(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till format i en widget för text indata i flera rader.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **stil** Format som ska läggas till. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text med text ingångs format Lägg till
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Add style GX_STYTLE_CURSOR_ALWAYS to multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_add(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the style GX_STYLE_CURSOR_ALWAYS has been successfully added. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_remove"></a>gx_multi_line_text_input_style_remove


Ta bort format

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_remove(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort de angivna formaten från widgeten multi-line text-indata.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **stil** Format som ska tas bort. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) data skapande av multi-line text har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Remove style GX_STYLE_CURSOR_ALWAYS from text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_remove(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS, the style GX_STYLE_CURSOR_ALWAYS has been successfully removed. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_set"></a>gx_multi_line_text_input_style_set

Ange text ingångs format för flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_style_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger format för en widget för text indata i flera rader.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **stil** Format som ska anges. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) formaterad text format uppsättning med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set style GX_STYLE_CURSOR_ALWAYS for text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_set(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the text input style has been set */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_color_set"></a>gx_multi_line_text_input_text_color_set


Ange text färg för text i flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_text_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar text färger för widgeten multi-line text-indata.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för textinspelning i flera rader
- **normal_fill_color_id** Resurs-ID för normal text färg som används i normalt tillstånd
- **selected_text_color_id** Resurs-ID för den valda text färgen som användes när widgeten får fokus
- **disabled_text_color_id** Resurs-ID för den inaktiverade text färgen som användes när GX_STYLE_ENABLED inte är aktiv
- **readonly_text_color_id** Resurs-ID för den skrivskyddade text färgen som användes när både GX_STYLE_ENABLED och GX_STYLE_TEXT_INPUT_READONLY är aktiva

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett färger för multi-line text-indata
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set text colors for the multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_text_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT,
    GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the fill colors of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_select"></a>gx_multi_line_text_input_text_select


Markera text

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_text_select(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten markerar text text med text med det angivna start-och slut markerings indexet och markerar den markerade texten med de valda fyllnings-och text färgerna.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontroll block för text indata i flera rader
- **start_index** Index för det första markerade specialtecknet
- **end_index** Index för det senast markerade specialtecknet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text markering för text markering med text
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) index värde är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Select text between index [0, 9]. */
status = gx_multi_line_text_input_text_select(&my_text_input,
    0,9);

/* If status is GX_SUCCESS, the text between 
    index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_set"></a>gx_multi_line_text_input_text_set


Tilldela text till text ingången (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CHAR *text);
```

### <a name="description"></a>Beskrivning

Detta API är inaktuellt och ersätts av gx_multi_line_text_input_text_set_ext ().

Den här tjänsten tilldelar den angivna strängen till text indata för flera rader. Om den multi_line_text_input widgetens buffertstorlek är mindre än sträng längden kommer strängen att trunkeras.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontroll block för text indata i flera rader
- **text** pekare till den null-avslutade strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett texten till text indata för flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the string “my string” to the text button “my_text_input”. */
status = gx_multi_line_text_input_text_set(&my_text_input,
    “myrstring”);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_text_set_ext

## <a name="gx_multi_line_text_input_text_set_ext"></a>gx_multi_line_text_input_text_set_ext


Tilldela text till text

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den angivna strängen till text indata för flera rader. Om den multi_line_text_input widgetens buffertstorlek är mindre än sträng längden kommer strängen att trunkeras.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontroll block för text indata i flera rader
- **sträng** pekare till GX_STRING som ska tilldelas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett texten till text indata för flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the string “my string” to the text button “my_text_input”. */
GX_STRING string;
string.gx_string_ptr = “myrstring”;
string.gx_string_length = strlen(string.gx_string_ptr);

status = gx_multi_line_text_input_text_set_ext(&my_text_input,
    &string);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_up_arrow"></a>gx_multi_line_text_input_up_arrow


Flytta text insättnings markören i flera rader till föregående rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_up_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar markören för text indata i flera rader till föregående textrad. Den här tjänsten anropas internt när en Uppil Key Down-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till föregående rad
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move the cursor to the previous line. */
status = gx_multi_line_text_input_up_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved to the previous line. */

```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_create"></a>gx_multi_line_text_view_create


Skapa flerradig text-vy

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_create(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT text_view_id, 
    GX_CONST GX_RECTANGLE *size);

```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en GX_MULTI_LINE_TEXT_VIEW-widget. Den här widgeten är härledd från GX_WINDOW, och därför kan alla gx_window API-tjänster också användas med den här typen av widget.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **namn** Namn på widgeten text visning
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för text strängen
- **stil** Typ av widget för textvyer. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **text_view_id** Programdefinierat ID för text visning
- **storlek** Mått för widgeten textvyer

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skapat widgeten text visning med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_create(&my_text_view,
    “my_text_view”, &my_parent,
    TEXT_STRING_ID, GX_STYLE_BORDER_RAISED,
    MY_TEXT_VIEW_ID, &size);

/* If status is GX_SUCCESS the text view “my_text_view” has been successfully created. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_draw"></a>gx_multi_line_text_view_draw


Rita en widget för text visning med flera rader

### <a name="prototype"></a>Prototyp

```C
VOID gx_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW * text_view);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en widget för text visning med flera rader. Den här tjänsten anropas vanligt vis internt under uppdatering av arbets ytan, men kan också anropas från anpassade ritnings funktioner för flerradig text visning.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom multi line text view drawing function. */

VOID my_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW *view)
{
    /* Call default multi line text view draw. */
    gx_multi_line_text_view_draw(view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_event_process"></a>gx_multi_line_text_view_event_process


Bearbeta händelse för text visning i flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_event_process(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för en widget för textvyer med flera rader.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för text visning med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom event handler. */
UINT my_event_handler(GX_MULTI_LINE_TEXT_VIEW *view, GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_view_event_process(view, event_ptr);
        /* Add custom actions here. */
        break;
    default:
        gx_multi_line_text_view_event_process (view, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_font_set"></a>gx_multi_line_text_view_font_set


Ange teckensnitt som används i multi-line text-vy

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger teckensnittet för en widget för text visning med flera rader.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **font_id** Resurs-ID för teckensnittet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett teckensnitt för text visning med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set font ID FONT_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_font_set(&my_text_view, FONT_ID);

/* If status is GX_SUCCESS, the text view “my_text_view” will use the specified font to display its text. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_line_space_set"></a>gx_multi_line_text_view_line_space_set


Ange rad avstånd för flerradig text

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_line_space_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_BYTE line_space);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger avståndet mellan text rader för widgeten flerradig text visning.

### <a name="parameters"></a>Parametrar

- **Visa** Kontroll block för widgeten text visning i flera rader
- **line_space** Värde att ange

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett rad utrymme svärdet för vyn med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

```C
/* Set line space of “my_text_view” to 2. */
status = gx_multi_line_text_view_line_space_set(&my_text_view, 2);

/* If status is GX_SUCCESS, the line space of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_scroll_info_get"></a>gx_multi_line_text_view_scroll_info_get

Hämta text rullnings information i flera rader


### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_scroll_info_get(
    GX_MULTI_LINE_TEXT_VIEW *text_view, ULONG style,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar rullnings informationen för flera rader i textvisningen.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **Stil** GX_SCROLLBAR_HORIZONTAL eller GX_SCROLLBAR_VERTICAL
- **Information** Pekare till mål för rullnings information. **Bilaga i** innehåller en definition för GX_SCROLL_INFO-strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) kunde inte hämta rullnings information för text visning
- Widgeten **GX_FAILURE** (0x10) är inte synlig eller teckensnitts-ID: t för textvy är inte giltigt
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for multi-line text view “my_text_view”. */
status = gx_multi_line_text_view_scroll_info_get(&my_text_view,
    &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for multi-line text view “my_text_view”. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_color_set"></a>gx_multi_line_text_view_text_color_set


Ange text färgen för text visning med flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_color_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCe_ID disabled_text_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar text färgen till widgeten flerradig text visning.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **normal_text_color_id** Resurs-ID för normal text färg som används i normalt tillstånd
- **selected_text_color_id** Resurs-ID för den valda text färgen som användes när widgeten får fokus
- **disabled_text_color_id** Resurs-ID för den inaktiverade text färgen som användes GX_STYLE_ENABLED är inte aktiv

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett färger för vyn med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set text colors for the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_color_set(&my_text_view,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_id_set"></a>gx_multi_line_text_view_text_id_set


Ange system text sträng i text visning med flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID text_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger resurs-ID för en sträng till widgeten flerradig text visning.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **text_id** Resurs-ID för text strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett sträng-ID för vyn med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set string ID STRING_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_id_set(&my_text_view, STRING_ID);

/* If status is GX_SUCCESS the text id of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_set"></a>gx_multi_line_text_view_text_set


Ange användardefinierad sträng i text visning med flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en text sträng till widgeten flerradig text visning. Om widgeten text_view skapades med Style GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen och därför måste gx_system_memory_allocate_set-API: et anropas en gång innan tjänsten begärs. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste den tilldelade strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **text** NULL-terminerad text sträng

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett en sträng för vyn med flera rader
- **GX_SYSTEM_MEMORY_ERROR** (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set string “my string” to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_set(&my_text_view, “my string”);

/* If status is GX_SUCCESS the text of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_whitespace_set"></a>gx_multi_line_text_view_whitespace_set


Ange blank steg för text visning på flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_whitespace_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_UBYTE whitespace);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger avståndet mellan widgetar och klient områden för en flerradig widget för text visning.

### <a name="parameters"></a>Parametrar

- **text_view** Kontroll block för widgeten text visning i flera rader
- **blank steg** Marginal bredden mellan text_view widgeten och den visade texten, i bild punkter.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett tomt utrymme för vyn med flera rader
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set whitespace of “my_text_view” to 2. */
status = gx_multi_line_text_view_whitespace_set(&my_text_view, 2);

/* If status is GX_SUCCESS the whitespace of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>Se även

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set

## <a name="gx_numeric_pixelmap_prompt_create"></a>gx_numeric_pixelmap_prompt_create


Skapa numerisk Pixelmap-prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_pixelmap_prompt_create(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, GX_RESOURCE_ID fill_id,
    ULONG style, USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en numerisk Pixelmap prompt-widget. En numeric_pixelmap_prompt är bara en pixelmap_prompt som har en egen buffert och tillhandahåller ett gx_numeric_pixelmap_prompt_value_set (INT) API, buffertstorleken definieras av konstant GX_NUMERIC_PROMPT_BUFFER_SIZE, som är standardvärdet 16.

GX_NUMERIC_PIXELMAP_PROMPT härleds från GX_PIXELMAP_PROMPT och stöder alla gx_pixelmap_prompt API-tjänster.

### <a name="parameters"></a>Parametrar

- **prompt** Numeriskt Pixelmap-prompt, kontroll block
- **namn** Namn på prompt
- **överordnad** Kontroll block för överordnad widget
- **text_id** ID för resurs sträng
- **fill_id** Pixelmap-ID för fyllnads områden
- **stil** Typ av numerisk Pixelmap-prompt, **bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **pixelmap_prompt_id** Programdefinierat ID för prompt
- **storlek** Mått för numerisk Pixelmap-prompt

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) skapade en numerisk pixlemap-prompt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_create(&my_numeric_pix_prompt,
    “my_numeric_pix_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_FEEL_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_NUMERIC_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric pixelmap prompt “my_numeric_pix_prompt” has been created. */
```

### <a name="see-also"></a>Se även

- gx_numeric_pixelmap_format_function_set
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_format_function_set"></a>gx_numeric_pixelmap_prompt_format_function_set


Åsidosätt format funktion för numerisk Pixelmap-prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_pixelmap_format_function_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    OID (*format_func)(GX_NUMERIC_PIXELMAP_PROMPT *, INT));
```

### <a name="description"></a>Beskrivning

Den här tjänsten åsidosätter standardformat-funktionen för widgeten numerisk pixlemap-prompt. Funktionen standardformat konverterar det numeriska Pixelmap-prompt svärdet till en sträng och lagrar det i widgetens privata buffert. Med den här tjänsten kan programmet definiera sin egen format funktion för att formatera och lagra det numeriska Pixelmap-prompt svärdet i widgetens privata buffert.

### <a name="parameters"></a>Parametrar

- **prompt** Numeriskt Pixelmap-prompt, kontroll block
- **format_func** Funktionen format ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett numerisk pixlemap prompt format funktion
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define my numeric pixelmap format function. */
VOID my_format_function(GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100,
        prompt->gx_numeric_pixelmap_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_pixelmap_prompt_buffer);
    prompt->gx_numeric_pixelmap_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_pixelmap_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override default format function of “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_format_function_set(
    &my_numeric_pix_prompt,
    my_format_function);

/* If status is GX_SUCCESS the format function of “my_numeric_pix_prompt” has been override. */
```

### <a name="see-also"></a>Se även

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_value_set"></a>gx_numeric_pixelmap_prompt_value_set


Ange värde för numerisk pixlemap-prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_pixelmap_prompt_value_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ett heltals värde till en numerisk Pixelmap-prompt.

### <a name="parameters"></a>Parametrar

- **prompt** Numeriskt Pixelmap-prompt, kontroll block
- **värde** Heltals värde som ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) angav ett numeriskt Pixelmap-prompt-värde
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set a value to “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_value_set(&my_numeric_pix_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric pixelmap prompt “my_numeric_pix_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_format_function_set

## <a name="gx_numeric_prompt_create"></a>gx_numeric_prompt_create


Skapa numerisk prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_prompt_create( 
    GX_NUMERIC_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style, USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en numerisk prompt-widget. En numeric_-prompt är bara en prompt som har en egen buffert och som tillhandahåller ett gx_numeric_-prompt_value_set (INT) API, buffertstorleken definieras av konstant GX_NUMERIC_PROMPT_BUFFER_SIZE, som är standardvärdet 16.

GX_NUMERIC_PROMPT härleds från GX_PROMPT och stöder alla gx_prompt API-tjänster.

### <a name="parameters"></a>Parametrar

- **prompt** Numeriskt varnings kontroll block
- **namn** Namn på prompt
- **överordnad** Kontroll block för överordnad widget
- **text_id** ID för resurs sträng
- **stil** Typ av numerisk prompt, **bilaga D** innehåller fördefinierade generella format för alla widgetar samt widget-/regionsspecifika format.
- **prompt_id** Programdefinierat ID för prompt
- **storlek** Mått för numerisk prompt

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) skapade numerisk prompt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_numeric _prompt”. */
status = gx_numeric_prompt_create(&my_numeric_prompt,
    “my_numeric_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_NUMERIC_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric prompt “my_numeric_prompt” has been created. */
```

### <a name="see-also"></a>Se även

- gx_numeric_format_function_set
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_format_function_set"></a>gx_numeric_prompt_format_function_set


Åsidosätt format funktion för numerisk prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_format_function_set(
    GX_NUMERIC_PROMPT *prompt,
    VOID (*format_func)(GX_NUMERIC_PROMPT *, INT));
```

### <a name="description"></a>Beskrivning

Den här tjänsten åsidosätter standardformat-funktionen för en numerisk prompt-widget. Funktionen standardformat konverterar det numeriska värdet för prompten till en sträng och lagrar det i widgetens privata buffert. Med den här tjänsten kan programmet definiera sin egen format funktion för att formatera och lagra det numeriska prompt svärdet i widgetens privata buffert.

### <a name="parameters"></a>Parametrar

- **prompt** Numeriskt varnings kontroll block
- **format_func** Funktionen format ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett numerisk prompt formats funktion
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define my numeric format function. */
VOID my_format_function(GX_NUMERIC_PROMPT *prompt, INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100, prompt->gx_numeric_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_prompt_buffer);
    prompt->gx_numeric_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override the default format function of “my_numeric_prompt”. */
status = gx_numeric_prompt_format_function_set(&my_numeric_prompt,
    my_format_function);

/* If status is GX_SUCCESS, the format function of “my_numeric_prompt” has been override. */
```

### <a name="see-also"></a>Se även

- gx_numeric_prompt_create
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_value_set"></a>gx_numeric_prompt_value_set


Ange numeriskt prompt-värde

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_prompt_value_set(
    GX_NUMERIC_PROMPT *prompt, 
    INT value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger ett heltals värde för en numerisk prompt.

### <a name="parameters"></a>Parametrar

- **prompt** Numeriskt varnings kontroll block
- **värde** Heltals värde som ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) angav ett numeriskt uppvarnings värde
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set a value to “my_numeric_prompt”. */
status = gx_numeric_prompt_value_set(&my_numeric_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric prompt “my_numeric_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_numeric_prompt_create
- gx_numeric_format_function_set

## <a name="gx_numeric_scroll_wheel_create"></a>gx_numeric_scroll_wheel_create


Skapa ett numeriskt rullnings hjul

### <a name="prototype"></a>Prototyp


UINT gx_numeric_scroll_wheel_create (GX_NUMERIC_SCROLL_WHEEL * Wheel, GX_CONST GX_CHAR * namn, GX_WIDGET * Parent, INT start_val, INT end_val, ULONG Style, USHORT wheel_id, GX_CONST GX_RECTANGLE * storlek);

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en numerisk widget för rullnings hjul.

Ett numeriskt rullnings hjul är en typ av widget för rullnings hjul som används särskilt för att visa ett intervall med tal. Andra typer av widgetar rullnings hjul är också tillgängliga. Mer information om rullnings listens widget för rullnings hjul, widgetar och widget för widget finns i API för gx_scroll_wheel_create ().

GX_NUMERIC_SCROLL_WHEEL härleds från GX_TEXT_SCROLL_WHEEL och har stöd för alla gx_text_scroll_wheel-och gx_scroll_wheel-tjänster.

Alla typer av rullnings hjul genererar GX_EVENT_LIST_SELECT händelser till deras överordnade när rullnings hjulet rullas.

Ett numeriskt rullnings hjul kommer som standard att ha ABS (end_val – start_val) + 1 rader. Med andra ord kommer rullnings hjulet att visa varje värde mellan start_val och end_val, öka eller decrementing med 1 med varje rad. Observera att start_val kan vara större eller mindre än end_val, beroende på vilket sätt programmet vill att intervallet ska visas.

Om programmet vill ändra radens ökning kan det göra detta genom att anropa gx_scroll_wheel_total_rows_set () efter att det numeriska rullnings hjulet har skapats. Till exempel kan ett program som vill skapa ett rullnings hjul som visar värdena år 1980 till 2020, öka med 5, göra detta:

```C
gx_numeric_scroll_wheel_create(&wheel, GX_NULL, parent, 1980,
    2020, style, id, &size);

/* the years 1980 through 2020, inclusive, incrementing by 5 years,
yields 9 total rows */

gx_scroll_wheel_total_rows_set(&wheel, 9);
```

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till numeriskt kontroll block för rullnings hjul
- **namn** Logiskt namn på Pixelmap knapp-widget
- **överordnad** Pekare till överordnad widget
- **start_val** Start av numeriskt värde
- **end_val** Avslutande numeriskt värde
- **stil** Typ av kryss ruta. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **wheel_id** Programdefinierat ID för rullnings hjulet
- **storlek** Mått för widgeten rullnings hjul

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skapat ett numeriskt rullnings hjul
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “year_wheel”. */
status = gx_numeric_scroll_wheel_create(&year_wheel,
    “year_selector””, &parent,
    1980, 2040,
    GX_STYLE_ENABLED | GX_STYLE_TEXT_CENTER |
    GX_STYLE_TRANSPARENT | GX_STYLE_WRAP |
    GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    YEAR_WHEEL_ID,
    &size);

/* If status is GX_SUCCESS the scroll wheel “year_wheel” has been created. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_text_get

## <a name="gx_numeric_scroll_wheel_range_set"></a>gx_numeric_scroll_wheel_range_set


Tilldela ett värde intervall för ett numeriskt rullnings hjul

### <a name="prototype"></a>Prototyp

```C
UINT
gx_numeric_scroll_wheel_range_set(
    GX_NUMERIC_SCROLL_WHEEL *wheel,
    INT start_val, INT end_val);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar värde intervallet som tillåts och visas med en numerisk widget för rullnings hjul.

Ett numeriskt rullnings hjul är en typ av widget för rullnings hjul som används särskilt för att visa ett intervall med tal. Andra typer av widgetar rullnings hjul är också tillgängliga. Mer information om rullnings listens widget för rullnings hjul, widgetar och widget för widget finns i API för gx_scroll_wheel_create ().

Om detta API anropas återställs rullnings hjulets sammanlagda rader till ABS (end_val – start_val) + 1, vilket innebär att rullnings hjulet ökar med 1 för varje rad. Om du vill ändra detta kan programmet anropa gx_scroll_wheel_total_rows_set () för att ändra det totala antalet rader, vilket i praktiken ändrar värdets ökning mellan rader.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till numeriskt kontroll block för rullnings hjul
- **start_val** Start av numeriskt värde 
- **end_val** Avslutande numeriskt värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett ett numeriskt rullnings hjuls intervall
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar 

### <a name="example"></a>Exempel

```C
/* Change range of “rate” scroll wheel. */

status = gx_numeric_scroll_wheel_range_set(&year_wheel, 0, 200);

/* If status is GX_SUCCESS the scroll wheel range has been modified. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_pixelmap_button_create"></a>gx_pixelmap_button_create


Knappen Skapa Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_button_create(
    GX_PIXELMAP_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id,
    GX_RESOURCE_ID disabled_id,
    ULONG style,
    USHORT pixelmap_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Pixelmap knapp-widget.

GX_PIXELMAP_BUTTON härleds från GX_BUTTON och stöder alla gx_button-tjänster.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till Pixelmap knapp kontroll block
- **namn** Logiskt namn på Pixelmap knapp-widget
- **överordnad** Pekare till överordnad widget
- **normal_id** Resurs-ID för normal tillstånd
- **selected_id** Resurs-ID för vald tillstånd
- **disabled_id** Resurs-ID för inaktiverat tillstånd
- **stil** Typ av kryss ruta. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **pixelmap_button_id** Programdefinierat ID för Pixelmap-knappen
- **storlek** Pixelmap-knappens mått

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skapat Pixelmap-knappen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_pixelmap_button”. */
status = gx_pixelmap_button_create(&my_pixelmap_button,
    “my_pixelmap_button”, &my_parent,
    MY_NORMAL_RESOURCE_ID, MY_SELECTED_RESOURCE_ID,
    MY_DESELECTED_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_PIXELMAP_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap button “my_pixelmap_button” has been created. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_draw
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_draw"></a>gx_pixelmap_button_draw


Knappen Rita Pixelmap

### <a name="prototype"></a>Prototyp

```C
VOID gx_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en widget för Pixelmap knapp. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade Pixelmap knapp-widgetar.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till Pixelmap knapp kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom pixelmap button drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button)
{
    /* Call default pixelmap button draw. */
    gx_pixelmap_button_draw(button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_event_process"></a>gx_pixelmap_button_event_process


Händelse bearbetning för Pixelmap knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_button_event_process(
    GX_PIXELMAP_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tillhandahåller standard händelse hantering för widgeten Pixelmap-knapp.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till Pixelmap knapp kontroll block
- **event_ptr** Pekare till GX_EVENT-struktur

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap knapp Draw
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
switch(event_ptr->gx_event_type)
{
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_button_event_process(icon, event_ptr);
    
        /* add my own handling here */
        break;
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_pixelmap_set"></a>gx_pixelmap_button_pixelmap_set


Knappen tilldela pixelmaps

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_button_pixelmap_set(
    GX_PIXELMAP_BUTTON *button, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id, 
    GX_RESOURCE_ID disabled_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger pixelmaps till knappen Pixelmap.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till Pixelmap knapp kontroll block
- **normal_id** Resurs-ID för Pixelmap som ska användas som normalt tillstånd
- **selected_id** Resurs-ID för den Pixelmap som ska användas när knappen är markerad
- **disabled_id** Resurs-ID för den Pixelmap som ska användas när knappen är inaktive rad

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförde anger Pixelmap till knappen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_button_pixelmap_set (&my_pixelmap_button,
    NORMAL_ID, SELECTED_ID,
    DISABLED_ID);

/* If status is GX_SUCCESS the pixelmap button is properly configured with the specified pixelmaps. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_prompt_create"></a>gx_pixelmap_prompt_create


Skapa Pixelmap-prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_prompt_create(
    GX_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_pixelmap_id,
    ULONG style,
    USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Pixelmap-prompt-widget. En Pixelmap-prompt skiljer sig från en standard GX_PROMPT i så att den målar bakgrunden i prompten med hjälp av pixelmaps. Funktionen Create accepterar ett Pixelmap-ID, den normala tillstånds fyllnings Pixelmap. Upp till sex pixelmaps kan tilldelas Pixelmap-prompten.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till Pixelmap-promptens kontroll block
- **namn** Logiskt namn på Pixelmap prompt-widget
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för text
- **fill_id** Resurs-ID för fyllning
- **stil** Typ av kryss ruta. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **pixelmap_prompt_id** Programdefinierat ID för Pixelmap-prompten
- **storlek** Pixelmap-promptens dimensioner

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap-prompten har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_pixelmap_prompt”. */
status = gx_pixelmap_prompt_create(&my_pixelmap_prompt,
    “my_pixelmap_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_LEFT_RESOURCE_ID,
    MY_FILL_RESOURCE_ID, MY_RIGHT_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap prompt “my_pixelmap_prompt” has been created. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_draw"></a>gx_pixelmap_prompt_draw


Prompten Draw Pixelmap

### <a name="prototype"></a>Prototyp

```C
VOID gx_pixelmap_prompt_draw(GX_PIXELMAP_PROMPT *prompt);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en widget för Pixelmap-prompt. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade Pixelmap-prompt-widgetar.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till Pixelmap-promptens kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom pixelmap prompt drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_PROMPT *prompt)
{
    /* Call default pixelmap prompt draw. */
    gx_pixelmap_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_pixelmap_set"></a>gx_pixelmap_prompt_pixelmap_set


Koppla pixelmaps till prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_prompt_pixelmap_set(
    GX_PIXELMAP_PROMPT *prompt,
    GX_RESOURCE_ID normal_left_pixelmap,
    GX_RESOURCE_ID normal_fill_pixelmap,
    GX_RESOURCE_ID normal_right_pixelmap,
    GX_RESOURCE_ID selected_left_pixelmap,
    GX_RESOURCE_ID selected_fill_pixelmap,
    GX_RESOURCE_ID selected_right_pixelmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar Pixelmap-ID: n till Pixelmap-prompten. De vänstra, ifyllda och högra Pixelmap-ID: na används för att tillåta att programmet använder en uppsättning pixelmaps för att fråga efter olika bredder, men en gemensam höjd för att spara på lagrings kraven. Om vänster och höger ID inte används, ska de anges till 0. Om frågan ska rita på egen hand när den får fokus, används de valda Pixelmap-ID: na för detta ändamål. Om de valda ID: na inte används eller är samma som de normala ID: na, anger du dem till 0.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till Pixelmap-promptens kontroll block
- **normal_left_id** Resurs-ID för Pixelmap som ska användas på vänster sida i normalt läge
- **normal_fill_id** Resurs-ID för den Pixelmap som ska användas vid sidan av normal status
- **normal_right_id** Resurs-ID för Pixelmap som ska användas på höger sida i läget normal
- **selected_left_id** Resurs-ID för Pixelmap som ska användas på vänster sida i det valda läget
- **selected_fill_id** Resurs-ID för den Pixelmap som ska användas för att fylla i det valda läget
- **selected_right_id** Resurs-ID för Pixelmap som ska användas på höger sida i det valda läget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) har angett Pixelmap till prompten
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0X33) resurs-ID är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Assign pixelmap IDs to “my_prompt”. Only the normal state pixelmaps are used in this case */
status = gx_pixelmap_prompt_pixelmap_set (&my_prompt,
    normal_left_id, normal_fill_id,
    normal_right_id, 0, 0, 0);

/* If status is GX_SUCCESS the pixelmap prompt is properly configured with pixelmaps. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_slider_create"></a>gx_pixelmap_slider_create


Skapa Pixelmap-skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_slider_create(
    GX_PIXELMAP_SLIDER *slider,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_SLIDER_INFO *info,
    GX_PIXELMAP_SLIDER_INFO *pixelmap_info, ULONG style,
    USHORT pixelmap_slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Pixelmap Slider-widget.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontroll block för Pixelmap-skjutreglage
- **namn** Logiskt namn på Pixelmap Slider-widget
- **överordnad** Pekare till överordnad widget
- **information** Pekare till en GX_SLIDER_INFO-struktur som innehåller värden som definierar minimi värdet för skjutreglage, högsta värde, aktuellt värde och barr gränser. **Bilaga I** innehåller en definition för GX_SLIDER_INFO-strukturen.
- **pixelmap_info** Pekar till en GX_PIXELMAP_SLIDER_INFO struktur som definierar pixelmaps som används för att rita skjutreglagets bakgrund och barr. **Bilaga I** innehåller en definition för GX_PIXELMAP_SLIDER_INFO-strukturen. Skjutreglagets bakgrund kan använda en eller två pixelmaps. Om en, så ändras inte bakgrunden när nålventil flyttas. Om två bakgrunder definieras används bakgrunden före den första bakgrunds Pixelmap och bakgrunden efter den andra bakgrunds Pixelmap.
- **stil** Typ av skjutreglage. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **pixelmap_slider_id** Programdefinierat ID för Pixelmap-skjutreglaget
- **storlek** Pixelmap-promptens dimensioner

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skapat Pixelmap-skjutreglaget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SLIDER_INFO info;
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate slider information structure. */
info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_min_travel = 10;
info.gx_slider_info_max_tralvel = 10;
info.gx_slider_info_needle_width = 5;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Create “my_pixelmap_slider”. */
status = gx_pixelmap_slider_create(&my_pixelmap_slider,
                            “my_pixelmap_slider”, &my_parent,
                            &info, &pixelmap_info,
                            GX_STYLE_BORDER_RAISED,
                            MY_PIXELMAP_SLIDER_ID, &size);

/* If status is GX_SUCCESS the pixelmap slider “my_pixelmap_slider” has been created. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_draw"></a>gx_pixelmap_slider_draw


Skjutreglage för Drawing Pixelmap

### <a name="prototype"></a>Prototyp

```C
VOID gx_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *slider);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en Pixelmap Slider-widget. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade widgetar för skjutreglage med Pixelmap.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontroll block för Pixelmap-skjutreglage

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom pixelmap slider drawing function. */

VOID my_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *pixelmap_slider)
{
    /* Call default pixelmap slider draw. */
    gx_pixelmap_slider_draw(pixelmap_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_event_process"></a>gx_pixelmap_slider_event_process


Process Pixelmap Slider-händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_slider_event_process(
    GX_PIXELMAP_SLIDER *slider,
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna widgeten för Pixelmap skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till Pixelmap
- **skjutreglaget** kontroll block händelse pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap för skjutreglage
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom event processing function. */
UINT my_event_hanlder(GX_PIXELMAP_SLIDER *pixelmap_slider, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                    event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                  event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_pixelmap_set"></a>gx_pixelmap_slider_pixelmap_set


Tilldela pixelmaps till skjutreglaget

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_slider_pixelmap_set(
    GX_PIXELMAP_SLIDER *slider,
    GX_PIXELMAP_SLIDER_INFO *pixinfo);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger pixelmaps till Pixelmap-skjutreglaget.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontroll block för Pixelmap-skjutreglage
- **pixinfo** Pekar till en GX_PIXELMAP_SLIDER_INFO struktur som definierar pixelmaps som används för att rita skjutreglagets bakgrund och barr. **Bilaga I** innehåller en definition för GX_PIXELMAP_SLIDER_INFO-strukturen. Skjutreglagets bakgrund kan använda en eller två pixelmaps. Om en, så ändras inte bakgrunden när nålventil flyttas. Om två bakgrunder definieras används bakgrunden före den första bakgrunds Pixelmap och bakgrunden efter den andra bakgrunds Pixelmap.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) anger Pixelmap till skjutreglaget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_slider _pixelmap_set (&my_pixelmap_slider,
                                &pixelmap_info);

/* If status is GX_SUCCESS the pixelmap slider is properly configured with “pixelmap_info”. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_progress_bar_background_draw"></a>gx_progress_bar_background_draw


Rita förlopps indikatorns bakgrund

### <a name="prototype"></a>Prototyp

```C
VOID gx_progress_bar_background_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar bakgrunden för den angivna förlopps indikatorn. Den här funktionen anropas internt som en del av gx_progress_bar_draw (), men exponeras för programmet för att stödja de fall där programmet definierar en anpassad ritnings funktion för förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **förlopps indikator** Pekare till förlopps indikatorns kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_create"></a>gx_progress_bar_create


Skapa en förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_create(
    GX_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_PROGRESS_BAR_INFO *progress_bar_info,
    ULONG style, 
    USHORT progress_bar_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **namn** Logiskt namn
- **överordnad** Pekare till överordnad widget
- **progress_bar_info** Pekare till en GX_PROGRESS_BAR_INFO-struktur. **Bilaga I** innehåller en definition för GX_PROGRESS_BAR_INFO-strukturen.
- **stil** Typ av förlopps indikator. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **progress_bar_id** Programdefinierat ID för förlopps indikatorn
- **storlek** Mått för förlopps indikatorn

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd förlopps indikator skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PROGRESS_BAR_INFO info;
GX_RECTANGLE size;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

size.gx_rectangle_left = 10;
size.gx_rectangle_top = 10;
size.gx_rectangle_right = 110;
size.gx_rectangle_bottom = 140;

/* Create a progress bar with the specified information. */
status = gx_progress_bar_create(&my_progress_bar, GX_NULL, GX_NULL,
                        &info, GX_STYLE_BORDER_THIN,
                        0, &size);

/* If status is GX_SUCSESS the progress bar “my_progress_bar” has been successfully created. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_draw"></a>gx_progress_bar_draw


Rita en förlopps indikator

### <a name="prototype"></a>Prototyp

```C
VOID gx_progress_bar_draw(GX_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en widget för förlopps indikatorn. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för anpassade widgetar för förlopps indikator.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar draw. */
    gx_progress_bar_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_progress_bar_create
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_event_process"></a>gx_progress_bar_event_process


Förlopp i förlopps indikator händelsen

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_event_process(
    GX_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse i förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **event_ptr** Pekare till GX_EVENT-struktur

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd prompt skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_PROGRESS_BAR *progress_bar, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_progress_bar_create
- gx_progress_bar_event_draw
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_font_set"></a>gx_progress_bar_font_set


Ange teckensnitt för förlopps fältets text

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_font_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger teckensnittet för en widget för förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **font_id** Teckensnitts resurs-ID

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) teckensnitts uppsättning för slutförd förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status = gx_progress_bar_font_set(&progress_bar,
                                        GX_FONT_ID_MEDIUM);

/* if status is GX_SUCCESS, the font was successfully assigned. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_info_set"></a>gx_progress_bar_info_set


Ange informations struktur för förlopps indikatorn

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_info_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återställer informations strukturen för en widget för förlopps indikator.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **information** Pekare till en GX_PROGRESS_BAR_INFO-struktur. **Bilaga I** innehåller en definition för GX_PROGRESS_BAR_INFO-strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har återställt information om förlopps fältet
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PROGRESS_BAR_INFO info;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

status = gx_progress_bar_info_set(&progress_bar, &info);

/* if status == GX_SUCCESS the progress bar info was re-assigned. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_info_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_pixelmap_set"></a>gx_progress_bar_pixelmap_set


Ange Pixelmap som används för att rita förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_pixelmap_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den Pixelmap som används för att fylla förlopps indikatorns bakgrund.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **pixelmap_id** Resurs-ID för Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap för förlopps indikator har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status = gx_progress_bar_pixelmap_set(&progress_bar,
                                GX_PIXELMAP_ID_PROGRESS_FILL);

/* if status is GX_SUCCESS, the pixelmap was successfully assigned. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_pielmap_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_range_set"></a>gx_progress_bar_range_set


Ange ett värde intervall för en förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_range_set(
    GX_PROGRESS_BAR *progress_bar,
    INT min_value, 
    INT max_value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger värde intervallet för förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **MIN_VALUE** Minsta värde för förlopps fältet
- **MAX_VALUE** Max värde för förlopps indikator

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) intervall uppsättning för slutförd förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status = gx_progress_bar_range_set(progress_bar, 0, 100);

/* if status is GX_SUCCESS, the progress bar range was successfully assigned. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_range_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_color_set"></a>gx_progress_bar_text_color_set


Ange text färgen för en förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_text_color_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger text färgen för en förlopps indikator-widget.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **normal_text_color** Resurs-ID för normal text färg som används i normalt tillstånd
- **selected_text_color** Resurs-ID för den valda text färgen som användes när widgeten får fokus
- **disabled_text_color** Resurs-ID för inaktive rad textfärg som används när GX_STYLE_ENABLED inte är aktiv

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text färgs uppsättning för lyckad förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set text colors for the progress bar “my_progress_bar”*/
UINT status = gx_progress_bar_text_color_set(&my_progress_bar,
                        GX_COLOR_ID_NORMAL_TEXT,
                        GX_COLOR_ID_SELECTED_TEXT,
                        GX_COLOR_ID_DISABLED_TEXT);

/* if status is GX_SUCCESS, the progress bar text colors were successfully assigned. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_draw"></a>gx_progress_bar_text_draw


Rita förlopps indikator text

### <a name="prototype"></a>Prototyp

```C
VOID gx_progress_bar_text_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar texten i den angivna förlopps indikatorn. Den här funktionen anropas internt som en del av gx_progress_bar_draw (), men exponeras för programmet för att stödja de fall där programmet definierar en anpassad ritnings funktion för förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **förlopps indikator** Pekare till förlopps indikatorns kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_value_set"></a>gx_progress_bar_value_set


Ange aktuellt värde för en förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_value_set(
    GX_PROGRESS_BAR *progress_bar,
    INT value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar förlopps indikatorns aktuella värde. Widgeten förlopps indikator inaktive ras automatiskt och ritas om automatiskt när förlopps indikatorns värde ändras.

### <a name="parameters"></a>Parametrar

- **progress_bar** Förlopps indikatorns kontroll block
- **värde** Förlopps indikatorns aktuella värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades ange värdet för förlopps indikatorn
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status = gx_progress_bar_value_set(progress_bar, 50);

/* if status == GX_SUCCESS the progress bar value was successfully assigned. */
```

### <a name="see-also"></a>Se även

- gx_progress_bar_value_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw

## <a name="gx_prompt_create"></a>gx_prompt_create


Skapa prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_create(
    GX_PROMPT *prompt, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en prompt-widget.

GX_PROMPT härleds från GX_WIDGET och stöder alla gx_widget-tjänster.

### <a name="parameters"></a>Parametrar

- **Pekare** till överordnad widget
- **text_id** Resurs-ID för prompt-text
- **stil** Typ av prompt. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **prompt_id** Programdefinierat ID för prompt
- **storlek** Varnings mått

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd prompt skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_prompt”. */
status = gx_prompt_create(&my_prompt, “my_promPt”, &my_parent,
                    MY_PROMPT_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_PROPMT_ID, &size);

/* If status is GX_SUCCESS the prompt “my_prompt” has been created. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_draw"></a>gx_prompt_draw


Draw-prompt

### <a name="prototype"></a>Prototyp

```C
VOID gx_prompt_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en prompt-widget. Den här tjänsten anropas internt av GUIX under uppdatering av arbets ytan, men kan också anropas av anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom prompt drawing function. */

VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* Call default prompt draw. */
    gx_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_event_process"></a>gx_prompt_event_process


Process-prompt-händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna prompten. Den här tjänsten ska anropas som standard händelse hanterare av eventuella anpassade händelse bearbetnings funktioner i prompten.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot kontroll block
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för lyckad prompt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic prompt event processing as part of custom event processing function. */

UINT custom_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default prompt event processing */
        status = gx_prompt_event_process(prompt, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_font_set"></a>gx_prompt_font_set


Ange teckensnitt för prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_font_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger teckensnittet för en prompt-widget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **font_id** Resurs-ID för teckensnitt

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00), teckensnitts uppsättning för lyckad varning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the font of “my_prompt”. */
status = gx_prompt_font_set(&my_prompt, MY_PROMPT_FONT_ID);

/* If status is GX_SUCCESS the font for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_color_set"></a>gx_prompt_text_color_set


Ange text färg för prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_color_set(
    GX_PROMPT *prompt,
    GX_RESOURCE_ID normal_color,
    GX_RESOURCE_ID selected_color,
    GX_RESOURCE_ID disabled_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger text färgen för en prompt-widget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **normal_color** Resurs-ID för färg för normal text. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **selected_color** Resurs-ID för den valda texten som används när widgeten får fokus. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **disabled_color** Resurs-ID för färg inaktive rad text som används när GX_STYLE_ENABLED inte är aktiv. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text färgs uppsättning för lyckad prompt
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET_SIZE** (0X14) ogiltig widgets storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the text color of “my_prompt”. */
status = gx_prompt_text_color_set(&my_prompt,
                    GX_COLOR_ID_BLACK,
                    GX_COLOR_ID_LIGHTGRAY,
                    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_draw"></a>gx_prompt_text_draw


Stöd för ritnings funktion

### <a name="prototype"></a>Prototyp

```C
VOID gx_prompt_text_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Beskrivning

Den här stöd funktionen ritar text delen av en prompt. Den här funktionen anropas internt av gx_prompt_draw () och tillhandahålls som en separat API som en bekvämlighet för program som definierar en anpassad prompt-funktion. Program som vill anpassa bakgrunds ritningen kan ge sin anpassade ritnings funktion och anropa den gx_prompt_text_draw tjänsten som en del av den anpassade ritningen för att rita uppslags texten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till varnings kontroll blocket

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Define a custom drawing function */
VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* insert code here to draw prompt background */

    /* call support function to do text drawing */
    gx_prompt_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) prompt);
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get"></a>gx_prompt_text_get


Hämta prompt-text (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_CHAR **return_text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_prompt_text_get_ext ().

Den här tjänsten hämtar texten i en prompt-widget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **return_text** Pekare till mål för text

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) framgångs text Hämta
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PROMPT my_prompt;
GX_CHAR *my_prompt_text;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get(&my_prompt, &my_prompt_text);

/* If status is GX_SUCCESS the pointer “my_prompt_text” points to the text displayed by “my_prompt”. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get_ext"></a>gx_prompt_text_get_ext


Hämta frågetext

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_STRING *return_string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar strängen för en prompt-widget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **return_string** Pekare till mål för sträng

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) framgångs text Hämta
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PROMPT my_prompt;
GX_STRING my_prompt_string;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get_ext(&my_prompt, &my_prompt_string);

/* If status is GX_SUCCESS then my_prompt_string has been initialize to hold a copy of the prompt string. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_id_set"></a>gx_prompt_text_id_set


Ange text-ID för prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_id_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID string_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger sträng-ID för widgeten text varning.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **string_id** Resurs-ID för strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ID för lyckad prompt-text har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_SYSTEM_MEMORY_ERROR** (0X30) minnes fri funktion har inte definierats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the string ID of “my_prompt”. */
status = gx_prompt_text_id_set(&my_prompt, MY_STRING_ID);

/* If status is GX_SUCCESS the text ID for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_prompt_text_set"></a>gx_prompt_text_set


Ange frågetext (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_set(
    GX_PROMPT *prompt, 
    GX_CHAR *text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten har ersatts av gx_prompt_text_set_ext ().

Den här tjänsten anger texten i en prompt-widget. Om widgeten prompt skapades med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

GX_PROMPT härleds från GX_WIDGET, och därför kan alla gx_widget API-tjänster användas med GX_PROMPT.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **text** Pekare till text

### <a name="return-values"></a>Retur värden

- Text uppsättning för **GX_SUCCESS** (0x00) har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Minnes tilldelnings funktionen för **GX_SYSTEM_MEMORY_ERROR** (0x30) har inte definierats
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the text of “my_prompt” to “my_text”. */
status = gx_prompt_text_set(&my_prompt, “my_text”);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_prompt_text_set_ext"></a>gx_prompt_text_set_ext

Ange frågetext

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_set_ext(
    GX_PROMPT *prompt,
    GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger texten i en prompt-widget. Om widgeten prompt skapades med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

GX_PROMPT härleds från GX_WIDGET, och därför kan alla gx_widget API-tjänster användas med GX_PROMPT.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare mot varnings kontroll block
- **text** Pekare till text

### <a name="return-values"></a>Retur värden

- Text uppsättning för **GX_SUCCESS** (0x00) har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Minnes tilldelnings funktionen för **GX_SYSTEM_MEMORY_ERROR** (0x30) har inte definierats
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING new_string;
new_string.gx_string_ptr = “my_text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set the text of “my_prompt” to “new_string”. */
status = gx_prompt_text_set(&my_prompt, &new_string);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_radial_progress_bar_anchor_set"></a>gx_radial_progress_bar_anchor_set


Ange start vinkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_anchor_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger start vinkeln för den radiella förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **vinkel** Den cirkelformade bågens start vinkel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) slut punkts uppsättning för radiellt förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE start_angle = 90;

/* Set the start angle of “my_progress_bar” to 90 degree. */
status = gx_radial_progress_bar_anchor_set(&my_progress_bar, start_angle);

/* If status is GX_SUCCESS the anchor value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_background_draw"></a>gx_radial_progress_bar_background_draw


Rita bakgrund

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_progress_bar_background_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en bakgrund för en radiell förlopps indikator. Den här tjänsten refereras internt av gx_radial_progress_bar_draw funktionen, men exponeras för användning av programmet i de fall där programmet definierar en anpassad ritnings funktion för radiell förlopps indikator

### <a name="parameters"></a>Parametrar

- **förlopps indikator** Pekare till kontroll block för radiellt förlopps indikator

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar background draw. */
    gx_radial_progress_bar_background_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```
### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_create"></a>gx_radial_progress_bar_create


Skapa radiell förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_create(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_PROGRESS_BAR_INFO *info,
    ULONG style
    USHORT id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en radiell förlopps indikator.

Om widgeten format GX_STYLE_ENABLED används i förlopps indikatorn, accepterar förlopps indikatorn pen_down, pen_drag och pen_up inmatade för att ändra förlopps indikatorns aktuella värde.

Widgets formatet GX_STYLE_PROGRESS_TEXT_DRAW kan användas för att rita förlopps indikatorns värde som text inom förlopps indikator området. Om det här formatet används i kombination med formatet GX_STYLE_PROGRESS_PERCENT visas förlopps indikatorns värde i procent. Annars visas förlopps indikatorns värde som det aktuella vinkel värdet.

### <a name="parameters"></a>Parametrar

- **förlopps indikator** Kontroll av pekare till radiellt förlopps indikator
- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **namn** Namn på radiell förlopps indikator
- **överordnad** Pekare till överordnad widget
- **information** Pekare till en GX_RADIAL_PROGRESS_BAR-struktur. **Bilaga I** innehåller en definition för GX_RADIAL_PROGRESS_BAR-strukturen.
- **stil** Typ av radiell förlopps indikator
- **ID** -Programdefinierat ID för förlopps indikatorn

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) skapa radiell förlopps indikator skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_WIDGET** (0X12) ogiltig överordnad widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                        GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                        GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                        GX_COLOR_ID_SELECTED_FILL;

/* Create a radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_create(&my_progress_bar,
                    “my_progress_bar”, parent, &info,
                    GX_STYLE_ENABLED | GX_STYLE_TRANSPARENT |
                    GX_STYLE_PROGRESS_TEXT_DRAW,
                    ID_MY_RADIAL_PROGRESS);

/* If status is GX_SUCCESS the radial progress bar “my_progress_bar” has been created. */
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_draw"></a>gx_radial_progress_bar_draw


Rita en radiell förlopps indikator

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en radiell förlopps indikator. Den här tjänsten används internt som den gx_radial_progress_bar_create funktionen refererar till, men exponeras för användning av programmet i de fall där programmet definierar en anpassad ritnings funktion för radiell förlopps indikator.

### <a name="parameters"></a>Parametrar

- **förlopps indikator** Pekare till kontroll block för radiellt förlopps indikator

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar draw. */
    gx_radial_progress_bar_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_size_calculate
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_event_process"></a>gx_radial_progress_bar_event_process


Händelse för process radiell förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_event_process(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för en radiell förlopps indikator. Den här funktionen refereras internt av funktionen gx_radial_progress_bar_create, men exponeras för användning av programmet i de fall där programmet definierar en anpassad funktion för radiell förlopps händelse bearbetning.

### <a name="parameters"></a>Parametrar

- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för radiell förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_RADIAL_PROGRESS_BAR *radial_progress, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
        case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_font_set"></a>gx_radial_progress_bar_font_set


Ange teckensnitt för radiellt förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_font_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger teckensnittet för en widget för radiellt förlopps indikator. Den här parametern har ingen inverkan om widgeten format GX_STYLE_PROGRESS_TEXT_DRAW inte har angetts.

### <a name="parameters"></a>Parametrar

- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **font_id** Resurs-ID för teckensnitt

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) teckensnitts uppsättning för radiell förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set font for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_font_set(&my_progress_bar, font);

/* If status is GX_SUCCESS the font of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_info_set"></a>gx_radial_progress_bar_info_set


Ange information om radiell förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_info_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RADIAL_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återställer de informations parametrar som tilldelats den radiella förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **information** Information struktur om pekare till radiell förlopps indikator. **Bilaga I** innehåller en definition för GX_RADIAL_PROGRESS_BAR_INFO-strukturen.

### <a name="return-values"></a>Retur värden

- Information om den sammanställda radiella förlopps indikatorn **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                GX_COLOR_ID_SELECTED_FILL;

/* Set appearance information for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_info_set(&my_progress_bar, &info);

/* If status is GX_SUCCESS the appearance information of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_color_set"></a>gx_radial_progress_bar_text_color_set


Ange textfärg för radiellt förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_text_color_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger text färgen för den radiella förlopps indikatorn. Det här värdet används endast om formatet GX_STYLE_PROGRESS_TEXT_DRAW har angetts.

### <a name="parameters"></a>Parametrar

- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **normal_color** Resurs-ID för text färgen i normalt läge. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **selected_color** Resurs-ID för textfärg när widgeten får fokus. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **disabled_color** Resurs-ID för text färgen om format GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text färgs uppsättning för radiellt förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set text color for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_color_set(&my_progress_bar,
                            GX_COLOR_ID_NORMAL_TEXT,
                            GX_COLOR_ID_SELECTED_TEXT,
                            GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_draw"></a>gx_radial_progress_bar_text_draw


Text för att rita radiell förlopps indikator

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_progress_bar_text_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar texten i den angivna radiella förlopps indikatorn. Den här funktionen anropas internt som en del av gx_radial_progress_bar_draw (), men exponeras för programmet för att stödja de fall där programmet definierar en anpassad ritnings funktion för förlopps indikatorn.

### <a name="parameters"></a>Parametrar

- **förlopps indikator** Pekare till kontroll block för radiellt förlopps indikator

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Draw text for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_draw (&my_progress_bar);

/* If status is GX_SUCCESS the text of “my_progress_bar” has been drawn. */

/* Write a custom radial progress bar drawing function. */
VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Add your own background draw here. */

    /* Call default radial progress bar text draw. */
    gx_radial_progress_bar_text_draw(radial_progress);

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_value_set"></a>gx_radial_progress_bar_value_set


Ange värde för radiell förlopps indikator

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_value_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger värdet för radiell förlopps indikator. Det tilldelade värdet är begränsat till intervallet [-360, 360], vilket definierar det möjliga intervallet med vinkel värden för den aktuella platsen för förlopps indikatorn. Programmet måste skala det verkliga värdet som anges för att tilldela ett vinkel värde till widgeten för förlopps indikatorn.

Förlopps indikatorn ritas så att det aktuella värdet anger vinkeln delta mellan ankar punkten och slut punkten för den övre bågen. Negativa värden gör att bågen ritas i en medsols riktning med början vid ankar positionen. Positivt aktuellt värde gör att bågen ritas in i riktningen medurs som börjar vid fäst punkten.

Om du till exempel vill rita en båge som börjar överst i bågen (12 klockan) och slutar till höger (tre klockan), tilldelar du ett ankar värde på 90 grader och ett aktuellt värde på-90 grader.

### <a name="parameters"></a>Parametrar

- **förlopps** indikator pekare till kontroll block för radiellt förlopps indikator
- **värde** Nytt förlopps indikator värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) värde uppsättning för radiell förlopps indikator
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltiga pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE new_value = 180;

/* Set value for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_value_set(&my_progress_bar,
                                        new_value);

/* If status is GX_SUCCESS the value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Se även

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw

## <a name="gx_radio_button_create"></a>gx_radio_button_create


Knappen Skapa alternativ

### <a name="prototype"></a>Prototyp

```C
UINT gx_radio_button_create(
    GX_RADIO_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, ULONG style,
    USHORT radio_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en alternativ knapp-widget. GX_RADIO_BUTTON härleds från GX_TEXT_BUTTON och därför stöds alla gx_text_button tjänster också av den här widgeten.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till kontroll block för radio knapp
- **namn** Logiskt namn för widgeten alternativ knapp
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för alternativ knapp
- **stil** Typ av alternativ knapp. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **radio_button_id** Programdefinierat ID för alternativ knappen
- **storlek** Alternativ knappens mått

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) alternativ knapp har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_** STORLEK (0x19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_radio_button”. */
status = gx_radio_button_create(&my_radio_button, “my_radio_button”, &my_parent,
                    MY_RADIO_BUTTON_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_RADIO_BUTTON_ID, &size);

/* If status is GX_SUCCESS the radio button “my_radio_button” has been created. */
```
### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_draw

## <a name="gx_radio_button_draw"></a>gx_radio_button_draw


Knappen Rita alternativ

### <a name="prototype"></a>Prototyp

```C
VOID gx_radio_button_draw(GX_RADIO_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en alternativ knapp-widget. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan också anropas av åsidosatta ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **knapp** Kontroll block för widgeten alternativ knapp

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom radio button drawing function. */

VOID my_radio_button_draw(GX_RADIO_BUTTON *radio_button)
{
    /* Call default radio button draw. */
    gx_radio_button_draw(radio_button);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radio_button);
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radio_button_pixelmap_set"></a>gx_radio_button_pixelmap_set


Ange pixelmaps för alternativ knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_radio_button_pixelmap_set(
    GX_RADIO_BUTTON *button,
    GX_RESOURCE_ID off_id,
    GX_RESOURCE_ID on_id,
    GX_RESOURCE_ID off_disabled_id,
    GX_RESOURCE_ID on_disabled_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar pixelmaps som ska visas med den angivna alternativ knappen för varje knapp läge. Resurs-ID: n kan dupliceras.

### <a name="parameters"></a>Parametrar

- **off_id** Pixelmap som används för alternativ knappens av tillstånd
- **on_id** Pixelmap används för radio knapps läge
- **off_disabled_id** Pixelmap används för alternativ knappen inaktiverat och inaktiverat
- **on_disabled_id** Pixelmap som används för alternativ knappen inaktiverat och på status

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) alternativ knapp pixelmaps inställd
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set pixelmap for “my_radio_button”. */
status = gx_radio_button_pixelmap_set(&my_radio_button,
                                MY_OFF_PIXELMAP,
                                MY_ON_PIXELMAP,
                                MY_OFF_DISABLED_PIXELMAP,
                                MY_ON_DISABLED_PIXELMAP);

/* If status is GX_SUCCESS the pixelmaps for radio button “my_radio_button” has been set. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radial_slider_anchor_angles_set"></a>gx_radial_slider_anchor_angles_set


Ange docknings lista för radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_anchor_angles_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE *anchor_angles, 
    USHORT anchor_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger fäst punkter för radiellt skjutreglage. Om du anger en fäst vinkel lista, är den radiella skjutreglaget vinkel en av de definierade fäst vinklarna.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för radiellt skjutreglage
- **anchor_angles** Vinkel lista som ska anges
- **anchor_count** Antal ankar vinklar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) har angetts
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget
- **GX_INVALID_VALUE** (0X22) ogiltig fäst lista

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE anchor_angles[]={0, 30, 60, 90, 120, 150, 180};
USHORT anchor_count = 7;

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                anchor_angles, anchor_count);

/* If status is GX_SUCCESS the anchor angles have been set for “my_radial_slider”. */

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                GX_NULL, 0);

/* If status is GX_SUCCESS the anchor angles have been removed from “my_radial_slider”. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_angle_set"></a>gx_radial_slider_angle_set

Ange vinkel för radiella skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_angle_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE new_angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger ett nytt vinkel värde för radiellt skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **new_angle** Nytt vinkel värde som ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) vinkel uppsättning för radiellt hörn
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set “my_radial_slider” angle to 0 degree(3 o’clock position). */
status = gx_radial_slider_angle_set(&my_radial_slider, 0);

/* If status is GX_SUCCESS the value of “my_radial_slider” has been set to 0 degree. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_set"></a>gx_radial_slider_animation_set


Information om animering av skapa radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_animation_set(
    GX_RADIAL_SLIDER *slider,
    USHORT steps, USHORT delay, 
    USHORT animation_style,
    VOID (*animation_update_callback)(GX_RADIAL_SLIDER *slider));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger animeringssekvenser, fördröjnings-och animeringsalternativ för radiella skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **steg** Totalt antal steg för en animering
- **fördröjning** Fördröjnings tid för varje steg i animeringen
- **animation_style** Över gångs funktions typ, inkluderar:
  - GX_ANIMATION_BACK_EASE_IN
  - GX_ANIMATION_BACK_EASE_OUT
  - GX_ANIMATION_BACK_EASE_IN_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN
  - GX_ANIMATION_BOUNCE_EASE_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN_OUT
  - GX_ANIMATION_CIRC_EASE_IN
  - GX_ANIMATION_CIRC_EASE_OUT
  - GX_ANIMATION_CIRC_EASE_IN_OUT
  - GX_ANIMATION_CUBIC_EASE_IN
  - GX_ANIMATION_CUBIC_EASE_OUT
  - GX_ANIMATION_CUBIC_EASE_IN_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN
  - GX_ANIMATION_ELASTIC_EASE_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN_OUT
  - GX_ANIMATION_EXPO_EASE_IN
  - GX_ANIMATION_EXPO_EASE_OUT
  - GX_ANIMATION_EXPO_EASE_IN_OUT
  - GX_ANIMATION_QUAD_EASE_IN
  - GX_ANIMATION_QUAD_EASE_OUT
  - GX_ANIMATION_QUAD_EASE_IN_OUT
  - GX_ANIMATION_QUART_EASE_IN
  - GX_ANIMATION_QUART_EASE_OUT
  - GX_ANIMATION_QUART_EASE_IN_OUT
  - GX_ANIMATION_QUINT_EASE_IN
  - GX_ANIMATION_QUINT_EASE_OUT
  - GX_ANIMATION_QUINT_EASE_IN_OUT
  - GX_ANIMATION_SINE_EASE_IN
  - GX_ANIMATION_SINE_EASE_OUT
  - GX_ANIMATION_SINE_EASE_IN_OUT
- **animation_update_callback** Användardefinierad callback-funktion som anropas efter varje steg i animeringen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) animeringseffekten för radiellt skjutreglage
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
VOID animation_callback(GX_RADIAL_SLIDER *slider)
{
    /* This function will be called after each animation step,
    add custom code here. */
}

/* Set animation info for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 15, 2,
                                GX_ANIMATION_CIRC_EASE_IN_OUT,
                                animation_callback);

/* If status is GX_SUCCESS the radial slider needle will move with specified animation. */

/* Disable animation for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 0, 0,
                                        0, 0);

/* If status is GX_SUCCESS the radial slider needle will move without animation. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_start"></a>gx_radial_slider_animation_start


Ange nytt radiellt Slider-värde med animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_animation_start(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE target_angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en animering för att flytta skjutreglaget från den aktuella positionen till den angivna positionen.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **target_angle** Mål vinkel värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) animeringseffekten för radiellt start
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Start an animation to move radial slider needle from
current position to 90 degree position. */
status = gx_radial_slider_animation_start(&my_radial_slider, 90);

/* If status is GX_SUCCESS the radial slider needle animation has been started. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_create"></a>gx_radial_slider_create


Skapa radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_create(
    GX_RADIAL_SLIDER *slider,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_SLIDER_INFO *info,
    ULONG style,
    USHORT slider_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för radiellt skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **namn** Widgeten logiskt namn på radiell Slider
- **överordnad** Pekare till överordnad widget
- **information** Definition av utseende för radiellt skjutreglage, **bilaga i** innehåller definition för GX_RADIAL_SLIDER_INFO.
- **stil** Typ av alternativ knapp. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **radio_button_id** Programdefinierat ID för radiellt skjutreglage
- **storlek** Mått för radiellt skjutreglage

### <a name="return-values"></a>Retur värden

- Skapa **GX_SUCCESS** (0x00) radiellt skjutreglaget skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_** STORLEK (0x19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_WIDGET** (0X12) ogiltig överordnad widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RADIAL_SLIDER_INFO info;
GX_RECTANGLE size;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Define widget size. */
gx_utility_rectangle_define(&size, 0, 0, 200, 200);

/* Create “my_radial_slider”. */
status = gx_radial_slider_create(&my_radial_slider,
                                “my_radial_slider”, &my_parent,
                                &info, GX_STYLE_ENABLED,
                                MY_RADIAL_SLIDER_ID, &size);

/* If status is GX_SUCCESS the radial slider “my_radial_slider” has been created. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_draw"></a>gx_radial_slider_draw


Skjutreglage för Rita radiell

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_slider_draw(GX_RADIAL_SLIDER *slider);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar ett radiellt skjutreglage. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan också anropas av åsidosatta ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom radio button drawing function. */

VOID my_radial_slider_draw(GX_RADIAL_SLIDER *radial_slider)
{
    /* Call default radial slider draw. */
    gx_radio_slider_draw(radial_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_event_process"></a>gx_radial_slider_event_process


Process radiellt Slider-händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_event_process(
    GX_RADIAL_SLIDER *slider,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse i ett radiellt skjutreglage. Den här tjänsten ska anropas som standard händelse hanterare av eventuella anpassade radiella skjutreglage Event Processing functions.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för att genomföra radiellt skjutreglage
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom event processing function. */

UINT my_event_process(GX_RADIAL_SLIDER *slider,
                    GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_slider_event_process(slider, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_radial_slider_event_process(slider, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_get"></a>gx_radial_slider_info_get


Hämta information om radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_info_get(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO **info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar information om radiell Slider.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **information** Informations pekar för länkad radiell Slider

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) information om radiellt skjutreglage
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RADIAL_SLIDER_INFO *info;

/* Retrive radial slider information structure. */
status = gx_radial_slider_info_get(&my_radial_slider,
                                    “my_radial_slider”, &info);

/* If status is GX_SUCCESS the radial slider information pointer of “my_radial_slider” has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_set"></a>gx_radial_slider_info_set


Ange information om radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_info_set(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger radiell information om skjutreglaget.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **information** Information om radiellt skjutreglage till set

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) information om det angivna radiella skjutreglaget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RADIAL_SLIDER_INFO info;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Reset radial slider info for “my_radial_slider”. */
status = gx_radial_slider_info_set(&my_radial_slider, &info);

/* If status is GX_SUCCESS the radial slider info of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_pixelmap_set"></a>gx_radial_slider_pixelmap_set


Ange pixelmaps för radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_pixelmap_set(
    GX_RADIAL_SLIDER *slider,
    GX_RESOURCE_ID background_pixemap,
    GX_REOUSRCE_ID needle_pixelmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten sätter radiellt skjutreglage i bakgrunden och pixelmaps.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontroll block för pekare till radiellt skjutreglage
- **background_pixelmap** Resurs-ID för bakgrunds Pixelmap
- **needle_pixelmap** Resurs-ID för barr Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Pixelmap för radiellt skjutreglaget har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create “my_radio_button”. */
status = gx_radial_slider_pixelmap_set(&my_radial_slider, GX_PIXELMAP_ID_BG, GX_PIXELMAP_ID_NEEDLE);

/* If status is GX_SUCCESS the background and needle pixelmap of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>Se även

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set

## <a name="gx_rich_text_view_create"></a>gx_rich_text_view_create

Skapa en RTF-vy

### <a name="prototype"></a>Prototyp

```C
UINT gx_rich_text_view_create(
    GX_RICH_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RICH_TEXT_FONTS *fonts,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en RTF-vy som anges.


**Formateringsmarkeringar används för att visa särskilda typer för text:**

- **\<b>\</b>** Ange teckensnitt för text med användare angivet fetstilt teckensnitts-ID
- **\<i>\</i>** Ange teckensnitt med användarens angivna kursiva teckensnitts-ID
- **\<u>\</u>** Aktivera understrykning av text
- **\<f GX_FONT_ID>\</f>** Ange text teckensnitt med angivet teckensnitts-ID
- **\<c GX_COLOR_ID>\</c>** Ange text teckensnitt med angivet färg-ID
- **\<hc GX_COLOR_ID>\</hc>** Ange färg-ID för text markerings färg
- **\<align left/right/center>\</align>** Ange text justering

**Exempel på användning av Taggar:**

- \<b>Detta är fet text< \b>
- \<i>Detta är en kursiv text< \i>
- \<u>Detta är text med understrykning< \u>
- \<f 0>Detta text teckensnitts-ID är inställt på 0< \f>
- \<c 1>Detta text färg-ID är inställt på 1< \c>
- \<hc 2>Det här text markerings färgs-ID: t är 2< \hc>
- \<align left> Den här texten är vänsterjusterad< \align>

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till RTF-visnings kontroll block
- **namn** Namn på Rich Text-vyn
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för text strängen
- **teckensnitt** Visar teckensnitts information för Rich Text-vyn. **Bilaga jag** innehåller en definition för GX_RICH_TEXT_FONTS-strukturen.
- **stil** Widgetens format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **ID** -Programdefinierat ID för Rich Text-vyn
- **storlek** Storlek på Rich Text-vyn

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) framgångs rik text visning skapas
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RICH_TEXT_VIEW rich_view;
GX_RCIH_TEXT_FONTS fonts;
GX_RECTANGLE size;

/* Defined widget size. */
gx_utility_rectangle_define(&size, 100, 100, 300, 150);

/* Define font information. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Create rich text view widget. */
status = gx_rich_text_view_create(&rich_view, “my_rich_view”,
                                  parent, GX_STRING_ID_TEST_STRING,
                                  &fonts,
                                  GX_STYLE_ENABLED,
                                  MY_RICH_VIEW_ID, &size);

/* If status is GX_SUCCESS the rich text view was successfully created. */

```

Demo programmet demo_guix_widget_types, som ingår i GUIX Studio-installationen, innehåller ett komplett exempel på hur du använder widgeten RTF-visning.

### <a name="see-also"></a>Se även

- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_draw"></a>gx_rich_text_view_draw


Rita RTF-vy

### <a name="prototype"></a>Prototyp

```C
VOID gx_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna RTF-widgeten. Den här tjänsten kallas vanligt vis internt av GUIX som en del av en uppdaterings åtgärd på arbets ytan, men den exponeras även för det program som kanske vill tillhandahålla en anpassad ritnings funktion och anropa standard bilden för RTF-visning som en anpassad ritnings bas.

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till RTF-widget för widget av textvyer

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Call default rich text view draw. */
    gx_rich_text_view_draw(text_view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_rich_text_view_create
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_fonts_set"></a>gx_rich_text_view_fonts_set

Ange teckensnitt för Rich text-vy

### <a name="prototype"></a>Prototyp

```C
UINT gx_rich_text_view_fonts_set(GX_RICH_TEXT_VIEW *text_view, GX_RICH_TEXT_FONTS *fonts);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger teckensnitt för en RTF-widget.

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till RTF-widget för widget av textvyer
- **teckensnitt** Visar information om teckensnitts information i RTF-format. **Bilaga jag** innehåller definitioner för att GX_RICH_TEXT_FONTS-strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) RTF-teckensnitt har angetts för text visning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RICH_TEXT_FONTS fonts;

/* Replace the font ids as needed. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Set the font of “my_rich_view”. */
status = gx_rich_text_view_fonts_set(&my_rich_view, &fonts);

/* If status is GX_SUCCESS the font for rich text view “my_rich_view” has been set. */
```

### <a name="see-also"></a>Se även

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_text_draw"></a>gx_rich_text_view_text_draw


Rita RTF-text

### <a name="prototype"></a>Prototyp

```C
VOID gx_rich_text_view_text_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Beskrivning

Den här stöd funktionen ritar text delen av en RTF-vy. Den här funktionen anropas internt av gx_rich_text_view_draw () och tillhandahålls som en separat API som bekvämlighet för program som definierar en anpassad ritnings funktion för RTF-visning. Program som vill anpassa bakgrunds ritningen för RTF-vyer kan ge sin anpassade ritnings funktion och anropa gx_rich_text_view_text_draw-tjänsten som en del av den anpassade ritningen för att rita RTF-texten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till RTF-widget för widget av textvyer

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Insert code here to draw rich text view background. */

    /* Call support function to do text drawing. */
    gx_rich_text_view_text_draw();

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *) rich_text_view);
}
```

### <a name="see-also"></a>Se även

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set

## <a name="gx_screen_stack_create"></a>gx_screen_stack_create


Initiera en skärms tack

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_create(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET **memory_buffer, 
    INT buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en skärms tack. Programmet måste definiera det minnes block och den buffertstorlek som används för att implementera skärms tack funktionen.

> [!NOTE]
> *Detta API är föråldrat och ersätts med gx_system_screen_stack_create (). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteks versioner..*

### <a name="parameters"></a>Parametrar

- **kontroll** Skärm bilds kontroll block
- **memory_buffer** Pekare till en minnesbuffert som används som en skärms tack
- **buffer_size** Minnes storlek i byte

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades skapa skärm stack
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_VALUE** (0X22) ogiltig buffertstorlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
#define SCREEN_STACK_SIZE 10

GX_SCREEN_STACK_CONTROL my_stack_control;
GX_WIDGET *screen_stack[SCREEN_STACK_SIZE];

/* Initialize “my_stack_control”. */
status = gx_screen_stack_create(&my_stack_control, screen_stack,
                        SCREEN_STACK_SIZE * sizeof(GX_WIDGET *));

/* If status is GX_SUCCESS the screen control block “my_stack control” has been initialized. */
```

### <a name="see-also"></a>Se även

- gx_screen_stack_push
- gx_screen_stack_pop
- gx_screen_stack_reset

## <a name="gx_screen_stack_pop"></a>gx_screen_stack_pop


Ta bort den översta posten från skärm bilden

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_pop(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den översta posten från skärm bilden och kopplar den till den tidigare överordnade skärmen. Detta API kopplar också bort alla befintliga underordnade från den överordnade.

> [!NOTE]
> *Detta API är föråldrat och ersätts med gx_system_screen_stack_pop (). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteks versioner..*

### <a name="parameters"></a>Parametrar

- **kontroll** Skärm bilds kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) popup för skärms tack
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Remove the topmost entry from the screen stack. */
status = gx_screen_stack_pop(&my_stack_control);

/* If status is GX_SUCCESS the topmost entry has been removed from the screen stack, 
    and the popped screen has been attached to its parent. */
```

### <a name="see-also"></a>Se även

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_push"></a>gx_screen_stack_push


Push-skärm och dess överordnade för stack

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_push(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET *screen,
    GX_WIDGET *new_screen);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar bort skärmen från den överordnade och skickar skärm pekaren och den överordnade pekaren till skärm bilden. Den nya skärm pekaren kopplas sedan till den överordnade.


> [!NOTE]
> *Detta API är föråldrat och ersätts med gx_system_screen_stack_pop (). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteks versioner..*

### <a name="parameters"></a>Parametrar

- **kontroll** Skärm bilds kontroll block
- **skärm** Skärm pekare för att skicka
- **new_screen** Pekare på den nya skärmen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad skärm Stacks-push
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Push “screen” and its parent to screen stack, Dettach “screen” from its parent, and attach “new screen” to the parent. */
status = gx_screen_stack_push(&my_stack_control,
                                screen, new_screen);

/* If status is GX_SUCCESS the widget “screen” and its parent have been pushed to screen stack, “screen” has been detached from its parent, “new_screen” has been attached to the parent. */
```

### <a name="see-also"></a>Se även

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_reset"></a>gx_screen_stack_reset


Tar bort alla poster från skärm bilden

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_reset(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla poster från skärm bilden.

> [!NOTE]
> *Detta API är föråldrat och ersätts med gx_system_screen_stack_pop (). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteks versioner..*

### <a name="parameters"></a>Parametrar

- **kontroll** Skärm bilds kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutför rullnings knapp skapa
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Remove all enteries from the screen stack. */
status = gx_screen_stack_reset(&my_stack_control);

/* If status is GX_SUCCESS all entries of screen stack has been removed. */
```

### <a name="see-also"></a>Se även

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_pop

## <a name="gx_scroll_thumb_create"></a>gx_scroll_thumb_create


Skapa rullnings knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_thumb_create(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_SCROLLBAR *parent, ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en rullnings-och miniatyr List. Den här tjänsten kallas vanligt vis internt när en GX_SCROLLBAR skapas, men görs offentlig för att tillåta anpassade SCROLLBAR-implementeringar.

### <a name="parameters"></a>Parametrar

- **scroll_thumb** Kontroll block för rullnings knapp i widget
- **överordnad** Pekare till överordnad rullnings List
- **stil** Typ av widget för rullnings List. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutför rullnings knapp skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SCROLL_THUMB my_scroll_thumb;

/* Create scroll thumb “my_scroll_thumb”. */
status = gx_scroll_thumb_create(&my_scroll_thumb, &my_scrollbar,
                                GX_STYLE_NONE);

/* If status is GX_SUCCESS the scroll thumb “my_scroll_thumb” has been created. */
```

### <a name="see-also"></a>Se även

- gx_scroll_thumb_draw
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_draw"></a>gx_scroll_thumb_draw


Rita rullnings knapp

### <a name="prototype"></a>Prototyp

```C
VOID gx_scroll_thumb_draw(GX_SCROLL_THUMB *scroll_thumb);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en rullnings-och miniatyr List. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan också anropas av åsidosatta ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **scroll_thumb** Kontroll block för rullnings knapp i widget

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom scroll thumb drawing function. */

VOID my_scroll_thumb_draw(GX_SCROLL_THUMB *thumb)
{
    /* Call default scroll thumb draw. */
    gx_scroll_thumb_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_scroll_thumb_create
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_event_process"></a>gx_scroll_thumb_event_process


Händelse för process rullnings knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_thumb_event_process(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hanterar händelser som skickas till en rullnings list för rullnings List. Den här tjänsten används vanligt vis internt av GUIX, men har gjorts offentlig för att hjälpa till med att implementera anpassade rullnings beteenden.

### <a name="parameters"></a>Parametrar

- **scroll_thumb** Kontroll block för rullnings knapp i widget
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för rullnings knapp
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_SCROLL_THUMB *thumb, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_scroll_thumb_event_process(thumb, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_scroll_thumb_event_process(thumb, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_scroll_thumb_create
- gx_scroll_thumb_draw

## <a name="gx_scroll_wheel_create"></a>gx_scroll_wheel_create


Skapa en widget för bas rullnings hjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_create( 
    GX_SCROLL_WHEEL *wheel, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows, 
    ULONG style,
    USHORT id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en allmän widget för rullnings hjul.

Ett generiskt rullnings hjul är den grundläggande widgeten för alla typer av rullnings hjul, inklusive *gx_text_scroll_wheel** * som är grunden för *gx_numeric_scroll_wheel** * och *gx_string_ scroll_wheel** * widgetar. Widgeten bas rullnings hjul innehåller händelse hantering, rullnings bar animering och vald rad beräkning för alla typer av rullnings hjul.

Program skapar vanligt vis inte en instans av en generisk widget för rullnings hjul, eftersom den här widgeten-typen inte ger någon ritnings funktion. Åtkomst till det här API: et är dock avsedd att hjälpa program som behöver skapa en anpassad widget för rullnings hjul.

GX_SCROLL_WHEEL baseras på GX_WINDOW och därför kan alla GX_WINDOW-API: er användas med GX_SCROLL_WHEEL och widgetar som härletts från GX_SCROLL_WHEEL.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **namn** Namn på programtilldelad widget
- **överordnad** Överordnad widget eller GX_NULL
- **total_rows** Totalt antal tillgängliga rader
- **stil** Format flaggor för widget
- **ID** för tilldelad widget
- **storlek** Rektangel som definierar den inledande widgetens storlek.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) rullnings hjul har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_SIZE** (0X19) ogiltig kontroll block storlek
- Widgeten **GX_ALREADY_CREATED** (0x13) har skapats
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Call generic create function during custom widget createl. */

UINT custom_scroll_wheel_create(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_CONST GX_CHAR *name,
                    GX_WIDGET *parent,
                    INT total_rows, ULONG style,
                    USHORT id,
                    GX_CONST GX_RECTANGLE *size)
{
    /* create base widget as part of custom create */
    status = gx_scroll_wheel_create(wheel, name, parent,
                            total_rows, style, id, size);

    /* If status is GX_SUCCESS the base scroll wheel has been created. */
}
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_event_process"></a>gx_scroll_wheel_event_process


Händelse bearbetnings funktion för widgeten allmän rullnings hjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_event_process(
    GX_SCROLL_WHEEL *wheel,
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tillhandahåller grundläggande hantering av ingångs händelser för alla widgetar av typen rullnings hjul.

Den här funktionen exponeras för program varan för att hjälpa till med program som behöver skapa en anpassad widget för rullnings hjul. Program skulle ofta tillhandahålla sin egen händelse bearbetnings funktion, men anropar den allmänna händelse bearbetningen för hjul-widgetar för händelser som de inte behöver anpassa.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **händelse** GX_EVENT pekare

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har rullat hjul händelse process
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Call generic scroll wheel event processing 
    as part of custom event processing function. */

UINT custom_scroll_wheel_event_process(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;

    default:
        /* pass all other events to the generic scroll wheel
            event processing */
        gx_scroll_wheel_event_process(wheel, event);
        break;
    }
}
```


### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_gradient_alpha_set"></a>gx_scroll_wheel_gradient_alpha_set


Tilldela tonings-alpha-värden för valfri överläggs toning

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_gradient_alpha_set(
    GX_SCROLL_WHEEL *wheel,
    GX_UBYTE start_alpha,
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar de första och sista alfa värdena för ett valfritt övertonings överlägg av widgeten rullnings hjul.

Alla widgetar för rullnings hjul stöder en "tona"-påverkan av rullnings hjulets rader som rader närmast den övre och nedre kanten av widgeten rullnings hjul. Den här toningen utförs genom att rita en övertonings Pixelmap över rullnings hjulets rader, vilket gör att raderna visas för att tona ut när raderna ritas längst upp och längst ned i widgeten rullnings hjul.

Med den här API-tjänsten kan programmet ändra tonings effekterna eller inaktivera den här inställningen helt genom att ange värdena för start och slut till 0.

Gradient-Pixelmap skapas vid körning när rullnings hjulet ursprungligen blir synligt. Detta kräver att en Memory Allocation service Runtime har definierats med hjälp av _gx_system_memory_allocator_set (). Om ingen funktion för allokering av minne har definierats skapas inte tonings avbildningen och ingen tonings påverkan blir tillgänglig.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **start_alpha** Överläggets toning startar alpha-värdet.
- **end_alpha** Överläggets slut för and lutande alfa värde.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har ställt in musens tonings alfa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_scroll_wheel_gradient_alpha_set(&wheel, 240, 0);
/* if status == GX_SUCCESS the wheel gradient alpha values were
Successfully assigned. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_row_height_set"></a>gx_scroll_wheel_row_height_set


Tilldela rad höjden för varje hjul rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_row_height_set(
    GX_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar rad höjden för varje rad i rullnings hjulet. Observera att om rullnings hjulet har format GX_STYLE_TEXT_SCROLL_WHEEL_ROUND passerar rad höjden genom en transformering som i praktiken minskar rad höjden som raden närmast den övre eller nedre kanten på hjulet.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **row_height** Värdet radhöjd i bild punkter.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett rullnings hjulets höjd
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_background_set"></a>gx_scroll_wheel_selected_background_set


Tilldela en bakgrunds bild för vald Wheel-rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_selected_background_set(
    GX_SCROLL_WHEEL*wheel, 
    GX_RESOURCE_ID image_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar ett valfritt Pixelmap-ID som ritas bakom den valda raden av rullnings hjulet. Detta kan användas för att markera den markerade raden så att användaren enkelt kan särskilja den rad i rullnings hjulet som är markerad.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **image_id** Pixelmap-ID som ska användas som den valda rad bakgrunds bilden.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett rullnings hjulets bakgrund
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_scroll_wheel_selected_background_set(&wheel,
GX_PIXELMAP_ID_SELECTED_ROW);

/* if status == GX_SUCCESS the background image has been
assigned. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_get"></a>gx_scroll_wheel_selected_get


Hämta den markerade hjul raden

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_selected_get(
    GX_SCROLL_WHEEL *wheel,
    INT *row);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kommer att fråga rullnings hjulet för att hämta den markerade raden. Anroparen måste skicka platsen för att returnera det valda rad indexet som den andra parametern till den här funktionen.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **rad** Den plats där det valda rad värdet kommer att returneras.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat den valda hjul raden
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x19)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
INT row;
status = gx_scroll_wheel_selected_get(&wheel, &row);

/* if status == GX_SUCCESS the selected row has been returned in
the row variable. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_set"></a>gx_scroll_wheel_selected_set


Tilldela den markerade rullnings hjuls raden

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_selected_set(
    GX_SCROLL_WHEEL *wheel,
    INT row);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den markerade rullnings hjul raden.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **rad** Raden för rullnings hjulet som ska markeras.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har ställt in den valda hjul raden
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_scroll_wheel_selected_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been set to select
row 20 */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_speed_set"></a>gx_scroll_wheel_speed_set


Tilldela rullnings hastighet

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_speed_set(
    GX_SCROLL_WHEEL *wheel,
    GX_FIXED_VAL start_speed_rate,
    GX_FIXED_VAL end_speed_rate,
    GX_VALUE max_steps,
    GX_VALUE delay);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar rullnings hastigheten för widgeten rullnings hjul.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **start_speed_rate** Frekvensen för rullnings start hastigheten till Snärtningen.
- **end_speed_rate** Frekvensen för rullnings slut hastigheten till Snärtningen
- **max_steps** Max steg för rullning.
- **fördröjning** Fördröjnings tid för varje steg.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett hjul hastighet
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) ogiltigt värde

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_scroll_wheel_speed_set(&wheel, GX_FIXED_VAL_MAKE(2),
                                GX_FIXED_VAL_MAKE(1) / 2, 10, 2);

/* if status == GX_SUCCESS the scroll wheel speed has been
successfully set. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_total_rows_set"></a>gx_scroll_wheel_total_rows_set


Tilldela det totala antalet rullnings hjuls rader tillgängliga

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_total_rows_set(
    GX_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar antalet rader som är tillgängliga i det angivna rullnings hjulet. Widgeten rullnings hjul tar vanligt vis emot rad innehållet från programmet i form av en sträng mat ris eller en sträng data som anges av användaren. Detta API informerar rullnings hjulet för det totala antalet rader som ska visas för användaren.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till generiskt kontroll block för rullnings hjul
- **total_rows** Totalt antal hjul rader att presentera för användaren.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har ställt in total rad för rullnings hjul
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) ogiltigt värde

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_scroll_wheel_total_rows_set(&wheel, 100);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 100 total rows */
```
### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scrollbar_draw"></a>gx_scrollbar_draw


Rita rullnings List

### <a name="prototype"></a>Prototyp

```C
VOID gx_scrollbar_draw(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en rullnings List. En gemensam ritnings funktion används för widgetar både lodräta och vågräta rullnings lister. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan också anropas av åsidosatta ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **rullnings List** Widgeten rullnings list för att rita

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom scrollbar drawing function. */

VOID my_scrollbar_draw(GX_SCROLLBAR *scrollbar)
{
    /* Call default scrollbar draw. */
    gx_scrollbar_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_ horizontal_scrollbar_create
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_event_process"></a>gx_scrollbar_event_process


Process rullnings händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_event_process(
    GX_SCROLLBAR *scrollbar,
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en rullnings händelse. En vanlig händelse hanterings funktion som används för widgetar både lodräta och vågräta rullnings lister.

### <a name="parameters"></a>Parametrar

- **rullnings List** Kontroll block för rullnings List
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för lyckad rullnings List
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
Call generic scrollbar event processing as part of custom event processing function. */

UINT custom_scrollbar_event_process(GX_SCROLLBAR *scrollbar,
                                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic scrollbar
            event processing */
        gx_scrollbar_event_process(scrollbar, event);
        break;
    }
}
```

### <a name="see-also"></a>Se även

- gx_ horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_limit_check"></a>gx_scrollbar_limit_check


Kontrol lera rullnings List gräns

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_limit_check(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kontrollerar gränsen för rullnings listen och förhindrar att rullnings listen för rullnings listen går förbi de fördefinierade gränserna.

### <a name="parameters"></a>Parametrar

- **rullnings List** Kontroll block för rullnings List

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kontroll av lyckad rullnings List
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Check scrollbar limit of “my_scrollbar”. */
status = gx_scrollbar_limit_check(&my_scrollbar);

/* If status is GX_SUCCESS the limit of scrollbar “my_scrollbar” has been checked. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_reset"></a>gx_scrollbar_reset


Återställ rullnings List

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_reset(
    GX_SCROLLBAR *scrollbar,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återställer rullnings listen.

### <a name="parameters"></a>Parametrar

- **rullnings List** Kontroll block för rullnings List
- **information** Pekare till GX_SCROLL_INFO-strukturen som definierar rullnings gränsen, det aktuella värdet och steget eller ökningen. **Bilaga i** innehåller en definition för GX_SCROLL_INFO-strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) återställning av lyckad rullnings List
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- Rullnings informationen för **GX_INVALID_VALUE** (0x22) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Reset scrollbar “my_scrollbar”. */

GX_SCROLL_INFO my_info;

my_info.gx_scroll_value = 0;
my_info.gx_scroll_minimum = 0;
my_info.gx_scroll_maximum = 100;
my_info.gx_scroll_visible = 10;
my_info.gx_scroll_increment = 1;

status = gx_scrollbar_reset(&my_scrollbar, &my_info);

/* If status is GX_SUCCESS the scrollbar “my_scrollbar” has been reset. */
```

### <a name="see-also"></a>Se även

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_value_set"></a>gx_scrollbar_value_set


Tilldela ScrollBar-värde

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_value_set(
    GX_SCROLLBAR *scrollbar,
    INT value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den aktuella ScrollBar-värdet. En GX_EVENT_VERTICAL_SCROLL-eller GX_EVENT_HORIZONTAL_SCROLL-händelse kommer att genereras till det överordnade fönstret.

### <a name="parameters"></a>Parametrar

- **rullnings List** Kontroll block för rullnings List
- **värde** Nytt rullnings värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för lyckad rullnings List
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- Rullning svärdet för **GX_INVALID_VALUE** (0x22) är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assign new value for scrollbar “my_scrollbar”. */

status = gx_scrollbar_value_set(&my_scrollbar, 0);

/* If status is GX_SUCCESS the current position of scrollbar “my_scrollbar” has been set. */

```

### <a name="see-also"></a>Se även

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_single_line_text_input_backspace"></a>gx_single_line_text_input_backspace


Bearbeta ett backsteg-tecken i widgeten text inflöde

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_backspace(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort tecknen innan markörens position för text. Den här tjänsten kallas internt när en nyckel för Backsteg-händelsen tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad text inmatare skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x23)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_single_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_clear"></a>gx_single_line_text_input_buffer_clear


Tar bort alla tecken från bufferten för inmatade filer

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_buffer_clear(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla tecken från bufferten för inmatade filer.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har rensat en text-buffert med enkel rad
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* clear input buffer of “my_text_input”. */
status = gx_single_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_buffer_backspace
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_get"></a>gx_single_line_text_input_buffer_get


Hämtar information om buffer för text indata-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_buffer_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CHAR **buffer_address, 
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar buffertstorleken för widgeten text indata.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **buffer_address** Adressen för indatabufferten
- **content_size** Antalet byte för indata
- **buffer_size** Storleken på indatabufferten

### <a name="return-values"></a>Retur värden

- Information om buffer **GX_SUCCESS** (0X00) har hämtats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *buffer_address;
UINT buffer_size;
UINT content_size;

/* Retrieve buffer information of “my_text_input” widget. */
status = gx_single_line_text_input_buffer_get(&my_text_input,
                    &buffer_address, &string_size, &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_delete"></a>gx_single_line_text_input_character_delete


Ta bort specialtecknet vid den aktuella markörens position

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_character_delete(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort specialtecknet efter markörens position för text ingång. Den här tjänsten anropas internt när händelsen ta bort nyckel tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) tog bort ett blank steg efter markören
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_single_line_text_input_character_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_multi_line_text_input_create
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_insert"></a>gx_single_line_text_input_character_insert


Infoga en tecken sträng vid aktuell markör position

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_character_insert(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten infogar en tecken sträng i bufferten för text ingångs sträng vid den aktuella pekar positionen.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **insert_str** Tecken sträng som ska infogas
- **insert_size** Antal byte som ska infogas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har infogat tecknen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Insert characters at current cursor position. */

GX_CHAR insert_text[10] = “insert”;
status = gx_single_line_text_input_character_insert(&my_text_input,
                                            insert_text,
                                            GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the text input widget has successfully insert the string. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_create"></a>gx_single_line_text_input_create


Skapa en widget för text inflöde

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_create(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    UINT style, USHORT text_input_id, GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för text inflöde. Anroparen måste tillhandahålla lagring för Indatasträngen och ange den maximala längden för strängen.

GX_SINGLE_LINE_TEXT_INPUT härleds från GX_PROMPT och därför kan alla gx_prompt tjänster användas med GX_SINGLE_LINE_TEXT_INPUT widgetar.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **namn** Logiskt namn för valfri widget
- **överordnad** Valfri överordnad widget
- **input_buffer** Lagring för Indatasträngen
- **buffer_size** Storlek på lagrings plats för inkommande sträng, i byte.
- **stil** Stil flaggor för text inspelning
- **text_input_id** Valfritt ID för widgeten indatamängd
- **storlek** Rektangel som definierar ursprunglig widgets storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad text inmatare skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SINGLE_LINE_TEXT_INPUT my_text_input;
static GX_CHAR           text_input_buffer[100];
GX_RECTANGLE             size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 110, 40);

/* Create single-line text input widget “my_text_input”. */
status = gx_single_line_text_input_create(&my_text_input,
                        “text_input”, GX_NULL, text_input_buffer, 100,
                        GX_STYLE_ENABLED, 0, &size);

/* If status is GX_SUCCESS, the text input widget has been created. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw"></a>gx_single_line_text_input_draw


Rita en widget för text inmatningar

### <a name="prototype"></a>Prototyp

```C
VOID gx_single_line_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar en widget för text inmatare. Den här tjänsten kallas vanligt vis internt under uppdatering av arbets ytan, men kan också anropas från funktioner för anpassad text indragnings funktion.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
    /* Call default single line text input draw. */
    gx_single_line_text_input_draw(input);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw_position_get"></a>gx_single_line_text_input_draw_position_get


Hämta start position för text ritning

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_draw_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_VALUE *xpos, GX_VALUE *ypos);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar start positionen för text inmatnings text.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **Xpos** Start position för hämtat rit objekt i x-koordinat
- **ypos** Start position för hämtat rit objekt i y-koordinat

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) flyttar text ingångs markören till slutet
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
GX_VALUE xpos;
GX_VALUE ypos;

    /* Draw background. */
    gx_widget_border_draw(input, border_color, upper_fill_color,
                          lower_fill_color, GX_TRUE);

    /* Retrieve text draw start position. */
    gx_single_line_text_input_draw_position_get(input, xpos,
                                                ypos);

    /* Add your text drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_end"></a>gx_single_line_text_input_end


Flytta text inmatade markören till sträng slutet

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_end(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar widgeten för text inmatade markör i slutet av Indatasträngen. Den här tjänsten anropas internt när en end Key Down-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) flyttar text ingångs markören till slutet
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move input cursor to end. */
status = gx_single_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to end. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_event_process"></a>gx_single_line_text_input_event_process


Händelse bearbetnings funktion för widget för text indata

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_event_process(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en enskild text ingångs händelse. Den här funktionen refereras internt av funktionen gx_single_line_text_input_create, men exponeras för användning av programmet i de fall där programmet definierar en anpassad händelse bearbetnings funktion för text i en enskild rad.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **event_ptr** Pekare till GX_EVENT-struktur

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text inmatad händelse har bearbetats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Call generic single line text input event processing as part of custom event processing function. */

UINT custom_sl_text_input_event_process(
                                GX_SINGLE_LINE_TEXT_INPUT *input,
                                GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default single line
            text input event processing */
        status =
        gx_single_line_text_input_event_process(input, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_fill_color_set"></a>gx_single_line_text_input_fill_color_set


Ange bakgrunds färg för text i en linje

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_fill_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger fyllnings färgen för text ingången i en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till text ingångs kontroll block
- **normal_fill_color_id** Resurs-ID för widgetens fyllnings färg i normalt läge. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **selected_fill_color_id** Resurs-ID för widgetens fyllnings färg när widgeten får fokus. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **disabled_fill_color_id** Resurs-ID för widgetens fyllnings färg när formatet GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **readonly_fill_color_id** Resurs-ID för widgetens fyllnings färg när båda formaten GX_STYLE_ENABLED och GX_STYLE_TEXT_INPUT_READYONLY har angetts. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text med fyllnings färg uppsättning för enkel linje text
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set fill colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_fill_color_set(&my_text_input,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL,
                    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” was
set. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_home"></a>gx_single_line_text_input_home


Flytta text inmatade markören till Start positionen

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_home(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar markörens position för text insättning till början av Indatasträngen. Den här tjänsten anropas internt när en händelse för start nyckel tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till Start positionen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move cursor to the start of the input text. */
status = gx_single_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the home position */
```

### <a name="see-also"></a>Se även
- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_left_arrow"></a>gx_single_line_text_input_left_arrow


Flytta insättnings punkten ett steg till vänster

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_left_arrow(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar text ingångs markören ett tecken till vänster. Den här tjänsten anropas internt när en vänster Key Down-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till vänster
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move the cursor one character to the left. */
status = gx_single_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the left. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_position_get"></a>gx_single_line_text_input_position_get

Flytta markören till pixel position

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    INT pixel_position);
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar text ingångs markören baserat på den begärda pixel positionen. Markörens index för text indatamängd beräknas baserat på x-värdet för pixel positionen. Den här tjänsten kallas internt när en Penn händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **pixel_position** X-värde för pixel position

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett markören till begärd position
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set cursor to requested position. */
status = gx_single_line_text_input_position_get(&my_text_input,
                                                100);

/* If status is GX_SUCCESS the text input widget cursor has been positioned */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_right_arrow"></a>gx_single_line_text_input_right_arrow


Flytta insättnings punkten ett steg till höger

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_right_arrow(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar text ingångs markören ett tecken till höger. Den här tjänsten anropas internt när en höger nyckel händelsen tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har flyttat markören till höger
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move cursor one character to the right. */
status = gx_single_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_add"></a>gx_single_line_text_input_style_add


Lägg till format

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_style_add(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till den eller de angivna stilarna i widgeten för text indatamängden.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **stil** Nytt format som ska läggas till. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har lagt till format i widgeten
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Add a new style to “my_text_input”. */
status = gx_single_line_text_input_style_add(&my_text_input,
GX_STYLE_CURSOR_AWAYS);

/* If status is GX_SUCCESS the GX_STYLE_CUSROSR_SHOR have been successfully added. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gax_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_remove"></a>gx_single_line_text_input_style_remove

Ta bort format

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_style_remove(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort de angivna stilarna från widgeten text inmatad text.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **stil** Formatmallar som ska tas bort. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har tagit bort formatmallar från widgeten
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Remove cursor blink style from “my_text_input”. */
status = gx_single_line_text_input_style_remove(&my_text_input,
GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the GX_STYLE_CURSOR_BLINK style has been successfully removed. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_set"></a>gx_single_line_text_input_style_set


Ange text ingångs format

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_style_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger de angivna stilarna till widgeten text inmatad text.

### <a name="parameters"></a>Parametrar

- **text_input** Kontroll block för widget för text insignal
- **stil** flaggor som ska tilldelas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett text ingångs formatet
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set style for “my_text_input”. */
status = gx_single_line_text_input_style_set(&my_text_input,
                    GX_STYLE_ENABLED | GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the text input style has been successfully set to the specified styles. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_signle_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_color_set"></a>gx_single_line_text_input_text_color_set


Ange textfärg för texttext

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger text färgen för text ingången i en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till text ingångs kontroll block
- **normal_text_color_id** Resurs-ID för text färgen i normalt läge. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **selected_text_color_id** Resurs-ID för text färgen när widgeten får fokus. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **disabled_text_color_id** Resurs-ID för text färgen när formatet GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **readonly_text_color_id** Resurs-ID för text färgen när båda formaten GX_STYLE_ENABLED och GX_STYLE_TEXT_INPUT_READONLY har angetts. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text med text färg uppsättning med texttext
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set text colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_color_set(&my_text_input,
                                        GX_COLOR_ID_NORMAL_TEXT,
                                        GX_COLOR_ID_SELECTED_TEXT,
                                        GX_COLOR_ID_DISABLED_TEXT,
                                        GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the text color “my_text_input” was set. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_select"></a>gx_single_line_text_input_text_select

Markera text

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten väljer text med det angivna start-och slut markerings indexet och markerar den markerade texten med de valda fyllnings-och text färgerna.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till text ingångs kontroll block
- **start_index** Index för det första markerade specialtecknet
- **end_index** Index för det senast markerade specialtecknet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text markerings text för text markering
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) index värde är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Select text between index [0, 9]. */
status = gx_single_line_text_input_text_select(&my_text_input,
                                                0,9);

/* If status is GX_SUCCESS, the text between index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_set"></a>gx_single_line_text_input_text_set


Ange text inmatad text text (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten har ersatts av gx_single_line_text_input_text_set_ext ()

Den här tjänsten anger texten för text ingången i den enskilda raden.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till text ingångs kontroll block
- **text** NULL-terminerad text sträng

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text med text färg uppsättning med texttext
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CONST GX_CHAR new_text = “Set Single Line Text Input Text”;

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set(&my_text_input,
                                        new_text);

/* If status is GX_SUCCESS, the text of “my_text_input” was set. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_text_set_ext

## <a name="gx_single_line_text_input_text_set_ext"></a>gx_single_line_text_input_text_set_ext


Ange text för text i enradig text

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger texten för text ingången i den enskilda raden.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till text ingångs kontroll block
- **sträng** GX_STRING variabel

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) text med text färg uppsättning med texttext
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING new_string;
new_string.gx_string_ptr = “Set Single Line Text Input Text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set_ext(&my_text_input,
                                        &new_string);

/* If status is GX_SUCCESS, the string has been assigned to my_text_input. */
```

### <a name="see-also"></a>Se även

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set_ext


## <a name="gx_slider_create"></a>gx_slider_create

Skapa skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_create(
    GX_SLIDER *slider, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, INT tick_count,
    GX_SLIDER_INFO *slider_info,
    ULONG style, USHORT slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för skjutreglage.

GX_SLIDER härleds från GX_WIDGET, och därför kan alla gx_widget API-tjänster användas med GX_SLIDER typ widgetar.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **namn**: namnet på skjutreglaget
- **överordnad**: pekare till överordnad widget
- **tick_count**: antal Tick för skjutreglage
- **slider_info**: pekar på Slider-information som är en struktur som används för att skicka skjutreglagets värde gränser, nålventil och placering och andra skjutreglagets parametrar. **Bilaga i** innehåller en definition för GX_SLIDER_INFO-strukturen.
- **format**: skjutreglagets typ. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **slider_id**: Programdefinierat ID för skjutreglaget
- **storlek**: dimensioner för skjutreglaget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) klart skjutreglaget har skapats
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_ALREADY_CREATED**: (0X13) widgeten har redan skapats
- **GX_INVALID_SIZE**: (0X19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_WIDGET**: 0x12 överordnade widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create slider “my_slider”. */

GX_SLIDER my_slider;
GX_SLIDER_INFO info;

info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_increment = 1;
info.gx_slider_info_min_travel = 20;
info.gx_slider_info_max_travel = 20;
info.gx_slider_info_needle_width = 10;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset = 5;

status = gx_slider_create(&my_slider, “my_slider”,
    &my_parent, 10, info, GX_STYLE_ENABLED, ID_MY_SLIDER, &size);

/* If status is GX_SUCCESS the slider “my_slider” has been created. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_draw"></a>gx_slider_draw

Skjutreglage för rit objekt

### <a name="prototype"></a>Prototyp

```C
VOID gx_slider_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar ett skjutreglage. Den här tjänsten används internt av funktionen gx_slider_create, men exponeras också för användning av programmet i dessa instanser när en anpassad ritnings funktion för skjutreglage har definierats.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Call default slider draw. */
    gx_slider_draw(slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_event_process"></a>gx_slider_event_process

Händelse för process Slider

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_event_process(
    GX_SLIDER *slider, 
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en Slider-händelse. Den här funktionen refereras internt av funktionen gx_slider_create, men exponeras för användning av programmet i de fall där programmet definierar en anpassad bearbetnings funktion för Slider-händelsen.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **händelse**: pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) slutfört skjutreglage händelse process
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic slider event processing as part of custom event processing function. */

UINT custom_slider_event_process(GX_SLIDER *slider,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;
    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default slider event processing */
            status = gx_slider_event_process(slider, event);
            break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_info_set"></a>gx_slider_info_set

Ange block för Slider-information

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_info_set(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar angiven Slider-information, till exempel skjutreglaget minimum, skjutreglaget maximalt och aktuellt värde för skjutreglaget till det angivna skjutreglaget. Skjutreglaget uppdaterar nål och ritar om baserat på den nya Slider-informationen.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **info**: pekar på informations strukturen för skjutreglaget. **Bilaga i** innehåller en definition för GX_SLIDER_INFO-strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett information om skjutreglaget
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SLIDER_INFO my_slider_info;
my_slider_info.gx_slider_info_min_val = 0;
my_slider_info.gx_slider_info_max_val = 100;
my_slider_info.gx_slider_info_current_val = 50;
my_slider_info.gx_slider_info_increment = 1;
my_slider_info.gx_slider_info_min_travel = 20;
my_slider_info.gx_slider_info_max_travel = 20;
my_slider_info.gx_slider_info_needle_width = 10;
my_slider_info.gx_slider_info_needle_height = 10;
my_slider_info.gx_slider_info_needle_inset = 5;

my_slider_info.gx_slider_info_needle_hotspot_offset = 5;

/* Set slider information for slider “my_slider”. */
status = gx_slider_info_set (&my_slider, &my_slider_info);

/* If status is GX_SUCCESS the “my_slider” is configured with my_slider_info. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_draw"></a>gx_slider_needle_draw

Nål för Rita-skjutreglage

### <a name="prototype"></a>Prototyp

```C
VOID gx_slider_needle_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar ett Barr för skjutreglaget. Den här tjänsten anropas automatiskt av funktionen gx_slider_draw, men kan också anropas av programmet som en del av en anpassad ritnings funktion för skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_position_get"></a>gx_slider_needle_position_get

Hämta Slider-position

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_needle_position_get(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *slider_info,
    GX_RECTANGLE *return_position);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar skjutreglagets nålventil baserat på det aktuella Slider-värdet.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **slider_info**: pekar på informations strukturen för Slider som definierar skjutreglagets gränser, nålans storlek och förskjutning och andra Slider-parametrar. **Bilaga i** innehåller en definition för GX_SLIDER_INFO-strukturen.
- **return_position**: pekare till målet för barr position

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckat skjutreglaget positions position
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_VALUE**: (0X22) skjutreglaget är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RECTANGLE needle_position;

/* Get the needle position for slider “my_slider”. */
status = gx_slider_needle_posistion_get(&my_slider, &slider_info,
    &needle_position);

/* If status is GX_SUCCESS the needle position for slider “my_slider” has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_tickmarks_draw"></a>gx_slider_tickmarks_draw

Kal streck för skjutreglage

### <a name="prototype"></a>Prototyp

```C
VOID gx_slider_tickmarks_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar skjutreglaget kal streck. Den här funktionen anropas internt av funktionen gx_slider_draw, men exponeras för användning av program som kan implementera en anpassad ritnings funktion för skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_travel_get"></a>gx_slider_travel_get

Hämta skjutreglaget

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_travel_get(
    GX_SLIDER *widget,
    GX_SLIDER_INFO *info,
    INT *return_min_travel, 
    INT *return_max_travel);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar skjutreglaget.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **info**: pekar på informations struktur för Slider. **Bilaga i** innehåller en definition för GX_SLIDER_INFO-strukturen.
- **return_min_travel**: pekare till målet för minsta res värde</td>
- **return_max_travell**: pekare till mål för maximalt res värde</td>

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) slutfört skjutreglaget Hämta
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_VALUE**: (0X22) skjutreglaget är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get travel information for for slider “my_slider”. */
status = gx_slider_travel_get(&my_slider, &info,
    &my_min_travel, &my_max_travel);

/* If status is GX_SUCCESS the travel max/min values for slider “my_slider” have been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_value_calculate"></a>gx_slider_value_calculate

Beräkna Slider-värde

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_value_calculate(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info,
    INT new_position);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar skjutreglagets värde baserat på den nål positionen för skjutreglaget. Den här funktionen anropas internt av GUIX när användaren flyttar skjutreglaget, men kan också anropas av programmet vid implementering av en widget för anpassade skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **info**: pekar mot Slider-information. **Bilaga i** innehåller en definition för GX_LISDER_INFO-strukturen.
- **new_position**: ny Slider-placering

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) slutfört skjutreglaget värde beräkna
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_VALUE**: (0X22) skjutreglaget är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Calculate new value for slider “my_slider”. */
status = gx_slider_value_calculate(&my_slider,
    &my_slider.gx_slider_info, new_slider_position);

/* If status is GX_SUCCESS the slider value of “my_slider” has been calculated. */

```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_set

## <a name="gx_slider_value_set"></a>gx_slider_value_set

Ange skjutreglagets värde

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_value_set(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *info, 
    INT new_value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger skjutreglagets värde. Detta API kan anropas av programmet för att flytta ett skjutreglage under program kontroll, vilket kringgår behovet av användarindata för att dra reglaget till Barr.

### <a name="parameters"></a>Parametrar

- **skjutreglage**: kontroll block för skjutreglage
- **info**: pekar på informations struktur för Slider. **Bilaga i** innehåller definition som GX_SLIDER_INFO struktur
- **new_value**: nytt Slider-värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckades skjutreglagets värde uppsättning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set new value for slider “my_slider”. */
status = gx_slider_value_set(&my_slider,
    &my_slider.gx_slider_info, new_value);

/* If status is GX_SUCCESS the new value has been set for slider “my_slider”. */
```

### <a name="see-also"></a>Se även

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate

##  <a name="gx_sprite_create"></a>gx_sprite_create

Skapa en sprite-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_create(
    GX_SPRITE *sprite, GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count,
    ULONG style, USHORT sprite_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en GX_SPRITE-widget. En sprite används för att visa en sekvens med pixelmaps som i en animering, eller så kan den användas som en Pixelmap för flera tillstånds skärmar.

GX_SPRITE härleds från GX_WIDGET och stöder alla gx_widget API-tjänster.

Widgeten GX_SPRITE kräver en matris med GX_SPRITE_FRAME strukturer för att definiera Sprite-animeringen. **Bilaga i** innehåller en definition för GX_PRITE_FRAME-strukturen.

### <a name="parameters"></a>Parametrar

- **Sprite**: kontroll block för Sprite-widget
- **namn**: valfritt Sprite-namn
- **överordnad**: pekare till överordnad widget
- **frame_list**: en matris med GX_SPRITE_FRAME strukturer
- **frame_count**: anger antalet poster i list rutans matris
- **format**: typ av Sprite. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **sprite_id**: Programdefinierat ID för Sprite
- **storlek**: mått för Sprite

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad Sprite-skapande
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_ALREADY_CREATED**: (0X13) widgeten har redan skapats
- **GX_INVALID_WIDGET**: 0x12 överordnade widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create sprite “my_sprite”. */

status = gx_sprite_create(&my_sprite, “my_sprite”,
    &my_parent,
    sprite_frame_list, frame_count,
    GX_STYLE_SPRITE_AUTO|GX_STYLE_SPRITE_LOOP,
    ID_MY_SPRITE, &size);

/* If status is GX_SUCCESS the sprite “my_sprite” has been created. */
```

### <a name="see-also"></a>Se även

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_current_frame_set
- gx_sprite_frame_list_set

## <a name="gx_sprite_current_frame_set"></a>gx_sprite_current_frame_set

Tilldela Sprite-ram

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_current_frame_set(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den aktuella Sprite-ramen. Om en GX_SPRITE-widget inte körs automatiskt, kan den användas som en kontrollerad tillstånds lampa för att visa den kommando rads Pixelmap.

### <a name="parameters"></a>Parametrar

- **Sprite**: kontroll block för Sprite-widget
- **ram**: Sprite-ram som ska visas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckades
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Assign frame number 3 as the current sprite frame */
status = gx_sprite_current_frame_set(&my_sprite, 3);

/* If status is GX_SUCCESS the sprite “my_sprite” will display frame index 3. */
```

### <a name="see-also"></a>Se även

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_frame_list_set"></a>gx_sprite_frame_list_set

Tilldela eller ändra en sprite-bildruta-lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_frame_list_set(
    GX_SPRITE *sprite,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kan användas för att tilldela eller tilldela om List rutan som används av en sprite-widget efter att widgeten Sprite har skapats. Information om innehållet i en sprite-Rams lista finns i gx_sprite_create API-dokumentationen.

### <a name="parameters"></a>Parametrar

- **Sprite**: kontroll block för Sprite-widget
- **frame_list**: matris med GX_SPRITE_FRAME strukturer eller GX_NULL om det inte visas någon ram.
- **frame_count**: antal ramar i list rutans matris

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) bild Rute uppsättning för bild listan har slutförts
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Assign framelist_1, which has 10 frames, to my_sprite */
status = gx_sprite_frame_list_set(&my_sprite, framelist_1, 10);

/* If status is GX_SUCCESS the new frame list is now associated with this sprite */
```

### <a name="see-also"></a>Se även

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_create

## <a name="gx_sprite_start"></a>gx_sprite_start

Starta en sprite-körnings ordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_start(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en sprite-sekvens för automatisk körning. Widgeten Sprite kommer att gå igenom Sprite-bild rutorna tills den sista ramen har nåtts, eller köras kontinuerligt om GX_SPRITE_LOOP formatet har angetts.

### <a name="parameters"></a>Parametrar

- **Sprite**: kontroll block för Sprite-widget
- **ram**: inledande Sprite-ram som ska visas, vanligt vis bild ruta 0

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) startade Sprite-körning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start the sprite “my_sprite” */
status = gx_sprite_start(&my_sprite, 0);

/* If status is GX_SUCCESS the sprite “my_sprite” will start running */
```

### <a name="see-also"></a>Se även

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_stop"></a>gx_sprite_stop

Stoppa en sprite-körnings ordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_stop(GX_SPRITE *sprite);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar en sprite-sekvens för automatisk körning.

### <a name="parameters"></a>Parametrar

- **Sprite**: kontroll block för Sprite-widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) körning av Sprite har stoppats
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the sprite sequence */
status = gx_sprite_stop(&my_sprite);

/* If status is GX_SUCCESS the sprite “my_sprite” is stopped. */
```

### <a name="see-also"></a>Se även

- gx_sprite_current_frame_set
- gx_sprite_start
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_string_scroll_wheel_create"></a>gx_string_scroll_wheel_create

Skapa en rullnings hjul för sträng typ

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_create(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    GX_CONST GX_CHAR **string_list, 
    ULONG style,
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en rullnings hjul för sträng typ.

GX_STRING_SCROLL_WHEEL härleds från GX_TEXT_SCROLL_WHEEL, och därför kan alla gx_text_scroll_wheel API-funktioner användas med GX_STRING_SCROLL_WHEEL widgetar.

Programmet kan skicka i en enkel sträng mat ris till funktionen Create som definierar de strängar som ska visas av rullnings hjulet, eller så kan programmet skicka GX_NULL som string_list parameter och anropa `gx_string_scroll_wheel_string_id_list_set()` API: et för att tillhandahålla en matris med sträng-ID. Om den sistnämnda metoden används, växlar sträng rullnings hjul automatiskt de visade strängarna om det aktiva programmets språk ändras.

Alternativt, om strängarna som ska visas inte är statiskt definierade eller inte vet när rullnings hjulet skapas, kan programmet skicka GX_NULL som parameter för sträng listan och anropa API-funktionen gx_text_scroll_wheel_callback_set () för att definiera en callback-funktion som innehåller de strängar som ska visas i real tid som krävs.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för sträng rullnings hjul
- **namn**: Programdefinierat widgets namn
- **överordnad**: överordnad hjul eller GX_NULL
- **total_rows**: totalt antal rader som ska visas för användaren
- **string_list**: statiskt definierad sträng mat ris eller GX_NULL
- **format**: önskade stil flaggor
- **ID**: programdefinierade hjul stils flaggor
- **storlek**: inledande rullnings hjul storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) skapade sträng rullnings hjul
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR (0x07)**: ogiltig pekare
- **GX_ALREADY_CREATED**: (0X13) widgeten har redan skapats
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Create the string scroll wheel. */

status = gx_string_scroll_wheel_create(&wheel, “Day Wheel”,
    root, 7, days,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    ID_SCROLL_WHEEL_DAY, &size);

/* If status is GX_SUCCESS the string scroll wheel has been created. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_event_process"></a>gx_string_scroll_wheel_event_process


Händelse vid rullnings hjul i process sträng

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, 
    INT id_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för det angivna sträng rullnings hjulet. Den här tjänsten ska anropas som standard händelse hanterare av eventuella anpassade händelse bearbetnings funktioner för String-hjul.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till kontroll block för rullnings hjul
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för upprullnings hjul för sträng
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic string scroll wheel event processing as part of custom event processing function. */

UINT custom_string_scroll_wheel_event_process(GX_STRING_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default string scroll wheel event processing */
        status = gx_string_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_id_list_set"></a>gx_string_scroll_wheel_string_id_list_set

Tilldela matris med sträng-ID: n

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, INT id_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en matris med sträng-ID: n till en widget för String-rullnings hjul. Den här metoden för att tilldela strängar till ett sträng rullnings hjul rekommenderas om strängarna definieras statiskt och widgeten måste köras på flera språk. Om detta API ska användas bör du först skapa widgeten rullnings hjul med en GX_NULL sträng lista.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för sträng rullnings hjul
- **string_id_list**: matris med sträng-ID
- **id_count**: ID-listans storlek.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett sträng-ID-matris
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_VALUE**: 0X22) ogiltig storlek på ID-lista

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CONST RESOURCE_ID wheel_ids[] = {
    GX_STRING_ID_SUNDAY,
    GX_STRING_ID_MONDAY,
    GX_STRING_ID_TUESDAY,
    GX_STRING_ID_WEDNESDAY,
    GX_STRING_ID_THURSDAY,
    GX_STRING_ID_FRIDAY,
    GX_STRING_ID_SATURDAY
};

GX_STRING_SCROLL_WHEEL wheel;

/* Stop the sprite sequence */

status = gx_string_scroll_wheel_string_id_list_set(&wheel, wheel_ids, 7);

/* If status is GX_SUCCESS the ID list has been assigned. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_list_set"></a>gx_string_scroll_wheel_string_list_set

Tilldela sträng mat ris

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_string_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *string_list, 
    INT string_count);
```

### <a name="description"></a>Beskrivning

Detta tilldelar en matris med strängar till en widget för att rulla med en String-hjul. Detta kan användas för att ändra de strängar som visas när widgeten ursprungligen har skapats.

Observera att string_scroll_wheel inte stöder GX_STYLE_TEXT_COPY, och därför bör matrisen med strängar som överförs till den här funktionen definieras statiskt av programmet.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för sträng rullnings hjul
- **string_list**: matris med sträng pekare
- **string_count**: sträng mat ris storlek.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har ändrat strängar för rullnings hjul
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_VALUE**: (0X22) ogiltig storlek på sträng lista

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Set the array of strings to the scroll wheel. */

status = gx_string_scroll_wheel_string_list_set(&wheel, days, 7);

/* If status is GX_SUCCESS the string array has been assigned. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_studio_widget_create"></a>gx_studio_widget_create

Skapa widget som definierats i filen med skapade specifikationer för Studio

### <a name="prototype"></a>Prototyp

```C
GX_WIDGET *gx_studio_widget_create(
    GX_BYTE *control,
    GX_CONST GX_STUDIO_WIDGET *definition, 
    GX_WIDGET *parent);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget och widgetens underordnade med en widget som definieras i filen GUIX Studio Generated Specifications. Med den här funktionen undviks "efter namn"-sökningen av den liknande funktionen `gx_studio_named_widget_create()` .

GX_STUDIO_WIDGETs strukturen definieras i huvud filen för programspecifikationer som genererades av GUIX Studio.

För statiskt allokerade widgetar definieras widgetens kontroll block i den genererade specifikationer. c-filen och angivet widgets namn som definierats i GUIX Studio. För dynamiskt allokerade widgetar ska programmet pass GX_NULL som kontroll block adressen för widgeten och funktionen försöker dynamiskt allokera widgets kontroll blocket med hjälp av `gx_system_memory_allocate()` funktionen, som också definieras av och tillhandahålls av programmet.

För att ett program ska referera direkt till widgeten GUIX Studio i den genererade filen med specifikationer, är det nödvändigt att följa namngivnings konventionen som används av kod generatorn för GUI Studio. GX_STUDIO_WIDGETs strukturen som genererades i filen Specifications. c namnges alltid enligt denna konvention: <widget_name>_define, där fältet <widget_name> kan upprepas flera gånger om widgeten är underordnad en underordnad widget.

### <a name="parameters"></a>Parametrar

- **kontroll** Pekar mot widgeten kontroll block, eller GX_NULL om dynamiskt allokeras.
- **definition** Definitions struktur för skapade Studio-widget
- **överordnad** pekare till den överordnade widgeten, om det finns

### <a name="return-values"></a>Retur värden

Pekar på det skapade kontroll blocket för widgeten eller GX_NULL om skapandet misslyckades.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the widget “playlist_screen”, which is statically allocated. */

widget = gx_studio_widget_create(&playlist_screen,
    &playlist_screen_define,
    root_window);

/* If widget != GX_NULL the widget was created. */

/* create the widget “songs_screen”, which is dynamically allocated */

widget = gx_studio_widget_create(GX_NULL,
    &songs_screen_define, root_window);
```

### <a name="see-also"></a>Se även

- gx_studio_named_widget_create

## <a name="gx_studio_named_widget_create"></a>gx_studio_named_widget_create

Skapa widget som definierats i filen med skapade specifikationer för Studio

### <a name="prototype"></a>Prototyp

```C
UINT *gx_studio_named_widget_create(
    char *name, 
    GX_WIDGET *parent,
    GX_WIDGET **new_widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget och widgetens underordnade med en widget som definieras i filen GUIX Studio Generated Specifications.

Den här API-funktionen används för att skapa skärmar på den översta nivån med det skärm namn som anges i GUIX Studio-programmet som definitions identifierare för widgeten.

### <a name="parameters"></a>Parametrar

- **namn**: skärm namnet enligt definitionen i GUIX Studio-programmet.
- **överordnad**: pekar mot överordnad widget, om det finns
- **new_widget**: widgeten plats för att returnera skapade widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckades
- Det gick inte att hitta **GX_FAILURE**: (0X11) med namngiven widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the widget named “child_popup”,
   which is a child of the top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_named_widget_create(“main_menu”,
    &root_window, &menu_screen);

/* If status == GX_SUCCESS the screen was created
   and linked to the root window. */
```

### <a name="see-also"></a>Se även

- gx_studio_widget_create

## <a name="gx_studio_display_configure"></a>gx_studio_display_configure

Konfigurera bildskärm som definierats i GUIX Studio-projekt

### <a name="prototype"></a>Prototyp

```C
UINT *gx_studio_display_configure(
    USHORT display,
    UINT (*driver)(GX_DISPLAY *),
    USHORT language, 
    USHORT theme,
    GX_WINDOW_ROOT **return_root);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en GX_DISPLAY så att den är redo att användas. Den här funktionen konsoliderar funktionerna för att initiera ett GX_DISPLAY kontroll block, skapar en arbets yta för att anpassa visningen och skapar ett rot fönster för arbets ytan. Den här funktionen installerar även det språk-och resurs tema som begärs när visningen har initierats.

Den här funktionen konsoliderar den programmerings ansträngning som oftast krävs för att förbereda en visning för användning. Funktionen anropar gx_display_create (), gx_display_color_table_set, gx_display_font_table_set, gx_display_pixelmap_table_set, gx_system_language_table_set, gx_system_active_language_set, gx_system_scroll_appearance_set, gx_canvas_create och gx_window_root_create funktioner, som i annat fall skulle krävas av program programmet.

### <a name="parameters"></a>Parametrar

- **Display**: index i visnings tabellen, som motsvarar visnings definitionerna i Studio-projektfilen.
- **driv rutin**: pekare för att Visa initierings funktionen för driv rutinen. Den här funktionen anropas för att initiera de indirekta funktions punkterna i GX_DISPLAY kontroll blocket, samt utföra eventuella nödvändiga maskin varu installationer.
- **språk**: index för ursprungligt språk tabell
- **språk**: inledande tema index
- **root**: pekare till variabel i vilken du vill returnera rot fönster adressen eller GX_NULL.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckades
- Det gick inte att initiera visning av **GX_FAILURE**: (0x11)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the widget named “child_popup”, which is a child of the
   top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_display_configure(MAIN_DISPLAY,
    my_driver_setup, LANGUAGE_ENGLISH, DEFAULT_THEME, GX_NULL);

/* If status == GX_SUCCESS the display was initialized, a canvas was
created for the display, a root window was created for the canvas, and
the requested language and theme have been installed.
*/
```

### <a name="see-also"></a>Se även

- gx_display_create
- gx_display_color_table_set
- gx_display_font_table_set
- gx_display_pixelmap_table_set
- gx_system_language_table_set
- gx_system_active_language_set
- gx_system_scroll_appearance_set
- gx_canvas_create
- gx_window_root_create

## <a name="gx_system_active_language_set"></a>gx_system_active_language_set

Ange aktivt språk

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_active_language_set(GX_UBYTE language);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger det aktuella språket. Språk indexet måste vara mindre än antalet kolumner i program Strängs tabellen. Den här funktionen har ersatts av gx_display_active_language_set. Alla nya program bör använda gx_display_active_langauge_set.

### <a name="parameters"></a>Parametrar

- **språk**: språk index, definierat i resurs huvud filen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett ett aktivt språk
- **GX_CALLER_ERROR**: * * (0X11) ogiltig anropare av den här funktionen
- **GX_PTR_ERROR**: * * (0X07) ogiltig pekare
- **GX_INVALID_VALUE**: * * (0X22) ogiltigt språk index

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set active language and mark widget canvas as dirty. */
status = gx_system_active_language_set(ID_LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>Se även

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get

## <a name="gx_system_animation_get"></a>gx_system_animation_get

Hämta kontroll block för animering från poolen system

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_animation_get(GX_ANIMATION **animation);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kan användas för att hämta ett kontroll block för animering från en pool av sådana kontroll block som underhålls av gx_system-komponenten. Animeringssekvensen för animeringssekvenser och relaterade API-tjänster anges bara om konstanten GX_ANIMATION_POOL_SIZE definieras med värdet 0. Standardinställningen för det här värdet är 6, vilket innebär att systemanimeringens Control Block-pool innehåller storlek GX_ANIMATION kontroll block.

Ett animerat kontroll block som tilldelas med detta API returneras automatiskt till den kostnads fria poolen om animeringen körs för slut för ande. Om animeringen stoppas med hjälp av gx_animation_stop eller inte kan startas på grund av ett returnerat fel, ska kontroll blocket för animeringen returneras till den kostnads fria poolen av programmet med hjälp av gx_system_animation_free.

### <a name="parameters"></a>Parametrar

- **animering**: adress för den pekare som ska ta emot GX_ANIMATION pekare.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) hämtade kontroll block för animering
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig animeringseffekt
- **GX_OUT_OF_ANIMATIONS**: (0X31) systemets animeringssekvens har tömts

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    gx_animation_start(animation, animation_info);
}
```

### <a name="see-also"></a>Se även

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_free

## <a name="gx_system_animation_free"></a>gx_system_animation_free

Returnera ett kontroll block för animering till mediepoolen

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_animation_free(GX_ANIMATION *animation);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kan användas för att returnera ett kontroll block för animering till mediepoolen. Animeringssekvensen för animeringssekvenser och relaterade API-tjänster anges bara om konstanten GX_ANIMATION_POOL_SIZE definieras med värdet 0. Standardinställningen för det här värdet är 6, vilket innebär att systemanimeringens Control Block-pool innehåller storlek GX_ANIMATION kontroll block.

Ett animerat kontroll block som tilldelas med gx_system_animation_get () returneras automatiskt till den kostnads fria poolen om animeringen körs för slut för ande. Försök att returnera ett kontroll block för animering till den lediga poolen som redan har returnerats till den kostnads fria poolen har ingen påverkan.

Om animeringen stoppas med hjälp av gx_animation_stop, eller om det inte går att starta på grund av ett returnerat fel, ska det animerings block som har hämtats med gx_system_animation_get () returneras till den kostnads fria poolen av programmet med hjälp av gx_system_animation_free ().

En animering måste vara i inaktivt läge innan den kan returneras till den kostnads fria poolen. En animering är i inaktivt läge när den inte har startats, när den stoppas eller när den körs för slut för ande.

### <a name="parameters"></a>Parametrar

- **animering**: pekar mot GX_ANIMATION kontroll blocket.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) uccessfully-publicerat animation block
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig animeringseffekt
- **GX_INVALID_ANIMATION**: (0x32) animeringen är inte inaktiv eller har inte allokerats från mediepoolen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    status = gx_animation_start(animation, animation_info);

    if (status != GX_SUCCESS)
    {
        /* animation did not start, return it to the free pool */
        gx_system_animation_free(animation);
    }
}
```

### <a name="see-also"></a>Se även

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get

## <a name="gx_system_bidi_text_disable"></a>gx_system_bidi_text_disable

Inaktivera stöd för dynamisk dubbelriktad text

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_bidi_text_disable(VOID);
```

### <a name="description"></a>Beskrivning

Tjänsten inaktiverar stöd för dynamisk dubbelriktad text. Den här tjänsten kräver att GX_DYNAMIC_BIDI_TEXT_SUPPORT definieras när GUIX-biblioteket skapas och krävs endast om körningen av dubbelriktade sträng data krävs. De flesta program använder GUIX Studio för att skapa korrekt omordning dubbelriktade text strängar.

### <a name="parameters"></a>Parametrar

**Ingen**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) stöd för dubbelriktad dubbelriktad text

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Diable bidi text support. */
status = gx_system_bidi_text_disable();

/* If status is GX_SUCCESS, bidi text support was disabled. */
```

### <a name="see-also"></a>Se även

- gx_system_bidi_text_enable

## <a name="gx_system_bidi_text_enable"></a>gx_system_bidi_text_enable

Aktivera stöd för dynamisk dubbelriktad text

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_bidi_text_enable(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten möjliggör dynamisk dubbelriktad text support. Den här tjänsten kräver att GX_DYNAMIC_BIDI_TEXT_SUPPORT definieras när GUIX-biblioteket skapas och krävs endast om körningen av dubbelriktade sträng data krävs. De flesta program använder GUIX Studio för att skapa korrekt omordning dubbelriktade text strängar.

### <a name="parameters"></a>Parametrar

**Ingen**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har aktiverat stöd för dubbelriktad text

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Enable bidi text support. */
status = gx_system_bidi_text_enable();

/* If status is GX_SUCCESS, bidi text support was enabled. */
```

### <a name="see-also"></a>Se även

- gx_system_bidi_text_disable

## <a name="gx_system_canvas_refresh"></a>gx_system_canvas_refresh

Uppdatera alla skadade arbets ytor

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_canvas_refresh(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tvingar fram en omedelbar omritning av alla skadade widgetar och arbets ytor. Den här tjänsten anropas vanligt vis internt av GUIX-systemkomponenten, men kan anropas av programmet för att tvinga fram en omedelbar omritning av systemet.

### <a name="parameters"></a>Parametrar

**Ingen**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har publicerat ett Animations block
- **GX_INVALID_CANVAS**: (0X20) ingen arbets yta har skapats
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Force immediate redraw operation. */
status = gx_system_canvas_refresh();

/* If status is GX_SUCCESS, canvas has been redraw. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_mark"></a>gx_system_dirty_mark

Felaktigt markerat fält

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_dirty_mark(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten markerar det här fältet i widgeten som smutsig. Detta gör att widgeten kan ställas in på ett effektivt sätt när system händelse bearbetningen har slutförts.

### <a name="parameters"></a>Parametrar

- **widget**: pekare mot widget kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har marker ATS som felaktig i widget
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Mark widget “my_widget” as dirty. */
status = gx_system_dirty_mark(&my_widget);

/* If status is GX_SUCCESS the area associated
   with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_partial_add"></a>gx_system_dirty_partial_add

Markera ofullständigt arean som felaktig

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_dirty_partial_add(
    GX_WIDGET *widget,
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Beskrivning

Den här tjänsten markerar del fältet i widgeten som smutsig. Detta köar widgeten för att rita om av GUIX-arbetsytans uppdaterings åtgärd när system händelse bearbetningen har slutförts.

### <a name="parameters"></a>Parametrar

- **widget**: pekare mot widget kontroll block
- **dirty_area**: smutsig yta i widgeten för att markera smutsig

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) slutfört partiellt felaktigt ytdiagram
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_SIZE**: (0X19) ogiltig storlek på smutsig yta

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Mark widget “my_widget” partial area as dirty. */

status = gx_system_dirty_partial_add(&my_widget,
    &partial_area);

/* If status is GX_SUCCESS the partial area “partial_area”
associated with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_draw_context_get"></a>gx_system_draw_context_get

Hämta rit kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_draw_context_get(GX_DRAW_CONTEXT **current_context);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar en pekare till den aktuella rit kontexten.

### <a name="parameters"></a>Parametrar

- **current_context**: pekare till mål för aktuell rit kontext pekare

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad aktuell kontext Hämta
- **GX_PTR_ERROR**: 0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_DRAW_CONTEXT *current_context;

/* Get current drawing context. */

status = gx_system_draw_context_get(&current_context);

/* If status is GX_SUCCESS the current drawing context
   is contained in “current_context”. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_fold"></a>gx_system_event_fold

Skicka händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_event_fold(GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten söker efter en händelse av samma typ i GUIX-händelse kön. Om en händelse av samma typ finns, uppdateras händelse nytto lasten så att den matchar den nya händelsen. Om det inte finns någon matchande händelse anropas funktionen gx_system_event_send för att lägga till den nya händelsen i slutet av händelse kön.

Den här funktionen används ofta av driv rutiner för snabb touch-inmatning för att förhindra att händelse kön fylls med flera PEN_DRAG händelser. Den här funktionen kan också anropas av programmet för att förhindra att flera händelser av samma typ läggs till i händelse kön GUIX.

### <a name="parameters"></a>Parametrar

- **händelse**: pekare till händelse

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad händelse sändning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_EVENT my_event;

memset(&my_event, 0, sizeof(GX_EVENT));

my_event.gx_event_type = GX_EVENT_PEN_DOWN;

my_event.gx_event_payload.gx_event_pointdata.gx_point_x = 100;
my_event.gx_event_payload.gx_event_pointdata.gx_point_y = 200;

/* Send “my_event” for processing. */
status = gx_system_event_fold(&my_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_send"></a>gx_system_event_send

Skicka händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_event_send(GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar den angivna händelsen till GUIX system Event Queue. Den nya händelsen placeras i slutet av kön.

### <a name="parameters"></a>Parametrar

- **händelse**: pekare till händelse

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad händelse sändning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Send “new_event” for processing. */

GX_EVENT new_event;

new_event.gx_event_target = widget ->gx_widget_parent;
new_event.gx_event_type = MY_EVENT_TYPE;

/* Set optional param. */
new_event.gx_event_payload.xxxx = yyyy
new_event.gx_event_sender = widget->gx_widget_id;

/* Push the event to event pool. */
status = gx_system_event_send(&new_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_focus_claim"></a>gx_system_focus_claim

Fokusera på anspråk

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_focus_claim(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hävdar fokus för den angivna widgeten. Om widgeten inte tidigare har fokus får den en GX_EVENT_FOCUS_GAINED-händelse.

### <a name="parameters"></a>Parametrar

- **widget**: pekar mot widget kontroll block till anspråk fokus

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) ett lyckat fokus krav
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_NO_CHANGE**: (0X08) widgeten redan äger fokus
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET**: (0X12-widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Claim focus for widget “my_widget”. */
status = gx_system_claim_focus(&my_widget);

/* If status is GX_SUCCESS the focus has been claimed for
   “my_widget”. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_initialize"></a>gx_system_initialize

Initiera GUIX

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_initialize(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar GUIX. Tjänsten måste anropas före någon annan GUIX-API-tjänst och bör bara anropas en gång vid system start.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad system initiering
- **GX_SYSTEM_ERROR**: (0XFE) ogiltig GX_EVENT kontroll block storlek eller händelse kön/mutex/tråden Create misslyckades.
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Initialize GUIX. */
status = gx_system_initialize();

/* If status is GX_SUCCESS, GUIX has been initialized. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_language_table_get"></a>gx_system_language_table_get

Hämta aktiv språk tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_language_table_get( 
    GX_CHAR ****language_table,
    GX_UBYTE *languages_count, 
    UINT *string_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den aktiva språk tabellen. Den här funktionen har ersatts av gx_display_language_table_get. Alla nya program bör använda gx_display_language_table_get.

### <a name="parameters"></a>Parametrar

- **language_table**: adress för den pekare som ska returnera språk tabell.
- **languages_count**: adress till variabel att returnera tabell kolumner.
- **string_count**: adress till den pekare som returnerar tabell rader.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) den aktiva språk tabellen har hämtats
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR ***language_table;

GX_UBYTE language_count;

UINT string_count;

/* Retrieve the language table */

status = gx_system_language_table_get(&language_table,
    &language_count, &string_count);
```

### <a name="see-also"></a>Se även

- gx_display_language_table_get
- gx_display_language_table_set

## <a name="gx_system_language_table_set"></a>gx_system_language_table_set

Tilldela aktiv språk tabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_language_table_set(
    GX_CHAR ***language_table,
    GX_UBYTE languages_count, 
    UINT string_count);
```

### <a name="description"></a>Beskrivning

Den här tjänsten installerar den aktiva språk tabellen. Den här funktionen har ersatts av gx_display_language_table_set. Alla nya program bör använda gx_display_language_table_set.

### <a name="parameters"></a>Parametrar

- **language_table**: pekare till språk tabell.
- **languages_count**: antalet språk i tabellen.
- **string_count**: antalet sträng tabell rader.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett språk tabell
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Retrieve the language table */

status = gx_system_language_table_set(language_table,
    language_count, string_count);
```

### <a name="see-also"></a>Se även

- gx_display_language_table_set
- gx_display_language_table_get
- gx_display_active_language_set

## <a name="gx_system_memory_allocator_set"></a>gx_system_memory_allocator_set

Tilldela funktioner för minnesallokering, fördelningen

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_memory_allocator_set(VOID *(allocate)(ULONG size),
    VOID(*release)(VOID *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar programmet angiven motringning för dynamisk minnesallokering och avallokering.

Om ingen GUIX-tjänst som använder dynamisk minnesallokering krävs av programmet behöver inte den här tjänsten anropas.

Om den används ska den här tjänsten anropas efter gx_system_initialize () som rensar GUIX service pekare och före eventuell GUIX-tjänst som kräver användning av dynamisk minnesallokering.

GUIX Services som kräver en minnesallokering för körning och tjänsten för resursallokering är:

- Läser in binära resurser från extern lagring till GUIX Runtime Environment.
- Bild avkodaren för program körnings-JPEG.
- Bild avkodaren för program körnings png.
- Använda text-widgetar med GX_STYLE_TEXT_COPY.
- Körnings pixemap funktioner för att ändra storlek och rotation.
- Körnings-och widgets kontroll block tilldelning.

### <a name="parameters"></a>Parametrar

- **allokerare**: funktion för allokering av minne
- **version**: minnes fri funktion

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) tilldelade funktionen för att allokera minne
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

I följande exempel används en ThreadX byte-pool för att implementera en threadsafe-dynamisk minnesallokering och minnes tilldelnings tjänst.

```C
TX_BYTE_POOL memory_pool;

#define SCRATCHPAD_SIZE (1024 * 4)

ULONG scratchpad[SCRATCHPAD_SIZE];

/* define memory allocation service */

VOID *memory_allocate(ULONG size)
{
    VOID *memptr;

    if (tx_byte_allocate(&memory_pool, &memptr, size, TX_NO_WAIT) == TX_SUCCESS)
    {
        return memptr;
    }
    return NULL;
}

/* define memory de-allocation service */
void memory_free(VOID *mem)
{
    tx_byte_release(mem);
}

/* create byte pool and install our dynamic memory services with GUIX
*/

VOID tx_application_define(void *first_unused_memory)
{
    /* create byte pool for GUIX to use */
    tx_byte_pool_create(&memory_pool, "scratchpad", scratchpad,
        SCRATCHPAD_SIZE * sizeof(ULONG));

    guix_setup();

    /* install our memory allocator and de-allocator */
    gx_system_memory_allocator_set(memory_allocate, memory_free);
}
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_pen_configure"></a>gx_system_pen_configure

Ange Pen-konfiguration

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_pen_configure(GX_PEN_CONFIGURATION *pen_configuration);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger Penn konfigurationen för att styra hastigheten och avstånds parametrarna som används för att utlösa genereringen av GX_EVENT_FLICK händelse typer.

Gx_pen_configuration_min_drag_dist medlem i GX_PEN_CONFIGURATION är en fast punkt data typ och du bör använda GX_FIXED_VAL_MAKE (värde) för att konvertera från INT till GX_FIXED_VAL. Om du till exempel vill ange minsta avstånd för dra till 0,5 bild punkt per Tick måste du ange gx_pen_configuration_min_drag_dist till `GX_FIXED_VAL_MAKE(1) / 2` .

I GUIX frigör 5.4.0 och äldre gx_pen_configuration_min_drag_dist medlem i GX_PEN_CONFIGURATION av (INT << 8) i stället för GX_FIXED_VAL typ. Om ditt projekt med 5.4.0 version GUIX library använder detta API måste du ändra min_drag_dist parameter eller #define GUIX_5_4_0_COMPATIBILITY när du skapar GUIX-biblioteket.

### <a name="parameters"></a>Parametrar

- **pen_configuration** Pekare till Penn konfigurations struktur. **Bilaga i** innehåller definition som GX_PEN_CONFIGURATION struktur

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett Pen-konfigurationen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define pen configuration, set minimum drag distance to 0.5 pixel
per tick, maximum pen speed to 10 ticks. That means GUIX will trigger
a vertical or horizontal flick event if the drag time is smaller than
10 ticks and the drag distance is bigger than 0.5 * drag_ticks. */

GX_PEN_CONFIGURATION pen_configuration;

#if defined(GUIX_5_4_0_COMPATIBILITY)
Pen_configuration.gx_pen_configuration_min_drag_dist = (1 << 8)/ 2;
#else
pen_configuration.gx_pen_configuration_min_drag_dist = GX_FIXED_VAL_MAKE(1) / 2;
#endif

pen_configuration.gx_pen_configuration_max_pen_speed_ticks = 10;

/* Set the pen configuration. */
status = gx_system_pen_configure(&pen_configuration);

/* If status is GX_SUCCESS the touch configure has been set. */
```

## <a name="gx_system_screen_stack_create"></a>gx_system_screen_stack_create

Skapa och initiera system skärms stacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_create(
    GX_WIDGET **memory, 
    INT size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar en minnesbuffert som ska användas för systemets skärm. System skärms stacken är en valfri funktion som kan användas av programmet för att hantera utseendet på program skärms flödet.

Om programmet avser att använda skärmarna på skärmarna måste gx_system_screen_stack_create funktionen först anropas för att konfigurera skärm stackens minnes region.

### <a name="parameters"></a>Parametrar

- **minne**: pekar på det reserverade minnes blocket.
- **storlek**: storlek, i byte, för det reserverade minnes blocket.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har skapats
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
#define SCREEN_STACK_DEPTH 8
GX_WIDGET *screen_stack[SCREEN_STACK_DEPTH * 2];

UINT status;

/* Get the scrollbar appearance. */

status = gx_system_screen_stack_create(screen_stack,
    sizeof(GX_WIDGET *) * SCREEN_STACK_DEPTH * 2);

/* If status is GX_SUCCESS the system screen stack is initialized
and ready for use. */
```

### <a name="see-also"></a>Se även

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_get"></a>gx_system_screen_stack_get

Popup-fönster för de översta skärm punkterna

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_get(
    GX_WIDGET **popped_parent,
    GX_WIDGET **popped_screen);
```

### <a name="description"></a>Beskrivning

Den här funktionen visar de översta skärm punkterna i stacken och returnerar dessa pekare till anroparen. Den här funktionen skiljer sig från gx_system_screen_stack_pop () i att den sida som visas inte automatiskt är kopplad till föregående överordnade objekt. I stället visas pekarna från stacken och returneras till anroparen, så att anroparen kan koppla eller ta bort den returnerade skärmen som du vill.

### <a name="parameters"></a>Parametrar

- **popped_parent**: platsen där den överordnade widgeten ska lagras.
- **popped_screen**: plats för att lagra den välpekade skärmen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) hämtning av skärms stack pekare
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_FAILURE**: (0X10) ogiltig eller tom skärm bild

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status;

GX_WIDGET *parent_screen;

GX_WIDGET *popped_screen;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_get(&parent_screen, &popped_screen);

/* If status is GX_SUCCESS, parent_screen and
popped_screen hold the topmost screen stack pointers. */
```

### <a name="see-also"></a>Se även

- gx_system_screen_stack_create
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_pop"></a>gx_system_screen_stack_pop

Plocka den översta posten från system skärms stacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_pop();
```

### <a name="description"></a>Beskrivning

Den här funktionen kan användas för att skriva över den översta posten i skärm bilden och automatiskt koppla den utskrivna skärmen till den underordnade widgeten.

### <a name="parameters"></a>Parametrar

**inget**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad hämtning av skärmande stack pekare
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_FAILURE**: (0X10) ogiltig eller tom skärm bild

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_pop();

/* If status is GX_SUCCESS, the topmost screen stack entry has been
popped from the stack and re-attached to the previous parent. */
```

### <a name="see-also"></a>Se även

- gx_system_screen_stack_get
- gx_system_screen_stack_create
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_push"></a>gx_system_screen_stack_push

Skicka en widget och en överordnad pekare till skärm bilden

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_push(GX_WIDGET *screen)
```

### <a name="description"></a>Beskrivning

Den här tjänsten placerar en pekare till angiven widget, som vanligt vis är en skärm på den översta nivån, i skärm bilden. Om widgeten har en överordnad tas den bort från den överordnade. Den överordnade widgeten pekar också på skärmen. Den överordnade widgeten kan vara NULL, vilket innebär att en skärm som inte är synlig eller kopplad till någon överordnad kan flyttas till skärm bilden. Om en widget som inte har någon överordnad skickas till skärm bilden, ska API: et för screen_stack_get () användas för att hämta den nedladdade skärmen, i stället för screen_stack_pop att använda API: et (), som försöker återansluta till den tidigare överordnade widgeten.

### <a name="parameters"></a>Parametrar

- **skärm**: pekar mot widgeten som ska flyttas till skärm bilden.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) får rullnings listens utseende
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_push(window);

/* If status is GX_SUCCESS, the widget pointed to by “window” has
been pushed to the screen stack, along with the widget’s parent
ponter. */
```

### <a name="see-also"></a>Se även

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_create
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_reset"></a>gx_system_screen_stack_reset

Återställa system skärms stacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_reset();
```

### <a name="description"></a>Beskrivning

Den här funktionen tar bort alla poster från system skärms stacken. Om skärmarna som visas från stacken har dynamiskt allokerade kontroll block tilldelade av GUIX Studio frigörs minnet för dessa kontroll block.

### <a name="parameters"></a>Parametrar

**inget**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) får rullnings listens utseende
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_reset();

/* If status is GX_SUCCESS the system screen stack has been cleared
of entries. */
```

### <a name="see-also"></a>Se även

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_create

## <a name="gx_system_scroll_appearance_get"></a>gx_system_scroll_appearance_get

Hämta rullnings utseende

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_scroll_appearance_get(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *return_appearance);
```

### <a name="description"></a>Beskrivning

Den här tjänsten får rullnings listens utseende.

### <a name="parameters"></a>Parametrar

- **format**: rullnings List format: `GX_SCROLLBAR_HORIZONTAL` eller `GX_SCROLLBAR_VERTICAL`
- **return_appearance**: pekar mot målets utseende. **Bilaga i** innehåller en definition som GX_SCROLLBAR_APPERANCE

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) får rullnings listens utseende
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

/* Get the scrollbar appearance. */

status = gx_system_scroll_appearance_get(style, &my_appearance);

/* If status is GX_SUCCESS “my_appearance” now contains the scroll
appearance. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_set
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_scroll_appearance_set"></a>gx_system_scroll_appearance_set

Ange rullnings utseende

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_scroll_appearance_set(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *appearance);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger standard rullnings utseende. När en rullning skapas, används den här utseende strukturen om inte programmet tillhandahåller en anpassad version.

### <a name="parameters"></a>Parametrar

- **format**: rullnings format `GX_SCROLLBAR_HORIZONTAL` eller `GX_SCROLLBAR_VERTICAL`
- **utseende**: pekare till utseende-strukturen initierad med olika visnings egenskaper för rullnings listen. Se **bilaga i** för definitionen av GX_SCROLLBAR_APPEARANCEs strukturen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett rullnings utseende uppsättning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

memset(&my_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

my_appearance.gx_scroll_width = 20;
my_appearance.gx_scroll_thumb_width = 18;

my_appearance.gx_scroll_thumb_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_border_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_button_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_travel_min = 20;
my_appearance.gx_scroll_thumb_travel_max = 20;
my_appearance.gx_scroll_thumb_border_style = GX_STYLE_BORDER_THIN;

/* Set the scroll appearance. */

status = gx_system_scroll_appearance_set(GX_SCROLLBAR_VERTICAL, &my_appearance);

/* If status is GX_SUCCESS the scroll appearance has been set. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_start"></a>gx_system_start

Starta GUIX

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_start(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar GUIX-bearbetning. Under normala omständigheter returnerar den här funktionen aldrig, utan börjar i stället att bearbeta GUIX-händelse kön. När händelse kön för GUIX är tom stoppas den anropande tråden tills nya händelser tas emot i händelse kön för GUIX.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad system start
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Start GUIX. */
status = gx_system_start();

/* If status is GX_SUCCESS . GUIX has been started. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_string_get"></a>gx_system_string_get

Hämta sträng

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_get(
    GX_RESOURCE_ID string_id,
    GX_CHAR **return_string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar strängen för det angivna resurs-ID: t med den första definierade visningen och det aktuella aktiva språket. Den här funktionen har ersatts av gx_display_string_get. Alla nya program bör använda gx_display_string_get.

### <a name="parameters"></a>Parametrar

- **string_id**: sträng resurs-ID
- **return_string**: pekar mot en sträng destinations pekare

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad sträng hämtning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR (0x07)**: ogiltig pekare
- **GX_INVALID_RESOURCE_ID**: (0X33) ogiltigt resurs-ID

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get the string associated with MY_STRING_ID. */

status = gx_system_string_get(MY_STRING_RESOURCE_ID, &my_string);

/* If status is GX_SUCCESS the string is contained in “my_string”.
*/
```

### <a name="see-also"></a>Se även

- gx_display_string_get
- gx_display_string_table_get
- gx_display_language_table_set

## <a name="gx_system_string_table_get"></a>gx_system_string_table_get

Hämtar sträng tabellen

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_table_get(
    GX_UBYTE language,
    GX_CHAR ***string_table,
    UINT *get_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar sträng tabellen för det begärda språket från den första visningen. Den här funktionen har ersatts av gx_display_string_table_get. Alla nya program bör använda gx_display_string_table_get.

### <a name="parameters"></a>Parametrar

- **språk**: språk index
- **string_table**: pekar på lagrings utrymmet för sträng tabell PEKAREN eller null om anroparen inte behöver hämta pekaren till sträng tabellen.
- **get_size**: pekar på lagrings utrymmet för antalet strängar i sträng tabellen, eller null om anroparen inte behöver hämta antalet strängar i sträng tabellen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad sträng tabell Hämta
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get the string table. */

CHAR **my_string_table; UINT table_size;

status = gx_system_string_table_get(LANGUAGE_ID_ENGLISH,
    &my_string_table, &table_size);

/* If status is GX_SUCCESS . the pointer to the string table has
been obtained. */
```

### <a name="see-also"></a>Se även

- gx_display_string_table_get
- gx_display_string_get
- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_system_string_width_get"></a>gx_system_string_width_get

Hämta sträng bredd (inaktuellt)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_width_get(
    GX_FONT *font, GX_CHAR *string,
    INT string_length,
    GX_VALUE *return_width);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_system_string_width_get_ext ().

Den här tjänsten beräknar visnings bredden för den angivna strängen i bild punkter med det angivna teckensnittet. Om parametern string_length är >= 0 inkluderas bara antalet tecken för begäran i beräkningen. Om parametern string_length är-1 används hela strängen upp till NULL-avgränsaren i beräkningen.

### <a name="parameters"></a>Parametrar

- **teckensnitt**: pekar mot strängens teckensnitt
- **sträng**: pekar mot sträng
- **string_length**: sträng längd
- **return_width**: målet för bredden på strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad sträng bredd get
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_FONT**: (0X16) ogiltigt teckensnitt
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get the string width of “my_string”. */

status = gx_system_string_width_get(&my_font, &my_string,
    strlen(my_string), &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>Se även

- gx_system_string_width_get_ext

## <a name="gx_system_string_width_get_ext"></a>gx_system_string_width_get_ext

Hämta sträng bredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_width_get_ext(
    GX_FONT *font,
    GX_STRING *string,
    GX_VALUE *return_width);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar visnings bredden för den angivna strängen i bild punkter med det angivna teckensnittet.

### <a name="parameters"></a>Parametrar

- **teckensnitt**: pekar mot strängens teckensnitt
- **sträng**: pekar mot sträng
- **return_width**: målet för bredden på strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad sträng bredd get
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_CALLER_ERROR**: 0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_FONT**: (0X16) ogiltigt teckensnitt
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING my_string; my_string.gx_string_ptr = “Monday”;

my_string.gx_string_length = strlen(my_string.gx_string_ptr);

/* Get the string width of “my_string”. */

status = gx_system_string_width_get_ext(&my_font,
    &my_string, &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>Se även

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_start"></a>gx_system_timer_start

Starta timer

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_timer_start(
    GX_WIDGET *owner, 
    UINT timer_id,
    UINT initial_ticks,
    UINT reschedule_ticks);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en timer för den angivna widgeten. Konstanten GX_MAX_ACTIVE_TIMERS definierat det högsta antalet aktiva timers som stöds. Standardvärdet för det här värdet är 32.

### <a name="parameters"></a>Parametrar

- **Owner**: pekare mot widget kontroll block
- **timer_id**: ID för timer
- **initial_ticks**: inledande förfallo datum
- **reschedule_ticks**: periodiska förfallo Tick

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad timer-start
- **GX_OUT_OF_TIMERS**: (0X04) inga fler timers
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_VALUE**: (0X22) timer (er) är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Start a periodic timer for the widget “my_widget”. */
status = gx_system_timer_start(&my_widget, MY_TIMER_ID, 10, 20);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
started. */
```

### <a name="see-also"></a>Se även

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_stop"></a>gx_system_timer_stop

Stoppa timer

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_timer_stop(
    GW_WIDGET *owner, 
    UINT timer_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar timern med den angivna timer_id associerad med den anropande widgeten. Om du vill stoppa alla timers som är länkade till en viss widget kan programmet skicka timer_id värdet 0.

### <a name="parameters"></a>Parametrar

- **Owner**: pekare mot widget kontroll block
- **timer_id**: ID för timer eller 0 för alla timers

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) slutfört timer-stopp
- **GX_NOT_FOUND**: (0X09) timer-ID hittades inte
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Stop the periodic timer for the widget “my_widget”. */
status = gx_system_timer_stop(&my_widget, MY_TIMER_ID);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
stopped. */
```

### <a name="see-also"></a>Se även

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_version_string_get"></a>gx_system_version_string_get

Hämta GUIX-bibliotekets versions sträng (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_version_string_get(GX_CHAR **version);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_system_version_string_get_ext ().

Den här tjänsten hämtar versions strängen för GUIX-biblioteket.

### <a name="parameters"></a>Parametrar

- **version**: pekare till retur sträng värde.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har hämtat versions strängen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *version;

/* get the library version string. */

status = gx_system_verrsion_string_get(&version);
```

### <a name="see-also"></a>Se även

- gx_system_version_string_get_ext ()

## <a name="gx_system_version_string_get_ext"></a>gx_system_version_string_get_ext

Hämta GUIX-bibliotekets versions sträng

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_version_string_get(GX_STRING *version);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar versions strängen för GUIX-biblioteket.

### <a name="parameters"></a>Parametrar

- **version**: pekare till retur sträng värde.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har hämtat versions strängen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING version;

/* get the library version string. */

status = gx_system_version_string_get_ext(&version);
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_widget_find

## <a name="gx_system_widget_find"></a>gx_system_widget_find

Hitta widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_widget_find(
    USHORT widget_id,
    INT search_level, 
    GX_WIDGET **return_search_result);
```

### <a name="description"></a>Beskrivning

Den här tjänsten söker efter angivet widgets-ID. Till skillnad från gx_widget_find () genomsöker den här funktionen underordnade till alla rot fönster som definieras i systemet, vilket innebär att det här är en uttömmande sökning av alla synliga widgetar. Om du känner till den överordnade widgeten som du söker efter, använder du gx_widget_find () i stället.

### <a name="parameters"></a>Parametrar

- **widget_id**: widgets-ID att söka efter
- **search_level**: definierar den rekursiva kapslings nivån som underordnade widgetar genomsöks till. Om värdet är 0 genomsöks bara omedelbara underordnade objekt för varje rot fönster. Om det här värdet är GX_SEARCH_DEPTH_INFINITE kapslar funktionen in i alla underordnade sökningar efter begärt widgets-ID. För andra värden > 0 definierar Sök nivån hur djupt kapslad den här funktionen kommer att söka efter begärd widgets-ID.
- **return_search_result**: pekare till målet för widgeten hittades

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad widgets sökning
- **GX_NOT_FOUND**: (0X09) widgets-ID hittades inte
- **GX_PTR_ERROR**: (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Search recursively from the top level widget for the widget with
ID of MY_WIDGET_ID. */

status = gx_system_widget_find(MY_WIDGET_ID,
    GX_SEARCH_DEPTH_INFINITE,
    &my_widget);

/* If status is GX_SUCCESS . the search was successful and
“my_widget” contains the pointer to the widget. */
```

### <a name="see-also"></a>Se även

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get

## <a name="gx_text_button_create"></a>gx_text_button_create

Knappen Skapa text

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_create(
    GX_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, 
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget för text knappar.

GX_TEXT_BUTTON härleds från GX_BUTTON och stöder alla gx_button API-tjänster.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **namn**: knappens logiska namn för text
- **överordnad**: pekare till överordnad widget för knappen
- **text_id**: resurs-ID för text
- **format**: text knapp format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **text_button_id**: Programdefinierat ID för text knappen
- **storlek**: knappens storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad text knapp skapa
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_ALREADY_CREATED**: (0X13) widgeten har redan skapats
- **GX_INVALID_SIZE**: (0X19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_WIDGET**: 0x12 överordnade widgeten är inte giltig


### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_BUTTON my_text_button;

GX_RECTANGLE size;

/* Define widget size. */

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Create text button “my_text_button”. */

status = gx_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID, &size);

/* If status is GX_SUCCESS, the text button “my_text_button” was
created. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_color_set
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_draw"></a>gx_text_button_draw

Knapp för att rita text

### <a name="prototype"></a>Prototyp

```C
VOID gx_text_button_draw(GX_TEXT_BUTTON *button);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar text knappen. Den här tjänsten kallas vanligt vis internt under uppdatering av arbets ytan, men kan också anropas från ritnings funktioner för anpassad text.

### <a name="parameters"></a>Parametrar

- **knapp**: pekare mot text knapp kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom text button draw function. */

VOID my_text_button_draw(GX_TEXT_BUTTON *text_button)
{
    /* Call default text button draw. */
    gx_text_button_draw(text_button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_event_process"></a>gx_text_button_event_process


Händelse för process text knapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna text knappen. Den här tjänsten ska anropas som standard händelse hanterare av eventuella funktioner för händelse bearbetning i en anpassad text knapp.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till kontroll block för text knapp
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- Händelse process för **GX_SUCCESS** (0X00) slutförd text knapp
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic text button event processing as part of custom event processing function. */

UINT custom_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text button event processing */
        status = gx_text_button_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_font_set"></a>gx_text_button_font_set

Ange tecken till text-knappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_font_set(
    GX_TEXT_BUTTON *button,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar ett teckensnitt till den angivna knappen.

### <a name="parameters"></a>Parametrar

- **knapp**: pekare mot text knapp kontroll block
- **font_id**: resurs-ID är teckensnittet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett teckensnittet
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the text button with the font ID MY_FONT. */
status = gx_text_button_font_set(&my_text_button, MY_FONT);

/* If status is GX_SUCCESS, the font of the text button
“my_text_button” was set to MY_FONT. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_color_set"></a>gx_text_button_text_color_set

Ange text knapps färg

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_color_set(
    GX_TEXT_BUTTON *text_button,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger färgen för text knappen.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **normal_text_color_id**: resurs-ID för normal text. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **selected_text_color_id**: resurs-ID för markerad text. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **disabled_text_color_id**: resurs-ID för inaktive rad text. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad text knapps färg uppsättning
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the color of the text button “my_text_button”. */
status = gx_text_button_text_color_set(&my_text_button,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the text color of “my_text_button” was
set. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_draw"></a>gx_text_button_text_draw

Stöd funktion för att rita knapp text

### <a name="prototype"></a>Prototyp

```C
VOID gx_text_button_text_draw(GX_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Beskrivning

Den här stöd funktionen ritar text delen av en text-knapp. Den här funktionen anropas internt av gx_text_button_draw och tillhandahålls som en separat API som bekvämlighet för program som definierar en anpassad knapp ritnings funktion. Program som vill anpassa knappens bakgrunds ritning kan ge sin anpassade ritnings funktion och anropa gx_text_button_text_draw-tjänsten som en del av den anpassade ritningen för att rita knapp texten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Define a custom drawing function */

VOID my_button_draw(GX_TEXT_BUTTON *button)
{
    /* Insert code here to draw button background */

    /* Call support function to do text drawing */
    gx_text_button_text_draw(button);

    /* Draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_get"></a>gx_text_button_text_get

Hämta text från text knappen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_get(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR **return_text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_text_button_text_get_ext ().

Den här tjänsten hämtar den angivna strängen från text knappen.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **return_text**: pekar mot den sträng som hämtats från text knappen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) hämtar texten från knappen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>Se även

- gx_text_button_text_get_ext

## <a name="gx_text_button_text_get_ext"></a>gx_text_button_text_get_ext

Hämta text från text knappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_get_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *return_string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den angivna strängen från text knappen.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **return_string**: pekar mot den sträng som hämtats från text knappen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) hämtar texten från knappen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get_ext(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer and length from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_id_set"></a>gx_text_button_text_id_set

Ange text resurs-ID: t för text knappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_id_set(
    GX_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger angivet sträng resurs-ID till text knappen.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **string_id**: resurs-ID för strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett sträng resurs-ID till text knappen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_INVALID_RESOURCE_ID**: sträng-ID för 0x33 är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the string ID ”MY_STRING_ID” to the text button
“my_text_button”. */

status = gx_text_button_text_id_set(&my_text_button,
    MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to
“my_text_button”. */
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get

## <a name="gx_text_button_text_set"></a>gx_text_button_text_set

Tilldela text knappen text (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_set(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_text_button_text_set_ext ().

Den här tjänsten tilldelar den angivna strängen till text knappen. Om widgeten text_button skapades med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **text**: pekar mot den null-avslutade strängen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett texten till knappen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_SYSTEM_MEMORY_ERROR**: (0X30) minnes allokeraren är inte definierad eller minnes tilldelningen misslyckades
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the string “my string” to the text button “my_text_button”.
*/

status = gx_text_button_text_set(&my_text_button, “my string”);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>Se även

- gx_text_button_event_process
- gx_text_button_text_set_ext
- gx_text_button_text_id_set

## <a name="gx_text_button_text_set_ext"></a>gx_text_button_text_set_ext

Tilldela text knappen text

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_set_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den angivna strängen till text knappen. Om widgeten text_button skapades med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade text strängen. Om GX_STYLE_TEXT_COPY inte är aktivt gör widgeten ingen privat kopia av den inkommande strängen, och därför måste strängen vara statiskt eller globalt allokerad, dvs. det får inte vara en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button**: pekare mot text knapp kontroll block
- **sträng**: pekar mot variabeln GX_STRING

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett texten till knappen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig
- **GX_SYSTEM_MEMORY_ERROR**: (0X30) minnes allokeraren är inte definierad eller minnes tilldelningen misslyckades
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING new_string; new_string.gx_string_ptr = “Monday”;

new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Assign the string “new_string” to the text button
“my_text_button”. */

status = gx_text_button_text_set_ext(&my_text_button, &new_string);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>Se även

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get
- gx_text_button_text_id_set

## <a name="gx_text_input_cursor_blink_interval_set"></a>gx_text_input_cursor_blink_interval_set

Ange blinknings intervall för markör

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_input_cursor_blink_interval_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE blink_interval);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger blinknings intervall svärdet för markören.

### <a name="parameters"></a>Parametrar

- **cursor_input** Markör kontroll block
- **blink_interval** Värde som ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett markörens blinknings intervall
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_VALUE**: (0X22) blinkande intervall värde är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set the blink interval value of “input_cursor” to 2. */
status = gx_text_input_cursor_blink_interval_set(input_cursor, 2);

/* If status is GX_SUCCESS, the blink interval value of
“input_cursor” has been successfully set to 2. */
```

### <a name="see-also"></a>Se även

- gx_text_input_cursor_height_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_height_set"></a>gx_text_input_cursor_height_set

Ange markörens höjd

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_input_cursor_height_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE height);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger markörens höjd.

### <a name="parameters"></a>Parametrar

- **cursor_input**: markör kontroll block
- **höjd** Värde som ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett markörens höjd
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_VALUE**: (0X22) height-värdet är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set height value of “input_cursor”. */
status = gx_text_input_cursor_height_set(&input_cursor, 15);

/* If status is GX_SUCCESS, the height value of “input_curosr” has
been successfully set to 15. */
```

### <a name="see-also"></a>Se även

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_width_set"></a>gx_text_input_cursor_width_set

Ange markörens bredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_input_cursor_blink_width_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE *width);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger markörens bredd.

### <a name="parameters"></a>Parametrar

- **cursor_input**: markör kontroll block
- **width**: värdet som ska anges

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett markörens bredd
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_VALUE**: (0X22) bredd är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set width of “input_curosr” to 2. */

status = gx_text_input_cursor_blink_width_set(&input_cursor, 2);

/* If status is GX_SUCCESS, the width of “input_cursor” has been
successfully set to 2. */
```

### <a name="see-also"></a>Se även

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_height_set

## <a name="gx_text_scroll_wheel_callback_set"></a>gx_text_scroll_wheel_callback_set

Tilldela motringningsfunktionen för text typen rulla hjul (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_callback_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *(*callback)(GX_TEXT_SCROLL_WHEEL *, int));
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_text_scroll_wheel_callback_set_ext ().

Den här tjänsten tilldelar callback-funktionen som en text typs rullnings hjul anropar för att fastställa vilken text sträng som ska visas på varje rad i rullnings hjulet.

För GX_NUMERIC_SCROLL_WHEEL och GX_STRING_SCROLL_WHEEL anges standardfunktionen för motringning och programmet behöver inte göra några ändringar för att använda dessa standard implementeringar.

Detta API tillhandahålls för att tillåta att programmet anpassar formateringen eller andra parametrar för den sträng som visas på varje rad i widgeten rullnings hjul.

Motringningsfunktionen får som inmatad som en pekare till kontroll blocket Scroll Wheel och det rad nummer som visas. Funktionen ska returnera en pekare till en text sträng.

### <a name="parameters"></a>Parametrar

- **hjul** Sträng rullnings kontroll block adress
- **motringning** Pekare till motringnings funktion

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett återanrop
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

GX_CHAR *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
    }
    else
    {
        return(“Invalid”);
    }
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_callback_set_ext"></a>gx_text_scroll_wheel_callback_set_ext

Tilldela motringningsfunktionen för text typen rulla hjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_callback_set_ext(
    GX_TEXT_SCROLL_WHEEL *wheel,
    UINT *(*callback)(GX_TEXT_SCROLL_WHEEL *, int, GX_STRING *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar callback-funktionen som en text typs rullnings hjul anropar för att fastställa vilken text sträng som ska visas på varje rad i rullnings hjulet.

För GX_NUMERIC_SCROLL_WHEEL och GX_STRING_SCROLL_WHEEL anges standardfunktionen för motringning och programmet behöver inte göra några ändringar för att använda dessa standard implementeringar.

Detta API tillhandahålls för att tillåta att programmet anpassar formateringen eller andra parametrar för den sträng som visas på varje rad i widgeten rullnings hjul.

Motringningsfunktionen får som inmatad som en pekare till kontroll blocket Scroll Wheel och det rad nummer som visas. Funktionen ska returnera en pekare till en text sträng.

### <a name="parameters"></a>Parametrar

- **hjul** Sträng rullnings kontroll block adress
- **motringning** Pekare till motringnings funktion

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett återanrop
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

UINT *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row,
    GX_STRING *return_string)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
        return_string->gx_string_ptr = string_buffer;
        return_string->gx_string_length = strlen(string_buffer);
    }
    else
    {
        return_string->gx_string_ptr = “Invalid”;
        return_string->gx_string_length = strlen(“Invalid”);
    }

    return GX_SUCCESS;
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set_ext(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_create"></a>gx_text_scroll_wheel_create

Skapa ett hjul för text rullning

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_create(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    ULONG style, 
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett text rullnings hjul. Text rullnings hjulet är en grundläggande widget för GX_STRING_SCROLL_WHEEL och GX_NUMERIC_SCROLL_WHEEL typ av widgetar. Den här funktionen anropas internt av gx_string_scroll_wheel_create och gx_numeric_scroll_wheel_create och tillhandahålls som en separat API som bekvämlighet för program som definierar en anpassad widget för rullnings hjul.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för text rullnings hjul
- **namn**: Programdefinierat widgets namn
- **överordnad**: överordnad hjul eller GX_NULL
- **total_rows**: totalt antal rader som ska visas för användaren
- **format**: önskade stil flaggor
- **ID**: programdefinierade hjul stils flaggor
- **storlek**: inledande rullnings hjul storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) text rullnings hjulet har skapats
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_ALREADY_CREATED**: (0X13) widgeten har redan skapats
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig


### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define a custom scroll wheel widget. */
typedef MY_SCROLL_WHEEL_STRUCT
{
    GX_TEXT_SCROLL_WHEEL text_scroll_wheel;

    /* Add custom members here. */

} MY_SCROLL_WHEEL;

MY_SCROLL_WHEEL my_scroll_wheel;

UINT my_scroll_wheel_create(MY_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    INT total_rows, ULONG style, USHORT Id,
    GX_CONST GX_RECTANGLE *size)
{
    /* Call base creation. */
    status = gx_text_scroll_wheel_create(
        &wheel.text_scroll_wheel,
        ”my_text_scroll_wheel”, GX_NULL, 7,
        GX_STYLE_ENABLED, ID_MY_SCROLL_WHEEL, &size);

    if (status == GX_SUCCESS)
    {
        /* Add custom initialization here. */
        if(parent)
        {
            gx_widget_link(parent, (GX_WIDGET *)wheel);
        }
    }
}
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_draw"></a>gx_text_scroll_wheel_draw

Rita ett hjul för text rullning

### <a name="prototype"></a>Prototyp

```C
VOID gx_text_scroll_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>Beskrivning

Detta är standard ritnings funktionen för alla typer av hjul baserat på GX_TEXT_SCROLL_WHEEL. Den här funktionen kan åsidosättas av program som kräver anpassning av text rullnings hjulets utseende.

GX_STRING_SCROLL_WHEEL och GX_NUMERIC_SCROLL_WHEEL är båda baserade på eller härleds från GX_TEXT_SCROLL_WHEEL.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för sträng rullnings hjul

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom wheel draw function. */
UINT my_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel)
{
    /* Perform default drawing */
    gx_text_scroll_wheel_draw(wheel);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_event_process"></a>gx_text_scroll_wheel_event_process


Process text rullnings hjul, händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för det angivna text rullnings hjulet. Den här tjänsten ska anropas som standard händelse hanterare med ett anpassat text rullnings hjul händelse bearbetnings funktioner.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare mot kontroll block för text rullnings hjul
- **event_ptr** Pekare till händelsen att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) händelse process för text rullnings hjul
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic text scroll wheel event processing as part of custom event processing function. */

UINT custom_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text scroll wheel event processing */
        status = gx_text_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_font_set"></a>gx_text_scroll_wheel_font_set

Tilldela teckensnitt som används för att rita rullnings hjuls rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_font_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_font, 
    GX_RESOURCE_ID selected_font);
```

### <a name="description"></a>Beskrivning

Tilldela teckensnitten som ska användas för att rita texten i en text rullnings bar Wheel-baserad widget.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för sträng rullnings hjul

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har tilldelat hjul teckensnitt
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_NUMERIC_SCROLL_WHEEL wheel;

status = gx_text_scroll_wheel_font_set(&wheel,
    GX_FONT_ID_WHEEL_NORMAL,
    GX_FONT_ID_WHEEL_SELECTED);

/* If status is GX_SUCCESS, the scroll wheel fonts have been assigned. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_text_color_set"></a>gx_text_scroll_wheel_text_color_set

Tilldela färger som används för att rita rullnings hjuls rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_text_color_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCe_ID disabled_text_color);
```

### <a name="description"></a>Beskrivning

Den här funktionen tilldelar text färgerna som används för att rita en textbaserade rullnings hjuls rader.

### <a name="parameters"></a>Parametrar

- **hjul**: kontroll block adress för sträng rullnings hjul
- **normal_text_color**: färg som används för att rita icke-markerade rader
- **selected_text_color**: färg som används för att rita den markerade raden.
- **disabled_text_color**: färg som används för att rita text för inaktiverad widget.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har tilldelat text färg för rullnings hjul
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING_SCROLL_WHEEL wheel;

UINT status = gx_text_scroll_wheel_text_color_set(&wheel,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the colors used to draw the wheel text have been assigned. */
```

### <a name="see-also"></a>Se även

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set

## <a name="gx_tree_view_create"></a>gx_tree_view_create

Skapa en trädvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_create(
    GX_TREE_VIEW *tree,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    ULONG style, 
    USHORT tree_view_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en trädvy som anges och associerar trädvyn med den angivna överordnade widgeten. Den accepterar alla typer av widget som underordnat meny alternativ. Vi rekommenderar att du använder GX_MENU typ widget som dess underordnade meny alternativ.

GX_TREE_VIEW härleds från GX_WINDOW och stöder alla gx_window API-tjänster.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **namn**: namnet på trädvyn
- **överordnad**: pekare till överordnad widget
- **format**: widgetens format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-speciella format.
- **menu_id**: Programdefinierat ID för trädvyn
- **storlek**: träd visningens storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad trädvy skapas
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_ALREADY_CREATED**: (0X13) widgeten har redan skapats
- **GX_INVALID_SIZE**: (0X19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_tree_view_create(&my_tree_view,
    “my_tree_view”, parent,
    GX_STYLE_ENABLED, MY_TREE_VIEW_ID,
    &size);

/* If status is GX_SUCCESS the tree view was successfully created. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_draw"></a>gx_tree_view_draw

Rita trädvy

### <a name="prototype"></a>Prototyp

```C
VOID gx_tree_view_draw(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna trädvyn. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för arbets ytans uppdatering, men exponeras för programmet för att hjälpa till med att implementera anpassade ritnings funktioner för widgetar anpassade träd visning.

### <a name="parameters"></a>Parametrar

- **träd** Pekare till trädvy, kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom tree view draw function. */
UINT my_tree_view_draw(GX_TREE_VIEW *tree_view)
{
    /* Perform default drawing */
    gx_tree_view_draw(tree_view);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_event_process"></a>gx_tree_view_event_process

Händelse för process träds visning

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_event_process(
    GX_TREE_VIEW *tree, 
    GX_EVENT event_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för den angivna trädvyn. Den här tjänsten ska anropas som standard händelse hanterare av eventuella anpassade händelse bearbetnings funktioner i trädvyn.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **event_ptr**: pekar på händelsen som ska bearbetas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad process träds händelse
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic tree view event processing as part of custom event
    processing function. */

UINT custom_tree_view_event_process(GX_TREE_VIEW *tree_view,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default tree view
                event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
    }
}
return status;
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_indentation_set"></a>gx_tree_view_indentation_set

Ange indrag för trädvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_indentation_set(
    GX_TREE_VIEW *tree,
    GX_VALUE indentation);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger indrag för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **indrag**: indrag för att ange

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har ställt in indrag i trädvy
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set tree view “my_tree” indentation to 10. */
status = gx_tree_view_indentation_set(&my_tree, 10);

/* If status is GX_SUCCESS the indentation of tree view “my_tree”
has been set to 10. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixemlap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_position"></a>gx_tree_view_position

Positions träd, Visa objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_position(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Beskrivning

Detta tjänst läges träd visar objekt.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har placerat träd visnings objekt
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Position tree view “my_tree” items. */
status = gx_tree_view_position(&my_tree);

/* If status is GX_SUCCESS the items of tree view “my_tree” has
been positioned. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_line_color_set"></a>gx_tree_view_root_line_color_set

Ange rot linje färg för trädvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_root_line_color_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID color_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar rot linje färgen för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **color_id**: resurs-ID för rot linje färg

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckades ange rot linje färg
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set root line color for tree view “my_tree”. */

status = gx_tree_view_root_line_color_set(&my_tree,
    MY_ROOT LINE_COLOR_ID);

/* If status is GX_SUCCESS the root line color of the tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_pixelmap_set"></a>gx_tree_view_root_pixelmap_set

Ange rot-Pixelmap för träd visning

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_root_pixelmap_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID expand_map_id,
    GX_RESOURCE_ID collapse_map_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar expandera och komprimera Pixelmap för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **expand_map_id**: resurs-ID för Expand-Pixelmap
- **collapse_map_id**: resurs-ID för komprimering av Pixelmap

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har angett rot-Pixelmap
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set root pixelmaps for tree view “my_tree”. */

status = gx_tree_view_root_pixelmap_set(&my_tree,
    MY_EXPAND_MAP_ID,
    MY_COLLAPSE_MAP_ID);

/* If status is GX_SUCCESS the root pixelmaps of tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_get"></a>gx_tree_view_selected_get

Hämta markerat objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_selected_get(
    GX_TREE_VIEW *tree,
    GX_WIDGET **selected);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det aktuella markerade objektet i trädvyn.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **markerad**: pekare till markerad widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har hämtat det valda objektet
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Retrieve selected item of tree view “my_tree”. */

GX_WIDGET *selected;

status = gx_tree_view_selected_get(&my_tree, &selected);

/* If status is GX_SUCCESS the selected item of tree view “my_tree”
has been retrieved. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_set"></a>gx_tree_view_selected_set

Ange valt objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_selected_set(
    GX_TREE_VIEW *tree,
    GX_WIDGET *selected);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger valt objekt för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd**: pekare mot trädvyn kontroll block
- **markerad**: pekare till det nya markerade objektet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad Draw-meny
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) ogiltig pekare
- **GX_INVALID_WIDGET**: (0X12) widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set selected item of tree view “my_tree” to “tree_view_item’. */
status = gx_tree_view_selected_set(&my_tree, &tree_view_item);

/* If status is GX_SUCCESS selected item of tree view “my_menu” has
been set to “tree_view_item”. */
```

### <a name="see-also"></a>Se även

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get

## <a name="gx_utility_canvas_to_bmp"></a>gx_utility_canvas_to_bmp

Konvertera arbets ytans Memort till bitmapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_canvas_to_bmp(
    GX_CANVAS *canvas, 
    GX_RECTANGLE *rect,
    UINT (*write_data)(GX_UBYTE *byte_data, UINT data_count));
```

### <a name="description"></a>Beskrivning

Den här tjänsten konverterar arbets ytans minne till bitmappsfilen.

### <a name="parameters"></a>Parametrar

- **arbets yta**: kontroll block för arbets yta
- **rect**: rektangel att konvertera
- **write_data**: motringnings funktion pekare för att skriva data till

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har konverterat heltals värde till sträng
- **GX_PTR_ERROR**: (0X07) ogiltig pekare för returnerad buffert
- **GX_INVALID_SIZE**: (0X19) ogiltig storlek på retursekvens

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
FILE *fp = GX_NULL;

/* define call back function of how to write the data read from
canvas memory. */

UINT write_data_callback(GX_UBYTE *byte_data, UINT data_count)
{
    if (fp)
    {
        fwrite(byte_data, 1, data_count, fp);
    }
    return GX_SUCCESS;
}

VOID scroll_wheel_screen_draw(GX_WINDOW *window)
{
    UINT status;

    GX_RECTANGLE size = {31,31,610,450};
    gx_window_draw(window);
    if (screenshot)
    {
        fp = fopen("../screenshot.bmp", "wb");
        /* Convert canvas memory to bitmap format.
           Status GX_SUCCESS means operation succeed. */
        status = gx_utility_canvas_to_bmp(root->gx_window_root_canvas,
            &size, write_data_callback);

        fclose(fp);
    }
}
```

### <a name="see-also"></a>Se även

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_circle_point_get"></a>gx_utility_circle_point_get

Beräkna punkt på en cirkel

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_circle_point_get(
    INT xCenter, 
    INT yCenter,
    UINT radius, 
    INT angle, 
    GX_POINT *point);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar punkten på en cirkel med cirkelns mitt punkt, radie och vinkel.

### <a name="parameters"></a>Parametrar

- **xCenter**: x-koordinat för cirkel Center
- **yCenter**: y-koordinat för cirkelns mitt punkt
- **RADIUS**: cirkel-radie
- **vinkel**: vinkel för att beräkna cirkelns perimeter punkt i grader
- **punkt**: adressen till GX_POINT-variabeln där den beräknade x, y-koordinaten ska lagras
- **end_alpha**: slut på Alfa värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) toningen skapades
- **GX_PTR_ERROR**: (0X07) ogiltig avsändar punkts adress
- **GX_INVALID_VALUE**: (0X22) ogiltig RADIUS-parameter

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_POINT point;
    UINT status;

        status = gx_utility_circle_point_get(100, 100,
20, 45,
&point);

/* If status is GX_SUCCESS the value of point is the x,y coordinate of a point on the circle perimeter at an angle of 45 degrees, where the circle is centered at (100, 100), has a radius of 20 pixels */

```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_create"></a>gx_utility_gradient_create

Skapa en tonings Pixelmap

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_gradient_create(
    GX_GRADIENT *gradient,
    GX_VALUE width, 
    GX_VALUE height,
    UCHAR type, 
    GX_UBYTE start_alpha, 
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en övertonings-Pixelmap vid körning. En övertonings bild kan användas för att utföra tonings effekter och andra intressanta visuella ändringar.

Den begärda Toningens bredd och höjd får inte vara mindre än 2x2 bild punkter.

GUIX innehåller en lista över skapade övertoningar internt, och den här funktionen söker först i listan över övertoningar för att hitta matchande övertonings-Pixelmap innan du skapar en ny Pixelmap. Samma tonings Pixelmap krävs flera gånger, bara en Pixelmap skapas, och varje övertoning som kräver den här Pixelmap delar den skapade Pixelmap.

Detta API kräver att gx_system_memory_allocator-funktionen definieras för att tillåta minnes tilldelning för körning.

Tonings typ flaggorna är GX_GRADIENT_TYPE_ALPHA och GX_GRADIENT_TYPE_MIRROR. Endast GX_GRADIENT_TYPE_ALPHA typ toningar stöds för närvarande (dvs. den här typen flagga måste anges). Flaggan GX_GRADIENT_TYPE_MORROR är valfri och när den anges instruerar skapande logiken för toning att skapa en toning som ändras från start_alpha till end_alpha och tillbaka till start_alpha. Annars skapas en linjär övertoning.

### <a name="parameters"></a>Parametrar

- **toning**: pekare till tonings kontroll block struktur
- **Bredd**: begärd Pixelmap bredd
- **höjd**: begärd Pixelmap-höjd
- **typ**: begärd tonings typ
- **start_alpha**: startar alpha-värde
- **end_alpha**: slut på Alfa värde

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) toningen skapades
- **GX_INVALID_SIZE**: (0X19) toningen är inte minst 2x2 bild punkter
- **GX_NOT_SUPPORTED**: (0X28) toningen är inte av typen GX_GRADIENT_TYPE_ALPHA
- **GX_FAILURE**: (0x10) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) tonings pekare är inte giltig<
- **GX_INVALID_VALUE**: (0X22) bredd och höjd-värdet är inte giltigt
- **GX_INVALID_TYPE**: (0X1B) tonings typen är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_GRADIENT gradient;

UINT status;

status = gx_utiity_gradient_create(&gradient, 3, 40,
    GX_GRADIENT_TYPE_ALPHA, 240, 0);

/* If status == GX_SUCCESS the gradient pixelmap has been created */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_delete"></a>gx_utility_gradient_delete

Ta bort en tidigare skapad toning

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_gradient_delete(GX_GRADIENT *gradient);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad övertoning. Om Pixelmap som är associerade med den här övertoningen inte används av några andra övertoningar, tas även Pixelmap-data bort.

### <a name="parameters"></a>Parametrar

- **toning**: pekare mot tonings kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) toningen togs bort
- **GX_CALLER_ERROR**: (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0X07) tonings pekaren är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_GRADIENT gradient;

UINT status;

/* Delete previously created gradient. */
status = gx_utility_gradient_delete(&gradient);

/* If status == GX_SUCCESS, the gradient has been deleted. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_ltoa"></a>gx_utility_ltoa

Konvertera långt heltal till ASCII

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_itoa(
    LONG value, 
    GX_CHAR *return_buffer,
    UINT seturn_buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konverterar ett långt heltals värde till en ASCII-sträng.

### <a name="parameters"></a>Parametrar

- **värde**: det långa heltal svärdet som ska konverteras
- **return_buffer**: MÅLCACHEN för ASCII-sträng
- **return_buffer_size**: storleken på måldomänkontrollanten

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har konverterat heltals värde till sträng
- **GX_PTR_ERROR**: (0X07) ogiltig pekare för returnerad buffert
- **GX_INVALID_SIZE**: (0X19) ogiltig storlek på retursekvens

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
INT my_value = 200;

GX_CHAR string_buffer[10];

UINT status;

/* Convert “my_value” into an ASCII string. */
status = gx_utility_ltoa(my_value, string_buffer, 10);

/* If status is GX_SUCCESS, “string_buffer” contains the ASCII
representation of “my_value”. */
```

### <a name="see-also"></a>Se även

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_acos"></a>gx_utility_math_acos

Beräkna arcus cosinus

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_math_acos(GX_FIXED_VAL x);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar vinkel värdet för arcus cosinus x.

Indatavärdet är en data typ med fast punkt, anropa GX_FIXED_VAL_MAKE för att konvertera från INT till GX_FIXED_VAL typ. Om du till exempel vill beräkna Arc-cosinus för 0,5, gör du inmatad som GX_FIXED_VAL_MAKE (1)/2.

I 5.4.0 eller lägre version GUIX är indatatypen för den här funktionen INT och värdet är begränsat till intervallet [-256, 256]. Programmet måste skala värdet från intervallet [-1, 1] till intervallet [-256, 256] innan du anropar den här tjänsten. Om ditt projekt med GUIX version är lika med eller lägre än 5.4.0 har en referens till detta API och du vill uppgradera projektet till det senaste GUIX-biblioteket. Du har två alternativ.

1. Korrigera indatavärdet för det här API-anropet för att använda GX_FIXED_VAL data typ värde.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **x**: värdet vars Arc-cosinus beräknas

### <a name="return-values"></a>Retur värden

- **vinkel**: vinkel värde för arcus cosinus x

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
/* Compute the angle value of arc cosine of “0.5”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    x = 256 / 2;
#else
    x = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_acos(x);

/* “angle” contains the angle value of arc cosine “x”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_asin"></a>gx_utility_math_asin

Beräkna arcus sinus

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_math_asin(GX_FIXED_VAL x);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar vinkel värdet för arcus sinus x.

Indatavärdet är en data typ med fast punkt, anropa GX_FIXED_VAL_MAKE för att konvertera från INT till GX_FIXED_VAL typ. Om du till exempel vill beräkna bågen sin of 0,5, gör du inmatad som GX_FIXED_VAL_MAKE (1)/2.

I 5.4.0 eller lägre version GUIX är indatatypen för den här funktionen INT och värdet är begränsat till intervallet [-256, 256]. Programmet måste skala värdet från intervallet [-1, 1] till intervallet [-256, 256] innan du anropar den här tjänsten. Om projektet med GUIX version är lika med eller lägre än 5.4.0 och du vill uppgradera projektet till det senaste GUIX-biblioteket. Du har två alternativ.

1. Korrigera indatavärdet för det här API-anropet för att använda GX_FIXED_VAL data typ värde.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **x**: värdet vars Arc-sinus beräknas

### <a name="return-values"></a>Retur värden

- **vinkel**: vinkel värde för arcus sinus x

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
/* Compute the angle value of arc sine of “x”. */

#if defined GUIX_5_4_0_COMPATIBILITY
    x = 256 / 2;
#else
    X = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_asin(x);

/* “angle” contains the angle value of arc sine “x”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_cos"></a>gx_utility_math_cos

Beräknings-cosinus

### <a name="prototype"></a>Prototyp

```C
GX_FIXED_VAL gx_utility_math_cos(GX_FIXED_VAL angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar cosinus för den angivna vinkeln.

Indatavärdet är en data typ med fast punkt, anropa GX_FIXED_VAL_MAKE för att konvertera från INT till GX_FIXED_VAL. Om du till exempel vill beräkna cosinus för 90 grad, gör du inmatad som GX_FIXED_VAL_MAKE (90).

Returvärdet är en data typ med fast punkt, anropa GX_FIXED_VAL_TO_INT för att konvertera från GX_FIXED_VAL till INT.

I 5.4.0 eller lägre version av GUIX-versionen är indatavärdet och returvärdet för den här tjänsten INT, indatavärdet och returvärdet för storas med 256. Programmet måste därför skala vinkel värdet med 256 innan du anropar den här tjänsten. Om projektet med GUIX version är lika med eller lägre än 5.4.0 och du vill uppgradera projektet till det senaste GUIX-biblioteket, har du två alternativ.

1. Korrigera indatavärdet och hanteringen till returvärdet för det här API-anropet för att använda GX_FIXED_VAL värde för datum typ.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **vinkel**: vinkel till beräkning av cosinus av

### <a name="return-values"></a>Retur värden

- **cosinus**: cosinus för den angivna vinkeln

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
/* Compute cosine of 90 degree. */

INT angle = 90;

#if defined (GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = angle << 8;
#else
    GX_FIXED_VAL scaled_angle = GX_FIXED_VAL_MAKE(angle);
#endif

my_angle_cosine = gx_utility_math_cos(scaled_angle);

/* “my_angle_cosine” contains the cosine of “my_angle”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_asin
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sin"></a>gx_utility_math_sin

Compute-sinus

### <a name="prototype"></a>Prototyp

```C
GX_FIXED_VAL gx_utility_math_sin(GX_FIXED_VAL angle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar sinus för den angivna vinkeln.

Indatavärdet är en data typ med fast punkt, anropa GX_FIXED_VAL_MAKE för att konvertera från INT till GX_FIXED_VAL. Om du till exempel vill beräkna sinus för 90 grad, gör du inmatad som GX_FIXED_VAL_MAKE (90). 

Returvärdet är en data typ med fast punkt, anropa GX_FIXED_VAL_TO_INT för att konvertera från GX_FIXED_VAL till INT.

I 5.4.0 eller lägre version GUIX är indatavärdet och retur värdes typen INT, och indatavärdet och returvärdet för storas med 256. Programmet måste därför skala vinkel värdet med 256 innan du anropar den här tjänsten. Om projektet med GUIX version är lika med eller lägre än 5.4.0 och du vill uppgradera projektet till det senaste GUIX-biblioteket, har du två alternativ.

1. Korrigera indatavärdet och lämna värdet till returvärdet för det här API-anropet för att använda GX_FIXED_VAL data typs värde.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **vinkel**: vinkel för att beräkna sinus av

### <a name="return-values"></a>Retur värden

- **sinus**: sinus för den angivna vinkeln

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
INT my_angle = 80;

/* Compute sine of “my_angle”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = my_angle << 8;
#else
    GX_FIXED_VAL = GX_FIXED_VAL_MAKE(my_angle);
#endif

my_angle_sine = gx_utility_math_sin(scaled_angle);

/* “my_angle_sine” contains the sine of “my_angle”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_asin
- gx_utility_math_cos
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sqrt"></a>gx_utility_math_sqrt

Compute, kvadratrot

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_math_sqrt(UINT value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar kvadratroten av det angivna värdet.

### <a name="parameters"></a>Parametrar

- **värde**: värde för att beräkna kvadratroten ur

### <a name="return-values"></a>Retur värden

- **kvadratrot**: kvadratroten för angivet värde

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
/* Compute square root of “my_value”. */
my_square_root = gx_utility_math_sqrt(my_value);

/* “my_square_root” contains the square root of “my_value”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_bidi_paragraph_reorder"></a>gx_utility_bidi_paragraph_reorder

Ändra ordning på dubbelriktad text till visnings ordningen

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_bidi_paragraph_reorder(GX_BIDI_TEXT_INFO *input_info, 
                                       GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Beskrivning

Den här tjänsten ordnar om dubbelriktad text i visnings ordningen. Om text ritnings teckensnittet och visnings bredden anges, används rad brytning först, och sorterings processen tillämpas baserat på varje rad. Om den tillhandahållna texten innehåller mer än ett stycke kommer tjänsten att dela upp texten i stycken, och rad brytningen och omordnings resultatet för varje stycke länkas som en lista.

### <a name="parameters"></a>Parametrar

- **input_info**: pekar mot information för rad brytning och text sortering
- **resolved_info_head**: pekar mot den länkade listan som innehåller rad brytningar och ordnar om resultatet av varje stycke i den angivna texten

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad dubbelriktad text ändra ordning
- **GX_PTR_ERROR**: (0X07) ogiltiga inmatade pekare
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel
#### <a name="draw-single-line-bidi-text-to-canvas"></a>Rita enkel linje dubbelriktad text till arbets ytan
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```
#### <a name="draw-multi-line-bidi-text-to-canvas"></a>Rita multi line dubbelriktad text till arbets ytan
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Multi Line BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        /* Draw reordered bidi text to canvas. */
        for(index = 0; index < resolved_info.gx_bidi_resolved_text_info_total_lines; index++)
        {
            gx_canvas_text_draw_ext(xpos, ypos, &resolved_info.gx_bidi_resolved_text_info_text[index]);
        
            ypos += font->gx_font_line_height;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

#### <a name="draw-multi-paragraph-bidi-text-to-canvas"></a>Rita multi-stycken dubbelriktad text till arbets ytan
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_BIDI_RESOLVED_TEXT_INFO *next;
    GX_CHAR bidi_text[] = "Multi Paragraph\r BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        next = resolved_info;
        
        /* Draw reordered bidi text to canvas. */
        while(next)
        {
            for(index = 0; index < next.gx_bidi_resolved_text_info_total_lines; index++)
            {
                gx_canvas_text_draw_ext(xpos, ypos, &next.gx_bidi_resolved_text_info_text[index]);
            
                ypos += font->gx_font_line_height;
            }
            
            next = next->gx_bidi_resolved_text_info_next;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>Se även

- gx_utility_bidi_resolved_text_info_delete

## <a name="gx_utility_bidi_resolved_text_info_delete"></a>gx_utility_bidi_resolved_text_info_delete

Ta bort löst dubbelriktad text informations lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_bidi_resolved_text_info_delete(GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den lösta informations listan som returnerades av gx_utility_bidi_paragraph_reorder.

### <a name="parameters"></a>Parametrar

- **resolved_info_head**: pekar mot listan löst dubbelriktad text information

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad åtgärd för att ta bort text
- **GX_PTR_ERROR**: (0X07) ogiltiga inmatade pekare
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>Se även

- gx_utility_bidi_paragraph_reorder

## <a name="gx_utility_pixelmap_resize"></a>gx_utility_pixelmap_resize

Ändra storlek på Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_pixelmap_resize(
    GX_PIXELMAP *src,
    GX_PIXELMAP *destination, 
    INT width, 
    INT height);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar storlek på en Pixelmap och returnerar en pekare till en ny Pixelmap, vilket är resultatet av storleken på Pixelmap.

Den här tjänsten kräver den tidigare användningen av gx_system_memory_allocator_set, för att tillåta allokering av minne för att lagra de ändrade storlekarna på Pixelmap data.

### <a name="parameters"></a>Parametrar

- **src**: pekare till Pixelmap för att ändra storlek
- **mål**: måldomänkontrollanten för den resulterande Pixelmap
- **width**: bredden på den resulterande Pixelmap i bild punkter
- **height**: hieght för den resulterande Pixelmap i bild punkter

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) Pixelmap ändra storlek
- **GX_PTR_ERROR**: (0X07) ogiltigt käll-eller mål Pixelmap-pekare
- **GX_INVALID_VALUE**: (0X22) bredd eller höjd-värde är ogiltigt
- **GX_NOT_SUPPORTED**: (0X28) Källa Pixelmap är komprimerat format
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
GX_PIXLEMAP *des_pixelmap;

/* Resize “src_pixelmap” with specifiy width and height. */
status = gx_utility_pixelmap_resize(src_pixelmap,
    &des_pixelmap, 100, 200);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of resize. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_rotate"></a>gx_utility_pixelmap_rotate

Rotera Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_pixelmap_rotate(
    GX_PIXELMAP *src, INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx, 
    UINT *rot_cy);
```

### <a name="description"></a>Beskrivning

Den här tjänsten roterar en Pixelmap och returnerar en pekare till en ny Pixelmap, vilket är resultatet av Pixelmap-rotationen. Använd gx_canvas_pixelmap_rotate () om du vill rotera en Pixelmap direkt till arbets ytan.

Den här tjänsten kräver att gx_system_memory_allocator_set används tidigare för att tillåta allokering av minne för att lagra de roterade Pixelmap-data.

### <a name="parameters"></a>Parametrar

- **src**: den Pixelmap som ska roteras
- **vinkel**: rotations vinkel i grader
- **mål**: måldomänkontrollanten för den resulterande Pixelmap
- **rot_cx**: x-koordinaten för rotations Center har hämtats med avseende på mål Pixelmap. Bör initieras med x-koordinaten för rotations Center med avseende på Source Pixelmap. Om rot_cx är GX_NULL kommer värdet inte att hämtas.
- **rot_cy**: y-koordinaten för rotations centrum har hämtats med avseende på mål Pixelmap. Bör initieras med y-koordinaten för rotations centrum med avseende på käll Pixelmap. Om rot_cy är GX_NULL kommer värdet inte att hämtas.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad Pixelmap rotation
- **GX_PTR_ERROR**: (0X07) ogiltigt käll-eller mål Pixelmap-pekare
- **GX_INVALID_VALUE**: (0X22) vinkel värde är 0
- **GX_INVALID_FORMAT**: (0x28) Pixelmap är komprimerat format, vilket inte stöds
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 30 degree in clockwise direction. */
status = gx_utility_pixelmap_rotate(src_pixelmap, 30,
    &des_pixelmap, &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_simple_rotate"></a>gx_utility_pixelmap_simple_rotate

Rotera Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_pixelmap_simple_rotate(
    GX_PIXELMAP *src,
    INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx,
    UINT *rot_cy);
```

### <a name="description"></a>Beskrivning

Den här tjänsten roterar en Pixelmap med 90 grad, 180 grad eller 270-grad.

### <a name="parameters"></a>Parametrar

- **src**: den Pixelmap som ska roteras
- **vinkel**: rotations vinkel i grader
- **mål**: måldomänkontrollanten för den resulterande Pixelmap
- **rot_cx**: x-koordinaten för rotations Center har hämtats med avseende på mål Pixelmap. Bör initieras med x-koordinaten för rotations Center med avseende på Source Pixelmap. Om rot_cx är GX_NULL kommer värdet inte att hämtas.
**rot_cy**: y-koordinaten för rotations centrum har hämtats med avseende på mål Pixelmap. Bör initieras med y-koordinaten för rotations centrum med avseende på käll Pixelmap. Om rot_cy är GX_NULL kommer värdet inte att hämtas.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) lyckad Pixelmap rotation
- **GX_PTR_ERROR**: (0X07) ogiltigt käll-eller mål Pixelmap-pekare
- **GX_INVALID_VALUE**: (0X22) vinkel värde är 0 eller inte en enkel vinkel som 90, 180, 270
- **GX_INVALID_FORMAT**: (0x28) Pixelmap är komprimerat format, vilket inte stöds
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 90 degree in clockwise direction. */
status = gx_utility_pixelmap_simple_rotate(src_pixelmap, 90,
    &des_pixelmap,
    &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center"></a>gx_utility_rectangle_center

Centrera rektangeln i en annan rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_center(
    GX_RECTANGLE *rectangle,
    GX_RECTANGLE *within_rectangle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten centrerar rektangeln i en annan rektangel.

### <a name="parameters"></a>Parametrar

- **rektangel**: rektangel till mitten
- **within_rectangle**: rektangel som ska centreras i

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) centrerade rektangeln
- **GX_PTR_ERROR**: (0X07) ogiltig pekare för indatakälla
- **GX_INVALID_SIZE**: (0X19) ogiltig Rectangle-storlek

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
UINT status;

/* Center “my_inner_rectangle” inside of “my_outer_rectangle”.*/
status = gx_utility_rectangle_center(&my_inner_rectangle,
    &my_outer_rectangle);

/* Is status is GX_SUCCESS, “my_inner_rectangle” is centered
within “my_other_rectangle”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center_find"></a>gx_utility_rectangle_center_find

Hitta mitten av rektangeln

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_center_find(
    GX_RECTANGLE *rectangle,
    GX_POINT *return_center);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hittar rektangelns centrum.

### <a name="parameters"></a>Parametrar

- **rektangel**: rektangel
- **return_center**: pekar mot mitt punkt

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har hittat mitten av rektangeln
- **GX_PTR_ERROR**: (0X07) ogiltig inmatare
- **GX_INVALID_SIZE**: (0X19) ogiltig Rectangle-storlek

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status;

GX_RECTANGLE my_rectangle;

GX_POINT my_center_point;

gx_utility_define(&my_rectangle, 0, 0, 100, 100);

/* Find center of “my_rectangle””. */

status = gx_utility_rectangle_center_find(&my_rectangle,
    &my_center_point);

/* If status is GX_SUCCESS, “my_center_point” is the center point
of “my_rectangle” (50, 50). */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_combine"></a>gx_utility_rectangle_combine

Kombinera två rektanglar till första

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_combine(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kombinerar den första och andra rektangeln till den första rektangeln. Den första rektangeln expanderas för att inkludera den andra.

### <a name="parameters"></a>Parametrar

- **first_rectangle**: första rektangeln och kombinerad rektangel
- **second_rectangle**: andra rektangeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har kombinerat två rektanglar
- **GX_PTR_ERROR**: (0X07) ogiltig inmatare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT status;

GX_RECTANGLE rect_a;

GX_RECTANGLE rect_b;

gx_utility_rectangle_define(&rect_a, 0, 0, 100, 100);
gx_utility_rectangle_define(&rect_b, 50, 50, 200, 200);

/* Combine “my_rectangle_a” to “my_rectangle_b”. */
status = gx_utility_rectangle_combine(&rect_a, &rect_b);

/* If status is GX_SUCCESS, “rect_a” is (0, 0, 200, 200) the merger
of the original “rect_a” and “rect_b”. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_compare"></a>gx_utility_rectangle_compare

Jämför två rektanglar

### <a name="prototype"></a>Prototyp

```C
GX_BOOL gx_utility_rectangle_compare( 
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Beskrivning

Den här tjänsten jämför den första och andra rektangeln. Om de är lika returneras ett värde för GX_TRUE.

### <a name="parameters"></a>Parametrar

- **first_rectangle**: första rektangeln
- **second_rectangle**: andra rektangeln

### <a name="return-values"></a>Retur värden

- **resultat**: GX_TRUE om rektanglar är identiska, annars returneras GX_FALSE.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Compare “my_rectangle_a” to “my_rectangle_b”. */
result = gx_utility_rectangle_compare(&my_rectangle_a,
    &my_rectangle_b);

/* If result is GX_TRUE, the two rectangles are equal. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_define"></a>gx_utility_rectangle_define

Definiera en rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_define(
    GX_RECTANGLE *rectangle,
    GX_VALUE left,
    GX_VALUE top, 
    GX_VALUE right, 
    GX_VALUE bottom);
```

### <a name="description"></a>Beskrivning

Den här tjänsten definierar en rektangel som anges.

### <a name="parameters"></a>Parametrar

- **rektangel**: kontroll block-rektangel
- **vänster**: den mest vänstra koordinaten
- **överkant**: mest översta koordinaten
- **höger**: den bästa koordinaten
- **nederkant**: flest koordinater

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har definierat en rektangel
- **GX_PTR_ERROR**: (0X07) ogiltig Rectangle-pekare

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
UINT status;

GX_RECTANGLE my_rect;

/* Define “my_rect”. */

status = gx_utility_rectangle_define(&my_rect, 10, 5, 200, 100);

/* If status is GX_SUCCESS, “my_rect” is defined. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_overlap_detect"></a>gx_utility_rectangle_overlap_detect

Identifiera överlappande av rektanglar

### <a name="prototype"></a>Prototyp

```C
GX_BOOL gx_utility_rectangle_overlap_detect(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle,
    GX_RECTANGLE *return_overlap_area);
```

### <a name="description"></a>Beskrivning

Den här tjänsten identifierar överlappande av de angivna rektanglarna. Om överlappande hittas returnerar tjänsten GX_TRUE och den överlappande rektangeln.

### <a name="parameters"></a>Parametrar

- **first_rectangle**: första rektangeln
- **second_rectangle**: andra rektangeln
- **return_overlap_area**: överlappande Rectangle-område

### <a name="return-values"></a>Retur värden

- **resultat**: GX_TRUE om rektanglar överlappar, annars GX_FALSE.

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
/* Detect overlap of “my_rectangle_a” and “my_rectangle_b”. */
result = gx_utility_rectangle_overlap_detect(&my_rectangle_a,
    &my_rectangle_b,
    &my_overlap_area);

/* If result is GX_TRUE, “my_overlap_area” specifies the area the
rectangles overlap. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_point_detect"></a>gx_utility_rectangle_point_detect

Identifiera om punkten finns i rektangeln

### <a name="prototype"></a>Prototyp

```C
GX_BOOL gx_utility_rectangle_point_detect(
    GX_RECTANGLE *rectangle,
    GX_POINT point);
```

### <a name="description"></a>Beskrivning

Den här tjänsten identifierar om den angivna punkten finns i rektangeln. Om punkten finns i rektangeln returnerar tjänsten GX_TRUE.

### <a name="parameters"></a>Parametrar

- **rektangel**: rektangel
- **punkt**: punkt

### <a name="return-values"></a>Retur värden

- **resultat**: GX_TRUE om punkten finns i rektangeln, annars GX_FALSE

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```c
GX_RECTANGLE my_rectangle;

GX_POINT my_point;

gx_utility_rectangle_define(&my_rectangle, 0, 0, 100, 100);

my_point.gx_point_x = 20; my_point.gx_point_y = 20;

/* Detect if point “my_point” is within “my_rectangle””. */
result = gx_utility_rectangle_point_detect(&my_rectangle,
    &my_point);

/* If result is GX_TRUE, “my_point” resides in the rectangle. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_resize"></a>gx_utility_rectangle_resize

Utöka rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_resize(
    GX_RECTANGLE *rectangle,
    GX_VALUE adjust);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ökar storleken på rektangeln enligt vad som anges.

### <a name="parameters"></a>Parametrar

- **rektangel**: pekare till rektangel
- **Justera**: belopp för att justera rektangeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) ändrade storlek på rektangeln
- **GX_PTR_ERROR**: (0X07) ogiltig pekare för indatakälla

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
UINT status;

/* Adjust “my_rectangle” by increasing 20 pixels on four sides */
status = gx_utility_rectangle_resize(&my_rectangle, 20);

/* If status is GX_SUCCESS, “my_rectangle” is 20 pixels larger. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_shift"></a>gx_utility_rectangle_shift

Shift-rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_shift(
    GX_RECTANGLE *rectangle,
    GX_VALUE x_shift,
    GX_VALUE y_shift);
```

### <a name="description"></a>Beskrivning

Den här tjänsten byter till rektangeln med de angivna värdena.

### <a name="parameters"></a>Parametrar

- **rektangel**: rektangel till Skift
- **x_shif**: antalet pixlar som ska flyttas till x-axeln
- **y_shift**: antal pixlar som ska flyttas på y-axeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0X00) har växlat till rektangeln
- **GX_PTR_ERROR**: (0X07) ogiltig pekare för indatakälla

### <a name="allowed-from"></a>Tillåten från

Alla

### <a name="example"></a>Exempel

```C
UINT status;

/* Shift “my_rectangle”. */

status = gx_utility_rectangle_shift(&my_rectangle, 10, 20);

/* If status is GX_SUCCESS, “my_rectangle” has been shifted. */
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_utility_string_to_alphamap"></a>gx_utility_string_to_alphamap

Rendera strängen till en 8bpp AlphaMap-typ Pixelmap (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_string_to_alphamap(
    const GX_CHAR *text, const
    GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Beskrivning

Den här tjänsten har ersatts av gx_utility_string_to_alphamap_ext ().

Den här tjänsten återger en text sträng till en AlphaMap, vilket är en särskild form av 8bpp-Pixelmap som bara innehåller alpha-värden. Den här tjänsten används vanligt vis tillsammans med gx_utility_pixelmap_rotate och gx_canvas_pixelmap_draw för att rita roterad text till arbets ytan.

Den här tjänsten beräknar den minnes storlek som krävs för den resulterande AlphaMap och anropar funktionen gx_system_memory_allocator () som definieras av programmet för att dynamiskt allokera minne. Programmet måste anropa gx_system_memory_allocator_set () vid en viss tidpunkt, vanligt vis när programmet startas, innan du använder den här tjänsten.

Om en text sträng ska roteras och ritas till arbets ytan bara en gång, anges tjänsten gx_canvas_rotated_text_draw () som ett alternativ. gx_canvas_rotated_text_draw () anropar gx_utility_string_to_alphamap (), gx_utility_pixelmap_rotate () och gx_canvas_pixelmap_draw () för att återge roterad text i en åtgärd. Men om samma text kommer att ritas flera gånger i olika vinklar, är det mer effektivt att skapa AlphaMap en gång med hjälp av gx_utility_string_to_alphmap API, och sedan rotera den resulterande AlphaMap flera gånger efter behov.

### <a name="parameters"></a>Parametrar

- **text**: text sträng att rendera till AlphaMap
- **teckensnitt**: det teckensnitt som ska återges texten
- **return_map**: pekar på den GX_PIXELMAP som ska returneras till anroparen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) en text sträng har Render ATS till en AlphaMap
- **GX_PTR_ERROR**: (0X07) ogiltig inmatare
- **GX_SYSTEM_MEMORY_ERROR**: (0X30) minnes tilldelning/kostnads fri funktion har inte definierats
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

/* render string to alphamap once */

gx_utility_string_to_alphamap("Hello World", font, &alphamap);

/* rotate and render the alphmap at multiple angles */

gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>Se även

- gx_utility_string_to_alphamap_ext

## <a name="gx_utility_string_to_alphamap_ext"></a>gx_utility_string_to_alphamap_ext

Rendera strängen till en 8bpp AlphaMap-typ Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_string_to_alphamap_ext(
    GX_CONST GX_STRING *string,
    GX_CONST GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återger en text sträng till en AlphaMap, vilket är en särskild form av 8bpp-Pixelmap som bara innehåller alpha-värden. Den här tjänsten används vanligt vis tillsammans med gx_utility_pixelmap_rotate och gx_canvas_pixelmap_draw för att rita roterad text till arbets ytan.

Den här tjänsten beräknar den minnes storlek som krävs för den resulterande AlphaMap och anropar funktionen gx_system_memory_allocator () som definieras av programmet för att dynamiskt allokera minne. Programmet måste anropa gx_system_memory_allocator_set () vid en viss tidpunkt, vanligt vis när programmet startas, innan du använder den här tjänsten.

Om en text sträng ska roteras och ritas till arbets ytan bara en gång, anges tjänsten gx_canvas_rotated_text_draw () som ett alternativ. gx_canvas_rotated_text_draw () anropar gx_utility_string_to_alphamap (), gx_utility_pixelmap_rotate () och gx_canvas_pixelmap_draw () för att återge roterad text i en åtgärd. Men om samma text kommer att ritas flera gånger i olika vinklar, är det mer effektivt att skapa AlphaMap en gång med hjälp av gx_utility_string_to_alphmap API, och sedan rotera den resulterande AlphaMap flera gånger efter behov.

### <a name="parameters"></a>Parametrar

- **sträng**: text sträng att rendera till AlphaMap
- **teckensnitt**: det teckensnitt som ska återges texten
- **return_map**: pekar på den GX_PIXELMAP som ska returneras till anroparen.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS**: (0x00) en text sträng har Render ATS till en AlphaMap
- **GX_PTR_ERROR**: (0X07) ogiltig inmatare
- **GX_SYSTEM_MEMORY_ERROR**: (0X30) minnes tilldelning/kostnads fri funktion har inte definierats
- **GX_INVALID_STRING_LENGTH**: (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING string;

GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

string.gx_string_ptr = “Hello World”;

string.gx_string_length = strlen(string.gx_string_ptr);

/* render string to alphamap once */
gx_utility_string_to_alphamap_ext(&string, font, &alphamap);

/* rotate and render the alphmap at multiple angles */
gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>Se även

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_vertical_list_children_position"></a>gx_vertical_list_children_position
### <a name="position-children-for-the-vertical-list"></a>Placera underordnade i den lodräta listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_children_position(
    GX_VERTICAL_LIST *vertical_list)
```

### <a name="description"></a>Beskrivning

Den här funktionen placerar underordnade objekt i den lodräta listan.

### <a name="parameters"></a>Parametrar

- **vertical_list** Pekare till kontroll blocket lodrät lista

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) placerade underordnade för den lodräta listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Position children in the vertical list */
status = gx_vertical_list_children_position (&vertical_list);

/* If status is GX_SUCCESS the children in the vertical list are positioned.. */
```

### <a name="see-also"></a>Se även

- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selecgted_widget_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_create"></a>gx_vertical_list_create
### <a name="create-vertical-list"></a>Skapa lodrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_create(
    GX_VERTICAL_LIST *vertical_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    VOID (*callback)(GX_VERTICAL_LIST *, GX_WIDGET *, INT),
    ULONG style, USHORT vertical_list_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en lodrät lista.

GX_VERTICAL_LIST härleds från GX_WINDOW och stöder alla gx_window API-tjänster.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontroll block för widgeten lodrät lista
- **namn** Namn på lodrät lista
- **överordnad** Pekare till överordnad widget
- **total_rows** Totalt antal rader i lodrät lista
- **motringning** En funktion som kommer att anropas av den lodräta listan när listan rullas. Anroparen måste börja med att skapa tillräckligt med GX_WIDGET underordnade underordnade för att fylla de synliga List raderna. När listan är rullad anropas den här funktionen för att återskapa de List objekt som motsvarar det angivna List indexet
- **stil** Typ av widget för rullnings List. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **vertical_list_id** Programdefinierat ID för lodrät lista
- **storlek** Lodrät listans dimensioner

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) skapade den lodräta listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- **GX_INVALID_VALUE** (0x22) ogiltigt antal rader
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create vertical list “my_list” with 20 rows. */
status = gx_vertical_list_create(&my_list, “my_list”, &my_parent,
                    20, callback, GX_STYLE_WRAP, MY_LIST_ID,
                    &size);

/* If status is GX_SUCCESS the vertical list “my_list” has been created. */
```

### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_event_process"></a>gx_vertical_list_event_process
### <a name="process-vertical-list-event"></a>Bearbeta lodrät lista-händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_event_process(GX_VERTICAL_LIST *list,
                                                      GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse i den lodräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontroll block för widgeten lodrät lista
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bearbetade händelsen lodrät lista
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Process “my_event” for vertical list “my_list”. */
status = gx_vertical_list_event_process(&my_list, &my_event);

/* If status is GX_SUCCESS the event for vertical list “my_list” has been processed. */
```

### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_selected_set

## <a name="gx_vertical_list_page_index_set"></a>gx_vertical_list_page_index_set
### <a name="set-starting-page-index"></a>Ange start sid index

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_page_index_set(
    GX_VERTICAL_LIST *list,
    INT index);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger start indexet för den lodräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontroll block för widgeten lodrät lista
- **index** Det nya översta indexet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett start index för den lodräta listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_VALUE** (0X22) ogiltigt index värde
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the starting page index of vertical list “my_list” to 4. */
status = gx_vertical_list_page_index_set(&my_list, 4);

/* If status is GX_SUCCESS the starting page index of “my_list” has
been set to 4. */
```
### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_index_get"></a>gx_vertical_list_selected_index_get
### <a name="get-selected-index-from-vertical-list"></a>Hämta markerat index från lodrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_selected_index_get(
    GX_VERTICAL_LIST *vertical_list,
    INT *return_index);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar det valda indexet för den lodräta listan

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontroll block för widgeten lodrät lista
- **return_index** Mål för returnerat markerat index

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämta den lodräta List posten
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
INT current_selected_index;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_index_get(&my_list, &current_selected_index);

/* If status is GX_SUCCESS, “current_list_index” contains the index of the selected list item. */
```
### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_set"></a>gx_vertical_list_selected_set
### <a name="assign-the-selected-entry-in-a-vertical-list"></a>Tilldela den markerade posten i en lodrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_selected_set(
    GX_VERTICAL_LIST *vertical_list,
    INT index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar den valda posten en lodrät lista. Om det behövs bläddrar den lodräta listan för att göra den markerade posten synlig.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontroll block för widgeten lodrät lista
- **index** Indexerad position för ny List post

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett den lodräta List posten
- **GX_FAILURE** (0x10) indatamängds index hittades inte i listan
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0X12) lodrät lista eller ogiltig widget för List post

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_vertical_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```
### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_get
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_widget_get"></a>gx_vertical_list_selected_widget_get
### <a name="get-selected-widget-from-vertical-list"></a>Hämta vald widget från lodrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_selected_widget_get(
    GX_VERTICAL_LIST *vertical_list,
    GX_WIDGET **return_list_entry);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar den markerade widgeten för den lodräta listan. Observera att om listan innehåller fler rader än underordnade widgetar och den valda underordnade widgeten har rullats från vyn, returnerar den här funktionen GX_NULL som GX_WIDGET visare, eftersom widgeten har återanvänts för att visa en ny post i listan.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontroll block för widgeten lodrät lista
- **return_list_entry** Mål för widgeten Return List post

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämta den lodräta List posten
- **GX_FAILURE** (0X10) den valda widgeten har rullats från vyn.
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_WIDGET *current_selected_widget;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_widget_get(&my_list, &current_selected_widget);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */
```

### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_total_rows_set"></a>gx_vertical_list_total_rows_set
### <a name="set-total-number-of-vertical-list-rows"></a>Ange det totala antalet lodräta List rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_total_rows_set(
    GX_VERTICAL_LIST *vertical_list,
    INT count);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar eller ändrar det totala antalet List rader.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontroll block för widgeten lodrät lista
- **antal** Nytt antal List rader

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett rad antalet för lodrät lista
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) radantal är inte giltigt

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set the list row count to 20 items. */
status = gx_vertical_list_total_rows_set(&my_list, 20);

/* If status is GX_SUCCESS, the total rows of “my_list” has been set to 20. */
```
### <a name="see-also"></a>Se även

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set

## <a name="gx_vertical_scrollbar_create"></a>gx_vertical_scrollbar_create
### <a name="create-vertical-scrollbar"></a>Skapa lodrät rullnings List

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance,
    ULONG style);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en lodrät rullnings List.

### <a name="parameters"></a>Parametrar

- **rullnings List** Kontroll block för rullnings List
- **namn** Namn på rullnings List
- **överordnad** Pekare till överordnad widget
- **utseende** Utseende på widgeten lodrät rullnings List.
- **stil** Rullnings listens format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) vågrät rullnings List har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create vertical scrollbar “my_scrollbar”. */
status = gx_vertical_scrollbar_create(&my_scrollbar,
                          “my_vertical_scrollbar”,
                          &my_parent, &scrollbar_appearance,
                          GX_STYLE_ENABLED);

/* If status is GX_SUCCESS the vertical scrollbar “my_scrollbar” has been created. */
```
### <a name="see-also"></a>Se även

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset

## <a name="gx_widget_allocate"></a>gx_widget_allocate
### <a name="allocate-a-widget-control-block"></a>Allokera ett kontroll block för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_allocate(
    GX_WIDGET **control_block,
    ULONG memsize);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar dynamiskt ett widgets kontroll block genom att anropa funktionen programdefinierad minnesallokering. Den här tjänsten används främst av de funktioner som genereras av GUIX Studio för att dynamiskt allokera kontroll block när egenskapen "dynamisk allokering" är markerad i vyn GUIX Studio-egenskaper.

### <a name="parameters"></a>Parametrar

- **control_block** Pekare som visar pekare för kontroll block
- **memsize** Kontroll block storlek, i byte

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) allokering av slutförd widget
- **GX_SYSTEM_MEMORY_ERROR** (0x30) allokerat minne har inte definierats eller så misslyckades minnes tilldelningen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_MEMORY_SIZE** (0X29) minnes storleken är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_TEXT_BUTTON *button;

/* Attach “my_widget” to “my_parent”. */
status = gx_widget_allocate(&button, sizeof(GX_TEXT_BUTTON));

/* If status is GX_SUCCESS the button widget control block is allocated. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_attach"></a>gx_widget_attach
### <a name="attach-widget-to-its-parent"></a>Bifoga widgeten till dess överordnade

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Beskrivning

Den här tjänsten kopplar widgeten till den angivna överordnade. Om widgeten redan är kopplad till en annan överordnad, kopplas den först från. Om widgeten redan är kopplad till samma överordnade funktion händer ingenting.

Widgeten blir den översta underordnade för dess överordnade objekt i form av z-ordning. Om widgeten på samma nivå överlappar, ritas denna widget ovanpå objekt på samma nivå. Använd gx_widget_back_attach eller gx_widget_back_move för att ställa in den nya widgeten på bak sidan av z-ordningen.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget** Widgeten pekare till underordnad

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00)-slutförd widget-koppling
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) överordnad eller widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_background_draw"></a>gx_widget_background_draw
### <a name="draw-a-widget-background"></a>Rita en bakgrund för widget

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_background_draw(GX_WIDGET *widget);
```
### <a name="description"></a>Beskrivning

Den här tjänsten utför en solid färg fyllning för en widgets bakgrund. Den här tjänsten anropas automatiskt av gx_widget_draw-funktionen, men kan också anropas av programmet som en del av en anpassad widgets ritnings funktion.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget som ska ritas

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
    /* Call default widget background draw. */
    gx_widget_background_draw(widget);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_attach"></a>gx_widget_back_attach
### <a name="attach-widget-to-its-parent"></a>Bifoga widgeten till dess överordnade

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_back_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Beskrivning

Den här tjänsten kopplar widgeten till den angivna överordnade. Om widgeten redan är kopplad till en annan överordnad, kopplas den först från. Om widgeten redan är kopplad till samma överordnade funktion händer ingenting.

Widgeten blir det överordnade objektets överordnade objekt vad gäller z-ordning. Om widgeten på samma nivå överlappar, ritas denna widgeten bakom dessa objekt på samma nivå. Använd gx_widget_attach eller gx_widget_front_move för att lägga den nya widgeten överst i z-ordningen.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget** Widgeten pekare till underordnad

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00)-slutförd widget-koppling
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) överordnad eller widgeten är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_back_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```
### <a name="see-also"></a>Se även

- gx_widget_back_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_move"></a>gx_widget_back_move
### <a name="move-widget-to-back"></a>Flytta widgeten bakåt

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_back_move(
    GX_WIDGET *widget,
    GX_BOOL *return_widget_moved);
```
### <a name="description"></a>Beskrivning

Den här tjänsten flyttar widgeten längst upp i den överordnade objektens Z-ordning efter underordnade widgetar.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **return_widget_moved** Pekare till mål för flagga som anger att widgeten har flyttats

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) en lyckad widget flyttas till bak Sidan
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_NO_CHANGE** (0X08) inga ändringar har tillämpats
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move “my_widget” to the back. */
status = gx_widget_back_move(&my_widget, &moved_flag);

/* If status is GX_SUCCESS and “moved_flag” is GX_TRUE, the widget “my_widget” was moved to the back. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_block_move"></a>gx_widget_block_move
### <a name="move-a-rectangular-block-of-pixels"></a>Flytta ett rektangulärt block med pixlar

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_block_move(
    GX_WIDGET *widget,
    GX_RECTANGLE *block,
    INT xshift, INT yshift);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar ett rektangulärt block av pixlar. Den här tjänsten används oftast för att implementera snabb rullning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare mot widget som begär block flyttning
- **blockera** Rektangulärt avgränsnings block att flytta
- **xshift** X-Shift-mängden i bild punkter
- **yshift** Y-shiftnas storlek i bild punkter

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) en lyckad widget flyttas till bak Sidan
- Det gick inte att hitta **GX_INVALID_CANVAS** (0X20) widgeten
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move a block of pixels 20 pixels to the right. */
status = gx_widget_block_move(&my_widget, &size, 20, 0);

/* If status is GX_SUCCESS the block of pixels was moved. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_draw"></a>gx_widget_border_draw
### <a name="draw-widget-border"></a>Rita widget-kantlinje

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_border_draw(
    GX_WIDGET *widget,
    GX_COLOR border_color,
    GX_COLOR upper_fill, 
    GX_COLOR lower_fill, 
    GX_BOOL fill);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar widgetens kant linje. Den här tjänsten anropas vanligt vis som en del av en widgets ritnings funktion. Den här tjänsten tolkar widgetens kant linje format flaggor för att rita ingen kant linje, en tunn kant linje, en upphöjd kant linje, en försänkt kant linje eller en tjock kant linje.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **border_color** Kant linje färg. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **upper_fill** Färg för den övre fyllningen. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **lower_fill** Färg för nedre fyllning. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.
- **Fyll** Den här booleska flaggan visar om widgetområdet ska fyllas i med angivna fyllnings färger. Om det här värdet är GX_FALSE ritas bara widgetens kant linje.

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
      /* Call widget border draw. */
      gx_widget_border_draw(widget, GX_COLOR_BLACK,
                            GX_COLOR_GREEN, GX_COLOR_BLUE,
                            GX_TRUE);

      /* Add your own drawing here. */

      /* Draw child widgets. */
      Gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_style_set"></a>gx_widget_border_style_set
### <a name="set-widget-border-style"></a>Ange kant linje format för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_border_style_set(
    GX_WIDGET *widget, 
    ULONG style);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger widgetens kant linje format.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **stil** Kant linje format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) kant linje format uppsättningen har slutförts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set border style of “my_widget”. */
status = gx_widget_border_style_set(&my_widget,
                                    GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the widget “my_widget” border style has been set. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_width_get"></a>gx_widget_border_width_get
### <a name="get-widget-border-width"></a>Hämta kant linje bredd för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_border_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar widgetens kant linje bredd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_width** Pekare till målet för widgetens kant linje bredd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat kant linje bredden
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE my_width;

/* Get border width of “my_widget”. */
status = gx_widget_border_width_get(&my_widget, &my_width);

/* If status is GX_SUCCESS, “my_width” contains the border width of the widget “my_widget”. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_canvas_get"></a>gx_widget_canvas_get
### <a name="get-widget-canvas"></a>Hämta arbets ytan för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_canvas_get(
    GX_WIDGET *widget,
    GX_CANVAS **return_canvas)
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar en pekare till den arbets yta som widgeten återges på.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_canvas** Pekare till målet för widgetens arbets yta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widgets arbets yta Hämta
- Det gick inte att hitta **GX_FAILURE** (0X10) widgeten
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Get canvas associated with “my_widget”. */
status = gx_widget_canvas_get(&my_widget, &my_canvas);

/* If status is GX_SUCCESS, “my_canvas” contains the canvas of the widget “my_widget”. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_child_detect"></a>gx_widget_child_detect
### <a name="detect-widget-child"></a>Identifiera underordnad widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_child_detect(
    GX_WIDGET *parent, 
    GX_WIDGET *child,
    GX_BOOL *return_detect);
```

### <a name="description"></a>Beskrivning

Den här tjänsten identifierar om widgeten är underordnad den överordnade widgeten. Den här tjänsten kapslar in för att söka efter underordnade objekt och returnerar TRUE om den överordnade widgeten är på en nivå som är överordnad den underordnade widgeten.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **underordnade** Widgeten pekare till underordnad
- **return_detect** Pekare till målet för identifiering

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) underordnad widget, underordnad widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig **GX_INVALID_WIDGET** (0x12) för överordnad eller underordnad widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BOOL detected;

/* Determine if “my_child” is a child of “my_widget”. */
status = gx_widget_child_detect(&my_widget, &my_child, &detected);

/* If status is GX_SUCCESS and “detected” is GX_TRUE, “my_child” is a child of widget “my_widget”. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_children_draw"></a>gx_widget_children_draw
### <a name="draw-widget-children"></a>Rita widget underordnade

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_children_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar alla underordnade objekt till den överordnade widgeten. Den här tjänsten anropas vanligt vis av alla standard ritnings funktioner i widgeten för att rita alla befintliga underordnade widgetar, och ska anropas av anpassade rit funktioner som gör att underordnade widgetar kan kopplas till din anpassade typ av widget.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
        /* Call default widget background draw. */
        gx_widget_background_draw(widget);

        /* Add your own drawing here. */

        /* Draw child widgets. */
        gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_client_get"></a>gx_widget_client_get
### <a name="get-widget-client-area"></a>Hämta widgets klient områden

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_client_get(
    GX_WIDGET *widget,
    GX_VALUE border_width,
    GX_RECTANGLE *return_client_area);
```
### <a name="description"></a>Beskrivning

Den här tjänsten beräknar klient delen av widgeten genom att dra ifrån widgetens kant linje bredd från den övergripande widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **border_width** Bredd på widgetens kant linje
- **return_client_area** Mål för retur av klient områden

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widgets klient områden Hämta
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0x22) ogiltig widgets kant linje

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RECTANGLE client_area
/* Get client area of widget “my_widget”. */
status = gx_widget_client_get(&my_widget, my_widget_width,
                              &client_area);

/* If status is GX_SUCCESS, the “client_area” is the client area of “my_widget”. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_color_get"></a>gx_widget_color_get
### <a name="get-color"></a>Hämta färg

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_color_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar färgen som är kopplad till det tillhandahållna resurs-ID: t. Den här tjänsten ska endast anropas av synliga widgetar.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till kontroll block för widget
- **resource_id** Resurs-ID för färg. **Bilaga B** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **return_color** Pekare till mål för färg. **Bilaga A** innehåller fördefinierade färger. Observera att programmet även kan lägga till anpassade färger.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad färg hämtning
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CANVAS** (0X20) widgeten är ogiltig eller så är widgeten osynlig
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_COLOR actual_color;

/* Get color for resource ID MY_FIRST_COLOR_ID. */
status = gx_widget_color_get(my_widget, MY_FIRST_COLOR_RESOURCE_ID,
                            &actual_color);

/* If status is GX_SUCCESS the actual color is contained in “actual_color”. */
```
### <a name="see-also"></a>Se även

- gx_widget_font_get
- gx_widget_pixelmap_get

## <a name="gx_widget_create"></a>gx_widget_create
### <a name="create-widget"></a>Skapa widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_create(
    GX_WIDGET *widget, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style, 
    USHORT widget_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en widget.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **namn** Logiskt namn på widget
- **överordnad** Pekare till överordnad widget
- **stil** ATS. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **widget_id** Programdefinierat ID för widgeten
- **storlek** Storlek på widgeten

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widgeten skapa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Den överordnade widgeten **GX_INVALID_WIDGET** (0x12) är inte giltig

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_WIDGET my_widget;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Get client area of widget “my_widget”. */
status = gx_widget_create(&my_widget, "my widget",
                          &my_parent_window, GX_STYLE_BORDER_RAISED, MY_WIDGET_ID, &size);

/* If status is GX_SUCCESS, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_created_test"></a>gx_widget_created_test
### <a name="test-if-widget-created"></a>Testa om widgeten har skapats

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_created_test(
    GX_WIDGET *widget,
    GX_BOOL *return_test);
```
### <a name="description"></a>Beskrivning

Den här tjänsten testar för att avgöra om widgeten redan har skapats. Om inga fel uppstår returnerar den här funktionen GX_SUCCESS, oavsett om widgeten har skapats eller inte. Resultatet av testet finns i return_test-pekaren.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_test** Mål för test resultat

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) slutförd test slut för ande
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BOOL was_created;

/* Test to see if widget “my_widget” is created. */
status = gx_widget_created_test(&my_widget, &was_created);

/* If status is GX_SUCCESS, no error occurred. If “was_created” is
GX_TRUE, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_delete"></a>gx_widget_delete
### <a name="delete-widget"></a>Ta bort widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_delete(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort widgeten. Om widgeten kontroll block tilldelas dynamiskt, anropas tjänsten gx_system_memory_free för att frigöra dynamiskt allokerat lagrings utrymme.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) klar widgeten ta bort GX_CALLER_ERROR (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_SYSTEM_MEMORY_ERROR** (0X30) minnes fri funktion har inte definierats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete widget “my_widget”. */
status = gx_widget_delete(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been deleted. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_detach"></a>gx_widget_detach
### <a name="detach-widget-from-parent"></a>Koppla från widget från överordnad

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_detach(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar bort widgeten från dess överordnade.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widget koppla GX_CALLER_ERROR (0X11) ogiltig anropare av den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Detach widget “my_widget” from its parent. */
status = gx_widget_detach(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been detached. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw"></a>gx_widget_draw
### <a name="draw-widget"></a>Rita widget

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar widgeten. Den här funktionen anropas vanligt vis internt av GUIX-funktionen för uppdatering av arbets ytan, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritnings funktioner.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
      /* Call default widget draw. */
      gx_widget_draw(widget);

      /* Add your own drawing here. */
}
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw_set"></a>gx_widget_draw_set
### <a name="assign-the-widget-drawing-function"></a>Tilldela ritnings funktionen för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_draw_set(
    GX_WIDGET *widget,
    VOID (*drawing_function) (GX_WIDGET *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten åsidosätter standard ritnings funktionen i widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **drawing_function** Pekare till ritnings funktion

### <a name="return-values"></a>Retur värden

- Åsidosätta **GX_SUCCESS** (0x00) widgeten ritnings funktion
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Define a custom drawing function. */
VOID my_drawing_function(GX_WIDGET *widget)
{
      /* Add your own drawing here. */
}

/* Set the drawing function of widget “my_widget” to “my_drawing_function”. */
status = gx_widget_draw_set(&my_widget, my_drawing_function);

/* If status is GX_SUCCESS the widget “my_widget” has the drawning function “my_drawing_function”. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_generate"></a>gx_widget_event_generate
### <a name="generate-widget-event"></a>Skapa widgets händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_generate(
    GX_WIDGET *widget, 
    USHORT event_type, LONG value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten genererar en GX_SIGNAL typ av händelse, som är en viss typ eller klass för GX_EVENT. gx_widget_event_generate () kodar ID för 16-bitars widget, tillsammans med den överförda event_type, till ett enda 32-bitars GX_EVENT. gx_event_type-värde. Parametern Value kodas till den genererade gx_event. gx_event_payload gx_event_payload.gx_event_longdatas fält.

Det genererade event.gx_event_target-fältet läses alltid in med den anropande widgetens överordnade objekt, vilket innebär att den genererade händelsen alltid skickas först till den överordnade för widgeten generera.

Observera att gx_widget_event_generate endast ska användas för att skicka GX_SIGNAL intervall händelse typer. För alla andra händelse typer, inklusive användardefinierade händelse typer, använder du API: et gx_system_event_send (), som ger fullständig kontroll över alla fält i händelsen som skickas i händelse kön för GUIX.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **event_type** Typ av händelse. **Bilaga E** innehåller fördefinierade GUIX-händelser. Ytterligare händelser kan läggas till av programmet.
- **värde** Ytterligare händelse information

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) generering av händelse för klarande widget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Generate a redraw event for widget “my_widget”. */
status = gx_widget_event_generate(&my_widget, GX_EVENT_REDRAW, 0);

/* If status is GX_SUCCESS the redraw event for widget “my_widget” has been generated. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get
- gx_system_event_send

## <a name="gx_widget_event_process"></a>gx_widget_event_process
### <a name="process-widget-event"></a>Händelse för process-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_process(
    GX_WIDGET *widget, 
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Det här är standard funktionen för händelse bearbetning för alla widgetar. När en anpassad händelse bearbetnings funktion skrivs bör standard åtgärden för alla händelse typer alltid vara att skicka händelsen till den widget som widgeten baseras på. Widgetar som baseras på de mest grundläggande GX_WIDGET typen skicka använder gx_widget_event_process som standard funktion för händelse bearbetning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widget av händelse bearbetning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Process event “my_event” for widget “my_widget”. */
status = gx_widget_event_process(&my_widget, &my_event);

/* If status is GX_SUCCESS the event “my_event” for widget “my_widget” has been processed. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_process_set"></a>gx_widget_event_process_set
### <a name="set-event-processing-function-of-widget"></a>Ställ in händelse bearbetnings funktion i widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_process_set(
    GX_WIDGET *widget,
    UINT (*event_processing) (GX_WIDGET *, GX_EVENT *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten åsidosätter funktionen för händelse bearbetning i widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **event_processing** Pekare till ny händelse bearbetnings funktion

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) åsidosättning av händelse bearbetning för widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
UINT my_event_process(GX_TREE_VIEW *tree_view,
                      GX_EVENT *event)
{
      UINT status = GX_SUCCESS;

      switch(event->gx_event_type)
      {
      case xyz:
            /* Insert custom event handling here */
            break;

      default:
            /* Pass all other events to the default tree view
               event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
      }
      return status;
}

/* Use “my_event_process” to process events for widget “my_tree_view”. */
status = gx_widget_event_process_set((GX_WIDGET *)&my_tree_view,
                    (VOID (*)(GX_WIDGET *))my_event_process);

/* If status is GX_SUCCESS all event processing for widget “my_tree_view” is handled by “my_event_process”. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_to_parent"></a>gx_widget_event_to_parent
### <a name="send-event-to-widgets-parent"></a>Skicka händelse till widgetens överordnade

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_to_parent(
    GX_WIDGET *widget,
    GX_EVENT *event);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skickar en händelse till widgetens överordnade.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **händelse** Pekare till händelsen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skickat händelsen till widgetens överordnade
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send my_event to the widget’s parent */
status = gx_widget_event_to_parent(&my_widget, my_event);

/* If status is GX_SUCCESS the event has been delivered to the parent of my_widget. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_fill_color_set"></a>gx_widget_fill_color_set
### <a name="set-widget-background-color"></a>Ange bakgrunds färg för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_fill_color_set(
    GX_WIDGET *widget,
    GX_RESOURCE_ID normal_color_id,
    GX_RESOURCE_ID selected_color_id,
    GX_RESOURCE_ID disabled_color_id);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger bakgrunds färgerna i widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **normal_color_id** Resurs-ID för fyllnings färgen i normalt läge. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **selected_color_id** Resurs-ID för fyllnings färgen när widgeten får fokus. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.
- **disabled_color_id** Resurs-ID för fyllnings färgen när format GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade färg resurs-ID: n. Observera att programmet även kan lägga till anpassade färg resurs-ID: n.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har angett en fyllnings färg för widget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set background of “my_widget”. */
status = gx_widget_fill_color_set(&my_widget,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL);

/* If status is GX_SUCCESS the widget “my_widget” background has been set. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_find"></a>gx_widget_find
### <a name="find-child-widget-of-parent-widget"></a>Sök efter underordnad widget för överordnad widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    INT search_depth, 
    GX_WIDGET **return_widget);
```
### <a name="description"></a>Beskrivning

Den här tjänsten söker igenom de underordnade objekten för den angivna överordnade söker efter en widget med det begärda ID-värdet.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget från vilken sökningen startas
- **widget_id** Widget-ID att söka efter
- **search_depth** Definierar den rekursiva kapslings nivå som funktionen ska söka igenom underordnade widgetar i. Om det här värdet är <= 0 genomsöks bara omedelbara underordnade objekt till den överordnade widgeten. Om det här värdet är GX_SEARCH_DEPTH_INFINITE genomsöks alla underordnade widgetar. För andra värden > 0 begränsar det här värdet hur djupt kapslad den här funktionen söker igenom underordnad widget som sökts efter begärt widgets-ID.
- **return_widget** Pekare till målet för widgeten hittades

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) sökning efter lyckad widget
- **GX_NOT_FOUND** (0X09) widgeten är inte fount
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_WIDGET *widget_found;

/* Find widget “my_widget”. */
status = gx_widget_find(&my_widget, GX_SEARCH_DEPTH_INFINITE
                        MY_WIDGET_ID, &widget_found);

/* If status is GX_SUCCESS, the pointer “widget_found” contains the pointer to the widget found. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_first_child_get"></a>gx_widget_first_child_get
### <a name="return-pointer-to-first-child-widget"></a>Återställ pekare till första underordnade widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_first_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Beskrivning

GUIX underhåller en träd struktur lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till det överordnade objektets första widget.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget_return** Pekare för att returnera widgeten för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESSs** pekare (0x00) returnerades
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_child_widget(GX_WIDGET *parent)
{
      GX_WIDGET *child;
      UINT status;

      status = gx_widget_first_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
            return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Se även

- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_focus_next"></a>gx_widget_focus_next
### <a name="move-focus-to-next-widget-in-navigation-order"></a>Flytta fokus till nästa widget i navigerings ordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_focus_next(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar fokus till nästa på samma nivå-widget i den länkade listan med widgetar som accepterar fokus.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till kontroll block för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) har flyttats
- **GX_FAILURE** (0x00) fokus flyttades inte
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move focus to next widget in navigation order. */ status =
gx_widget_focus_next(&my_widget);

/* If status is GX_SUCCESS the focus has been moved to the next
widget in the navigation order */
```
### <a name="see-also"></a>Se även

- gx_widget_focus_previous

## <a name="gx_widget_focus_previous"></a>gx_widget_focus_previous
### <a name="move-focus-to-previous-widget-in-navigation-order"></a>Flytta fokus till föregående widget i navigerings ordningen

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_focus_previous(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar fokus till föregående widget i navigerings ordningen.

### <a name="parameters"></a>Parametrar

- **widget** Pekare mot widget som har fokus.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) har flyttats
- **GX_FAILURE** (0x00) fokus flyttades inte

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Move focus to previuos widget in navigation order. */ status =
gx_widget_focus_previous(&my_widget);

/* If status is GX_SUCCESS the input focus has been moved to the
previous widget. */
```
### <a name="see-also"></a>Se även

- gx_widget_focus_next

## <a name="gx_widget_font_get"></a>gx_widget_font_get
### <a name="get-font-for-specified-resource-id"></a>Hämta teckensnitt för angivet resurs-ID

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_font_get(
    GX_WIDGETG *widget,
    GX_RESOURCE_ID resource_id,
    GX_FONT **return_font);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det teckensnitt som är associerat med det angivna resurs-ID: t från tabellen Font för visningen där widgeten är synlig. Den här funktionen ska endast anropas av en Visible-widget.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till kontroll block för widget
- **resource_id** Resurs-ID för teckensnitt
- **return_font** Pekare till mål för teckensnitts pekare

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat teckensnitt
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CANVAS** (0X20) widgeten är ogiltig eller så är widgeten osynlig
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_FONT *my_font;
/* Get font for MY_FONT_ID. */
status = gx_widget_font_get(widget, MY_FONT_RESOURCE_ID, &my_font);
/* If status is GX_SUCCESS the font pointer has been retrieved in “my_font”. */
```
### <a name="see-also"></a>Se även

- gx_widget_color_get
- gx_widget_pixelmap_get

## <a name="gx_widget_free"></a>gx_widget_free
### <a name="release-memory-associated-with-a-widget"></a>Versions minne som är associerat med en widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_free(GX_WIDGETG *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör det minne som är associerat med ett kontroll block för validering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till kontroll block för widget
- **resource_id** Resurs-ID för teckensnitt
- **return_font** Pekare till mål för teckensnitts pekare

### <a name="return-values"></a>Retur värden

- Widgeten **GX_SUCCESS** (0X00) har frigjorts
- **GX_SYSTEM_MEMPRY_ERROR** (0X30) minnes fri funktion har inte definierats
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_WIDGET widget;
UINT status;

status = gx_widget_allocate(&widget, sizeof(GX_WIDGET))

/* Free a runtime allocated widget. */
if (status == GX_SUCCESS)
{
      status = gx_widget_free(widget);
}

/* If status is GX_SUCCESS the memory that allocated to the widget has been released. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_front_move"></a>gx_widget_front_move
### <a name="move-widget-to-front"></a>Flytta widgeten till fram sidan

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_front_move(
    GX_WIDGET *widget, 
    GX_BOOL *return_moved);
```

### <a name="description"></a>Beskrivning

Den här tjänsten flyttar widgeten längst fram i den överordnade Z-ordningen lista över underordnade widgetar.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget att flytta
- **return_moved** Pekare till mål för widgeten indikator flyttades

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widget flytta längst fram
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_NO_CHANGE** (0x08) är redan framförd
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BOOL widget_moved;

/* Move widget “my_widget” to the front. */
status = gx_widget_front_move(&my_widget, &widget_moved);

/* If status is GX_SUCCESS and “widget_moved” is GX_TRUE, the
widget “my_widget” was moved to the front . */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_height_get"></a>gx_widget_height_get
### <a name="get-widget-height"></a>Hämta widgetens höjd

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_height_get(
    GX_WIDGET *widget,
    UINT *return_height);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar widgetens höjd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_height** Pekare till målet för widgetens höjd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widgets höjd Hämta
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE widget_height;

/* Get height for widget “my_widget”. */
status = gx_widget_height_get(&my_widget, &widget_height);

/* If status is GX_SUCCESS the height of the widget is contained in
“widget_height” . */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_hide"></a>gx_widget_hide
### <a name="hide-widget"></a>Dölj widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_hide(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten döljer widgeten. Den här widgeten är fortfarande kopplad till den överordnade, men det är inte tillåtet att rita på arbets ytan.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widget Dölj
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Hide widget “my_widget”. */
status = gx_widget_hide(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is hidden. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_style_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_last_child_get"></a>gx_widget_last_child_get
### <a name="return-pointer-to-last-child-widget"></a>Återställ pekare till sista underordnade widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_last_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Beskrivning

GUIX underhåller en träd struktur lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till det överordnade objektets sista widget.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget_return** Pekare för att returnera widgeten för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESSs** pekare (0x00) returnerades
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_last_child_widget(GX_WIDGET *parent)
{

      GX_WIDGET *child;
      UINT status;

      status = gx_widget_last_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
              return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Se även

- gx_widget_first_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_next_sibling_get"></a>gx_widget_next_sibling_get
### <a name="return-pointer-to-next-sibling-of-current-widget"></a>Retur pekare till nästa objekt på samma nivå som aktuell widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_next_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Beskrivning

GUIX underhåller en träd struktur lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till nästa objekt på samma nivå som den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuella** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widgeten för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESSs** pekare (0x00) returnerades
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve next sibling widget pointer. */

GX_WIDGET *get_next(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_next_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
            return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Se även

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_parent_get"></a>gx_widget_parent_get
### <a name="return-pointer-to-parent-of-current-widget"></a>Retur pekare till överordnad för aktuell widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_parent_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Beskrivning

GUIX underhåller en träd struktur lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till den aktuella widgetens överordnad.

### <a name="parameters"></a>Parametrar

- **aktuella** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widgeten för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESSs** pekare (0x00) returnerades
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve parent widget */

GX_WIDGET *get_parent(GX_WIDGET *current)
{
      GX_WIDGET *parent;
      UINT status;

      status = gx_widget_parent_get(current, &parent);
      if (status == GX_SUCCESS)
      {
            return parent;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Se även

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_pixelmap_get"></a>gx_widget_pixelmap_get
### <a name="get-pixelmap"></a>Hämta Pixelmap

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_pixelmap_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_PIXELMAP **return_pixelmap);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar de Pixelmap som är associerade med det tillhandahållna resurs-ID: t. Den här tjänsten ska endast anropas för synliga widgetar.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till kontroll block för widget
- **pixelmap_id** Resurs-ID för Pixelmap
- **return_pixelmap** Pekare till Pixelmap-destinations pekare

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades Pixelmap get
- **GX_INVALID_RESOURCE_ID** (0X33) ogiltigt resurs-ID
- **GX_INVALID_CANVAS** (0X20) widgeten är ogiltig eller så är widgeten osynlig
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
GX_PIXELMAP *my_pixelmap;

/* Get the pixelmap associated with MY_PIXELMAP_ID. */
status = gx_widget_pixelmap_get(widget, MY_PIXELMAP_RESOURCE_ID,
                                &my_pixelmap);

/* If status is GX_SUCCESS, “my_pixelmap” contains the pixemap pointer. */
```
### <a name="see-also"></a>Se även

- gx_widget_color_get
- gx_widget_font_get

## <a name="gx_widget_previous_sibling_get"></a>gx_widget_previous_sibling_get
### <a name="return-pointer-to-previous-sibling-of-the-current-widget"></a>Retur pekare till föregående objekt på samma nivå som den aktuella widgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_previous_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Beskrivning

GUIX underhåller en träd struktur lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till föregående objekt på samma nivå som den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuella** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widgeten för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESSs** pekare (0x00) returnerades
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve previous sibling widget */

GX_WIDGET *get_previous(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_previous_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
          return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Se även

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_resize"></a>gx_widget_resize
### <a name="resize-widget"></a>Ändra storlek på widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_resize(
    GX_WIDGET *widget, 
    GX_RECTANGLE *new_size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar storlek på widgeten. Om widgeten är synlig inkommer den automatiskt att inval IDE ras och placeras i kö för att rita om.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **new_size** Ny widgets storlek

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) ändra storlek på widgeten
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RECTANGLE new_size;

gx_utility_rectangle_define(&new_size, 0, 0, 100, 100);

/* Resize widget “my_widget”. */
status = gx_widget_resize(&my_widget, &new_size);

/* If status is GX_SUCCESS the widget “my_widget” has been resized. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_shift"></a>gx_widget_shift
### <a name="shift-widget"></a>Shift-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_shift(
    GX_WIDGET *widget, 
    GX_VALUE x_shift,
    GX_VALUE y_shift, 
    GX_BOOL mark_dirty);
```

### <a name="description"></a>Beskrivning

Den här tjänsten växlar widgeten och markerar den som smutsig.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **x_shift** Antal pixlar som ska flyttas på x-axeln
- **y_shift** Antal pixlar som ska flyttas på y-axeln
- **mark_dirty** GX_TRUE för att indikera smutsig, annars GX_FALSE

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widgets shift-GX_CALLER_ERROR (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Shift widget “my_widget”. */
status = gx_widget_shift(&my_widget, 10, 20, GX_FALSE);

/* If status is GX_SUCCESS the widget “my_widget” has been shifted. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_show"></a>gx_widget_show
### <a name="show-widget"></a>Visa widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_show(GX_WIDGET *widget);
```

### <a name="description"></a>Beskrivning

Den här tjänsten visar widgeten. Widgeten blir bara synlig om den är kopplad till en överordnad mapp och den överordnade widgeten också är synlig.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) klar widgeten Visa
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Show widget “my_widget”. */
status = gx_widget_show(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been shown. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_add"></a>gx_widget_status_add
### <a name="add-widget-status"></a>Lägg till widgets status

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_add(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till valfri kombination av status flaggor i den angivna widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **status** Status som ska läggas till

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) status Lägg till för widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Add status to widget “my_widget”. */
status = gx_widget_status_add(&my_widget, status_to_add);

/* If status is GX_SUCCESS the widget “my_widget” status was. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_get"></a>gx_widget_status_get
### <a name="get-widget-status"></a>Hämta widgets status

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_get(
    GX_WIDGET *widget,
    ULONG *return_status)
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar status flaggor från widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_status** Pekare till den status som returneras

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) status Hämta för widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
ULONT get_status;

/* Retrieve status flag from widget “my_widget”. */ status =
gx_widget_status_get(&my_widget, &get_status);

/* If status is GX_SUCCESS the status from widget “my_widget” is
saved to “get_status”. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_remove"></a>gx_widget_status_remove
### <a name="remove-widget-status"></a>Ta bort widgets status

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_remove(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort angivna status flaggor från variabeln widget Internal status.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **status** Status som ska tas bort

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) borttagning av widgeten status
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Remove status of widget “my_widget”. */
status = gx_widget_status_remove(&my_widget, status_to_remove);

/* If status is GX_SUCCESS, the status flags are removed from the
widget “my_widget”. */
```
### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_test"></a>gx_widget_status_test
### <a name="test-widget-status"></a>Testa widgeten status

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_test(
    GX_WIDGET *widget, 
    ULONG status,
    GX_BOOL *return_test);
```
### <a name="description"></a>Beskrivning

Den här tjänsten testar status flaggorna för den angivna widgeten och lagrar resultatet i minnet som påpekas av "return_test".

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **status** Status som ska testas
- **return_status** Pekare till målet för resultatet av testet

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) status test för widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_BOOL test_result;

/* Test status of widget “my_widget”. */
status = gx_widget_status_test(&my_widget, status_to_test,
                              &test_result);

/* If status is GX_SUCCESS the widget “my_widget” status was tested
and the result in “test_result”. */
```
### <a name="see-also"></a>Se även

- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_string_get"></a>gx_widget_string_get
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id-deprecated"></a>Hämta strängen som är associerad med en synlig widget och sträng-ID (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_widget_string_get_ext ().

Den här tjänsten returnerar sträng tabell posten för angivet sträng-ID-värde. Den här tjänsten liknar gx_display_string_get, förutom att den aktiva visningen fastställs automatiskt i stället för att skickas in av anroparen. Den här tjänsten kan endast användas för widgetar som är synliga, d.v.s. den visning som är kopplad till denna widget är känd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **string_id** Sträng-ID-värde från resurs huvud
- **sträng** Adress till variabel att returnera sträng

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) status test för widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CONST GX_CHAR *string;

/* Test status of widget “my_widget”. */
status = gx_widget_string_get(&my_widget, GX_STRING_ID_SHUTDOWN,
      &string);

/* If status is GX_SUCCESS the string has been retrieved */
```
### <a name="see-also"></a>Se även

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_string_get_ext"></a>gx_widget_string_get_ext
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id"></a>Hämta strängen som är associerad med en synlig widget och sträng-ID

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar sträng tabell posten för angivet sträng-ID-värde. Den här tjänsten liknar gx_display_string_get, förutom att den aktiva visningen fastställs automatiskt i stället för att skickas in av anroparen. Den här tjänsten kan endast användas för widgetar som är synliga, d.v.s. den visning som är kopplad till denna widget är känd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **string_id** Sträng-ID-värde från resurs huvud
- **sträng** Adress till variabel att returnera sträng

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) status test för widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_STRING string;

/* Test status of widget “my_widget”. */

status = gx_widget_string_get_ext(&my_widget,
                          GX_STRING_ID_SHUTDOWN, &string);

/* If status is GX_SUCCESS the string has been retrieved */
```

### <a name="see-also"></a>Se även

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_style_add"></a>gx_widget_style_add
### <a name="add-widget-style"></a>Lägg till format för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_add(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en stil i widgeten. Dessutom vidtas följande åtgärder.

Om det tillagda formatet är GX_STYLE_TRANSPARENT kommer status GX_STATUS_TRANSPARENT läggas till.

Om det tillagda formatet är GX_STYLE_ENABLED kommer status GX_STATUS_SELECTABLE läggas till.

Om widgeten är synlig inkommer den automatiskt att inval IDE ras och placeras i kö för att rita om.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **stil** Nytt format som ska läggas till. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) Lägg till widgeten format
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Add style to widget “my_widget”. */
status = gx_widget_style_add(&my_widget, GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS, the style was successfully applied to the widget “my_widget”. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_get"></a>gx_widget_style_get
### <a name="get-widget-style"></a>Hämta widgets format

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_get(
    GX_WIDGET *widget, 
    ULONG *return_style)
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar format flaggan från widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_style** Pekare till det format som returneras.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har hämtat widgets format
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar


### <a name="example"></a>Exempel

```C
/* Retrieve style from widget into “style”. */
status = gx_widget_style_get(&my_widget, &style);

/* If status is GX_SUCCESS the style flag from widget is saved in “style”. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_remove
- gx_widget_style_add
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_remove"></a>gx_widget_style_remove
### <a name="remove-widget-style"></a>Ta bort widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_remove(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en stil från widgeten. Dessutom vidtas följande åtgärder.

Om det borttagna formatet är GX_STYLE_TRANSPARENT tas status GX_STATUS_TRANSPARENT bort.

Om det borttagna formatet är GX_STYLE_ENABLED tas status GX_STATUS_SELECTABLE bort.

Om widgeten är synlig inkommer den automatiskt att inval IDE ras och placeras i kö för att rita om.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **stil** Format att ta bort. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00)-lyckad borttagning av widget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Remove style from widget “my_widget”. */
status = gx_widget_style_remove(&my_widget,
                                GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the GX_STYLE_BORDER_RAISED style was removed from the widget “my_widget”.*/
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_set"></a>gx_widget_style_set
### <a name="set-widget-style"></a>Ange format för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_set(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Beskrivning

Den här tjänsten ställer in ett format på widgeten.

Om set-formatet innehåller GX_STYLE_TRANSPARENT läggs status GX_STATUS_TRANSPARENT till, annars tas statusen bort.

Om set-formatet innehåller GX_STYLE_ENABLED läggs status GX_STATUS_SELECTABLE till, annars tas statusen bort.

Om widgeten är synlig inkommer den automatiskt att inval IDE ras och placeras i kö för att rita om.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **stil** Format som ska anges. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad widgets format uppsättning
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set style GX_STYLE_TRANSPARENT to the widget “my_widget”. */
status = gx_widget_style_set(&my_widget, GX_STYLE_TRANSPARENT);

/* If status is GX_SUCCESS the widget “my_widget” style is set to GX_STYLE_TRANSPARENT. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_text_blend"></a>gx_widget_text_blend
### <a name="blend-text-assigned-to-widget-deprecated"></a>Blanda text som har tilldelats widgeten (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_widget_text_blend_ext ().

Den här tjänsten blandar den angivna texten via en widget med aktuell pensel och text justering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Text färg
- **font_id** Teckensnitts-ID
- **sträng** Ritnings sträng
- **x_offset** Justering av ritnings position
- **y_offset** Justering av ritnings position
- **alpha** Blend-värde 0-255

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bredd för lyckad widget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend(&my_widget, my_text_color, my_font_id,
                              &my_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>Se även

- gx_widget_text_blend_ext

## <a name="gx_widget_text_blend_ext"></a>gx_widget_text_blend_ext
### <a name="blend-text-assigned-to-widget"></a>Blanda text kopplad till widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_widget_text_blend_ext ().

Den här tjänsten återger en sträng över den angivna widgeten med aktuell pensel och text justering och angiven färg, teckensnitt och x, y-förskjutning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Text färg
- **font_id** Teckensnitts-ID
- **sträng** Ritnings sträng
- **x_offset** Justering av ritnings position
- **y_offset** Justering av ritnings position
- **alpha** Blend-värde 0-255

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bredd för lyckad widget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_STRING_LENGTH** (0X34) ogiltig sträng längd

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend_ext(&my_widget,
        my_text_color,
        my_font_id,
        &render_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>Se även

- gx_widget_text_draw_ext

## <a name="gx_widget_text_draw"></a>gx_widget_text_draw
### <a name="draw-text-assigned-to-widget-deprecated"></a>Rita text som är kopplad till widgeten (inaktuell)

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset)
```

### <a name="description"></a>Beskrivning

Den här tjänsten är föråldrad till förmån för gx_widget_text_draw_ext ().

Den här tjänsten ritar den angivna texten via en widget med aktuell pensel och text justering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Text färg
- **font_id** Teckensnitts-ID
- **sträng** Ritnings sträng
- **x_offset** Justering av ritnings position
- **y_offset** Justering av ritnings position

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text draw. */
    gx_widget_text_draw(widget, my_text_color, my_font_id
                        &my_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>Se även

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_draw_ext"></a>gx_widget_text_draw_ext
### <a name="draw-text-assigned-to-widget"></a>Rita text som är kopplad till widget

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget,
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset,
    INT y_offset)
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar den angivna texten via en widget med aktuell pensel och text justering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Text färg
- **font_id** Teckensnitts-ID
- **text_id** Text-ID
- **x_offset** Justering av ritnings position
- **y_offset** Justering av ritnings position

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Write a custom widget draw function. */
VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background draw here. */

    /* Call widget text draw. */
    gx_widget_text_draw_ext(widget, my_text_color, my_font_id
                        &render_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>Se även

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_id_draw"></a>gx_widget_text_id_draw
### <a name="draw-text-assigned-to-widget"></a>Rita text som är kopplad till widget

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_text_id_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    UINT text_id,
    INT x_offset, 
    INT y_offse)
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar text över en widget med ett text-ID.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Text färg
- **font_id** Teckensnitts-ID
- **text_id** Text-ID
- **x_offset** Justering av ritnings position
- **y_offset** Justering av ritnings position

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text id draw. */
    gx_widget_text_id_draw(widget, my_text_color, my_font_id
                            &my_string_id, xoffset, yoffset);
}
```

### <a name="see-also"></a>Se även

- gx_widget_text_blend
- gx_widget_text_draw

## <a name="gx_widget_top_visible_child_find"></a>gx_widget_top_visible_child_find
### <a name="return-pointer-to-visible-child-that-is-top-of-z-order"></a>Returnera pekare till synligt underordnat som är överst i Z-ordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_top_visible_child_find(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Beskrivning

GUIX underhåller en träd struktur lista över överordnade och underordnade widgetar.
Den här tjänsten returnerar en pekare till den översta synliga underordnad för den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuella** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widgeten för widget

### <a name="return-values"></a>Retur värden

- **GX_SUCCESSs** pekare (0x00) returnerades
- **GX_PTR_ERROR** (0X07) ogiltig widgets pekare
- **GX_INVALID_WIDGET** (0X12) ogiltig widget

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve topmost visible widget on the display */

GX_WIDGET *get_top_window(GX_WINDOW_ROOT *root)
{
    GX_WIDGET *top_window;
    UINT status;

    status = gx_widget_top_visible_child_find(root, &top_window);
    if (status == GX_SUCCESS)
    {
        return top_window;
    }
    return GX_NULL;
}
```

### <a name="see-also"></a>Se även

- gx_widget_first_child_get,
- gx_widget_last_child_get,
- gx_widget_next_sibling_get,
- gx_widget_parent_get,
- gx_widget_previous_sibling_get

## <a name="gx_widget_type_find"></a>gx_widget_type_find
### <a name="search-for-a-widget-of-the-requested-type"></a>Sök efter en widget av den begärda typen

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_type_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    GX_WIDGET **return_widget)
```

### <a name="description"></a>Beskrivning

Den här tjänsten söker efter en widget av den begärda typen.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_width** Pekare till målet för widgetens bredd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bredd för lyckad widget
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_WIDGET *retrieved_widget;

/* Find horizontal scrollbar under “parent_widget”. */
status = gx_widget_type_find(&parent_widget,
                GX_TYPE_HORIZONTAL_SCROLL_BAR, &retrieved_widget);

/* If status is GX_SUCCESS, the horizontal scrollbar widget is retrieved. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_width_get"></a>gx_widget_width_get
### <a name="get-widget-width"></a>Hämta widgetens bredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width)
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar bredden på widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_width** Pekare till målet för widgetens bredd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bredd för lyckad widget
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE my_widget_width;

/* Get width of widget “my_widget”. */
status = gx_widget_width_get(&my_widget, &my_widget_width);

/* If status is GX_SUCCESS the width of widget “my_widget” is in “my_widget_width”. */
```

### <a name="see-also"></a>Se även

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_window_client_height_get"></a>gx_window_client_height_get
### <a name="get-window-client-height"></a>Hämta fönster klientens höjd

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_client_height_get(
    GX_WINDOW *window,
    GX_VALUE *return_height);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar fönstrets klient höjd.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **return_height** Pekare till mål för klient höjd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckades fönster klient höjd Hämta
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RECTANGLE my_client_height;

/* Get client height of “my_window”. */
status = gx_window_client_height_get(&my_window,
                                     &my_client_height);

/* If status is GX_SUCCESS the window “my_window” client height is contained in “my_client_height”. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- x_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_scroll"></a>gx_window_client_scroll
### <a name="scroll-window-clients"></a>Rulla fönster klienter

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_client_scroll(
    GX_WINDOW *window, 
    GX_VALUE x_scroll,
    GX_VALUE y_scroll);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rullar fönstrets klienter efter den angivna mängden.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **x_scroll** Antal att rulla på x-axeln
- **y_scroll** Antal att rulla på y-axeln

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) rullning av fönster klient
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_VALUE** (0X22) rullnings värde (s) är inte giltiga

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Scroll clients of “my_window”. */
status = gx_window_client_scroll(&my_window, 10, 0);

/* If status is GX_SUCCESS the clients of window “my_window” have been scrolled. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_width_get"></a>gx_window_client_width_get
### <a name="get-window-client-width"></a>Hämta fönstrets klient bredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_client_width_get(
    GX_WINDOW *window,
    GX_VALUE *return_width);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar klient bredden för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **return_height** Pekare till mål för klient bredd

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) fönstrets klient bredd Hämta
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_VALUE my_client_widthl

/* Get client width of “my_window”. */
status = gx_window_client_width_get(&my_window, &my_client_width);

/* If status is GX_SUCCESS “my_client_width” contains the client width of window “my_window”. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_close"></a>gx_window_close
### <a name="close-modal-window"></a>Stäng modal fönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_close(GX_WINDOW *window);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tvingar fram en spärr ande fönster för att koppla från den överordnade och returnera från den modala körnings slingan.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) fönstret har stängts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Close window “my_window”. */
status = gx_window_close(&my_window);

/* If status is GX_SUCCESS window “my_window” has been closed. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_create"></a>gx_window_create
### <a name="create-window"></a>Skapa fönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_create(
    GX_WINDOW *window, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style,
    USHORT window_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett fönster.

GX_WINDOW härleds från GX_WIDGET och stöder alla gx_widget API-tjänster.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster kontroll block
- **namn** Logiskt namn på fönstret
- **överordnad** Pekare till överordnad widget
- **stil** Fönster format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-/regionsspecifika format.
- **window_id** Programdefinierat ID för fönstret
- **storlek** Storlek på fönstret

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) fönstret har skapats
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_WINDOW my_window;

/* Create window “my_window”. */
status = gx_window_create(&my_window, "my window",
                          &my_parent_window, GX_STYLE_BORDER_RAISED,
                          MY_WINDOW_ID, &size);

/* If status is GX_SUCCESS window “my_window” has been created. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_draw"></a>gx_window_draw
### <a name="draw-window"></a>Rita fönster

### <a name="prototype"></a>Prototyp

```C
VOID gx_window_draw(GX_WINDOW *window);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ritar ett fönster. Den här tjänsten kallas vanligt vis internt under uppdatering av arbets ytan, men kan också anropas från anpassade fönster rit funktioner.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster kontroll block

### <a name="return-values"></a>Retur värden

- **Ingen**

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a custom window draw function. */

VOID my_custom_window_draw(GX_WINDOW *window)
{
    /* Call default window draw. */
    gx_window_draw(window);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_event_process"></a>gx_window_event_process
### <a name="process-window-event"></a>Händelse för process fönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_event_process(
    GX_WINDOW *window, 
    GX_EVENT *event);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar en händelse för det här fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster kontroll block
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) bearbetning av händelse bearbetning i fönster
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic window event processing as part of custom event processing function. */

UINT custom_window_event_process(GX_WINDOW *window,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default window
            event processing */
            status = gx_window_event_process(window, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_execute"></a>gx_window_execute
### <a name="modally-execute-a-window"></a>Köra ett fönster samtidigt

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_execute(
    GX_WINDOW *window,
    ULONG *return_ptr)
```

### <a name="description"></a>Beskrivning

Den här tjänsten kör ett fönster. Alla indata från användaren (Penn händelser osv.) utanför fönstrets klient del kommer att ignoreras. Observera att den här funktionen anger en kontinuerlig blockerande körnings slinga och återgår inte till anroparen förrän modell körningen har avslut ATS.

Den modala körningen avslutas när händelse bearbetningen för mottagna händelser returnerar ett status värde som inte är noll eller när gx_window_close API-funktionen anropas. Retur koden för händelse bearbetning som inte är noll returneras till anroparen genom den return_ptr som skickas till detta API

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster kontroll block
- **return_ptr** Plats för att spara avslutnings statusen för den modala körningen. Kan vara GX_NULL.

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad körning
- **GX_SYSTEM_EVENT_RECEIVE_ERROR (0x05)** Det gick inte att pickup-händelsen från händelse kön
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Execute a modal window. */
status = gx_window_execute(&my_window, &return_code);

/* If status is GX_SUCCESS the window was executed, and return_code holds the execution return code. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_create"></a>gx_window_root_create
### <a name="create-a-root-window"></a>Skapa ett rot fönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_CONST GX_CHAR *name,
    GX_CANVAS *canvas, 
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar ett rot fönster.

### <a name="parameters"></a>Parametrar

- **root_window** Pekare till fönster kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har skapat rot fönstret
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- **GX_INVALID_SIZE** (0X19) ogiltig block storlek för widgets kontroll
- Widgeten **GX_ALREADY_CREATED** (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ROOT_WINDOW root_window;
GX_CANVAS canvas;

/* Create canvas here. */

/* Create a root window */
status = gx_window_root_create(&root_window, “root”, &canvas,
GX_STYLE_BORDER_NONE, GX_NULL, &size);

/* If status is GX_SUCCESS, the “root_window” is successfully created. */
```

### <a name="see-also"></a>Se även

- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find

## <a name="gx_window_root_delete"></a>gx_window_root_delete
### <a name="destroy-a-root-window"></a>Förstör ett rot fönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_delete(GX_WINDOW_ROOT *root_window)
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett rot fönster.

### <a name="parameters"></a>Parametrar

- **root_window** Pekare till fönster kontroll block

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har tagit bort rot fönstret
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_SYSTEM_MEMORY_ERROR** (0X30) minnes fri funktion har inte definierats

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Delete a root window */
status = gx_window_root_delete(&root_window);

/* If status is GX_SUCCESS the “root_window” is destroyed. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_event_process"></a>gx_window_root_event_process
### <a name="process-event-for-the-root-window"></a>Process händelse för rot fönstret

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_EVENT *event)
```

### <a name="description"></a>Beskrivning

Den här tjänsten bearbetar händelser för det angivna rot fönstret.

### <a name="parameters"></a>Parametrar

- **root_window** Pekare till fönster kontroll block
- **händelse** Pekare till händelsen som ska bearbetas

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) har bearbetat rot fönster händelsen
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Call generic root window event processing as part of custom event processing function. */

UINT custom_root_window_event_process(GX_ROOT_WINDOW *root,
                                      GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default root window
            event processing */
        status = gx_window_root_event_process(root, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_find"></a>gx_window_root_find
### <a name="find-root-window"></a>Hitta rot fönstret

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_find(
    GX_WIDGET *widget,
    GX_WINDOW_ROOT **return_root_window);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hittar rot fönstret för den angivna widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till kontroll block för widget
- **return_root_window** Pekare till målet för rot fönstret hittades

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0X00) lyckad rot fönster Sök
- **GX_FAILURE** (0X00) rot fönstret finns inte
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Find root window associated with window “my_window”. */
status = gx_window_root_find(&my_window, &root_window);

/* If status is GX_SUCCESS the “root_window” contains the root window for window “my_window”. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scroll_info_get"></a>gx_window_scroll_info_get
### <a name="get-window-scroll-info"></a>Hämta fönstrets rullnings information

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_scroll_info_get(
    GX_WINDOW *window, 
    ULONG style,
    GX_SCROLL_INFO *return_scroll_info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar fönstrets rullnings information.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **stil** GX_SCROLLBAR_HORIZONTAL eller GX_SCROLLBAR_VERTICAL
- **return_scroll_info** Pekare till mål för rullnings information. Det överordnade fönstret initierar den här strukturen för att informera rullnings listen för det överordnade fönstrets totala storlek, visnings Bart yta och rullnings steg och-gränser. Standard implementeringen använder Windows-klientprogrammet som visnings Bart yta och rullas efter pixlar, men anpassad fönster implementering kan använda rullnings parametrar. **Bilaga i** innehåller definitionen av GX_SCROLL_INFOs strukturen

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) rullning av fönster rullnings information Hämta
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_TYPE** (0X1B) ogiltig typ

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for window “my_window”. */
status = gx_window_scroll_info_get(&my_window,
                    GX_SCROLLBAR_HORIZONTAL, &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for window “my_window”. */
```
### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scrollbar_find"></a>gx_window_scrollbar_find
### <a name="find-window-scrollbar"></a>Hitta fönster rullnings List

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_scrollbar_find(
    GX_WINDOW *window, 
    USHORT type,
    GX_SCROLLBAR **return_scrollbar);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hittar rullnings listen för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **typ** GX_TYPE_VERTICAL_SCROLL eller GX_TYPE_HORIZONTAL_SCROLL
- **return_scrollbar** Pekare till målet för ScrollBar

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) rullning av rullnings fönster Sök
- Det gick inte att hitta **GX_NOT_FOUND** (0X09) rullnings List
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)
- **GX_INVALID_TYPE** (0X1B) ogiltig typ

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Find horizontal scrollbar for window “my_window”. */
status = gx_window_scrollbar_find(&my_window,
                 GX_SCROLLBAR_HORIZONTAL, &my_scrollbar);

/* If status is GX_SUCCESS the “my_scrollbar” contains the horizontal scrollbar for window “my_window”. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_get"></a>gx_window_wallpaper_get
### <a name="get-window-wallpaper"></a>Hämta fönstrets Skriv bords underlägg

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_wallpaper_get(
    GX_WINDOW *window,
    GX_RESOURCE_ID *return_wallpaper_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar Skriv bords underlägget för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **return_wallpaper_id** Pekare till mål för resurs-ID för Skriv bords underlägg

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) framgångs rik fönster-skrivbordsunderlägg Hämta
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_RESOURCE_ID my_window_wallpaper;

/* Get wallpaper for window “my_window”. */
status = gx_window_wallpaper_get(&my_window, &my_window_wallpaper);

/* If status is GX_SUCCESS the “my_window_wallpaper” contains the wallpaper resource ID for window “my_window”. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_set"></a>gx_window_wallpaper_set
### <a name="set-window-wallpaper"></a>Ange fönster Skriv bords underlägg

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_wallpaper_set(
    GX_WINDOW *window,
    GX_RESOURCE_ID wallpaper_id,
    GX_BOOL tile);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger Skriv bords underlägg för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **wallpaper_id** Resurs-ID för Skriv bords underlägg som ska användas
- **panel** Skriv bords underlägg visas sida vid sida om GX_TRUE, annars visas inte bakgrunden

### <a name="return-values"></a>Retur värden

- **GX_SUCCESS** (0x00) fönstrets Skriv bords skriv bord har angetts
- **GX_CALLER_ERROR** (0X11) ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0X07) ogiltig pekare
- Ogiltig widget för **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set wallpaper for window “my_window”. */
status = gx_window_wallpaper_set(&my_window,
                                 MY_WALLPAPER_RESOURCE_ID,
                                 GX_TRUE);

/* If status is GX_SUCCESS the wallpaper for window “my_window” is set. */
```

### <a name="see-also"></a>Se även

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
-  gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
