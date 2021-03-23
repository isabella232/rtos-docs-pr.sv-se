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
# <a name="appendix-g---guix-font-structure"></a><span data-ttu-id="245b6-103">Bilaga G – GUIX teckensnitts struktur</span><span class="sxs-lookup"><span data-stu-id="245b6-103">Appendix G - GUIX Font Structure</span></span>

<span data-ttu-id="245b6-104">GUIX-teckensnitt skapas normalt av GUIX Studio-programmet och teckensnitts tecken återges av GUIX-bildskärms driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="245b6-104">GUIX fonts are normally produced by the GUIX Studio application, and font glyphs are rendered by the GUIX display driver.</span></span> <span data-ttu-id="245b6-105">Program varan behöver bara ange teckensnitt och färger som varje widget för text visning ska använda.</span><span class="sxs-lookup"><span data-stu-id="245b6-105">The application software need only specify the font and colors that each text display widget should use.</span></span> <span data-ttu-id="245b6-106">Data strukturerna för GUIX-teckensnitt dokumenteras här så att utvecklare kan skapa egna metoder för att skapa eller konvertera andra teckensnitt till teckensnitts formatet GUIX.</span><span class="sxs-lookup"><span data-stu-id="245b6-106">The GUIX font data structures are documented here for completeness, and to enable developers to create their own methods for generating or converting other fonts into the GUIX font format.</span></span>

<span data-ttu-id="245b6-107">Varje GUIX-teckensnitt börjar med en GX_FONT-struktur.</span><span class="sxs-lookup"><span data-stu-id="245b6-107">Each GUIX font starts with a GX_FONT structure.</span></span> <span data-ttu-id="245b6-108">GX_FONTs strukturen definierar globala teckensnitts parametrar, t. ex. det tecken som ingår i teckensnittet och rad höjden för teckensnittet.</span><span class="sxs-lookup"><span data-stu-id="245b6-108">The GX_FONT structure defines global font parameters, such as the character included within the font and the line height of the font.</span></span> <span data-ttu-id="245b6-109">GX_FONT strukturen pekar på en matris med GX_GLYPH strukturer.</span><span class="sxs-lookup"><span data-stu-id="245b6-109">The GX_FONT structure points at an array of GX_GLYPH structures.</span></span> <span data-ttu-id="245b6-110">Varje GX_GLYPH-struktur definierar bredd, höjd och bas linje förskjutning för ett särskilt Character-tecken.</span><span class="sxs-lookup"><span data-stu-id="245b6-110">Each GX_GLYPH structure defines the width, height, and baseline offset of one specific character glyph.</span></span> <span data-ttu-id="245b6-111">GX_GLYPHs strukturen pekar också på faktiska data för GLYPH-bitmappen (som kan vara NULL för blank steg).</span><span class="sxs-lookup"><span data-stu-id="245b6-111">The GX_GLYPH structure also points to the actual glyph bitmap data (which may be NULL for whitespace characters).</span></span>

<span data-ttu-id="245b6-112">GX_FONTs strukturen, som finns i gx_api. h, deklareras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="245b6-112">The GX_FONT structure, contained in gx_api.h, is declared as follows:</span></span>

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

<span data-ttu-id="245b6-113">I fältet gx_font_format definieras teckensnitts bitarna per pixel och andra flaggor, som definieras i huvud filen gx_api. h.</span><span class="sxs-lookup"><span data-stu-id="245b6-113">The gx_font_format field defines the font bits-per-pixel and other flags, as defined in the gx_api.h header file.</span></span>

<span data-ttu-id="245b6-114">Gx_font_prespace definierar pixel utrymmet som ska hoppas över varje textrad i en flerradig text visning.</span><span class="sxs-lookup"><span data-stu-id="245b6-114">The gx_font_prespace defines the pixel space to skip above each line of text in a multi-line text display.</span></span>

<span data-ttu-id="245b6-115">I fältet gx_font_postspace definieras pixel utrymmet som ska hoppas över under varje textrad i en flerradig text visning.</span><span class="sxs-lookup"><span data-stu-id="245b6-115">The gx_font_postspace field defines the pixel space to skip below each line of text in a multi-line text display.</span></span>

<span data-ttu-id="245b6-116">Fältet gx_font_line_height definierar höjden på det högsta specialtecknet i teckensnittet.</span><span class="sxs-lookup"><span data-stu-id="245b6-116">The gx_font_line_height field defines the height of the tallest glyph in the font.</span></span>

<span data-ttu-id="245b6-117">I fältet gx_font_baseline definieras avståndet, i bild punkter, från den översta raden med Glyph-pixlar till tecken bas linjen.</span><span class="sxs-lookup"><span data-stu-id="245b6-117">The gx_font_baseline field defines the distance, in pixels, from the top row of glyph pixels to the font baseline.</span></span>

<span data-ttu-id="245b6-118">Fältet gx_font_first_glyph definierar den första Unicode-teckenuppsättningen som ingår i den här teckensnitts sidan.</span><span class="sxs-lookup"><span data-stu-id="245b6-118">The gx_font_first_glyph field defines the first Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="245b6-119">Fältet gx_font_last_glyph definierar den sista Unicode-teckenuppsättningen som ingår på den här teckensnitts sidan.</span><span class="sxs-lookup"><span data-stu-id="245b6-119">The gx_font_last_glyph field defines the last Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="245b6-120">Gx_font_glyphss pekaren pekar på en matris med GX_GLYPH strukturer.</span><span class="sxs-lookup"><span data-stu-id="245b6-120">The gx_font_glyphs pointer points to an array of GX_GLYPH structures.</span></span> <span data-ttu-id="245b6-121">Matrisen måste ha samma storlek som antalet tecken som finns på den här teckensnitts sidan, dvs.</span><span class="sxs-lookup"><span data-stu-id="245b6-121">This array must be equal in size to the number of characters contained on this font page, i.e</span></span> <span data-ttu-id="245b6-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span><span class="sxs-lookup"><span data-stu-id="245b6-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span></span>

