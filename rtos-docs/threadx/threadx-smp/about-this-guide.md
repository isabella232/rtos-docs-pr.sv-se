---
title: Om den här guiden
description: Den här guiden innehåller omfattande information Azure RTOS om ThreadX SMP, Microsofts högpresterande inbäddade realtidskärna.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6a8758bff2f205b06448905634172c05dd7fe189cce9fbe3977f6080c51eb95d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784792"
---
# <a name="about-this-guide"></a>Om den här guiden

Den här guiden innehåller omfattande information Azure RTOS om ThreadX SMP, Microsofts högpresterande inbäddade realtidskärna.

Den är avsedd för den inbäddade realtidsutvecklaren. Utvecklaren bör vara bekant med standardfunktioner för realtidsoperativsystemet och programmeringsspråket C.

## <a name="organization"></a>Organisation

| Kapitel       | Översikt                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Kapitel 1** | Ger en grundläggande översikt över ThreadX SMP och dess relation till inbäddad utveckling i realtid.           |
| **Kapitel 2** | Innehåller de grundläggande stegen för att installera och använda ThreadX SMP i *ditt program direkt från grunden.*           |
| **Kapitel 3** | Beskriver i detalj den funktionella driften av ThreadX SMP, den högpresterande SMP-kerneln i realtid.    |
| **Kapitel 4** | Beskriver programmets gränssnitt till ThreadX SMP.                                                        |
| **Kapitel 5** | Beskriver hur du skriver I/O-drivrutiner för ThreadX SMP-program.                                                |
| **Kapitel 6** | Beskriver demonstrationsprogrammet som medföljer varje ThreadX SMP-processorsupportpaket. |
| **Bilaga A** | ThreadX SMP API        |
| **Bilaga B** | ThreadX SMP-konstanter  |
| **Bilaga C** | ThreadX SMP-datatyper |
| **Bilaga D** | ASCII-diagram            |

## <a name="guide-conventions"></a>Guidekonventioner

- *Italics*  -  *typeface anger boktitlar, betonar viktiga ord och anger variabler.*
- **Fetstil**  -  **typeface anger filnamn, nyckelord och betonar dessutom viktiga ord och variabler.**

> [!IMPORTANT]
> Informationssymboler uppmärksammar viktig eller ytterligare information som kan påverka prestanda eller funktion.

> [!WARNING]
> Varningssymboler uppmärksammar situationer där utvecklare bör vara noga med att undvika eftersom de kan orsaka allvarliga fel.

## <a name="threadx-smp-data-types"></a>ThreadX SMP-datatyper

Förutom de anpassade ThreadX SMP-kontrollstrukturdatatyperna finns det en serie särskilda datatyper som används i ThreadX SMP-tjänstens anropsgränssnitt. Dessa särskilda datatyper mappar direkt till datatyper för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen finns i filen ***tx_port.h*** som finns på distributionsdisken.

Följande är en lista över ThreadX SMP-tjänstens anropsdatatyper och deras associerade innebörder:

| Datatyp          | Innebörd                                                          |
| --------- | --------------------------------------------------------- |
| **Uint**  | Grundläggande heltal utansignering. Den här typen måste ha stöd för 8-bitars osignerade data. Den mappas dock till den mest praktiska osignerade datatypen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data.                                                                     |
| **Void**  | Nästan alltid likvärdigt med kompilatorns void-typ.                                                                                |
| **Char**  | Oftast en standardtyp med 8 bitar.                                                                                          |

Ytterligare datatyper används i ThreadX SMP-källan. De finns också i filen ***tx_port.h.***

## <a name="customer-support-center"></a>Customer Support Center

E-post för [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) support: Webbsida: azure.com/rtos

### <a name="latest-product-information"></a>Senaste produktinformation

Besök webbplatsen azure.com/rtos och välj menyalternativet "Support" för att hitta den senaste onlinesupportinformationen, inklusive information om de senaste Versionerna av ThreadX SMP-produkten.

### <a name="what-we-need-from-you"></a>Vad vi behöver från dig

Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och huruvida det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller ThreadX SMP som föregick problemet.
3. Innehållet i strängen ***_tx_version_id** _ finns i filen _ *_tx_port.h_** i distributionen. Den här strängen ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för ***_tx_build_options*** ULONG-variabeln. Den här variabeln ger oss information om hur ThreadX SMP-biblioteket har skapats.

### <a name="where-to-send-comments-about-this-guide"></a>Var du vill skicka kommentarer om den här guiden

Skicka eventuella kommentarer och förslag via e-post till Kundsupporten [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) på Ange "ThreadX SMP User Guide" i ämnesraden.
