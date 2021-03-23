---
title: Kapitel 3 – överväganden för USBX DPUMP-klass
description: USBX innehåller en DPUMP-klass för värden och enhets sidan. Den här klassen är inte en standard klass i sig själv, utan i stället ett exempel som illustrerar hur du skapar en enkel enhet med två Mass ledningar och hur du skickar data till och från dessa två pipes
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828614"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>Kapitel 3 – överväganden för USBX DPUMP-klass

USBX innehåller en **DPUMP** -klass för värden och enhets sidan. Den här klassen är inte en standard klass i sig själv, utan i stället ett exempel som illustrerar hur du skapar en enkel enhet med två Mass ledningar och hur du skickar data till och från dessa två ledningar. **DPUMP** -klassen kan användas för att starta en anpassad klass eller för äldre RS232-enheter.

Flödes diagram för USB-DPUMP:

![Flödes diagram för USB-DPUMP](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>USBX DPUMP-enhets klass

Enhetens **DPUMP** -klass använder en tråd som startas vid anslutning till USB-värden. Tråden väntar på ett paket som kommer från den utgående slut punkten. När ett paket tas emot kopierar det innehållet till Mass-och slut punktens buffert och publicerar en transaktion på den här slut punkten, väntar på att värden ska utfärda en begäran om att läsa från den här slut punkten. Detta ger en loopback-mekanism mellan utsamlings-och Mass slut punkter.
