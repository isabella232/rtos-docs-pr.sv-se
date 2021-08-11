---
title: Azure RTOS traceX-användarhandbok
description: Den här guiden innehåller omfattande information Azure RTOS TraceX, Microsoft Windows-baserat systemanalysverktyg från Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 89a39112d6fc6d231408179ebb3867c21f927326930a1610529b142aa71a1027
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784078"
---
# <a name="about-this-guide"></a>Om den här guiden

Den här guiden innehåller omfattande information Azure RTOS TraceX, Microsoft Windows-baserat systemanalysverktyg för Microsoft Azure RTOS.

Den är avsedd för den inbäddade realtidsutvecklaren med hjälp Azure RTOS ThreadX Real-Time RTOS (Operating System) och tilläggskomponenter. Utvecklaren bör känna till standardkoncepten Azure RTOS ThreadX Azure RTOS FileX och Azure RTOS NetX.

## <a name="organization"></a>Organisation

- [Kapitel 1](chapter1.md) – innehåller en grundläggande översikt över Azure RTOS TraceX och beskriver dess relation till realtidsutveckling.
- [Kapitel 2](chapter2.md) – innehåller de grundläggande stegen för att installera och använda Azure RTOS TraceX för att analysera ditt program direkt.
- [Kapitel 3](chapter3.md) – beskriver huvudfunktionerna i Azure RTOS TraceX.
- [Kapitel 4 –](chapter4.md) Beskriver funktionerna för prestandaanalys i Azure RTOS TraceX.
- [Kapitel 5](chapter5.md) – beskriver hur du ställer in Azure RTOS ThreadX, Azure RTOS FileX och Azure RTOS NetX för att generera en spårningsbuffert som kan visas av Azure RTOS TraceX.
- [Kapitel 6](chapter6.md) – beskriver Azure RTOS TraceX-händelser i detalj.
- [Kapitel 7](chapter7.md) – beskriver Azure RTOS FileX-händelser i detalj.
- [Kapitel 8](chapter8.md) – beskriver Azure RTOS NetX-händelser i detalj.
- [Kapitel 9](chapter9.md) – beskriver Azure RTOS USBX-händelser i detalj.
- [Kapitel 10](chapter10.md) – beskriver hur du skapar anpassade användarhändelser i detalj.
- [Kapitel 11](chapter11.md) – beskriver den interna spårningsbufferten i detalj.
- [Bilaga A](appendix-a.md) – Azure RTOS ThreadX-portspecifik fil med sin tidsstämpelkälla för insamling av spårningshändelser.
- [Bilaga B](appendix-b.md) – Azure RTOS ThreadX *tx_trace.h-fil* som visar implementeringsinformation om händelsespårningsbufferten.
- [Bilaga C](appendix-c.md) – Sammanfattar kommandoradsverktyg för att konvertera olika filformat till rätt Azure RTOS TraceX-binära filer.
- [Bilaga D](appendix-d.md) – Exempel på dumpning av spårningsfiler från olika utvecklingsverktyg.

## <a name="guide-conventions"></a>Guidekonventioner

*Italics* – Typeface anger boktitlar, betonar viktiga ord och anger variabler.

**Boldface** – Typeface anger filnamn, nyckelord och betonar viktiga ord och variabler ytterligare.

> [!NOTE]
> Visar information om anteckningen.

## <a name="customer-support-center"></a>Kundsupport

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och huruvida det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS ThreadX som föregick problemet.
3. Innehållet i den *_tx_version_id* strängen som finns *i tx_port.h-filen* för distributionen. Den här strängen ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för *_tx_build_options* ULONG-variabeln. Den här variabeln ger oss information om hur Azure RTOS ThreadX-biblioteket har skapats.
