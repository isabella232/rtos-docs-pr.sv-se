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
# <a name="appendix-c---guix-widget-styles"></a>Bilaga C – GUIX widgets format

__***Allmänna format (används med de flesta typer av widgetar):***__

**GX_STYLE_BORDER_NONE**
  - Värde: 0x00000000
  - Beskrivning: Använd det här formatet för att rita en widget utan kant linje.

**GX_STYLE_BORDER_RAISED**
  - Värde: 0x00000001
  - Beskrivning: Rita widget med en upphöjd kant linje.

**GX_STYLE_BORDER_RECESSED**
  - Värde: 0x00000002
  - Beskrivning: Rita widget med en försänkt kant linje.

**GX_STYLE_BORDER_THIN**
  - Värde: 0x00000004
  - Beskrivning: Rita en kant linje med en bild punkts bredd.

**GX_STYLE_BORDER_THICK** 
  - Värde: 0x00000008
  - Beskrivning: Rita widget med en tjock kant linje.

**GX_STYLE_BORDER_MASK**
  - Värde: 0x0000000f
  - Beskrivning: mask värde som används för att bara testa format fälten i widgeten format medlem.

**GX_STYLE_TRANSPARENT**
  - Värde: 0x10000000
  - Beskrivning: skapa en widget som är minst delvis transparent. Det här formatet bör användas när en widget inte ritar helt ogenomskinlig, inklusive widgetar som ritar en halv genomskinlig Pixelmap som widgetens bakgrund. Den här format flaggan informerar GUIX om att widgetens överordnade widget måste ritas för att uppdatera widgetens bakgrunds områden.

**GX_STYLE_DRAW_SELECTED**
  - Värde: 0x20000000
  - Beskrivning: ange att widgeten ska ritas med valda tillstånds färger och teckensnitt. Olika typer av widgetar använder DRAW_SELECTED format på olika sätt för att indikera att widgeten är markerad.

**GX_STYLE_ENABLED**
  - Värde: 0x40000000
  - Beskrivning: markera widgeten som aktive rad, vilket gör att widgeten kan ta emot indata från användaren och generera utmatnings signaler.
  
**GX_STYLE_DYNAMICALLY_ALLOCATED**
  - Värde: 0x80000000
  - Beskrivning: anger att widgeten kontroll block minne tilldelas dynamiskt med hjälp av gx_system_memory_allocator tjänsten när widgeten skapas och kontroll Blocks minnet frigörs om widgeten förstörs.

**GX_STYLE_USE_LOCAL_ALPHA**
  - Värde: 0x01000000
  - Beskrivning: instruerar GUIX Drawing Functions att använda det lokala widgeten alpha-värde när widgeten ritas. Den här flaggan används vanligt vis av den interna GUIX-logiken för att implementera tonings-animeringar.


__***Format för text justering (format som används för alla widgetar som ritar text):***__

**GX_STYLE_TEXT_LEFT**
  - Värde: 0x00001000
  - Beskrivning: texten ritas vänsterjusterat i ett-widgets klient fält.

**GX_STYLE_TEXT_RIGHT** 
  - Värde: 0x00002000
  - Beskrivning: texten ritas högerjusterat i det aktiva widgets-fältet.

**GX_STYLE_TEXT_CENTER**
  - Värde: 0x00004000
  - Beskrivning: texten ritas centrerad i widgetens klient del.

**GX_STYLE_TEXT_COPY**
  - Värde: 0x00008000
  - Beskrivning: som standard behåller widgeten som ritar text bara en pekare till den text som skickas av programmet. För statiskt definierad text som definieras i sträng tabellen finns det ingen anledning till att widgeten gör en privat kopia av den tilldelade texten. Men om texten som är kopplad till en widget skapas dynamiskt med funktioner som Sprint () eller gx_utility_ltoa, är det ofta praktiskt att berätta för widgeten att det ska vara en egen privat kopia av en tilldelad text. Detta gör att programmet kan använda automatiska eller tillfälliga variabler när du definierar text strängen, när programmet annars skulle behövas för att definiera statiskt definierade tecken mat ris för varje text-widget som använder dynamiskt definierad text. När den här format flaggan har angetts använder widgeten gx_system_memory_allocator funktionen för att dynamiskt allokera det minnes block som krävs för att lagra en privat kopia av den tilldelade strängen. Därför är det predikat att använda den här format flaggan i programmet som definierar memory_allocator och memory_deallocator funktioner. GX_STYLE_TEXT_COPY ska inte rensas när den har angetts och om du gör det kan det orsaka oförutsägbara resultat.

__***Knapp format (gäller endast för widgeten GUIX knapp):***__

