---
title: Användar handbok för Azure återställnings tider USBX Device stack
description: Den här guiden innehåller omfattande information om Azure återställnings tider-USBX, högpresterande USB Foundation-programvara från Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825428"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Användar handbok för Azure återställnings tider USBX Device stack

Den här guiden innehåller omfattande information om Azure återställnings tider-USBX, högpresterande USB Foundation-programvara från Microsoft.

Den är avsedd för den inbäddade programutvecklaren i real tid. Utvecklaren bör vara bekant med standard operativ system funktioner i real tid, USB-specifikationen och programmeringsspråket C.

Teknisk information som rör USB finns i specifikationer för USB-specifikation och USB-klass som kan hämtas på https://www.USB.org/developers

## <a name="organization"></a>Organisation

- [**Kapitel 1**](usbx-device-stack-1.md) – innehåller en introduktion till Azure återställnings tider USBX

- [**Kapitel 2**](usbx-device-stack-2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-USBX med ditt ThreadX-program

- [**Kapitel 3**](usbx-device-stack-3.md) – beskriver funktionella komponenter i enhets stacken för Azure återställnings tider USBX

- [**Kapitel 4**](usbx-device-stack-4.md) – beskriver Azure återställnings tider USBX Device stack-tjänster

- [**Kapitel 5**](usbx-device-stack-5.md) – beskriver varje Azure återställnings tider USBX-enhets klass inklusive API: er

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.
3. Innehållet i den **_tx_version_id** strängen som finns i filen **_tx_port. h_** i distributionen. Den här strängen ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för *_tx_build_options* **ulong** -variabeln. Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.
