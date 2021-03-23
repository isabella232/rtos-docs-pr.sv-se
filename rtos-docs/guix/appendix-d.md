---
title: Bilaga D – GUIX pensel, attribut för arbets yta och toning
description: Lär dig mer om GUIX-penseln, arbetsytans och Toningens attribut.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827276"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>Bilaga D – GUIX pensel, attribut för arbets yta och toning

__**Pensel format:**__

**GX_BRUSH_OUTLINE**
- Värde: 0x0000
- Beskrivning: det här pensel formatet gäller för form ritnings funktioner som gx_canvas_rectangle_draw eller gx_canvas_polygon_draw. Det här formatet visar att figuren ska vara definierad, förutom att du kan fylla. Om GX_BRUSH_OUTLINE-formatet har angetts och GX_BRSUH_SOLID_FILL är avmarkerat visas figuren bara.

**GX_BRUSH_SOLID_FILL**
- Värde: 0x0001
- Beskrivning: det här pensel formatet används för form ritnings funktioner och anger att den begärda formen ska fyllas med en solid färg med den aktuella pensel fyllnings färgen.

**GX_BRUSH_PIXELMAP_FILL**
- Värde: 0x0002
- Beskrivning: det här pensel formatet används för form ritnings funktioner och anger att den önskade formen ska vara ett mönster som är ifyllt med den aktuella penseln Pixelmap.

**GX_BRUSH_ALIAS**
- Värde: 0x0004
- Beskrivning: det här pensel formatet gäller för alla linje rit-och form konturer. Om den här flaggan är inställd, ritas linjer och kant linjer med mer exakt, men även mer tid på att använda algoritmer för kant utjämning. Den här format flaggan används bara för 16-BPP färgdjup och högre.

**GX_BRUSH_UNDERLINE**
- Värde: 0x0008
- Beskrivning: den här flaggan gäller för text ritning och anger att efterföljande text som ritas ska vara understruken.

**GX_BRUSH_ROUND**
- Värde: 0x0010
- Beskrivning: den här flaggan gäller för linje ritning och anger att linje änd punkter ritas med en runda eller cirkulär form, i stället för standardformen.

__**Flaggor för arbets ytor:**__

**GX_CANVAS_SIMPLE**
- Värde: 0x01
- Beskrivning: en minnes arbets yta som används för att rita på skärmen.

**GX_CANVAS_MANAGED**
- Värde: protokollnumret 0x02
- Beskrivning: en arbets yta som automatiskt töms på den aktiva visningen, antingen som en del av den sammansatta skapande processen eller som en del av växlings åtgärden för en enskild arbets yta.

**GX_CANVAS_VISIBLE**
- Värde: 0x04
- Beskrivning: den här flaggan kan användas för att aktivera och inaktivera en arbets yta utan att förlora ritnings innehållet i arbets ytan.

**GX_CANVAS_MODIFIED**
- Värde: 0x08
- Beskrivning: reserverad för framtida användning.

**GX_CANVAS_COMPOSITE**
- Värde: 0x20
- Beskrivning: den här flaggan används av programmet när du konfigurerar ett system med flera arbets ytor som sammansätter flera hanterade arbets ytor i den sammansatta arbets ytan och den sammansatta enheten är driven för maskin varu Rams bufferten.

__**Tonings typer:**__

**GX_GRADIENT_TYPE_VERTICAL**
- Värde: 0x01
- Beskrivning: skapar en lodrät AlphaMap-övertoning.

**GX_GRADIENT_TYPE_ALPHA**
- Värde: protokollnumret 0x02
- Beskrivning: utformerar en tonings toning i alpha-mappar. Detta är för närvarande det enda stödda tonings formatet.

**GX_GRADIENT_TYPE_MIRROR**
- Värde: 0x04
- Beskrivning: den här flaggan anger att toningen ska vara hög vid mitten av intervallet för bredd/höjd och återgå till startvärdet när den når höger/nedre kant. Utan den här format flaggan är övertoningen en linjär övertoning från översta till nedre eller från vänster till höger, beroende på GX_GRADIENT_TYPE_VERTICAL flagga.