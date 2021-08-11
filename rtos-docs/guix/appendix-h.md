---
title: Bilaga H – GUIX Build-Time Configuration-flaggor
description: Lär dig mer om GUIX-konfigurationsflaggor för byggtid.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ecd4d86fbc6fb1ebaa002675e66492758edaf14ed90aa03fc9f4cf4abb87e661
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784214"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>Bilaga H – GUIX Build-Time Configuration-flaggor

GUIX stöder flera alternativ för villkorlig kompilering och konfigurationsvärden. Standardinställningen för dessa villkor och konfigurationsvärden kan åsidosättas genom att definiera värdet i förväg, antingen i gx_user.h-huvudfilen eller på kompilatorns kommandorad.

**GX_DISABLE_THREADX_BINDING**
- Standard: Odefinierad
- Beskrivning: Den här villkorsinställningen kan användas för att inaktivera standard-ThreadX RTOS-bindningen. Om du vill köra GUIX med ett annat RTOS än ThreadX bör du #define GX_DISABLE_THREADX_BINDING tillhandahålla dina egna RTOS-bindningstjänster.

GX_SYSTEM_TIMER_MS
- Standard: 20
- Beskrivning: Det här värdet definierar önskat GUIX-timerintervall eller precision.

TX_TIMER_TICKS_PER_SECOND
- Standard: 100
- Beskrivning: Det här värdet definierar antalet avbrottsfrekvenser för TX-timer. Eftersom standardtimern för ThreadX-intervallet är 10 ms används som standard 100 Hz-frekvens för det här värdet.

GX_DISABLE_MULTITHREAD_SUPPORT
- Standard: Inte definierad
- Beskrivning: Den här kompileringstiden kan användas för att inaktivera GUIX API-stöd för flera trådar som anropar GUIX API samtidigt. Om endast en programtråd någonsin kommer att använda GUIX-API:et bör du definiera den här flaggan för att minska systemkostnaderna för skydd av kritiska kodavsnitt.

GX_DISABLE_UTF8_SUPPORT
- Standard: Inte definierad.
- Beskrivning: Den här kompileringstiden kan användas för att ta bort det interna GUIX-stödet för UTF8-formatsträngkodning. Om du bara använder teckenvärden M-0xff i ditt program minskar den kodstorlek och det omkostnader som är associerade med stöd för UTF8-formatssträngkodning om du #define den här #define.

GX_DISABLE_ARC_DRAWING_SUPPORT
- Standard: Inte definierad.
- Beskrivning: Detta villkor kan användas för att minska GUIX-bibliotekets kodstorlek och GX_DISPLAY-strukturstorlek genom att ta bort stöd för arc-drawing-funktionerna cirkel, båge, cirkel och ellips. Dessa funktioner krävs inte av guix-standardwidgetuppsättningen.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- Standard: Inte definierad.
- Beskrivning: Detta villkor kan definieras för att ta bort stöd för GUIX-bibliotekskörning för JPEG- och PNG-programavkodare. Om programmet inte kräver körningsavkodning av jpg- eller png-filer, vilket innebär att programmet inte använder pixelkartor i RAW-format som skapas av Studio och inte läser bildfiler från ett externt filsystem, kan du aktivera den här #define för att minska GUIX-bibliotekets fotavtryck.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- Standard: Inte definierad
- Beskrivning: Detta villkor kan användas för att ta bort GUIX-biblioteksstödet för inläsning av binära resursdata. Binära resurser kan användas för att göra körningsbindning av resursdata med ditt GUIX-program. Om du bara använder C-källkodsformatets resursfiler kan du definiera detta villkor för att minska guix-bibliotekets fotavtryck.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- Standard: Inte definierad.
- Beskrivning: Vid körning med 16 bpp och högre färgdjup stöder GUIX valfritt ritning av icke-arc-grafik, pixelkartor och teckensnitt med ett alfavärde som definieras av penseln för ritningskontext. Stöd för det här ritningsläget medför en liten ökning av körningskostnader och biblioteksfotavtryck, som kan elimineras genom att definiera den här flaggan om du inte behöver stöd för alfablandningsritning. Observera att pixelkartor med alfakanal, antialiasade teckensnitt och andra antialiasritningslägen fortfarande stöds oavsett den här villkorliga inställningen.

