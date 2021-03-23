---
title: Kapitel 1 – Introduktion till Azure återställnings tider USBX Device stack
description: USBX är en USB-stack med full funktionalitet för djupt inbäddade program. I det här kapitlet introduceras USBX som beskriver dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828623"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="0879e-104">Kapitel 1 – Introduktion till Azure återställnings tider USBX Device stack</span><span class="sxs-lookup"><span data-stu-id="0879e-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="0879e-105">USBX är en USB-stack med full funktionalitet för djupt inbäddade program.</span><span class="sxs-lookup"><span data-stu-id="0879e-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="0879e-106">I det här kapitlet introduceras USBX, som beskriver program och förmåner</span><span class="sxs-lookup"><span data-stu-id="0879e-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="0879e-107">USBX-funktioner</span><span class="sxs-lookup"><span data-stu-id="0879e-107">USBX features</span></span>

<span data-ttu-id="0879e-108">USBX stöder de tre befintliga USB-specifikationerna: 1,1, 2,0 och OTG.</span><span class="sxs-lookup"><span data-stu-id="0879e-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="0879e-109">Den är utformad för att vara skalbar och kommer att kunna hantera enkla USB-topologier med bara en ansluten enhet samt komplexa topologier med flera enheter och sammanhängande nav.</span><span class="sxs-lookup"><span data-stu-id="0879e-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="0879e-110">USBX stöder alla data överförings typer för USB-protokollen: kontroll, Mass, avbrott och isokrona.</span><span class="sxs-lookup"><span data-stu-id="0879e-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="0879e-111">USBX stöder både värd sidan och enhets sidan.</span><span class="sxs-lookup"><span data-stu-id="0879e-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="0879e-112">Varje sida består av tre lager.</span><span class="sxs-lookup"><span data-stu-id="0879e-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="0879e-113">Styrenhets skikt</span><span class="sxs-lookup"><span data-stu-id="0879e-113">Controller layer</span></span>
- <span data-ttu-id="0879e-114">Stack skikt</span><span class="sxs-lookup"><span data-stu-id="0879e-114">Stack layer</span></span>
- <span data-ttu-id="0879e-115">Klass skikt</span><span class="sxs-lookup"><span data-stu-id="0879e-115">Class layer</span></span>

<span data-ttu-id="0879e-116">Relationen mellan USB-skikten är följande:</span><span class="sxs-lookup"><span data-stu-id="0879e-116">The relationship between the USB layers is as follows:</span></span>

![USB-skikt](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="0879e-118">Produkt höjd punkter</span><span class="sxs-lookup"><span data-stu-id="0879e-118">Product Highlights</span></span>

- <span data-ttu-id="0879e-119">Slutför support för ThreadX-processor</span><span class="sxs-lookup"><span data-stu-id="0879e-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="0879e-120">Ingen royalties</span><span class="sxs-lookup"><span data-stu-id="0879e-120">No royalties</span></span>
- <span data-ttu-id="0879e-121">Fullständig ANSI C-källkod</span><span class="sxs-lookup"><span data-stu-id="0879e-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="0879e-122">Real tids prestanda</span><span class="sxs-lookup"><span data-stu-id="0879e-122">Real-time performance</span></span>
- <span data-ttu-id="0879e-123">Teknisk support som svarar</span><span class="sxs-lookup"><span data-stu-id="0879e-123">Responsive technical support</span></span>
- <span data-ttu-id="0879e-124">Stöd för flera klasser</span><span class="sxs-lookup"><span data-stu-id="0879e-124">Multiple class support</span></span>
- <span data-ttu-id="0879e-125">Flera klass instanser</span><span class="sxs-lookup"><span data-stu-id="0879e-125">Multiple class instances</span></span>
- <span data-ttu-id="0879e-126">Integrering av klasser med ThreadX, FileX och NetX</span><span class="sxs-lookup"><span data-stu-id="0879e-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="0879e-127">Stöd för USB-enheter med flera konfigurationer</span><span class="sxs-lookup"><span data-stu-id="0879e-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="0879e-128">Stöd för USB-sammansatta enheter</span><span class="sxs-lookup"><span data-stu-id="0879e-128">Support for USB composite devices</span></span>
- <span data-ttu-id="0879e-129">Stöd för USB-energihantering</span><span class="sxs-lookup"><span data-stu-id="0879e-129">Support for USB power management</span></span>
- <span data-ttu-id="0879e-130">Stöd för USB-OTG</span><span class="sxs-lookup"><span data-stu-id="0879e-130">Support for USB OTG</span></span>
- <span data-ttu-id="0879e-131">Exportera spårnings händelser för TraceX</span><span class="sxs-lookup"><span data-stu-id="0879e-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="0879e-132">Kraftfulla tjänster av USBX</span><span class="sxs-lookup"><span data-stu-id="0879e-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="0879e-133">Fullständigt stöd för USB-enhets ramverk</span><span class="sxs-lookup"><span data-stu-id="0879e-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="0879e-134">USBX kan stödja de mest krävande USB-enheterna, inklusive flera konfigurationer, flera gränssnitt och flera alternativa inställningar.</span><span class="sxs-lookup"><span data-stu-id="0879e-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="0879e-135">Lättanvända API: er</span><span class="sxs-lookup"><span data-stu-id="0879e-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="0879e-136">USBX tillhandahåller den bästa inbäddade USB-stacken på ett sätt som är lätt att förstå och använda.</span><span class="sxs-lookup"><span data-stu-id="0879e-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="0879e-137">USBX-API: n gör tjänsterna intuitiva och konsekventa.</span><span class="sxs-lookup"><span data-stu-id="0879e-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="0879e-138">Genom att använda de tillhandahållna USBX klass-API: erna behöver inte användar programmet förstå USB-protokollens komplexitet.</span><span class="sxs-lookup"><span data-stu-id="0879e-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
