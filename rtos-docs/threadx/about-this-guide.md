---
title: Om guiden Azure RTOS ThreadX
description: Den här guiden innehåller omfattande information om Azure RTOS ThreadX, Microsofts högpresterande kernel i realtid.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28f088409fdd5e2c075cbf90b21d3d260c811806066e74bffc395207cde0239c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802132"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Om guiden Azure RTOS ThreadX

Den här guiden innehåller omfattande information Azure RTOS ThreadX, Microsofts högpresterande kernel i realtid. 

Den är avsedd för den inbäddade realtidsutvecklaren. Utvecklaren bör vara bekant med standardfunktioner för realtidsoperativsystemet och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – Ger en grundläggande översikt över Azure RTOS ThreadX och dess relation till inbäddad utveckling i realtid

[Kapitel 2](chapter2.md) – Ger de grundläggande stegen för att installera Azure RTOS använda ThreadX i ditt program *direkt*

[Kapitel 3](chapter3.md) – Beskriver i detalj den funktionella driften Azure RTOS ThreadX, kerneln med höga prestanda i realtid

[Kapitel 4](chapter4.md) – Beskriver programmets gränssnitt för att Azure RTOS ThreadX

[Kapitel 5 –](chapter5.md) Beskriver hur du skriver I/O-drivrutiner Azure RTOS ThreadX-program

[Kapitel 6](chapter6.md) – Beskriver demonstrationsprogrammet som levereras med varje Azure RTOS ThreadX-processorsupportpaket

[Bilaga A](appendix-a.md) – Azure RTOS ThreadX API

[Bilaga B](appendix-b.md) – Azure RTOS ThreadX-konstanter

[Bilaga C](appendix-c.md) – Azure RTOS ThreadX-datatyper

[Bilaga D](appendix-d.md) – ASCII-diagram

## <a name="guide-conventions"></a>Guidekonventioner

*Italics* – typeface anger boktitlar, betonar viktiga ord och anger parametrar.

**Fetstil** – typansiktet anger nyckelord, konstanter, typnamn, användargränssnittselement, variabelnamn och betonar viktiga ord ytterligare.

***Italics och Boldface*** – typeface anger filnamn och funktionsnamn.

> [!IMPORTANT]
> Informationssymboler uppmärksammar viktig eller ytterligare information som kan påverka prestanda eller funktion.

> [!WARNING]
> Varningssymboler uppmärksammar situationer där utvecklare bör vara noga med att undvika eftersom de kan orsaka allvarliga fel.

## <a name="azure-rtos-threadx-data-types"></a>Azure RTOS ThreadX-datatyper

Förutom de anpassade datatyperna Azure RTOS ThreadX-kontrollstruktur finns det en serie särskilda datatyper som används i Azure RTOS ThreadX-tjänstens anropsgränssnitt. Dessa särskilda datatyper mappar direkt till datatyperna i den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen finns i filen ***tx_port.h*** som ingår i källan.

Följande är en lista över datatyper Azure RTOS ThreadX-tjänsten och deras associerade betydelser:

| Datatyp  | Beskrivning |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Uint** | Grundläggande heltal utansignering. Den här typen måste ha stöd för 8-bitars osignerade data. Den mappas dock till den mest praktiska osignerade datatypen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data. |
| **Void** | Nästan alltid likvärdigt med kompilatorns void-typ. |
| **Char** | Oftast en standardtyp med 8 bitar. |
|  |  |

Ytterligare datatyper används i Azure RTOS ThreadX-källan. De finns också i filen ***tx_port.h.***

## <a name="customer-support-center"></a>Customer Support Center

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och om det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS ThreadX som föregick problemet.
3. Innehållet i den *_tx_version_id strängen* som finns *i tx_port.h-filen* för distributionen. Den här strängen ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för **den _tx_build_options** **ULONG-variabeln.** Den här variabeln ger oss information om hur Azure RTOS ThreadX-biblioteket har skapats.
