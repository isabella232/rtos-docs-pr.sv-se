---
title: Bilaga G – GUIX teckensnitts struktur
description: Lär dig mer om teckensnitts strukturen i GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5f0232e6c21851014b85cfe7b07795062fd1e8d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827267"
---
# <a name="appendix-g---guix-font-structure"></a>Bilaga G – GUIX teckensnitts struktur

GUIX-teckensnitt skapas normalt av GUIX Studio-programmet och teckensnitts tecken återges av GUIX-bildskärms driv rutinen. Program varan behöver bara ange teckensnitt och färger som varje widget för text visning ska använda. Data strukturerna för GUIX-teckensnitt dokumenteras här så att utvecklare kan skapa egna metoder för att skapa eller konvertera andra teckensnitt till teckensnitts formatet GUIX.

Varje GUIX-teckensnitt börjar med en GX_FONT-struktur. GX_FONTs strukturen definierar globala teckensnitts parametrar, t. ex. det tecken som ingår i teckensnittet och rad höjden för teckensnittet. GX_FONT strukturen pekar på en matris med GX_GLYPH strukturer. Varje GX_GLYPH-struktur definierar bredd, höjd och bas linje förskjutning för ett särskilt Character-tecken. GX_GLYPHs strukturen pekar också på faktiska data för GLYPH-bitmappen (som kan vara NULL för blank steg).

GX_FONTs strukturen, som finns i gx_api. h, deklareras enligt följande:

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

I fältet gx_font_format definieras teckensnitts bitarna per pixel och andra flaggor, som definieras i huvud filen gx_api. h.

Gx_font_prespace definierar pixel utrymmet som ska hoppas över varje textrad i en flerradig text visning.

I fältet gx_font_postspace definieras pixel utrymmet som ska hoppas över under varje textrad i en flerradig text visning.

Fältet gx_font_line_height definierar höjden på det högsta specialtecknet i teckensnittet.

I fältet gx_font_baseline definieras avståndet, i bild punkter, från den översta raden med Glyph-pixlar till tecken bas linjen.

Fältet gx_font_first_glyph definierar den första Unicode-teckenuppsättningen som ingår i den här teckensnitts sidan.

Fältet gx_font_last_glyph definierar den sista Unicode-teckenuppsättningen som ingår på den här teckensnitts sidan.

Gx_font_glyphss pekaren pekar på en matris med GX_GLYPH strukturer. Matrisen måste ha samma storlek som antalet tecken som finns på den här teckensnitts sidan, dvs. (gx_font_last_glyph – gx_font_first_glyph) + 1.

Gx_font_next_page medlem används för flera sid teckensnitt. Flera sid teckensnitt används för utökade teckenuppsättningar och för att optimera storleken på GX_GLYPH struktur mat ris. Om alla tecken i teckensnittet finns på en teckensnitts sida eller om det är den sista sidan av teckensnittet i fråga, är gx_font_next_page medlem inställd på GX_NULL.

Som nämnts ovan innehåller GX_FONTs strukturen ovan en pekare till en matris med GX_GLYPHS strukturer. Det måste finnas en GX_GLYPH-struktur för varje tecken på sidan teckensnitt. GX_GLYPHs strukturen definieras som:

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

Gx_glyph_maps pekaren pekar på Glyph-bitmappen. Den här pekaren kan vara GX_NULL för blank stegs tecken. Bitmappsdata kodas som 1 BPP, 2 BPP, 4 BPP eller 8 BPP alpha-värden. För 1-bitars data anger värdet 1 att pixeln ska skrivas i förgrunds färgen och värdet 0 anger att pixeln är transparent. För 8 bitars data sträcker sig värdena från 0 (helt transparent) till 255 (helt opague). Alla mellanliggande värde representerar ett blandnings värde för teckensnitt med Kantutjämna. Glyphs bitmap-data fylls alltid i för full byte-justering för format som använder mindre än 8bpp data värden.

Värdena för gx_glyph_ascent och gx_glyph_descent placerar specialtecknet lodrätt i förhållande till teckensnittets bas linje.

Värdena för gx_glyph_width och gx_glyph_height anger storleken på data för Glyph-bitmappen.

Värdet gx_glyph_advance anger pixel bredden för att flytta rit positionen efter att du ritat specialtecknet (det får inte vara lika med tecken bredden).

Värdet gx_glyph_leading anger de pixlar som ska förflyttas i x-riktning innan specialtecknet renderas.