GX_DISABLE_THREADX_TIMER_SOURCE
- Standard: Inte definierad.
- Beskrivning: Detta villkor kan användas för att inaktivera ThreadX-timerkällan. Du bör definiera GX_DISABLE_THREADX_TIMER_SOURCE om du vill använda en annan timerkälla.

GX_REPEAT_BUTTON_INITIAL_TICS
- Standard: 10.
- Beskrivning: Om en knapp har GX_STYLE_BUTTON_REPEAT anger det här värdet hur länge knappen ska vänta innan den börjar skicka upprepade GX_EVENT_CLICKED händelser.

GX_MAX_QUEUE_EVENTS
- Standard: 48.
- Beskrivning: Definierar storleken på GUIX-händelsekön i enheter med poster för händelsestruktur. Om händelsekön spills över tas händelser som push-skickas till kön bort och GX_SYSTEM_ERROR returneras av funktionen gx_system_event_send().

GX_MAX_DIRTY_AREAS
- Standard: 64.
- Beskrivning: Definierar det maximala antalet unika poster i listan som kan underhållas av en arbetsyta. När den felformaterande listan spills över markerar GUIX som standard arbetsytans rotfönster som felformat, vilket är mindre effektivt än att rita enskilda underordnade widgetar.

GX_MAX_CONTEXT_NESTING
- Standard: 8.
- Beskrivning: Definierar den maximala kapsling för ritningskontextstacken. Detta motsvarar den maximala kapsling av över-/underordnade/underordnade/underordnade widgetar i gränssnittsdefinitionen.

GX_MAX_INPUT_CAPTURE_NESTING
- Standard: 4.
- Beskrivning: Definierar storleken på stacken som används för att underhålla listan över widgetar som fångar användarens indata (mus och tangentbord).

GX_SYSTEM_THREAD_PRIORITY
- Standard: 16.
- Beskrivning: Definierar prioriteten för GUIX-tråden som skapades under gx_system_initialize().

GX_SYSTEM_THREAD_TIMESLICE
- Standard: 10.
- Beskrivning: Definierar GUIX-trådens tidslikhet när det gäller RTOS-timers tick. Om andra trådar definieras med samma prioritet som GUIX-tråden avgör det här värdet hur ofta dessa konkurrerande trådar beviljas CPU-kontroll.

GX_CURSOR_BLINK_INTERVAL
- Standard: 20.
- Beskrivning: Definierar den hastighet med vilken indatamarkören blinkar för textinmatningswidgetar. Det här värdet gäller tick för GUIX-timer, som som standard definieras som 50 ms, så värdet 20 anger att indatamarkören blinkar en gång per sekund.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- Standard: 32.
- Beskrivning: Definierar storleken på list-start-indexcachen som underhålls av flerrads-textvyn och flerradswidgetar för textinmatning. Den här cachen används för att utföra snabb vertikal rullning av flerradstextwidgetar. För bästa prestanda bör cachestorleken anges större än antalet synliga rader i den största flerradstextwidgeten som definieras av programmet. Om till exempel de mest synliga raderna för en textwidget är 20 rader kan programmet definiera en cachestorlek på 32 (standard), vilket gör att GUIX kan rulla lodrätt utan att räkna om alla radstartsindex.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- Standard: 4.
- Beskrivning: Kontrollblocket för flerradstextknappen har en pekare till varje rad med text som ska visas av knappen. Det här värdet avgör hur många textpekare som behövs av den sämsta flerradstextknappen.

