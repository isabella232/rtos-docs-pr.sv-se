---
title: Kapitel 1 – Introduktion till Azure återställnings tider USBX Host stack
description: I det här kapitlet introduceras USBX Host stack som beskriver dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a9fdd86d47bd4680409cc550c87bc6f456d146a9
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377058"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="024b8-103">Kapitel 1 – Introduktion till Azure återställnings tider USBX Host stack</span><span class="sxs-lookup"><span data-stu-id="024b8-103">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="024b8-104">USBX är en USB-stack med full funktionalitet för djupt inbäddade program.</span><span class="sxs-lookup"><span data-stu-id="024b8-104">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="024b8-105">I det här kapitlet introduceras USBX som beskriver dess program och fördelar.</span><span class="sxs-lookup"><span data-stu-id="024b8-105">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="024b8-106">USBX-funktioner</span><span class="sxs-lookup"><span data-stu-id="024b8-106">USBX features</span></span>

<span data-ttu-id="024b8-107">USBX stöder de tre befintliga USB-specifikationerna: 1,1, 2,0 och OTG.</span><span class="sxs-lookup"><span data-stu-id="024b8-107">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="024b8-108">Den är utformad för att vara skalbar och kommer att kunna hantera enkla USB-topologier med bara en ansluten enhet samt komplexa topologier med flera enheter och sammanhängande nav.</span><span class="sxs-lookup"><span data-stu-id="024b8-108">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="024b8-109">USBX stöder alla data överförings typer för USB-protokollen: kontroll, Mass, avbrott och isokrona.</span><span class="sxs-lookup"><span data-stu-id="024b8-109">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="024b8-110">USBX stöder både värd sidan och enhets sidan.</span><span class="sxs-lookup"><span data-stu-id="024b8-110">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="024b8-111">Varje sida består av tre lager.</span><span class="sxs-lookup"><span data-stu-id="024b8-111">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="024b8-112">Styrenhets skikt</span><span class="sxs-lookup"><span data-stu-id="024b8-112">Controller layer</span></span>
- <span data-ttu-id="024b8-113">Stack skikt</span><span class="sxs-lookup"><span data-stu-id="024b8-113">Stack layer</span></span>
- <span data-ttu-id="024b8-114">Klass skikt</span><span class="sxs-lookup"><span data-stu-id="024b8-114">Class layer</span></span>

<span data-ttu-id="024b8-115">Relationen mellan USB-skikten är följande.</span><span class="sxs-lookup"><span data-stu-id="024b8-115">The relationship between the USB layers is as follows.</span></span>

