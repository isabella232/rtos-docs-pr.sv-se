---
title: Azure RTOS användarhandbok för USBX-värdstack
description: Den här guiden innehåller omfattande information Azure RTOS USBX, högpresterande USB Foundation-programvara från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a41f1b386156be6f8fa773fe2b90bb873cff0fd0e8636bc4d3d8f75295bf7f19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802557"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a>Azure RTOS användarhandbok för USBX-värdstack

Den här guiden innehåller omfattande information Azure RTOS USBX, högpresterande USB Foundation-programvara från Microsoft.

Den är avsedd för den inbäddade realtidsutvecklaren. Utvecklaren bör vara bekant med standardfunktioner för realtidsoperativsystemet, USB-specifikationen och programmeringsspråket C.

Teknisk information om USB finns i USB-specifikationen och USB-klassspecifikationerna som kan laddas ned på [https://www.USB.org/developers](https://www.USB.org/developers)

## <a name="organization"></a>Organisation

- [**Kapitel 1**](usbx-host-stack-1.md) – innehåller en introduktion Azure RTOS USBX

- [**Kapitel 2 –**](usbx-host-stack-2.md) ger grundläggande steg för att installera och använda Azure RTOS USBX med ditt Azure RTOS ThreadX-program

- [**Kapitel 3**](usbx-host-stack-3.md) – ger en funktionell översikt över Azure RTOS USBX och grundläggande information om USB

- [**Kapitel 4**](usbx-host-stack-4.md) – beskriver programmets gränssnitt för att Azure RTOS USBX i värdläge

- [**Kapitel 5 –**](usbx-host-stack-5.md) beskriver API:erna för de Azure RTOS USBX-värdklasserna

- [**Kapitel 6**](usbx-host-stack-6.md) – beskriver Azure RTOS USBX CDC-ECM-klass

## <a name="customer-support-center"></a>Customer Support Center

Skicka en supportbiljett via Azure-portalen för frågor eller hjälp med att följa stegen här. Ange följande information i ett e-postmeddelande så att vi kan lösa din supportbegäran mer effektivt.

1. En detaljerad beskrivning av problemet, inklusive förekomstfrekvens och om det kan återskapas på ett tillförlitligt sätt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure RTOS ThreadX som föregick problemet.
3. Innehållet i den *_tx_version_id strängen* som finns *i tx_port.h-filen* för distributionen. Den här strängen ger oss värdefull information om din körningsmiljö.
4. Innehållet i RAM-minnet för *_tx_build_options* ULONG-variabeln. Den här variabeln ger oss information om hur Azure RTOS ThreadX-biblioteket har skapats.