GX_POLYGON_MAX_EDGE_NUM
- Standard: 10.
- Beskrivning: Det här värdet avgör den mest komplexa polygonen som kan ritas med GUIX. Algoritmen för polygonritning avgör vilka linjer som behövs för att definiera polygonkanterna, och den här definitionen definierar det maximala antalet kanter som kan stödjas.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- Standard: 16.
- Beskrivning: För ett nummerrullningshjul konverterar widgeten för rullningshjul heltalsvärden till ascii-strängar. Det här värdet avgör den maximala längden på strängen som krävs för att visa de tilldelade heltalsvärdena.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- Standard: 5.
- Beskrivning: Definierar antalet GUIX-timer tick (50 ms) mellan uppdateringar av en cirkelmätare som konfigurerats för att animera nålförflyttningen mellan den sista och aktuella vinkelpositionen.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- Standard: 16.
- Beskrivning: En numerisk prompt allokerar en buffert för att konvertera ett heltalsvärde som tilldelats prompten till en ascii-sträng. Den här definitionen definierar storleken på den här teckenbufferten.

GX_ANIMATION_POOL_SIZE
- Standard: 6.
- Beskrivning: GUIX definierar en animeringspool från vilken strukturer med animeringsinformation kan allokeras och returneras dynamiskt med hjälp av gx_system_animation_get- och gx_system_animation_free()-API:er. Den här definitionen definierar storleken på den här animeringskontrollblockpoolen.

GX_MOUSE_SUPPORT
- Standard: Inte definierad.
- Beskrivning: Den här definitionen ger stöd för musinmatning. Programvarumusen kräver att visningsdrivrutinen ritar och spårar musmarkören, vilket ger extra kostnader för visningsdrivrutinen. Den här definitionen bör endast definieras när en mus (inte en pekskärm) måste stödjas.

GX_HARDWARE_MOUSE_SUPPORT
- Standard: Inte definierad.
- Beskrivning: När den här definitionen definieras använder GUIX-visningsdrivrutinen stöd för maskinvarumarkörsritning. Detta minskar det minne som krävs för att avbilda arbetsytans minne under musmarkören och förbättrar systemprestanda för de maskinvarumål som stöder ett grafiklager med musöverlägg.

GX_FONT_KERNING_SUPPORT
- Standard: Inte definierad.
- Beskrivning: Den här definitionen kan definieras för att aktivera stöd för teckensnitts-kerning. Tecken kerning förbättrar glyph avstånd för vissa glyph kombinationer. Det här stödet lägger till en liten mängd omkostnader för ritningsfunktionerna för körningssträngar och lägger också till en liten mängd storlek i teckendatastrukturerna.

GX_WIDGET_USER_DATA
- Standard: Inte definierad.
- Beskrivning: Om detta definieras läggs ett användardefinierat datafält till i GX_WIDGET kontrollblocket. Det här datafältet kan tilldelas med hjälp av egenskapsvyn i GUIX Studio. Det här datafältet ignoreras av GUIX internt, men kan användas av programprogramvara för många olika syften.

GUIX_5_4_0_COMPATIBILITY
- Standard: Inte definierad.
- Beskrivning: Vissa GUI-API:er ändrades efter version 5.4.0 för att lägga till stöd för inaktiverade textfärger och för att förbättra noggrannheten för vissa matematiska funktioner med hjälp av matchningsparametrar med fast punkt. Dessa ändringar gör att GUIX-biblioteksutgåningar efter 5.4.0 inte är kompatibla med tidigare versioner. Men genom att aktivera den här #define-versionen kan biblioteket byggas så att API:erna är helt kompatibla med versionerna <= 5.4.0, vilket innebär att inga ändringar behövs i befintliga program för att kompileras med den senaste GUIX-bibliotekslanseringen.

GX_MAX_STRING_LENGTH
- Standard: 102400
- Beskrivning: Definierar den maximala längden på en sträng, som används för att testa ogiltiga strängar. Om indatasträngen överskrider den maximala stränglängden kommer den att betrakta den som ogiltig.