---
title: Bilaga G – GUIX-teckensnittsstruktur
description: Lär dig mer om GUIX-teckensnittsstrukturen.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c7cedb49268f97f8e1fc4cd28329b0b61e697d57562865896f0502bdd1d45f1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784197"
---
# <a name="appendix-g---guix-font-structure"></a>Bilaga G – GUIX-teckensnittsstruktur

GUIX-teckensnitt produceras vanligtvis av GUIX Studio-programmet och teckenfraser renderas av GUIX-visningsdrivrutinen. Programprogramvaran behöver bara ange teckensnitt och färger som varje textvisningswidget ska använda. GUIX-teckensnittsdatastrukturer dokumenteras här för fullständighet och för att utvecklare ska kunna skapa egna metoder för att generera eller konvertera andra teckensnitt till GUIX-teckensnittsformatet.

Varje GUIX-teckensnitt börjar med en GX_FONT struktur. Den GX_FONT strukturen definierar globala teckensnittsparametrar, till exempel det tecken som ingår i teckensnittet och radhöjden för teckensnittet. De GX_FONT strukturpunkterna i en matris med GX_GLYPH strukturer. Varje GX_GLYPH struktur definierar bredd, höjd och baslinjeförskjutning för ett visst tecken glyph. Den GX_GLYPH strukturen pekar även på faktiska glyph-bitmappdata (som kan vara NULL för blankstegstecken).

Den GX_FONT strukturen, som finns i gx_api.h, deklareras på följande sätt:

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

Fältet gx_font_format definierar teckensnittet bits-per-pixel och andra flaggor, enligt definitionen i gx_api.h-huvudfilen.

Den gx_font_prespace definierar pixelutrymmet som ska hoppas över varje rad med text i en flerradstextvisning.

Fältet gx_font_postspace definierar pixelutrymmet som ska hoppas över under varje textrad i en flerradstextvisning.

Fältet gx_font_line_height definierar höjden på det högsta glyf:et i teckensnittet.

Fältet gx_font_baseline definierar avståndet, i bildpunkter, från den översta raden med glyph-bildpunkter till teckensnittsbaslinjen.

Fältet gx_font_first_glyph definierar den första Unicode-teckenkodningen som ingår på den här teckensnittssidan.

Fältet gx_font_last_glyph definierar den senaste Unicode-teckenkodningen som ingår på den här teckensnittssidan.

Pekaren gx_font_glyphs pekar på en matris med GX_GLYPH strukturer. Den här matrisen måste vara lika stor som antalet tecken på den här teckensidan, dvs. (gx_font_last_glyph – gx_font_first_glyph) + 1.

Den gx_font_next_page medlemmen används för flera sidtyper. Flera sidtyper används för utökade teckenuppsättningar och för att optimera storleken på GX_GLYPH strukturmatriser. Om alla tecken i teckensnittet finns på en teckensida, eller om det är den sista sidan i teckensnittet i fråga, är gx_font_next_page-medlemmen inställd på GX_NULL.

Som nämnts ovan innehåller GX_FONT ovan en pekare till en matris med GX_GLYPHS strukturer. Det måste finnas en GX_GLYPH struktur för varje tecken på teckensidan. Strukturen GX_GLYPH definieras som:

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

Pekaren gx_glyph_map pekar på glyph-bitmappen. Den här pekaren kan GX_NULL för blankstegstecken. Bitmappdata kodas som alfavärdena 1 bpp, 2 bpp, 4 bpp eller 8 bpp. För 1-bitars data indikerar värdet 1 att pixeln ska skrivas i förgrundsfärgen och värdet 0 anger att pixeln är transparent. För 8-bitars data sträcker sig värdena från 0 (helt transparent) till 255 (helt opague). Alla mellanliggande värden representerar ett blandningsvärde för antialiasade teckensnitt. Bit bitmappdata är alltid utplattade till fullständig bytejustering för format som använder mindre än 8bpp datavärden.

Värdena gx_glyph_ascent och gx_glyph_descent placera glyph lodrätt med avseende på teckensnittsbaslinjen.

Värdena gx_glyph_width och gx_glyph_height anger storleken på glyph-bitmappdata.

Värdet gx_glyph_advance pixelbredden för att flytta fram ritningspositionen efter att du har ritat glyph (detta kanske inte är lika med glyph-bredden).

Värdet gx_glyph_leading anger vilka bildpunkter som ska gå framåt i x-riktningen innan glyph återges.