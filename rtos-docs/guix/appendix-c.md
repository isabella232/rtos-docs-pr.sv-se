---
title: Bilaga C – GUIX-widgetformat
description: Läs mer om GUIX-widgetformaten.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9519d68af64b777e34deb1bf11e6962e78a96b86bdbfd90f5b379c5b56c92268
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784656"
---
# <a name="appendix-c---guix-widget-styles"></a>Bilaga C – GUIX-widgetformat

__***Allmänna format (används med de flesta widgettyper):***__

**GX_STYLE_BORDER_NONE**
  - Värde: 0x00000000
  - Beskrivning: Använd det här formatet för att rita en widget utan kantlinje.

**GX_STYLE_BORDER_RAISED**
  - Värde: 0x00000001
  - Beskrivning: Rita widget med en upphöjd kantlinje.

**GX_STYLE_BORDER_RECESSED**
  - Värde: 0x00000002
  - Beskrivning: Rita widget med en försedd kantlinje.

**GX_STYLE_BORDER_THIN**
  - Värde: 0x00000004
  - Beskrivning: Rita en kantlinje med en pixelbredd.

**GX_STYLE_BORDER_THICK** 
  - Värde: 0x00000008
  - Beskrivning: Rita widget med en tjock kantlinje.

**GX_STYLE_BORDER_MASK**
  - Värde: 0x0000000f
  - Beskrivning: Maskera värdet som används för att endast testa formatfälten för widgetformatmedlemmen.

**GX_STYLE_TRANSPARENT**
  - Värde: 0x10000000
  - Beskrivning: Skapa en widget som är minst delvis transparent. Det här formatet bör användas när en widget inte ritar sig helt täckande, inklusive widgetar som ritar en halvtransparent pixelkarta som widgetens bakgrund. Den här stilflaggan informerar GUIX om att den överordnade widgeten måste ritas för att uppdatera widgetbakgrundsområdet.

**GX_STYLE_DRAW_SELECTED**
  - Värde: 0x20000000
  - Beskrivning: Ange att widgeten ska ritas med valda tillståndsfärger och teckensnitt. Olika widgettyper använder DRAW_SELECTED på olika sätt för att indikera att widgeten är markerad.

**GX_STYLE_ENABLED**
  - Värde: 0x40000000
  - Beskrivning: Markera widgeten som aktiverad, vilket gör att widgeten kan acceptera användarindatahändelser och generera utdatasignaler.
  
**GX_STYLE_DYNAMICALLY_ALLOCATED**
  - Värde: 0x80000000
  - Beskrivning: Anger att widgetens blockminne allokeras dynamiskt med hjälp av gx_system_memory_allocator-tjänsten när widgeten skapas, och kontrollblockminnet frigörs om widgeten förstörs.

**GX_STYLE_USE_LOCAL_ALPHA**
  - Värde: 0x01000000
  - Beskrivning: Instruerar GUIX-ritningsfunktionerna att använda det lokala widget-alfavärdet när widgeten ritas. Den här flaggan används vanligtvis av den interna GUIX-logiken för att implementera animeringar som tonar ut widgetar.


__***Format för textjustering (format som tillämpas på alla widgetar som ritar text):***__

**GX_STYLE_TEXT_LEFT**
  - Värde: 0x00001000
  - Beskrivning: Texten ritas vänsterjusterad i widgetklientområdet.

**GX_STYLE_TEXT_RIGHT** 
  - Värde: 0x00002000
  - Beskrivning: Texten ritas högerjusterad i widgetklientområdet.

**GX_STYLE_TEXT_CENTER**
  - Värde: 0x00004000
  - Beskrivning: Texten ritas i mitten i widgetklientområdet.

**GX_STYLE_TEXT_COPY**
  - Värde: 0x00008000
  - Beskrivning: Som standard håller widgetar som ritar text bara en pekare till den text som skickas av programmet. För statiskt definierad text som definieras i strängtabellen finns det ingen anledning för widgeten att göra en privat kopia av den tilldelade texten. Men om texten som tilldelats en widget skapas dynamiskt med funktioner som sprint() eller gx_utility_ltoa är det ofta praktiskt att be widgeten att behålla sin egen privata kopia av all tilldelad text. Detta gör att programmet kan använda automatiska eller tillfälliga variabler när du definierar textsträngen, när programmet annars skulle behöva definiera statiskt definierade teckenmatriser för varje textwidget som använder dynamiskt definierad text. När den här stilflaggan har angetts använder widgeten gx_system_memory_allocator för att dynamiskt allokera det minnesblock som behövs för att innehålla en privat kopia av den tilldelade strängen. Därför används den här stilflaggan i programmet som definierar memory_allocator och memory_deallocator funktioner. GX_STYLE_TEXT_COPY bör inte rensas när den har angetts, och det kommer att orsaka oförutsägbara resultat.

