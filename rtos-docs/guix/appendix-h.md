---
title: Bilaga H – GUIX Build-Time konfigurations flaggor
description: Lär dig mer om konfigurations flaggor för GUIX-kompilering.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 65095e326bc6809eba6e9472e2d74325351354ca
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826415"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>Bilaga H – GUIX Build-Time konfigurations flaggor

GUIX stöder flera alternativ för villkorlig kompilering och konfigurations värden. Standardinställningen för dessa villkor och konfigurations värden kan åsidosättas genom att förkonfigurera värdet, antingen i sidhuvuds filen gx_user. h eller på kommando raden för kompileraren.

**GX_DISABLE_THREADX_BINDING**
- Standard: odefinierad
- Beskrivning: det här villkoret kan användas för att inaktivera standard bindningen för ThreadX-återställnings tider. Om du vill köra GUIX med en annan återställnings tider än ThreadX bör du #define GX_DISABLE_THREADX_BINDING och tillhandahålla dina egna återställnings tider-bindnings tjänster.

GX_SYSTEM_TIMER_MS
- Standard: 20
- Beskrivning: det här värdet definierar det önskade intervallet för GUIX-timer eller precision.

TX_TIMER_TICKS_PER_SECOND
- Standard: 100
- Beskrivning: det här värdet definierar antalet avbrotts frequences för TX-timer. Eftersom standardvärdet för ThreadX-intervall är 10 MS, är det här värdet som standard en frekvens på 100 Hz.

GX_SYSTEM_TIMER_TICKS
- Standard: ((GX_SYSTEM_TIMER_MS * TX_TIMER_TICKS_PER_SECOND)/1000)
- Beskrivning: det här värdet definierar antalet underliggande återställnings tider timer-Tick per GUIX timer-Ticket. Standardvärdet är 2, vilket innebär att GUIX timer-intervall är 2 ThreadX timer-avbrott eller 20 MS som standard.

GX_DISABLE_MULTITHREAD_SUPPORT
- Standard: inte definierat
- Beskrivning: denna villkorliga kompileringstid kan användas för att inaktivera GUIX API-stöd för flera trådar som anropar GUIX-API samtidigt. Om endast en program tråd kommer att använda GUIX-API: et bör du definiera den här flaggan för att minska systemets kostnader för att skydda viktiga kod avsnitt.

GX_DISABLE_UTF8_SUPPORT
- Standard: har inte definierats.
- Beskrivning: denna villkorliga kompileringstid kan användas för att ta bort GUIX internt stöd för UTF8-format. Om du bara använder tecken värden M-0xFF i ditt program, kommer den här #define att minska kod storleken och omkostnader som är kopplade till stöd för UTF8-format.

GX_DISABLE_ARC_DRAWING_SUPPORT
- Standard: har inte definierats.
- Beskrivning: det här villkoret kan användas för att minska GUIX-bibliotekets storlek och GX_DISPLAY struktur storlek genom att ta bort stöd för båg ritnings funktionserna cirkel, båge, cirkel och ellips. Dessa funktioner krävs inte av standard uppsättningen för GUIX-widget.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- Standard: har inte definierats.
- Beskrivning: det här villkoret kan definieras för att ta bort stöd för GUIX-biblioteks körning av JPEG och PNG-programvara. Om programmet inte kräver körnings avkodning av jpg-eller PNG-filer, vilket innebär att programmet inte använder RAW-pixelmaps som producerats av Studio och inte läser bildfiler från ett externt fil system, kan du aktivera den här #define för att minska storleken på GUIX-biblioteket.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- Standard: inte definierat
- Beskrivning: det här villkoret kan användas för att ta bort GUIX-bibliotekets stöd för inläsning av binära resurs data. Binära resurser kan användas för körnings bindning av resurs data med ditt GUIX-program. Om du bara använder resursfiler i formatet C-källkod kan du definiera detta villkor för att minska GUIX-bibliotekets storlek.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- Standard: har inte definierats.
- Beskrivning: när du kör med 16 BPP och högre färgdjup, kan GUIX även rita icke-båg grafik, pixelmaps och teckensnitt med ett alfa värde som definieras av rit kontextens pensel. Om du har stöd för det här ritnings läget ökar du storleken på små omkostnader och biblioteks storlekarna, som kan elimineras genom att du definierar den här flaggan om du inte behöver stöd för alfa-blandnings ritning. Observera att pixelmaps med alpha Channel, Kantutjämna teckensnitt och andra kant Utjämnings lägen fortfarande stöds oavsett den här villkorliga inställningen.

