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
# <a name="azure-rtos-usbx-host-stack-user-guide"></a><span data-ttu-id="13433-103">Användar handbok för värd stack för Azure återställnings tider USBX</span><span class="sxs-lookup"><span data-stu-id="13433-103">Azure RTOS USBX Host Stack User Guide</span></span>

<span data-ttu-id="13433-104">Den här guiden innehåller omfattande information om Azure återställnings tider-USBX, högpresterande USB Foundation-programvara från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="13433-104">This guide provides comprehensive information about Azure RTOS USBX, the high-performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="13433-105">Den är avsedd för den inbäddade programutvecklaren i real tid.</span><span class="sxs-lookup"><span data-stu-id="13433-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="13433-106">Utvecklaren bör vara bekant med standard operativ system funktioner i real tid, USB-specifikationen och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="13433-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="13433-107">Teknisk information som rör USB finns i specifikationer för USB-specifikation och USB-klass som kan hämtas på [https://www.USB.org/developers](https://www.USB.org/developers)</span><span class="sxs-lookup"><span data-stu-id="13433-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at [https://www.USB.org/developers](https://www.USB.org/developers)</span></span>

## <a name="organization"></a><span data-ttu-id="13433-108">Organisation</span><span class="sxs-lookup"><span data-stu-id="13433-108">Organization</span></span>

- <span data-ttu-id="13433-109">[**Kapitel 1**](usbx-host-stack-1.md) – innehåller en introduktion till Azure återställnings tider USBX</span><span class="sxs-lookup"><span data-stu-id="13433-109">[**Chapter 1**](usbx-host-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="13433-110">[**Kapitel 2**](usbx-host-stack-2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-USBX med ditt Azure återställnings tider ThreadX-program</span><span class="sxs-lookup"><span data-stu-id="13433-110">[**Chapter 2**](usbx-host-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your Azure RTOS ThreadX application</span></span>

- <span data-ttu-id="13433-111">[**Kapitel 3**](usbx-host-stack-3.md) – innehåller en funktionell översikt över Azure återställnings tider USBX och grundläggande information om USB</span><span class="sxs-lookup"><span data-stu-id="13433-111">[**Chapter 3**](usbx-host-stack-3.md) - provides a functional overview of Azure RTOS USBX and basic information about USB</span></span>

- <span data-ttu-id="13433-112">[**Kapitel 4**](usbx-host-stack-4.md) – information om programmets gränssnitt till Azure återställnings tider-USBX i värd läge</span><span class="sxs-lookup"><span data-stu-id="13433-112">[**Chapter 4**](usbx-host-stack-4.md) - details the application's interface to Azure RTOS USBX in host mode</span></span>

- <span data-ttu-id="13433-113">[**Kapitel 5**](usbx-host-stack-5.md) – beskriver API: erna för värd klasserna för Azure återställnings tider-USBX</span><span class="sxs-lookup"><span data-stu-id="13433-113">[**Chapter 5**](usbx-host-stack-5.md) - describes the APIs of the Azure RTOS USBX Host classes</span></span>

- <span data-ttu-id="13433-114">[**Kapitel 6**](usbx-host-stack-6.md) – beskriver Azure återställnings tider USBX CDC-ECM-klassen</span><span class="sxs-lookup"><span data-stu-id="13433-114">[**Chapter 6**](usbx-host-stack-6.md) - describes the Azure RTOS USBX CDC-ECM class</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="13433-115">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="13433-115">Customer Support Center</span></span>

<span data-ttu-id="13433-116">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="13433-116">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="13433-117">Lämna oss med följande information i ett e-postmeddelande så att vi kan lösa ditt support ärende mer effektivt.</span><span class="sxs-lookup"><span data-stu-id="13433-117">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="13433-118">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="13433-118">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="13433-119">En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="13433-119">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="13433-120">Innehållet i den *_tx_version_id* strängen som finns i filen *tx_port. h* i distributionen.</span><span class="sxs-lookup"><span data-stu-id="13433-120">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="13433-121">Den här strängen ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="13433-121">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="13433-122">Innehållet i RAM-minnet för *_tx_build_options* ulong-variabeln.</span><span class="sxs-lookup"><span data-stu-id="13433-122">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="13433-123">Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.</span><span class="sxs-lookup"><span data-stu-id="13433-123">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