__***Knappformat (gäller endast guix-knappwidgettyper):***__

**GX_STYLE_BUTTON_PUSHED**
  - Värde 0x00000010
  - Beskrivning: Anger att knappen är i push-läge eller valt tillstånd.

**GX_STYLE_BUTTON_TOGGLE**
  - Värde 0x00000020
  - Beskrivning: Knappen växlar status mellan push- och push-push-händelse vid varje klickhändelse. Det här formatet används ofta med "kryssrutor"-formatknappar.

**GX_STYLE_BUTTON_RADIO**
  - Värde 0x00000040
  - Beskrivning: Det här formatet anger att knappen kommer att vara exklusiv och avmarkera alla knappsyssling när den är markerad. Det här formatet används ofta med formatknapparna "alternativknapp".

**GX_STYLE_BUTTON_EVENT_ON_PUSH**
  - Värde: 0x00000080
  - Beskrivning: Anger att knappen genererar en klickhändelse när den först pushas. Standardåtgärden är att generera en klickhändelse när knappen släpps.

**GX_STYLE_BUTTON_REPEAT**
  - Värde 0x00000100
  - Beskrivning: Anger att knappen ska skicka upprepade klickhändelser till den överordnade knappen när knappen hålls i push-läge.

__***Listformat (gäller endast widgettyper för GUIX-lista):***__

**GX_STYLE_CENTER_SELECTED** 
  - Värde: 0x00000010
  - Beskrivning: Reserverad

**GX_STYLE_WRAP**
  - Värde 0x00000020
  - Beskrivning: Listans underordnade radbrytningar från början till slut när listan dras eller rullas förbi indexet för start- eller slutlistan.

**GX_STYLE_FLICKABLE**
  - Värde: 0x00000040
  - Beskrivning: Reserverad

__***Bildpunktsknapp och ikonknappformat:***__

**GX_STYLE_HALIGN_CENTER**
  - Värde: 0x00010000
  - Beskrivning: Knappens pixelkarta ska centreras inom knappgränsen på den vågräta axeln.

**GX_STYLE_HALIGN_LEFT**
  - Värde: 0x00020000
  - Beskrivning: Knappens pixelkarta ska vara vänsterjusterad inom knappgränsen på den vågräta axeln.

**GX_STYLE_HALIGN_RIGHT**
  - Värde 0x00040000
  - Beskrivning: Knappens pixelkarta ska vara högerjusterad inom knappgränsen på den vågräta axeln.

**GX_STYLE_VALIGN_CENTER**
  - Värde 0x00080000
  - Beskrivning: Knappens pixelkarta ska centreras inom knappgränsen på den lodräta axeln.

**GX_STYLE_VALIGN_TOP**
  - Värde: 0x00100000
  - Beskrivning: Knappens pixelkarta ska vara överst justerad inom knappgränsen på den lodräta axeln.

**GX_STYLE_VALIGN_BOTTOM**
  - Värde: 0x00200000
  - Beskrivning: Knappens pixelkarta ska vara nederkant inom knappgränsen på den lodräta vågräta axeln.

__***Skjutreglageformat (endast app för att GX_SLIDER härledda widgettyper):***__

**GX_STYLE_SHOW_NEEDLE**
  - Värde: 0x00000200
  - Beskrivning: Det här formatet måste inkluderas för att skjutreglaget ska rita nålindikatorn. Det här formatet kan inaktiveras om programmet vill inaktivera skjutreglaget eller rita en anpassad nålindikator.

**GX_STYLE_SHOW_TICKMARKS**
  - Värde: 0x00000400
  - Beskrivning: Skjutreglagewidgeten gör programvaruritning av streckade bockmarkeringslinjer när det här formatet är aktiverat.

**GX_STYLE_SLIDER_VERTICAL**
  - Värde 0x00000800
  - Beskrivning: Ange den här stilflaggan för att skapa ett lodrätt skjutreglage och avmarkera den här stilflaggan för att skapa ett vågrätt skjutreglage.

__***Alternativete Styles (gäller endast för GX_SPRITE widgettyper):***__

**GX_STYLE_SPRITE_AUTO**
  - Värde: 0x00000010
  - Beskrivning: Anger att animeringen kommer att köras automatiskt när widgeten har tagit emot GX_EVENT_SHOW händelsen.

**GX_STYLE_SPRITE_LOOP**
  - Värde: 0x00000020
  - Beskrivning: Med det här formatet kommer widgeten att kontinuerligt loopa genom grafiska animeringsramar tills programmet har stoppat programmet.

__***Skjutreglageformat för pixelkarta:***__

**GX_STYLE_TILE_BACKGROUND**
  - Värde 0x00001000
  - Beskrivning: Bakgrundsbilden för skjutreglaget är panelerad för att fylla rektangeln för reglaget. Detta gör att en liten lodrät eller vågrät strimlistbild kan användas för att fylla skjutreglagets bakgrund.

