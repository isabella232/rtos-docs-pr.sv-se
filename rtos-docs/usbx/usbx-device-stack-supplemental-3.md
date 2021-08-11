---
title: Kapitel 3 – USBX DPUMP-klassöverväganden
description: USBX innehåller en DPUMP-klass för värd- och enhetssidan. Den här klassen är inte en standardklass i sig, utan snarare ett exempel som illustrerar hur du skapar en enkel enhet med hjälp av två masspipelar och skickar data fram och tillbaka på dessa två pipes
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d453d9ee19b9bc7ca7809102f087f46fdde05dc62b756d9eb3f38f493805be4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791161"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>Kapitel 3 – USBX DPUMP-klassöverväganden

USBX innehåller en **DPUMP-klass** för värd- och enhetssidan. Den här klassen är inte en standardklass i sig, utan snarare ett exempel som illustrerar hur du skapar en enkel enhet med hjälp av två masspipelar och skickar data fram och tillbaka på dessa två pipes. **DPUMP-klassen** kan användas för att starta en anpassad klass eller för äldre RS232-enheter.

USB DPUMP-flödesdiagram:

![USB DPUMP-Flow diagram](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>USBX DPUMP-enhetsklass

Enhetens **DPUMP-klass** använder en tråd som startas vid anslutning till USB-värden. Tråden väntar på att ett paket ska komma på massutfyllnadsslutpunkten. När ett paket tas emot kopieras innehållet till bufferten Massinslutpunkt och en transaktion skickas på den här slutpunkten i väntan på att värden ska utfärda en begäran om att läsa från den här slutpunkten. Detta ger en loopback-mekanism mellan massutfyllnad och massin bulk in-slutpunkter.