**GX_STYLE_BUTTON_PUSHED**
  - Värde 0x00000010
  - Beskrivning: anger att knappen är i läget pushd eller markerad.

**GX_STYLE_BUTTON_TOGGLE**
  - Värde 0x00000020
  - Beskrivning: knappen växlar status mellan pushd och pushd vid varje klickning-händelse. Det här formatet används ofta med knapparna "kryss ruta".

**GX_STYLE_BUTTON_RADIO**
  - Värde 0x00000040
  - Beskrivning: det här formatet anger att knappen är exkluderad och avmarkerar alla knappar på samma nivå när de är markerade. Det här formatet används ofta med format knapparna "alternativ knapp".

**GX_STYLE_BUTTON_EVENT_ON_PUSH**
  - Värde: 0x00000080
  - Beskrivning: anger att knappen genererar en klick händelse när den skickas från början. Standard åtgärden är att generera en klicknings händelse när knappen släpps.

**GX_STYLE_BUTTON_REPEAT**
  - Värde 0x00000100
  - Beskrivning: anger att knappen ska skicka upprepade klicknings händelser till knappen överordnad när knappen hålls i läget PUSHD.

__***List format (gäller endast för GUIX List widgetar typer):***__

**GX_STYLE_CENTER_SELECTED** 
  - Värde: 0x00000010
  - Beskrivning: reserverad

**GX_STYLE_WRAP**
  - Värde 0x00000020
  - Beskrivning: listan underordnade visas från början till slut när listan dras eller rullas förbi början eller slutet av list indexet.

**GX_STYLE_FLICKABLE**
  - Värde: 0x00000040
  - Beskrivning: reserverad

__***Pixelmap-knapp och knapp format för ikon:***__

**GX_STYLE_HALIGN_CENTER**
  - Värde: 0x00010000
  - Beskrivning: knappens Pixelmap ska centreras i den vågräta axelns knapp gränser.

**GX_STYLE_HALIGN_LEFT**
  - Värde: 0x00020000
  - Beskrivning: knappens Pixelmap ska vara vänsterjusterad inom den vågräta axelns knapp gränser.

**GX_STYLE_HALIGN_RIGHT**
  - Värde 0x00040000
  - Beskrivning: knappens Pixelmap ska vara högerjusterad inom den vågräta axelns knapp gränser.

**GX_STYLE_VALIGN_CENTER**
  - Värde 0x00080000
  - Beskrivning: knappens Pixelmap ska vara centrerad inom knapp kanten på den lodräta axeln.

**GX_STYLE_VALIGN_TOP**
  - Värde: 0x00100000
  - Beskrivning: knappens Pixelmap ska justeras mot överkant i den lodräta axelns knapp gränser.

**GX_STYLE_VALIGN_BOTTOM**
  - Värde: 0x00200000
  - Beskrivning: knappens Pixelmap ska ligga längst ned i knapp kanten på den lodräta vågräta axeln.

__***Skjutreglage (endast appy till GX_SLIDER och härledda typer av widgetar):***__

**GX_STYLE_SHOW_NEEDLE**
  - Värde: 0x00000200
  - Beskrivning: det här formatet måste ingå i skjutreglaget för att rita en nål. Det här formatet kan inaktive ras om programmet vill inaktivera skjutreglaget eller rita en anpassad nål.

**GX_STYLE_SHOW_TICKMARKS**
  - Värde: 0x00000400
  - Beskrivning: widgeten skjutreglage kommer att göra program ritning av streckade skal streck linjer när det här formatet är aktiverat.

**GX_STYLE_SLIDER_VERTICAL**
  - Värde 0x00000800
  - Beskrivning: Ange den här format flaggan för att skapa ett lodrätt skjutreglage och ta bort den här format flaggan om du vill skapa ett vågrätt skjutreglage.

__***Sprite-format (gäller endast för GX_SPRITE widgetar typer):***__

**GX_STYLE_SPRITE_AUTO**
  - Värde: 0x00000010
  - Beskrivning: anger att Sprite-animeringen ska köras automatiskt när widgeten Sprite mottagit GX_EVENT_SHOW-händelsen.

**GX_STYLE_SPRITE_LOOP**
  - Värde: 0x00000020
  - Beskrivning: med det här formatet kommer widgeten Sprite att upprepas genom Sprite-animeringsbildrutor tills spriten stoppas av programmet.

__***Pixelmap för skjutreglage:***__

**GX_STYLE_TILE_BACKGROUND**
  - Värde 0x00001000
  - Beskrivning: skjutreglagets bakgrunds bild visas sida vid sida för att fylla den sprite-rektangeln. Detta gör att en liten lodrät eller vågrät rand bild kan användas för att fylla skjutreglagets bakgrund.

__***Ytterligare förlopps indikator format:***__

