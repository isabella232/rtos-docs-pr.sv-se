---
title: Användarhandbok för Azure RTOS GUIX
description: Den här guiden innehåller omfattande information Azure RTOS GUIX, den högpresterande GUI-produkten från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: e7cc1f44648111a75cd6b28d6b98480b721af9c8521e8fcb8cdac6f24c5514e7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784707"
---
# <a name="about-guix-user-guide"></a>Om GUIX-användarhandbok

Den här guiden innehåller omfattande information Azure RTOS GUIX, den högpresterande GUI-produkten från Microsoft. Den är avsedd för inbäddade realtidsutvecklare som är bekanta med grundläggande GUI-begrepp, Azure RTOS ThreadX och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1 – Introduktion till Azure RTOS GUIX](chapter-1.md)

[Kapitel 2 – Installation och användning av Azure RTOS GUIX](chapter-2.md)

[Kapitel 3 – Funktionell översikt över Azure RTOS GUIX](chapter-3.md)

[Kapitel 4 – Beskrivning av Azure RTOS GUIX-tjänster](chapter-4.md)

[Kapitel 5 – Azure RTOS GUIX-visningsdrivrutiner](chapter-5.md)  

[Azure RTOS GUIX-exempel](guix-example.md)

[Bilaga A – Azure RTOS GUIX-färgdefinitioner](appendix-a.md)

[Bilaga B – Azure RTOS GUIX-färgformat](appendix-b.md)

[Bilaga C – Azure RTOS GUIX-widgetformat](appendix-c.md)

[Bilaga D – Azure RTOS GUIX-pensel, arbetsyteattribut och toningar](appendix-d.md)

[Bilaga E – Azure RTOS GUIX-händelsebeskrivning](appendix-e.md)

[Bilaga F – Azure RTOS GUIX RTOS-bindningstjänster](appendix-f.md)

[Bilaga G – Azure RTOS GUIX-teckenstruktur](appendix-g.md)

[Bilaga H – Azure RTOS GUIX Build-Time Configuration-flaggor](appendix-h.md)

[Bilaga I – Azure RTOS GUIX-informationsstrukturer](appendix-i.md)

## <a name="guide-conventions"></a>Guidekonventioner

*Italics* – Typeface anger boktitlar, betonar viktiga ord och anger variabler.

**Boldface** – Typeface anger filnamn, nyckelord och betonar viktiga ord och variabler ytterligare.

> [!IMPORTANT]
> Informationssymboler uppmärksammar viktig eller ytterligare information som kan påverka prestanda eller funktion.

## <a name="azure-rtos-guix-data-types"></a>Azure RTOS GUIX-datatyper

Förutom de anpassade GUIX Azure RTOS-kontrollstrukturdatatyperna finns det flera särskilda datatyper som används i anropsgränssnitten Azure RTOS GUIX-tjänsten. Dessa särskilda datatyper mappar direkt till datatyper för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från ThreadX och finns i ***filen tx_port.h*** som ingår i ThreadX-distributionen.

Följande är en lista över de Azure RTOS GUIX-tjänstens anropsdatatyper och deras associerade betydelser:

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Uint**             | Grundläggande osignerat heltal. Den här typen mappas till den mest praktiska osignerade datatypen.                                |
| **INT**              | Grundläggande signerat heltal. Den här typen mappas till den mest praktiska signerade datatypen.                                    |
| **ULONG**            | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.                                                      |
| **Void**             | Nästan alltid likvärdigt med kompilatorns void-typ.                                                                 |
| **GX_CHAR**         | Skriv oftastdefed som den kompilatordefinierade teckentypen.                                                               |
| **GX_BYTE**          | 8-bitars signerad typ.                                                                                                    |
| **GX_UBYTE**         | 8-bitars osignerad typ.                                                                                                  |
| **GX_VALUE**        | 16- eller 32-bitars signerad typ. Definieras efter behov för bästa prestanda i målsystemet.                                |
| **GX_FIXED_VAL**   | Numerisk datatyp med fast punkt.                                                                                        |
| **GX_RESOURCE_ID** | Osignerad lång typ.                                                                                                   |
| **GX_COLOR**        | Osignerad lång typ.                                                                                                   |
| **GX_STRING**       | Struktur som GX_CHAR \* gx_string_ptr UINT-gx_string_length.                                          |
| **GX_POINT**        | Struktur som innehåller gx_point_x och gx_point_y.                                                                   |
| **GX_RECTANGLE**    | Struktur som gx_rectangle_left, gx_rectangle_top, gx_rectangle_right och gx_rectangle_bottom fält. |
| **GX_GLYPH**        | Struktur som innehåller glyph-mått.                                                                                   |
| **GX_FONT**         | Struktur som innehåller teckensnittsmått.                                                                                    |
| **GX_BRUSH**        | Struktur som innehåller penselmått.                                                                               |
**GX_PIXELMAP**       | Struktur som innehåller pixelkarta-mått.

Ytterligare datatyper används i den Azure RTOS GUIX-källan. De finns antingen i filerna ***tx_port.h** _ eller _ *_gx_port.h_** .

## <a name="customer-support-center"></a>Kundsupport

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och huruvida det kan återskapas på ett tillförlitligt sätt.

2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS GUIX som föregick problemet.

3. Innehållet i _tx_version_id och gx_version_id i _filerna ***tx_port.h**_ och _ *_gx_port.h_** för distributionen. Dessa strängar ger oss värdefull information om din körningsmiljö.

4. Innehållet i RAM-minnet för följande ULONG-variabler:

    **_tx_build_options** **_gx_system_build_options**

    De här variablerna ger oss information om hur Azure RTOS ThreadX och Azure RTOS GUIX-biblioteken har skapats.

5. Innehållet i RAM-minnet för följande ULONG-variabler:

    **_gx_system_last_error** **_gx_system_error_count**

    Dessa variabler håller reda på interna systemfel i Azure RTOS GUIX. Om _gx_system_error_count är större än en anger du en brytpunkt för funktionen som returneras i _gx_system_error_process-funktionen och anger värdet för _gx_system_last_error nu. Detta ger den första interna Azure RTOS GUIX-systemfel.

6. En spårningsbuffert avbildas omedelbart efter att problemet har identifierats. Detta åstadkoms genom att skapa Azure RTOS ThreadX- och Azure RTOS GUIX-bibliotek med TX_ENABLE_EVENT_TRACE och anropa tx_trace_enable med spårningsbuffertinformationen.

7. Det Azure RTOS GUIX Studio-projekt som du använder, om tillämpligt, eller åtminstone ett litet projekt som är tillräckligt för att demonstrera vilken brist du rapporterar.