__***Ytterligare format för förloppsfält:***__

**GX_STYLE_PROGRESS_PERCENT**
  - Värde: 0x00000010
  - Beskrivning: När det här formatet anges ritar förloppsfältet stapelvärdet som en procentandel i stället för ett råvärde. Texten centreras i förloppsfältets avgränsande rektangel.

**GX_STYLE_PROGRESS_TEXT_DRAW**
  - Värde: 0x00000020
  - Beskrivning: Rita det aktuella förloppsstapelvärdet som decimaltext centrerat i förloppsfältet.

**GX_STYLE_PROGRESS_VERTICAL**
  - Värde: 0x0000040
  - Beskrivning: Ange att förloppet är lodrätt orienterat. Standardinställningen är vågrät orientering.

**GX_STYLE_PROGRESS_SEGMENT_FILL**:
  - **Värde:** 0x00000100
  - Beskrivning: Förloppsfältets värde anges med segmenterade fyllda rektanglar i stället för en heldragen fyllning.

__***Ytterligare format för radiell förloppsstapel:***__

**GX_STYLE_RADIAL_PROGRESS_ALIAS**
  - Värde: 0x00000200
  - Beskrivning: Rita den radiella förloppsstapeln med antialiasade penselformat. Detta kräver mer processorbandbredd men ger också ett bättre utseende. För cpu-mål med lägre prestanda kan du rensa den här stilflaggan, vilket ger snabbare ritningshastighet.

**GX_STYLE_RADIAL_PROGRESS_ROUND**
  - Värde: 0x00000400
  - Beskrivning: Använd en penselformat med runda linjer när du ritar den radiella förloppsstapelns båge. Standardvärdet är en kvadratisk linjeslut.

__***Ytterligare format för textinmatning:***__

**GX_STYLE_ CURSOR_BLINK**
  - Värde: 0x00000040
  - Beskrivning: Markören för textinmatningswidgeten blinkar på och av i stället för att vara konstant.

**GX_STYLE_ CURSOR_ALWAYS**
  - Värde: 0x00000080
  - Beskrivning. Widgetmarkören för textinmatning visas normalt bara när widgeten äger indatafokus. Den här stilflaggan gör att markören alltid visas oavsett indatafokus.

**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**
  - Värde: 0x00000100
  - Beskrivning: Med den här stilflaggan anger du GX_EVENT_TEXT_EDITED händelse varje gång tangenten ned-händelsen tas emot av textinmatningswidgeten.

__***Ytterligare fönsterformat:***__

**GX_STYLE_TILE_WALLPAPER**
  - Värde: 0x00040000
  - Beskrivning: Fönstret visar alla tilldelade bakgrundsbilder som fyller fönstrets klientrektangel.

**GX_STYLE_AUTO_HSCROLL**
  - Värde: 0x00100000
  - Beskrivning: Reserverad för framtida användning.

**GX_STYLE_AUTO_VSCROLL**
  - Värde: 0x00200000
  - Beskrivning: Reserverad för framtida användning.

__***Ytterligare menyformat:***__

**GX_STYLE_MENU_EXPANDED**
  - Värde: 0x00000010
  - Beskrivning: Widgeten för avtalsmenyn är först i expanderat tillstånd.

__***Ytterligare trädvyformat:***__

**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**
  - Värde: 0x00000010
  - Beskrivning: Trädvywidgeten bör rita linjer från nodikonen till rotträdsnoden.

__***Ytterligare format för rullningslist:***__

**GX_SCROLLBAR_BACKGROUND_TILE**
  - Värde: 0x00010000
  - Beskrivning: Reserverad för framtida användning.

**GX_SCROLLBAR_RELATIVE_THUMB**
  - Värde: 0x00020000
  - Beskrivning: Rullningslistens tumbredd (för en vågrät rullningslist) eller höjd (för en lodrät rullningslist) beräknas baserat på förhållandet mellan det synliga området i det överordnade fönstret och det minsta och högsta rullningslistintervallet.

**GX_SCROLLBAR_END_BUTTONS**
  - Värde: 0x00040000
  - Beskrivning: Rullningslisten skapar och bifogar automatiskt knappar i varje ände av rullningslistens region.

**GX_SCROLLBAR_VERTICAL** 
  - Värde: 0x01000000
  - Beskrivning: Rullningslisten är lodrätt orienterad.

**GX_SCROLLBAR_HORIZONTAL**
  - Värde: 0x02000000
  - Beskrivning: Rullningslisten är vågrätt orienterad.

__***Format för textrullningshjul:***__

**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**
  - Värde: 0x00000200
  - Beskrivning: Rullningshjulet använder en Sinus-algoritm för att göra så att rullningshjulet ser ut att ha en avrundad form. Den här stilflaggan kan ge betydande omkostnader för rullningshjulswidgetens prestanda, men kan också ge hjulet ett 3D-realistiskt utseende.