---
title: Azure RTOS FileX-användarhandbok
description: Den här guiden innehåller omfattande information Azure RTOS filex, det högpresterande filsystemet i realtid från Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fe70fc3cff6e656328d38b2583116e58a6c98510d5f0554f81a7b728f95457
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782412"
---
# <a name="about-this-filex-user-guide"></a>Om den här användarhandboken för FileX

Den här guiden innehåller omfattande information Azure RTOS FileX, det högpresterande inbäddade filsystemet i realtid från Microsoft. För att få ut mesta av den här guiden bör du vara bekant med standardfunktioner för operativsystemet i realtid, FAT-filsystemtjänster och programmeringsspråket C.

## <a name="organization"></a>Organisation

[Kapitel 1](chapter1.md) – Introducerar Azure RTOS FileX

[Kapitel 2](chapter2.md) – Ger grundläggande steg för att installera och använda Azure RTOS FileX med ditt Azure RTOS ThreadX-program

[Kapitel 3](chapter3.md) – Ger en funktionell översikt över Azure RTOS FileX-systemet och grundläggande information om FAT-filformat

[Kapitel 4](chapter4.md) – Beskriver programmets gränssnitt för att Azure RTOS FileX

[Kapitel 5 –](chapter5.md) Beskriver den angivna Azure RTOS FileX RAM-drivrutinen och hur du skriver egna anpassade Azure RTOS FileX-drivrutiner

[Kapitel 6](chapter6.md) – Beskriver Azure RTOS FileX-feltolerant modul

[Bilaga A](appendix-a.md) – Azure RTOS FileX Services

[Bilaga B](appendix-b.md) – Azure RTOS FileX-konstanter

[Bilaga C](appendix-c.md) – Azure RTOS FileX-datatyper

[Bilaga D](appendix-d.md) – ASCII-diagram

## <a name="guide-conventions"></a>Guidekonventioner

*Italics* – Typeface anger boktitlar, betonar viktiga ord och anger variabler.

**Boldface** – Typeface anger filnamn, nyckelord och betonar viktiga ord och variabler ytterligare.

> [!NOTE]
> Informationssymboler uppmärksammar viktig eller ytterligare information som kan påverka prestanda eller funktion.

> [!IMPORTANT]
> Varningssymboler uppmärksammar situationer som utvecklare bör undvika eftersom de kan orsaka allvarliga fel.

## <a name="filex-data-types"></a>FileX-datatyper

Förutom de anpassade datatyperna Azure RTOS FileX-kontrollstruktur finns det en serie särskilda datatyper som används i Azure RTOS anropsgränssnitt för FileX-tjänsten. Dessa särskilda datatyper mappar direkt till datatyper för den underliggande C-kompilatorn. Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer. Den exakta implementeringen ärvs från Azure RTOS ThreadX och finns i filen tx_port.h som ingår i Azure RTOS ThreadX-distributionen.

Följande är en lista över datatyper Azure RTOS FileX-tjänstens anrop och deras associerade betydelser.

| Typ  | Description  |
|---|---|
| **Uint** | Grundläggande osignerat heltal. Den här typen måste ha stöd för 8-bitars osignerade data. Den mappas dock till den mest praktiska osignerade datatypen. |
| **ULONG** | Osignerad lång typ. Den här typen måste ha stöd för 32-bitars osignerade data. |
| **Void** | Nästan alltid likvärdigt med kompilatorns void-typ. |
| **Char** | Oftast en standardtyp med 8 bitar. |
| **ULONG64** | 64-bitars heltalsdatatypen osignerad. |

Ytterligare datatyper används i FileX-källan. De finns antingen i filerna ***tx_port.h** _ eller _ *_fx_port.h_** .

## <a name="customer-support-center"></a>Kundsupport

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt.

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och huruvida det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller FileX som föregick problemet.
3. Innehållet i _tx_version_id och fx_version_id i _filerna ***tx_port.h**_ och _ *_fx_port.h_** för distributionen. Dessa strängar ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för följande **ULONG-variabler.** Dessa variabler ger oss information om hur dina ThreadX- och FileX-bibliotek har skapats:

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