![USB-skikt](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="024b8-117">Produkt höjd punkter</span><span class="sxs-lookup"><span data-stu-id="024b8-117">Product Highlights</span></span>

- <span data-ttu-id="024b8-118">Slutför support för ThreadX-processor</span><span class="sxs-lookup"><span data-stu-id="024b8-118">Complete ThreadX processor support</span></span>
- <span data-ttu-id="024b8-119">Ingen royalties</span><span class="sxs-lookup"><span data-stu-id="024b8-119">No royalties</span></span>
- <span data-ttu-id="024b8-120">Fullständig ANSI C-källkod</span><span class="sxs-lookup"><span data-stu-id="024b8-120">Complete ANSI C source code</span></span>
- <span data-ttu-id="024b8-121">Real tids prestanda</span><span class="sxs-lookup"><span data-stu-id="024b8-121">Real-time performance</span></span>
- <span data-ttu-id="024b8-122">Teknisk support som svarar</span><span class="sxs-lookup"><span data-stu-id="024b8-122">Responsive technical support</span></span>
- <span data-ttu-id="024b8-123">Stöd för flera värd styrenheter</span><span class="sxs-lookup"><span data-stu-id="024b8-123">Multiple host controller support</span></span>
- <span data-ttu-id="024b8-124">Stöd för flera klasser</span><span class="sxs-lookup"><span data-stu-id="024b8-124">Multiple class support</span></span>
- <span data-ttu-id="024b8-125">Flera klass instanser</span><span class="sxs-lookup"><span data-stu-id="024b8-125">Multiple class instances</span></span>
- <span data-ttu-id="024b8-126">Integrering av klasser med ThreadX, FileX och NetX</span><span class="sxs-lookup"><span data-stu-id="024b8-126">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="024b8-127">Stöd för USB-enheter med flera konfigurationer</span><span class="sxs-lookup"><span data-stu-id="024b8-127">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="024b8-128">Stöd för USB-sammansatta enheter</span><span class="sxs-lookup"><span data-stu-id="024b8-128">Support for USB composite devices</span></span>
- <span data-ttu-id="024b8-129">Stöd för överlappande hubbar</span><span class="sxs-lookup"><span data-stu-id="024b8-129">Support for cascading hubs</span></span>
- <span data-ttu-id="024b8-130">Stöd för USB-energihantering</span><span class="sxs-lookup"><span data-stu-id="024b8-130">Support for USB power management</span></span>
- <span data-ttu-id="024b8-131">Stöd för USB-OTG</span><span class="sxs-lookup"><span data-stu-id="024b8-131">Support for USB OTG</span></span>
- <span data-ttu-id="024b8-132">Exportera spårnings händelser för TraceX</span><span class="sxs-lookup"><span data-stu-id="024b8-132">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="024b8-133">Kraftfulla tjänster av USBX</span><span class="sxs-lookup"><span data-stu-id="024b8-133">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="024b8-134">Stöd för flera värd styrenheter</span><span class="sxs-lookup"><span data-stu-id="024b8-134">Multiple Host Controller Support</span></span>

<span data-ttu-id="024b8-135">USBX kan stödja flera USB-värdstyrenheter som körs samtidigt.</span><span class="sxs-lookup"><span data-stu-id="024b8-135">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="024b8-136">Med den här funktionen kan USBX stödja USB 2,0-standarden med hjälp av bakåtkompatibilitet som är kopplat till de flesta USB 2,0-värd styrenheter på marknaden idag.</span><span class="sxs-lookup"><span data-stu-id="024b8-136">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="024b8-137">Schemaläggare för USB-programvara</span><span class="sxs-lookup"><span data-stu-id="024b8-137">USB Software Scheduler</span></span>

<span data-ttu-id="024b8-138">USBX innehåller en USB-programvara som krävs för att stödja USB-styrenheter som inte har bearbetning av maskin varu listor.</span><span class="sxs-lookup"><span data-stu-id="024b8-138">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="024b8-139">USBX Software Scheduler ordnar USB-överföringar med rätt frekvens av tjänst och prioritet och instruerar USB-styrenheten att köra varje överföring.</span><span class="sxs-lookup"><span data-stu-id="024b8-139">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="024b8-140">Fullständigt stöd för USB-enhets ramverk</span><span class="sxs-lookup"><span data-stu-id="024b8-140">Complete USB Device Framework Support</span></span>

<span data-ttu-id="024b8-141">USBX kan stödja de mest krävande USB-enheterna, inklusive flera konfigurationer, flera gränssnitt och flera alternativa inställningar.</span><span class="sxs-lookup"><span data-stu-id="024b8-141">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="024b8-142">Lättanvända API: er</span><span class="sxs-lookup"><span data-stu-id="024b8-142">Easy-To-Use APIs</span></span>

<span data-ttu-id="024b8-143">USBX tillhandahåller den mycket bästa inbäddade USB-stacken på ett sätt som är lätt att förstå och använda.</span><span class="sxs-lookup"><span data-stu-id="024b8-143">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="024b8-144">USBX-API: n gör tjänsterna intuitiva och konsekventa.</span><span class="sxs-lookup"><span data-stu-id="024b8-144">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="024b8-145">Genom att använda de tillhandahållna USBX klass-API: erna behöver inte användar programmet förstå USB-protokollens komplexitet.</span><span class="sxs-lookup"><span data-stu-id="024b8-145">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