<span data-ttu-id="245b6-123">Gx_font_next_page medlem används för flera sid teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="245b6-123">The gx_font_next_page member is used for multiple page fonts.</span></span> <span data-ttu-id="245b6-124">Flera sid teckensnitt används för utökade teckenuppsättningar och för att optimera storleken på GX_GLYPH struktur mat ris.</span><span class="sxs-lookup"><span data-stu-id="245b6-124">Multiple page fonts are used for extended character sets and to optimize the size of the GX_GLYPH structure arrays.</span></span> <span data-ttu-id="245b6-125">Om alla tecken i teckensnittet finns på en teckensnitts sida eller om det är den sista sidan av teckensnittet i fråga, är gx_font_next_page medlem inställd på GX_NULL.</span><span class="sxs-lookup"><span data-stu-id="245b6-125">If all of the characters of the font are contained within one font page, or if this is the last page of the font in question, the gx_font_next_page member is set to GX_NULL.</span></span>

<span data-ttu-id="245b6-126">Som nämnts ovan innehåller GX_FONTs strukturen ovan en pekare till en matris med GX_GLYPHS strukturer.</span><span class="sxs-lookup"><span data-stu-id="245b6-126">As noted above, the GX_FONT structure above contains a pointer to an array of GX_GLYPHS structures.</span></span> <span data-ttu-id="245b6-127">Det måste finnas en GX_GLYPH-struktur för varje tecken på sidan teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="245b6-127">There must be one GX_GLYPH structure for each character on the font page.</span></span> <span data-ttu-id="245b6-128">GX_GLYPHs strukturen definieras som:</span><span class="sxs-lookup"><span data-stu-id="245b6-128">The GX_GLYPH structure is defined as:</span></span>

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

<span data-ttu-id="245b6-129">Gx_glyph_maps pekaren pekar på Glyph-bitmappen.</span><span class="sxs-lookup"><span data-stu-id="245b6-129">The gx_glyph_map pointer points to the glyph bitmap.</span></span> <span data-ttu-id="245b6-130">Den här pekaren kan vara GX_NULL för blank stegs tecken.</span><span class="sxs-lookup"><span data-stu-id="245b6-130">This pointer may be GX_NULL for whitespace characters.</span></span> <span data-ttu-id="245b6-131">Bitmappsdata kodas som 1 BPP, 2 BPP, 4 BPP eller 8 BPP alpha-värden.</span><span class="sxs-lookup"><span data-stu-id="245b6-131">The bitmap data is encoded as 1 bpp, 2 bpp, 4 bpp, or 8 bpp alpha values.</span></span> <span data-ttu-id="245b6-132">För 1-bitars data anger värdet 1 att pixeln ska skrivas i förgrunds färgen och värdet 0 anger att pixeln är transparent.</span><span class="sxs-lookup"><span data-stu-id="245b6-132">For 1 bit data, a value of 1 indicates that the pixel should be written in the foreground color, and a value of 0 indicates that the pixel is transparent.</span></span> <span data-ttu-id="245b6-133">För 8 bitars data sträcker sig värdena från 0 (helt transparent) till 255 (helt opague).</span><span class="sxs-lookup"><span data-stu-id="245b6-133">For 8 bit data, the values range from 0 (fully transparent) to 255 (fully opague).</span></span> <span data-ttu-id="245b6-134">Alla mellanliggande värde representerar ett blandnings värde för teckensnitt med Kantutjämna.</span><span class="sxs-lookup"><span data-stu-id="245b6-134">All intermediate value represent a blending value for anti-aliased fonts.</span></span> <span data-ttu-id="245b6-135">Glyphs bitmap-data fylls alltid i för full byte-justering för format som använder mindre än 8bpp data värden.</span><span class="sxs-lookup"><span data-stu-id="245b6-135">The glyph bitmap data is always padded to full byte alignment for formats using less than 8bpp data values.</span></span>

<span data-ttu-id="245b6-136">Värdena för gx_glyph_ascent och gx_glyph_descent placerar specialtecknet lodrätt i förhållande till teckensnittets bas linje.</span><span class="sxs-lookup"><span data-stu-id="245b6-136">The gx_glyph_ascent and gx_glyph_descent values position the glyph vertically with respect to the font baseline.</span></span>

<span data-ttu-id="245b6-137">Värdena för gx_glyph_width och gx_glyph_height anger storleken på data för Glyph-bitmappen.</span><span class="sxs-lookup"><span data-stu-id="245b6-137">The gx_glyph_width and gx_glyph_height values specify the size of the glyph bitmap data.</span></span>

<span data-ttu-id="245b6-138">Värdet gx_glyph_advance anger pixel bredden för att flytta rit positionen efter att du ritat specialtecknet (det får inte vara lika med tecken bredden).</span><span class="sxs-lookup"><span data-stu-id="245b6-138">The gx_glyph_advance value specifies the pixel width to advance the drawing position after drawing the glyph (this may not be equal to the glyph width).</span></span>

<span data-ttu-id="245b6-139">Värdet gx_glyph_leading anger de pixlar som ska förflyttas i x-riktning innan specialtecknet renderas.</span><span class="sxs-lookup"><span data-stu-id="245b6-139">The gx_glyph_leading value specifies the pixels to advance in the x-direction prior to rendering the glyph.</span></span>