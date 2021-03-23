---
title: Om användar handboken för Azure återställnings tider NetX
description: Den här guiden innehåller omfattande information om Azure återställnings tider NetX, Microsofts högpresterande nätverks stack.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8e1c23892c4360ddc8783b04ae8f23e371899f1d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826919"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="122d6-103">Om användar handboken för Azure återställnings tider NetX</span><span class="sxs-lookup"><span data-stu-id="122d6-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="122d6-104">Den här guiden innehåller omfattande information om Azure återställnings tider NetX, Microsofts högpresterande nätverks stack.</span><span class="sxs-lookup"><span data-stu-id="122d6-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="122d6-105">Den är avsedd för inbäddade program varu utvecklare i real tid som är bekanta med grundläggande nätverks koncept, Azure återställnings tider-ThreadX och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="122d6-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="122d6-106">Organisation</span><span class="sxs-lookup"><span data-stu-id="122d6-106">Organization</span></span>

<span data-ttu-id="122d6-107">[Kapitel 1](chapter1.md) – introducerar Azure återställnings tider netx</span><span class="sxs-lookup"><span data-stu-id="122d6-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="122d6-108">[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-netx med ditt ThreadX-program.</span><span class="sxs-lookup"><span data-stu-id="122d6-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="122d6-109">[Kapitel 3](chapter3.md) – innehåller en funktionell översikt över Azure återställnings tider netx-systemet och grundläggande information om TCP/IP-nätverksfunktioner.</span><span class="sxs-lookup"><span data-stu-id="122d6-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="122d6-110">[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider netx.</span><span class="sxs-lookup"><span data-stu-id="122d6-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="122d6-111">[Kapitel 5](chapter5.md) – beskriver nätverks driv rutiner för Azure återställnings tider netx.</span><span class="sxs-lookup"><span data-stu-id="122d6-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="122d6-112">[Bilaga A](appendix-a.md) – Azure återställnings tider netx-tjänster</span><span class="sxs-lookup"><span data-stu-id="122d6-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="122d6-113">[Bilaga B](appendix-b.md) – Azure återställnings tider netx-konstanter</span><span class="sxs-lookup"><span data-stu-id="122d6-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="122d6-114">[Bilaga C](appendix-c.md) – data typer för Azure återställnings tider-netx</span><span class="sxs-lookup"><span data-stu-id="122d6-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="122d6-115">[Bilaga D](appendix-d.md) – BSD-Compatible socket-API</span><span class="sxs-lookup"><span data-stu-id="122d6-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="122d6-116">[Bilaga E](appendix-e.md) -ASCII-diagram</span><span class="sxs-lookup"><span data-stu-id="122d6-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="122d6-117">Data typer för Azure dataåterställnings tiders-NetX</span><span class="sxs-lookup"><span data-stu-id="122d6-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="122d6-118">Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-NetX, finns det flera särskilda data typer som används i Azure återställnings tider NetX service Call-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="122d6-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="122d6-119">Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="122d6-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="122d6-120">Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer.</span><span class="sxs-lookup"><span data-stu-id="122d6-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="122d6-121">Den exakta implementeringen ärvs från ThreadX och kan hittas i filen ***tx_port. h*** som ingår i ThreadX-distributionen.</span><span class="sxs-lookup"><span data-stu-id="122d6-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="122d6-122">Följande är en lista över data typer för Azure återställnings tider NetX service Call och deras associerade betydelser:</span><span class="sxs-lookup"><span data-stu-id="122d6-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <!-- -->    | <!-- -->    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="122d6-123">**UINT**</span><span class="sxs-lookup"><span data-stu-id="122d6-123">**UINT**</span></span>  | <span data-ttu-id="122d6-124">Basic-osignerat heltal.</span><span class="sxs-lookup"><span data-stu-id="122d6-124">Basic unsigned integer.</span></span> <span data-ttu-id="122d6-125">Den här typen måste ha stöd för 32-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen.</span><span class="sxs-lookup"><span data-stu-id="122d6-125">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="122d6-126">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="122d6-126">**ULONG**</span></span> | <span data-ttu-id="122d6-127">Osignerad lång typ.</span><span class="sxs-lookup"><span data-stu-id="122d6-127">Unsigned long type.</span></span> <span data-ttu-id="122d6-128">Den här typen måste ha stöd för 32-bitars osignerade data.</span><span class="sxs-lookup"><span data-stu-id="122d6-128">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="122d6-129">**VOID**</span><span class="sxs-lookup"><span data-stu-id="122d6-129">**VOID**</span></span>  | <span data-ttu-id="122d6-130">Nästan alltid ekvivalent med kompilatorns void-typ.</span><span class="sxs-lookup"><span data-stu-id="122d6-130">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="122d6-131">**HÄNGANDE**</span><span class="sxs-lookup"><span data-stu-id="122d6-131">**CHAR**</span></span>  | <span data-ttu-id="122d6-132">Oftast en vanlig 8-bitars tecken typ.</span><span class="sxs-lookup"><span data-stu-id="122d6-132">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="122d6-133">Ytterligare data typer används i Azure återställnings tider NetX-källan.</span><span class="sxs-lookup"><span data-stu-id="122d6-133">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="122d6-134">De finns antingen i ***tx_port. h** _ eller _ *_nx_port. h_** filer.</span><span class="sxs-lookup"><span data-stu-id="122d6-134">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="122d6-135">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="122d6-135">Customer Support Center</span></span>

<span data-ttu-id="122d6-136">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="122d6-136">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="122d6-137">Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:</span><span class="sxs-lookup"><span data-stu-id="122d6-137">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="122d6-138">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="122d6-138">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="122d6-139">En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-NetX som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="122d6-139">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="122d6-140">Innehållet i **_tx_version_id** -och **_nx_version_id** -strängar som finns i **_tx_port. h_*_-och _*_nx_port. h_** -filerna för distributionen.</span><span class="sxs-lookup"><span data-stu-id="122d6-140">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="122d6-141">De här strängarna ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="122d6-141">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="122d6-142">Innehållet i RAM-minnet för följande **ulong** -variabler:</span><span class="sxs-lookup"><span data-stu-id="122d6-142">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="122d6-143">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="122d6-143">**_tx_build_options**</span></span>

    <span data-ttu-id="122d6-144">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="122d6-144">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="122d6-145">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="122d6-145">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="122d6-146">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="122d6-146">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="122d6-147">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="122d6-147">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="122d6-148">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="122d6-148">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="122d6-149">Dessa variabler ger oss information om hur dina Azure återställnings tider ThreadX-och Azure återställnings tider NetX-bibliotek skapades.</span><span class="sxs-lookup"><span data-stu-id="122d6-149">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="122d6-150">En spårnings-buffert som samlats in omedelbart efter det att problemet upptäcktes.</span><span class="sxs-lookup"><span data-stu-id="122d6-150">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="122d6-151">Detta åstadkommer du genom att skapa Azure återställnings tider-ThreadX och Azure återställnings tider NetX-biblioteken med **TX_ENABLE_EVENT_TRACE** och anropa **tx_trace_enable** med information om spårnings-bufferten.</span><span class="sxs-lookup"><span data-stu-id="122d6-151">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="122d6-152">Mer information finns i användar handboken för Azure återställnings tider TraceX.</span><span class="sxs-lookup"><span data-stu-id="122d6-152">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
