---
title: Kapitel 4 – Beskrivning av GUIX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla GUIX-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c89014c571b2b59279487cd24d5ec9e36019ed4c3ec2b6470b80e150214ebf3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786831"
---
# <a name="chapter-4---description-of-guix-services"></a>Kapitel 4 – Beskrivning av GUIX-tjänster

Det här kapitlet innehåller en beskrivning av alla GUIX-tjänster (visas nedan) i alfabetisk ordning.  

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den GX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade. 

| **GUIX-tjänst**                      | **Beskrivning**                                                                             |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| gx_accordion_menu_create            | Skapa dragspelsmeny                                                                        |
| gx_accordion_menu_draw              | Menyn Rita dragspel                                                                          |
| gx_accordion_menu_event_process    | Processspelarmenyhändelse                                                                 |
| gx_accordion_menu_position          | Placera menyalternativ                                                                          |
| gx_animation_canvas_define          | Ange minne till en animeringskontrollant för en arbetsyta som ska användas för efterföljande animeringar. |
| gx_animation_create                  | Skapa en animeringskontrollant                                                               |
| gx_animation_delete                  | Ta bort en eller flera animeringskontrollanter |
| gx_animation_drag_disable           | Inaktivera dra animerings hook på skärmen                                                           |
| gx_animation_drag_enable            | Aktivera skärm dra animering hook                                                            |
| gx_animation_landing_speed_set     | Ange landningshastighet för animering med skärm dra                                                  |
| gx_animation_start                   | Initiera en animeringssekvens                                                               |
| gx_animation_stop                    | Pausa en animeringssekvens                                                                |
| gx_binres_language_count_get      |  Hämta språkantal från en binär resursfil                                          |
| gx_binres_language_info_load      |  Läs språknamn och storleksinformation från binär resursfil.                           |
| gx_binres_language_table_load      | (inaktuell) Läsa in en språktabell från en binär resursdatabuffert                          |
| gx_binres_language_table_load_ext | Läsa in en språktabell från en binär resursdatabuffert                                       |
| gx_binres_theme_load                | Läsa in ett tema från databufferten för binär resurs                                                |
| gx_brush_default                     | Initiera aktuell pensel till standardvärden                                                         |
| gx_brush_define                      | Definiera pensel                                                                                 |
| gx_button_background_draw           | Bakgrund för knappen Rita                                                                       |
| gx_button_create                     | Knappen Skapa                                                                                |
| gx_button_deselect                   | Knappen Avmarkera                                                                              |
| gx_button_draw                       | Knappen Rita                                                                                  |
| gx_button_event_process            | Händelse för processknapp                              |
| gx_button_select                    | Knappen Välj                                     |
| gx_canvas_alpha_set                | Ange alfa-blend-värde för arbetsyta                  |
| gx_canvas_arc_draw                 | Rita cirkel arc                                   |
| gx_canvas_block_move               | Flytta block                                        |
| gx_canvas_circle_draw              | Rita cirkel                                       |
| gx_canvas_create                    | Skapa en arbetsyta                                   |
| gx_canvas_delete                    | Ta bort en arbetsyta                                   |
| gx_canvas_drawing_complete         | Slutföra arbetsyteritning                           |
| gx_canvas_drawing_initiate         | Initiera ritning på arbetsytan                        |
| gx_canvas_ellipse_draw             | Rita en ellips                                   |
| gx_canvas_hardware_layer_bind     | Binda arbetsyta till grafiklager                     |
| gx_canvas_hide                      | Göra en arbetsyta osynlig                           |
| gx_canvas_line_draw                | Rita linje                                         |
| gx_canvas_memory_define            | Tilldela minnesadress för arbetsyta                      |
| gx_canvas_offset_set               | Tilldela skärmförskjutning för arbetsyta x,y                  |
| gx_canvas_pie_draw                 | Rita en cirkelform (sektorer)                          |
| gx_canvas_pixel_draw               | Rita en enskild pixel                               |
| gx_canvas_pixelmap_blend           | Blanda en pixelkarta med bakgrund                  |
| gx_canvas_pixelmap_get             | Hämta en pixelkarta som pekar på arbetsytedata            |
| gx_canvas_pixelmap_draw            | Rita pixelkarta                                     |
| gx_canvas_pixelmap_rotate          | Rotera pixelkarta                                   |
| gx_canvas_pixelmap_tile            | Bildpunktskarta för panel                                     |
| gx_canvas_polygon_draw             | Rita polygon                                      |
| gx_canvas_rectangle_draw           | Rita rektangel                                    |
| gx_canvas_rotated_text_draw       | (inaktuell) Rita text roterad runt mittpunkten |
| gx_canvas_rotated_text_draw_ext  | Rita text roterad runt mittpunkten              |
| gx_canvas_shift                     | Skift-arbetsyta från x,y                               |
| gx_canvas_show                      | Göra en arbetsyta synlig                             |
| gx_canvas_text_draw                | (inaktuell) Rita text                            |
| gx_canvas_text_draw_ext           | Rita text                                         |
| gx_checkbox_create                  | Skapa en kryssruta                                 |
| gx_checkbox_draw                    | Rita en kryssruta                                   |
| gx_checkbox_event_process          | Kryssruta för händelseprocessfunktion                   |
| gx_checkbox_pixelmap_set           | Tilldela kryssruta för pixelkarta                          |
| gx_checkbox_select                  | Markera kryssrutan                                   |
| gx_circular_gauge_angle_get       | Hämta mätarwidgetens nålvinkel                |
| gx_circular_gauge_angle_set       | Tilldela mätarwidgetens nålvinkel                  |
| gx_circular_gauge_animation_set   | Definiera animering av cirkelformad mätare                   |
| gx_circular_gauge_background_draw | Rita cirkelformad mätare i bakgrunden                    |
| gx_circular_gauge_create           | Skapa en widget för cirkelmätare                    |
| gx_circular_gauge_draw             | Rita en cirkelformad mätarwidget                      |
| gx_circular_gauge_event_process   | Process cirkulär mätarhändelse                      |
| gx_context_brush_default            | Ange penseln för den aktuella kontexten                                      |
| gx_context_brush_define             | Definiera penseln för den aktuella kontexten                                       |
| gx_context_brush_get                | Hämta pensel av aktuell kontext                                          |
| gx_context_brush_pattern_set       | Ange mönstret för penseln i den aktuella kontexten                           |
| gx_context_brush_set                | Ange pensel för aktuell kontext                                          |
| gx_context_brush_style_set         | Ange penselformat för aktuell kontext                                    |
| gx_context_brush_width_set         | Ange penselbredd för aktuell ontext                                     |
| gx_context_color_get                | Matcha ett färg-ID till färgvärdet                                     |
| gx_context_fill_color_set          | Ange fyllningsfärg för aktuell kontext                                     |
| gx_context_font_get                 | Matcha ett teckensnitts-ID med teckensnitts pekarvärdet                               |
| gx_context_font_set                 | Ange teckensnitt för aktuell kontext                                           |
| gx_context_line_color_set          | Ange linjefärg för aktuell kontext                                     |
| gx_context_pixelmap_get             | Matcha ett pixelkarta-ID till pixelkartans pekarvärde                       |
| gx_context_pixelmap_set             | Tilldela en pensel pixelkarta som används för områdesfyllningar                            |
| gx_context_raw_brush_define        | Definiera råborste för aktuell kontext                                   |
| gx_context_raw_fill_color_set     | Ange rå fyllningsfärg för aktuell kontext                                 |
| gx_context_raw_line_color_set     | Ange rålinjefärg för aktuell kontext                                 |
| gx_context_string_get               | Hämta sträng som är associerad med aktuell ritningskontext (inaktuell). |
| gx_context_string_get_ext          | Hämta sträng som är associerad med aktuell ritningskontext (inaktuell). |
| gx_display_active_language_set     | Tilldela aktivt språk                                                |
| gx_display_color_set                | Ersätt ett färgvärde i visningsfärgtabellen.                       |
| gx_display_color_table_set         | Tilldela färgtabellen som används av en visning                              |
| gx_display_create                    | Skapa visning                                                        |
| gx_display_delete                    | Ta bort visning                                                        |
| gx_display_font_table_set          | Tilldela teckensnittstabellen som används av en visning                               |
| gx_display_language_table_get      | Hämta språktabellen som är associerad med en visning (inaktuell)    |
| gx_display_language_table_get_ext | Hämta språktabellen som är associerad med en visning                 |
| gx_display_language_table_set      | Tilldela språktabellen till angiven visning (inaktuell)           |
| gx_display_language_table_set_ext | Tilldela språktabellen till den angivna visningen.                       |
| gx_display_pixelmap_table_set      | Tilldela pixelkartan som används av en visning                           |
| gx_display_string_get               | Hämta sträng som är associerad med sträng-ID (inaktuell)                |
| gx_display_string_get_ext          | Hämta sträng som är associerad med sträng-ID                             |
| gx_display_string_table_get             | Hämta strängtabell som är associerad med angiven visning (inaktuell). |
| gx_display_string_table_get_ext        | Hämta strängtabell som är associerad med angiven visning               |
| gx_display_theme_install                 | Installera teman på den angivna visningen                               |
| gx_drop_list_close                       | Stäng listrutan                                                       |
| gx_drop_list_create                      | Skapa listrutan                                                      |
| gx_drop_list_event_process               | Bearbetning av listhändelse                                            |
| gx_drop_list_open                        | Öppna listrutan                                                        |
| gx_drop_list_pixelmap_set               | Ange pixelkarta till släpplista                                             |
| gx_drop_list_popup_set                  | Ange popup-fönster till listruta                                                |
| gx_generic_scroll_wheel_children_position | Placera underordnade i ett allmänt rullningshjul |
| gx_generic_scroll_wheel_create| Skapa en allmän widget för rullningshjul |
| gx_generic_scroll_wheel_draw | Rita allmän widget för rullningshjul |
| gx_generic_scroll_wheel_event_process| Bearbeta allmän rullningshjulshändelse|
| gx_generic_scroll_wheel_row_height_set| Ange radhöjd för allmänt rullningshjul|
| gx_generic_scroll_wheel_total_rows_set| Ange totalt antal rader för allmänt rullningshjul |
| gx_horizontal_list_children_position    | Placera underordnade widgetar i vågrät lista                          |
| gx_horizontal_list_create                | Skapa vågrät lista                                                |
| gx_horizontal_list_event_process        | Bearbeta händelse i vågrät lista                                      |
| gx_horizontal_list_page_index_set      | Tilldela vågrätt listsideindex                                     |
| gx_horizontal_list_selected_index_get  | Hämta det valda objektindexet                                           |
| gx_horizontal_list_selected_widget_get | Hämta den valda objektwidgeten                                          |
| gx_horizontal_list_selected_set         | Ange det valda objektet                                                 |
| gx_horizontal_list_total_columns_set   | Ändra antalet listkolumner när de har skapats                          |
| gx_horizontal_scrollbar_create           | Skapa vågrät rullningslist                                           |
| gx_icon_button_create                    | Knappen Skapa ikon                                                    |
| gx_icon_button_draw                      | Knappen Rita en ikon                                                   |
| gx_icon_button_pixelmap_set             | Knappen Ange pixelkarta i ikon                                           |
| gx_icon_background_draw                  | Bakgrund för ikonen Rita                                                  |
| gx_icon_create                            | Ikonen Skapa                                                           |
| gx_icon_draw                              | Ikonen Rita                                                             |
| gx_icon_event_process                    | Ikon för händelsebearbetningsfunktion                                        |
| gx_icon_pixelmap_set                     | Ange pixelkarta för ikon                                                 |
| gx_image_reader_create                   | Skapa bildläsarmodulinstans                                   |
| gx_image_reader_palette_set             | Definiera bildläsarpalett                                           |
| gx_image_reader_start                    | Starta dekomprimerings- och konverteringsprocessen                           |
| gx_line_chart_axis_draw                 | Rita linjediagram x,y-axel                                              |
| gx_line_chart_create                     | Skapa GX_LINE_CHART instans                                       |
| gx_line_chart_data_draw                 | Rita linjediagrammets datalinje                                             |
| gx_line_chart_draw                       | Standardritning av linjediagram                                            |
| gx_line_chart_update                     | Tvinga uppdatering av linjediagramdata                                       |
| gx_line_chart_y_scale_calculate        | Beräkna skalan för y-axelns datavärden till pixelkoordinater.           |
| gx_menu_create                            | Menyn Skapa                                                           |
| gx_menu_draw                              | Menyn Rita                                                             |
| gx_menu_event_process                     | Processmenyhändelse                                                    |
| gx_menu_insert                                | Infoga ett nytt objekt                                                               |
| gx_menu_remove                                | Ta bort ett objekt                                                                  |
| gx_menu_text_draw                            | Rita menytext                                                                  |
| gx_menu_text_offset_set                     | Ange förskjutning i menytext                                                       |
| gx_multi_line_text_button_create           | Knappen Skapa flerradstext                                                   |
| gx_multi_line_text_button_draw             | Knappen Rita flerradstext                                                     |
| gx_multi_line_text_button_event_process   | Ange teckensnitt för flerradstextknapp                                             |
| gx_multi_line_text_button_text_draw       | Textritning i ritning                                                 |
| gx_multi_line_text_button_text_id_set    | Ange systemsträng till textknapp                                                |
| gx_multi_line_text_button_text_set        | Tilldela användardefinierad sträng till textknappen (inaktuell)                          |
| gx_multi_line_text_button_text_set_ext   | Tilldela användardefinierad sträng till textknapp                                       |
| gx_multi_line_text_input_backspace         | Ta bort tecknet före textindatamarkörens position med flera rader               |
| gx_multi_line_text_input_buffer_get       | Hämtar buffertinformation för textinmatningswidget                               |
| gx_multi_line_text_input_buffer_clear     | Tar bort alla tecken från textinmatningsbufferten                               |
| gx_multi_line_text_input_char_insert      | Infoga utf8-formatsträng vid textindatamarkörposition med flera linjer (inaktuell) |
| gx_multi_line_text_input_char_insert_ext | Infoga UTF8-formatsträng vid textindatamarkörens position med flera linjer              |
| gx_multi_line_text_input_create            | Skapa textinmatning med flera linjer                                                    |
| gx_multi_line_text_input_cursor_pos_get  | Hämta markörpositionen för textinmatning med flera linjer                                  |
| gx_multi_line_text_input_delete            | Ta bort tecknet efter markörpositionen för textinmatning med flera rader                 |
| gx_multi_line_text_input_down_arrow       | Flytta markören för textinmatning med flera linjer till nästa rad                              |
| gx_multi_line_text_input_end               | Flytta markören för textinmatning med flera linjer till slutet av den aktuella raden                |
| gx_multi_line_text_input_event_process    | Bearbeta textinmatningstext med flera rad                                              |
| gx_multi_line_text_input_fill_color_set  | Ange fyllningsfärger för textinmatning med flera linjer                                       |
| gx_multi_line_text_input_home              | Flytta markören för textinmatning med flera linjer till början av den aktuella raden              |
| gx_multi_line_text_input_left_arrow       | Flytta en textinmatningsmarkör med flera linjer åt vänster med ett tecken                         |
| gx_multi_line_text_input_right_arrow      | Flytta textindatamarkören med flera linjer åt höger med ett tecken                        |
| gx_multi_line_text_input_style_add        | Lägga till flaggor för textformat med flera linjer                                                 |
| gx_multi_line_text_input_style_remove     | Ta bort flaggor för flerradstextformat                                              |
| gx_multi_line_text_input_style_set        | Tilldela flerradsflaggor för textformat                                              |
| gx_multi_line_text_input_text_color_set  | Tilldela textfärger för textinmatning med flera linjer                                    |
| gx_multi_line_text_input_text_select      | Välj textinmatningstext med flera linjer                                               |
| gx_multi_line_text_input_text_set         | Tilldela text till textinmatning med flera linjer (inaktuell)                               |
| gx_multi_line_text_input_text_set_ext          | Tilldela text till textinmatning med flera linjer                         |
| gx_multi_line_text_input_up_arrow               | Flytta markören för textinmatning med flera linjer till föregående rad       |
| gx_multi_line_text_view_create                   | Skapa flerradstextvy                                  |
| gx_multi_line_text_view_event_process           | Bearbeta textvisningshändelse med flera rad                           |
| gx_multi_line_text_view_font_set                | Ange teckensnitt som används i textvyn med flera linjer                        |
| gx_multi_line_text_view_line_space_set         | Ange radutrymme för flerradsvy                          |
| gx_multi_line_text_view_scroll_info_get        | Hämta information om bläddring i flerradsvy                         |
| gx_multi_line_text_view_text_color_set         | Ange textfärg i textvyn med flera linjer                       |
| gx_multi_line_text_view_text_id_set            | Ange systemets textsträng i textvyn med flera linjer               |
| gx_multi_line_text_view_text_set                | Ange användardefinierad sträng till flerradig textvy (inaktuell) |
| gx_multi_line_text_view_text_set_ext           | Ange användardefinierad sträng till flerradstextvy              |
| gx_multi_line_text_view_whitespace_set          | Ange tomt utrymme för flerradstextvy                          |
| gx_numeric_pixelmap_prompt_create                 | Skapa en fråga för numerisk pixelkarta                               |
| gx_numeric_pixelmap_prompt_format_ function_set | Funktionen Åsidosätt format i fråga om numerisk pixelkarta          |
| gx_numeric_pixelmap_prompt_value_set             | Ange numeriskt promptvärde                                     |
| gx_numeric_prompt_create                           | Skapa numerisk prompt                                        |
| gx_numeric_prompt_format_function_set            | Funktionen Åsidosätt format för numerisk prompt                   |
| gx_numeric_prompt_value_set                       | Ange numeriskt promptvärde                                     |
| gx_numeric_scroll_wheel_create                    | Skapa en widget för numeriska rullningshjul                           |
| gx_numeric_scroll_wheel_range_set                | Tilldela värdeintervall för rullningshjul                              |
| gx_pixelmap_button_create                          | Knappen Skapa pixelkarta                                       |
| gx_pixelmap_button_draw                            | Knappen Rita pixelkarta                                         |
| gx_pixelmap_button_event_process                  | Bildpunktskarta för händelsebearbetning                             |
| gx_pixelmap_button_pixelmap_set                   | Knappen Ange pixelkarta i pixelkarta                              |
| gx_pixelmap_prompt_create                          | Uppmaning om att skapa pixelkarta                                       |
| gx_pixelmap_prompt_draw                            | Fråga om att rita pixelkarta                                         |
| gx_pixelmap_prompt_pixelmap_set                   | Ange pixelkarta i pixelkarta                              |
| gx_pixelmap_slider_create                          | Skapa skjutreglage för pixelkarta                                       |
| gx_pixelmap_slider_draw                            | Skjutreglaget Rita pixelkarta                                         |
| gx_pixelmap_slider_event_process        | Bildpunktskarta för händelsebearbetning av skjutreglage       |
| gx_pixelmap_slider_pixelmap_set         | Ange pixelkarta i skjutreglaget för pixelkarta        |
| gx_progress_bar_background_draw         | Bakgrund av förloppsfältet Rita           |
| gx_progress_bar_create                   | Skapa en förloppsstapel                  |
| gx_progress_bar_draw                     | Rita en förloppsstapel                    |
| gx_progress_bar_event_process           | Bearbeta en förloppshändelse           |
| gx_progress_bar_font_set                | Ange teckensnitt för förloppsfältets text          |
| gx_progress_bar_info_set                | Ange informationsstruktur för förloppsfältet |
| gx_progress_bar_pixelmap_set            | Ange pixelkarta som används för att rita förloppsstapeln |
| gx_progress_bar_range_set               | Ange förloppsfältets värdeintervall        |
| gx_progress_bar_text_color_set         | Ange textfärg för förloppsfältet            |
| gx_progress_bar_text_draw               | Rita förloppsfälttext                 |
| gx_progress_bar_value_set               | Ange värde för förloppsfältet                 |
| gx_prompt_create                          | Skapa prompt                          |
| gx_prompt_draw                            | Draw prompt (Rita fråga)                            |
| gx_prompt_event_process                   | Händelse för processuppfråga                   |
| gx_prompt_font_set                       | Ange teckensnitt för prompt                        |
| gx_prompt_text_color_set                | Ange textfärg för prompt                  |
| gx_prompt_text_draw                      | Textritning i promptritning    |
| gx_prompt_text_get                       | Hämta prompttext (inaktuell)           |
| gx_prompt_text_get_ext                  | Hämta prompttext                        |
| gx_prompt_text_id_set                   | Ange prompt med systemtextsträng     |
| gx_prompt_text_set                       | Ange prompttext (inaktuell)           |
| gx_prompt_text_set_ext                  | Ange prompttext                        |
| gx_radial_progress_bar_anchor_set      | Ange startvinkel                     |
| gx_radial_progress_bar_background_draw | Rita bakgrund för radiell förloppsstapel    |
| gx_radial_progress_bar_create           | Skapa en radiell förloppsstapel           |
| gx_radial_progress_bar_draw             | Rita en radiell förloppsstapel             |
| gx_radial_progress_bar_event_process   | Förloppshändelse för processradiell förlopp      |
| gx_radial_progress_bar_font_set        | Ange teckensnitt för radiell förloppsfält           |
| gx_radial_progress_bar_info_set        | Ange information om radiell förloppsfält    |
| gx_radial_progress_bar_text_color_set | Ange textfärg för radiell förloppsstapel     |
| gx_radial_progress_bar_text_draw       | Rita radiell förloppsfälttext          |
| gx_radial_progress_bar_value_set       | Ange värde för radiell förloppsstapel          |
| gx_radio_button_create                   | Alternativknappen Skapa                    |
| gx_radio_button_draw                     | Alternativknappen Rita                      |
| gx_radio_button_pixelmap_set            | Ställ in pixelkarta i alternativknappen           |
| gx_radial_slider_anchor_angles_set     | Ange lista över vinkel för radiellt skjutreglage    |
| gx_radial_slider_angle_set              | Ange vinkel för radiellt skjutreglage                |
| gx_radial_slider_animation_set          | Ange information om animering av radiell skjutreglage       |
| gx_radial_slider_animation_start               | Ange vinkel för radiellt skjutreglage med animering                      |
| gx_radial_slider_create                         | Skapa ett radiellt skjutreglage                                      |
| gx_radial_slider_draw                           | Rita ett radiellt skjutreglage                                        |
| gx_radial_slider_event_process                 | Bearbeta en radiell skjutreglagehändelse                               |
| gx_radial_slider_info_get                      | Hämta pekare för radiell skjutreglageinformation                  |
| gx_radial_slider_info_set                      | Ange information om radiellt skjutreglage                               |
| gx_radial_slider_pixelmap_set                  | Ange pixelkartor för radiellt skjutreglage                                 |
| gx_rich_text_view_create                       | Skapa en RTF-vy                                     |
| gx_rich_text_view_draw                         | Rita RTF-vy                                         |
| gx_rich_text_view_set_fonts                    | Ange teckensnitt för RTF-vy                                    |
| gx_rich_text_view_text_draw                    | Rita rtf-textvisningstext                                    |
| gx_screen_stack_create                          | Skapa GUIX-skärmstackens kontrollblock och minnesområde. |
| gx_screen_stack_pop                             | Öppna den översta skärmen från skärmstacken.                   |
| gx_screen_stack_push                            | Push-skicka den aktuella skärmen till skärmstacken.                |
| gx_screen_stack_reset                           | Återställa skärmstacken                                      |
| gx_scroll_wheel_create                          | Skapa widget för basrullningshjul                             |
| gx_scroll_wheel_event_process                  | Bearbetning av rullningshjulshändelse                               |
| gx_scroll_wheel_gradient_alpha_set            | Ändra överläggstoning för rullningshjul                        |
| gx_scroll_wheel_row_height_set                | Tilldela höjd för rullningshjulsrad                              |
| gx_scroll_wheel_selected_background_set       | Tilldela bakgrundsbild för vald rad                    |
| gx_scroll_wheel_selected_get                   | Hämta valt radindex                                 |
| gx_scroll_wheel_selected_set                   | Tilldela valt radindex                                   |
| gx_scroll_wheel_speed_set                      | Tilldela rullningshastighet                                      |
| gx_scroll_wheel_total_rows_set                | Tilldela totalt antal tillgängliga rader                       |
| gx_scrollbar_draw                                | Rita rullningslist                                              |
| gx_scrollbar_event_process                      | Bearbeta rullningslistshändelse                                     |
| gx_scrollbar_limit_check                        | Kontrollera rullningslistgränsen                                       |
| gx_scrollbar_reset                               | Återställ rullningslist                                             |
| gx_scrollbar_value_set                          | Tilldela rullningslistvärde                                      |
| gx_single_line_text_input_backspace           | Hantera blankstegstecken                                  |
| gx_single_line_text_input_buffer_clear       | Rensa teckenbufferten                                  |
| gx_single_line_text_input_buffer_get         | Hämta buffert pekare                                     |
| gx_single_line_text_input_character_delete   | Ta bort tecken                                            |
| gx_single_line_text_input_character_insert   | Infoga tecken                                            |
| gx_single_line_text_input_create              | Skapa textinmatning med en rad                               |
| gx_single_line_text_input_draw                | Rita enradswidget för textinmatning                          |
| gx_single_line_text_input_draw_position_get | Hämta startpositionen för text rita                           |
| gx_single_line_text_input_end                 | Flytta markören till slutet                                          |
| gx_single_line_text_input_event_process      | Bearbetning av textinmatningshändelse                                 |
| gx_single_line_text_input_fill_color_set    | Ange fyllningsfärger för textinmatning på en rad                  |
| gx_single_line_text_input_home                | Flytta markören till startsidan                                         |
| gx_single_line_text_input_left_arrow         | Hantera vänsterpil                                       |
| gx_single_line_text_input_position_get       | Hämta markörposition                                         |
| gx_single_line_text_input_right_arrow        | Hantera högerpil                                      |
| gx_single_line_text_input_style_add          | Lägga till formatflaggor                                             |
| gx_single_line_text_input_style_remove       | Ta bort formatflaggor                                          |
| gx_single_line_text_input_style_set          | Tilldela formatflaggor                                          |
| gx_single_line_text_input_text_color_set  | Ange textfärger för textinmatning med en rad                      |
| gx_single_line_text_input_text_select     | Välj textinmatningstext på en rad                              |
| gx_single_line_text_input_text_set        | Ange textinmatningstext på en rad (inaktuell)                    |
| gx_single_line_text_input_text_set_ext    | Ange textinmatningstext på en rad                                 |
| gx_slider_create                          | Skapa skjutreglage                                                   |
| gx_slider_draw                            | Dra skjutreglage                                                     |
| gx_slider_event_process                   | Händelse för processreglage                                            |
| gx_slider_info_set                        | Ange informationsblock för skjutreglage                                    |
| gx_slider_needle_draw                     | Dra skjutreglagets nål                                              |
| gx_slider_needle_position_get             | Hämta skjutreglagets nålposition                                      |
| gx_slider_tickmarks_draw                  | Bockmarkeringar för skjutreglage                                           |
| gx_slider_travel_get                      | Hämta skjutreglagets färd                                               |
| gx_slider_value_calculate                 | Beräkna skjutreglagevärde                                          |
| gx_slider_value_set                       | Ange skjutreglagevärde                                                |
| gx_sprite_create                          | Skapa GX_SPRITE widget                                         |
| gx_sprite_current_frame_set               | Tilldela aktuell visningsram för din widget                  |
| gx_sprite_frame_list_set                  | Tilldela eller ändra en listruta                            |
| gx_sprite_start                           | Starta en sekvens för et-sekvenser                                         |
| gx_sprite_stop                            | Stoppa en sekvens för et-sekvenser                                          |
| gx_string_scroll_wheel_create             | Skapa `GX_STRING_SCROLL_WHEEL` widget                          |
| gx_string_scroll_wheel_event_process      | Händelse för processsträngens rullningshjul                               |
| gx_string_scroll_wheel_string_id_list_set | Tilldela matris med sträng-ID:er                                      |
| gx_string_scroll_wheel_string_list_set    | Ändra strängmatris som visas                                   |
| gx_string_scroll_wheel_text_get           | Hämta text för rullningshjulsrad                              |
| gx_studio_widget_create                   | Skapa widget som definierats i Studio                             |
| gx_studio_named_widget_create             | Skapa skärm definierad i Studio                             |
| gx_studio_display_configure               | Skapa och initiera `GX_DISPLAY` , `GX_CANVAS` och `GX_WINDOW_ROOT` |
| gx_system_active_language_set             | Tilldela aktivt språk-ID                                       |
| gx_system_canvas_refresh                  | Tvinga fram uppdatering (ritning) av grovjobbade arbetsyta                       |
| gx_system_dirty_mark                      | Markera område som är grovt                                                 |
| gx_system_dirty_partial_add               | Markera partiellt område som är grovt                                         |
| gx_system_draw_context_get                | Hämta ritningskontext                                             |
| gx_system_event_fold                      | Foldevent                                                       |
| gx_system_event_send                      | Skicka händelse                                                      |
| gx_system_focus_claim                     | Anspråksfokus                                                     |
| gx_system_initialize                      | Initiera GUIX                                                 |
| gx_system_language_table_get              | Hämta språktabell                                         |
| gx_system_language_table_set              | Tilldela språktabell                                           |
| gx_system_memory_allocator_set            | Tilldela minnes allocator/de-allocator                            |
| gx_system_pen_configure                  | Ange pennkonfiguration                                  |
| gx_system_screen_stack_create           | Skapa skärmstackkontroll                            |
| gx_system_screen_stack_get              | Hämta pekare för skärmstack                         |
| gx_system_screen_stack_pop              | Popup-översta skärmen från skärmstack                       |
| gx_system_screen_stack_push             | Skicka den angivna skärmen till skärmstacken              |
| gx_system_screen_stack_reset            | Återställa skärmstacken                                 |
| gx_system_scroll_appearance_get         | Hämta rullningsutseende                                  |
| gx_system_scroll_appearance_set         | Ange rullningsutseende                                  |
| gx_system_start                           | Starta GUIX                                             |
| gx_system_string_get                     | Hämta sträng                                             |
| gx_system_string_table_get              | Hämta strängtabell                                       |
| gx_system_string_table_set              | Ange strängtabell                                       |
| gx_system_string_width_get              | Hämta strängbredd (inaktuell)                          |
| gx_system_string_width_get_ext         | Hämta strängbredd                                       |
| gx_system_theme_install                  | Installera teckensnitts-/färg-/pixelkarta-tabeller                     |
| gx_system_timer_start                    | Starttimer                                            |
| gx_system_timer_stop                     | Stopptimer                                             |
| gx_system_version_string_get            | Hämta VERSIONSsträngen för GUIX-biblioteket (inaktuell)      |
| gx_system_version_string_get_ext       | Hämta versionssträngen för GUIX-biblioteket                   |
| gx_system_widget_find                    | Hitta widget                                            |
| gx_text_button_create                    | Knappen Skapa text                                     |
| gx_text_button_draw                      | Knappen Rita text                                       |
| gx_text_button_event_process             | Bearbeta textknappshändelse                              |
| gx_text_button_font_set                 | Ange teckensnitt för textknappen                               |
| gx_text_button_text_color_set          | Ange textknappfärg                                  |
| gx_text_button_text_draw                | Textritning i knappritning                 |
| gx_text_button_text_get                 | Hämta text som används i textknappen (inaktuell)              |
| gx_text_button_text_get_ext            | Hämta text som används i textknappen                           |
| gx_text_button_text_id_set             | Tilldela systemsträngen till textknappen                    |
| gx_text_button_text_set                 | Tilldela användardefinierad sträng till textknapp (inaktuell) |
| gx_text_button_text_set_ext            | Tilldela användardefinierad sträng till textknapp              |
| gx_text_scroll_wheel_callback_set      | Tilldela återanrop för stränghämtning (inaktuell)          |
| gx_text_scroll_wheel_callback_set_ext | Tilldela återanrop för stränghämtning                       |
| gx_text_scroll_wheel_create             | Skapa rullningshjul för bastext                          |
| gx_text_scroll_wheel_draw               | Funktion för att rita textrullningshjul                  |
| gx_text_scroll_wheel_event_process      | Processhändelse för textrullningshjul                        |
| gx_text_scroll_wheel_font_set          | Tilldela teckensnitt för textrullningshjul                         |
| gx_text_scroll_wheel_text_color_set   | Tilldela textfärger för textrullningshjul                   |
| gx_tree_view_create                    | Skapa en trädvy                          |
| gx_tree_view_draw                      | Rita trädvy                              |
| gx_tree_view_event_process            | Processträdvyhändelse                     |
| gx_tree-view_indentation_set           | Ange indrag för trädvy                   |
| gx_tree_view_position                  | Placera trädvyobjekt                    |
| gx_tree_view_root_line_color_set    | Ange rotlinjefärg för trädvy               |
| gx_tree_view_root_pixelmap_set       | Ange trädvyns rot pixelkartor                |
| gx_tree_view_selected_get             | Hämta valt objekt                      |
| gx_tree_view_selected_set             | Ange valt objekt                           |
| gx_utility_canvas_to_bmp              | Konvertera arbetsyteminne till format för bitmapp      |
| gx_utility_circle_point_get           | Beräkningspunkt på en cirkel               |
| gx_utility_gradient_create             | Skapa en toningspunktskarta                  |
| gx_utility_gradient_delete              | Ta bort en tonad pixelkarta                  |
| gx_utility_ltoa                         | Konvertera långt heltal till ASCII               |
| gx_utility_math_acos                   | Cosinus för beräknings arc                          |
| gx_utility_math_asin                   | Beräknings arc sinus                             |
| gx_utility_math_cos                    | Beräknings cosinus                              |
| gx_utility_math_sin                    | Beräknings sinus                                |
| gx_utility_math_sqrt                   | Kvadratrot för beräkning                         |
| gx_utility_bidi_paragraph_reorder         | Ändra ordningen på BiDi-text till dess visningsordning|
| gx_utility_bidi_resolved_text_info_delete | Ta bort ordnad BiDi-text               |
| gx_utility_pixelmap_resize             | Ändra storlek på pixelkarta                             |
| gx_utility_pixelmap_rotate             | Rotera pixelkarta efter godtycklig vinkel          |
| gx_utility_pixelmap_simple_rotate      | Rotera pixelkarta med 90, 180, 270 grader     |
| gx_utility_rectangle_center            | Center-rektangel inuti en annan rektangel   |
| gx_utility_rectangle_center_find      | Hitta mitten av rektangeln                    |
| gx_utility_rectangle_combine           | Kombinera två rektanglar till den första           |
| gx_utility_rectangle_compare           | Jämföra två rektanglar                      |
| gx_utility_rectangle_define            | Definiera rektangel                            |
| gx_utility_rectangle_resize            | Ändra storlek på rektangel                            |
| gx_utility_rectangle_overlap_detect   | Identifiera överlappning av rektanglar                |
| gx_utility_rectangle_point_detect     | Identifiera om punkten finns i rektangeln        |
| gx_utility_rectangle_shift             | Skift-rektangel                             |
| gx_utility_string_to_alphamap         | Rendera textsträng till alfakarta (inaktuell) |
| gx_utility_string_to_alphamap_ext    | Rendera textsträng till alfakarta              |
| gx_vertical_list_children_position    | Placera underordnade i lodrät lista          |
| gx_vertical_list_create                | Skapa lodrät lista                        |
| gx_vertical_list_event_process        | Bearbeta lodrät lista-händelse                 |
| gx_vertical_list_selected_index_get  | Hämta valt objektindex                     |
| gx_vertical_list_selected_widget_get | Hämta vald widget                         |
| gx_vertical_list_selected_set         | Ange post i lodrät lista                  |
| gx_vertical_list_total_rows_set      | Ändra antalet listrader efter skapandet   |
| gx_vertical_scrollbar_create           | Skapa lodrät rullningslist                   |
| gx_widget_allocate                      | Allokera en widget dynamiskt               |
| gx_widget_attach                        | Koppla widget till överordnad                     |
| gx_widget_background_draw              | Bakgrund för rita widget                      |
| gx_widget_back_attach                  | Koppla widgeten i bakåt                       |
| gx_widget_back_move                    | Flytta widgeten till bakåt                         |
| gx_widget_block_move                   | Flytta block med bildpunkter                        |
| gx_widget_border_draw                  | Rita widgetkantlinje                          |
| gx_widget_border_style_set            | Ange kantformat för widget                     |
| gx_widget_border_width_get            | Ange bredd på widgetens kantlinje                     |
| gx_widget_canvas_get               | Hämta widgetarbetsyta                                                         |
| gx_widget_child_detect             | Identifiera widget underordnad                                                       |
| gx_widget_children_draw            | Underordnade rita widget                                                      |
| gx_widget_client_get               | Hämta widgetklientområde                                                    |
| gx_widget_color_get                | Matcha färg-ID till färgvärde för en synlig widget                      |
| gx_widget_create                    | Skapa widget                                                             |
| gx_widget_created_test             | Testa om widgeten har skapats                                                    |
| gx_widget_delete                    | Ta bort widget                                                             |
| gx_widget_detach                    | Koppla från widget från överordnad                                                 |
| gx_widget_draw                      | Rita widget                                                               |
| gx_widget_draw_set                 | Ställ in rita-funktion för widget                                               |
| gx_widget_event_generate           | Generera widgethändelse                                                     |
| gx_widget_event_process            | Händelse för processwidget                                                      |
| gx_widget_event_process_set       | Ange händelsebearbetningsfunktion för widget                                   |
| gx_widget_event_to_parent         | Skicka händelse till widgetens överordnade                                             |
| gx_widget_fill_color_set          | Tilldela widgetfyllningsfärg                                                  |
| gx_widget_find                      | Hitta widget                                                               |
| gx_widget_first_child_get         | Returnera pekaren till det första underordnade                                             |
| gx_widget_focus_next               | Flytta indatafokus till nästa widget                                           |
| gx_widget_focus_previous           | Flytta indatafokus till föregående widget                                       |
| gx_widget_font_get                 | Matcha teckensnitts-ID till en teckensnittspekare för en synlig widget                    |
| gx_widget_free                      | Ledigt blockminne för widgetkontroll                                          |
| gx_widget_front_move               | Flytta widgeten framifrån                                                      |
| gx_widget_height_get               | Hämta widgethöjd                                                         |
| gx_widget_hide                      | Dölj widget                                                               |
| gx_widget_last_child_get          | Returnera pekaren till det sista underordnade                                              |
| gx_widget_next_sibling_get        | Gå tillbaka till nästa nivå på samma nivå                                            |
| gx_widget_parent_get               | Återgå pekare till överordnad widget                                           |
| gx_widget_pixelmap_get             | Matcha pixelkartans ID till en pixelkarta-pekare för en synlig widget            |
| gx_widget_previous_sibling_get    | Returnera pekaren till föregående på samma sätt                                        |
| gx_widget_resize                    | Ändra storlek på widget                                                             |
| gx_widget_shift                     | Skift-widget                                                              |
| gx_widget_show                      | Visa widget                                                               |
| gx_widget_status_add               | Lägg till widgetstatus                                                         |
| gx_widget_status_get               | Hämta widgetstatusflaggor                                              |
| gx_widget_status_remove            | Ta bort widgetstatus                                                      |
| gx_widget_string_get               | Hämta sträng som är associerad med sträng-ID för synlig widget (inaktuell) |
| gx_widget_string_get_ext          | Hämta sträng som är associerad med sträng-ID för synlig widget.             |
| gx_widget_status_test              | Status för testwidget                                                        |
| gx_widget_style_add                | Lägg till widgetformat                                                          |
| gx_widget_style_get                | Hämta flaggor för widgetformat                                               |
| gx_widget_style_remove             | Ta bort widgetformat                                                       |
| gx_widget_style_set                | Ange widgetformat                                                          |
| gx_widget_text_blend               | Rendera blandad text över widget (inaktuell)                              |
| gx_widget_text_blend_ext          | Rendera blandad text över widget                                           |
| gx_widget_text_draw                | Rendera text över widget (inaktuell)                                      |
| gx_widget_text_draw_ext           | Rendera text över widget                                            |
| gx_widget_text_id_draw            | Rendera text som identifierats av sträng-ID över widget                           |
| gx_widget_top_visible_child_find | Returnera pekaren till synligt understreck som ritas överst i Z-ordningen   |
| gx_widget_type_find                | Hitta widgettyp                                                          |
| gx_widget_width_get                | Hämta widgetbredd                                                          |
| gx_window_canvas_set               | Ange fönsterarbetsyta                                                         |
| gx_window_client_height_get       | Hämta fönsterklientens höjd                                                  |
| gx_window_client_scroll            | Rullningsfönsterklienter                                                     |
| gx_window_client_width_get        | Hämta fönsterklientbredd                                                   |
| gx_window_close                     | Avsluta körning av modalfönster                                          |
| gx_window_create                    | Fönstret Skapa                                                             |
| gx_window_draw                      | Fönstret Rita                                                               |
| gx_window_event_process            | Processfönsterhändelse                                                      |
| gx_window_execute                   | Körning av modal fönster                                                    |
| gx_window_root_create              | Fönstret Skapa rot                                                        |
| gx_window_root_delete              | Förstör rotfönstret                                                       |
| gx_window_root_event_process      | Bearbeta händelse för rotfönstret                                             |
| gx_window_root_find                | Hitta rotfönstret                                                          |
| gx_window_scroll_info_get         | Hämta information om fönsterrullning                                                    |
| gx_window_scrollbar_find           | Hitta rullningslisten för fönster                                                     |
| gx_window_wallpaper_get            | Hämta fönsterbakgrund                                                      |
| gx_window_wallpaper_set            | Ange fönsterbakgrund                                                      |

## <a name="gx_accordion_menu_create"></a>gx_accordion_menu_create

Skapa en avtalsmeny

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

### <a name="description"></a>Description

Den här tjänsten skapar en avtalsmeny som anges och bifogar överensstämmelsemenyn till den angivna överordnade widgeten. En dragspelsmeny är en expanderande/komprimerad menyvisningswidget. Den accepterar alla typer av widget som underordnade menyalternativ. Spelmenyer kan kapslas, vilket innebär att flera nivåer av menydjup kan skapas.

Om du vill infoga ett underordnat objekt i en widget för menyalternativ rekommenderar vi att du GX_MENU en widget som ett överordnat menyalternativ.

Tips för att skapa en avtalsmeny på en nivå:

1.  Skapa en avtalsmeny.

2.  Koppla GX_MENU typwidgetar till avtalsmenyn.

3.  Koppla underordnade widgetar till den överordnade GX_MENU typ. Den underordnade objekttypen kan vara vilken GUIX-widgettyp som helst.

Tips för att skapa en avtalsmeny på flera nivåer:

1.  Skapa en avtalsmeny.

2.  Koppla GX_MENU typwidgetar till avtalsmenyn.

3.  Koppla GX_ACCORDION_MENU typwidget till den överordnade GX_MENU-typen.

4.  Koppla menyalternativ till den överordnade GX_ACCORDION_MENU enligt beskrivningen i skapa en avtalsmeny på en nivå.

### <a name="parameters"></a>Parametrar

- **överensstämmelse** Pekare till kontrollblock för överspelningsmeny
- **namn** Namn på avtalsmenyn
- **överordnad** Pekare till överordnad widget
- **style** Widgetens format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **accordion_menu_id** Programdefinierat ID för avtalsmenyn
- **storlek** Storleken på avtalsmenyn

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Generering av en lyckad avtalsmeny
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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

Demoprogrammet är demo_guix_widget_types ingår i GUIX Studio-installationen och innehåller ett komplett exempel på hur du använder widgeten för överensstämmelsemeny.

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

Menyn Rita dragning

### <a name="prototype"></a>Prototyp

```C
VOID gx_accordion_menu_draw(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Description

Den här tjänsten ritar den angivna avtalsmenyn. Den här tjänsten anropas vanligtvis internt av GUIX-mekanismen för arbetsyteuppdatering, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade dragningsmenywidgetar.

### <a name="parameters"></a>Parametrar

- **överensstämmelse** Pekare till kontrollblock för överspelningsmeny

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Processspelarmenyhändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_accordion_menu_event_process(
    GX_ACCORDION_MENU *accordion, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna överensstämmelsemenyn. Den här tjänsten ska anropas som standardhändelsehanterare av eventuella anpassade funktioner för bearbetning av händelser på menyn.

Den här tjänsten hanterar GX_EVENT_PEN_DOWN och GX_EVENT_PEN_UP händelser för att expandera/dölja ett menyalternativ.

### <a name="parameters"></a>Parametrar

- **överensstämmelse** Pekare till kontrollblock för överspelningsmeny
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **händelseprocess GX_SUCCESS** (0x00) Lyckad överensstämmelsemeny
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Placera menyalternativ

### <a name="prototype"></a>Prototyp

```C
UINT gx_accordion_menu_position(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Description

Den här tjänsten placerar menyalternativen för fattningsmenyn. Den här funktionen anropas vanligtvis internt när sedelmenyn blir synlig. Om du vill infoga/ta bort objekt till/från en brytningsmeny eller ändra expandera formaten för det underordnade objektet, ska den här funktionen anropas för att flytta de underordnade objekten.

### <a name="parameters"></a>Parametrar

- **överensstämmelse** Pekare till kontrollblock för överspelningsmeny

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad överensstämmelsemenyposition
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Ge arbetsytans minne till en animeringskontrollant

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_canvas_define(
    GX_ANIMATION *animation, 
    GX_CANVAS *canvas);
```

### <a name="description"></a>Description

Den här tjänsten tillhandahåller en minnesarbetsyta till en animeringskontrollant som används för att implementera animeringssekvensen. Den här tillhandahållna arbetsytan bör vara tillräckligt stor för att rymma animeringsmålwidgeten.

När en animeringsarbetsyta definieras ritas målwidgeten en gång till den här animeringsarbetsytan och skärmens dra-eller-toning-effekt uppnås genom att ändra arbetsytans förskjutning och/eller arbetsytans alfavärde. När maskinvarustöd för flera grafiklager tillhandahålls kan en animeringsarbetsyta som  är bunden till ett maskinvarugrafiköverläggslager avsevärt förbättra prestandan för animeringar med dra och toning.

Animeringshanteraren kräver en animeringsarbetsyta för att köra animeringstyperna tona in och tona ut om den körs på ett färgdjup som är mindre än 16 bpp.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering
- **arbetsyta** Minnesarbetsyta som används för att implementera översättningsanimeringen.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Animeringsarbetsyta har definierats
- **GX_INVALID_STATUS** (0x10) Ogiltig animeringsstatus
- **GX_INVALID_MEMORY_SIZE** (0x29) Det angivna minnesblocket är inte tillräckligt stort för att skapa arbetsytan
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

- gx_animation_create
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_drag_enable
- gx_animation_landing_speed_set
- gx_animation_start
- gx_animation_stop

## <a name="gx_animation_create"></a>gx_animation_create

Skapa en animeringskontrollant

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_create(GX_ANIMATION *animation);
```

### <a name="description"></a>Description

Den här tjänsten skapar en animeringskontrollant. Kontrollanten initieras till inaktivt tillstånd. Man kan inte starta en animering om den inte är i inaktivt tillstånd. Den GX_ANIMATION kan hämtas med hjälp av gx_system_animation_get(), eller så kan det vara ett statiskt definierat kontrollblock.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering


### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Animeringskontrollanten har skapats
- **GX_ALREADY_CREATED** (0x13) Kontrollblock som redan har initierats
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

/* Initialize the control block */

if (animation)
{
    status = gx_animation_create(animation);
}

/* If status is GX_SUCCESS the new animation controller was successfully created and initialized. */

```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_delete"></a>gx_animation_delete

Ta bort en eller flera animeringskontrollanter

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_delete(GX_ANIMATION *animation, GX_WIDGET *parent);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en animeringssekvens om pekaren för indataanimering har angetts. Annars tas alla animeringar som tillhör den angivna överordnade widgeten bort.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering
- **överordnad** Pekare till överordnad widget


### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Animeringskontrollanter har tagits bort
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

- Ta bort en animering

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

if (animation)
{
    /* Create an animation.  */
    gx_animation_create(animation);

    /* Delete an animation.  */
    status = gx_animation_delete(animation, GX_NULL);
}

/* If status is GX_SUCCESS the animation controller was successfully deleted and returned back to system animation pool. */

```

- Ta bort flera animeringar
```C

status = gx_animation_delete(GX_NULL, parent);

/* If status is GX_SUCCESS all the animations belong to the parent were successfully deleted. */

```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define,
- gx_animation_create
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set,
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_disable"></a>gx_animation_drag_disable

Inaktivera skärm dra animering hook

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_drag_disable(
    GX_ANIMATION *animation, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Description

Den här tjänsten tar bort proceduren dra animeringen från widgetens standardhändelseprocessfunktion och stoppar animeringssekvensen. Proceduren dra animering hook hanterar händelser för en skärm dra animering.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering
- **widget** Pekare till widgetkontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_drag_enable
- gx_animation_landing_speed_set
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_enable"></a>gx_animation_drag_enable

Aktivera skärm dra animering hook

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_drag_enable(
    GX_ANIMATION *animation,
    GX_WIDGET *widget, 
    GX_ANIMATION_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten anger den internt definierade funktionen för att dra animeringshändelsen som en hook-procedur för en widgets standardhändelseprocessfunktion. Funktionen för att dra animeringshändelser hanterar händelser för en animering som drar skärmen.

Proceduren dra hook på skärmen blir standardhanterare för pennindatahändelser som skickas till målwidgeten. Den ursprungliga widgetens händelsebearbetningsfunktion anropas i seriekedja efter kontroll av händelsetyper med skärmfördrång.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering
- **widget** Pekare till widgetkontrollblock
- **info** Animeringsinformation

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_STATUS** (0x26) Ogiltig animeringsstatus
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde
- **GX_INVALID_WIDGET** (0x12) Bildskärmslista har inte angetts

### <a name="allowed-from"></a>Tillåts från

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

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_landing_speed_set
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_landing_speed_set"></a>gx_animation_landing_speed_set

Ange landningshastighet för animering med skärm dra

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_landing_speed_set(
    GX_ANIMATION *animation, 
    USHORT shift_per_step);
```

### <a name="description"></a>Description

Den här tjänsten anger landningshastigheten för animering med skärm dra.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering
- **shift_per_step** Skiftavstånd för varje steg

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_VALUE** (0x22) Ogiltig parameter

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Set landing speed of “my_animation” to 20. */
status = gx_animation_landing_peed_set(&my_animation, 20);

/* If status is GX_SUCCESS the landing speed is successfully set to 20. */
```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_slide_disable
- gx_animation_slide_enable
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_start"></a>gx_animation_start

Starta en timerdriven animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_start(
    GX_ANIMATION *animation, 
    GX_ANIMATION_INFO *params);
```

### <a name="description"></a>Description

Den här tjänsten initierar en animeringssekvens med hjälp av en tidigare skapad animeringsinstans och en ny uppsättning animeringsparametrar. Den här funktionen gör en lokal kopia av parametrarna, vilket innebär att parameterstrukturen inte behöver definieras statiskt.

Den GX_ANIMATION kontrollstrukturen kan definieras statiskt av programmet eller hämtas med hjälp av API:gx_system_animation_get().

Strukturen GX_ANIMATION_INFO definierar parametrarna för animeringen som ska köras. En fullständig beskrivning av den här strukturen och innebörden av varje fält finns i avsnittet GUIX-animeringskomponent i kapitel 3 i den här handboken.

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering
- **params** Pekare till parameterstruktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_VALUE** (0x22) Ogiltig parameter
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltigt animeringsmål
- **GX_INVALID_STATUS** (0x26) Ogiltig animeringsstatus
- **GX_INVALID_CANVAS** (0x20) Ogiltig animeringsarbetsyta

### <a name="allowed-from"></a>Tillåts från

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

Stoppa en aktiv timerdriven animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_animation_stop(GX_ANIMATION *animation);
```

### <a name="description"></a>Description

Stoppa en animering som startats tidigare. Om block pekaren för animeringskontroll allokerades med gx_system_animation_get kan programmet använda kontrollblocket igen eller returnera det till systempoolen med hjälp av gx_system_animation_free().

### <a name="parameters"></a>Parametrar

- **animering** Pekare till kontrollblock för animering

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ogiltig pekare GX_PTR_ERROR (0x07)
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_STATUS** (0x26) Ogiltig kontrollantstatus

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_ANIMATION animation;

status = gx_animation_stop(&animation);

/* If status is GX_SUCCESS the animation is stopped */

```

### <a name="see-also"></a>Se även

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_drag_enable
- gx_animation_start
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_binres_language_count_get"></a>gx_binres_language_count_get

Returnera antalet språk som finns i binära resursdata

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_count_get(
    GX_UBYTE *root_address, 
    GX_VALUE *returned_count);
```

### <a name="description"></a>Description

Den här tjänsten parsar ett datahuvud för binär resurs för att returnera antalet språk som finns i binära data. Detta är användbart för program som måste visa en urvalslista för användaren så att användaren kan välja bland olika språk.

### <a name="parameters"></a>Parametrar

- **root_address** Adress för binära resursdata i minnet
- **return_count** Plats för att lagra returnerat språkantal

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_FORMAT** (0x24) Ogiltig binär resurs
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Läsa in information om språktabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_info_load(
    GX_UBYTE *root_address, 
    GX_LANGUAGE_HEDAER *put_info);
```

### <a name="description"></a>Description

Den här tjänsten parsar en binär resursdatablob för att fylla i en matris med GX_LANGUAGE_HEADER-strukturer, vilket informerar tillämpningen av språknamnen och strängtabellstorleken för varje språk som finns i binärdata. Programmet bör först anropa gx_binres_language_count_get() för att fastställa antalet språk i binära data och försäkra sig om att put_info-pekaren som skickas till den här funktionen pekar på en matris med language_count GX_LANGUAGE_HEADER strukturer.

Den här tjänsten används av programmet för att vid körning fastställa innehållet i ett binärt resursdata segment.

Strukturen GX_LANGUAGE_HEADER definieras som:

```c
typedef struct GX_LANGUAGE_HEADER_STRUCT{
    USHORT gx_language_header_magic_number;
    USHORT gx_language_header_index;
    UCHAR gx_language_header_name[GX_LANGUAGE_HEADER_NAME_SIZE];
    ULONG  gx_language_header_data_size;
} GX_LANGUAGE_HEADER;
```

- Fältet *magic_number* används för intern validering av binärresursdataformatet.
- Fältet *header_index* anger i vilken ordning språken definieras i binärdata.
- Fältet *header_name* innehåller språknamnet.
- Fältet *header_data_size* innehåller datastorleken för språksträngtabellen.

### <a name="parameters"></a>Parametrar

- **root_address** Adress för binära resursdata i minnet
- **put_info** Pekare till matris med GX_LANGUAGE_HEADER strukturer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_FORMAT** (0x24) Ogiltig binär resurs
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Resurs för inläsningsspråktabell (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_table_load(
    GX_UBYTE *root_address, 
    GX_UBYTE **returned_language_table);
```

### <a name="description"></a>Description

Med det här inaktuella API:et kan program läsa in strängtabelldata från äldre (före version 5.6) binära resursdatafiler.

Nya program bör använda gx_binres_language_table_load_ext().

Den här tjänsten skapar en språktabellstruktur som innehåller pekare till tabellresurser, de genererade datastrukturerna pekar på resursdata "på plats". Resursdata kopieras inte. Resursdata måste placeras på en allmän minnesplats för åtkomst och basadressen för den här minnesplatsen skickas till det här API:et.

Den här tjänsten kräver ett allokerat minnesblock för körning som är tillräckligt stort för att rymma språktabellstrukturen, och därför måste gx_system_memory_allocator_set-API:et anropas en gång innan den här tjänsten begärs.

Den returnerade språktabellen definierar en eller flera strängtabeller, varje strängtabell som innehåller pekare till strängresurser i resursdataminnet.

### <a name="parameters"></a>Parametrar

- **root_address** Adress för binära resursdata i minnet
- **returnerade _language_table** Pekare till inläst språktabell

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_FORMAT** (0x24) Ogiltig binär resurs
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) Minnes allocator eller kostnadsfri funktion har inte definierats

### <a name="allowed-from"></a>Tillåts från

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

Läsa in resurs för språktabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_language_table_load_ext(
    GX_UBYTE *root_address, 
    GX_STRING **returned_language_table);
```

### <a name="description"></a>Description

Den här tjänsten skapar en språktabellstruktur som innehåller pekare till tabellresurser, de genererade datastrukturerna pekar på resursdata "på plats". Resursdata kopieras inte. Resursdata måste placeras på en allmän minnesplats för åtkomst och basadressen för den här minnesplatsen skickas till det här API:et.

Den här tjänsten kräver ett allokerat minnesblock för körning som är tillräckligt stort för att rymma språktabellstrukturen, och därför måste gx_system_memory_allocator_set-API:et anropas en gång innan den här tjänsten begärs.

Den returnerade språktabellen definierar en eller flera strängtabeller, varje strängtabell som innehåller pekare till strängresurser i resursdataminnet.

### <a name="parameters"></a>Parametrar

- **root_address** Adress för binära resursdata i minnet
- **returnerade _language_table** Pekare till inläst språktabell

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_FORMAT** (0x24) Ogiltig binär resurs
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) Minnesbefriare eller kostnadsfri funktion har inte definierats

### <a name="allowed-from"></a>Tillåts från

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

Läsa in temaresurs

### <a name="prototype"></a>Prototyp

```C
UINT gx_binres_theme_load(
    GX_UBYTE *root_address, 
    INT theme_id, GX_THEME **returned_theme);
```

### <a name="description"></a>Description

Den här tjänsten skapar en GX_THEME struktur som innehåller pekare till resurstabellerna för det begärda temat. De genererade datastrukturerna pekar på resursdata "på plats", utan kopierar inte resursdata. Resursdata måste placeras på en allmän minnesplats för åtkomst och basadressen för den här minnesplatsen skickas till det här API:et.

Den här tjänsten kräver ett allokerat minnesblock för körning som är tillräckligt stort för att innehålla tematabellstrukturen, och därför måste gx_system_memory_allocator_set-API:et anropas en gång innan den här tjänsten begärs.

### <a name="parameters"></a>Parametrar

- **root_address** Adress för binära resursdata i minnet
- **theme_id** Identifieraren för temat
- **returned_theme** Pekare till inläst tema

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades
- **GX_INVALID_FORMAT** (0x24) Ogiltig binär resurs
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt tema-ID
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnesbefriare eller kostnadsfri funktion har inte definierats

### <a name="allowed-from"></a>Tillåts från

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
Ange standardborsten

### <a name="prototype"></a>Prototyp

```C
UINT gx_brush_default(GX_BRUSH *brush);
```

### <a name="description"></a>Description

Den här tjänsten anger penseln för den aktuella kontexten till systemets standardvärde.

### <a name="parameters"></a>Parametrar
- **brush** Pekare till penselkontrollblock.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad penseldefinition
- **GX_PTR_ERROR** (0x07) Ogiltig penselpekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten definierar en pensel med den angivna linjefärgen, fyllningsfärg och format.

### <a name="parameters"></a>Parametrar

- **brush** Pekare till penselkontrollblock
- **line_color** Färg på pensellinjen. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **fill_color** Färg på penselfyllning. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **style (stil)** Penselformat. **Bilaga D** beskriver de penselformat som stöds. Penselformat kan kombineras till en variabel med hjälp av en bitvis OR-åtgärd.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad penseldefinition
- **GX_PTR_ERROR** (0x07) Ogiltig penselpekare

### <a name="allowed-from"></a>Tillåts från

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

 Bakgrund för knappen Rita

###<a name="prototype"></a>Prototyp

```C
VOID gx_button_background_draw(GX_BUTTON *button);
```

### <a name="description"></a>Description

Den här tjänsten ritar knappbakgrunden. Den här funktionen anropas vanligtvis internt av gx_button_draw,men exponeras för programmet för att hjälpa till att skriva anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knappkontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar en knapp som anges och associerar knappen med den angivna överordnade widgeten.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knappkontrollblock
- **namn** Knappens logiska namn
- **överordnad** Pekare till överordnad widget för knappen
- **style** Knappformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **button_id** Programdefinierat ID för knappen
- **storlek** Knappens storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Knappgenereringen lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Knappen Avmarkera

### <a name="prototype"></a>Prototyp

```C
UINT gx_button_deselect(
    GX_BUTTON *button, 
    GX_BOOL gen_event);
```

### <a name="description"></a>Description

Den här tjänsten avmarkerar den angivna knappen och genererar en signalhändelse beroende på knappformat.


| Knappformat              | Signal                     |
|---------------------------|----------------------------|
| Ingen                      | GX_EVENT_CLICKED         |
| GX_STYLE_BUTTON_RADIO  | GX_EVENT_RADIO_DESELECT |
| GX_STYLE_BUTTON_TOGGLE | GX_EVENT_TOGGLE_OFF     |



### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knappkontrollblock
- **gen_event** Om GX_TRUE genererar knappen en händelse GX_EVENT_CLICKED, GX_EVENT_DESELECT eller GX_EVENT_TOGGLE_OFFSET beroende på knappstilen. Om GX_FALSE genererar knappen ingen händelse på högre nivå även om den normalt gör det.

### <a name="return-values"></a>Returvärden

- **knappen GX_SUCCESS** (0x00) Lyckades avmarkeras
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten ritar den angivna knappen. Den här funktionen anropas vanligtvis internt av GUIX-mekanismen för arbetsyteuppdatering, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade knappwidgetar.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knappkontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Processknapphändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_button_event_process(
    GX_BUTTON *button, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna knappen.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knappkontrollblock
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad knapphändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten väljer den angivna knappen och genererar en signalhändelse beroende på knappformat.

Avmarkerar på samma sätt som för en alternativknappsgrupp.

| Knappformat                       | Signal                   |
|------------------------------------|--------------------------|
| GX_STYLE_BUTTON_RADIO           | GX_EVENT_RADIO_SELECT |
| GX_STYLE_BUTTON_EVENT_ON_PUSH | GX_EVENT_CLICKED       |
| GX_STYLE_BUTTON_TOGGLE          | GX_EVENT_TOGGLE_ON    |


### <a name="parameters"></a>Parametrar

- **knapp** Pekare till knappkontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Knappen Lyckades
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange alfa-blend-värde för arbetsyta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_alpha_set(
    GX_CANVAS *canvas, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Description

Den här tjänsten anger värdet alpha-blend för den angivna arbetsytan. Alfavärden för arbetsyta kan vara mellan 0 (transparent) och 255 (helt täckande).

Att blanda överläggsarbetsytan kräver antingen stöd för maskinvarugrafiklager eller programvarustöd genom att skapa en sammansatt arbetsyta.

Maskinvarustöd för arbetsyteblandning aktiveras genom att anropa API:et gx_canvas_hardware_layer_bind() innan du anger alfavärdet för arbetsytan. När en arbetsyta är bunden till ett maskinvarugrafiklager anropar API:et för gx_canvas_alpha_set() direkt maskinvarugrafiklagrets blandningstjänster.

Om du vill använda programvarustöd för arbetsyteblandning måste programmet skapa en arbetsyta med GX_CANVAS_COMPOSITE-format, där alla andra hanterade arbetsyta är sammansatta före den slutliga visningen. Programvarustöd för arbetsyteblandning tillhandahålls endast när du kör med en visningsdrivrutin med 16 bpp eller högre färgdjup.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **alfa** Alpha-blend-värde, intervall från 0 (transparent) till 255 (täckande).

### <a name="return--values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad alfablandningsvärdeuppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_ERROR** (0x20) Ogiltig arbetsyta

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en cirkelbåg på arbetsytan med hjälp av den aktuella penseln. Cirkelbåge klipps till arbetsytans ogiltiga region. Den här tjänsten GX_ARC_DRAWING_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-position för mitten av cirkel arc
- **ycenter** y-position för mitten av cirkel arc
- **r** Radie för cirkel arc
- **start_angle** Startvinkel för cirkelbåge
- **end_angle** Slutvinkel för cirkelbåge

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad arc draw
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Flytta block med bildpunkter för arbetsyta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_block_move(GX_RECTANGLE *block,
    GX_VALUE x_shift, GX_VALUE y_shift, GX_RECTANGLE *dirty);
```

### <a name="description"></a>Description

Den här tjänsten flyttar ett block med pixeldata för arbetsytan i den riktning som anges. Den här tjänsten används internt av GUIX för att utföra snabb bläddring, men kan också användas av programmet.

### <a name="parameters"></a>Parametrar

- **blockera** Koordinater för det område som ska flyttas
- **x_shift** Antal bildpunkter som ska flyttas på x-axeln
- **y_shift** Antal bildpunkter som ska flyttas på y-axeln
- **dirty** Om blockflyttningen lyckas returnerar den här funktionen den del av källrektangeln som fortfarande är felaktig för anroparen i den här parametern.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad blockflyttning
- **GX_FAILURE** (0x10) Misslyckad blockflyttning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten ritar en cirkel på arbetsytan med hjälp av den aktuella penseln. Cirkeln klipps till arbetsytans ogiltiga region. Den här tjänsten GX_ARC_DRAWING_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-coord för mitten av cirkeln
- **ycenter** y-coord of center of the cirlce
- **r** Radie för cirkeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad cirkeldrag
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0x22) Ogiltig cirkelradie
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa arbetsyta

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

### <a name="description"></a>Description

Den här tjänsten skapar arbetsytan med de angivna egenskaperna och tillhörande minne.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **namn** Logiskt namn för arbetsytan
- **visa** Pekare till visning som skapats tidigare
- **typ** Typ av arbetsytaArbetsytans typer är:
- **GX_CANVAS_SIMPLE:** En minnesarbetsyta som används för att rita utanför skärmen.
- **GX_CANVAS_MANAGED:** En arbetsyta som automatiskt rensas till den aktiva visningen, antingen som en del av den sammansatta byggprocessen eller som en del av buffertreglageåtgärden för en enda arbetsytearkitektur.
- **GX_CANVAS_VISIBLE:** Den här flaggan kan användas för att aktivera och inaktivera en arbetsyta utan att förlora arbetsytans ritningsinnehåll.
- **GX_CANVAS_MODIFIED:** Reserverat för framtida användning.
- **GX_CANVAS_COMPOSITE:** Den här flaggan används av programmet när du konfigurerar ett system med flera arbetsyta som ska sammansatta flera hanterade arbetsyta till den sammansatta arbetsytan, och den sammansatta är den som drivs av maskinvarurambufferten.
- **bredd** Bredd i bildpunkter
- **höjd** Höjd i bildpunkter
- **memory_area** Minnesområde för arbetsyta. Det här värdet kan
- **GX_NULL** när arbetsytan skapades
- **och** senare initieras med gx_canvas_memory_define
- **memory_size** Storleken på minnesområdet i byte eller 0 om arbetsytans minne definieras när arbetsytan har skapats.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad arbetsyte skapas
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_CANVAS_SIZE** (0x1C) Ogiltig blockstorlek för arbetsytekontroll
- **GX_INVALID_TYPE** (0x1B) Ogiltig arbetsytetyp

### <a name="allowed-from"></a>Tillåts från

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

Ta bort arbetsyta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_delete(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

Den här tjänsten tar bort arbetsytan. Arbetsytan tas bort från den interna länkade listan över arbetsyta som underhålls av GUIX.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad arbetsyte skapas
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta

### <a name="allowed-from"></a>Tillåts från

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

Slutföra arbetsyteritning

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_drawing_complete(
    GX_CANVAS *canvas, 
    GX_BOOL flush);
```

### <a name="description"></a>Description

Den här tjänsten låter GUIX veta att programmets ritning på den angivna arbetsytan är klar.

Programmet kan använda den här tjänsten för att tvinga omedelbar ritning till en arbetsyta. Detta rensar arbetsytan till den synliga rambufferten och/eller utlöser en växlingsåtgärd för bugger, beroende på systemets minnesarkitektur.

Den här tjänsten bör endast anropas av programmet för att stänga en ritningssekvens som börjar med gx_canvas_drawing_initiate().

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **flush** Om **_GX_TRUE_** rensas ändringar i arbetsytan till skärmen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Slutförande av ritningen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Initiera arbetsyteritning

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_drawing_initiate(
    GX_CANVAS *canvas,
    GX_WIDGET *who, 
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Description

Den här tjänsten initierar ritningen på den angivna arbetsytan. Den här tjänsten anropas internt som en del av den uppskjutna ritningsåtgärden som utförs automatiskt av GUIX när en arbetsyta behöver uppdateras. Programmet tillåts dock kringgå GUIX-algoritmen för uppskjuten ritning och utföra omedelbar och direkt ritning på en arbetsyta genom att först anropa gx_canvas_drawing_inititate, sedan anropa önskade ritningsfunktioner och sedan anropa gx_canvas_drawing_complete().

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **vem** Pekare till widgetens kontrollblock för anroparen. Den här parametern används för att initiera ritningens urklipp och visa parametrar för efterföljande ritningsåtgärder.
- **dirty_area** Område att rita inom. Den här parametern skickas av anroparen för att ange det område som anroparen vill att alla ritningsåtgärder ska klippas till. Det här är vanligtvis det område som tidigare markerats som dirty (grovt) men anroparen kan expandera eller ta bort urklippsområdet.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad ritningsinitiering
- **GX_DRAW_NESTING_EXCEEDED** (0x05) Överskrid det högsta kapslingsantalet
- **GX_NO_VIEW** (0x03) Inga visningsportar för anroparen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en ellips på arbetsytan med hjälp av den aktuella penseln. Ellipsen klipps till arbetsytans ogiltiga region. Den här tjänsten GX_ARC_DRAWING_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-coord för mitten av ellipsen
- **ycenter** y-coord för mitten av ellipsen
- **en** längd på den semi-större axeln
- **b** Längden på den delvis mindre axeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad cirkeldrag
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Binda arbetsyta till maskinvarugrafikskikt

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_hardware_layer_bind(
    GX_CANVAS *canvas, 
    INT layer);
```

### <a name="description"></a>Description

Den här tjänsten binder en GUIX-arbetsyta till ett maskinvarugrafiklager. Den här tjänsten krävs endast för maskinvaruenheter som stöder flera maskinvarugrafiska lager.

Om du binder en arbetsyta till ett maskinvarugrafiklager implementeras API:erna gx_canvas_show(), gx_canvas_hide(), gx_canvas_alpha_set() och gx_canvas_offset_set() direkt av drivrutinstjänster för maskinvaruvisning.

Om drivrutinen för maskinvaruvisning inte stöder flera grafiklager returnerar den här tjänsten inte GX_INVALID_DISPLAY.

### <a name="parameters"></a>Parametrar

- **arbetsytearbetsyta** som ska implementeras i maskinvara
- **lager** maskinvarugrafikskikt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad bindning
- **GX_INVALID_DISPLAY** (0x1D) Visningslagertjänsten har inte definierats
- **GX_PTR_ERROR** (0x17) Ogiltiga pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta
- **GX_NOT_SUPPORTED** (0x28) Stöds inte

### <a name="allowed-from"></a>Tillåts från

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

Dölj en arbetsyta, vilket gör den osynlig

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

Den här tjänsten döljer en GUIX-arbetsyta. Om arbetsytan har bundets till ett maskinvarugrafiklager med hjälp gx_canvas_hardware_layer_bind(), implementeras den här tjänsten med maskinvarustöd.

### <a name="parameters"></a>Parametrar

- **arbetsytearbetsyta** som ska döljas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Dölj
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta
- **GX_PTR_ERROR** (0x17) Ogiltiga pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en linje på arbetsytan med hjälp av den aktuella penseln. Raden är klippt till arbetsytans ogiltiga region.

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-position för raden
- **y_end** Starta radens y-position
- **x_start** Avslutande x-position för raden
- **y_end** Avslutande y-position för raden

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad linjedragning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext
- **GX_INVALID_WIDTH** (0x1E) Ogiltig penselbredd

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Definiera arbetsyteminne

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_memory_define(
    GX_CANVAS *canvas, 
    GX_COLOR *memory,
    ULONG memsize);
```

### <a name="description"></a>Description

Den här tjänsten kan användas för att tilldela arbetsytans minnesadress när arbetsytan har skapats.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till arbetsyta som skapats tidigare
- **minne** Minnesadress för arbetsyta
- **memsize** Storlek på arbetsytans minnesblock i byte

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad tilldelning
- **GX_INVALID_CANVAS** (0x20) Ogiltigt kontrollblock
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Definiera musmarkörbilden

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_mouse_define(GX_CANVAS *canvas,
    GX_MOUSE_CURSOR_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten definierar musinformation för den angivna arbetsytan. Den här tjänsten GX_MOUSE_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **info** Pekare till markörinformation. **Bilaga I** innehåller en definition GX_MOUSE_CURSOR_INFO struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad musinformationsuppsättning
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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


Stänga av markören

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_mouse_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

Den här tjänsten gör markören dold från den angivna arbetsytan. Den här tjänsten GX_MOUSE_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Dölj en lyckad markör
- **GX_FAILURE** (0X10) Misslyckad markör dölj
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen


### <a name="allowed-from"></a>Tillåts från

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


Aktivera markören

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_mouse_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

Den här tjänsten gör markören synlig för den angivna arbetsytan. Den här tjänsten GX_MOUSE_SUPPORT måste definieras. Det gx_canvas_mouse_define API:et ska anropas för att definiera markörbilden innan den här tjänsten begärs.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad musinformationsuppsättning
- **GX_FAILURE** (0X10) Visa misslyckad musmarkör
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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


Tilldela skärmförskjutning för arbetsyta x,y

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_offset_set(
    GX_CANVAS *canvas,
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en x,y-visningsförskjutning för den angivna arbetsytan. Detta styr den position där arbetsytan är sammansatt i den synliga rambufferten och används ofta när arbetsytan är mindre än den fysiska visningen.

Om arbetsytan har bundets till ett maskinvarugrafiklager med hjälp av API:gx_canvas_hardware_layer_bind() implementeras tjänsten gx_canvas_offset_set direkt med maskinvarustöd.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **x** X koordinat för offset
- **y** Y-koordinat för offset

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad tilldelning av offset
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en cirkel på arbetsytan med hjälp av den aktuella penseln för ritningskontext. Cirkeldiagrammet klipps till arbetsytans ogiltiga region. Den här tjänsten kräver att konfigurationsalternativet GX_ARC_DRAWING_SUPPORT definieras.

### <a name="parameters"></a>Parametrar

- **xcenter** x-position för mitten av cirkeldiagrammet
- **ycenter** y-position för mitten av cirkeldiagrammet
- **r** Radie för cirkeldiagrammet
- **start_angle** Startvinkeln för cirkeldiagrammet
- **end_angle** Slutvinkel för cirkel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad arc draw
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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


Rita pixel

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixel_draw(GX_POINT position);
```

### <a name="description"></a>Description

Den här tjänsten ritar en pixel på arbetsytan med linjefärgen för den aktuella penseln för ritningskontexten. Om konfigurationsalternativet GX_BRUSH_ALPHA_SUPPORT definieras blandar du pixeln med annars ritar du pixeln som helt täckande.

- **peka** x,y bildpunktsposition som ska ritas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Blanda pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_blend(
    GX_VALUE x_position,
    GX_VALUE y_position, 
    GX_PIXELMAP *pixelmap, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Description

Den här tjänsten blandar en pixelkarta med arbetsytans bakgrund. Blandningsförhållandet anges av anroparen. Alfavärdet kan vara mellan 0 (helt transparent) och 255 (helt täckande). Pixelkartan kan också innehålla en intern alfakanal, som kombineras med det inkommande blandningsvärdet. Den här tjänsten stöds endast av visningsdrivrutiner som körs med 16 bpp-färgdjup och högre.

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-position för pixelkartan
- **y_end** Starta pixelkartans y-position
- **pixelkarta** Pekare till pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_NOT_SUPPORTED** (0x28) Stöds inte
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Rita pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_draw(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Description

Den här tjänsten ritar en pixelkarta på arbetsytan.

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-position för pixelkartan
- **y_end** Starta bildpunktskartans y-position
- **pixelkarta** Pekare till pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Hämta pixelkarta för arbetsyta

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_get(GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Description

Den här tjänsten returnerar GX_PIXELMAP struktur som pekar på arbetsytedata. Pixelkartans format är inställt på det aktuella visningsfärgformatet.

### <a name="parameters"></a>Parametrar

- **pixelkarta** Returnerad pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad pixelkarta get
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Rita roterad pixelkarta

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

### <a name="description"></a>Description

Den här tjänsten roterar en pixelkarta vid den angivna vinkeln och renderar pixelkartan till arbetsytan direkt när rotationen utförs. Den här tjänsten skiljer sig från gx_utility_pixelmap_rotate eftersom utdata från rotationen återges direkt till arbetsytans minne och den roterade pixelkartan inte returneras till anroparen.

Fördelen med den här tjänsten jämfört gx_utility_pixelmap_rotate är att inget ytterligare minne krävs för att hålla den roterade pixelkartan. Nackdelen är att rotationskoden måste köras varje gång pixelkartan ritas.

Verifiering av cklippning och visningsport framtvingas under återgivningen av den roterade pixelkartan.

### <a name="parameters"></a>Parametrar

- **x_position** Starta x-position för pixelkartan
- **y_position** Starta bildpunktskartans y-position
- **pixelkarta** Pekare till pixelkarta
- **vinkel** Vinkel att rotera
- **rot_cx** X-coord för rotationscenter. Om det här värdet är inställt på -1 används mitten av bilden som rotationscenter.
- **rot_cy** Y-coord för rotationscenter. Om det här värdet är inställt på -1 används mitten av bilden som rotationscenter.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Bildpunktskarta för panel

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_pixelmap_tile(
    GX_RECTANGLE *fill,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Description

Den här tjänsten fyller en rektangel i en arbetsyta med den begärda pixelkartan.

### <a name="parameters"></a>Parametrar

- **fyll i** Område till panel med pixelkarta
- **pixelkarta** Pekare till pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext
- **GX_INVALID_VALUE** (0x22) Ogiltig fyllningsstorlek

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en polygon på arbetsytan med hjälp av den aktuella penseln för ritningskontext.

### <a name="parameters"></a>Parametrar

- **point_array** Matris med punkter i polygonen
- **number_of_points** Antal punkter i polygon

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad polygondrag
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en rektangel på arbetsytan.

### <a name="parameters"></a>Parametrar

- **rektangel** Rektangel som ska ritas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad rektangeldrag
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext

### <a name="allowed-from"></a>Tillåts från

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


Rita text som roterats runt en mittpunkt (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_rotated_text_draw(
    const GX_CHAR *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Description

Det här API:et har gjorts inaktuellt och har gx_canvas_rotated_text_draw_ext(). Även om det fortfarande stöds bör nya program inte använda det här API:et och bör i stället använda gx_canvas_rotated_text_draw_ext().

Den här tjänsten ritar text till arbetsytan. Texten ritas roteras om den begärda mittpunkten. Det aktuella teckensnittet för ritningskontexten och färg på ritningskontextlinjen används för att återge texten.

Den här tjänsten använder funktionen gx_utility_string_to_alphamap att rendera textsträngen till en tillfällig 8bpp-pixelkarta som endast innehåller alfavärde. Tjänsten roterar sedan alfakartan med hjälp av funktionen gx_utility_pixelmap_rotate. När den sista alfakartan har renderats på arbetsytan frigör den här tjänsten den tillfälliga alfakartan och tillhörande minne.

Eftersom en tillfällig alfakarta krävs för att rendera roterad text måste programmet konfigurera gx_system_memory_allocator med hjälp av anrops-API:et gx_system_memory_allocator_set() innan det försöker rita roterad text.

Den här tjänsten ska endast användas för att rendera roterad text "en gång". Om samma textsträng ritas flera gånger på olika platser eller i olika rotationsvinklar är det mer effektivt att använda verktygsfunktionen gx_utility_string_to_alphamap() för att skapa textens alfakarta en gång och sedan använda gx_utility_pixelmap_rotate flera gånger för att rotera den resulterande alfakartan upprepade gånger.

### <a name="parameters"></a>Parametrar

- **text** Textsträng som ska ritas
- **xCenter** Centrera kring vilken text som ska roteras.
- **yCenter** Centrera positionen runt vilken text som ska roteras.
- **vinkel** Önskad rotationsvinkel för text i grader.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textåtergivning
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Otillräckligt minne tillgängligt eller gx_system_memory_allocator har inte tilldelats
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Rita text som roterats runt en mittpunkt

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_rotated_text_draw_ext(
    GX_CONST GX_STRING *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Description

Den här tjänsten ritar text till arbetsytan. Texten ritas roteras om den begärda mittpunkten. Det aktuella teckensnittet för ritningskontexten och färg på ritningskontextlinjen används för att återge texten.

Den här tjänsten använder funktionen gx_utility_string_to_alphamap att rendera textsträngen till en tillfällig 8bpp-pixelkarta som endast innehåller alfavärde. Tjänsten roterar sedan alfakartan med hjälp av funktionen gx_utility_pixelmap_rotate. När den sista alfakartan har renderats på arbetsytan frigör den här tjänsten den tillfälliga alfakartan och tillhörande minne.

Eftersom en tillfällig alfakarta krävs för att rendera roterad text måste programmet konfigurera gx_system_memory_allocator av ***anrops-API:et gx_system_memory_allocator_set*** innan det försöker rita roterad text.

Den här tjänsten ska endast användas för att rendera roterad text "en gång". Om samma textsträng ritas flera gånger på olika platser eller i olika rotationsvinklar är det mer effektivt att använda verktygsfunktionen gx_utility_string_to_alphamap() för att skapa textens alfakarta en gång och sedan använda gx_utility_pixelmap_rotate flera gånger för att rotera den resulterande alfakartan upprepade gånger.

### <a name="parameters"></a>Parametrar

- **text** Textsträng som ska ritas
- **xCenter** Centrera kring vilken text som ska roteras.
- **yCenter** Centrera positionen runt vilken text som ska roteras.
- **vinkel** Önskad rotationsvinkel för text i grader.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textåtergivning
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0x06) Ogiltig dragkontext
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Otillräckligt minne tillgängligt eller gx_system_memory_allocator har inte tilldelats.
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Skift-arbetsyta med x,y

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_shift(
    GX_CANVAS *canvas, 
    GX_VALUE x, GX_VALUE y);
```

### <a name="description"></a>Description

Den här tjänsten flyttar den angivna arbetsyteförskjutningen med det angivna beloppet. Detta påverkar den position där arbetsytan återges i den synliga rambufferten.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta
- **x** bildpunkter för att flytta på X-axeln
- **y bildpunkter** för att flytta på Y-axeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad arbetsyteväxling
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta

### <a name="allowed-from"></a>Tillåts från

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


Göra en arbetsyta synlig

### <a name="prototype"></a>Prototyp

```C
UINT gx_canvas_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

Den här tjänsten gör en arbetsyta synlig. Om arbetsytan tidigare har varit bunden till ett maskinvarugrafiklager med hjälp av API:gx_canvas_hardware_layer_bind() implementeras tjänsten gx_canvas_show() direkt med maskinvarustöd.

### <a name="parameters"></a>Parametrar

- **arbetsyta** Pekare till kontrollblock för arbetsyta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad tilldelning av offset
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CANVAS** (0x20) Ogiltig arbetsyta

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar text på arbetsytan. Det här API:et, som fortfarande stöds, är inaktuellt och nya program bör i stället använda gx_canvas_text_draw_ext().

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-koordinat för text
- **y_start** Starta y-koordinaten för text
- **sträng** Pekare till sträng att rita
- **längd** Om längden >= 0 begränsar antalet tecken som ritas till längd. Om längden < 0 dras hela strängen tills NULL-terminatorn har ritats.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad text draw
- **GX_FAILURE** (0x1E) Misslyckad text draw
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar text på arbetsytan.

### <a name="parameters"></a>Parametrar

- **x_start** Starta x-koordinat för text
- **y_start** Starta y-koordinaten för text
- **sträng** Pekare till sträng att rita

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad text draw
- **GX_FAILURE** (0x1E) Misslyckad text draw
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_CONTEXT** (0x06) Ingen öppen ritningskontext
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd
- **GX_INVALID_FONT** (0x16) Ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåts från

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


Skapa kryssruta

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

### <a name="description"></a>Description

Den här tjänsten skapar en kryssruta med de angivna egenskaperna. GX_CHECKBOX härleds från GX_TEXT_BUTTON och alla gx_text_button-tjänster kan användas med GX_CHECKBOX widgetar.

### <a name="parameters"></a>Parametrar

- **kryssruta** Pekare till kryssruta kontrollblocknamn Logiskt namn för kryssruta widget
- **överordnad** Pekare till den överordnade widgeten
- **text_id** Resurs-ID för kryssrutatext
- **style (stil)** Kryssrutasstil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **checkbox_id** Kryssruta för programdefinierat ID
- **storlek** Kryssrutas dimensioner

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades skapa
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig storlek

### <a name="allowed-from"></a>Tillåts från

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

Kryssrutan Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_checkbox_draw(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Description

Den här tjänsten ritar den angivna kryssrutan. Den här funktionen anropas vanligtvis internt av GUIX-arbetsytans uppdateringsmekanism, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade kryssrutawidgetar.

### <a name="parameters"></a>Parametrar

- **kryssruta** Pekare till kryssruta för kontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Processkryssruta

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_event_process(
    GX_CHECKBOX *checkbox, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna kryssrutan. Den här tjänsten ska anropas som standardhändelsehanterare av alla anpassade funktioner för händelsebearbetning av kryssrutor.

### <a name="parameters"></a>Parametrar

- **kryssruta** Pekare till kryssruta för kontrollblock
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Händelseprocessen lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange pixelkarta för kryssruta

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_pixelmap_set(
    GX_CHECKBOX *checkbox,
    GX_RESOURCE_ID unchecked_id, 
    GX_RESOURCE_ID checked_id,
    GX_RESOURCE_ID unchecked_disabled_id, 
    GX_RESOURCE_ID checked_disabled_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar pixelkartor som ska visas av den angivna kryssrutan för varje kryssrutas tillstånd. Resurs-ID:erna kan dupliceras.

### <a name="parameters"></a>Parametrar

- **kryssruta** Pekare till kryssruta för kontrollblock
- **unchecked_id** Pixelkarta som används för avmarkerat tillstånd
- **checked_id** Pixelkarta som används för kontrollerat tillstånd
- **unchecked_disabled_id** Pixelkarta som används för en inaktiverad och avmarkerad kryssruta
- **checked_disabled_id** Pixelkarta som används för en inaktiverad och markerad kryssruta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Kryssrutan Lyckades
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Markera kryssrutan

### <a name="prototype"></a>Prototyp

```C
UINT gx_checkbox_select(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Description

Den här tjänsten tvingar fram en kryssruta till det valda tillståndet.

### <a name="parameters"></a>Parametrar

- **kryssruta** Pekare till kryssruta för kontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Kryssrutan Lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten hämtar den aktuella nålvinkeln för widgeten för cirkelmätare.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för cirkelformad mätare
- **vinkel** Aktuell nålvinkel som ska hämtas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad cirkelmätare vinkel get
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange målvinkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_angle_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT angle);
```

### <a name="description"></a>Description

Den här tjänsten anger målvinkeln för en widget för cirkelmätare.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för cirkelformad mätare
- **vinkel** Målnålsvinkel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad vinkeluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange animeringsparametrar

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_animation_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT steps, 
    INT delay);
```

### <a name="description"></a>Description

Den här tjänsten anger animeringssteg och fördröjningstid för en widget för cirkelmätare.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för cirkelformad mätare
- **steg** Totalt antal steg för en rotation
- **fördröjning** Fördröjningstid för varje steg

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Kryssrutan Lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde

### <a name="allowed-from"></a>Tillåts från

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


Rita cirkelmätares bakgrund

### <a name="prototype"></a>Prototyp

```C
VOID gx_circular_gauge_background_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Description

Den här tjänsten ritar bakgrunden till den angivna cirkelformade mätaren. Den här tjänsten anropas vanligtvis internt av gx_circular_gauge_draw-funktionen, men exponeras för programmet för att hjälpa till att skriva anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för cirkelformad mätare

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för cirkelformad mätare med de angivna egenskaperna.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för cirkelformad mätare
- **namn** Logiskt namn på widget för cirkelformad mätare
- **överordnad** Pekare till den överordnade widgeten
- **info** Pekare till mätarinformationsstrukturen. **Bilaga I** innehåller definition för GX_CIRCULAR_GAUGE_INFO struktur
- **background_id** Resurs-ID för bildpunktskarta för cirkelmätare i bakgrunden
- **style (stil)** Format för cirkelformad mätare. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **circular_gauge_id** Programdefinierat ID för cirkulär mätare
- **xpos** Mätarposition för x-koordinat
- **ypos** Position för mätare y-koordinat

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Kryssrutan Lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för kontroll
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats

### <a name="allowed-from"></a>Tillåts från

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

Rita cirkelformad mätare

### <a name="prototype"></a>Prototyp

```C
VOID gx_circular_gauge_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Description

Den här tjänsten ritar den angivna cirkulära mätaren. Den här funktionen anropas vanligtvis internt av GUIX-arbetsytans uppdateringsmekanism, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade mätarwidgetar.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för cirkelformad mätare

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Händelse för process cirkulär mätare

### <a name="prototype"></a>Prototyp

```C
UINT gx_circular_gauge_event_process(
    GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna cirkulära mätaren.

### <a name="parameters"></a>Parametrar

- **mätare** Pekare till kontrollblock för mätare
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad händelseprocess för mätare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange pensel av aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_default(GX_DRAW_CONTEXT *context);
```

### <a name="description"></a>Description

Den här tjänsten anger penseln för den angivna ritningskontexten till standard.

### <a name="parameters"></a>Parametrar

- **kontext** Pekare till kontextkontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har skapats
- **GX_PTR_ERROR** (0x07) Ogiltig kontext pekare

### <a name="allowed-from"></a>Tillåts från

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


Definiera pensel av aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_define(
    GX_RESOURCE_ID line_color_id,
    GX_RESOURCE_ID fill_color_id, 
    UINT style);
```

### <a name="description"></a>Description

Den här tjänsten definierar penseln i den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **line_color_id** Resurs-ID för linjefärg. **Bilaga B** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet även kan lägga till anpassade resurs-ID:n för färg.
- **fill_color_id** Resurs-ID för fyllningsfärg. **Bilaga B** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet även kan lägga till anpassade resurs-ID:n för färg.
- **style** Penselformat. **Bilaga D** beskriver de penselformat som stöds. Penselformat kan kombineras till en variabel med hjälp av bitvis OR-åtgärd.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Definiera en lyckad kontextborste
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext definierar
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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


Hämta pensel av aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_get(GX_BRUSH **return_brush);
```

### <a name="description"></a>Description

Den här tjänsten returnerar en pekare till den aktiva penseln i den aktuella ritningskontexten. Om det inte finns någon aktiv ritningskontext misslyckas tjänsten och returnerar en NULL-pekare.

### <a name="parameters"></a>Parametrar

- **return_brush** Pekare till mål för pensel.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Context Brush har hämtats
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange penselmönster för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_pattern_set(ULONG pattern);
```

### <a name="description"></a>Description

Den här tjänsten anger penselmönstret för den aktuella ritningskontexten.

Penselmönstret används för att rita streckade vågräta och streckade lodräta linjer. När gx_canvas_line_draw() anropas och linjen är vågrät eller lodrät och brush.gx_brush_line_pattern-fältet inte är noll ritas en mönsterlinje.

Penselmönstermasken stöds för närvarande endast för vågräta och lodräta linjer.

### <a name="parameters"></a>Parametrar

- **mönster** Mönster som ska användas för penseln. Det här är ett enkelt hexidecimalt på/av-mönster som ska användas för mönsterlinjeritning.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad kontextborsteuppsättning
- **GX_INVALID_CONTEXT** (0x06) Ogiltig ritningskontext

### <a name="allowed-from"></a>Tillåts från

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


Ange pensel för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_set(GX_BRUSH *brush);
```

### <a name="description"></a>Description

Den här tjänsten anger penseln för den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **brush** Pekare som ska användas för den aktuella kontexten.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad kontextborsteuppsättning
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange penselformat för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_style_set(UINT style);
```

### <a name="description"></a>Description

Den här tjänsten anger penselformatet för den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **style (stil)** Penselformat för aktuell kontext. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad kontextborsteformatuppsättning
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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


Ange penselbredd för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_brush_width_set(UINT width);
```

### <a name="description"></a>Description

Den här tjänsten anger bredden på den aktiva penseln i den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

**bredd** Penselbredd i bildpunkter i aktuell kontext

### <a name="return-values"></a>Returvärden

**GX_SUCCESS** (0x00) Lyckad kontextborstebreddsuppsättning

**GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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


Hämta färgvärde som är associerat med färg-ID i den aktuella ritade kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_color_get(
    GX_RESOURCE_ID color_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Description

Den här tjänsten hämtar färgvärdet som är associerat med det angivna färg-ID:t. Färgvärdet returneras i färgformatet för den aktiva kontextvisningen. Den här tjänsten ska bara anropas inifrån en aktiv ritningsåtgärd.

### <a name="parameters"></a>Parametrar

**color_id** Resurs-ID för färg som begärts.

**return_color** Adressen till variabeln som ska innehålla det returnerade färgvärdet.

### <a name="return-values"></a>Returvärden

**GX_SUCCESS** (0x00) Lyckat färgvärde get

**GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID

**GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

**GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Ange fyllningsfärg för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_fill_color_set(GX_RESOURCE_ID fill_color_id);
```

### <a name="description"></a>Description

Den här tjänsten anger fyllningsfärgen för den aktiva penseln i den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **fill_color_id** Resurs-ID för fyllningsfärgen för den aktuella kontexten. **Bilaga B** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet även kan lägga till anpassade resurs-ID:n för färg.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad kontextfyllningsfärguppsättning
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Hämta teckensnitt som är associerat med teckensnitts-ID i den aktuella ritade kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_font_get(
    GX_RESOURCE_ID font_id,
    GX_FONT **return_font);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den teckensnittspekare som är associerad med det angivna teckensnitts-ID:t. Den här tjänsten ska bara anropas inifrån en aktiv ritningsåtgärd.

### <a name="parameters"></a>Parametrar

- **font_id** Resurs-ID för teckensnittet som begärdes.
- **return_font** Adressen till variabeln som ska innehålla den returnerade teckensnittspekaren.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Teckensnittet har hämtats
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Ange teckensnitt för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_font_set(GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

Den här tjänsten anger teckensnittet i den aktiva penseln i den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **font_id** Teckensnittsresurs-ID för aktuell kontext

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad kontextteckensnittsuppsättning
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Ange linjefärg för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_line_color_set(GX_RESOURCE_ID line_color_id);
```

### <a name="description"></a>Description

Den här tjänsten anger linjefärgen för den aktiva penseln i den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **line_color_id** Linjefärg för aktuell kontext. **Bilaga B** innehåller fördefinierade färgresurs-ID:er. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färguppsättning för kontextlinje
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Hämta pixelkarta som är associerad med pixelkartans ID i den aktuella ritade kontexten

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_pixelmap_get(
    GX_RESOURCE_ID pixelmap_id,
    GX_PIXELMAP **return_map);
```

### <a name="description"></a>Description

Den här tjänsten hämtar pekaren för pixelkartan som är associerad med det angivna pixelkarta-ID:t.

### <a name="parameters"></a>Parametrar

- **pixelmap_id** Resurs-ID för pixelkarta begärd.
- **return_map** Adressen till variabeln som ska innehålla den returnerade pixelkarta-adressen.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hämtad pixelkarta
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext
- **GX_PTR_ERROR** (0x07) Ogiltig pixelkarta-pekare

### <a name="allowed-from"></a>Tillåts från

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

Ange pixelkarta för aktuell ritad kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_pixelmap_set(GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar pixelkartan för den aktiva penseln i den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **pixelmap_id** Resurs-ID för pixelkarta som ska användas för aktuell kontext

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad bildpunktsuppsättning för kontext
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVLAID_CONTEXT** (0x06) Ogiltig kontext

### <a name="allowed-from"></a>Tillåts från

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

Definiera raw-pensel för aktuell rita-kontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_raw_brush_define(
    GX_COLOR line_color,
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Description

Den här tjänsten definierar den råa penseln för den aktuella skärmkontexten. Rådefinitioner används när 32-bitars ARGB-färgvärden ska skickas till penseln i stället för färg-ID:er. Råfärgdefinitioner är användbara när den önskade färgen inte finns i den aktuella systemfärgtabellen eller när RGB-färgvärdet beräknas vid körning.

### <a name="parameters"></a>Parametrar

- **line_color** Linjefärg i 32-bitars ARGB-färgformat. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **fill_color** Färg på fyllning i 32-bitars argb-färgformat. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **style (stil)** Penselformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Definiera en lyckad kontextrå pensel
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Ange rå fyllningsfärg för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_raw_fill_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Description

Den här tjänsten anger den råa fyllningsfärgen för den aktuella skärmkontexten. Parametern line_color är ett 32-bitars ARGB-format för råfärg i stället för ett färg-ID-värde. Råfärgdefinitioner är användbara när den önskade färgen inte finns i den aktuella systemfärgtabellen eller när RGB-färgvärdet beräknas vid körning.

### <a name="parameters"></a>Parametrar

- **line_color** Linjefärg. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färguppsättning för råkontextfyllning
- **GX_INVALID_CONTEXT** (0x06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Ange rålinjefärg för aktuell ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_raw_line_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Description

Den här tjänsten anger linjefärgen för den aktiva penseln i den aktuella ritningskontexten. Parametern line_color är ett 32-bitars ARGB-format för råfärg i stället för ett färg-ID-värde. Råfärgdefinitioner är användbara när den önskade färgen inte finns i den aktuella systemfärgtabellen eller när RGB-färgvärdet beräknas vid körning.

### <a name="parameters"></a>Parametrar

- **line_color** Färg på radvärdet. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färguppsättning för kontextrå linje
- **GX_INVALID_CONTEXT** (0X06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Hämta sträng som är associerad med sträng-ID (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_string_get(GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **return_string);
```

### <a name="description"></a>Description

Det här inaktuella API:et returnerar strängen som är associerad med det angivna sträng-ID:t. Nya program bör använda gx_context_string_get_ext().

### <a name="parameters"></a>Parametrar

- **string_id** Sträng-ID som genereras av GUIX Studio-programmet.
- **return_string** Adressen till variabeln som ska returnera sträng pekaren.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färguppsättning för kontext raw-linje
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0X06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Hämta sträng som är associerad med det angivna sträng-ID:t.

### <a name="prototype"></a>Prototyp

```C
UINT gx_context_string_get_ext(
    GX_RESOURCE_ID string_id, 
    GX_STRING *return_string);
```

### <a name="description"></a>Description

Den här tjänsten returnerar strängen som är associerad med ett visst sträng-ID. Den här tjänsten kan bara anropas när det finns en aktiv ritningskontext, dvs. inifrån ritningsfunktionen för en widget. Den här tjänsten identifierar den aktiva arbetsytan och visar och hämtar strängen från den visningsinstans som finns.

### <a name="parameters"></a>Parametrar

- **string_id** Sträng-ID som används för att identifiera strängen, som genereras av GUIX Studio i programmets resurshuvudfil.
- **return_string** Adressen till GX_STRING variabel där strängpekaren och stränglängden returneras.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färguppsättning för kontext raw-linje
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_CONTEXT** (0X06) Ingen aktiv ritningskontext

### <a name="allowed-from"></a>Tillåts från

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

Tilldela visningsaktivt språk

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_active_language_set(
    GX_DISPLAY *display, 
    GX_UBYTE language);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar det aktiva språket för den angivna visningen. Språkindexet motsvarar de språk som definierats i tabellen med visningsspråk och är inte en ANSI-språkidentifierare.

Olika skärmar i ett system med flera skärmar kan köra olika aktiva språk. Tabellen med visningsspråk ska tilldelas innan det här API:et används. När en visning initieras med gx_studio_display_configure installeras språktabellen automatiskt och programmet skickar det aktiva språkindexet.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **språk** Aktivt språkindex

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Tilldela språk
- **GX_PTR_ERROR** (0x07) Ogiltig visningspekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt språkindex

### <a name="allowed-from"></a>Tillåts från

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

Tilldela om ett färgvärde

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_color_set(
    GX_DISPLAY *display,
    GX_RESOURCE_ID color_id, 
    GX_COLOR new_color);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar om färgvärdet som är associerat med det angivna färg-ID:t. Detta kan användas för att ändra färgtabellen för en visning utan att tillhandahålla en helt ny färgtabell. Det angivna färgvärdet måste ha det ursprungliga format som stöds av visningen.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **color_id** Färg-ID som ska tilldelas om
- **new_color** Färgvärde som ska tilldelas till color_id plats

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färgtilldeling
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt färg-ID
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_DISPLAY** (0x1D) Ogiltig visning

### <a name="allowed-from"></a>Tillåts från

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

Tilldela visningsfärgtabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_color_table_set(
    GX_DISPLAY *display,
    GX_COLOR *color_table, 
    INT color_count);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar om färgtabellen som ska användas av visningen. Den här tjänsten anropas vanligtvis av den GUIX Studio-genererade visningskonfigurationsfunktionen, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **color_table** Matris med färgvärden i enhetligt format.
- **color_count** Anger antalet poster i färgtabellen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färgtabelluppsättning
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_DISPLAY** (0x1D) Ogiltig visning

### <a name="allowed-from"></a>Tillåts från

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

Skapa visning

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_create(
    GX_DISPLAY *display, 
    GX_CONST CHAR *name,
    UINT (*display_driver_setup)(GX_DISPLAY *),
    GX_VALUE width, 
    GX_VALUE height);
```

### <a name="description"></a>Description

Den här tjänsten skapar en visning och anropar funktionen för att konfigurera visningsdrivrutiner. GUIX tar den här visningen och lägger till den i sin interna lista över skärmar.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **namn** Namnet på visningen
- **display_driver_setup** Pekare för att visa funktionen för drivrutinsinstallation
- **optional_driver_info** Pekare till valfri drivrutinsinformation
- **color_format** Färgformat enligt definitionen i **bilaga C**
- **bredd** Antal bildpunkter på x-axeln
- **höjd** Antal bildpunkter på y-axeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad visnings skapas
- **GX_SYSTEM_ERROR** (0xFE) Det gick inte att konfigurera visningen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_SIZE** (0x23) Ogiltig blockstorlek för visningskontroll

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten stänger av en visning och rensar allokerade resurser.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **display_driver_cleanup** Pekare för att visa funktionen för att rensa drivrutiner

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad visnings borttagning
- **GX_FAILURE** (0x10) Den skapade visningslistan är NULL
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Tilldela visningsteckensnittstabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_font_table_set(
    GX_DISPLAY *display,
    GX_FONT **font_table, 
    INT table_size);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar om teckensnittstabellen som ska användas av visningen. Den här tjänsten anropas vanligtvis av den GUIX Studio-genererade visningskonfigurationsfunktionen, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **font_table** Matris med GX_FONT pekare.
- **table_size** Antal teckensnitt i tabellen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckensnittstabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Hämta visningsspråktabell (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_get(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE *language_count,
    UINT *string_table_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar språktabellen från den angivna visningen. Den här tjänsten kan användas av ett program för att ändra visningsspråktabellen vid körning med hjälp av dynamiskt definierade strängar.

Detta API är inaktuellt och stöds endast för program som använder den gamla formatspråktabellen (dvs. den Studio-genererade resursfilen genereras för biblioteksversion före version 5.6). Nya program bör använda gx_display_language_table_get_ext().

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **tabell** Adress för att ta emot tabell pekare
- **language_count** Adress för att ta emot språkantal
- **string_table_size** Adress för att ta emot strängtabellens storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckentabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Hämta visningsspråktabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_get_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE *language_count, 
    UINT *string_table_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar språktabellen från den angivna visningen. Den här tjänsten kan användas av ett program för att ändra visningsspråktabellen vid körning med hjälp av dynamiskt definierade strängar.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **tabell** Adress för att ta emot tabell pekare
- **language_count** Adress för att ta emot språkantal
- **string_table_size** Adress för att ta emot strängtabellens storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckentabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Tilldela visningsspråktabell (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_set(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE number_of_languages, 
    UINT number_of_strings);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell och nya program bör använda gx_display_language_table_set_ext(). Den här tjänsten stöds endast för kompatibilitet med Studio-genererade resursfiler som är riktade mot biblioteksversioner före version 5.6.

Den här tjänsten tilldelar språktabellen som ska användas av visningen. Den här tjänsten anropas vanligtvis av den GUIX Studio-genererade funktionen gx_studio_display_configure, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **tabell** Språktabell
- **number_of_languages** Antal kolumner i den angivna tabellen
- **number_of_strings** Antal strängar i varje tabellkolumn

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckentabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Tilldela visningsspråktabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_language_table_set_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE number_of_languages,
    UINT number_of_strings);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar språktabellen som ska användas av visningen. Den här tjänsten anropas vanligtvis av den GUIX Studio-genererade funktionen gx_studio_display_configure, men kan även anropas av programmet.

Tabelltilldelning för körningsspråk görs vanligtvis när språk läses in från en binär resursfil med hjälp av gx_binres_language_table_load().

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **tabell** Språktabell
- **number_of_languages** Antal kolumner i den angivna tabellen
- **number_of_strings** Antal strängar i varje tabellkolumn

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckentabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

Tilldela visningsteckensnittstabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_pixelmap_table_set(
    GX_DISPLAY *display,
    GX_PIXELMAP **pixelmap_table, 
    INT table_size);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar om pixelkartan som ska användas av visningen. Den här tjänsten anropas vanligtvis av den Studio-genererade konfigurationsfunktionen för visning, men kan även anropas av programprogramvaran.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **pixelmap_table** Matris med GX_PIXELMAP pekare.
- **table_size** Antal pixelkartor i tabellen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En lyckad uppsättning pixelkarta-tabell
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Hämta en sträng från den aktiva strängtabellen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_get(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id, 
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_display_string_get_ext().

Den här tjänsten hämtar en sträng från den aktiva strängtabellen för den angivna visningen. Det aktiva språket används för att välja strängen från språktabellen som är tilldelad till visningen.

Sträng-ID:er genereras av GUIX Studio och finns i programmets resources.h-huvudfil.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **string_id** Sträng-ID, genererat av GUIX Studio.
- **sträng** Adress för strängpekarvariabel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad stränghämtning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_RESOURCE_ID** (0X33) Ogiltigt sträng-ID
- **GX_PTR_ERROR** (0x07) Ogiltig visningspekare

### <a name="allowed-from"></a>Tillåts från

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

Hämta en sträng från den aktiva strängtabellen

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_get_ext(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id,
    GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten hämtar en sträng från den aktiva strängtabellen för den angivna visningen. Det aktiva språket används för att välja strängen från språktabellen som är tilldelad till visningen.

Sträng-ID:er genereras av GUIX Studio och finns i programmets resources.h-huvudfil.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **string_id** Sträng-ID, genererat av GUIX Studio.
- **sträng** Adress för GX_STRING variabel i
- **vilka** string.gx_string_ptr och
- **string.gx_string_length** returneras.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad stränghämtning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_RESOURCE_ID** (0X33) Ogiltigt sträng-ID
- **GX_PTR_ERROR** (0x07) Ogiltig visningspekare

### <a name="allowed-from"></a>Tillåts från

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


Hämta den aktiva strängtabellen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_CHAR ***table,
    UINT *table_size);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell och ersätts av gx_display_string_table_get_ext().

Den här tjänsten hämtar strängtabellen som är associerad med det aktiva språket. Den här tjänsten används inte ofta, men tillhandahålls för fullständighet för de program som kan behöva göra körningsändringar i strängtabellen.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **språk** Tabellkolumn som ska hämtas.
- **tabell** Adressen till variabeln som pekaren ska returneras till.
- **table_size** Adress för variabeln som ska returnera tabellstorleken

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckentabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_NOT_FOUND** (0x09) Ogiltigt språkindex
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Hämta den aktiva strängtabellen

### <a name="prototype"></a>Prototyp

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_STRING **table, 
    UINT *table_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar strängtabellen som är associerad med det aktiva språket. Den här tjänsten används inte ofta, men tillhandahålls för fullständighet för de program som kan behöva göra körningsändringar i strängtabellen.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **språk** Tabellkolumn som ska hämtas.
- **tabell** Adressen till variabeln som pekaren ska returneras till.
- **table_size** Adress för variabeln som ska returnera tabellstorleken

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckentabelluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_NOT_FOUND** (0x09) Ogiltigt språkindex
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten installerar teman på den angivna visningen. Den här tjänsten anropas vanligtvis av den Studio-genererade konfigurationsfunktionen för visning, men kan även anropas av programprogramvaran.

### <a name="parameters"></a>Parametrar

- **visa** Pekare för att visa kontrollblock
- **theme_table** Tematabell som ska installeras

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Tematabellen har installerats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig tematabell pekare
- **GX_INVALID_DISPLAY** (0x1D) Ogiltig visning

### <a name="allowed-from"></a>Tillåts från

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


Stäng en listlista

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_close(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Description

Den här tjänsten stänger popup-listan för den angivna listrutan.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontrollblocket för listrutan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades stängde listrutan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

gx_drop_list_pixelmap_set, gx_drop_list_popup_get

## <a name="gx_drop_list_create"></a>gx_drop_list_create


Skapa en listrutan

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

### <a name="description"></a>Description

Den här tjänsten skapar en listrutan. En listruta är en kombination av widgeten för listrutan och en lodrät popup-lista som visas när listrutan öppnas. Den lodräta popup-listan skapas automatiskt när widgeten för listrutan skapas och visas eller döljs när listrutans widget öppnas respektive stängs.

Widgeten för listrutan stöder två associerade pixelkartor. Den första, som beskrivs som "List Wallpaper" (Visa bakgrundsbild) i egenskapsvyn i Studio, är den valfria pixelkartan för skrivbordsunderlägg som visas som bakgrund till den lodräta listan som visas när listrutans widget öppnas. Den andra pixelkartan, som beskrivs som "Bakgrundsbild" i Studio-egenskapsvyn, är en valfri bild som visas som bakgrund till själva listrutan.

En widget i listrutan kan ha (men måste inte ha) en underordnad widget som används för att öppna och stänga listrutan. Detta är vanligtvis en ikon eller knappwidget, men även en anpassad widget kan användas som växlingsknapp för att öppna/stänga för den överordnade listrutan. Nyckelinställningen som gör att den här underordnade widgeten använder listrutan är att den underordnade widgeten måste ha det fördefinierade widget-ID:t ID_DROP_LIST_BUTTON.

Så här definierar du en underordnad widget som öppnar och stänger listrutan, först lägga till och underordnad widget i listrutan och placera den underordnade i listrutan efter behov:

![Skärmbild av listrutan.](./media/guix/image6.jpg)

Använd sedan Studio-egenskapsvyn för att tilldela den underordnade widgeten ID-värdet ID_DROP_LIST_BUTTON, vilket är ett internt definierat ID-värde som identifieras av den överordnade listrutan:

![Skärmbild av egenskapsvyn i Studio.](./media/guix/image7.jpg)

### <a name="parameters"></a>Parametrar
- **drop_list** Pekare till kontrollblocket för listrutan
- **namn** Namn på listrutan
- **överordnad** Pekare till den överordnade widgeten
- **total_rows** Totalt antal rader i listrutan
- **open_height** Höjden på den lodräta listan som visas när listrutan öppnas.
- **motringning** Funktion som anropas av den lodräta listan när listan rullas. Mer information finns i dokumentationen GX_VERTICAL_LIST information.
- **style** Kantlinjeformatet i listrutan.
- **drop_list_id** Programdefinierat ID för listrutan
- **storlek** Mått för listrutan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa listrutan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåts från

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


Bearbeta drop list-händelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_event_process(
    GX_DROP_LIST *list, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för listrutan.

### <a name="parameters"></a>Parametrar

- **drop_list** Kontrollblock för listwidget
- **händelse** Pekare till händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En hanterad drop list-händelse har bearbetats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Öppna en listlista

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_open(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Description

Den här tjänsten öppnar en tidigare skapad listlista.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontrollblocket för listrutan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa listrutan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Tilldela en bakgrundsbild till listrutan

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_pixelmap_set(
    GX_DROP_LIST *drop_list,
    GX_RESOURCE_ID id);
```

### <a name="description"></a>Description

Tilldela en bakgrundsbild till listrutan. Den här pixelkartan används som bakgrund för själva listwidgeten och inte för den lodräta popup-listan som visas när listan öppnas. Om du vill tilldela en pixelkarta till listrutan måste du först anropa gx_drop_list_popup_get för att hämta en pekare till popup-listan och sedan använda gx_window_wallpaper_set() för att tilldela en pixelkarta till den här popup-listan.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontrollblocket för listrutan
- **id** Resurs-ID till pixlemap

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad bildpunktsuppsättning för släpplista
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt pixlemap-ID

### <a name="allowed-from"></a>Tillåts från

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


Hämta pekare till lodrät popup-lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_drop_list_popup_get(
    GX_DROP_LIST *drop_list,
    GX_VERTICAL_LIST **return_list);
```

### <a name="description"></a>Description

En widget i listrutan består av själva listlistewidgeten och en lodrät popup-lista som visas när listr listwidgeten öppnas. Den här tjänsten hämtar en pekare till den lodräta listkomponenten i listrutan, så att programmet kan anropa API-tjänster direkt på den här lodräta listan.

### <a name="parameters"></a>Parametrar

- **drop_list** Pekare till kontrollblocket för listrutan
- **return_list** Pekare till den lodräta listan som lagras i listrutan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En lodrät popup-lista har hämtats
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

## <a name="gx_generic_scroll_wheel_children_position"></a>gx_generic_scroll_wheel_children_position
### <a name="position-children-for-the-generic-scroll-wheel"></a>Placera underordnade för det allmänna rullningshjulet

### <a name="prototype"></a>Prototyp

```C
UINT gx_generic_scroll_wheel_children_position(
    GX_GENERIC_SCROLL_WHEEL *wheel)
```

### <a name="description"></a>Description

Den här funktionen placerar underordnade för det allmänna rullningshjulet enligt den allmänna rullningshjulets radhöjd. Den här funktionen anropas som standard när det allmänna rullningshjulet visas.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till det allmänna kontrollblocket för rullningshjul

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Placerade de underordnade för det allmänna rullningshjulet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Position children in the generic scroll wheel. */
status = gx_generic_scroll_wheel_children_position (&wheel);

/* If status is GX_SUCCESS the children in the generic scroll wheel are positioned. */
```

### <a name="see-also"></a>Se även

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_create"></a>gx_generic_scroll_wheel_create


Skapa ett allmänt rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_generic_scroll_wheel_create(
    GX_GENERIC_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows,
    VOID (*callback)(GX_GENERIC_SCROLL_WHEEL *, GX_WIDGET *, INT),
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en allmän widget för rullningshjul.

Ett allmänt rullningshjul är en typ av widget för rullningshjul som består av underordnade widgetar. Andra typer av widgetar för rullningshjul är också tillgängliga. Mer information om hierarkin för rullningshjulswidget, widgettyper och widgetar finns i API:gx_scroll_wheel_create().

GX_GENERIC_SCROLL_WHEEL härleds från GX_SCROLL_WHEEL och stöder alla gx_scroll_wheel tjänster.

Alla typer av rullningshjul GX_EVENT_LIST_SELECT händelser till sin överordnade när rullningshjulet rullas.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **namn** Logiskt namn på allmän widget för rullningshjul
- **överordnad** Pekare till den överordnade widgeten
- **total_rows** Totalt antal rader i rullningshjulet.
- **motringning** Återanropsfunktion för att skapa en widgetrad. Det kan vara GX_NULL om antalet totalt antal rader matchar det underordnade antalet. Den bör anges för återanvändning av widget när det underordnade antalet är mindre än antalet rader eller om GX_STYLE_WRAP har angetts. Och se i det här fallet till att det underordnade antalet är 1 mer än antalet synliga rader.
- **style** Stil på ett allmänt rullningshjul. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar och widgetspecifika format.
- **id** Programdefinierat ID för allmänt rullningshjul
- **storlek** Dimensioner för allmän widget för rullningshjul

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ett allmänt rullningshjul har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_VALUE** (0x22) Ogiltigt antal rader
- **GX_INVALID_WIDGET** (0x12) Ogiltig överordnad widget

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C

/* Define visible rows.  */
#define VISIBLE_ROWS 5

/* Define row memory.  */
GX_NUMERIC_PROMPT row_memory[VISIBLE_ROWS + 1];

/* Define callback function.  */
VOID row_create(GX_GENERIC_SCROLL_WHEEL *wheel, GX_WIDGET *widget, INT index)
{
GX_NUMERIC_PROMPT *row = (GX_PROMPT *)widget;
GX_BOOL result;
GX_RECTANGLE size;

    gx_widget_created_test(widget, &result);

    if(!result)
    {
        gx_numeric_prompt_create(row, "", wheel, 0, GX_STYLE_ENABLED, 0, &size);
    }

    gx_numeric_prompt_value_set(row, index);
}

/* Create "generic_wheel” with 20 rows.  */
status = gx_generic_scroll_wheel_create(&generic_wheel, “generic_wheel”, &parent, 20, row_create,
                                       GX_STYLE_ENABLED, WHEEL_ID, &size);

/* If status is GX_SUCCESS the generic scroll wheel "generic_wheel”" has been created. */

/* Create children for generic scroll wheel.  */
for(index = 0; index <= VISIBLE_ROWS; index++)
{
    row_create(generic_wheel, (GX_WIDGET *)&row_memory[index], index);
}
```

### <a name="see-also"></a>Se även

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_draw"></a>gx_generic_scroll_wheel_draw
### <a name="draw-window"></a>Fönstret Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_generic_scroll_wheel_draw(GX_GENERIC_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>Description

Den här tjänsten ritar ett allmänt rullningshjul. Den här tjänsten anropas vanligtvis internt under arbetsyteuppdateringen, men kan även anropas från anpassade allmänna rullningshjulsritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Write a custom generic scroll wheel draw function. */

VOID my_custom_generic_scroll_wheel_draw(GX_GENERIC_SCROLL_WHEEL *wheel)
{
    /* Call default generic scroll wheel draw. */
    gx_generic_scroll_wheel_draw(wheel);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Se även

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_event_process"></a>gx_generic_scroll_wheel_event_process
### <a name="process-generic-scroll-wheel-event"></a>Bearbeta allmän rullningshjulshändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_generic_scroll_wheel_event_process(
    GX_GENERIC_SCROLL_WHEEL *wheel, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för det här fönstret.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **händelse** Pekare till händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad generisk bearbetning av rullningshjulshändelse
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Call generic generic scroll wheel event processing as part of custom event processing function. */

UINT custom_generic_scroll_wheel_event_process(GX_GENERIC_SCROLL_WHEEL *wheel,
                                               GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:

            /* Insert custom event handling here */
            break;

        default:

            /* Pass all other events to the default generic scroll wheel
            event processing */
            status = gx_generic_scroll_wheel_event_process(wheel, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>Se även

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_row_height_set"></a>gx_generic_scroll_wheel_row_height_set


Tilldela radhöjden för varje hjulrad

### <a name="prototype"></a>Prototyp

```C
UINT gx_generic_scroll_wheel_row_height_set(
    GX_GENERIC_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar radhöjden för varje rad i rullningshjulet.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till det allmänna kontrollblocket för rullningshjul
- **row_height** Radhöjdsvärde i bildpunkter.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har ställt in rullningshjulets höjd
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Ogiltig radhöjd

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_generic_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>Se även

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_total_rows_set"></a>gx_generic_scroll_wheel_total_rows_set


Tilldela de totala tillgängliga rullningshjulsraderna

### <a name="prototype"></a>Prototyp

```C
UINT gx_generic_scroll_wheel_total_rows_set(
    GX_GENERIC_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar eller ändrar det totala antalet generiska rader med rullningshjul.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt allmänt kontrollblock för rullningshjul
- **total_rows** Totalt antal hjulrader som ska visas för användaren.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett allmän rad för totalt antal rullningshjul
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Ogiltigt antal rader totalt

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
status = gx_generic_scroll_wheel_total_rows_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 20 total rows */
```
### <a name="see-also"></a>Se även

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set

## <a name="gx_horizontal_list_children_position"></a>gx_horizontal_list_children_position


Placera underordnade för den vågräta listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_children_position(GX_HORIZONTAL_LIST *horizontal_list);
```

### <a name="description"></a>Description

Den här funktionen placerar underordnade för den vågräta listan. Den här funktionen anropas automatiskt när listan tar GX_EVENT_SHOW händelse, men bör anropas direkt om listan ändras när den har gjorts synlig.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Pekare till kontrollblocket för vågrät lista

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades placerade underordnade för den vågräta listan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en vågrät lista.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontrollblock för vågrät lista
- **namn** Namn på vågrät lista
- **överordnad** Pekare till överordnad widget
- **total_columns** Totalt antal comumn i vågrät lista
- **motringning** Det här är en pekare till en återanropsfunktion som tillhandahålls av programmet. Återanropsfunktionen anropas när den vågräta listan rullas för att skapa de nyligen synliga listobjekten. På så sätt kan den vågräta listan visa alla användardefinierade widgettyper som listobjekt.
- **style (stil)** Stil på rullningslistswidgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **horizontal_list_id** Programdefinierat ID för vågrät lista
- **storlek** Dimensioner för horizonallistan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Den vågräta listan har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_VALUE** (0x22) Antal kolumner som inte är giltiga

### <a name="allowed-from"></a>Tillåts från

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


Bearbeta vågrät listhändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den vågräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontrollblock för vågrät lista
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Vågrät lista-händelse har bearbetats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange index för startsidan

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_page_index_set(
    GX_HORIZONTAL_LIST *list,
    INT *index);
```

### <a name="description"></a>Description

Den här tjänsten anger startindexet för den vågräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontrollblock för vågrät lista
- **index** Det nya toppindexet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett index för startsidan för den vågräta listan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde

### <a name="allowed-from"></a>Tillåts från

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


Hämta valt postindex från vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_selected_index_get(
    GX_horizobntal_LIST *horizontal_list,
    INT *return_index);
```

### <a name="description"></a>Description

Den här tjänsten returnerar det valda listpostindexet för den vågräta listan.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontrollblock för vågrät lista
- **return_index** Mål för index för returlista

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades fick den vågräta listposten
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Tilldela den valda posten i en vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_selected_set(
    GX_HORIZONATAL_LIST *horizontal_list,
    INT index);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den valda posten i en vågrät lista. Om det behövs bläddrar den vågräta listan för att göra den valda posten synlig.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontrollblock för vågrät lista
- **index** Indexbaserad position för ny listpost

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange den vågräta listposten
- **GX_FAILURE** (0x10) Indexet är inte i ett ogiltigt intervall
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Hämta markerad post från vågrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_selected_widget_get(
    GX_horizobntal_LIST *horizontal_list,
    GX_WIDGET **return_list_entry);
```

### <a name="description"></a>Description

Den här tjänsten returnerar den valda listposten i den vågräta listan. Observera att om den vågräta listan har fler rader än underordnade widgetar och den valda posten har rullats från vyn, returnerar detta API GX_NULL eftersom underordnade widgetar används igen när listinnehållet rullas. Funktionen gx_horizontal_list_selected_index_get returnerar indexet för det valda objektet på ett tillförlitligt sätt, även om objektet har bläddrats från vyn.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontrollblock för vågrät lista
- **return_list_entry** Mål för widget för returlista

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades fick du den vågräta listposten
- **GX_FAILURE** (0x10) Vald widget har bläddrats från vyn i en lista med fler rader än underordnade klient.
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Tilldela det totala antalet listkolumner

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_list_total_columns_set(
    GX_HORIZONTAL_LIST *horizontal_list,
    INT count);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar det totala antalet kolumner som ska visas av den vågräta listan.

### <a name="parameters"></a>Parametrar

- **horizontal_list** Kontrollblock för vågrät lista
- **antal** Antal kolumner som ska visas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Antal tilldelade kolumner
- **GX_CALLER_ERROR** (0x10) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt antalsvärde

### <a name="allowed-from"></a>Tillåts från

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


Skapa vågrät rullningslist

### <a name="prototype"></a>Prototyp

```C
UINT gx_horizontal_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name,
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten skapar en vågrät rullningslist. ID:t för en vågrät rullningslist är fördefinierat (eftersom ett fönster måste veta hur händelser ska fångas upp från den) och storleken är automatisk (eftersom det måste fylla det överordnade fönstrets klientbredd). Om vi bestämmer oss för att tillåta rullningslisterna i klientområdet måste vi lägga till ytterligare en create-funktion med id- och storleksparametrarna.

### <a name="parameters"></a>Parametrar

- **rullningslist** Kontrollblock för rullningslistswidget
- **namn** Namn på rullningslist
- **överordnad** Pekare till överordnad widget
- **utseende** Utseendestrukturen definierar utseendet på rullningslisten. Om det här värdet GX_NULL använder rullningslisten det standardutseende som definieras av gx_system_scroll_appearance_get. Se bilaga **I för** definitionen av GX_SCROLLBAR_APPEARANCE struktur.
- **Stil** Stil på rullningslistswidgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en vågrät rullningslist
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar den angivna ikonknappwidgeten.

GX_ICON_BUTTON härleds från GX_BUTTON och stöder alla gx_button API-tjänster.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till ikonknappkontrollblock
- **namn** Logiskt namn på ikonknappwidget
- **överordnad** Pekare till den överordnade widgeten
- **icon_id** Resurs-ID för ikon
- **style (stil)** Ikonformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **icon_button_id** Knapp för programdefinierat ID för ikon
- **storlek** Ikonens dimensioner

### <a name="return-values"></a>Returvärden

- **ikonknappen GX_SUCCESS** (0x00) Har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar ikonknappen. Den här funktionen anropas vanligtvis internt av GUIX som en del av en uppdateringsåtgärd för arbetsytan, men den exponeras även för programmet som kanske vill tillhandahålla en anpassad ritningsfunktion och anropar standardikonknappritningen som anpassad ritningsbas.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till ikonknappkontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange pixelkarta till ikonknappwidgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_button_pixelmap_set(
    GX_ICON_BUTTON *button,
    GX_RESOURCE_ID icon_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en ny pixelkarta till ikonknappwidgeten.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till ikonknappkontrollblock
- **icon_id** Resurs-ID för pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett ikonknapp pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Bakgrund för ikonen Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_icon_background_draw(GX_ICON *icon);
```

### <a name="description"></a>Description

Den här tjänsten ritar bakgrunden till den angivna ikonwidgeten. Den här tjänsten anropas vanligtvis internt av gx_icon_button_draw-funktionen, men exponeras för programmet för att hjälpa till att skriva anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **ikon** Pekare till kontrollblock för ikonwidget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar den angivna ikonwidgeten.

### <a name="parameters"></a>Parametrar

- **ikon** Pekare till ikonkontrollblock
- **namn** Logiskt namn på ikonwidget
- **överordnad** Pekare till den överordnade widgeten
- **pixelmap_id** Resurs-ID för pixelkarta
- **style** Ikonformat
- **icon_id** Programdefinierat ID för ikon
- **x** Starta x-koordinatposition
- **y** Startar y-koordinatposition

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ikonen Skapa
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Ikonen Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_icon_draw(GX_ICON *icon);
```

### <a name="description"></a>Description

Den här tjänsten ritar den angivna ikonwidgeten. Den här tjänsten anropas vanligtvis internt av GUIX som en del av en uppdateringsåtgärd för arbetsytan, men den exponeras även för programmet som kanske vill tillhandahålla en anpassad ritningsfunktion och anropa standardikonritningen som anpassad ritningsbas.

### <a name="parameters"></a>Parametrar

- **ikon** Pekare till kontrollblock för ikonwidget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Händelsebearbetning för ikonwidget

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_event_process(
    GX_ICON *icon, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten hanterar händelser som skickas till en GX_ICON widget.

### <a name="parameters"></a>Parametrar

- **ikon** Pekare till kontrollblock för ikonwidget
- **event_ptr** Pekare till GX_EVENT struktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Händelse för lyckad bearbetad ikon
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange pixelkarta för ikon

### <a name="prototype"></a>Prototyp

```C
UINT gx_icon_pixelmap_set(
    GX_ICON *icon, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id);
```

### <a name="description"></a>Description

Den här tjänsten anger pixelkartan för den angivna ikonwidgeten.

### <a name="parameters"></a>Parametrar

- **ikon** Pekare till kontrollblock för ikonwidget
- **normal_id** Resurs-ID för normalt tillstånd
- **selected_id** Resurs-ID för valt tillstånd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad ikon för pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Skapa en instans av bildläsarmodulen

### <a name="prototype"></a>Prototyp

```C
UINT gx_image_reader_create(
    GX_IMAGE_READER *image_reader,
    GX_CONST GX_UBYTE *data, 
    INT data_size,
    GX_UBYTE color_format, 
    GX_UBYTE mode);
```

### <a name="description"></a>Description

Den här funktionen skapar en raw-bildläsare/-avkodare för körning. För närvarande stöds endast jpeg- och png-raw-bildtyper. Den här tjänsten GX_SOFTWARE_DECODER_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **image_reader** Kontrollblock för bildläsare
- **data** Pekare till rådata för indata.
- **data_size** Storleken på indata i rådata.
- **color_format** Det begärda färgformatet för utdata.
- **läge** Komprimera, dithera och alfalägen flaggor.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en bildläsare
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltig datastorlek

### <a name="allowed-from"></a>Tillåts från

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


Definiera bildläsarpalett

### <a name="prototype"></a>Prototyp

```C
UINT gx_image_reader_palette_set(
    GX_IMAGE_READER *image_reader,
    GX_COLOR *pal,
    UINT palsize);
```

### <a name="description"></a>Description

Den här tjänsten anger paletten för bildläsarkontrollblock. Den här tjänsten GX_SOFTWARE_DECODER_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **image_reader** Kontrollblock för bildläsare
- **pal** Pekare till paletten
- **palsize** Storleken på paletten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Paletteuppsättningen för bildläsaren lyckades
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltig palettestorlek

### <a name="allowed-from"></a>Tillåts från

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

Starta dekomprimerings- och konverteringsprocessen

### <a name="prototype"></a>Prototyp

```C
UINT gx_image_reader_start(
    GX_IMAGE_READER *image_reader, 
    GX_PIXELMAP *outmap);
```

### <a name="description"></a>Description

Den här tjänsten avkodar en raw-bild till ett angivet färgformat. För närvarande stöds endast jpeg- och png-raw-bildtyper. Detta kräver GX_SOFTWARE_DECODER_SUPPORT måste definieras.

### <a name="parameters"></a>Parametrar

- **image_reader** Kontrollblock för bildläsare
- **pixelkarta** Pixelkarta för utdata

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad avbildningsavkodning
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnestilldelningen har inte definierats eller så misslyckades minnesallokeringen
- **GX_NOT_SUPPORTED** (0x28) Bildtyp eller format för utdatafärg stöds inte
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Rita linjediagram x,y-axel

### <a name="prototype"></a>Prototyp

```C
VOID gx_line_chart_axis_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Description

Den här tjänsten ritar x,y-axeln i ett linjediagram. Parametrarna för axelfärger och linjebredd hämtas från linjediagrammets informationsstruktur.

Den här tjänsten anropas vanligtvis internt av gx_line_chart_draw-funktionen, men exponeras för programmet för att hjälpa till att skriva anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **diagram** Kontrollblock för linjediagram.

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar ett linjediagramsfönster. Diagramritningsparametrarna och diagramdata skickas via GX_LINE_CHART_INFO struktur.

GX_LINE_CHART baseras på GX_WINDOW och stöder alla GX_WINDOW API:er.

### <a name="parameters"></a>Parametrar

- **diagram** Pekare till GX_LINE_CHART kontrollblocket.
- **namn** Valfritt linjediagramnamn
- **överordnad** Överordnad widget eller GX_NULL
- **info** Struktur som definierar ritningsparametrar för linjediagram. **Bilaga I** innehåller definition GX_LINE_CHART_INFO struktur.
- **style** Flaggor för widgetformat
- **chart_id** Diagram för logiskt ID-värde
- **storlek** Rektangel för diagramfönstersrektangel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa linjediagram
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats

### <a name="allowed-from"></a>Tillåts från

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


Rita linjediagramsdatalinje

### <a name="prototype"></a>Prototyp

```C
VOID gx_line_chart_data_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Description

Den här tjänsten ritar linjediagrammets datalinje. Parametrarna för linjefärger och linjebredd hämtas från linjediagrammets informationsstruktur.

Den här tjänsten anropas vanligtvis internt av gx_line_chart_draw-funktionen, men exponeras för programmet för att hjälpa till att skriva anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **diagram** Kontrollblock för linjediagram

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Rita linjediagrammet

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Description

Det här är standardritningsfunktionen för linjediagram, som ritar diagramaxeln och datalinjen. Program tillhandahåller vanligtvis en anpassad ritningsfunktion som ersätter standardritningen för att lägga till saker som bockmarkeringar, skalning eller annan information till diagramaxeln och datalinjen som ritas av baslinjediagramwidgeten.

### <a name="parameters"></a>Parametrar

- **diagram** Pekare till kontrollblocket för linjediagram.

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Uppdatera linjediagrammets datalinje

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_update(
    GX_LINE_CHART *chart, 
    INT *data,
    INT data_count)
```

### <a name="description"></a>Description

Den här tjänsten uppdaterar datamatrisen som ritats av linjediagramsfönstret och tvingar fönstret att rita om.

### <a name="parameters"></a>Parametrar

- **diagram** Kontrollblock för linjediagram
- **data** Datamatris som ska ritas
- **data_count** Storleken på datamatrisen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa textknapp
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Beräkna skalningsvärde för fast punkt-y-axel

### <a name="prototype"></a>Prototyp

```C
UINT gx_line_chart_y_scale_calculate(
    GX_LINE_CHART *chart,
    INT *return_val);
```

### <a name="description"></a>Description

Den här tjänsten beräknar det skalningsvärde med fast punkt som används för att rita datavärden på diagrammets Y-axel. Rektangeln chart_info och diagramrektangeln används för att beräkna det här skalningsvärdet.

### <a name="parameters"></a>Parametrar

- **diagram** Kontrollblock för linjediagram
- **return_val** Adress för värdet som ska innehålla returvärdet för fast punkt.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Beräkna ett lyckat y-skalningsvärde
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en meny som anges och associerar menyn med den angivna överordnade widgeten. Den accepterar alla typer av widget som underordnade menyalternativ. Om du vill infoga en widget som ett underobjekt, **anropar du gx_menu_insert**.

GX_MENU härleds från GX_PIXELMAP_PROMPT och stöder alla gx_pixelmap_prompt API-tjänster.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock
- **namn** Namnet på menyn
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för text
- **fill_id** Resurs-ID för fyllning
- **style (stil)** Widgetens stil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **menu_id** Programdefinierat ID för menyn
- **storlek** Menyns storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Menyn har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Menyn Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_menu_draw(GX_MENU *menu);
```

### <a name="description"></a>Description

Den här tjänsten ritar den angivna menyn. Den här funktionen anropas vanligtvis internt av GUIX-arbetsyteuppdateringsmekanismen, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade menywidgetar.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Processmenyhändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_event_process(GX_MENU *menu, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna menyn. Den här tjänsten ska anropas som standardhändelsehanterare av anpassade funktioner för menyhändelsebearbetning.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad menyhändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x23) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten infogar ett nytt objekt på menyn.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock
- **widget** Pekare till widgeten som ska infogas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Infogat nytt objekt i menyn
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort ett objekt från menyn.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock
- **widget** Pekare till widget att ta bort

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Menyalternativet har tagits bort
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Text i Rita-menyn

### <a name="prototype"></a>Prototyp

```C
VOID gx_menu_text_draw(GX_MENU *menu);
```

### <a name="description"></a>Description

Den här tjänsten ritar texten i en meny. Den här funktionen anropas vanligtvis internt av GUIX-mekanismen för arbetsyteuppdatering, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade menywidgetar.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange förskjutning i menytext

### <a name="prototype"></a>Prototyp

```C
UINT gx_menu_text_offset_set(
    GX_MENU *menu, 
    GX_VALUE x_offset,
    GX_VALUE y_offset);
```

### <a name="description"></a>Description

Den här tjänsten anger x, y visningsförskjutning för menytext.

### <a name="parameters"></a>Parametrar

- **meny** Pekare till menykontrollblock
- **x_offset** X koordinat för offset
- **y_offset** Y-koordinat för offset

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad förskjutning i set-menytext
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Knappen Skapa flerradstext

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget med flerradig textknapp. En textknapp med flera rader visar knapptexten över 1 n rader. Det maximala antalet rader definieras av konstanten GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES, som standard är 4. Radbrytningarna anges med vagnretur och/eller vagnretur + radmatningspar i textsträngen som tilldelats till flerradstextknappen.

GX_MULTI_LINE_TEXT_BUTTON härleds från GX_TEXT_BUTTON och stöder alla gx_text_button API-tjänster.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till textknappens kontrollblock
- **namn** Textknappens logiska namn
- **överordnad** Pekare till överordnad widget för knappen
- **text_id** Resurs-ID för text
- **style** Textknappstil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **text_button_id** Programdefinierat ID för textknappen
- **storlek** Knappens storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en textknapp med flera linjer
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Knappen Rita flerradstext

### <a name="prototype"></a>Prototyp

```C
VOID gx_multi_line_text_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button);
```

### <a name="description"></a>Description

Den här tjänsten ritar textknappen med flera linjer. Den här funktionen anropas vanligtvis internt av GUIX som en del av en uppdateringsåtgärd för arbetsytan, men den exponeras även för det program som kanske vill tillhandahålla en anpassad ritningsfunktion och anropar standardritningen för flerradig textknapp som anpassad ritningsbas.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till textknappens kontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Standardhändelsehantering för flerradstextknapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_button_event_process(
    GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten är standardfunktionen för händelsehantering för widgeten för flerradig textknapp. Den här funktionen görs tillgänglig för program som vill tillhandahålla anpassad händelsehantering för en textknappwidget.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till textknappens kontrollblock
- **event_ptr** Händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hanterad händelse
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Stödfunktion för ritning

### <a name="prototype"></a>Prototyp

```C
VOID gx_multi_line_text_button_text_draw(GX_MULTI_LINE_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Description

Den här stödfunktionen ritar textdelen av en flerradstextknapp. Den här funktionen anropas internt av gx_multi_line_text_button_draw() och tillhandahålls som ett separat API för program som definierar en anpassad funktion för flerradig textknappsritning. Program som vill anpassa knappbakgrundsritningen kan tillhandahålla sin anpassade ritningsfunktion och anropa multi_line_text_button_text_draw-tjänsten som en del av sin anpassade ritning för att rita knapptexten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till textknappens kontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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


Ange textresurs-ID till textknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_button_text_id_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id)
```

### <a name="description"></a>Description

Den här tjänsten anger det angivna strängresurs-ID:t till textknappen. Strängen kan innehålla tecken på ny rad som visar texten på flera rader i knappområdet.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till textknappens kontrollblock
- **string_id** Resurs-ID för strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange strängresurs-ID till textknappen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Tilldela text till textknappen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_button_text_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_multi_line_text_button_text_set_ext().

Den här tjänsten tilldelar den angivna strängen till textknappen. Om text_button-widgeten har skapats med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade textsträngen och därför måste gx_system_memmory_allocate_set-API:et anropas en gång innan den här tjänsten begärs. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste strängen vara statisk eller globalt allokerad, det vill säga det kanske inte är en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till textknappkontrollblock
- **text** pekare till den NULL-avslutade strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange texten till knappen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_MEMORY_ERROR** (0x30) Minnesbetoaren har inte definierats
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Tilldela text till textknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_button_text_set_ext(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_STRING *string)
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den angivna strängen till textknappen. Om text_button-widgeten har skapats med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade textsträngen och därför måste gx_system_memmory_allocate_set-API:et anropas en gång innan den här tjänsten begärs. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste strängen vara statisk eller globalt allokerad, det vill säga det kanske inte är en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till textknappkontrollblock
- **sträng pekare** till GX_STRING variabel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange texten till knappen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_MEMORY_ERROR** (0x30) Minnesbetoaren har inte definierats
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Ta bort ett tecken före textindatamarkörens position på flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_backspace(
    GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten tar bort tecknet före markörpositionen för textinmatning med flera rader. Den här tjänsten anropas internt när en down-händelse för backstegsnyckel tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckat backsteg för textinmatning med flera linjer
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x23) Widget är inte giltig
- **GX_FAILURE** (0x10) Ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåts från

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


Tar bort alla tecken från textinmatningsbufferten

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_buffer_clear(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla tecken från textindatabufferten.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textindatabuffert med flera linjer rensas
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Hämtar buffertinformation för textinmatningswidgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_buffer_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    GX_CHAR **buffer_address,
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar buffertinformation för en flerradig textinmatningswidget.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **buffer_address** Adressen för indatabufferten
- **content_size** Byteantalet för indata
- **buffer_size** Storleken på indatabufferten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad flerradstext get
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Infoga en teckensträng vid aktuell textindatamarkörsposition med flera linjer (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_char_insert(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Description

Det här API:et är inaktuellt och ersätts av gx_multi_line_text_input_char_insert_ext().

Den här tjänsten infogar en teckensträng i indatasträngsbufferten med flera linjer vid den aktuella markörpositionen. Den här tjänsten anropas internt när en specifik nyckel ned-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **insert_str** Teckensträng i UTF-8-format som ska infogas
- **insert_size** Antal byte som ska infogas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har infogat teckensträngen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Ogiltig strängstorlek
- **GX_FAILURE** (0x10) Ogiltigt teckensnitt eller utanför buffertstorleken

### <a name="allowed-from"></a>Tillåts från

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


Infoga en teckensträng vid aktuell textindatamarkörsposition med flera linjer (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_char_insert_ext(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten infogar en teckensträng i indatasträngsbufferten med flera linjer vid den aktuella markörpositionen. Den här tjänsten anropas internt när specifika ned-/ned-händelser tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **sträng** UTF-8-kodad teckensträng som ska infogas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har infogat teckensträngen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Ogiltig strängstorlek
- **GX_FAILURE** (0x10) Ogiltigt teckensnitt eller utanför buffertstorleken
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Skapa textinmatning med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_create(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WINDOW *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    ULONG style, USHORT text_input_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en widget för textinmatning med flera linjer.

GX_MULTI_LINE_TEXT_INPUT härleds från GX_MULTI_LINE_TEXT_VIEW och stöder alla gx_multi_line_text_view tjänster.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **namn** Namn på textinmatningswidget
- **överordnad** Pekare till överordnad widget
- **input_buffer** Pekare till textinmatningsbuffert
- **buffer_size** Storlek på buffert för textinmatning i byte
- **style (stil)** Stil på textinmatningswidgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **text_input_id** Programdefinierat ID för textinmatning
- **storlek** Dimensioner för textinmatningswidget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad flerradstextinmatning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Hämta textindatamarkörens position på flera rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_cursor_pos_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_POINT cursor_pos);
```

### <a name="description"></a>Description

Den här tjänsten hämtar markörpositionen för flerradig textinmatning.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **cursor_pos** Hämtad markörposition

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markörpositionen har hämtats
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ta bort tecknet vid markörpositionen för textinmatning på flera rader

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_delete(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten tar bort tecknet efter markörpositionen för textinmatning med flera rader. Den här tjänsten anropas internt när en borttagningsnyckel nedåt-händelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ta bort ett tecken efter markören
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_FAILURE** (0x10) Ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåts från

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


Flytta markören för textinmatning med flera linjer till nästa rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_down_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten placerar markören för textinmatningswidgeten med flera linjer till nästa rad. Den här tjänsten anropas internt när en nedåtpil nedåt-händelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Textinmatningsmarkören har flyttats till nästa rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_FAILURE** (0x10) Ogiltig teckensnitts- eller radhöjd

### <a name="allowed-from"></a>Tillåts från

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


Flytta markören för textinmatning med flera linjer till slutet av den aktuella raden

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_end(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten placerar widgetmarkören för textinmatning med flera linjer i slutet av den aktuella strängraden. Den här tjänsten anropas internt när en slutnyckel nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Textinmatningsmarkören har flyttats till slutet av den aktuella raden
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Standardhändelsehantering för textinmatning med flera rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_event_process(
    GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten är standardfunktionen för händelsehantering för flerradig textinmatningswidget. Den här funktionen görs tillgänglig för program som vill tillhandahålla anpassad händelsehantering för en textinmatningswidget med flera linjer.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till kontrollblock för textinmatning med flera linjer
- **event_ptr** Händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hanterad händelse
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ange bakgrundsfärg för textinmatning med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_fill_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar fyllningsfärger för flerradig textinmatningswidget.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **normal_fill_color_id** Resurs-ID för den normala fyllningsfärgen som används i normalt tillstånd
- **selected_fill_color_id** Resurs-ID för den valda fyllningsfärgen som används när widgeten får fokus
- **disabled_fill_color_id** Resurs-ID för den inaktiverade fyllningsfärgen som används när GX_STYLE_ENABLED inte är aktiv
- **readonly_fill_color_id** Resurs-ID för den skrivskyddade fyllningsfärg som används när både GX_STYLE_ENABLED och GX_STYLE_INPUT_READONLY är aktiva.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett färger för flerradstextinmatning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Flytta textinmatningsmarkören till början av den aktuella raden

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_home(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar markörpositionen för textinmatning till början av den aktuella raden. Den här tjänsten anropas internt när en hemnyckel nedåt-händelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till början av den aktuella raden
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Flytta textindatamarkören med flera linjer ett tecken till vänster

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_left_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar textindatamarkören med flera linjer ett tecken till vänster. Den här tjänsten anropas internt när en vänsternyckel nedåt-händelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till vänster
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_FAILURE** (0x10) Ogiltigt teckensnitt

### <a name="allowed-from"></a>Tillåts från

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


Flytta markören för flerradstextindata ett tecken till höger

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_right_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar textindatamarkören med flera linjer ett tecken till höger. Den här tjänsten anropas internt när en högernyckel nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till höger
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Lägga till format för textinmatning med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_style_add(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten lägger till format i en flerradig textinmatningswidget.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **style** Format som ska läggas till. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckat textinmatningsformat med flera rad, lägg till
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort de angivna formaten från flerradig textinmatningswidget.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **style** Format som ska tas bort. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad flerrads skapa textinmatning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Ange format för textinmatning med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_style_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten anger format för en flerradig textinmatningswidget.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **style** Format som ska anges. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad uppsättning flerradstextinmatning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange textfärg för textinmatning med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_text_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar textfärger för flerradig textinmatningswidget.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för textinmatningswidget med flera linjer
- **normal_fill_color_id** Resurs-ID för den normala textfärgen som används i normalt tillstånd
- **selected_text_color_id** Resurs-ID för den valda textfärgen som används när widgeten får fokus
- **disabled_text_color_id** Resurs-ID för den inaktiverade textfärg som används när GX_STYLE_ENABLED inte är aktiv
- **readonly_text_color_id** Resurs-ID för den skrivskyddade textfärg som används när både GX_STYLE_ENABLED och GX_STYLE_TEXT_INPUT_READONLY är aktiva

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett färger för flerradstextinmatningen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Välj text

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_text_select(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Description

Den här tjänsten väljer textinmatningstext med flera linjer med angivet start- och slutmarkeringsindex och markerar den markerade texten med den markerade fyllningen och textfärgerna.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med flera linjer
- **start_index** Index för det första markerade tecknet
- **end_index** Index för det senast valda tecknet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatningstextmarkering med flera linjer
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Indexvärdet är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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


Tilldela text till textinmatningen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CHAR *text);
```

### <a name="description"></a>Description

Det här API:et är inaktuellt och ersätts av gx_multi_line_text_input_text_set_ext().

Den här tjänsten tilldelar den angivna strängen till textinmatningen med flera linjer. Om multi_line_text_input widgetens indatabuffertstorlek är mindre än stränglängden trunkeras strängen.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med flera linjer
- **text** pekare till den NULL-avslutade strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange texten till flerradstextinmatning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Tilldela text till textinmatningen

### <a name="prototype"></a>Prototyp

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den angivna strängen till flerradig textinmatning. Om multi_line_text_input widgetens indatabuffertstorlek är mindre än stränglängden trunkeras strängen.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med flera linjer
- **sträng pekare** till GX_STRING ska tilldelas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange texten till flerradstextinmatning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Flytta markören för textinmatning med flera linjer till föregående rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_input_up_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar textindatamarkören med flera linjer till föregående textrad. Den här tjänsten anropas internt när en uppåtpil nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till föregående rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Skapa flerradstextvy

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

### <a name="description"></a>Description

Den här tjänsten skapar en GX_MULTI_LINE_TEXT_VIEW widget. Den här widgettypen härleds från GX_WINDOW och därför kan alla gx_window API-tjänster också användas med den här widgettypen.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för flerradswidget för textvy
- **namn** Namnet på textvywidgeten
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för textsträngen
- **style** Format för textvywidgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **text_view_id** Programdefinierat ID för textvyn
- **storlek** Dimensioner för textvywidget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En flerradswidget för textvy har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Rita en flerradswidget för textvy

### <a name="prototype"></a>Prototyp

```C
VOID gx_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW * text_view);
```

### <a name="description"></a>Description

Den här tjänsten ritar en flerradig textvywidget. Den här tjänsten anropas vanligtvis internt under arbetsyteuppdateringen, men kan även anropas från anpassade ritningsfunktioner för flerradig textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för flerradswidget för textvy

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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


Bearbeta textvisningshändelse med flera rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_event_process(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för en widget med flerradig textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för widget med flerradsvy
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad händelseprocess för textvisning med flera linjer
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange teckensnitt som används i textvyn med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

Den här tjänsten anger teckensnittet för en widget för flerradig textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för widget med flerradsvy
- **font_id** Resurs-ID för teckensnittet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Teckensnitt har angetts för textvyn med flera linjer
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange radutrymme för flerradsvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_line_space_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_BYTE line_space);
```

### <a name="description"></a>Description

Den här tjänsten anger avståndet mellan textrader för widgeten för flerradig textvy.

### <a name="parameters"></a>Parametrar

- **visa** Kontrollblock för flerradswidget för textvy
- **line_space** Värde att ange

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange radutrymmesvärde för flerradstextvyn
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Hämta information om rullningslisten för flerradsvyn


### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_scroll_info_get(
    GX_MULTI_LINE_TEXT_VIEW *text_view, ULONG style,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten hämtar rullningsinformationen för flerradig textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för flerradswidget för textvy
- **Stil** GX_SCROLLBAR_HORIZONTAL eller GX_SCROLLBAR_VERTICAL
- **Information** Pekare till mål för rullningsinformation. **Bilaga I** innehåller en definition GX_SCROLL_INFO struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Rullningsinformationen för textvyn har hämtats
- **GX_FAILURE** (0x10) Widget är inte synlig eller textvisningens teckensnitts-ID är inte giltigt
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange textfärgen för flerradstextvyn

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_color_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCe_ID disabled_text_color_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar textfärg till flerradig textvisningswidget.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för flerradswidget för textvy
- **normal_text_color_id** Resurs-ID för den normala textfärgen som används i normalt tillstånd
- **selected_text_color_id** Resurs-ID för den valda textfärgen som används när widgeten får fokus
- **disabled_text_color_id** Resurs-ID för den inaktiverade textfärgen som GX_STYLE_ENABLED är inte aktiv

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett färger för textvyn med flera linjer
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange systemets textsträng i textvyn med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID text_id);
```

### <a name="description"></a>Description

Den här tjänsten anger resurs-ID för en sträng till widgeten för flerradig textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för widget med flerradsvy
- **text_id** Resurs-ID för textsträngen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange sträng-ID för flerradstextvyn
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID

### <a name="allowed-from"></a>Tillåts från

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


Ange användardefinierad sträng i textvyn med flera linjer

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_text_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en textsträng till widgeten för flerradig textvy. Om text_view-widgeten har skapats med format GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade textsträngen och därför måste gx_system_memory_allocate_set-API:et anropas en gång innan den här tjänsten begärs. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste den tilldelade strängen allokeras statiskt eller globalt, det vill säga det kanske inte är en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för widget med flerradsvy
- **text** NULL-avslutad textsträng

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett strängen för flerradstextvyn
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnestilldelning har inte definierats eller så misslyckades minnesallokeringen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange tomt utrymme för flerradstextvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_multi_line_text_view_whitespace_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_UBYTE whitespace);
```

### <a name="description"></a>Description

Den här tjänsten anger avståndet mellan widgetens konturer och klientområdet för en widget med flerradig textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Kontrollblock för widget med flerradsvy
- **tomt utrymme** Bredd på marginalen mellan text_view widget och den visade texten, i bildpunkter.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett tomt utrymme för flerradstextvyn
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Skapa en fråga för numerisk pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_pixelmap_prompt_create(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, GX_RESOURCE_ID fill_id,
    ULONG style, USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en widget med en numerisk pixelkarta. En numeric_pixelmap_prompt är bara en pixelmap_prompt som behåller sin egen buffert och tillhandahåller ett GX_NUMERIC_PIXELMAP_PROMPT_VALUE_SET(INT)-API definieras buffertstorleken av konstanten GX_NUMERIC_PROMPT_BUFFER_SIZE, som standard är 16.

GX_NUMERIC_PIXELMAP_PROMPT härleds från GX_PIXELMAP_PROMPT och stöder alla gx_pixelmap_prompt API-tjänster.

### <a name="parameters"></a>Parametrar

- **prompt** Kontrollblock för numerisk pixelkarta
- **namn** Namn på fråga
- **överordnad** Kontrollblock för överordnad widget
- **text_id** Resurssträngs-ID
- **fill_id** Pixelkartans ID för fyllningsområdet
- **style (stil)** Stil för numerisk pixelkarta, **bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-specifika format.
- **pixelmap_prompt_id** Programdefinierat ID för prompt
- **storlek** Fråga om dimensioner för numerisk pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en numerisk pixlemap-prompt
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Funktionen Åsidosätt format i fråga om numerisk pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_pixelmap_format_function_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    OID (*format_func)(GX_NUMERIC_PIXELMAP_PROMPT *, INT));
```

### <a name="description"></a>Description

Den här tjänsten åsidosätter standardformatfunktionen för widgeten för numerisk pixlemap-prompt. Standardformatfunktionen konverterar det numeriska pixelkarta-promptvärdet till en sträng och lagrar det i widgetens privata buffert. Med den här tjänsten kan programmet definiera en egen formatfunktion för att formatera och lagra det numeriska pixelkarta-promptvärdet i widgetens privata buffert.

### <a name="parameters"></a>Parametrar

- **prompt** Kontrollblock för numerisk pixelkarta
- **format_func** Funktionen Format som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange funktionen för numeriskt pixlemap-format
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange numeriskt promptvärde för pixlemap

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_pixelmap_prompt_value_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value);
```

### <a name="description"></a>Description

Den här tjänsten är ett heltalsvärde till en numerisk bildpunktskarta.

### <a name="parameters"></a>Parametrar

- **prompt** Kontrollblock för numerisk pixelkarta
- **värde** Heltalsvärde som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange promptvärdet numerisk pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för numerisk prompt. En numeric_ fråga är bara en prompt som behåller sin egen buffert och tillhandahåller ett GX_NUMERIC_ PROMPT_VALUE_SET(INT) API. Buffertstorleken definieras av konstanten GX_NUMERIC_PROMPT_BUFFER_SIZE, som standard är 16.

GX_NUMERIC_PROMPT härleds från GX_PROMPT och stöder alla gx_prompt API-tjänster.

### <a name="parameters"></a>Parametrar

- **prompt** Kontrollblock för numerisk prompt
- **namn** Namn på fråga
- **överordnad** Kontrollblock för överordnad widget
- **text_id** Resurssträngs-ID
- **style (stil)** Format för numerisk prompt, **bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widget-specifika format.
- **prompt_id** Programdefinierat ID för prompt
- **storlek** Dimensioner för numerisk prompt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Frågor om numerisk autentisering
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Funktionen Åsidosätt format för numerisk prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_format_function_set(
    GX_NUMERIC_PROMPT *prompt,
    VOID (*format_func)(GX_NUMERIC_PROMPT *, INT));
```

### <a name="description"></a>Description

Den här tjänsten åsidosätter standardformatfunktionen för en numerisk promptwidget. Standardformatfunktionen konverterar det numeriska promptvärdet till en sträng och lagrar det i widgetens privata buffert. Med den här tjänsten kan programmet definiera en egen formatfunktion för att formatera och lagra det numeriska promptvärdet i widgetens privata buffert.

### <a name="parameters"></a>Parametrar

- **prompt** Kontrollblock för numerisk prompt
- **format_func** Funktionen Format som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Funktionen för numerisk promptformat har angetts
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange numeriskt promptvärde

### <a name="prototype"></a>Prototyp

```C
UINT gx_numeric_prompt_value_set(
    GX_NUMERIC_PROMPT *prompt, 
    INT value);
```

### <a name="description"></a>Description

Den här tjänsten anger ett heltalsvärde till en numerisk prompt.

### <a name="parameters"></a>Parametrar

- **prompt** Kontrollblock för numerisk prompt
- **värde** Heltalsvärde som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange numeriskt promptvärde
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Skapa numeriska rullningshjul

### <a name="prototype"></a>Prototyp


UINT gx_numeric_scroll_wheel_create( GX_NUMERIC_SCROLL_WHEEL *wheel, GX_CONST GX_CHAR *name, GX_WIDGET *parent, INT start_val, INT end_val, ULONG style, USHORT wheel_id, GX_CONST GX_RECTANGLE *size);

### <a name="description"></a>Description

Den här tjänsten skapar en widget för numeriska rullningshjul.

Ett numeriskt rullningshjul är en typ av widget för rullningshjul som används specifikt för att visa ett intervall med siffror. Andra typer av widgetar för rullningshjul är också tillgängliga. Mer information om hierarkin för rullningshjulswidget, widgettyper och widgetar finns i API:et gx_scroll_wheel_create() .

GX_NUMERIC_SCROLL_WHEEL härleds från GX_TEXT_SCROLL_WHEEL och stöder alla gx_text_scroll_wheel och gx_scroll_wheel tjänster.

Alla typer av rullningshjul GX_EVENT_LIST_SELECT händelser till sin överordnade när rullningshjulet rullas.

Ett numeriskt rullningshjul har som standard abs(end_val – start_val) + 1 rader. Med andra ord visar rullningshjulet varje värde mellan start_val och end_val öka eller minska med 1 för varje rad. Observera att start_val kan vara större eller mindre end_val, beroende på hur programmet vill att intervallet ska visas.

Om programmet vill ändra radsteget kan det göra detta genom att anropa gx_scroll_wheel_total_rows_set() när du har skapat det numeriska rullningshjulet. Till exempel kan ett program som vill skapa ett rullningshjul som visar värdena år 1980 till 2020, öka med 5, göra detta:

```C
gx_numeric_scroll_wheel_create(&wheel, GX_NULL, parent, 1980,
    2020, style, id, &size);

/* the years 1980 through 2020, inclusive, incrementing by 5 years,
yields 9 total rows */

gx_scroll_wheel_total_rows_set(&wheel, 9);
```

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till kontrollblock för numeriska rullningshjul
- **namn** Logiskt namn på widgeten för pixelkarta-knappen
- **överordnad** Pekare till den överordnade widgeten
- **start_val** Starta numeriskt värde
- **end_val** Slut på numeriskt värde
- **style** Kryssruta för format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **wheel_id** Programdefinierat ID för rullningshjulet
- **storlek** Dimensioner för widget för rullningshjul

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Numeriskt rullningshjul har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Tilldela värdeintervall för numeriskt rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT
gx_numeric_scroll_wheel_range_set(
    GX_NUMERIC_SCROLL_WHEEL *wheel,
    INT start_val, INT end_val);
```

### <a name="description"></a>Description

Den här tjänsten ändrar det värdeintervall som tillåts och visas av en widget med numeriska rullningshjul.

Ett numeriskt rullningshjul är en typ av widget för rullningshjul som används specifikt för att visa ett intervall med siffror. Andra typer av widgetar för rullningshjul är också tillgängliga. Mer information om hierarkin för rullningshjulswidget, widgettyper och widgetar finns i API:et gx_scroll_wheel_create() .

När du anropar detta API återställs det totala antalet rader med rullningshjulet till abs(end_val – start_val) + 1, vilket innebär att rullningshjulet ökar med 1 för varje rad. Om du vill ändra detta kan programmet anropa gx_scroll_wheel_total_rows_set() för att ändra det totala antalet rader, vilket effektivt ändrar värdesteget mellan rader.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till kontrollblock för numeriska rullningshjul
- **start_val** Starta numeriskt värde 
- **end_val** Slut på numeriskt värde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange intervall för numeriska rullningshjul
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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


Knappen Skapa pixelkarta

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för pixelkartan.

GX_PIXELMAP_BUTTON härleds från GX_BUTTON och stöder alla gx_button tjänster.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till pixelkartans knappkontrollblock
- **namn** Logiskt namn på widgeten för pixelkarta-knappen
- **överordnad** Pekare till den överordnade widgeten
- **normal_id** Resurs-ID för normalt tillstånd
- **selected_id** Resurs-ID för valt tillstånd
- **disabled_id** Resurs-ID för inaktiverat tillstånd
- **style** Kryssruta för format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **pixelmap_button_id** Programdefinierat ID för knappen pixelkarta
- **storlek** Knappen Dimensions of pixelmap (Mått för pixelkarta)

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Knappen Pixelkarta har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Knappen Rita pixelkarta

### <a name="prototype"></a>Prototyp

```C
VOID gx_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button);
```

### <a name="description"></a>Description

Den här tjänsten ritar en pixelkarta-knappwidget. Den här funktionen anropas vanligtvis internt av GUIX-mekanismen för arbetsyteuppdatering, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade pixelkarta knappwidgetar.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till pixelkartans knappkontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Händelsebearbetning för bildpunktskarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_button_event_process(
    GX_PIXELMAP_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tillhandahåller standardhändelsehantering för widgettypen pixelkarta.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till pixelkartans knappkontrollblock
- **event_ptr** Pekare till GX_EVENT struktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Knapp draw för lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Knappen Tilldela pixelkartor till

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_button_pixelmap_set(
    GX_PIXELMAP_BUTTON *button, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id, 
    GX_RESOURCE_ID disabled_id);
```

### <a name="description"></a>Description

Den här tjänsten anger pixelkartor till knappen pixelkarta.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till pixelkartans knappkontrollblock
- **normal_id** Resurs-ID för pixelkartan som ska användas som normalt tillstånd
- **selected_id** Resurs-ID för pixelkartan som ska användas när knappen väljs
- **disabled_id** Resurs-ID för pixelkartan som ska användas när knappen är inaktiverad

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades anger pixelkartan till knappen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Uppmaning om att skapa pixelkarta

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för pixelkartan. En pixelkarta skiljer sig från en standard GX_PROMPT på så sätt att den färgar bakgrunden i prompten med pixelkartor. Funktionen create accepterar ett pixelkarta-ID, det normala tillståndet, pixelkarta. Upp till sex pixelkartor kan tilldelas till pixelkartan.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till kontrollblock för pixelkarta
- **namn** Logiskt namn på widgeten för pixelkartan
- **överordnad** Pekare till den överordnade widgeten
- **text_id** Resurs-ID för text
- **fill_id** Resurs-ID för fyllning
- **style (stil)** Kryssrutasstil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **pixelmap_prompt_id** Programdefinierat ID för bildpunktskarta
- **storlek** Uppmaning om dimensioner för pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en lyckad pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats

### <a name="allowed-from"></a>Tillåts från

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


Fråga om att rita pixelkarta

### <a name="prototype"></a>Prototyp

```C
VOID gx_pixelmap_prompt_draw(GX_PIXELMAP_PROMPT *prompt);
```

### <a name="description"></a>Description

Den här tjänsten ritar en widget för pixelkartan. Den här funktionen anropas vanligtvis internt av GUIX-arbetsytans uppdateringsmekanism, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade widgetar för pixelkartan.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till kontrollblock för pixelkarta

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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


Tilldela pixelkartor för att fråga

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

### <a name="description"></a>Description

Den här tjänsten tilldelar pixelkartans ID:n till pixelkartan. Id:n för vänster, fyllning och höger bildpunktskarta används för att tillåta att programmet använder en uppsättning pixelkartor för frågor med olika bredd men en gemensam höjd för att spara på lagringskraven. Om vänster- och höger-ID:erna inte används ska de anges till 0. Om uppmaningen ska rita sig själv på ett annat sätt när den får indatafokus används de valda pixelkartans ID:n för detta ändamål. Om de valda ID:na inte används eller är samma som vanliga ID:n anger du dem till 0.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till kontrollblock för pixelkarta
- **normal_left_id** Resurs-ID för pixelkartan som ska användas på vänster sida i normalt tillstånd
- **normal_fill_id** Resurs-ID för pixelkartan som ska användas som en panelfyllning i det normala tillståndet
- **normal_right_id** Resurs-ID för pixelkartan som ska användas på höger sida i normalt tillstånd
- **selected_left_id** Resurs-ID för pixelkartan som ska användas på vänster sida i det valda tillståndet
- **selected_fill_id** Resurs-ID för pixelkartan som ska användas som en panelfyllning i det valda tillståndet
- **selected_right_id** Resurs-ID för pixelkartan som ska användas på höger sida i det valda tillståndet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckades anger pixelkartan till prompten
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0x33) Resurs-ID är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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


Skapa skjutreglage för pixelkarta

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

### <a name="description"></a>Description

Den här tjänsten skapar en skjutreglagewidget för pixelkarta.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till skjutreglagets skjutreglage för pixelkarta
- **namn** Logiskt namn på skjutreglagewidgeten för pixelkarta
- **överordnad** Pekare till den överordnade widgeten
- **info** Pekare till GX_SLIDER_INFO struktur som innehåller värden som definierar skjutreglagets minsta värde, högsta värde, aktuellt värde och nålgränser. **Bilaga I** innehåller definition GX_SLIDER_INFO struktur.
- **pixelmap_info** Pekare till en GX_PIXELMAP_SLIDER_INFO struktur som definierar pixelkartor som används för att dra skjutreglagets bakgrund och nål. **Bilaga I** innehåller definition för GX_PIXELMAP_SLIDER_INFO struktur. Skjutreglagets bakgrund kan använda en eller två pixelkartor. Om den ena ändras inte bakgrunden när nålen rör sig. Om två bakgrunder definieras använder bakgrunden före nålen den första pixelkartan i bakgrunden och bakgrunden efter nålen använder den andra pixelkartan i bakgrunden.
- **style (stil)** Skjutreglagets stil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **pixelmap_slider_id** Programdefinierat ID för skjutreglaget pixelkarta
- **storlek** Uppmaning om dimensioner för pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skjutreglaget pixelkarta har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Skjutreglaget Rita pixelkarta

### <a name="prototype"></a>Prototyp

```C
VOID gx_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *slider);
```

### <a name="description"></a>Description

Den här tjänsten ritar en skjutreglagewidget för pixelkarta. Den här funktionen anropas vanligtvis internt av GUIX-mekanismen för arbetsyteuppdatering, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade skjutreglagewidgetar för pixelkarta.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till skjutreglagets pixelkarta

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Skjutreglagehändelse för process pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_slider_event_process(
    GX_PIXELMAP_SLIDER *slider,
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna skjutreglagewidgeten för pixelkarta.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till pixelkarta
- slider control block event Pointer to event to process **(skjutreglaget** blockerar händelse pekaren till den händelse som ska bearbetas)

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad händelseprocess för skjutreglaget för pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela pixelkartor till skjutreglaget

### <a name="prototype"></a>Prototyp

```C
UINT gx_pixelmap_slider_pixelmap_set(
    GX_PIXELMAP_SLIDER *slider,
    GX_PIXELMAP_SLIDER_INFO *pixinfo);
```

### <a name="description"></a>Description

Den här tjänsten anger pixelkartor till skjutreglaget för pixelkarta.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till skjutreglagets pixelkarta
- **pixinfo** Pekare till en GX_PIXELMAP_SLIDER_INFO struktur som definierar pixelkartor som används för att rita skjutreglagets bakgrund och nål. **Bilaga I** innehåller definition GX_PIXELMAP_SLIDER_INFO struktur. Skjutreglagets bakgrund kan använda en eller två pixelkartor. Om det finns en sådan ändras inte bakgrunden när nålen rör sig. Om två bakgrunder definieras använder bakgrunden före nålen den första pixelkartan i bakgrunden och bakgrunden efter nålen använder den andra pixelkartan i bakgrunden.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Anger pixelkartan till skjutreglaget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Förloppsfältsbakgrund för rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_progress_bar_background_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Description

Den här tjänsten ritar bakgrunden till den angivna förloppsfältet. Den här funktionen anropas internt som en del av gx_progress_bar_draw(), men exponeras för programmet för att stödja de fall där programmet definierar en anpassad förloppsritning.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till förloppsfältets kontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Skapa en förloppsstapel

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för förloppsfältet.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **namn** Logiskt namn
- **överordnad** Pekare till den överordnade widgeten
- **progress_bar_info** Pekare till en GX_PROGRESS_BAR_INFO struktur. **Bilaga I** innehåller definition GX_PROGRESS_BAR_INFO struktur.
- **style** Förloppsfältets format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **progress_bar_id** Programdefinierad ID för förloppsfältet
- **storlek** Förloppsfältets dimensioner

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa förloppsfältet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Rita en förloppsstapel

### <a name="prototype"></a>Prototyp

```C
VOID gx_progress_bar_draw(GX_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

Den här tjänsten ritar en widget för förloppsfältet. Den här funktionen anropas vanligtvis internt av GUIX-mekanismen för arbetsyteuppdatering, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade förloppslistwidgetar.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Förlopp för en förloppshändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_event_process(
    GX_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en förloppshändelse.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **event_ptr** Pekare till GX_EVENT struktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en kommandotolk
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange teckensnitt för förloppsfältets text

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_font_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

Den här tjänsten anger teckensnittet för en förloppsfältwidget.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **font_id** Resurs-ID för teckensnitt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Teckensnittsuppsättning för lyckad förloppsstapel
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange informationsstruktur för förloppsfältet

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_info_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten återställer informationsstrukturen för en förloppsfältwidget.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **info** Pekare till en GX_PROGRESS_BAR_INFO struktur. **Bilaga I** innehåller definition GX_PROGRESS_BAR_INFO struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Information om återställning av förloppsfältet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange pixelkarta som används för att rita förloppsstapeln

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_pixelmap_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Description

Den här tjänsten anger pixelkartan som används för att fylla förloppsfältets bakgrund.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **pixelmap_id** Resurs-ID för pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad förloppsdiagramsuppsättning för stapeldiagram
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange värdeintervall för en förloppsstapel

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_range_set(
    GX_PROGRESS_BAR *progress_bar,
    INT min_value, 
    INT max_value);
```

### <a name="description"></a>Description

Den här tjänsten anger förloppsfältets värdeintervall.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **min_value** Minimivärde för förloppsstapel
- **max_value** Maxvärde för förloppsstapel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad förloppsstapelintervalluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Ange textfärgen för en förloppsstapel

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_text_color_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Description

Den här tjänsten anger textfärgen för en förloppsfältwidget.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **normal_text_color** Resurs-ID för normal textfärg som används i normalt tillstånd
- **selected_text_color** Resurs-ID för vald textfärg som används när widgeten får fokus
- **disabled_text_color** Resurs-ID för inaktiverad textfärg som används när GX_STYLE_ENABLED inte är aktiv

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Textfärguppsättning för lyckad förloppsstapel
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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


Rita förloppsfältstext

### <a name="prototype"></a>Prototyp

```C
VOID gx_progress_bar_text_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Description

Den här tjänsten ritar texten i den angivna förloppsstapeln. Den här funktionen anropas internt som en del av gx_progress_bar_draw(), men exponeras för programmet för att stödja de fall där programmet definierar en anpassad förloppsritningfunktion.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till förloppsfältets kontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange aktuellt värde för en förloppsstapel

### <a name="prototype"></a>Prototyp

```C
UINT gx_progress_bar_value_set(
    GX_PROGRESS_BAR *progress_bar,
    INT value);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar det aktuella förloppsfältets värde. Widgeten för förloppsfältet ogiltigförklaras automatiskt och ritas om när förloppsfältets värde ändras.

### <a name="parameters"></a>Parametrar

- **progress_bar** Kontrollblock för förloppskontroller
- **värde** Aktuellt värde för förloppsfältet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange värdet för förloppsfältet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en promptwidget.

GX_PROMPT härleds från GX_WIDGET och stöder alla gx_widget tjänster.

### <a name="parameters"></a>Parametrar

- **Pekare** till den överordnade widgeten
- **text_id** Resurs-ID för prompttext
- **style (stil)** Promptformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **prompt_id** Programdefinierat ID för prompt
- **storlek** Dimensioner för prompt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Prompten skapas
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Draw prompt (Rita fråga)

### <a name="prototype"></a>Prototyp

```C
VOID gx_prompt_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Description

Den här tjänsten ritar en promptwidget. Den här tjänsten anropas internt av GUIX under uppdatering av arbetsytan, men kan även anropas av anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Händelse för processuppfråga

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna prompten. Den här tjänsten ska anropas som standardhändelsehanterare av alla anpassade funktioner för händelsebearbetning av prompter.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga efter kontrollblock
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad prompthändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten anger teckensnittet för en promptwidget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock
- **font_id** Resurs-ID för teckensnitt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckensnittsuppsättning för prompt
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ange textfärg för prompt

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_color_set(
    GX_PROMPT *prompt,
    GX_RESOURCE_ID normal_color,
    GX_RESOURCE_ID selected_color,
    GX_RESOURCE_ID disabled_color);
```

### <a name="description"></a>Description

Den här tjänsten anger textfärgen för en promptwidget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock
- **normal_color** Resurs-ID för färg för normal text. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **selected_color** Resurs-ID för färg för vald text som används när widgeten får fokus. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **disabled_color** Resurs-ID för färg för inaktiverad text som används när GX_STYLE_ENABLED inte är aktiv. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textfärguppsättning för prompt
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET_SIZE** (0x14) Ogiltig widgetstorlek

### <a name="allowed-from"></a>Tillåts från

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


Stödfunktion för ritning

### <a name="prototype"></a>Prototyp

```C
VOID gx_prompt_text_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Description

Den här stödfunktionen ritar textdelen av en prompt. Den här funktionen anropas internt av gx_prompt_draw() och tillhandahålls som ett separat API som en bekvämlighet för program som definierar en anpassad promptritningsfunktion. Program som vill anpassa promptens bakgrundsritning kan tillhandahålla sin anpassade ritningsfunktion och anropa gx_prompt_text_draw-tjänsten som en del av sin anpassade ritning för att rita prompttexten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare till promptkontrollblocket

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Hämta prompttext (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_CHAR **return_text);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_prompt_text_get_ext().

Den här tjänsten hämtar texten i en promptwidget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock
- **return_text** Pekare till mål för text

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Prompttext hämta
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Hämta prompttext

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_STRING *return_string);
```

### <a name="description"></a>Description

Den här tjänsten hämtar strängen för en promptwidget.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock
- **return_string** Pekare till mål för sträng

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Prompttext hämta
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ange text-ID för fråga

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_id_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID string_id);
```

### <a name="description"></a>Description

Den här tjänsten anger sträng-ID:t för widgeten för textuppfråga.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock
- **string_id** Resurs-ID för strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Prompttext-ID har angetts
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnesfri funktion har inte definierats

### <a name="allowed-from"></a>Tillåts från

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


Ange prompttext (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_set(
    GX_PROMPT *prompt, 
    GX_CHAR *text);
```

### <a name="description"></a>Description

Den här tjänsten har gjorts inaktuell till förmån för gx_prompt_text_set_ext().

Den här tjänsten anger texten för en promptwidget. Om promptwidgeten skapades med GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade textsträngen. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste strängen vara statisk eller globalt allokerad, det vill säga det kanske inte är en automatisk eller tillfällig variabel.

GX_PROMPT härleds från GX_WIDGET och därför kan alla GX_WIDGET API-tjänster användas med GX_PROMPT.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att fråga widgetkontrollblock
- **text** Pekare till text

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Prompttextuppsättningen lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnes allokerande funktion har inte definierats
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

Ange prompttext

### <a name="prototype"></a>Prototyp

```C
UINT gx_prompt_text_set_ext(
    GX_PROMPT *prompt,
    GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten anger texten för en promptwidget. Om promptwidgeten skapades med GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av textsträngen som tilldelats. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste strängen allokeras statiskt eller globalt, dvs. det kanske inte är en automatisk eller tillfällig variabel.

GX_PROMPT härleds från GX_WIDGET och därför kan alla GX_WIDGET API-tjänster användas med GX_PROMPT.

### <a name="parameters"></a>Parametrar

- **prompt** Pekare för att uppmana widgetkontrollblock
- **text** Pekare till text

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Prompttextuppsättningen lyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **funktionen GX_SYSTEM_MEMORY_ERROR** (0x30) Minnes allokera har inte definierats
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Ange startvinkel

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_anchor_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE angle);
```

### <a name="description"></a>Description

Den här tjänsten anger startvinkeln för radiell förloppsstapel.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsfält
- **vinkel** Startvinkel för cirkelformad båge

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad radiell förloppslist för ankaruppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar en bakgrund i radiell förloppsstapel. Den här tjänsten refereras internt av gx_radial_progress_bar_draw-funktionen, men exponeras för användning av programmet i de fall där programmet definierar en anpassad ritningsfunktion för radiell förloppsstapel

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsstapel

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Skapa radiell förloppsstapel

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

### <a name="description"></a>Description

Den här tjänsten skapar en radiell förloppsstapel.

Om widgetformatet GX_STYLE_ENABLED tillämpas på förloppsfältet accepterar förloppsfältet pen_down, pen_drag och pen_up indata för att ändra det aktuella värdet för förloppsfältet.

Widgetstilen GX_STYLE_PROGRESS_TEXT_DRAW användas för att aktivera ritning av förloppsstapelvärdet som text i förloppsfältet. Om det här formatet används i kombination med GX_STYLE_PROGRESS_PERCENT visas förloppsfältets värde i procent. Annars visas förloppsfältets värde som det aktuella angular-värdet.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontroll av radiell förloppsstapel
- **förloppsfält** Pekare till kontrollblock för radiell förloppsfält
- **namn** Namn på radiell förloppsstapel
- **överordnad** Pekare till överordnad widget
- **info** Pekare till en GX_RADIAL_PROGRESS_BAR struktur. **Bilaga I** innehåller definition GX_RADIAL_PROGRESS_BAR struktur.
- **style** Format för radiell förloppsstapel
- **id** Programdefinierad ID för förloppsfältet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad radiell förloppsstapel för att skapa
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_WIDGET** (0x12) Ogiltig överordnad widget

### <a name="allowed-from"></a>Tillåts från

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


Rita en radiell förloppsstapel

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

Den här tjänsten ritar en radiell förloppsstapel. Den här tjänsten används internt refererad av gx_radial_progress_bar_create-funktionen, men exponeras för användning av programmet i de fall där programmet definierar en anpassad förloppsritningsfunktionen för radiella förlopp.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsfält

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Förloppshändelse för processradiell förlopp

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_event_process(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en radiell förloppshändelse. Den här funktionen refereras internt av gx_radial_progress_bar_create-funktionen, men exponeras för användning av programmet i de fall där programmet definierar en anpassad funktion för radiell förloppshändelsebearbetning.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsfält
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad radiell förloppshändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange teckensnitt för radiell förloppsfält

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_font_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

Den här tjänsten anger teckensnittet för en widget för radiell förloppsfält. Den här parametern har ingen effekt om widgetformatet GX_STYLE_PROGRESS_TEXT_DRAW inte har angetts.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsfält
- **font_id** Resurs-ID för teckensnitt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad teckensnittsuppsättning för radiell förloppsfält
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange information om radiell förloppsfält

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_info_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RADIAL_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten återställer informationsparametrarna som tilldelats till radialförloppsfältet.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsfält
- **info** Pekare till informationsstrukturen för radiella förloppsfält. **Bilaga I** innehåller definition GX_RADIAL_PROGRESS_BAR_INFO struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Information om lyckad radiell förloppsfält
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange textfärg för radiell förloppsstapel

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_text_color_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Description

Den här tjänsten anger textfärgen för radiell förloppsstapel. Det här värdet används bara om GX_STYLE_PROGRESS_TEXT_DRAW har angetts.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsstapel
- **normal_color** Resurs-ID för textfärg i normalt tillstånd. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.
- **selected_color** Resurs-ID för textfärg när widgeten får fokus. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.
- **disabled_color** Resurs-ID för textfärg när GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textfärguppsättning för radiell förloppsstapel
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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


Rita radiell förloppsfälttext

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_progress_bar_text_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

Den här tjänsten ritar texten i angiven radiell förloppsstapel. Den här funktionen anropas internt som en del av gx_radial_progress_bar_draw(), men exponeras för programmet för att stödja de fall där programmet definierar en anpassad förloppsstapelritning.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsstapel

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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


Ange värde för radiell förloppsstapel

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_progress_bar_value_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE value);
```

### <a name="description"></a>Description

Den här tjänsten anger värdet för radiell förloppsstapel. Det tilldelade värdet är begränsat till intervallet [-360, 360] och definierar det möjliga intervallet med angularvärden för den aktuella platsen i förloppsfältet. Programmet måste skala det verkliga värdet som anges för att tilldela ett angular-värde till förloppsfältets widget.

Förloppsfältet ritas så att det aktuella värdet anger vinkeldeltan mellan fästpunkten och slutpunkten för den övre bågen. Negativa värden gör att bågen ritas i en medurs riktning med början vid fästpunktspositionen. Ett positivt aktuellt värde gör att bågen ritas i en moturs riktning med början vid fästpunktspositionen.

Om du till exempel vill rita en båge som börjar överst i bågen (klockan 12) och slutar till höger (klockan tre), tilldelar du ett ankarvärde på 90 grader och ett aktuellt värde på -90 grader.

### <a name="parameters"></a>Parametrar

- **förloppsfält** Pekare till kontrollblock för radiell förloppsstapel
- **värde** Nytt förloppsfältvärde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Värdet för lyckad radiell förloppsstapel har angetts
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltiga pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Alternativknappen Skapa

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

### <a name="description"></a>Description

Den här tjänsten skapar en alternativknappswidget. GX_RADIO_BUTTON härleds från GX_TEXT_BUTTON, och därför stöds gx_text_button tjänster också av den här widgettypen.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till alternativknappskontrollblock
- **namn** Logiskt namn på alternativknappswidget
- **överordnad** Pekare till den överordnade widgeten
- **text_id** Alternativknappens resurs-ID
- **style** Alternativknappsformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **radio_button_id** Programdefinierat ID för alternativknappen
- **storlek** Alternativknappen Dimensioner

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en lyckad alternativknapp
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_** STORLEK (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Alternativknappen Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_radio_button_draw(GX_RADIO_BUTTON *button);
```

### <a name="description"></a>Description

Den här tjänsten ritar en alternativknappswidget. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan även anropas av åsidosatta ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **knapp** Pekare till kontrollblock för alternativknappswidget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Ange pixelkartor för alternativknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_radio_button_pixelmap_set(
    GX_RADIO_BUTTON *button,
    GX_RESOURCE_ID off_id,
    GX_RESOURCE_ID on_id,
    GX_RESOURCE_ID off_disabled_id,
    GX_RESOURCE_ID on_disabled_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar pixelkartor som ska visas med den angivna alternativknappen för varje knapptillstånd. Resurs-ID:erna kan dupliceras.

### <a name="parameters"></a>Parametrar

- **off_id** Pixelkarta som används för alternativknappens inaktiverade tillstånd
- **on_id** Pixelkarta som används för alternativknapp i tillstånd
- **off_disabled_id** Pixelkarta som används för alternativknappen inaktiverat och inaktiverat tillstånd
- **on_disabled_id** Pixelkarta som används för alternativknappen inaktiverad och i tillstånd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En lyckad pixelkarta med alternativknapp har angetts
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange radiellt skjutreglage för fästpunktslista

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_anchor_angles_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE *anchor_angles, 
    USHORT anchor_count);
```

### <a name="description"></a>Description

Den här tjänsten anger fästvinklar för radiellt skjutreglage. Om du anger en lista över ankarvinklar är den radiella skjutreglagets vinkel en av definierade fästpunktsvinklar.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Kontrollblock för radiell skjutreglage
- **anchor_angles** Vinkellista att ange
- **anchor_count** Antal fästpunktsvinklar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckade ankarvinklar
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget
- **GX_INVALID_VALUE** (0x22) Ogiltig fästpunktslista

### <a name="allowed-from"></a>Tillåts från

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

Ange vinkel för radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_angle_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE new_angle);
```

### <a name="description"></a>Description

Den här tjänsten anger nytt vinkelvärde för radiellt skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiell skjutreglage
- **new_angle** Nytt vinkelvärde som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad radiell skjutreglagets vinkeluppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Skapa information om animering av radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_animation_set(
    GX_RADIAL_SLIDER *slider,
    USHORT steps, USHORT delay, 
    USHORT animation_style,
    VOID (*animation_update_callback)(GX_RADIAL_SLIDER *slider));
```

### <a name="description"></a>Description

Den här tjänsten anger animeringssteg, fördröjningstid och animeringsformat för animering med radiellt skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiell skjutreglage
- **steg** Totalt antal steg för en animering
- **fördröjning** Fördröjningstid för varje animeringssteg
- **animation_style** Funktionen Easing innehåller:
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
- **animation_update_callback** Användardefinierad återanropsfunktion som anropas efter varje animeringssteg

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad animering med radiellt skjutreglage
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange nytt värde för radiellt skjutreglage med animering

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_animation_start(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE target_angle);
```

### <a name="description"></a>Description

Den här tjänsten startar en animering för att flytta skjutreglagets nål från den aktuella positionen till den angivna positionen.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiellt skjutreglage
- **target_angle** Målvinkelvärde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Animering med lyckat radiellt skjutreglage startar
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för radiellt skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiellt skjutreglage
- **namn** Logiskt namn på widget för radiellt skjutreglage
- **överordnad** Pekare till den överordnade widgeten
- **info** Utseendedefinition för radiellt **skjutreglage, bilaga I** innehåller definition GX_RADIAL_SLIDER_INFO.
- **style** Alternativknappsformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **radio_button_id** Programdefinierat ID för radiellt skjutreglage
- **storlek** Dimensioner för radiellt skjutreglage

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa ett lyckat radiellt skjutreglage
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_** STORLEK (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Ogiltig överordnad widget

### <a name="allowed-from"></a>Tillåts från

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


Dra radiellt skjutreglage

### <a name="prototype"></a>Prototyp

```C
VOID gx_radial_slider_draw(GX_RADIAL_SLIDER *slider);
```

### <a name="description"></a>Description

Den här tjänsten drar ett radiellt skjutreglage. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan även anropas av åsidosatta ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiellt skjutreglage

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Händelse för skjutreglage för processradiell

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_event_process(
    GX_RADIAL_SLIDER *slider,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en radiell skjutreglagehändelse. Den här tjänsten ska anropas som standardhändelsehanterare av alla anpassade funktioner för radiell skjutreglage för händelsebearbetning.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiell skjutreglage
- **event_ptr** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad radiell skjutreglagehändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten hämtar informationspekaren för radiell skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiell skjutreglage
- **info** Informationspekaren för det radiella skjutreglaget hämtades

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Information om lyckat radiellt skjutreglage
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten anger radiell skjutreglageinformation.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiell skjutreglage
- **info** Radiell skjutreglageinformation att ange

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Information om lyckat radiellt skjutreglage
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Ange radiella skjutreglage för pixelkartor

### <a name="prototype"></a>Prototyp

```C
UINT gx_radial_slider_pixelmap_set(
    GX_RADIAL_SLIDER *slider,
    GX_RESOURCE_ID background_pixemap,
    GX_REOUSRCE_ID needle_pixelmap);
```

### <a name="description"></a>Description

Den här tjänsten anger bakgrund och bildpunktskartor för radiellt skjutreglage.

### <a name="parameters"></a>Parametrar

- **skjutreglage** Pekare till kontrollblock för radiell skjutreglage
- **background_pixelmap** Resurs-ID för pixelkarta i bakgrunden
- **needle_pixelmap** Resurs-ID för pixelkarta med nål

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad radiell skjutreglage för pixelkarta
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en RTF-vy enligt givna.


**Formateringstaggar används för att visa särskilda typer av text:**

- **\<b>\</b>** Ange textteckensnitt med användarens angivna fetstils-ID
- **\<i>\</i>** Ange textteckensnitt med användarangivet kursivt teckensnitts-ID
- **\<u>\</u>** Aktivera textunderstrykning
- **\<f GX_FONT_ID>\</f>** Ange textteckensnitt med angivet teckensnitts-ID
- **\<c GX_COLOR_ID>\</c>** Ange textteckensnitt med angivet färg-ID
- **\<hc GX_COLOR_ID>\</hc>** Ange färg för angiven färg-ID för text
- **\<align left/right/center>\</align>** Ange textjustering

**Exempel på formatering av tagganvändning:**

- \<b>Det här är fet text<\b>
- \<i>Det här är kursiv text<\i>
- \<u>Det här är text med understrykning<\u>
- \<f 0>Det här textteckensnitts-ID:t är inställt på 0<\f>
- \<c 1>Det här textfärgs-ID:t är inställt på 1<\c>
- \<hc 2>Det här färg-ID:t för markering av text är inställt på 2<\hc>
- \<align left> Den här texten är vänsterjusterad<\align>

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till kontrollblock för rtf-textvy
- **namn** Namnet på RTF-vyn
- **överordnad** Pekare till överordnad widget
- **text_id** Resurs-ID för textsträngen
- **teckensnitt** Pekare till teckensnittsinformationen för RTF-vyn. **Apendix I innehåller** en definition för GX_RICH_TEXT_FONTS struktur.
- **style (stil)** Widgetens stil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **id** Programdefinierat ID för RTF-vyn
- **storlek** Storlek på RTF-vyn

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad generering av RTF-vy
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll

### <a name="allowed-from"></a>Tillåts från

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

Demoprogrammets demo_guix_widget_types ingår i GUIX Studio-installationen och ger ett komplett exempel på hur du använder widgeten för rtf-textvy.

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

### <a name="description"></a>Description

Den här tjänsten ritar den angivna RTF-widgeten. Den här tjänsten anropas vanligtvis internt av GUIX som en del av en uppdateringsåtgärd för arbetsytan, men den exponeras även för programmet som kanske vill tillhandahålla en anpassad ritningsfunktion och anropa standardritningen för RTF-vyn som anpassad ritningsbas.

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till kontrollblock för rtf-textvywidget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange teckensnitt för rtf-textvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_rich_text_view_fonts_set(GX_RICH_TEXT_VIEW *text_view, GX_RICH_TEXT_FONTS *fonts);
```

### <a name="description"></a>Description

Den här tjänsten anger teckensnitten för en widget för rtf-textvy.

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till kontrollblock för rtf-textvywidget
- **teckensnitt** Pekare till teckensnittsinformation för RTF-vy. **Apendix I innehåller** definitioner för GX_RICH_TEXT_FONTS struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Teckensnitt för RTF-visning har angetts
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Rita rtf-textvisningstext

### <a name="prototype"></a>Prototyp

```C
VOID gx_rich_text_view_text_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Description

Den här stödfunktionen ritar textdelen av en RTF-vy. Den här funktionen anropas internt av gx_rich_text_view_draw() och tillhandahålls som ett separat API som en bekvämlighet för program som definierar en anpassad funktion för rtf-vyritning. Program som vill anpassa bakgrundsritningen i RTF-vyn kan tillhandahålla sin anpassade ritningsfunktion och anropa gx_rich_text_view_text_draw-tjänsten som en del av sin anpassade ritning för att rita rtf-textvyns text över bakgrunden.

### <a name="parameters"></a>Parametrar

- **text_view** Pekare till kontrollblock för rtf-textvywidget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Initiera en skärmstack

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_create(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET **memory_buffer, 
    INT buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten initierar en skärmstack. Programmet måste definiera minnesblocket och buffertstorleken som används för att implementera skärmstacksfunktionen.

> [!NOTE]
> *Det här API:et är inaktuellt och ersätts med gx_system_screen_stack_create(). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteksversion.*

### <a name="parameters"></a>Parametrar

- **kontroll** Kontrollblock för skärmstack
- **memory_buffer** Pekare till en minnesbuffert som används som en skärmstack
- **buffer_size** Minnesstorlek i byte

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en lyckad skärmstack
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE** (0x22) Ogiltig buffertstorlek

### <a name="allowed-from"></a>Tillåts från

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


Ta bort posten längst upp från skärmstacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_pop(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Description

Den här tjänsten tar bort posten längst upp från skärmstacken och kopplar den skärm som visas till dess föregående överordnade. Det här API:et tar även bort eventuella befintliga underordnade objekt från den överordnade.

> [!NOTE]
> *Detta API är inaktuellt och ersätts med gx_system_screen_stack_pop(). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteksversion.*

### <a name="parameters"></a>Parametrar

- **kontroll** Kontrollblock för skärmstack

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckat popup-fönster för skärmstack
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Push-skärmen och dess föräldrar till stacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_push(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET *screen,
    GX_WIDGET *new_screen);
```

### <a name="description"></a>Description

Den här tjänsten tar bort skärmen från dess överordnade objekt och flyttar skärmpekaren och den överordnade pekaren till skärmstacken. Den nya skärmpekaren kopplas sedan till den överordnade skärmen.


> [!NOTE]
> *Detta API är inaktuellt och ersätts med gx_system_screen_stack_pop(). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteksversion.*

### <a name="parameters"></a>Parametrar

- **kontroll** Kontrollblock för skärmstack
- **skärm** Skärmbild som ska push-flyttas
- **new_screen** Pekare för den nya skärmen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad push-push av skärmstack
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Tar bort alla poster från skärmstacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_screen_stack_reset(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla poster från skärmstacken.

> [!NOTE]
> *Detta API är inaktuellt och ersätts med gx_system_screen_stack_pop(). Den här versionen tillhandahålls endast för bakåtkompatibilitet med tidigare biblioteksversion.*

### <a name="parameters"></a>Parametrar

- **kontroll** Kontrollblock för skärmstack

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad rullningstums skapas
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Skapa bläddringstum

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_thumb_create(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_SCROLLBAR *parent, ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten skapar ett tumhjul för rullning. Den här tjänsten anropas vanligtvis internt när en GX_SCROLLBAR skapas, men görs offentlig för att tillåta anpassade implementeringar av rullningslisten.

### <a name="parameters"></a>Parametrar

- **scroll_thumb** Kontrollblock för bläddringswidget
- **överordnad** Pekare till överordnad rullningslist
- **style** Stil på rullningslistswidgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad bläddringstum skapa
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Rita rullningstum

### <a name="prototype"></a>Prototyp

```C
VOID gx_scroll_thumb_draw(GX_SCROLL_THUMB *scroll_thumb);
```

### <a name="description"></a>Description

Den här tjänsten ritar ett tumhjul för rullning. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan även anropas av åsidosatta ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **scroll_thumb** Kontrollblock för bläddringswidget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Process för bläddringstumhändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_thumb_event_process(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten hanterar händelser som skickas till ett tumhjul i rullningslisten. Den här tjänsten används vanligtvis internt av GUIX, men görs offentlig för att underlätta implementeringen av anpassade rullningslistsbeteenden.

### <a name="parameters"></a>Parametrar

- **scroll_thumb** Kontrollblock för bläddringswidget
- **händelse** Pekare till händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad process för bläddringstumhändelse
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Skapa en widget för basrullningshjul

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

### <a name="description"></a>Description

Den här tjänsten skapar en widget för basrullningshjul.

Ett basrullningshjul är baswidgeten för alla widgettyper för rullningshjul, inklusive **gx_generic_scroll_wheel** och **gx_text_scroll_wheel** som är basen för **gx_numeric_scroll_wheel** **och gx_string_ scroll_wheel** widgetar. Widgeten för basrullningshjul ger händelsehantering, animering för rullning och vald radberäkning för alla typer av rullningshjulswidgetar.

Program skulle normalt inte skapa en instans av en allmän widget för rullningshjul, eftersom den här widgettypen inte har någon ritningsfunktion. Åtkomst till detta API tillhandahålls dock för att hjälpa program som behöver skapa en anpassad typ av rullningshjulswidget.

GX_SCROLL_WHEEL baseras på GX_WINDOW, och därför kan alla GX_WINDOW API:er användas med GX_SCROLL_WHEEL och widgetar som härletts från GX_SCROLL_WHEEL.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **namn** Namn på program tilldelad widget
- **överordnad** Överordnad widget eller GX_NULL
- **total_rows** Totalt antal tillgängliga rader
- **style** Flaggor för widgetformat
- **id Program-ID** för tilldelad widget
- **storlek** Rektangel som definierar den inledande widgetstorleken.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Rullningshjulet har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för kontroll
- **GX_ALREADY_CREATED** widget (0x13) har skapats
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Händelsebearbetningsfunktion för allmän widget för rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_event_process(
    GX_SCROLL_WHEEL *wheel,
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten tillhandahåller grundläggande hantering av indatahändelse för alla typer av rullningshjulswidgetar.

Den här funktionen exponeras för programprogramvaran för att hjälpa till med program som behöver skapa en anpassad typ av rullningshjulswidget. Program tillhandahåller ofta en egen händelsebearbetningsfunktion, men anropar den allmänna händelsebearbetningen för hjulwidgetar för händelser som de inte behöver anpassa.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **händelse** GX_EVENT pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Händelseprocessen för rullningshjul
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela tonade alfavärden för valfri överläggstoning

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_gradient_alpha_set(
    GX_SCROLL_WHEEL *wheel,
    GX_UBYTE start_alpha,
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Description

Den här tjänsten definierar start- och slutvärdena för alfavärden för ett valfritt toningsöverlägg för widgeten för rullningshjul.

Alla rullningshjulswidgetar stöder en "tona"-effekt av rullningshjulsraderna som raderna nära den övre och nedre kanten av rullningshjulswidgeten. Den här tonande effekten uppnås genom att rita en gradient pixelkarta över rullningshjulsraderna, vilket gör att raderna verkar tona ut när raderna ritas upptill och längst ned i widgeten för rullningshjul.

Med den här API-tjänsten kan programmet ändra den tonande effektens intensitet eller inaktivera den här effekten helt genom att ange start- och slutvärdena för alfa till 0.

Den tonade pixelkartan skapas vid körning när rullningshjulet först blir synligt. Detta kräver att en minnesallokeringstjänst för körning har definierats med hjälp av _gx_system_memory_allocator_set(). Om ingen minnesbetoningsfunktion har definierats skapas inte toningsbilden och ingen toningseffekt blir tillgänglig.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **start_alpha** Överläggstoningen som börjar med alfavärdet.
- **end_alpha** Överläggstoningen som slutar med alfavärdet.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange alfa för rullningshjulets toning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela radhöjden för varje hjulrad

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_row_height_set(
    GX_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar radhöjden för varje rad i rullningshjulet. Observera att om rullningshjulet har GX_STYLE_TEXT_SCROLL_WHEEL_ROUND passerar radhöjden genom en transformering som effektivt minskar radhöjden när raden närmar sig hjulets övre eller nedre kant.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **row_height** Radhöjdsvärde i bildpunkter.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har ställt in rullningshjulets höjd
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela bakgrundsbild för rad som har valts med hjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_selected_background_set(
    GX_SCROLL_WHEEL*wheel, 
    GX_RESOURCE_ID image_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar ett valfritt pixelkarta-ID som ritas bakom den valda raden på rullningshjulet. Detta kan användas för att markera den markerade raden så att användaren enkelt kan se vilken rad i rullningshjulet som har valts.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **image_id** Pixelkarta-ID som ska användas som vald radbakgrundsbild.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Konfigurera rullningshjulsbakgrunden
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Hämta den markerade hjulraden

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_selected_get(
    GX_SCROLL_WHEEL *wheel,
    INT *row);
```

### <a name="description"></a>Description

Den här tjänsten frågar rullningshjulet för att hämta den markerade raden. Anroparen måste skicka platsen för att returnera det valda radindexet som den andra parametern till den här funktionen.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **rad** Plats där det valda radvärdet returneras.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har hämtat den valda hjulraden
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x19) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela vald rad med rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_selected_set(
    GX_SCROLL_WHEEL *wheel,
    INT row);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den markerade rullningshjulsraden.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **rad** Rad på rullningshjulet som ska väljas.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har ställt in den valda hjulraden
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela rullningshastighet

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_speed_set(
    GX_SCROLL_WHEEL *wheel,
    GX_FIXED_VAL start_speed_rate,
    GX_FIXED_VAL end_speed_rate,
    GX_VALUE max_steps,
    GX_VALUE delay);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar rullningshastigheten för widgeten för rullningshjulet.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **start_speed_rate** Hastigheten för rullningsstarthastigheten till speed (hastighet).
- **end_speed_rate** Hastigheten för rullningssluthastighet till hastighet
- **max_steps** Maximalt antal steg för rullning.
- **fördröjning** Fördröjningstid för varje steg.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har ställt in hjulhastighet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde

### <a name="allowed-from"></a>Tillåts från

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


Tilldela de totala tillgängliga rullningshjulsraderna

### <a name="prototype"></a>Prototyp

```C
UINT gx_scroll_wheel_total_rows_set(
    GX_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar antalet rader som är tillgängliga i det angivna rullningshjulet. Widgeten för rullningshjul tar vanligtvis emot radinnehållet från programmet i form av en matris med strängar eller strängdata från användaren. Detta API informerar rullningshjulet om det totala antalet rader som ska visas för användaren.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till allmänt kontrollblock för rullningshjul
- **total_rows** Totalt antal hjulrader som ska visas för användaren.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange rullningshjulets totala rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Ogiltigt värde

### <a name="allowed-from"></a>Tillåts från

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


Rita rullningslist

### <a name="prototype"></a>Prototyp

```C
VOID gx_scrollbar_draw(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Description

Den här tjänsten ritar en rullningslist. En vanlig ritningsfunktion används för både lodräta och vågräta rullningslistswidgetar. Den här tjänsten anropas internt av GUIX-arbetsytans uppdatering, men kan även anropas av åsidosatta ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **rullningslist** Rullningslistswidget att rita

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Bearbeta rullningslistshändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_event_process(
    GX_SCROLLBAR *scrollbar,
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en rullningslistshändelse. En vanlig händelsehanteringsfunktion som används för både lodräta och vågräta rullningslistswidgetar.

### <a name="parameters"></a>Parametrar

- **rullningslist** Kontrollblock för rullningslistswidget
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad rullningslisthändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Kontrollera rullningslistsgränsen

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_limit_check(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Description

Den här tjänsten kontrollerar gränsen för rullningslisten och förhindrar att rullningslistens tumhjul går utanför de fördefinierade gränserna.

### <a name="parameters"></a>Parametrar

- **rullningslist** Kontrollblock för rullningslistswidget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Kontroll av lyckad gräns för rullningslist
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Återställ rullningslist

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_reset(
    GX_SCROLLBAR *scrollbar,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten återställer rullningslisten.

### <a name="parameters"></a>Parametrar

- **rullningslist** Kontrollblock för rullningslistswidget
- **info** Pekare till GX_SCROLL_INFO struktur som definierar rullningslistens gränser, aktuellt värde och steg eller ökning. **Bilaga I** innehåller definition för GX_SCROLL_INFO struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad återställning av rullningslisten
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Rullningsinformationen är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tilldela rullningslistens värde

### <a name="prototype"></a>Prototyp

```C
UINT gx_scrollbar_value_set(
    GX_SCROLLBAR *scrollbar,
    INT value);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar det aktuella rullningslistsvärdet. En GX_EVENT_VERTICAL_SCROLL eller GX_EVENT_HORIZONTAL_SCROLL-händelse genereras till det överordnade fönstret.

### <a name="parameters"></a>Parametrar

- **rullningslist** Kontrollblock för rullningslistswidget
- **värde** Nytt rullningslistvärde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad rullningslisthändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Rullningsvärdet är inte giltigt

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Bearbeta ett backstegstecken i textinmatningswidgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_backspace(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten tar bort tecknet före markörpositionen för textinmatning. Den här tjänsten anropas internt när en backstegsnyckel nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatning med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x23) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Tar bort alla tecken från textinmatningsbufferten

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_buffer_clear(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten tar bort alla tecken från textindatabufferten.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Rensad indatabuffert med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Hämtar buffertinformation för textinmatningswidgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_buffer_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CHAR **buffer_address, 
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar buffertinformation för textinmatningswidgeten.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **buffer_address** Indatabuffertens adress
- **content_size** Byteantalet för indata
- **buffer_size** Storleken på indatabufferten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Buffertinformation har hämtats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ta bort tecknet vid den aktuella markörpositionen

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_character_delete(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten tar bort tecknet efter markörpositionen för textinmatning. Den här tjänsten anropas internt när en borttagningsnyckel nedåt-händelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ta bort ett tecken efter markören
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Infoga en teckensträng vid aktuell markörposition

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_character_insert(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Description

Den här tjänsten infogar en teckensträng i textinmatningssträngens buffert vid den aktuella markörpositionen.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **insert_str** Teckensträng som ska infogas
- **insert_size** Byteantal som ska infogas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har infogat tecknet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Skapa en widget för textinmatning

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_create(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    UINT style, USHORT text_input_id, GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en textinmatningswidget. Anroparen måste ange lagring för indatasträngen och ange strängens maximala längd.

GX_SINGLE_LINE_TEXT_INPUT härleds från GX_PROMPT och därför kan alla gx_prompt-tjänster användas med GX_SINGLE_LINE_TEXT_INPUT widgetar.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **namn** Valfritt logiskt widgetnamn
- **överordnad** Valfri överordnad widget
- **input_buffer** Storage för indatasträng
- **buffer_size** Storlek på lagringsområdet för indatasträngen, i byte.
- **style (stil)** Formatflaggor för textinmatning
- **text_input_id** Valfritt ID för indatawidgeten
- **storlek** Rektangel som definierar den inledande widgetstorleken

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatning med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Rita en textinmatningswidget

### <a name="prototype"></a>Prototyp

```C
VOID gx_single_line_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten ritar en widget för textinmatning. Den här tjänsten anropas vanligtvis internt under arbetsyteuppdateringen, men kan även anropas från anpassade ritningsfunktioner för textinmatning.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Hämta startpositionen för textr rita

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_draw_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_VALUE *xpos, GX_VALUE *ypos);
```

### <a name="description"></a>Description

Den här tjänsten hämtar startpositionen för att rita textinmatningstext.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **xpos** Hämtad startposition för dragningen i x koordinat
- **ypos** Hämtade startpositionen för dragningen i y-koordinaten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Flytta textinmatningsmarkören till slutet
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Flytta textindatamarkören till slutet av strängen

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_end(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten placerar widgetmarkören för textinmatning i slutet av indatasträngen. Den här tjänsten anropas internt när en slutnyckel nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Flytta textinmatningsmarkören till slutet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Händelsebearbetningsfunktion för textinmatningswidget

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_event_process(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en textindatahändelse med en rad. Den här funktionen refereras internt av gx_single_line_text_input_create-funktionen, men exponeras för användning av programmet i de fall där programmet definierar en anpassad händelsebearbetningsfunktion för textinmatning på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **event_ptr** Pekare till GX_EVENT struktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Korrekt bearbetad textinmatningshändelse
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ange bakgrundsfärg för textinmatning med en rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_fill_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Description

Den här tjänsten anger fyllningsfärgen för textinmatningen på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med en rad
- **normal_fill_color_id** Resurs-ID för widgeten fyller i färg i normalt tillstånd. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.
- **selected_fill_color_id** Resurs-ID för widgetens fyllningsfärg när widgeten får fokus. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet även kan lägga till anpassade resurs-ID:n för färg.
- **disabled_fill_color_id** Resurs-ID för widgeten fyller i färg när GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet även kan lägga till anpassade resurs-ID:n för färg.
- **readonly_fill_color_id** Resurs-ID för widgetens fyllningsfärg när både GX_STYLE_ENABLED och GX_STYLE_TEXT_INPUT_READYONLY har angetts. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet även kan lägga till anpassade resurs-ID:n för färg.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färguppsättning för textinmatning med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Flytta textindatamarkören till hempositionen

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_home(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar markörpositionen för textinmatning till början av indatasträngen. Den här tjänsten anropas internt när en startnyckel nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till hempositionen
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Flytta indatamarkören ett tecken till vänster

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_left_arrow(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar textindatamarkören ett tecken till vänster. Den här tjänsten anropas internt när en vänsternyckel nedåt-händelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till vänster
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Flytta markören till pixelposition

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    INT pixel_position);
```

### <a name="description"></a>Description

Den här tjänsten placerar textindatamarkören baserat på den begärda pixelpositionen. Markörindexet för textinmatning beräknas baserat på x-värdet för pixelpositionen. Den här tjänsten anropas internt när en pennhändelse tas emot, men kan även anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **pixel_position** X-värdet för pixelposition

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange markören till begärd position
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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


Flytta indatamarkören ett tecken till höger

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_right_arrow(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

Den här tjänsten flyttar textindatamarkören ett tecken till höger. Den här tjänsten anropas internt när en högernyckel nedåt-händelse tas emot, men kan också anropas av programmet.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Markören har flyttats till höger
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Lägga till format

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_style_add(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten lägger till de angivna formaten till widgeten för textinmatning på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **style** Nytt format att lägga till. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Stil har lagts till i widgeten
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort de angivna formaten från widgeten med textinmatning på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **style** Format som ska tas bort. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Formaten har tagits bort från widgeten
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ange format för textinmatning

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_style_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten anger de angivna formaten till en textinmatningswidget med en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Kontrollblock för enradswidget för textinmatning
- **style** style-flaggor att tilldela

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange textinmatningsformatet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Ange textfärg för textinmatning med en rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Description

Den här tjänsten anger textfärgen för textinmatningen på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med en rad
- **normal_text_color_id** Resurs-ID för textfärgen i normalt tillstånd. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **selected_text_color_id** Resurs-ID för textfärgen när widgeten får fokus. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **disabled_text_color_id** Resurs-ID för textfärgen när GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **readonly_text_color_id** Resurs-ID för textfärgen när både GX_STYLE_ENABLED och GX_STYLE_TEXT_INPUT_READONLY anges. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatningstextuppsättning med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Välj text

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Description

Den här tjänsten väljer text med angivet start- och slutmarkeringsindex och markerar den markerade texten med de markerade fyllnings- och textfärgerna.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med en rad
- **start_index** Index för det första markerade tecknet
- **end_index** Index för det senast valda tecknet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatningstextmarkering med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Indexvärdet är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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


Ange textinmatningstext på en rad (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Description

Den här tjänsten har gjorts inaktuell till förmån för gx_single_line_text_input_text_set_ext()

Den här tjänsten anger texten i textinmatningen på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med en rad
- **text** NULL-avslutad textsträng

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatningstextuppsättning med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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


Ange textinmatningstext på en rad

### <a name="prototype"></a>Prototyp

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten anger texten i textinmatningen på en rad.

### <a name="parameters"></a>Parametrar

- **text_input** Pekare till kontrollblock för textinmatning med en rad
- **sträng** GX_STRING variabel

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textinmatningstextuppsättning med en rad
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en skjutreglagewidget.

GX_SLIDER härleds från GX_WIDGET, och därför kan alla GX_WIDGET API-tjänster användas med GX_SLIDER-widgetar.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **name**: Namnet på skjutreglaget
- **överordnad:** Pekare till överordnad widget
- **tick_count:** Antal tick för skjutreglage
- **slider_info: Pekare** till skjutreglagets information som är en struktur som används för att överföra gränserna för skjutreglagets värde, skjutreglagets nålstorlek och position samt andra skjutreglageparametrar. **Bilaga I** innehåller definition för GX_SLIDER_INFO struktur.
- **style**: Skjutreglagets format. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **slider_id:** Programdefinierat ID för skjutreglaget
- **storlek:** Skjutreglagets dimensioner

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Skapa skjutreglaget
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED**: (0x13) Widget har redan skapats
- **GX_INVALID_SIZE**: (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET**: (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Dra skjutreglage

### <a name="prototype"></a>Prototyp

```C
VOID gx_slider_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Description

Den här tjänsten drar ett skjutreglage. Den här tjänsten används internt av gx_slider_create-funktionen, men exponeras också för användning av programmet i dessa instanser när en anpassad skjutreglageritningsfunktion definieras.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Händelse för processreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_event_process(
    GX_SLIDER *slider, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en skjutreglagehändelse. Den här funktionen refereras internt av gx_slider_create-funktionen, men exponeras för användning av programmet i de fall där programmet definierar en anpassad funktion för händelsebearbetning av skjutreglage.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **händelse:** Pekare till händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad händelseprocess för skjutreglage
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange informationsblock för skjutreglage

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_info_set(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den angivna skjutreglageinformationen, till exempel lägsta skjutreglage, högsta skjutreglage och aktuellt värde för skjutreglaget till det angivna skjutreglaget. Skjutreglaget uppdaterar nålens position och ritar om baserat på den nya skjutreglageinformationen.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **info**: Pekare till skjutreglagets informationsstruktur. **Bilaga I** innehåller definition GX_SLIDER_INFO struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Information om skjutreglaget har ställts in
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Dra skjutreglagets nål

### <a name="prototype"></a>Prototyp

```C
VOID gx_slider_needle_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Description

Den här tjänsten drar ett skjutreglage med en nål. Den här tjänsten anropas automatiskt av gx_slider_draw-funktionen, men kan också anropas av programmet som en del av en anpassad skjutreglageritningsfunktion.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämta skjutreglagets nålposition

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_needle_position_get(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *slider_info,
    GX_RECTANGLE *return_position);
```

### <a name="description"></a>Description

Den här tjänsten beräknar skjutreglagets nålposition baserat på det aktuella skjutreglagets värde.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **slider_info: Pekare** till skjutreglagets informationsstruktur som definierar skjutreglagets gränser, nålstorlek och offset och andra skjutreglageparametrar. **Bilaga I** innehåller definition GX_SLIDER_INFO struktur.
- **return_position:** Pekare till mål för nålposition

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckat skjutreglage med nålposition get
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_VALUE:**(0x22) Skjutreglageinformation är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Bockmarkeringar för skjutreglage

### <a name="prototype"></a>Prototyp

```C
VOID gx_slider_tickmarks_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Description

Den här tjänsten ritar reglagets bockmarkeringar. Den här funktionen anropas internt av gx_slider_draw,men exponeras för användning av program som kan implementera en anpassad skjutreglageritningsfunktion.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämta skjutreglagets färd

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_travel_get(
    GX_SLIDER *widget,
    GX_SLIDER_INFO *info,
    INT *return_min_travel, 
    INT *return_max_travel);
```

### <a name="description"></a>Description

Den här tjänsten hämtar skjutreglagets färd.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **info**: Pekare till skjutreglagets informationsstruktur. **Bilaga I** innehåller definition GX_SLIDER_INFO struktur.
- **return_min_travel:** Pekare till mål för minsta resevärde</td>
- **return_max_travell:** Pekare till mål för högsta resevärde</td>

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckat skjutreglage för att hämta
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_VALUE:**(0x22) Skjutreglageinformation är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Beräkna skjutreglagevärde

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_value_calculate(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info,
    INT new_position);
```

### <a name="description"></a>Description

Den här tjänsten beräknar skjutreglagets värde baserat på skjutreglagets nålposition. Den här funktionen anropas internt av GUIX när användaren flyttar skjutreglagets nål, men kan även anropas av programmet när en anpassad skjutreglagewidget implementeras.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **info**: Pekare till skjutreglagets information. **Bilaga I** innehåller definition GX_LISDER_INFO struktur.
- **new_position: Ny** skjutreglageposition

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckat skjutreglagevärde beräkna
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_VALUE:**(0x22) Skjutreglageinformation är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Ange skjutreglagevärde

### <a name="prototype"></a>Prototyp

```C
UINT gx_slider_value_set(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *info, 
    INT new_value);
```

### <a name="description"></a>Description

Den här tjänsten anger skjutreglagets värde. Det här API:et kan anropas av programmet för att flytta en nål med skjutreglaget under programkontrollen, vilket kringgår behovet av användarindata för att dra skjutreglagets nål.

### <a name="parameters"></a>Parametrar

- **slider**: Kontrollblock för skjutreglage
- **info**: Pekare till skjutreglagets informationsstruktur. **Bilaga I** innehåller en definition GX_SLIDER_INFO struktur
- **new_value: Nytt** skjutreglagevärde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Skjutreglagets värde har angetts
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Skapa en widget för din widget

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

### <a name="description"></a>Description

Den här tjänsten skapar en GX_SPRITE widget. En webbplats används för att visa en sekvens med pixelkartor som i en animering, eller kan användas som en widget för visning av pixelkartor med flera tillstånd.

GX_SPRITE härleds från GX_WIDGET och stöder alla gx_widget API-tjänster.

Widgeten GX_SPRITE kräver en matris med GX_SPRITE_FRAME strukturer för att definiera den första animeringen. **Bilaga I** innehåller definition GX_PRITE_FRAME struktur.

### <a name="parameters"></a>Parametrar

- **widgete:** Kontrollblock för Widget
- **name**: Valfritt tilläggsnamn
- **överordnad:** Pekare till överordnad widget
- **frame_list:** En matris med GX_SPRITE_FRAME strukturer
- **frame_count**: anger antalet poster i matrisen för bildrutelistan
- **style**: Stil på ditten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **sprite_id:** Programdefinierat ID för ditt program
- **size**: Dimensions of ditte

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad lyckat skapa
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED:**(0x13) Widget har redan skapats
- **GX_INVALID_WIDGET**: (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Tilldela diner-ram

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_current_frame_set(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den aktuella ramen. Om en GX_SPRITE widget inte körs automatiskt kan den användas som ett programkontrollerat tillståndsbelysning som visar den kommandoterade bildpunktskartan för bildpunkter.

### <a name="parameters"></a>Parametrar

- **widgete:** Kontrollblock för Widget
- **frame**: Den Första ram som ska visas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckades
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Tilldela eller ändra en figurramlista

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_frame_list_set(
    GX_SPRITE *sprite,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count);
```

### <a name="description"></a>Description

Den här tjänsten kan användas för att tilldela eller tilldela om bildrutelistan som används av en vält widget efter att widgeten har skapats. Information om innehållet i en listruta finns i dokumentationen gx_sprite_create API.

### <a name="parameters"></a>Parametrar

- **widgete:** Widget widget kontrollblock
- **frame_list:** Matris med GX_SPRITE_FRAME strukturer eller GX_NULL om det inte finns någon ramlista.
- **frame_count:** Antal bildrutor i matrisen med bildrutor

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad fördrutelisteuppsättning
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Starta en startkörningssekvens

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_start(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Description

Den här tjänsten startar en automatisk körningssekvens. Den här widgeten går igenom de första bildrutorna tills den sista bildrutan har nåtts, eller körs kontinuerligt om GX_SPRITE_LOOP har angetts.

### <a name="parameters"></a>Parametrar

- **widgete:** Widget widget kontrollblock
- **frame**: Inledande stomme som ska visas, vanligtvis bildruta 0

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Har startats och körts
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Stoppa en startkörningssekvens

### <a name="prototype"></a>Prototyp

```C
UINT gx_sprite_stop(GX_SPRITE *sprite);
```

### <a name="description"></a>Description

Den här tjänsten stoppar en autokörningssekvens.

### <a name="parameters"></a>Parametrar

- **widgete:** Widget widget kontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Har stoppats vid körningen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa ett rullningshjul av strängtyp

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

### <a name="description"></a>Description

Den här tjänsten skapar ett rullningshjul av strängtyp.

GX_STRING_SCROLL_WHEEL härleds från GX_TEXT_SCROLL_WHEEL, och därför kan alla API gx_text_scroll_wheel funktioner användas med GX_STRING_SCROLL_WHEEL widgetar.

Programmet kan skicka en enkel strängmatris till funktionen create som definierar de strängar som ska visas av rullningshjulet, eller så kan programmet skicka GX_NULL som string_list-parameter och anropa API:et för att tillhandahålla en matris med `gx_string_scroll_wheel_string_id_list_set()` sträng-ID:n. Om den senare metoden används växlar strängrullningshjulet automatiskt de visade strängarna om det aktiva programspråket ändras.

Alternativt, om de strängar som ska visas inte definieras statiskt eller inte vet när rullningshjulet skapas, kan programmet skicka GX_NULL som stränglistparameter och anropa API-funktionen gx_text_scroll_wheel_callback_set() för att definiera en återanropsfunktion som tillhandahåller de strängar som ska visas i realtid efter behov..

### <a name="parameters"></a>Parametrar

- **wheel**: Blockadress för kontroll av rullningshjul för strängar
- **name**: Programdefinierat widgetnamn
- **överordnad:** Överordnat eller GX_NULL
- **total_rows:** Totalt antal rader som ska visas för användaren
- **string_list:** Statiskt definierad strängmatris eller GX_NULL
- **style**: Önskade formatflaggor
- **Id:** Programdefinierade flaggor för hjulformat
- **storlek:** Ursprunglig storlek på rullningshjulet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Strängrullningshjulet har skapats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR (0x07)**: Ogiltig pekare
- **GX_ALREADY_CREATED**: (0x13) Widget har redan skapats
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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


Händelse för processsträngens rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, 
    INT id_count);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för det angivna rullningshjulet för strängar. Den här tjänsten ska anropas som standardhändelsehanterare av anpassade funktioner för bearbetning av rullningshjulssträngar.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till kontrollblock för strängrullningshjul
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Händelseprocess för strängrullningshjul
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Tilldela matris med sträng-ID:er

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, INT id_count);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en matris med sträng-IP-nummer till en widget med rullningshjul för strängar. Den här metoden för att tilldela strängar till ett rullningshjul för strängar rekommenderas om strängarna har definierats statiskt och widgeten måste fungera på flera språk. Om detta API ska användas bör widgeten för rullningshjul först skapas med en GX_NULL stränglista.

### <a name="parameters"></a>Parametrar

- **wheel**: Blockadress för kontroll av rullningshjul för strängar
- **string_id_list:** Matris med sträng-ID:er
- **id_count:** Storleken på ID-listan.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange sträng-ID-matris
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_VALUE**: 0x22) Ogiltig ID-liststorlek

### <a name="allowed-from"></a>Tillåts från

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

Tilldela matris med strängar

### <a name="prototype"></a>Prototyp

```C
UINT gx_string_scroll_wheel_string_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *string_list, 
    INT string_count);
```

### <a name="description"></a>Description

Detta tilldelar en matris med strängar till en widget med rullningshjul för strängar. Detta kan användas för att ändra de strängar som visas när widgeten har skapats från början.

Observera att string_scroll_wheel inte stöder GX_STYLE_TEXT_COPY, och därför bör matrisen med strängar som skickas till den här funktionen statiskt definieras av programmet.

### <a name="parameters"></a>Parametrar

- **wheel**: Adress till kontrollblock för rullningshjulssträng
- **string_list:** Matris med strängpekare
- **string_count:** Strängmatrisens storlek.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Har ändrat strängar för rullningshjulet
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_VALUE**: (0x22) Ogiltig strängliststorlek

### <a name="allowed-from"></a>Tillåts från

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

Skapa widget definierad i Studio-genererad specifikationsfil

### <a name="prototype"></a>Prototyp

```C
GX_WIDGET *gx_studio_widget_create(
    GX_BYTE *control,
    GX_CONST GX_STUDIO_WIDGET *definition, 
    GX_WIDGET *parent);
```

### <a name="description"></a>Description

Den här tjänsten skapar en widget och widgetens underordnade med hjälp av en widgetspecifikation som definierats i den GUIX Studio-genererade specifikationsfilen. Den här funktionen undviker sökning efter "efter namn" för den liknande funktionen `gx_studio_named_widget_create()` .

Strukturen GX_STUDIO_WIDGET definieras i programspecifikationshuvudfilen som genereras av GUIX Studio.

För statiskt allokerade widgetar definieras widgetkontrollblocket i den genererade specifications.c-filen och ges widgetnamnet som definierats i GUIX Studio. För dynamiskt allokerade widgetar ska programmet skicka GX_NULL som blockadress för widgetkontroll och funktionen försöker dynamiskt allokera widgetkontrollblocket med hjälp av funktionen , som också definieras av och tillhandahålls av `gx_system_memory_allocate()` programmet.

För att ett program ska kunna referera direkt till GUIX Studio-widgetdefinitionen i den genererade specifikationsfilen måste du följa namngivningskonventionen som används av GUI Studio-kodgeneratorn. Den GX_STUDIO_WIDGET struktur som genereras i filen specifications.c namnges alltid enligt den här konventionen: <widget_name>_define, där <widget_name>-fältet kan upprepas flera gånger om widgeten är underordnad en underordnad widget.

### <a name="parameters"></a>Parametrar

- **kontroll** Pekare till widgetkontrollblock eller GX_NULL tilldelas dynamiskt.
- **definition** Definitionsstruktur för Studio-genererad widget
- **överordnad** pekare till widgetens överordnade, om det finns någon

### <a name="return-values"></a>Returvärden

Pekare till det skapade widgetkontrollblocket eller GX_NULL om skapandet inte lyckades.

### <a name="allowed-from"></a>Tillåts från

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

Skapa widget definierad i Studio-genererad specifikationsfil

### <a name="prototype"></a>Prototyp

```C
UINT *gx_studio_named_widget_create(
    char *name, 
    GX_WIDGET *parent,
    GX_WIDGET **new_widget);
```

### <a name="description"></a>Description

Den här tjänsten skapar en widget och widgetens underordnade med hjälp av en widgetspecifikation som definierats i den GUIX Studio-genererade specifikationsfilen.

Den här API-funktionen används för att skapa skärmar på den översta nivån med det skärmnamn som anges i GUIX Studio-programmet som widgetdefinitionsidentifierare.

### <a name="parameters"></a>Parametrar

- **name**: Skärmnamn enligt definitionen i GUIX Studio-programmet.
- **överordnad:** pekare till widgetens överordnade, om det finns någon
- **new_widget: plats** för att returnera en skapad widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckades
- **GX_FAILURE**: (0x11) Det gick inte att hitta den namngivna widgeten

### <a name="allowed-from"></a>Tillåts från

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

Konfigurera visning definierad i GUIX Studio-projekt

### <a name="prototype"></a>Prototyp

```C
UINT *gx_studio_display_configure(
    USHORT display,
    UINT (*driver)(GX_DISPLAY *),
    USHORT language, 
    USHORT theme,
    GX_WINDOW_ROOT **return_root);
```

### <a name="description"></a>Description

Den här tjänsten initierar en GX_DISPLAY så att den är redo att användas. Den här funktionen konsoliderar funktionerna för att GX_DISPLAY ett kontrollblock, skapa en arbetsyta som passar visningen och skapa ett rotfönster för arbetsytan. Den här funktionen installerar också det språk och resurstema som begärdes efter att visningen har initierats.

Den här funktionen konsoliderar det programmeringsarbete som oftast krävs för att förbereda en visning för användning. Funktionen anropar funktionerna gx_display_create(), gx_display_color_table_set, gx_display_font_table_set, gx_display_pixelmap_table_set, gx_system_language_table_set, gx_system_active_language_set, gx_system_scroll_appearance_set, gx_canvas_create och gx_window_root_create, som annars skulle krävas av programmet.

### <a name="parameters"></a>Parametrar

- **display**: Indexera till visningstabellen, vilket motsvarar visningsdefinitionerna i Studio-projektfilen.
- **driver**: pekare för att visa initieringsfunktionen för drivrutiner. Den här funktionen anropas för att initiera pekare för den indirekta funktionen GX_DISPLAY för kontrollblocket, samt för att utföra alla maskinvaruinställningar som krävs.
- **language**: initial language table index
- **language**: initial theme index
- **root**: pekare till variabel där du vill returnera rotfönstrets adress eller GX_NULL.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckades
- **GX_FAILURE:**(0x11) Det gick inte att initiera visningen

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten anger det aktuella språket. Språkindexet måste vara mindre än antalet kolumner i programsträngstabellen. Den här funktionen har gjorts inaktuell och ersatts av gx_display_active_language_set. Alla nya program bör använda gx_display_active_langauge_set.

### <a name="parameters"></a>Parametrar

- **language**: Språkindex, definierat i resurshuvudfilen.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Har angett aktivt språk
- **GX_CALLER_ERROR:**** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR:**** (0x07) Ogiltig pekare
- **GX_INVALID_VALUE:**** (0x22) Ogiltigt språkindex

### <a name="allowed-from"></a>Tillåts från

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

Hämta animeringskontrollblock från systempoolen

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_animation_get(GX_ANIMATION **animation);
```

### <a name="description"></a>Description

Den här tjänsten kan användas för att hämta ett animeringskontrollblock från en pool med sådana kontrollblock som underhålls av gx_system komponenten. Animeringskontrollblockpoolen och relaterade API-tjänster tillhandahålls endast om konstanten GX_ANIMATION_POOL_SIZE definieras med värdet 0. Standardinställningen för det här värdet är 6, vilket innebär att blockpoolen för systemanimeringskontrollen innehåller GX_ANIMATION kontrollblocket.

Ett kontrollblock för animering som allokerats med hjälp av det här API:et returneras automatiskt till den kostnadsfria poolen om animeringen har slutförts. Om animeringen stoppas med gx_animation_stop eller inte kan startas på grund av ett returnerat fel, ska animeringskontrollblocket returneras till den kostnadsfria poolen av programmet med hjälp av gx_system_animation_free.

### <a name="parameters"></a>Parametrar

- **animering:** Adressen till pekaren som ska GX_ANIMATION pekaren.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Animeringskontrollblocket har erhållits
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Markör för ogiltig animering
- **GX_OUT_OF_ANIMATIONS**: (0x31) Systemanimeringspoolen är slut

### <a name="allowed-from"></a>Tillåts från

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

Returnera ett animeringskontrollblock till systempoolen

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_animation_free(GX_ANIMATION *animation);
```

### <a name="description"></a>Description

Den här tjänsten kan användas för att returnera ett kontrollblock för animering till systempoolen. Animeringskontrollblockpoolen och relaterade API-tjänster tillhandahålls endast om konstanten GX_ANIMATION_POOL_SIZE definieras med värdet 0. Standardinställningen för det här värdet är 6, vilket innebär att blockpoolen för systemanimeringskontrollen innehåller GX_ANIMATION kontrollblocket.

Ett kontrollblock för animering som allokerats med gx_system_animation_get() returneras automatiskt till den kostnadsfria poolen om animeringen har slutförts. Det har ingen effekt att försöka returnera ett kontrollblock för animering till den kostnadsfria poolen som redan har returnerats till den kostnadsfria poolen.

Om animeringen stoppas med gx_animation_stop eller inte kan startas på grund av ett returnerat fel, ska animeringskontrollblocket som har erhållits med gx_system_animation_get() returneras till den kostnadsfria poolen av programmet med hjälp av gx_system_animation_free().

Animeringen måste vara i inaktivt tillstånd innan den kan returneras till den kostnadsfria poolen. En animering är i inaktivt tillstånd när den inte har startats, när den har stoppats eller när den har slutförts.

### <a name="parameters"></a>Parametrar

- **animering:** Pekare till GX_ANIMATION kontrollblocket.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) har publicerat animeringsblocket
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Markör för ogiltig animering
- **GX_INVALID_ANIMATION**: (0x32) Animeringen är inte inaktiv eller har inte allokerats från systempoolen

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten inaktiverar stöd för dynamisk dubbelriktad text. Den här GX_DYNAMIC_BIDI_TEXT_SUPPORT måste definieras när GUIX-biblioteket byggs och krävs endast om du behöver ändra ordning på BiDi-strängdata. De flesta program använder GUIX Studio för att skapa korrekt sorterade BiDi-textsträngar.

### <a name="parameters"></a>Parametrar

**Ingen**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har inaktiverat stöd för bidi-text

### <a name="allowed-from"></a>Tillåts från

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

Aktivera stöd för dynamisk bidi-text

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_bidi_text_enable(VOID);
```

### <a name="description"></a>Description

Den här tjänsten möjliggör stöd för dynamisk dubbelriktad text. Den här GX_DYNAMIC_BIDI_TEXT_SUPPORT måste definieras när GUIX-biblioteket byggs och krävs endast om du behöver ändra ordning på BiDi-strängdata. De flesta program använder GUIX Studio för att skapa korrekt sorterade BiDi-textsträngar.

### <a name="parameters"></a>Parametrar

**Ingen**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Stöd för bidi-text har aktiverats

### <a name="allowed-from"></a>Tillåts från

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

Uppdatera alla dirty-arbetsyta

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_canvas_refresh(VOID);
```

### <a name="description"></a>Description

Den här tjänsten tvingar fram en omedelbar omritning av alla felgrafiska widgetar och arbetsyta. Den här tjänsten anropas vanligtvis internt av GUIX-systemkomponenten, men kan anropas av programmet för att tvinga fram en omedelbar systemreritningsåtgärd.

### <a name="parameters"></a>Parametrar

**Ingen**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Animeringsblock har släppts
- **GX_INVALID_CANVAS**: (0x20) Ingen arbetsyta har skapats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

Mark area dirty (Markera område)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_dirty_mark(GX_WIDGET *widget);
```

### <a name="description"></a>Description

Den här tjänsten markerar området för den här widgeten som dirty (grovt). Detta köar i praktiken widgeten för att rita om när systemhändelsebearbetningen har slutförts.

### <a name="parameters"></a>Parametrar

- **widget:** Pekare till widgetkontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Har markerats som en widget
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Markera partiellt område som är grovt

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_dirty_partial_add(
    GX_WIDGET *widget,
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Description

Den här tjänsten markerar det partiella området för den här widgeten som grovt. Detta köar widgeten för att ritas om av GUIX-arbetsytans uppdateringsåtgärd när systemhändelsebearbetningen har slutförts.

### <a name="parameters"></a>Parametrar

- **widget:** Pekare till widgetkontrollblock
- **dirty_area:** Dirty area of widget to mark dirty

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ett delvis grovt områdesmärke har lyckats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_SIZE**: (0x19) Ogiltig storlek på felaktigt område

### <a name="allowed-from"></a>Tillåts från

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

Hämta ritningskontext

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_draw_context_get(GX_DRAW_CONTEXT **current_context);
```

### <a name="description"></a>Description

Den här tjänsten returnerar en pekare till den aktuella ritningskontexten.

### <a name="parameters"></a>Parametrar

- **current_context: Pekare** till mål för aktuell pekare för ritningskontext

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad aktuell kontext get
- **GX_PTR_ERROR**:0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten söker i GUIX-händelsekön efter en händelse av samma typ. Om det finns en händelse av samma typ uppdateras händelsenyttolasten så att den matchar den nya händelsen. Om ingen matchande händelse hittas anropas gx_system_event_send för att lägga till den nya händelsen i slutet av händelsekön.

Den här funktionen används ofta av fast touch-indatadrivrutiner för att förhindra att händelsekön fylls med flera PEN_DRAG händelser. Den här funktionen kan också anropas av programmet för att förhindra att flera händelser av samma typ läggs till i GUIX-händelsekön.

### <a name="parameters"></a>Parametrar

- **event**: Pekare till händelse

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Lyckad händelsesändning
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skickar den angivna händelsen till GUIX-systemhändelsekön. Den nya händelsen placeras i slutet av kön.

### <a name="parameters"></a>Parametrar

- **event**: Pekare till händelse

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad händelsesändning
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Anspråksfokus

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_focus_claim(GX_WIDGET *widget);
```

### <a name="description"></a>Description

Den här tjänsten gör anspråk på fokus för den angivna widgeten. Om widgeten inte tidigare har fokus, får den en GX_EVENT_FOCUS_GAINED händelse.

### <a name="parameters"></a>Parametrar

- **widget:** Pekare till widgetkontrollblock till anspråksfokus

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad fokusanspråk
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_NO_CHANGE**: (0x08) Widget äger redan fokus
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET**: (0x12 Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten initierar GUIX. Den här tjänsten måste anropas före någon annan GUIX API-tjänst och bör endast anropas en gång vid systemstart.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ett lyckat system initieras
- **GX_SYSTEM_ERROR**: (0xFE) Ogiltig GX_EVENT för blockstorlek för kontroll eller händelsekö/mutex/thread create misslyckades.
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

Hämta aktiv språktabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_language_table_get( 
    GX_CHAR ****language_table,
    GX_UBYTE *languages_count, 
    UINT *string_count);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den aktiva språktabellen. Den här funktionen är inaktuell till förmån för gx_display_language_table_get. Alla nya program bör använda gx_display_language_table_get.

### <a name="parameters"></a>Parametrar

- **language_table:** Adressen till pekaren som ska returnera språktabellen.
- **languages_count:** Adressen till variabeln som ska returnera tabellkolumner.
- **string_count:** Adressen till pekaren för att returnera tabellrader.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Hämtad aktiv språktabell
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Tilldela aktiv språktabell

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_language_table_set(
    GX_CHAR ***language_table,
    GX_UBYTE languages_count, 
    UINT string_count);
```

### <a name="description"></a>Description

Den här tjänsten installerar den aktiva språktabellen. Den här funktionen har gjorts inaktuell och ersatts av gx_display_language_table_set. Alla nya program bör använda gx_display_language_table_set.

### <a name="parameters"></a>Parametrar

- **language_table:** Pekare till språktabell.
- **languages_count:** Antal språk i tabellen.
- **string_count:** Antal rader med strängtabeller.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Språktabellen har angetts
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Tilldela funktioner för minnesallokering, avallokering

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_memory_allocator_set(VOID *(allocate)(ULONG size),
    VOID(*release)(VOID *));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar programmet en återanropsfunktion för dynamisk minnesallokering och avallokering.

Om ingen GUIX-tjänst som använder dynamisk minnesallokering krävs av programmet behöver den här tjänsten inte anropas.

Om den används ska den här tjänsten anropas efter gx_system_initialize() som rensar GUIX-tjänst pekare och före en GUIX-tjänst som kräver användning av dynamisk minnesallokering.

GUIX-tjänster som kräver en runtime-minnesallokering och avallokeringstjänst omfattar:

- Läsa in binära resurser från extern lagring i GUIX-körningsmiljön.
- Jpeg-bildavkodaren för programkörning.
- Png-bildavkodaren för programkörning.
- Använda textwidgetar med GX_STYLE_TEXT_COPY.
- Funktioner för storleksändring och rotationsverktyg för runtime pixemap.
- Körningsskärmen och widgeten styr blockallokeringen.

### <a name="parameters"></a>Parametrar

- **allocator:** Funktionen Minnes allocator
- **release**: Minnesfri funktion

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Funktionen allokera minne har tilldelats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

I följande exempel används en ThreadX-bytepool för att implementera en threadsafe dynamisk minnesallokering och minnes-avallokeringstjänst.

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

Ange pennkonfiguration

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_pen_configure(GX_PEN_CONFIGURATION *pen_configuration);
```

### <a name="description"></a>Description

Den här tjänsten anger pennkonfiguration för att styra pennhastigheten och avståndsparametrarna som används för att utlösa genereringen av GX_EVENT_FLICK händelsetyper.

Den gx_pen_configuration_min_drag_dist medlem GX_PEN_CONFIGURATION är en fast punktdatatyp och du bör använda GX_FIXED_VAL_MAKE(value) för att konvertera från INT till GX_FIXED_VAL. Om du till exempel vill ange det minsta dra avståndet till 0,5 pixel per tick måste du ange gx_pen_configuration_min_drag_dist till `GX_FIXED_VAL_MAKE(1) / 2` .

I GUIX-versionerna 5.4.0 och äldre var gx_pen_configuration_min_drag_dist-medlemmen i GX_PEN_CONFIGURATION av typen (INT << 8) i stället för GX_FIXED_VAL typ. Om ditt projekt med GUIX-biblioteket i version 5.4.0 använder det här API:et måste du ändra min_drag_dist-parametern eller #define GUIX_5_4_0_COMPATIBILITY när du skapar GUIX-biblioteket.

### <a name="parameters"></a>Parametrar

- **pen_configuration** Pekare till pennkonfigurationsstruktur. **Bilaga I** innehåller definition för GX_PEN_CONFIGURATION struktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Korrekt inställning av pennkonfiguration
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

Skapa och initiera systemskärmstacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_create(
    GX_WIDGET **memory, 
    INT size);
```

### <a name="description"></a>Description

Den här tjänsten definierar en minnespool som ska användas för systemskärmstacken. Systemskärmstacken är en valfri funktion som kan användas av programmet för att hantera programmets skärmflödesutseende.

Om programmet har för avsikt att använda skärmstacktjänsterna måste gx_system_screen_stack_create först anropas för att konfigurera skärmstackens minnesregion.

### <a name="parameters"></a>Parametrar

- **memory**: Pekare till det reserverade minnesblocket.
- **storlek:** Storleken i byte för det reserverade minnesblocket.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Har skapats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Pop the topmost screen stack pointers (Öppna stackpekaren längst upp på skärmen)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_get(
    GX_WIDGET **popped_parent,
    GX_WIDGET **popped_screen);
```

### <a name="description"></a>Description

Den här funktionen pops the topmost screen stack pointers and returns those pointers to the caller. Den här funktionen skiljer sig från gx_system_screen_stack_pop() på så sätt att skärmen inte automatiskt återansluts till föregående överordnade skärm. I stället visas pekarna från stacken och returneras till anroparen, så att anroparen kan koppla eller ta bort den returnerade skärmen efter behov.

### <a name="parameters"></a>Parametrar

- **popped_parent: Plats** där den överordnade widgetens pekare ska lagras.
- **popped_screen:** Plats där den skärmpekaren ska lagras.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Hämtning av pekare för skärmstackar
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_FAILURE**: (0x10) Ogiltig eller tom skärmstack

### <a name="allowed-from"></a>Tillåts från

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

Pop the topmost entry from the system screen stack (Öppna posten längst upp från systemskärmstacken)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_pop();
```

### <a name="description"></a>Description

Den här funktionen pops the topmost entry for the screen stack and automatically attaches the poped screen to the poped parent widget.

### <a name="parameters"></a>Parametrar

**inget**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad hämtning av pekare för skärmstack
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_FAILURE**: (0x10) Ogiltig eller tom skärmstack

### <a name="allowed-from"></a>Tillåts från

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

Skicka en widget och en överordnad pekare till skärmstacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_push(GX_WIDGET *screen)
```

### <a name="description"></a>Description

Den här tjänsten placerar en pekare till den angivna widgeten, som vanligtvis är en skärm på den översta nivån, på skärmstacken. Om widgeten har ett överordnat objekt är den frånkopplad från den överordnade widgeten. Den överordnade widgetens pekare skickas också till skärmstacken. Den överordnade widgeten kan vara NULL, vilket innebär att en skärm som inte är synlig eller ansluten till någon överordnad kan push-kopplas till skärmstacken. Om en widget utan överordnad push-skickas till skärmstacken ska API:et screen_stack_get() användas för att hämta pekaren för push-skärmen i stället för att använda API:et screen_stack_pop() som försöker återansluta widgeten till den föregående överordnade widgeten.

### <a name="parameters"></a>Parametrar

- **screen**: Pekare till widgeten som ska push-skickas till skärmstacken.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Får rullningslistens utseende
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Återställa systemskärmstacken

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_screen_stack_reset();
```

### <a name="description"></a>Description

Den här funktionen tar bort alla poster från systemskärmstacken. Om skärmarna från stacken har dynamiskt allokerat kontrollblock som allokerats av GUIX Studio frigörs minnet för dessa kontrollblock.

### <a name="parameters"></a>Parametrar

**inget**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Får rullningslistens utseende
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Hämta rullningsutseende

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_scroll_appearance_get(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *return_appearance);
```

### <a name="description"></a>Description

Den här tjänsten får rullningslistens utseende.

### <a name="parameters"></a>Parametrar

- **style**: Rullningsliststil: `GX_SCROLLBAR_HORIZONTAL` eller `GX_SCROLLBAR_VERTICAL`
- **return_appearance**: Pekare till mål för utseende. **Bilaga I** innehåller definition för GX_SCROLLBAR_APPERANCE

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Får rullningslistens utseende
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Ange rullningsutseende

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_scroll_appearance_set(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *appearance);
```

### <a name="description"></a>Description

Den här tjänsten anger standardutseendet för rullning. När en rullning skapas används den här utseendestrukturen om inte programmet tillhandahåller en anpassad version.

### <a name="parameters"></a>Parametrar

- **style**: Rullningsstil `GX_SCROLLBAR_HORIZONTAL` eller `GX_SCROLLBAR_VERTICAL`
- **appearance**: Pekare till utseendestruktur initierad med olika attribut för rullningslistens utseende. Se bilaga **I för** definitionen av GX_SCROLLBAR_APPEARANCE struktur.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Konfigurera rullningsutseende
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten startar GUIX-bearbetning. Under normala omständigheter returnerar den här funktionen aldrig, utan börjar i stället bearbeta GUIX-händelsekön. När GUIX-händelsekön är tom pausar den här tjänsten den anropande tråden tills nya händelser tas emot i GUIX-händelsekön.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad systemstart
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten hämtar strängen för det angivna resurs-ID:t med hjälp av den första definierade visningen och det aktiva språket. Den här funktionen har gjorts inaktuell till förmån för gx_display_string_get. Alla nya program bör använda gx_display_string_get.

### <a name="parameters"></a>Parametrar

- **string_id:** Strängresurs-ID
- **return_string: Pekare** till strängmål pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad sträng get
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR (0x07)**: Ogiltig pekare
- **GX_INVALID_RESOURCE_ID**: (0x33) Ogiltigt resurs-ID

### <a name="allowed-from"></a>Tillåts från

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

Hämtar strängtabellen

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_table_get(
    GX_UBYTE language,
    GX_CHAR ***string_table,
    UINT *get_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar strängtabellen för det begärda språket från den första visningen. Den här funktionen har gjorts inaktuell till förmån för gx_display_string_table_get. Alla nya program bör använda gx_display_string_table_get.

### <a name="parameters"></a>Parametrar

- **language**: Språkindex
- **string_table:** Pekare till lagringsutrymmet för strängtabellspekaren, eller NULL om anroparen inte behöver hämta pekaren till strängtabellen.
- **get_size:** Pekare till lagringen för antalet strängar i strängtabellen, eller NULL om anroparen inte behöver hämta antalet strängar i strängtabellen.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad strängtabell get
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen

### <a name="allowed-from"></a>Tillåts från

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

Hämta strängbredd (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_width_get(
    GX_FONT *font, GX_CHAR *string,
    INT string_length,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_system_string_width_get_ext().

Den här tjänsten beräknar visningsbredden för den angivna strängen i bildpunkter med hjälp av det angivna teckensnittet. Om parametern string_length är >= 0 inkluderas endast antalet tecken för begäran i beräkningen. Om string_length parametern är -1 används hela strängen upp till NULL-terminatorn i beräkningen.

### <a name="parameters"></a>Parametrar

- **font**: Pekare till strängens teckensnitt
- **string**: Pekare till sträng
- **string_length:** Strängens längd
- **return_width:** Mål för strängbredd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad strängbredd get
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_FONT**: (0x16) Ogiltigt teckensnitt
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

Hämta strängbredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_string_width_get_ext(
    GX_FONT *font,
    GX_STRING *string,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

Den här tjänsten beräknar visningsbredden för den angivna strängen i bildpunkter med hjälp av det angivna teckensnittet.

### <a name="parameters"></a>Parametrar

- **font**: Pekare till strängens teckensnitt
- **string**: Pekare till sträng
- **return_width:** Mål för strängbredd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad strängbredd get
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_CALLER_ERROR**: 0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_FONT**: (0x16) Ogiltigt teckensnitt
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

Starttimer

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_timer_start(
    GX_WIDGET *owner, 
    UINT timer_id,
    UINT initial_ticks,
    UINT reschedule_ticks);
```

### <a name="description"></a>Description

Den här tjänsten startar en timer för den angivna widgeten. Konstanten GX_MAX_ACTIVE_TIMERS de maximala aktiva timers som stöds. Standardinställningen för det här värdet är 32.

### <a name="parameters"></a>Parametrar

- **ägare:** Pekare till widgetkontrollblock
- **timer_id:** ID för timer
- **initial_ticks:** tick för inledande förfallotid
- **reschedule_ticks:** Tick för periodisk förfallotid

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad timerstart
- **GX_OUT_OF_TIMERS**: (0x04) Inga fler timers
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_VALUE:**(0x22) Timervärden är inte giltiga

### <a name="allowed-from"></a>Tillåts från

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

Stopptimer

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_timer_stop(
    GW_WIDGET *owner, 
    UINT timer_id);
```

### <a name="description"></a>Description

Den här tjänsten stoppar timern med den angivna timer_id som är associerad med den anropande widgeten. Om du vill stoppa alla timers som är länkade till en viss widget kan programmet skicka timer_id värdet 0.

### <a name="parameters"></a>Parametrar

- **ägare:** Pekare till widgetkontrollblock
- **timer_id:** ID för timer eller 0 för alla timers

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad timerstopp
- **GX_NOT_FOUND:**(0x09) Timer-ID hittades inte
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Hämta versionssträngen för GUIX-biblioteket (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_version_string_get(GX_CHAR **version);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_system_version_string_get_ext().

Den här tjänsten hämtar VERSIONSsträngen för GUIX-biblioteket.

### <a name="parameters"></a>Parametrar

- **version**: Pekare för att returnera strängvärdet.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Versionssträngen har hämtats
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
GX_CHAR *version;

/* get the library version string. */

status = gx_system_verrsion_string_get(&version);
```

### <a name="see-also"></a>Se även

- gx_system_version_string_get_ext()

## <a name="gx_system_version_string_get_ext"></a>gx_system_version_string_get_ext

Hämta versionssträngen för GUIX-biblioteket

### <a name="prototype"></a>Prototyp

```C
UINT gx_system_version_string_get(GX_STRING *version);
```

### <a name="description"></a>Description

Den här tjänsten hämtar VERSIONSsträngen för GUIX-biblioteket.

### <a name="parameters"></a>Parametrar

- **version**: Pekare för att returnera strängvärdet.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Versionssträngen har hämtats
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten söker efter det angivna widget-ID:t. Till skillnad gx_widget_find() söker den här funktionen efter underordnade till alla rotfönster som definierats i systemet, vilket innebär att det här är en fullständig sökning av alla synliga widgetar. Om du känner till den överordnade widgeten som du söker efter använder du gx_widget_find() i stället.

### <a name="parameters"></a>Parametrar

- **widget_id:** Widget-ID att söka efter
- **search_level:** Definierar den rekursiva kapslingsnivån där underordnade widgetar genomsöks. Om det här värdet är 0 genomsöks endast omedelbara underordnade till varje rotfönster. Om det här värdet GX_SEARCH_DEPTH_INFINITE kapslas funktionen ned till alla underordnade som söker efter det begärda widget-ID:t. För andra värden > 0 definierar söknivån hur djupt kapslad funktionen ska söka efter det begärda widget-ID:t.
- **return_search_result**: Pekare till mål för widget hittades

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad widgetsökning
- **GX_NOT_FOUND**: (0x09) Widget-ID hittades inte
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en textknappswidget.

GX_TEXT_BUTTON härleds från GX_BUTTON och stöder alla gx_button API-tjänster.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappkontrollblock
- **name**: Logiskt namn på textknappen
- **överordnad:** Pekare till överordnad widget för knappen
- **text_id:** Resurs-ID för text
- **style**: Textknappstil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **text_button_id:** Programdefinierat ID för textknappen
- **storlek:** Knappens storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Textknapp skapas
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED**: (0x13) Widget har redan skapats
- **GX_INVALID_SIZE**: (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET**: (0x12) Överordnad widget är inte giltig


### <a name="allowed-from"></a>Tillåts från

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

Knappen Rita text

### <a name="prototype"></a>Prototyp

```C
VOID gx_text_button_draw(GX_TEXT_BUTTON *button);
```

### <a name="description"></a>Description

Den här tjänsten ritar textknappen. Den här tjänsten anropas vanligtvis internt under arbetsyteuppdateringen, men kan även anropas från anpassade textknappritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **knapp:** Pekare till textknappens kontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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


Bearbeta textknapphändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna textknappen. Den här tjänsten ska anropas som standardhändelsehanterare av anpassade funktioner för textknappshändelsebearbetning.

### <a name="parameters"></a>Parametrar

- **text_button** Pekare till textknappkontrollblock
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad textknapphändelseprocess
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ställ in teckensnittet på textknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_font_set(
    GX_TEXT_BUTTON *button,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar ett teckensnitt till den angivna knappen.

### <a name="parameters"></a>Parametrar

- **knapp:** Pekare till textknappens kontrollblock
- **font_id:** Resurs-ID för teckensnittet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange teckensnittet
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Ange textknappfärg

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_color_set(
    GX_TEXT_BUTTON *text_button,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id);
```

### <a name="description"></a>Description

Den här tjänsten anger textknappens färg.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappkontrollblock
- **normal_text_color_id:** Resurs-ID för normal text. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **selected_text_color_id:** Resurs-ID för markerad text. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **disabled_text_color_id:** Resurs-ID för färg för inaktiverad text. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Lyckad textknappsfärguppsättning
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_draw"></a>gx_text_button_text_draw

Stödfunktion för att rita knapptext

### <a name="prototype"></a>Prototyp

```C
VOID gx_text_button_text_draw(GX_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Description

Den här stödfunktionen ritar textdelen av en textknapp. Den här funktionen anropas internt av gx_text_button_draw och tillhandahålls som ett separat API för program som definierar en anpassad knappritningsfunktion. Program som vill anpassa knappbakgrundsritningen kan tillhandahålla sin anpassade ritningsfunktion och anropa gx_text_button_text_draw-tjänsten som en del av sin anpassade ritning för att rita knapptexten över bakgrunden.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappskontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_get"></a>gx_text_button_text_get

Hämta text från textknappen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_get(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR **return_text);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_text_button_text_get_ext().

Den här tjänsten hämtar den angivna strängen från textknappen.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappskontrollblock
- **return_text:** Pekare till strängen som hämtats från textknappen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Hämta texten från knappen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Hämta text från textknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_get_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *return_string);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den angivna strängen från textknappen.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappskontrollblock
- **return_string:** Pekare till strängen som hämtats från textknappen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Hämta texten från knappen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_id_set"></a>gx_text_button_text_id_set

Ange textresurs-ID till textknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_id_set(
    GX_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id);
```

### <a name="description"></a>Description

Den här tjänsten anger det angivna strängresurs-ID:t till textknappen.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappkontrollblock
- **string_id:** Resurs-ID för strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Ange strängresurs-ID till textknappen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_INVALID_RESOURCE_ID**: (0x33) Sträng-ID är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get

## <a name="gx_text_button_text_set"></a>gx_text_button_text_set

Tilldela text till textknappen (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_set(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_text_button_text_set_ext().

Den här tjänsten tilldelar den angivna strängen till textknappen. Om widgeten text_button har skapats med GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade textsträngen. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste strängen allokeras statiskt eller globalt, det vill säga det kanske inte är en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappkontrollblock
- **text**: pekare till den NULL-avslutade strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange texten till knappen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller minnesallokeringen misslyckades
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

Tilldela text till textknappen

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_button_text_set_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den angivna strängen till textknappen. Om widgeten text_button har skapats med GX_STYLE_TEXT_COPY skapar widgeten en privat kopia av den tilldelade textsträngen. Om GX_STYLE_TEXT_COPY inte är aktiv, gör widgeten inte en privat kopia av den inkommande strängen och därför måste strängen allokeras statiskt eller globalt, det vill säga det kanske inte är en automatisk eller tillfällig variabel.

### <a name="parameters"></a>Parametrar

- **text_button:** Pekare till textknappkontrollblock
- **sträng**: pekare till GX_STRING variabeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange texten till knappen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller minnesallokeringen misslyckades
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get
- gx_text_button_text_id_set

## <a name="gx_text_input_cursor_blink_interval_set"></a>gx_text_input_cursor_blink_interval_set

Ange blinkintervall för markör

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_input_cursor_blink_interval_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE blink_interval);
```

### <a name="description"></a>Description

Den här tjänsten anger blinkintervallvärdet för markören.

### <a name="parameters"></a>Parametrar

- **cursor_input** Markörkontrollblock
- **blink_interval** Värde som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange blinkintervallet för markören
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_VALUE:**(0x22) Blinkintervallvärdet är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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

Ange markörhöjd

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_input_cursor_height_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE height);
```

### <a name="description"></a>Description

Den här tjänsten anger markörens höjd.

### <a name="parameters"></a>Parametrar

- **cursor_input:** Markörkontrollblock
- **höjd** Värde som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Markörhöjd har angetts
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_VALUE**: (0x22) Höjd-värdet är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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

Ange markörbredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_input_cursor_blink_width_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE *width);
```

### <a name="description"></a>Description

Den här tjänsten anger markörens bredd.

### <a name="parameters"></a>Parametrar

- **cursor_input:** Markörkontrollblock
- **width**: Värde som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange markörbredden
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_VALUE**: (0x22) Bredd-värdet är inte giltigt

### <a name="allowed-from"></a>Tillåts från

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

Tilldela återanropsfunktionen för texttypens rullningshjul (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_callback_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *(*callback)(GX_TEXT_SCROLL_WHEEL *, int));
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_text_scroll_wheel_callback_set_ext().

Den här tjänsten tilldelar återanropsfunktionen som en texttyps rullningshjul anropar för att fastställa textsträngen som ska visas på varje rad i rullningshjulet.

För GX_NUMERIC_SCROLL_WHEEL och GX_STRING_SCROLL_WHEEL tillhandahålls standardfunktioner för återanrop och programmet behöver inte göra några ändringar för att använda dessa standardimplementeringar.

Det här API:et tillhandahålls så att programmet kan anpassa formateringen eller andra parametrar för strängen som visas på varje rad i widgeten för rullningshjul.

Återanropsfunktionen får som indata en pekare till rullningshjulets kontrollblock och radnumret som visas. Funktionen ska returnera en pekare till en textsträng.

### <a name="parameters"></a>Parametrar

- **hjul** Blockadress för kontrollblock för rullningshjul för strängar
- **motringning** Pekare till återanropsfunktion

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange återanrop
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Tilldela återanropsfunktionen för rullningshjulet för texttyp

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_callback_set_ext(
    GX_TEXT_SCROLL_WHEEL *wheel,
    UINT *(*callback)(GX_TEXT_SCROLL_WHEEL *, int, GX_STRING *));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar återanropsfunktionen som en texttyps rullningshjul anropar för att fastställa textsträngen som ska visas på varje rad i rullningshjulet.

För GX_NUMERIC_SCROLL_WHEEL och GX_STRING_SCROLL_WHEEL tillhandahålls standardfunktioner för återanrop och programmet behöver inte göra några ändringar för att använda dessa standardimplementeringar.

Det här API:et tillhandahålls så att programmet kan anpassa formateringen eller andra parametrar för strängen som visas på varje rad i widgeten för rullningshjul.

Återanropsfunktionen får som indata en pekare till rullningshjulets kontrollblock och radnumret som visas. Funktionen ska returnera en pekare till en textsträng.

### <a name="parameters"></a>Parametrar

- **hjul** Blockadress för kontrollblock för rullningshjul för strängar
- **motringning** Pekare till återanropsfunktion

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange återanrop
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Skapa ett textrullningshjul

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

### <a name="description"></a>Description

Den här tjänsten skapar ett textrullningshjul. Textrullningshjulet är en baswidget för GX_STRING_SCROLL_WHEEL och GX_NUMERIC_SCROLL_WHEEL typwidgetar. Den här funktionen anropas internt av gx_string_scroll_wheel_create och gx_numeric_scroll_wheel_create och tillhandahålls som ett separat API för program som definierar en anpassad widget för rullningshjul.

### <a name="parameters"></a>Parametrar

- **wheel**: Adress till kontrollblock för textrullningshjul
- **name**: Programdefinierat widgetnamn
- **överordnad:** Hjulparent eller GX_NULL
- **total_rows:** Totalt antal rader som ska visas för användaren
- **style:** Desired style flags (Önskade formatflaggor)
- **ID:** Programdefinierade flaggor i hjulformat
- **size**: Ursprunglig storlek på rullningshjulet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Textrullningshjulet har skapats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED:**(0x13) Widget har redan skapats
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig


### <a name="allowed-from"></a>Tillåts från

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

Rita ett textrullningshjul

### <a name="prototype"></a>Prototyp

```C
VOID gx_text_scroll_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>Description

Det här är standardritningsfunktionen för alla hjultyper baserat på GX_TEXT_SCROLL_WHEEL. Den här funktionen kan åsidosättas av program som kräver anpassning av utseendet på textens rullningshjulsritning.

GX_STRING_SCROLL_WHEEL och GX_NUMERIC_SCROLL_WHEEL är både baserade på eller härledda från GX_TEXT_SCROLL_WHEEL.

### <a name="parameters"></a>Parametrar

- **wheel**: Adress till kontrollblock för rullningshjulssträng

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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


Processhändelse för textrullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för det angivna textrullningshjulet. Den här tjänsten ska anropas som standardhändelsehanterare av anpassade funktioner för bearbetning av textrullningshjulshändelse.

### <a name="parameters"></a>Parametrar

- **hjul** Pekare till kontrollblock för textrullningshjul
- **event_ptr** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Händelseprocessen för ett lyckat textrullningshjul
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Tilldela teckensnitt som används för att rita rader med rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_font_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_font, 
    GX_RESOURCE_ID selected_font);
```

### <a name="description"></a>Description

Tilldela teckensnitten som används för att rita texten i en textrullningshjulsbaserad widget.

### <a name="parameters"></a>Parametrar

- **wheel**: Blockadress för kontroll av rullningshjul för strängar

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Har tilldelats hjulteckensnitt
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Tilldela färger som används för att rita rader med rullningshjul

### <a name="prototype"></a>Prototyp

```C
UINT gx_text_scroll_wheel_text_color_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCe_ID disabled_text_color);
```

### <a name="description"></a>Description

Den här funktionen tilldelar textfärgerna som används för att rita en textbaserad rullningshjulsrad.

### <a name="parameters"></a>Parametrar

- **wheel**: Blockadress för kontroll av rullningshjul för strängar
- **normal_text_color:** Färg som används för att rita icke-valda rader
- **selected_text_color:** Färg som används för att rita vald rad.
- **disabled_text_color: Färg** som används för att rita text för inaktiverad widget.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Textfärg för rullningshjul har tilldelats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en trädvy som angetts och associerar trädvyn med den angivna överordnade widgeten. Den accepterar alla typer av widget som underordnade menyalternativ. Vi rekommenderar att du använder widgeten GX_MENU som dess underordnade menyalternativ.

GX_TREE_VIEW härleds från GX_WINDOW och stöder alla gx_window API-tjänster.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **name**: Namnet på trädvyn
- **överordnad:** Pekare till överordnad widget
- **style**: Stil på widgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **menu_id:** Programdefinierat ID för trädvyn
- **storlek:** Trädvyns storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Skapandet av trädvyn lyckades
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED**: (0x13) Widget har redan skapats
- **GX_INVALID_SIZE**: (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar den angivna trädvyn. Den här funktionen anropas vanligtvis internt av GUIX-arbetsyteuppdateringsmekanismen, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner för anpassade trädvywidgetar.

### <a name="parameters"></a>Parametrar

- **träd** Pekare till trädvykontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Händelse för processträdsvy

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_event_process(
    GX_TREE_VIEW *tree, 
    GX_EVENT event_ptr);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den angivna trädvyn. Den här tjänsten ska anropas som standardhändelsehanterare av alla anpassade funktioner för händelsebearbetning i trädvyn.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **event_ptr:** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad processträdvyhändelse
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten anger indrag för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **indentation**: Indrag som ska anges

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Har angett indrag för trädvy
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Placera trädvyobjekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_position(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Description

Den här tjänsten placerar trädvyobjekt.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Objekt i trädvyn har positionerats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Ange trädvyns rotlinjefärg

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_root_line_color_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID color_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar rotlinjefärg för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **color_id:** Resurs-ID för rotlinjefärg

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad uppsättning rotlinjefärg
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Ange trädvyns rotpunktskarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_root_pixelmap_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID expand_map_id,
    GX_RESOURCE_ID collapse_map_id);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en bildpunktskarta för att expandera och komprimera för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **expand_map_id: Resurs-ID** för expandera pixelkarta
- **collapse_map_id: Resurs-ID** för komprimerad pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Ange rotpunktskarta
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten hämtar aktuellt markerat objekt i trädvyn.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **selected**: Pekare till vald widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Det valda objektet har hämtats
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Ange markerat objekt

### <a name="prototype"></a>Prototyp

```C
UINT gx_tree_view_selected_set(
    GX_TREE_VIEW *tree,
    GX_WIDGET *selected);
```

### <a name="description"></a>Description

Den här tjänsten anger det valda objektet för trädvyn.

### <a name="parameters"></a>Parametrar

- **träd:** Pekare till kontrollblock för trädvy
- **selected**: Pekare till det nya markerade objektet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Menyn Har ritats
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET**: (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Konvertera arbetsytans anteckningsnota till bitmapp

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_canvas_to_bmp(
    GX_CANVAS *canvas, 
    GX_RECTANGLE *rect,
    UINT (*write_data)(GX_UBYTE *byte_data, UINT data_count));
```

### <a name="description"></a>Description

Den här tjänsten konverterar arbetsytans minne till en bitmappsfil.

### <a name="parameters"></a>Parametrar

- **canvas**: Block pekare för arbetsytekontroll
- **rect:** Rektangel att konvertera
- **write_data: Pekare** för återanropsfunktion för att skriva data till

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Heltalsvärdet har konverterats till sträng
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare för returbuffert
- **GX_INVALID_SIZE**: (0x19) Ogiltig returbuffertstorlek

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten beräknar punkten på en cirkel baserat på cirkelcentret, radien och vinkeln.

### <a name="parameters"></a>Parametrar

- **xCenter:** x koordinat för cirkelcenter
- **yCenter:** y koordinat för cirkelcenter
- **radius:** Cirkelradie
- **angle**: Vinkel som du vill beräkna perimeterpunkten för cirkeln med i grader
- **point**: Adressen GX_POINT variabel där den beräknade x,y-koordinaten ska lagras
- **end_alpha:** Slut alfavärde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Toning skapades
- **GX_PTR_ERROR**: (0x07) Ogiltig returpunktsadress
- **GX_INVALID_VALUE**: (0x22) Ogiltig radius-parameter

### <a name="allowed-from"></a>Tillåts från

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

Skapa en toningspunktskarta

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

### <a name="description"></a>Description

Den här tjänsten skapar en tonad pixelkarta vid körning. En toningsbild kan användas för toning och andra intressanta visuella ändringar.

Bredden och höjden på den begärda toningen får inte vara mindre än 2 x 2 bildpunkter.

GUIX upprätthåller internt en lista över skapade toningar, och den här funktionen söker först igenom toningslistan för att hitta en matchande toningsbildpunktskarta innan en ny pixelkarta skapas. Med andra ord behövs samma toning av pixelkartan flera gånger, bara en pixelkarta skapas och varje toning som kräver den här pixelkartan delar den skapade pixelkartan.

Detta API kräver att gx_system_memory_allocator-funktionen definieras för att tillåta minnesallokering för körning.

Flaggor av toningstyp innehåller GX_GRADIENT_TYPE_ALPHA och GX_GRADIENT_TYPE_MIRROR. Endast GX_GRADIENT_TYPE_ALPHA toningar stöds för närvarande (dvs. den här typflaggan måste anges). Flaggan GX_GRADIENT_TYPE_MORROR är valfri och när den har angetts instruerar logiken för toning att skapa en toning som ändras från start_alpha till end_alpha och tillbaka till start_alpha. Annars skapas en linjär toning.

### <a name="parameters"></a>Parametrar

- **gradient**: Pekare till toningskontrollens blockstruktur
- **width**: Begärd bredd på pixelkarta
- **height**( höjd): Begärd pixelkartans höjd
- **type**: Begärd toningstyp
- **start_alpha:** Startar alfavärdet
- **end_alpha:** Slut alfavärde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Toning skapades
- **GX_INVALID_SIZE**: (0x19) Toning är inte minst 2 x 2 bildpunkter
- **GX_NOT_SUPPORTED**: (0x28) Toning är inte typen GX_GRADIENT_TYPE_ALPHA
- **GX_FAILURE:**(0x10) Minnestilldelningen har inte definierats eller så misslyckas minnesallokeringen
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR**: (0x07) Toningspekaren är inte giltig<
- **GX_INVALID_VALUE**: (0x22) Värdet för Bredd och höjd är inte giltigt
- **GX_INVALID_TYPE:**(0x1B) Toningstypen är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

Ta bort en toning som skapats tidigare

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_gradient_delete(GX_GRADIENT *gradient);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en toning som skapats tidigare. Om pixelkartan som är associerad med den här toningen inte används av andra toningar tas även pixelkartans data bort.

### <a name="parameters"></a>Parametrar

- **gradient**: Pekare till toningskontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Toning har tagits bort
- **GX_CALLER_ERROR**: (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR:**(0x07) Toningspekaren är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten konverterar ett långt heltalsvärde till en ASCII-sträng.

### <a name="parameters"></a>Parametrar

- **value**: Långt heltalsvärde som ska konverteras
- **return_buffer:** Målbuffert för ASCII-sträng
- **return_buffer_size:** Storleken på målbufferten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Konverterat heltalsvärde till sträng
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare för returbuffert
- **GX_INVALID_SIZE**: (0x19) Ogiltig returbuffertstorlek

### <a name="allowed-from"></a>Tillåts från

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

Cosinus för beräknings arc

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_math_acos(GX_FIXED_VAL x);
```

### <a name="description"></a>Description

Den här tjänsten beräknar vinkelvärdet för arc cosinus x.

Indatavärdet är en datatyp med fast punkt, anropa GX_FIXED_VAL_MAKE konvertera från INT till GX_FIXED_VAL typ. Om du till exempel vill beräkna arc cosine för 0,5 gör du indata som GX_FIXED_VAL_MAKE(1) / 2.

I GUIX-versionen 5.4.0 eller mindre är indatavärdestypen för den här funktionen INT och värdet är begränsat till intervallet [-256, 256]. Programmet måste skala värdet från intervallet [-1, 1] till intervallet [-256, 256] innan den här tjänsten anropas. Om ditt projekt med GUIX-versionen är lika med eller mindre än 5.4.0 har referens till detta API och du vill uppgradera projektet med det senaste guix-biblioteket. Du har två alternativ.

1. Åtgärda indatavärdet för det här API-anropet för att GX_FIXED_VAL datatypsvärdet.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **x**: Värde vars arc-cosinus beräknas

### <a name="return-values"></a>Returvärden

- **angle**: Vinkelvärde för arc cosinus x

### <a name="allowed-from"></a>Tillåts från

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

Beräknings arc sinus

### <a name="prototype"></a>Prototyp

```C
INT gx_utility_math_asin(GX_FIXED_VAL x);
```

### <a name="description"></a>Description

Den här tjänsten beräknar vinkelvärdet för arc sinus x.

Indatavärdet är en datatyp med fast punkt, anropa GX_FIXED_VAL_MAKE konvertera från INT till GX_FIXED_VAL typ. Om du till exempel vill beräkna arcus för 0,5 gör du indata som GX_FIXED_VAL_MAKE(1) / 2.

I GUIX-versionen 5.4.0 eller mindre är indatavärdestypen för den här funktionen INT och värdet är begränsat till intervallet [-256, 256]. Programmet måste skala värdet från intervallet [-1, 1] till intervallet [-256, 256] innan den här tjänsten anropas. Om ditt projekt med GUIX-versionen är lika med eller mindre än 5.4.0 och du vill uppgradera projektet med det senaste guix-biblioteket. Du har två alternativ.

1. Åtgärda indatavärdet för det här API-anropet för att GX_FIXED_VAL datatypsvärdet.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **x**: Värde vars arc sinus beräknas

### <a name="return-values"></a>Returvärden

- **angle**: Vinkelvärde för arc sinus x

### <a name="allowed-from"></a>Tillåts från

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

Compute-cosinus

### <a name="prototype"></a>Prototyp

```C
GX_FIXED_VAL gx_utility_math_cos(GX_FIXED_VAL angle);
```

### <a name="description"></a>Description

Den här tjänsten beräknar cosinus för den angivna vinkeln.

Indatavärdet är en datatyp med fast punkt, anropa GX_FIXED_VAL_MAKE konvertera från INT till GX_FIXED_VAL. Om du till exempel vill beräkna cosinus för 90 grad gör du indata som GX_FIXED_VAL_MAKE(90).

Returvärdet är en datatyp med fast punkt, anropa GX_FIXED_VAL_TO_INT konvertera från GX_FIXED_VAL till INT.

I GUIX-versionen 5.4.0 eller mindre är indatavärdet och returvärdestypen för den här tjänsten INT, indatavärdet och returvärdet förstoras med 256. Programmet måste därför skala vinkelvärdet med 256 innan den här tjänsten anropas. Om ditt projekt med GUIX-version är lika med eller mindre än 5.4.0 och du vill uppgradera projektet med det senaste guix-biblioteket har du två alternativ.

1. Åtgärda indatavärdet och hanteringen till returvärdet för det här API-anropet för att GX_FIXED_VAL värdet för datumtyp.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **angle**: Vinkel för att beräkna cosinus för

### <a name="return-values"></a>Returvärden

- **cosinus:** Cosinus för tillhandahållen vinkel

### <a name="allowed-from"></a>Tillåts från

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

Beräknings sinus

### <a name="prototype"></a>Prototyp

```C
GX_FIXED_VAL gx_utility_math_sin(GX_FIXED_VAL angle);
```

### <a name="description"></a>Description

Den här tjänsten beräknar sinus för den angivna vinkeln.

Indatavärdet är en datatyp med fast punkt, anropa GX_FIXED_VAL_MAKE konvertera från INT till GX_FIXED_VAL. Om du till exempel vill beräkna sinus för 90 grad gör du indata som GX_FIXED_VAL_MAKE(90). 

Returvärdet är en datatyp med fast punkt, anropa GX_FIXED_VAL_TO_INT konvertera från GX_FIXED_VAL till INT.

I 5.4.0 eller lägre version GUIX är indatavärdet och returvärdestypen INT, indatavärdet och returvärdet förstoras med 256. Programmet måste därför skala vinkelvärdet med 256 innan den här tjänsten anropas. Om ditt projekt med GUIX-version är lika med eller mindre än 5.4.0 och du vill uppgradera projektet med det senaste guix-biblioteket har du två alternativ.

1. Åtgärda indatavärdet och handningen till returvärdet för det här API-anropet för att GX_FIXED_VAL datatypsvärdet.
1. Definiera GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametrar

- **angle**: Vinkel för att beräkna sinus för

### <a name="return-values"></a>Returvärden

- **sinus:** sinus för asynlig vinkel

### <a name="allowed-from"></a>Tillåts från

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

Kvadratrot för beräkning

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_math_sqrt(UINT value);
```

### <a name="description"></a>Description

Den här tjänsten beräknar kvadratroten för det angivna värdet.

### <a name="parameters"></a>Parametrar

- **value**: Värde för att beräkna kvadratroten av

### <a name="return-values"></a>Returvärden

- **kvadratrot:** Kvadratrot för an angett värde

### <a name="allowed-from"></a>Tillåts från

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

Ändra ordning på BiDi-text till dess visningsordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_bidi_paragraph_reorder(GX_BIDI_TEXT_INFO *input_info, 
                                       GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Description

Den här tjänsten ordnar om BiDi-text till visningsordningen. Om teckensnitt och visningsbredd för text ritas tillämpas radbrytning först, och omsorteringsprocessen tillämpas baserat på varje rad. Om den angivna texten innehåller fler än ett stycke delar tjänsten upp texten i stycken, radbrytningen och omsorteringsresultatet för varje stycke länkas som en lista.

### <a name="parameters"></a>Parametrar

- **input_info**: Pekare till information om radbrytning och omsortering av text
- **resolved_info_head:** Pekare till den länkade listan som innehåller radbrytning och omsortering av resultat för varje stycke i den angivna texten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad omsortering av bidi-text
- **GX_PTR_ERROR**: (0x07) Ogiltiga indatapekare
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller så misslyckas minnesallokeringen

### <a name="allowed-from"></a>Tillåts från

Alla

### <a name="example"></a>Exempel
#### <a name="draw-single-line-bidi-text-to-canvas"></a>Rita en enskild rads bidi-text till arbetsytan
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
#### <a name="draw-multi-line-bidi-text-to-canvas"></a>Rita flerrads-bidi-text till arbetsyta
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

#### <a name="draw-multi-paragraph-bidi-text-to-canvas"></a>Rita flera styckens bidi-text till arbetsytan
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

Ta bort löst BiDi-textinformationslista

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_bidi_resolved_text_info_delete(GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Description

Den här tjänsten tar bort listan över lösta information som returneras av gx_utility_bidi_paragraph_reorder.

### <a name="parameters"></a>Parametrar

- **resolved_info_head:** Pekare till den lösta BiDi-textinformationslistan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad löst text borttagning
- **GX_PTR_ERROR**: (0x07) Ogiltiga indatapekare
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller så misslyckas minnesallokeringen

### <a name="allowed-from"></a>Tillåts från

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

Ändra storlek på pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_pixelmap_resize(
    GX_PIXELMAP *src,
    GX_PIXELMAP *destination, 
    INT width, 
    INT height);
```

### <a name="description"></a>Description

Den här tjänsten ändrar storlek på en pixelkarta och returnerar en pekare till en ny pixelkarta, vilket är resultatet av storleksändringen av pixelkartan.

Den här tjänsten kräver att du använder gx_system_memory_allocator_set för att tillåta allokering av minne för att lagra storleksändrat pixelkarta-data.

### <a name="parameters"></a>Parametrar

- **src:** Pekare till pixelkartan för att ändra storlek
- **mål:** Målbufferten för den resulterande pixelkartan
- **width**: Bredden på den resulterande pixelkartan, i bildpunkter
- **height**:Hieght of the resulting pixelmap, in pixels

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS:**(0x00) Storleksändring av en lyckad pixelkarta
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare för käll- eller målpunktskarta
- **GX_INVALID_VALUE**: (0x22) Värdet bredd eller höjd är inte giltigt
- **GX_NOT_SUPPORTED:**(0x28) Käll pixelkarta är komprimerat format
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller så misslyckas minnesallokeringen

### <a name="allowed-from"></a>Tillåts från

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

Rotera pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_pixelmap_rotate(
    GX_PIXELMAP *src, INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx, 
    UINT *rot_cy);
```

### <a name="description"></a>Description

Den här tjänsten roterar en pixelkarta och returnerar en pekare till en ny pixelkarta, vilket är resultatet av rotationen av pixelkartan. Om du vill rotera en pixelkarta direkt till arbetsytan använder du gx_canvas_pixelmap_rotate().

Den här tjänsten kräver tidigare användning av gx_system_memory_allocator_set för att tillåta allokering av minne för att lagra roterade pixelkarta-data.

### <a name="parameters"></a>Parametrar

- **src:** Pixelkartan som ska roteras
- **vinkel:** Rotationsvinkel i grader
- **mål:** Målbufferten för den resulterande pixelkartan
- **rot_cx:** Hämtade x koordinaten för rotationscentret med avseende på målpunktskartan. Bör initieras med x-koordinaten för rotationscentret med avseende på käll pixelkarta. Om rot_cx är GX_NULL hämtas inte värdet.
- **rot_cy:** Hämtad y-koordinat för rotationscentret med avseende på målpunktskarta. Bör initieras med rotationscentrets y-koordinat med avseende på käll pixelkarta. Om rot_cy är GX_NULL hämtas inte värdet.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad pixelkartarotering
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare för käll- eller målpunktskarta
- **GX_INVALID_VALUE**: (0x22) Vinkelvärdet är 0
- **GX_INVALID_FORMAT:**(0x28) Käll pixelkarta är komprimerat format, vilket inte stöds
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller så misslyckas minnesallokeringen

### <a name="allowed-from"></a>Tillåts från

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

Rotera pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_pixelmap_simple_rotate(
    GX_PIXELMAP *src,
    INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx,
    UINT *rot_cy);
```

### <a name="description"></a>Description

Den här tjänsten roterar en pixelkarta med 90 grader, 180 grader eller 270 grader.

### <a name="parameters"></a>Parametrar

- **src:** Pixelkartan som ska roteras
- **vinkel:** Rotationsvinkel i grader
- **mål:** Målbufferten för den resulterande pixelkartan
- **rot_cx:** Hämtade x koordinaten för rotationscentret med avseende på målpunktskartan. Bör initieras med x-koordinaten för rotationscentret med avseende på käll pixelkarta. Om rot_cx är GX_NULL hämtas inte värdet.
**rot_cy:** Hämtad y-koordinat för rotationscentret med avseende på målpunktskarta. Bör initieras med rotationscentrets y-koordinat med avseende på käll pixelkarta. Om rot_cy är GX_NULL hämtas inte värdet.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Lyckad pixelkartarotering
- **GX_PTR_ERROR**: (0x07) Ogiltig pekare för käll- eller målpunktskarta
- **GX_INVALID_VALUE:**(0x22) Vinkelvärdet är 0 eller inte en enkel vinkel som 90, 180, 270
- **GX_INVALID_FORMAT:**(0x28) Käll pixelkarta är komprimerat format, vilket inte stöds
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnestilldelningen har inte definierats eller så misslyckas minnesallokeringen

### <a name="allowed-from"></a>Tillåts från

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

Center-rektangel inom en annan rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_center(
    GX_RECTANGLE *rectangle,
    GX_RECTANGLE *within_rectangle);
```

### <a name="description"></a>Description

Den här tjänsten centrerar rektangeln inom en annan rektangel.

### <a name="parameters"></a>Parametrar

- **rektangel:** Rektangel till mitten
- **within_rectangle:** Rektangel som ska centreras inom

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Rektangeln har centrerats
- **GX_PTR_ERROR**: (0x07) Ogiltig rektangel för indata
- **GX_INVALID_SIZE**: (0x19) Ogiltig rektangelstorlek

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten hittar mitten av rektangeln.

### <a name="parameters"></a>Parametrar

- **rektangel**: Rektangel
- **return_center:** Pekare till mittpunkt

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Hittades i mitten av rektangeln
- **GX_PTR_ERROR**: (0x07) Ogiltig indatapekare
- **GX_INVALID_SIZE**: (0x19) Ogiltig rektangelstorlek

### <a name="allowed-from"></a>Tillåts från

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

Kombinera två rektanglar till den första

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_combine(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Description

Den här tjänsten kombinerar den första och andra rektangeln till den första rektangeln. Den första rektangeln expanderas för att inkludera den andra.

### <a name="parameters"></a>Parametrar

- **first_rectangle:** Första rektangel och kombinerad rektangel
- **second_rectangle:** Andra rektangeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Två rektanglar har kombinerats
- **GX_PTR_ERROR**: (0x07) Ogiltig indatapekare

### <a name="allowed-from"></a>Tillåts från

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

Jämföra två rektanglar

### <a name="prototype"></a>Prototyp

```C
GX_BOOL gx_utility_rectangle_compare( 
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Description

Den här tjänsten jämför den första och andra rektangeln. Om de är lika returneras GX_TRUE värde.

### <a name="parameters"></a>Parametrar

- **first_rectangle:** Första rektangeln
- **second_rectangle:** Andra rektangeln

### <a name="return-values"></a>Returvärden

- **result**: GX_TRUE om rektanglar är lika, GX_FALSE returneras.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten definierar en rektangel som anges.

### <a name="parameters"></a>Parametrar

- **rektangel:** Rektangelkontrollblock
- **left**: Vänster mest koordinat
- **översta:** Längst upp i koordinaten
- **right**: Höger mest koordinat
- **längst ned:** Längst ned i koordinaten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) En rektangel har definierats
- **GX_PTR_ERROR**: (0x07) Ogiltig rektangelpekare

### <a name="allowed-from"></a>Tillåts från

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

Identifiera överlappning av rektanglar

### <a name="prototype"></a>Prototyp

```C
GX_BOOL gx_utility_rectangle_overlap_detect(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle,
    GX_RECTANGLE *return_overlap_area);
```

### <a name="description"></a>Description

Den här tjänsten identifierar eventuell överlappning av de angivna rektanglarna. Om överlappning hittas returnerar tjänsten en GX_TRUE överlappande rektangel.

### <a name="parameters"></a>Parametrar

- **first_rectangle:** Första rektangeln
- **second_rectangle:** Andra rektangeln
- **return_overlap_area: Överlappande** rektangelområde

### <a name="return-values"></a>Returvärden

- **result**: GX_TRUE rektanglar överlappar, annars GX_FALSE.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten identifierar om den angivna punkten finns i rektangeln. Om punkten finns i rektangeln returnerar tjänsten GX_TRUE.

### <a name="parameters"></a>Parametrar

- **rektangel**: Rektangel
- **point**: Punkt

### <a name="return-values"></a>Returvärden

- **result**: GX_TRUE om punkten finns i rektangeln, annars GX_FALSE

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ökar storleken på rektangeln som anges.

### <a name="parameters"></a>Parametrar

- **rektangel**: Pekare till rektangel
- **justera**: Mängd för att justera rektangeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Rektangelns storlek har ändrats
- **GX_PTR_ERROR**: (0x07) Ogiltig rektangel för indata

### <a name="allowed-from"></a>Tillåts från

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

Skift-rektangel

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_rectangle_shift(
    GX_RECTANGLE *rectangle,
    GX_VALUE x_shift,
    GX_VALUE y_shift);
```

### <a name="description"></a>Description

Den här tjänsten flyttar rektangeln med de angivna värdena.

### <a name="parameters"></a>Parametrar

- **rektangel:** Rektangel för att flytta
- **x_shif:** Antal bildpunkter som ska flyttas på x-axeln
- **y_shift:** Antal bildpunkter som ska flyttas på y-axeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) Rektangeln har flyttats
- **GX_PTR_ERROR**: (0x07) Ogiltig rektangel för indata

### <a name="allowed-from"></a>Tillåts från

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

Rendera sträng till en pixelkarta med 8bpp-alfakarta (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_string_to_alphamap(
    const GX_CHAR *text, const
    GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Description

Den här tjänsten har gjorts inaktuell och ersatts av gx_utility_string_to_alphamap_ext().

Den här tjänsten renderar en textsträng till en alfakarta, som är en särskild form av 8bpp pixelkarta som endast innehåller alfavärden. Den här tjänsten används vanligtvis tillsammans med gx_utility_pixelmap_rotate och gx_canvas_pixelmap_draw för att rita roterad text på arbetsytan.

Den här tjänsten beräknar den minnesstorlek som krävs för den resulterande alfakartan och anropar funktionen gx_system_memory_allocator() som definieras av programmet för att dynamiskt allokera minne. Programmet måste anropa gx_system_memory_allocator_set() någon gång, vanligtvis under programstart, innan den här tjänsten används.

Om en textsträng ska roteras och ritas på arbetsytan bara en gång tillhandahålls tjänsten gx_canvas_rotated_text_draw() som ett alternativ. gx_canvas_rotated_text_draw() anropar gx_utility_string_to_alphamap(), gx_utility_pixelmap_rotate() och gx_canvas_pixelmap_draw() för att rendera den roterade texten i en enda åtgärd. Men om samma text ritas flera gånger roteras i olika vinklar är det mer effektivt att skapa alfakartan när du använder gx_utility_string_to_alphmap-API:et och sedan rotera den resulterande alfakartan flera gånger efter behov.

### <a name="parameters"></a>Parametrar

- **text:** Textsträng som ska renderas till alfakarta
- **font**: Teckensnittet som ska vara för att rendera texten
- **return_map:** Pekaren till GX_PIXELMAP som ska returneras till anroparen.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) En textsträng har renderats till en alfakarta
- **GX_PTR_ERROR**: (0x07) Ogiltig indatapekare
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnesallokering/kostnadsfri funktion har inte definierats
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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

Rendera sträng till en pixelkarta med 8bpp-alfakartor

### <a name="prototype"></a>Prototyp

```C
UINT gx_utility_string_to_alphamap_ext(
    GX_CONST GX_STRING *string,
    GX_CONST GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Description

Den här tjänsten renderar en textsträng till en alfakarta, som är en särskild form av 8bpp pixelkarta som endast innehåller alfavärden. Den här tjänsten används vanligtvis tillsammans med gx_utility_pixelmap_rotate och gx_canvas_pixelmap_draw för att rita roterad text på arbetsytan.

Den här tjänsten beräknar den minnesstorlek som krävs för den resulterande alfakartan och anropar funktionen gx_system_memory_allocator() som definieras av programmet för att dynamiskt allokera minne. Programmet måste anropa gx_system_memory_allocator_set() någon gång, vanligtvis under programstart, innan den här tjänsten används.

Om en textsträng ska roteras och ritas på arbetsytan bara en gång tillhandahålls tjänsten gx_canvas_rotated_text_draw() som ett alternativ. gx_canvas_rotated_text_draw() anropar gx_utility_string_to_alphamap(), gx_utility_pixelmap_rotate() och gx_canvas_pixelmap_draw() för att rendera den roterade texten i en enda åtgärd. Men om samma text ritas flera gånger roteras i olika vinklar är det mer effektivt att skapa alfakartan när du använder gx_utility_string_to_alphmap-API:et och sedan rotera den resulterande alfakartan flera gånger efter behov.

### <a name="parameters"></a>Parametrar

- **sträng:** Textsträng som ska renderas till alfakarta
- **font**: Teckensnittet som ska vara för att rendera texten
- **return_map:** Pekaren till GX_PIXELMAP som ska returneras till anroparen.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS**: (0x00) En textsträng har renderats till en alfakarta
- **GX_PTR_ERROR**: (0x07) Ogiltig indatapekare
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) Minnesallokering/kostnadsfri funktion har inte definierats
- **GX_INVALID_STRING_LENGTH**: (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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
### <a name="position-children-for-the-vertical-list"></a>Placera underordnade för den lodräta listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_children_position(
    GX_VERTICAL_LIST *vertical_list)
```

### <a name="description"></a>Description

Den här funktionen placerar underordnade för den lodräta listan.

### <a name="parameters"></a>Parametrar

- **vertical_list** Pekare till kontrollblocket för lodrät lista

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Placera underordnade för den lodräta listan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="description"></a>Description

Den här tjänsten skapar en lodrät lista.

GX_VERTICAL_LIST härleds från GX_WINDOW och stöder alla gx_window API-tjänster.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontrollblock för lodrät lista
- **namn** Namn på lodrät lista
- **överordnad** Pekare till överordnad widget
- **total_rows** Totalt antal rader i lodrät lista
- **motringning** En funktion som anropas av den lodräta listan när listan rullas. Anroparen bör först skapa tillräckligt med GX_WIDGET underordnade för att fylla de synliga listraderna. När listan rullas anropas den här funktionen för att skapa om listans underordnade som motsvarar det angivna listindexet
- **style (stil)** Stil på rullningslistswidgeten. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **vertical_list_id** Programdefinierat ID för lodrät lista
- **storlek** Dimensioner för lodrät lista

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Den lodräta listan har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_VALUE** (0x22) Antal rader som inte är giltiga
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för den lodräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontrollblock för lodrät lista
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Den lodräta listhändelsen har bearbetats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="set-starting-page-index"></a>Ange index för startsidan

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_page_index_set(
    GX_VERTICAL_LIST *list,
    INT index);
```
### <a name="description"></a>Description

Den här tjänsten anger startindexet för den lodräta listan.

### <a name="parameters"></a>Parametrar

- **lista** Kontrollblock för lodrät lista
- **index** Det nya toppindexet

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett startsideindex för den lodräta listan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig widget-pekare
- **GX_INVALID_VALUE** (0x22) Ogiltigt indexvärde
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-selected-index-from-vertical-list"></a>Hämta valt index från den lodräta listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_selected_index_get(
    GX_VERTICAL_LIST *vertical_list,
    INT *return_index);
```
### <a name="description"></a>Description

Den här tjänsten returnerar det valda indexet för den lodräta listan

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontrollblock för lodrät lista
- **return_index** Mål för retur av valt index

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hämta den lodräta listposten
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="assign-the-selected-entry-in-a-vertical-list"></a>Tilldela den valda posten i en lodrät lista

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_selected_set(
    GX_VERTICAL_LIST *vertical_list,
    INT index);
```

### <a name="description"></a>Description

Den här tjänsten tilldelar den valda posten i en lodrät lista. Om det behövs bläddrar den lodräta listan för att göra den valda posten synlig.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontrollblock för lodrät lista
- **index** Indexbaserad position för ny listpost

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange den lodräta listposten
- **GX_FAILURE** (0x10) Indataindex hittades inte i listan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget för lodrät lista eller listpost är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-selected-widget-from-vertical-list"></a>Hämta vald widget från den lodräta listan

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_selected_widget_get(
    GX_VERTICAL_LIST *vertical_list,
    GX_WIDGET **return_list_entry);
```
### <a name="description"></a>Description

Den här tjänsten returnerar den valda widgeten i den lodräta listan. Observera att om listan innehåller fler rader än underordnade widgetar och den valda underordnade widgeten har rullats från vyn, returnerar den här funktionen GX_NULL som GX_WIDGET-pekare, eftersom widgeten har återanvändas för att visa en ny listpost.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontrollblock för lodrät lista
- **return_list_entry** Mål för widget för returlista

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hämta den lodräta listposten
- **GX_FAILURE** (0x10) Den valda widgeten har rullats från vyn.
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="set-total-number-of-vertical-list-rows"></a>Ange totalt antal lodräta listrader

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_list_total_rows_set(
    GX_VERTICAL_LIST *vertical_list,
    INT count);
```
### <a name="description"></a>Description

Den här tjänsten tilldelar eller ändrar det totala antalet listrader.

### <a name="parameters"></a>Parametrar

- **vertical_list** Kontrollblock för lodrät lista
- **antal** Antal nya rader i listan

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ange antalet rader i den lodräta listan
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Radantal inte giltigt

### <a name="allowed-from"></a>Tillåts från

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
### <a name="create-vertical-scrollbar"></a>Skapa lodrät rullningslist

### <a name="prototype"></a>Prototyp

```C
UINT gx_vertical_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance,
    ULONG style);
```
### <a name="description"></a>Description

Den här tjänsten skapar en lodrät rullningslist.

### <a name="parameters"></a>Parametrar

- **rullningslist** Kontrollblock för rullningslistswidget
- **namn** Namn på rullningslist
- **överordnad** Pekare till överordnad widget
- **utseende** Utseendet på en lodrät rullningslistwidget.
- **style** Rullningslistens format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en lodrät rullningslist
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="allocate-a-widget-control-block"></a>Allokera ett widgetkontrollblock

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_allocate(
    GX_WIDGET **control_block,
    ULONG memsize);
```
### <a name="description"></a>Description

Den här tjänsten allokerar dynamiskt ett widgetkontrollblock genom att anropa den programdefinierade minnesallokeringsfunktionen. Den här tjänsten används främst av de funktioner som genereras av GUIX Studio för att dynamiskt allokera kontrollblock när egenskapen "Dynamisk allokering" väljs i GUIX Studio-egenskapsvyn.

### <a name="parameters"></a>Parametrar

- **control_block** Pekare till returnerad kontrollblockspekare
- **memsize** Kontrollera blockstorleken i byte

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Allokera en lyckad widget
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnestilldelningen har inte definierats eller så misslyckades minnesallokeringen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_MEMORY_SIZE** (0x29) Minnesstorleken är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="attach-widget-to-its-parent"></a>Koppla widgeten till dess överordnade

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Description

Den här tjänsten kopplar widgeten till den angivna överordnade komponenten. Om widgeten redan är kopplad till en annan överordnad, kopplas den först från. Om widgeten redan är kopplad till samma överordnade funktion gör funktionen ingenting.

Widgeten blir först-underordnad till sin överordnade när det gäller z-ordning. Om widgetar på samma sätt överlappar varandra ritas den här widgeten ovanpå på samma sätt. Om du vill placera den nya widgeten i z-ordningen använder du gx_widget_back_attach eller gx_widget_back_move.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget** Pekare till underordnad widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Överordnad eller widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="draw-a-widget-background"></a>Rita en widgetbakgrund

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_background_draw(GX_WIDGET *widget);
```
### <a name="description"></a>Description

Den här tjänsten utför en heldragen färgfyllning av en widgetbakgrund. Den här tjänsten anropas automatiskt av gx_widget_draw-funktionen, men kan också anropas av programmet som en del av en anpassad widgetritning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget som ska ritas

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="attach-widget-to-its-parent"></a>Koppla widgeten till dess överordnade

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_back_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Description

Den här tjänsten kopplar widgeten till den angivna överordnade komponenten. Om widgeten redan är kopplad till en annan överordnad, kopplas den först från. Om widgeten redan är kopplad till samma överordnade funktion gör funktionen ingenting.

Widgeten blir den underordnade till den överordnade widgeten när det gäller z-ordning. Om widgetar på samma sätt överlappar varandra ritas den här widgeten bakom dessa på samma sätt. Om du vill placera den nya widgeten framför z-ordningen använder du gx_widget_attach eller gx_widget_front_move.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget** Pekare till underordnad widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Överordnad eller widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="move-widget-to-back"></a>Flytta widgeten till bakåt

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_back_move(
    GX_WIDGET *widget,
    GX_BOOL *return_widget_moved);
```
### <a name="description"></a>Description

Den här tjänsten flyttar widgeten till bakåt i den överordnades Z-ordning för underordnade widgetar.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **return_widget_moved** Pekare till mål för flaggan som anger att widgeten har flyttats

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) En lyckad widget flyttas till bakåt
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_NO_CHANGE** (0x08) Inga ändringar tillämpas
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="move-a-rectangular-block-of-pixels"></a>Flytta ett rektangulärt block med bildpunkter

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_block_move(
    GX_WIDGET *widget,
    GX_RECTANGLE *block,
    INT xshift, INT yshift);
```

### <a name="description"></a>Description

Den här tjänsten flyttar ett rektangulärt block med bildpunkter. Den här tjänsten används oftast för att implementera snabb bläddring.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget som begär blockflyttning
- **blockera** Rektangel-begränsningsblock som ska flyttas
- **xshift** X-skiftbeloppet i bildpunkter
- **yshift** Y-skiftbeloppet i bildpunkter

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget flytta till bakåt
- **GX_INVALID_CANVAS** (0x20) Widget-arbetsytan hittades inte
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar widgetens kantlinje. Den här tjänsten anropas vanligtvis som en del av en widgetritning. Den här tjänsten tolkar widgetens kantlinjeflaggor så att de inte ritar någon kantlinje, en tunn kantlinje, en upphöjd kantlinje, en flaggad kantlinje eller en tjock kantlinje.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **border_color** Färg på kantlinje. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **upper_fill** Färg på övre fyllning. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **lower_fill** Färg på lägre fyllning. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.
- **fyll i** Den här booleska flaggan anger om widgetområdet ska fyllas med angivna fyllningsfärger. Om det här värdet GX_FALSE ritas endast widgetens kantlinje.

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="set-widget-border-style"></a>Ange kantformat för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_border_style_set(
    GX_WIDGET *widget, 
    ULONG style);
```

### <a name="description"></a>Description

Den här tjänsten anger widgetens kantlinjeformat.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **style** Kantlinjeformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad stiluppsättning för widget-kantlinje
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-widget-border-width"></a>Hämta bredd på widgetens kantlinje

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_border_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

Den här tjänsten hämtar widgetens kantlinjebredd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_width** Pekare till mål för widgetens kantlinjebredd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Kantlinjebredden har hämtats
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-widget-canvas"></a>Hämta widgetarbetsyta

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_canvas_get(
    GX_WIDGET *widget,
    GX_CANVAS **return_canvas)
```
### <a name="description"></a>Description

Den här tjänsten returnerar en pekare till arbetsytan där widgeten återges.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_canvas** Pekare till mål för widgetens arbetsyta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget-arbetsyta hämta
- **GX_FAILURE** (0x10) Widget-arbetsytan hittades inte
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten identifierar om widgeten är underordnad den överordnade widgeten. Den här tjänsten kapslas för att söka efter underordnade till underordnade objekt och returnerar TRUE om den överordnade widgeten på någon nivå är en överordnad för den underordnade widgeten.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **underordnad** Pekare till underordnad widget
- **return_detect** Pekare till mål för identifiering

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad underordnad widgetidentifiering
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Överordnad eller underordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="draw-widget-children"></a>Underordnade rita widget

### <a name="prototype"></a>Prototyp

```C
VOID gx_widget_children_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Description

Den här tjänsten ritar alla underordnade till den överordnade widgeten. Den här tjänsten anropas vanligtvis av alla standardwidgetritningsfunktioner för att rita befintliga underordnade widgetar och bör anropas av alla anpassade ritningsfunktioner så att underordnade widgetar kan kopplas till din anpassade överordnade widgettyp.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="get-widget-client-area"></a>Hämta klientområde för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_client_get(
    GX_WIDGET *widget,
    GX_VALUE border_width,
    GX_RECTANGLE *return_client_area);
```
### <a name="description"></a>Description

Den här tjänsten beräknar klientområdet för widgeten genom att subtrahera widgetens kantlinjebredd från den övergripande widgetstorleken.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **border_width** Bredden på widgetens kantlinje
- **return_client_area** Mål för att returnera klientområde

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckade widgetklientområdet get
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Widget-kantlinjen är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten hämtar färgen som är associerad med det angivna resurs-ID:t. Den här tjänsten bör endast anropas av synliga widgetar.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widgetkontrollblock
- **resource_id** Resurs-ID för färg. **Bilaga B** innehåller fördefinierade färgresurs-ID:er. Observera att programmet kan lägga till anpassade resurs-ID:n för färg också.
- **return_color** Pekare till mål för färg. **Bilaga A** innehåller fördefinierade färger. Observera att programmet kan lägga till anpassade färger också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad färg get
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CANVAS** (0x20) Widget-arbetsytan är inte giltig eller widgeten är osynlig
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="description"></a>Description

Den här tjänsten skapar en widget.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **namn** Logiskt namn på widget
- **överordnad** Pekare till överordnad widget
- **style (stil)** Stil. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **widget_id** Programdefinierat ID för widgeten
- **storlek** Widgetens storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa en lyckad widget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Överordnad widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="description"></a>Description

Den här tjänsten testar för att avgöra om widgeten har skapats tidigare. Om inga fel påträffas returnerar den här funktionen GX_SUCCESS, oavsett om widgeten har skapats ännu eller inte. Resultatet av testet finns i return_test pekaren.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_test** Mål för testresultat

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Slutfört test
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort widgeten. Om widgetkontrollblocket tilldelas dynamiskt anropas gx_system_memory_free till fri dynamiskt allokerad lagring.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget ta bort GX_CALLER_ERROR (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Funktionen Minnesfri har inte definierats

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort widgeten från dess överordnade objekt.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget koppla GX_CALLER_ERROR (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten ritar widgeten. Den här funktionen anropas vanligtvis internt av GUIX-arbetsyteuppdateringsmekanismen, men exponeras för programmet för att hjälpa till med implementeringen av anpassade ritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="assign-the-widget-drawing-function"></a>Tilldela widgetens ritningsfunktion

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_draw_set(
    GX_WIDGET *widget,
    VOID (*drawing_function) (GX_WIDGET *));
```

### <a name="description"></a>Description

Den här tjänsten åsidosätter standardritningsfunktionen för widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **drawing_function** Pekare till ritningsfunktionen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Åsidosättning av funktion för att rita widget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="generate-widget-event"></a>Generera widgethändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_generate(
    GX_WIDGET *widget, 
    USHORT event_type, LONG value);
```

### <a name="description"></a>Description

Den här tjänsten genererar GX_SIGNAL typ av händelse, som är en viss typ eller klass av GX_EVENT. gx_widget_event_generate() kodar 16-bitars widget-ID:t tillsammans med det som skickas i event_type till ett enda 32-bitars GX_EVENT.gx_event_type-värde. Värdeparametern kodas till den genererade gx_event. gx_event_payload.gx_event_longdata.

Det genererade event.gx_event_target alltid läses in med den anropande widgetens överordnade, vilket innebär att den genererade händelsen alltid skickas först till den överordnade widgeten för den genererande widgeten.

Observera att gx_widget_event_generate endast ska användas för att skicka GX_SIGNAL intervallhändelsetyper. För alla andra händelsetyper, inklusive användardefinierade händelsetyper, använder du API:et gx_system_event_send() som ger fullständig kontroll över alla fält i händelsen som pushas i GUIX-händelsekön.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **event_type** Typ av händelse. **Bilaga E** innehåller fördefinierade GUIX-händelser. Ytterligare händelser kan läggas till av programmet.
- **värde** Ytterligare händelseinformation

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget-händelsegenerering
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="process-widget-event"></a>Händelse för processwidget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_process(
    GX_WIDGET *widget, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Det här är standardfunktionen för händelsebearbetning för alla widgetar. När en anpassad händelsebearbetningsfunktion skrivs bör standardåtgärden för alla händelsetyper alltid vara att skicka händelsen till den widgettyp som en widget baseras på. Widgetar som baseras på de mest grundläggande GX_WIDGET typ använder gx_widget_event_process som standardfunktion för händelsebearbetning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **händelse** Pekare till händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widgethändelsebearbetning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="set-event-processing-function-of-widget"></a>Ange händelsebearbetningsfunktion för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_event_process_set(
    GX_WIDGET *widget,
    UINT (*event_processing) (GX_WIDGET *, GX_EVENT *));
```

### <a name="description"></a>Description

Den här tjänsten åsidosätter händelsebearbetningsfunktionen för widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **event_processing** Pekare till ny händelsebearbetningsfunktion

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Åsidosättning av lyckad widgethändelsebearbetning
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="description"></a>Description

Den här tjänsten skickar en händelse till widgetens överordnade.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **händelse** Pekare till händelsen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Händelsen har skickats till widgetens överordnade
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="set-widget-background-color"></a>Ange bakgrundsfärg för widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_fill_color_set(
    GX_WIDGET *widget,
    GX_RESOURCE_ID normal_color_id,
    GX_RESOURCE_ID selected_color_id,
    GX_RESOURCE_ID disabled_color_id);
```
### <a name="description"></a>Description

Den här tjänsten anger widgetens bakgrundsfärger.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **normal_color_id** Resurs-ID för fyllningsfärgen i normalt tillstånd. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.
- **selected_color_id** Resurs-ID för fyllningsfärgen när widgeten får fokus. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.
- **disabled_color_id** Resurs-ID för fyllningsfärgen när GX_STYLE_ENABLED inte har angetts. **Bilaga A** innehåller fördefinierade resurs-ID:er för färg. Observera att programmet kan lägga till resurs-ID:n för anpassad färg också.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har angett widgetens fyllningsfärg
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="find-child-widget-of-parent-widget"></a>Hitta underordnad widget för överordnad widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    INT search_depth, 
    GX_WIDGET **return_widget);
```
### <a name="description"></a>Description

Den här tjänsten söker igenom underordnade objekt till den angivna överordnade och letar efter en widget med det begärda ID-värdet.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget som sökningen startas från
- **widget_id** Widget-ID att söka efter
- **search_depth** Definierar den rekursiva kapslingsnivå där funktionen söker efter underordnade widgetar. Om det här värdet <= 0 genomsöks endast omedelbara underordnade till den överordnade widgeten. Om det här GX_SEARCH_DEPTH_INFINITE söks alla underordnade till alla underordnade widgetar igenom. För andra värden > 0 begränsar det här värdet hur djupt kapslat funktionen söker igenom underordnade widgetar som har sökts efter det begärda widget-ID:t.
- **return_widget** Pekare till mål för hittad widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hitta en lyckad widget
- **GX_NOT_FOUND** widget (0x09) fungerar inte
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="return-pointer-to-first-child-widget"></a>Gå tillbaka till den första underordnade widgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_first_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX har en trädstrukturerad lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till den första underordnade widgeten för den överordnade widgeten.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget_return** Pekare för att returnera widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) returnerad pekare
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="move-focus-to-next-widget-in-navigation-order"></a>Flytta fokus till nästa widget i navigeringsordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_focus_next(GX_WIDGET *widget);
```

### <a name="description"></a>Description

Den här tjänsten flyttar fokus till nästa widget på samma nivå i den länkade listan över widgetar som accepterar fokus.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widgetkontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) har flyttats
- **GX_FAILURE** (0x00) flyttades inte
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

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
### <a name="move-focus-to-previous-widget-in-navigation-order"></a>Flytta fokus till föregående widget i navigeringsordning

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_focus_previous(GX_WIDGET *widget);
```

### <a name="description"></a>Description

Den här tjänsten flyttar fokus till föregående widget i navigeringsordningen.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget som aktuell har indatafokus.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) har flyttats
- **GX_FAILURE** (0x00) flyttades inte

### <a name="allowed-from"></a>Tillåts från

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
### <a name="description"></a>Description

Den här tjänsten hämtar teckensnittet som är associerat med det angivna resurs-ID:t från teckensnittstabellen på skärmen där widgeten visas. Den här funktionen ska bara anropas av en synlig widget.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widgetkontrollblock
- **resource_id** Resurs-ID för teckensnitt
- **return_font** Pekare till mål för teckensnittspekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Teckensnittet har hämtats
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CANVAS** (0x20) Widget-arbetsytan är inte giltig eller widgeten är osynlig
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="release-memory-associated-with-a-widget"></a>Frigöra minne som är associerat med en widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_free(GX_WIDGETG *widget);
```

### <a name="description"></a>Description

Den här tjänsten släpper minnet som är associerat med ett widgetkontrollblock.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widgetkontrollblock
- **resource_id** Resurs-ID för teckensnitt
- **return_font** Pekare till mål för teckensnittspekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Har frisfritt widget
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) Minnesfri funktion har inte definierats
- **GX_PTR_ERROR** (0x07) Ogiltig widget-pekare

### <a name="allowed-from"></a>Tillåts från

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
### <a name="move-widget-to-front"></a>Flytta widget till front

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_front_move(
    GX_WIDGET *widget, 
    GX_BOOL *return_moved);
```

### <a name="description"></a>Description

Den här tjänsten flyttar widgeten till fronten i den överordnade Z-ordningens lista över underordnade widgetar.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget att flytta
- **return_moved** Pekare till mål för indikeringswidgeten har flyttats

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget flytta till front
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_NO_CHANGE** widget (0x08) redan framför
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-widget-height"></a>Hämta widgethöjd

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_height_get(
    GX_WIDGET *widget,
    UINT *return_height);
```

### <a name="description"></a>Description

Den här tjänsten hämtar widgetens höjd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_height** Pekare till mål för widgethöjd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widgethöjd få
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten döljer widgeten. Den här widgeten är fortfarande kopplad till den överordnade widgeten, men den får inte ritas på arbetsytan.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** widgeten har 0x00 (0x00) döljs
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="return-pointer-to-last-child-widget"></a>Återgå pekaren till den senaste underordnade widgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_last_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX har en trädstrukturerad lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till den sista underordnade widgeten för den överordnade widgeten.

### <a name="parameters"></a>Parametrar

- **överordnad** Pekare till överordnad widget
- **widget_return** Pekare för att returnera widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) returnerad pekare
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="return-pointer-to-next-sibling-of-current-widget"></a>Gå tillbaka till nästa nivå för den aktuella widgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_next_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX har en trädstrukturerad lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till nästa nivå på samma nivå som den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuell** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) returnerad pekare
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="return-pointer-to-parent-of-current-widget"></a>Returnera pekaren till överordnad för den aktuella widgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_parent_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX har en trädstrukturerad lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till den överordnade widgeten för den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuell** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) returnerad pekare
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="get-pixelmap"></a>Hämta pixelkarta

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_pixelmap_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_PIXELMAP **return_pixelmap);
```

### <a name="description"></a>Description

Den här tjänsten hämtar pixelkartan som är associerad med det angivna resurs-ID:t. Den här tjänsten bör endast anropas för synliga widgetar.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widgetkontrollblock
- **pixelmap_id** Resurs-ID för pixelkarta
- **return_pixelmap** Pekare till målpekaren för pixelkarta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad pixelkarta get
- **GX_INVALID_RESOURCE_ID** (0x33) Ogiltigt resurs-ID
- **GX_INVALID_CANVAS** (0x20) Widget-arbetsytan är inte giltig eller widgeten är osynlig
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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
### <a name="return-pointer-to-previous-sibling-of-the-current-widget"></a>Gå tillbaka till föregående på samma sätt som den aktuella widgeten

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_previous_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Description

GUIX har en trädstrukturerad lista över överordnade och underordnade widgetar. Den här tjänsten returnerar en pekare till föregående på samma sätt som den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuell** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) returnerad pekare
- **GX_PTR_ERROR** (0x07) Felaktig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten ändrar storlek på widgeten. Om widgeten visas blir den automatiskt ogiltig och i kö för omritning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **new_size** Ny widgetstorlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Ändra storlek på en lyckad widget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="shift-widget"></a>Skift-widget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_shift(
    GX_WIDGET *widget, 
    GX_VALUE x_shift,
    GX_VALUE y_shift, 
    GX_BOOL mark_dirty);
```

### <a name="description"></a>Description

Den här tjänsten flyttar widgeten och markerar den eventuellt som felig.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **x_shift** Antal bildpunkter som ska flyttas på x-axeln
- **y_shift** Antal bildpunkter som ska flyttas på y-axeln
- **mark_dirty** GX_TRUE för att indikera en grov, annars GX_FALSE

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget för GX_CALLER_ERROR (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten visar widgeten. Widgeten blir bara synlig om den är kopplad till en överordnad widget och den överordnade widgeten också visas.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widget visas
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="add-widget-status"></a>Lägg till widgetstatus

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_add(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Description

Den här tjänsten lägger till valfri kombination av statusflaggor till den angivna widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **status** Status att lägga till

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Status för lyckad widget har lagt till
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-widget-status"></a>Hämta widgetstatus

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_get(
    GX_WIDGET *widget,
    ULONG *return_status)
```

### <a name="description"></a>Description

Den här tjänsten hämtar statusflaggor från widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_status** Pekare till den status som returneras

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Status för lyckad widget får
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="remove-widget-status"></a>Ta bort widgetstatus

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_remove(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Description

Den här tjänsten tar bort de angivna statusflaggorna från widgetens interna statusvariabel.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **status** Status att ta bort

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad statusborttagning av widget
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="test-widget-status"></a>Status för testwidget

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_status_test(
    GX_WIDGET *widget, 
    ULONG status,
    GX_BOOL *return_test);
```
### <a name="description"></a>Description

Den här tjänsten testar statusflaggorna för den angivna widgeten och lagrar resultatet i minnet som "return_test".

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **status** Status att testa
- **return_status** Pekare till mål för testresultat

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Statustest för lyckad widget
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id-deprecated"></a>Hämta sträng som är associerad med en synlig widget och sträng-ID (inaktuell)

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_widget_string_get_ext().

Den här tjänsten returnerar strängtabellposten för det angivna sträng-ID-värdet. Den här tjänsten liknar den gx_display_string_get, förutom att den aktiva visningen fastställs automatiskt i stället för att skickas av anroparen. Den här tjänsten kan bara användas för widgetar som är synliga, dvs. visningen som är associerad med den här widgeten är känd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **string_id** Sträng-ID-värde från resurshuvud
- **sträng** Adressen för variabeln som ska returneras av strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Statustest för lyckad widget
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id"></a>Hämta sträng som är associerad med en synlig widget och sträng-ID

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

Den här tjänsten returnerar strängtabellposten för det angivna sträng-ID-värdet. Den här tjänsten liknar den gx_display_string_get, förutom att den aktiva visningen fastställs automatiskt i stället för att skickas av anroparen. Den här tjänsten kan bara användas för widgetar som är synliga, dvs. visningen som är associerad med den här widgeten är känd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **string_id** Sträng-ID-värde från resurshuvud
- **sträng** Adressen för variabeln som ska returneras av strängen

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Statustest för lyckad widget
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="add-widget-style"></a>Lägg till widgetformat

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_add(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Description

Den här tjänsten lägger till ett format i widgeten. Dessutom vidtas följande åtgärder.

Om det tillagda formatet GX_STYLE_TRANSPARENT läggs statusen GX_STATUS_TRANSPARENT till.

Om det tillagda formatet GX_STYLE_ENABLED läggs statusen GX_STATUS_SELECTABLE till.

Om widgeten visas blir den automatiskt ogiltig och i kö för omritning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **style** Nytt format att lägga till. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Successful widget style add
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-widget-style"></a>Hämta widgetformat

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_get(
    GX_WIDGET *widget, 
    ULONG *return_style)
```

### <a name="description"></a>Description

Den här tjänsten hämtar formatflaggan från widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_style** Pekare till formatet som returneras.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Widgetformatet har hämtats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="remove-widget-style"></a>Ta bort widgetformat

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_remove(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Description

Den här tjänsten tar bort ett format från widgeten. Dessutom vidtas följande åtgärder.

Om det borttagna formatet GX_STYLE_TRANSPARENT tas statusen GX_STATUS_TRANSPARENT bort.

Om det borttagna formatet GX_STYLE_ENABLED tas GX_STATUS_SELECTABLE bort.

Om widgeten visas ogiltigförklaras den automatiskt och läggs i kö för omritning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **style** Stil som ska tas bort. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Bort från widgetformatet
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="set-widget-style"></a>Ange widgetformat

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_style_set(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Description

Den här tjänsten anger ett format till widgeten.

Om uppsättningsformatet GX_STYLE_TRANSPARENT läggs statusen GX_STATUS_TRANSPARENT, annars tas statusen bort.

Om uppsättningsformatet GX_STYLE_ENABLED läggs statusen GX_STATUS_SELECTABLE, annars tas statusen bort.

Om widgeten visas ogiltigförklaras den automatiskt och läggs i kö för omritning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **style** Stil som ska anges. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Stiluppsättning för lyckad widget
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="blend-text-assigned-to-widget-deprecated"></a>Blanda text tilldelad till widget (inaktuell)

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

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_widget_text_blend_ext().

Den här tjänsten blandar den angivna texten över en widget med hjälp av aktuell pensel- och textjustering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Textfärg
- **font_id** Teckensnitts-ID
- **sträng** Ritningssträng
- **x_offset** Justering av ritningsposition
- **y_offset** Justering av ritningsposition
- **alfa** Blandningsvärde 0–255

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widgetbredd get
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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
### <a name="blend-text-assigned-to-widget"></a>Blanda text tilldelad till widget

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

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_widget_text_blend_ext().

Den här tjänsten renderar en sträng över den angivna widgeten med hjälp av den aktuella pensel- och textjusteringen och angiven färg, teckensnitt och x,y-förskjutning.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Textfärg
- **font_id** Teckensnitts-ID
- **sträng** Ritningssträng
- **x_offset** Justering av ritningsposition
- **y_offset** Justering av ritningsposition
- **alfa** Blandningsvärde 0–255

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widgetbredd get
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_STRING_LENGTH** (0x34) Ogiltig stränglängd

### <a name="allowed-from"></a>Tillåts från

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
### <a name="draw-text-assigned-to-widget-deprecated"></a>Rita text tilldelad till widget (inaktuell)

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

### <a name="description"></a>Description

Den här tjänsten är inaktuell till förmån för gx_widget_text_draw_ext().

Den här tjänsten ritar den angivna texten över en widget med hjälp av aktuell pensel- och textjustering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Textfärg
- **font_id** Teckensnitts-ID
- **sträng** Ritningssträng
- **x_offset** Justering av ritningsposition
- **y_offset** Justering av ritningsposition

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="draw-text-assigned-to-widget"></a>Rita text tilldelad till widget

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

### <a name="description"></a>Description

Den här tjänsten ritar den angivna texten över en widget med hjälp av aktuell pensel- och textjustering.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Textfärg
- **font_id** Teckensnitts-ID
- **text_id** Text-ID
- **x_offset** Justering av ritningsposition
- **y_offset** Justering av ritningsposition

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="draw-text-assigned-to-widget"></a>Rita text tilldelad till widget

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

### <a name="description"></a>Description

Den här tjänsten ritar text över en widget givet ett text-ID.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **tColor** Textfärg
- **font_id** Teckensnitts-ID
- **text_id** Text-ID
- **x_offset** Justering av ritningsposition
- **y_offset** Justering av ritningsposition

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

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
### <a name="return-pointer-to-visible-child-that-is-top-of-z-order"></a>Returnera pekaren till synlig underordnad som är överst i Z-ordningen

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_top_visible_child_find(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Description

GUIX har en trädstrukturerad lista över över- och underordnade widgetar.
Den här tjänsten returnerar en pekare till den översta synliga underordnade till den aktuella widgeten.

### <a name="parameters"></a>Parametrar

- **aktuell** Pekare till aktuell widget
- **widget_return** Pekare för att returnera widget-pekare

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) returnerad pekare
- **GX_PTR_ERROR** (0x07) Ogiltig widget-pekare
- **GX_INVALID_WIDGET** (0x12) Ogiltig widget

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten söker efter en widget av den begärda typen.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_width** Pekare till mål för widgetbredd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widgetbredd get
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-widget-width"></a>Hämta widgetbredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_widget_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width)
```

### <a name="description"></a>Description

Den här tjänsten hämtar widgetens bredd.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widget
- **return_width** Pekare till mål för widgetbredd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad widgetbredd get
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-window-client-height"></a>Hämta fönsterklientens höjd

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_client_height_get(
    GX_WINDOW *window,
    GX_VALUE *return_height);
```

### <a name="description"></a>Description

Den här tjänsten hämtar klientens höjd för fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **return_height** Pekare till mål för klientens höjd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckade fönsterklienthöjd get
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="scroll-window-clients"></a>Rullningsfönsterklienter

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_client_scroll(
    GX_WINDOW *window, 
    GX_VALUE x_scroll,
    GX_VALUE y_scroll);
```

### <a name="description"></a>Description

Den här tjänsten rullar fönsterklienterna med det angivna beloppet.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **x_scroll** Mängd som ska rullas på x-axeln
- **y_scroll** Mängd som ska rullas på y-axeln

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad fönsterklientrullning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_VALUE** (0x22) Rullningsvärden är inte giltiga

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-window-client-width"></a>Hämta fönsterklientbredd

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_client_width_get(
    GX_WINDOW *window,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

Den här tjänsten hämtar klientbredden för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **return_height** Pekare till mål för klientbredd

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad fönsterklientbredd get
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="close-modal-window"></a>Stäng modalfönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_close(GX_WINDOW *window);
```

### <a name="description"></a>Description

Den här tjänsten tvingar ett modalt fönster att koppla från det överordnade fönstret och returnera från den modala körningsloopen.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönsterkontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Fönstret har stängts
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="create-window"></a>Fönstret Skapa

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

### <a name="description"></a>Description

Den här tjänsten skapar ett fönster.

GX_WINDOW härleds från GX_WIDGET och stöder alla gx_widget API-tjänster.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönsterkontrollblock
- **namn** Fönstrets logiska namn
- **överordnad** Pekare till överordnad widget
- **style** Fönsterformat. **Bilaga D** innehåller fördefinierade allmänna format för alla widgetar samt widgetspecifika format.
- **window_id** Fönstrets programdefinierade ID
- **storlek** Fönstrets storlek

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Skapa ett fönster
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_ALREADY_CREATED** widgeten (0x13) har redan skapats
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="draw-window"></a>Fönstret Rita

### <a name="prototype"></a>Prototyp

```C
VOID gx_window_draw(GX_WINDOW *window);
```

### <a name="description"></a>Description

Den här tjänsten ritar ett fönster. Den här tjänsten kallas vanligtvis internt under uppdatering av arbetsytan, men kan även anropas från anpassade fönsterritningsfunktioner.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönsterkontrollblock

### <a name="return-values"></a>Returvärden

- **Ingen**

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="process-window-event"></a>Processfönsterhändelse

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_event_process(
    GX_WINDOW *window, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

Den här tjänsten bearbetar en händelse för det här fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönsterkontrollblock
- **händelse** Pekare till händelse att bearbeta

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad bearbetning av fönsterhändelse
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="modally-execute-a-window"></a>Kör ett fönster modally

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_execute(
    GX_WINDOW *window,
    ULONG *return_ptr)
```

### <a name="description"></a>Description

Den här tjänsten kör ett fönster. Användarindata (pennhändelser osv.) utanför fönstrets klientområde ignoreras. Observera att den här funktionen går in i en kontinuerlig blockerande körningsloop och inte återgår till anroparen förrän modellkörningen avslutas.

Modal körning avslutas när händelsebearbetningen för en mottagen händelse returnerar ett statusvärde som inte är noll eller när API-gx_window_close anropas. Returkoden för händelsebearbetning som inte är noll returneras till anroparen via den return_ptr skickas till det här API:et

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönsterkontrollblock
- **return_ptr** Plats för att spara avslutsstatus för modal körning. Kan vara GX_NULL.

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad körning
- **GX_SYSTEM_EVENT_RECEIVE_ERROR(0x05)** Upphämtningshändelsen från händelsekön misslyckades
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="create-a-root-window"></a>Skapa ett rotfönster

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

### <a name="description"></a>Description

Den här tjänsten skapar ett rotfönster.

### <a name="parameters"></a>Parametrar

- **root_window** Pekare till rotfönstrets kontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Rotfönstret har skapats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_SIZE** (0x19) Ogiltig blockstorlek för widgetkontroll
- **GX_ALREADY_CREATED** (0x13) Widget har redan skapats

### <a name="allowed-from"></a>Tillåts från

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
### <a name="destroy-a-root-window"></a>Förstöra ett rotfönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_delete(GX_WINDOW_ROOT *root_window)
```

### <a name="description"></a>Description

Den här tjänsten tar bort ett rotfönster.

### <a name="parameters"></a>Parametrar

- **root_window** Pekare till rotfönstrets kontrollblock

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Rotfönstret har tagits bort
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Minnesfri funktion har inte definierats

### <a name="allowed-from"></a>Tillåts från

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
### <a name="process-event-for-the-root-window"></a>Processhändelse för rotfönstret

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_EVENT *event)
```

### <a name="description"></a>Description

Den här tjänsten bearbetar händelser för det angivna rotfönstret.

### <a name="parameters"></a>Parametrar

- **root_window** Pekare till rotfönstrets kontrollblock
- **händelse** Pekare till den händelse som ska bearbetas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Rotfönsterhändelsen har bearbetats
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="find-root-window"></a>Hitta rotfönstret

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_root_find(
    GX_WIDGET *widget,
    GX_WINDOW_ROOT **return_root_window);
```

### <a name="description"></a>Description

Den här tjänsten hittar rotfönstret för den angivna widgeten.

### <a name="parameters"></a>Parametrar

- **widget** Pekare till widgetkontrollblock
- **return_root_window** Pekare till mål för rotfönstret som hittas

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad rotfönsters find
- **GX_FAILURE** (0x00) Rotfönstret finns inte
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-window-scroll-info"></a>Hämta information om fönsterrullning

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_scroll_info_get(
    GX_WINDOW *window, 
    ULONG style,
    GX_SCROLL_INFO *return_scroll_info);
```

### <a name="description"></a>Description

Den här tjänsten hämtar rullningsinformationen för fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **style** GX_SCROLLBAR_HORIZONTAL eller GX_SCROLLBAR_VERTICAL
- **return_scroll_info** Pekare till mål för rullningsinformation. Det överordnade fönstret initierar den här strukturen för att informera rullningslisten för det överordnade fönstrets totala storlek, visningsbart område och rullningssteg och gränser. Standardimplementering använder Windows-klientområdet som visningsbart område och rullar med bildpunkter, men anpassad fönsterimplementering kan använda rullningsparametrarna. **Bilaga I** innehåller definitionen av GX_SCROLL_INFO struktur

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Information om lyckad fönsterrullning hämta
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_TYPE** (0x1B) Ogiltig typ

### <a name="allowed-from"></a>Tillåts från

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
### <a name="find-window-scrollbar"></a>Hitta rullningslist för fönster

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_scrollbar_find(
    GX_WINDOW *window, 
    USHORT type,
    GX_SCROLLBAR **return_scrollbar);
```

### <a name="description"></a>Description

Den här tjänsten hittar rullningslisten för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **typ** GX_TYPE_VERTICAL_SCROLL eller GX_TYPE_HORIZONTAL_SCROLL
- **return_scrollbar** Pekare till mål för rullningslisten

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Hitta rullningslisten i fönstret
- **Rullningslisten** GX_NOT_FOUND (0x09) hittades inte
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig
- **GX_INVALID_TYPE** (0x1B) Ogiltig typ

### <a name="allowed-from"></a>Tillåts från

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
### <a name="get-window-wallpaper"></a>Hämta fönsterbakgrund

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_wallpaper_get(
    GX_WINDOW *window,
    GX_RESOURCE_ID *return_wallpaper_id);
```

### <a name="description"></a>Description

Den här tjänsten hämtar skrivbordsunderlägget för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **return_wallpaper_id** Pekare till mål för resurs-ID för skrivbordsunderlägg

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Fönsterbakgrund hämta
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
### <a name="set-window-wallpaper"></a>Ange fönsterbakgrund

### <a name="prototype"></a>Prototyp

```C
UINT gx_window_wallpaper_set(
    GX_WINDOW *window,
    GX_RESOURCE_ID wallpaper_id,
    GX_BOOL tile);
```

### <a name="description"></a>Description

Den här tjänsten anger skrivbordsunderlägget för det angivna fönstret.

### <a name="parameters"></a>Parametrar

- **fönster** Pekare till fönster
- **wallpaper_id** Resurs-ID för skrivbordsunderlägg som ska användas
- **panel** Skrivbordsunderlägget är GX_TRUE, annars är skrivbordsunderlägget inte panelerat

### <a name="return-values"></a>Returvärden

- **GX_SUCCESS** (0x00) Lyckad fönsterbakgrundsuppsättning
- **GX_CALLER_ERROR** (0x11) Ogiltig anropare för den här funktionen
- **GX_PTR_ERROR** (0x07) Ogiltig pekare
- **GX_INVALID_WIDGET** (0x12) Widget är inte giltig

### <a name="allowed-from"></a>Tillåts från

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