**GX_STYLE_PROGRESS_PERCENT**
  - Värde: 0x00000010
  - Beskrivning: när det här formatet anges ritas stapelns värde som en procent andel i stället för ett oformaterat värde. Texten centreras i den förlopps indikatorns rektangel.

**GX_STYLE_PROGRESS_TEXT_DRAW**
  - Värde: 0x00000020
  - Beskrivning: Rita aktuellt förlopps indikator värde som decimal text centrerad i förlopps indikatorn.

**GX_STYLE_PROGRESS_VERTICAL**
  - Värde: 0x0000040
  - Beskrivning: anger att förloppet är lodrätt orienterad. Standardvärdet är vågrät orientering.

**GX_STYLE_PROGRESS_SEGMENT_FILL**:
  - **Värde**: 0x00000100
  - Beskrivning: förlopps indikatorns värde anges med segmenterade fyllda rektanglar i stället för en solid fyllning.

__***Fler format för radiell förlopps indikator:***__

**GX_STYLE_RADIAL_PROGRESS_ALIAS**
  - Värde: 0x00000200
  - Beskrivning: Rita den radiella förlopps indikatorn med hjälp av färgmarkerade pensel format. Detta kräver mer processor bandbredd men ger också ett nicer utseende. Om du tar bort den här typen av processor mål ger det snabbare ritnings hastighet.

**GX_STYLE_RADIAL_PROGRESS_ROUND**
  - Värde: 0x00000400
  - Beskrivning: Använd en rundad linje slut pensel stil när du ritar den radiella förlopps indikatorns båge. Standardvärdet är en fyrkantig linje slutar.

__***Ytterligare text ingångs format:***__

**GX_STYLE_ CURSOR_BLINK**
  - Värde: 0x00000040
  - Beskrivning: markören för text inmatade widgeten blinkar i stället för att vara konstant.

**GX_STYLE_ CURSOR_ALWAYS**
  - Värde: 0x00000080
  - Beskrivning. Markören för text inmatade widget visas vanligt vis bara när widgeten äger indatamängds fokus. Den här format flaggan gör att markören alltid är synlig oavsett infokus.

**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**
  - Värde: 0x00000100
  - Beskrivning: med den här format flaggan anger händelsen GX_EVENT_TEXT_EDITED händelse varje gång en nyckel händelsen tas emot av widgeten för text inflöde.

__***Ytterligare fönster format:***__

**GX_STYLE_TILE_WALLPAPER**
  - Värde: 0x00040000
  - Beskrivning: fönstret visas med en tilldelad bakgrunds bild för att fylla fönstrets klient-rektangel.

**GX_STYLE_AUTO_HSCROLL**
  - Värde: 0x00100000
  - Beskrivning: reserverad för framtida användning.

**GX_STYLE_AUTO_VSCROLL**
  - Värde: 0x00200000
  - Beskrivning: reserverad för framtida användning.

__***Ytterligare meny format:***__

**GX_STYLE_MENU_EXPANDED**
  - Värde: 0x00000010
  - Beskrivning: widgeten för dragspelswidget är inlednings vis i expanderat läge.

__***Ytterligare träd format:***__

**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**
  - Värde: 0x00000010
  - Beskrivning: trädvyn i trädvyn ska rita rader från Node-ikonen till rotnoden.

__***Ytterligare rullnings List format:***__

**GX_SCROLLBAR_BACKGROUND_TILE**
  - Värde: 0x00010000
  - Beskrivning: reserverad för framtida användning.

**GX_SCROLLBAR_RELATIVE_THUMB**
  - Värde: 0x00020000
  - Beskrivning: rullnings listens bredd (för en vågrät rullnings List) eller höjd (för en lodrät rullnings List) beräknas baserat på förhållandet för det synliga området i det överordnade fönstret till det minsta och högsta rullnings intervallet.

**GX_SCROLLBAR_END_BUTTONS**
  - Värde: 0x00040000
  - Beskrivning: rullnings listen skapar och lägger automatiskt till knappar i slutet av området rullnings List.

**GX_SCROLLBAR_VERTICAL** 
  - Värde: 0x01000000
  - Beskrivning: rullnings listen är lodrätt orienterad.

**GX_SCROLLBAR_HORIZONTAL**
  - Värde: 0x02000000
  - Beskrivning: rullnings listen är vågrätt orienterad.

__***Hjul format för text rullning:***__

**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**
  - Värde: 0x00000200
  - Beskrivning: rullnings hjulet använder en Sinusoidal-algoritm som gör att rullnings hjulet visas med en rundad form. Den här format flaggan kan förbättra prestandan för widgeten rullnings hjul, men det kan också ge hjulet ett 3D realistiskt utseende.