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
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="a52f7-104">Kapitel 3 – överväganden för USBX DPUMP-klass</span><span class="sxs-lookup"><span data-stu-id="a52f7-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="a52f7-105">USBX innehåller en **DPUMP** -klass för värden och enhets sidan.</span><span class="sxs-lookup"><span data-stu-id="a52f7-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="a52f7-106">Den här klassen är inte en standard klass i sig själv, utan i stället ett exempel som illustrerar hur du skapar en enkel enhet med två Mass ledningar och hur du skickar data till och från dessa två ledningar.</span><span class="sxs-lookup"><span data-stu-id="a52f7-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="a52f7-107">**DPUMP** -klassen kan användas för att starta en anpassad klass eller för äldre RS232-enheter.</span><span class="sxs-lookup"><span data-stu-id="a52f7-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="a52f7-108">Flödes diagram för USB-DPUMP:</span><span class="sxs-lookup"><span data-stu-id="a52f7-108">USB DPUMP flow chart:</span></span>

![Flödes diagram för USB-DPUMP](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="a52f7-110">USBX DPUMP-enhets klass</span><span class="sxs-lookup"><span data-stu-id="a52f7-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="a52f7-111">Enhetens **DPUMP** -klass använder en tråd som startas vid anslutning till USB-värden.</span><span class="sxs-lookup"><span data-stu-id="a52f7-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="a52f7-112">Tråden väntar på ett paket som kommer från den utgående slut punkten.</span><span class="sxs-lookup"><span data-stu-id="a52f7-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="a52f7-113">När ett paket tas emot kopierar det innehållet till Mass-och slut punktens buffert och publicerar en transaktion på den här slut punkten, väntar på att värden ska utfärda en begäran om att läsa från den här slut punkten.</span><span class="sxs-lookup"><span data-stu-id="a52f7-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="a52f7-114">Detta ger en loopback-mekanism mellan utsamlings-och Mass slut punkter.</span><span class="sxs-lookup"><span data-stu-id="a52f7-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