GX_DISABLE_THREADX_TIMER_SOURCE
- Standard: har inte definierats.
- Beskrivning: det här villkoret kan användas för att inaktivera ThreadX timer-källa. Du bör definiera GX_DISABLE_THREADX_TIMER_SOURCE om du vill använda en annan timer-källa.

GX_REPEAT_BUTTON_INITIAL_TICS
- Standard: 10.
- Beskrivning: om en knapp har formatet GX_STYLE_BUTTON_REPEAT definierar det här värdet hur lång tid knappen väntar innan den börjar skicka upprepade GX_EVENT_CLICKED händelser.

GX_MAX_QUEUE_EVENTS
- Standard: 48.
- Beskrivning: definierar storleken på händelse kön GUIX i enheter av händelse struktur poster. Om händelse kön överskrider varandra ignoreras händelser som skickas till kön och GX_SYSTEM_ERROR returneras av funktionen gx_system_event_send ().

GX_MAX_DIRTY_AREAS
- Standard: 64.
- Beskrivning: definierar det maximala antalet unika Felaktiga List poster som kan underhållas av en arbets yta. När den skadade listan överflödar, kommer GUIX att markera rot fönstret för arbets ytan som smutsig, vilket är mindre effektivt än att rita enskilda underordnade widgetar.

GX_MAX_CONTEXT_NESTING
- Standard: 8.
- Beskrivning: definierar den maximala kapslingen för rit kontexts Tacken. Detta motsvarar den maximala kapslingen av överordnade/underordnade/underordnade/underordnade widgetar i användar gränssnitts definitionen.

GX_MAX_INPUT_CAPTURE_NESTING
- Standard: 4.
- Beskrivning: definierar den stack storlek som används för att underhålla listan med widgetar som fångar in användarindata (mus och tangent bord).

GX_SYSTEM_THREAD_PRIORITY
- Standard: 16.
- Beskrivning: definierar prioriteten för den GUIX-tråd som skapas under gx_system_initialize ().

GX_SYSTEM_THREAD_TIMESLICE
- Standard: 10.
- Beskrivning: definierar GUIX-trådens timeslice med avseende på återställnings tider timer-Tick. Om andra trådar definieras med samma prioritet som GUIX-tråden, anger det här värdet hur ofta de konkurrerande trådarna beviljas CPU-kontroll.

GX_CURSOR_BLINK_INTERVAL
- Standard: 20.
- Beskrivning: definierar den hastighet som Indatakällan blinkar för att mata in widgetar text ingångar. Värdet är för GUIX timer-Tick, som som standard definieras som 50 ms, så värdet 20 anger att insättnings punkten blinkar en gång per sekund.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- Standard: 32.
- Beskrivning: definierar storleken på den lista över start index som underhålls av widgeten med flera rader och text ingångar i flera rader. Denna cache används för att utföra snabb lodrät rullning av text-widgetar med flera rader. För bästa prestanda bör cachestorleken anges till fler än antalet synliga rader i den största text widgeten för flera rader som definieras av programmet. Om till exempel de mest synliga raderna för en widget för text är 20 rader, kan programmet definiera en cachestorlek på 32 (standard), vilket gör att GUIX kan rulla lodrätt utan att omberäkna alla rad start index.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- Standard: 4.
- Beskrivning: kontroll blocket för flera rader innehåller en pekare till varje textrad som ska visas med knappen. Det här värdet anger antalet text pekare som behövs för den värsta text knappen med flera rader.

