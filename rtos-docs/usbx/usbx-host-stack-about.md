---
title: Användar handbok för värd stack för Azure återställnings tider USBX
description: Den här guiden innehåller omfattande information om Azure återställnings tider-USBX, högpresterande USB Foundation-programvara från Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827330"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a>Användar handbok för värd stack för Azure återställnings tider USBX

Den här guiden innehåller omfattande information om Azure återställnings tider-USBX, högpresterande USB Foundation-programvara från Microsoft.

Den är avsedd för den inbäddade programutvecklaren i real tid. Utvecklaren bör vara bekant med standard operativ system funktioner i real tid, USB-specifikationen och programmeringsspråket C.

Teknisk information som rör USB finns i specifikationer för USB-specifikation och USB-klass som kan hämtas på [https://www.USB.org/developers](https://www.USB.org/developers)

## <a name="organization"></a>Organisation

- [**Kapitel 1**](usbx-host-stack-1.md) – innehåller en introduktion till Azure återställnings tider USBX

- [**Kapitel 2**](usbx-host-stack-2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-USBX med ditt Azure återställnings tider ThreadX-program

- [**Kapitel 3**](usbx-host-stack-3.md) – innehåller en funktionell översikt över Azure återställnings tider USBX och grundläggande information om USB

- [**Kapitel 4**](usbx-host-stack-4.md) – information om programmets gränssnitt till Azure återställnings tider-USBX i värd läge

- [**Kapitel 5**](usbx-host-stack-5.md) – beskriver API: erna för värd klasserna för Azure återställnings tider-USBX

- [**Kapitel 6**](usbx-host-stack-6.md) – beskriver Azure återställnings tider USBX CDC-ECM-klassen

## <a name="customer-support-center"></a>Kund Support Center

Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här. Lämna oss med följande information i ett e-postmeddelande så att vi kan lösa ditt support ärende mer effektivt.

1. En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.
2. En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.
3. Innehållet i den *_tx_version_id* strängen som finns i filen *tx_port. h* i distributionen. Den här strängen ger oss värdefull information om din kör tids miljö.
4. Innehållet i RAM-minnet för *_tx_build_options* ulong-variabeln. Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.
