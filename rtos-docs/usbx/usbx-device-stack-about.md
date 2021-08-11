---
title: Azure RTOS användarhandbok för USBX-enhetsstack
description: Den här guiden innehåller omfattande information Azure RTOS USBX, högpresterande USB Foundation-programvara från Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 042398377766a3e73f72d4dbba0478ba707d378a379fd33de7808675eb96f257
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788770"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Azure RTOS användarhandbok för USBX-enhetsstack

Den här guiden innehåller omfattande information Azure RTOS USBX, den högpresterande USB-grundprogramvaran från Microsoft.

Den är avsedd för den inbäddade realtidsutvecklaren. Utvecklaren bör vara bekant med standardfunktioner för realtidsoperativsystemet, USB-specifikationen och programmeringsspråket C.

Teknisk information om USB finns i USB-specifikationen och USB-klassspecifikationerna som kan laddas ned på https://www.USB.org/developers

## <a name="organization"></a>Organisation

- [**Kapitel 1**](usbx-device-stack-1.md) – innehåller en introduktion Azure RTOS USBX

- [**Kapitel 2**](usbx-device-stack-2.md) – innehåller de grundläggande stegen för att installera och använda Azure RTOS USBX med ditt ThreadX-program

- [**Kapitel 3**](usbx-device-stack-3.md) – beskriver de funktionella komponenterna i den Azure RTOS USBX-enhetsstacken

- [**Kapitel 4 –**](usbx-device-stack-4.md) beskriver Azure RTOS USBX-enhetsstacktjänster

- [**Kapitel 5 –**](usbx-device-stack-5.md) beskriver varje Azure RTOS USBX-enhetsklass, inklusive deras API:er

## <a name="customer-support-center"></a>Customer Support Center

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt:

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och huruvida det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS ThreadX som föregick problemet.
3. Innehållet i den **_tx_version_id** strängen som finns **_i tx_port.h-filen_** för distributionen. Den här strängen ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för *_tx_build_options* **ULONG-variabeln.** Den här variabeln ger oss information om hur Azure RTOS ThreadX-biblioteket har skapats.