GX_POLYGON_MAX_EDGE_NUM
- Standard: 10.
- Beskrivning: det här värdet avgör den mest komplexa polygon som kan ritas av GUIX. Algoritmen för polygon av polygon avgör vilka rader som behövs för att definiera polygonens kanter, och den här definitionen definierar det maximala antalet kanter som kan stödjas.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- Standard: 16.
- Beskrivning: för ett tal rullnings hjul konverterar widgeten rullnings hjul heltal till ASCII-strängar. Det här värdet anger den maximala sträng längden för strängen som krävs för att visa de tilldelade heltals värdena.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- Standard: 5.
- Beskrivning: definierar antalet GUIX timer-Tick (50 ms) mellan uppdateringar av en cirkulär mätare som kon figurer ATS för att animera en nålventil mellan den sista och den aktuella vinkel positionen.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- Standard: 16.
- Beskrivning: en numerisk prompt allokerar en buffert för att konvertera ett heltals värde som tilldelas en prompt till en ASCII-sträng. Den här definitionen definierar storleken på den här teckenformateringen.

GX_ANIMATION_POOL_SIZE
- Standard: 6.
- Beskrivning: GUIX definierar en animeringssekvens från vilken animeringens informations strukturer kan tilldelas dynamiskt och returneras, med hjälp av gx_system_animation_get-och gx_system_animation_free-API: er. Den här definitionen definierar storleken på den här bildpoolen för animeringssekvenss kontroll.

GX_MOUSE_SUPPORT
- Standard: har inte definierats.
- Beskrivning: den här definitionen aktiverar stöd för mus ineffekter. För program varu mus krävs det att bildskärms driv rutinen ritar och spårar mus markören, vilket ger extra kostnader för bildskärms driv rutinen. Den här definitionen ska bara definieras när en mus (inte en touch-skärm) måste stödjas.

GX_HARDWARE_MOUSE_SUPPORT
- Standard: har inte definierats.
- Beskrivning: när den här definitionen har definierats använder GUIX-bildskärms driv rutinen stöd för ritning av maskin varans mus markör. Detta minskar det minne som krävs för att avbilda arbets ytans minne under mus markören och förbättrar system prestandan för dessa maskin varu mål som stöder ett bild lager för mus överlägg.

GX_FONT_KERNING_SUPPORT
- Standard: har inte definierats.
- Beskrivning: den här definitionen kan definieras för att aktivera stöd för teckensnitts kerning. Teckensnitts kerning förbättrar tecken avståndet för vissa kombinationer av glyfer. Det här stödet lägger till en liten mängd kostnader för ritnings funktionerna för körnings funktionen och lägger också till en liten mängd storlek i data strukturerna för teckensnitt.

GX_WIDGET_USER_DATA
- Standard: har inte definierats.
- Beskrivning: om det här alternativet är definierat lägger detta till ett användardefinierat data fält i GX_WIDGET kontroll blocket. Det här data fältet kan tilldelas med egenskapsvyn i GUIX Studio. Det här data fältet ignoreras av GUIX internt, men kan användas av program program vara i många olika syfte.

GUIX_5_4_0_COMPATIBILITY
- Standard: har inte definierats.
- Beskrivning: vissa GUI-API: er ändrades efter versions 5.4.0 för att lägga till stöd för inaktiverade text färger och förbättra noggrannheten för vissa matematik funktioner med hjälp av matchnings parametrar med fast punkt. De här ändringarna gör GUIX biblioteks utgåvor när 5.4.0 inte är kompatibla med tidigare versioner. Men genom att aktivera den här #define kan biblioteket vara byggt så att API: erna är helt kompatibla med versioner <= 5.4.0, vilket innebär att inga ändringar behövs i befintliga program för att kompilera med den senaste biblioteks versionen av GUIX.

GX_MAX_STRING_LENGTH
- Standard: 102400
- Beskrivning: definierar den maximala längden för en sträng som används för att testa ogiltiga strängar. Om Indatasträngen överskrider den maximala sträng längden, betraktas den som ogiltig.