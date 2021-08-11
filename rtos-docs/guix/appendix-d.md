---
title: Bilaga D – GUIX-pensel, arbetsyteattribut och toningar
description: Lär dig mer om GUIX-pensel-, arbetsyte- och toningsattribut.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9fbc98f1094cab6be4bc0826fef7c0feb77b50b066b22342cd52404bd85ff98e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784639"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>Bilaga D – GUIX-pensel, arbetsyteattribut och toningar

__**Penselformat:**__

**GX_BRUSH_OUTLINE**
- Värde: 0x0000
- Beskrivning: Det här penselformatet gäller för formritningsfunktioner som gx_canvas_rectangle_draw eller gx_canvas_polygon_draw. Det här formatet anger att formen ska beskrivas, förutom att den eventuellt kan fyllas i. Om GX_BRUSH_OUTLINE har angetts och GX_BRSUH_SOLID_FILL rensas, så är formen bara konturerad.

**GX_BRUSH_SOLID_FILL**
- Värde: 0x0001
- Beskrivning: Det här penselformatet gäller för formritningsfunktioner och anger att den begärda formen ska fyllas med en solid färg med hjälp av den aktuella penselfyllningsfärgen.

**GX_BRUSH_PIXELMAP_FILL**
- Värde: 0x0002
- Beskrivning: Det här penselformatet gäller för formritningsfunktioner och anger att den begärda formen ska vara ett mönster fyllt med den aktuella penselpunktskartan.

**GX_BRUSH_ALIAS**
- Värde: 0x0004
- Beskrivning: Det här penselformatet gäller för alla linjeritningar och formkontur. Om den här flaggan anges ritas linjer och konturer med mer exakta men även mer tidskrävande antialiasbaserade ritningsalgoritmer. Den här stilflaggan används endast för 16 bpp-färgdjup och högre.

**GX_BRUSH_UNDERLINE**
- Värde: 0x0008
- Beskrivning: Den här flaggan gäller för textritning och anger att efterföljande text som ritas ska vara understruken.

**GX_BRUSH_ROUND**
- Värde: 0x0010
- Beskrivning: Den här flaggan gäller för linjeritning och anger att linjens ändar ritas med en runda eller cirkelformad form, i stället för den förvalda kvadratformen.

__**Flaggor för arbetsyta:**__

**GX_CANVAS_SIMPLE**
- Värde: 0x01
- Beskrivning: En minnesarbetsyta som används för att rita utanför skärmen.

**GX_CANVAS_MANAGED**
- Värde: 0x02
- Beskrivning: En arbetsyta som automatiskt rensas till den aktiva visningen, antingen som en del av den sammansatta byggprocessen eller som en del av buffertreglageåtgärden för en enda arbetsytearkitektur.

**GX_CANVAS_VISIBLE**
- Värde: 0x04
- Beskrivning: Den här flaggan kan användas för att aktivera och inaktivera en arbetsyta utan att förlora arbetsytans ritningsinnehåll.

**GX_CANVAS_MODIFIED**
- Värde: 0x08
- Beskrivning: Reserverad för framtida användning.

**GX_CANVAS_COMPOSITE**
- Värde: 0x20
- Beskrivning: Den här flaggan används av programmet när du konfigurerar ett system med flera arbetsyteenheter som ska sammansatta flera hanterade arbetsyta i den sammansatta arbetsytan och den sammansatta styrs av maskinvarurambufferten.

__**Toningstyper:**__

**GX_GRADIENT_TYPE_VERTICAL**
- Värde: 0x01
- Beskrivning: Skapar en lodrät alfakartetoning.

**GX_GRADIENT_TYPE_ALPHA**
- Värde: 0x02
- Beskrivning: Creats an alpha-map style gradient. Detta är för närvarande det enda toningsformat som stöds.

**GX_GRADIENT_TYPE_MIRROR**
- Värde: 0x04
- Beskrivning: Den här flaggan anger att toningen ska vara som högst i mitten av bredd-/höjdintervallet och återgå till startvärdet när den når den högra/nedre kanten. Utan den här stilflaggan blir toningen en linjär toning från uppifrån och ned eller från vänster till höger, beroende på GX_GRADIENT_TYPE_VERTICAL flagga.