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
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="e9d14-103">Användar handbok för Azure återställnings tider USBX Device stack</span><span class="sxs-lookup"><span data-stu-id="e9d14-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="e9d14-104">Den här guiden innehåller omfattande information om Azure återställnings tider-USBX, högpresterande USB Foundation-programvara från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e9d14-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="e9d14-105">Den är avsedd för den inbäddade programutvecklaren i real tid.</span><span class="sxs-lookup"><span data-stu-id="e9d14-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="e9d14-106">Utvecklaren bör vara bekant med standard operativ system funktioner i real tid, USB-specifikationen och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="e9d14-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="e9d14-107">Teknisk information som rör USB finns i specifikationer för USB-specifikation och USB-klass som kan hämtas på https://www.USB.org/developers</span><span class="sxs-lookup"><span data-stu-id="e9d14-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="e9d14-108">Organisation</span><span class="sxs-lookup"><span data-stu-id="e9d14-108">Organization</span></span>

- <span data-ttu-id="e9d14-109">[**Kapitel 1**](usbx-device-stack-1.md) – innehåller en introduktion till Azure återställnings tider USBX</span><span class="sxs-lookup"><span data-stu-id="e9d14-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="e9d14-110">[**Kapitel 2**](usbx-device-stack-2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-USBX med ditt ThreadX-program</span><span class="sxs-lookup"><span data-stu-id="e9d14-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="e9d14-111">[**Kapitel 3**](usbx-device-stack-3.md) – beskriver funktionella komponenter i enhets stacken för Azure återställnings tider USBX</span><span class="sxs-lookup"><span data-stu-id="e9d14-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="e9d14-112">[**Kapitel 4**](usbx-device-stack-4.md) – beskriver Azure återställnings tider USBX Device stack-tjänster</span><span class="sxs-lookup"><span data-stu-id="e9d14-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="e9d14-113">[**Kapitel 5**](usbx-device-stack-5.md) – beskriver varje Azure återställnings tider USBX-enhets klass inklusive API: er</span><span class="sxs-lookup"><span data-stu-id="e9d14-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="e9d14-114">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="e9d14-114">Customer Support Center</span></span>

<span data-ttu-id="e9d14-115">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="e9d14-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="e9d14-116">Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:</span><span class="sxs-lookup"><span data-stu-id="e9d14-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="e9d14-117">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="e9d14-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="e9d14-118">En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="e9d14-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="e9d14-119">Innehållet i den **_tx_version_id** strängen som finns i filen **_tx_port. h_** i distributionen.</span><span class="sxs-lookup"><span data-stu-id="e9d14-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="e9d14-120">Den här strängen ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="e9d14-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="e9d14-121">Innehållet i RAM-minnet för *_tx_build_options* **ulong** -variabeln.</span><span class="sxs-lookup"><span data-stu-id="e9d14-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="e9d14-122">Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.</span><span class="sxs-lookup"><span data-stu-id="e9d14-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
