---
title: Användarhandbok för Azure RTOS GUIX
description: Den här guiden innehåller omfattande information om Azure återställnings tider GUIX, den högpresterande GUI-produkten från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827291"
---
# <a name="about-guix-user-guide"></a>Om Användar handbok för GUIX

Den här guiden innehåller omfattande information om Azure återställnings tider GUIX, den högpresterande GUI-produkten från Microsoft. Den är avsedd för inbäddade program varu utvecklare i real tid som är bekanta med grundläggande GUI-koncept, Azure återställnings tider-ThreadX och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1 – Introduktion till Azure återställnings tider GUIX](chapter-1.md)

[Kapitel 2 – installation och användning av Azure återställnings tider GUIX](chapter-2.md)

[Kapitel 3 – funktionell översikt över Azure återställnings tider GUIX](chapter-3.md)

[Kapitel 4 – Beskrivning av Azure återställnings tider GUIX-tjänster](chapter-4.md)

[Kapitel 5 – Azure återställnings tider GUIX display Drivers](chapter-5.md)  

[Azure återställnings tider GUIX-exempel](guix-example.md)

[Bilaga A – GUIX färg definitioner för Azure återställnings tider](appendix-a.md)

[Bilaga B – färg format för Azure återställnings tider-GUIX](appendix-b.md)

[Bilaga C – widgets format för Azure återställnings tider-GUIX](appendix-c.md)

[Bilaga D – Azure återställnings tider GUIX pensel, attribut för arbets yta och toning](appendix-d.md)

[Bilaga E – händelse Beskrivning för Azure återställnings tider GUIX](appendix-e.md)

[Bilaga F – Azure återställnings tider GUIX återställnings tider binding Services](appendix-f.md)

[Bilaga G – Azure återställnings tider GUIX-teckensnitts struktur](appendix-g.md)

[Bilaga H – Azure återställnings tider-GUIX Build-Time konfigurations flaggor](appendix-h.md)

[Bilaga I – Azure återställnings tider GUIX informations strukturer](appendix-i.md)

## <a name="guide-conventions"></a>Guide konventioner

*Kursiv stil* – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.

**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.

> [!IMPORTANT]
> Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.

## <a name="azure-rtos-guix-data-types"></a>Data typer för Azure dataåterställnings tiders-GUIX

Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-GUIX, finns det flera särskilda data typer som används i Azure återställnings tider GUIX service Call-gränssnitt. Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från ThreadX och kan hittas i filen ***tx_port. h*** som ingår i ThreadX-distributionen.

Följande är en lista över data typer för Azure återställnings tider GUIX service Call och deras associerade betydelser:

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **UINT**             | Basic-osignerat heltal. Den här typen är mappad till den mest användbara osignerade data typen.                                |
| **INT**              | Basic-signerat heltal. Den här typen är mappad till den mest praktiska signerade data typen.                                    |
| **ULONG**            | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.                                                      |
| **VOID**             | Nästan alltid ekvivalent med kompilatorns void-typ.                                                                 |
| **GX_CHAR**         | Oftast TypeDef som den definierade tecken typen compiler.                                                               |
| **GX_BYTE**          | 8-bitars signerad typ.                                                                                                    |
| **GX_UBYTE**         | 8-bitars osignerad typ.                                                                                                  |
| **GX_VALUE**        | 16-eller 32-bitars signerad typ. Definieras som nödvändig för bästa prestanda på mål systemet.                                |
| **GX_FIXED_VAL**   | Numerisk datatyp för fast punkt.                                                                                        |
| **GX_RESOURCE_ID** | Osignerad lång typ.                                                                                                   |
| **GX_COLOR**        | Osignerad lång typ.                                                                                                   |
| **GX_STRING**       | Struktur som innehåller GX_CHAR \* gx_string_ptr och UINT gx_string_length.                                          |
| **GX_POINT**        | Struktur som innehåller gx_point_x och gx_point_y.                                                                   |
| **GX_RECTANGLE**    | Struktur som innehåller gx_rectangle_left, gx_rectangle_top, gx_rectangle_right och gx_rectangle_bottom fält. |
| **GX_GLYPH**        | Struktur som innehåller Glyph-mått.                                                                                   |
| **GX_FONT**         | Struktur som innehåller teckensnitts mått.                                                                                    |
| **GX_BRUSH**        | Struktur som innehåller pensel mått.                                                                               |
**GX_PIXELMAP**       | Struktur som innehåller Pixelmap-mått.

Ytterligare data typer används i Azure återställnings tider GUIX-källan. De finns antingen i ***tx_port. h** _ eller _ *_gx_port. h_** filer.

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.

2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-GUIX som föregåde problemet.

3. Innehållet i _tx_version_id-och _gx_version_id-strängar som finns i ***tx_port. h**_ -och _ *_gx_port. h_**-filerna i distributionen. De här strängarna ger oss värdefull information om din kör tids miljö.

4. Innehållet i RAM-minnet för följande ULONG-variabler:

    **_tx_build_options** **_gx_system_build_options**

    Dessa variabler ger oss information om hur dina Azure återställnings tider ThreadX-och Azure återställnings tider GUIX-bibliotek skapades.

5. Innehållet i RAM-minnet för följande ULONG-variabler:

    **_gx_system_last_error** **_gx_system_error_count**

    Dessa variabler håller koll på interna systemfel i Azure återställnings tider GUIX. Om _gx_system_error_count är större än en måste du ange en Bryt punkt för funktionen i funktionen _gx_system_error_process och ange värdet för _gx_system_last_error i det här läget. Detta ger det första interna Azure återställnings tider GUIX-systemfel.

6. En spårnings-buffert som samlats in omedelbart efter det att problemet upptäcktes. Detta åstadkommer du genom att skapa Azure återställnings tider-ThreadX och Azure återställnings tider GUIX-biblioteken med TX_ENABLE_EVENT_TRACE och anropa tx_trace_enable med information om spårnings-bufferten.

7. Azure återställnings tider GUIX Studio-projektet som du använder, om det är tillämpligt eller minst ett litet projekt tillräckligt litet för att demonstrera den brist som du rapporterar.
