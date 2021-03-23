---
title: Om användar handboken för Azure återställnings tider NetX Duo
description: Den här guiden innehåller omfattande information om Azure återställnings tider NetX Duo, Microsofts högpresterande IPv4/IPv6-stack med dubbla nätverk.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826238"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="e48c0-103">Om användar handboken för Azure återställnings tider NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e48c0-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="e48c0-104">Den här guiden innehåller omfattande information om Azure återställnings tider NetX Duo, Microsofts högpresterande IPv4/IPv6-stack med dubbla nätverk.</span><span class="sxs-lookup"><span data-stu-id="e48c0-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="e48c0-105">Den är avsedd för inbäddade program varu utvecklare i real tid som är bekanta med grundläggande nätverks koncept, Azure återställnings tider-ThreadX och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="e48c0-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="e48c0-106">Organisation</span><span class="sxs-lookup"><span data-stu-id="e48c0-106">Organization</span></span>

<span data-ttu-id="e48c0-107">[Kapitel 1](chapter1.md) – introducerar Azure återställnings tider netx Duo</span><span class="sxs-lookup"><span data-stu-id="e48c0-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="e48c0-108">[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider netx Duo med ditt ThreadX-program</span><span class="sxs-lookup"><span data-stu-id="e48c0-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="e48c0-109">[Kapitel 3](chapter3.md) – innehåller en funktionell översikt över Azure återställnings tider netx Duo-systemet och grundläggande information om TCP/IP nätverks standarder</span><span class="sxs-lookup"><span data-stu-id="e48c0-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="e48c0-110">[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider netx Duo</span><span class="sxs-lookup"><span data-stu-id="e48c0-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="e48c0-111">[Kapitel 5](chapter5.md) – beskriver nätverks driv rutiner för Azure återställnings tider netx Duo</span><span class="sxs-lookup"><span data-stu-id="e48c0-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="e48c0-112">[Bilaga A](appendix-a.md) – Azure återställnings tider netx Duo-tjänster</span><span class="sxs-lookup"><span data-stu-id="e48c0-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="e48c0-113">[Bilaga B](appendix-b.md) – Azure återställnings tider netx Duo-konstanter</span><span class="sxs-lookup"><span data-stu-id="e48c0-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="e48c0-114">[Bilaga C](appendix-c.md) – Azure återställnings tider netx Duo-datatyper</span><span class="sxs-lookup"><span data-stu-id="e48c0-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="e48c0-115">[Bilaga D](appendix-d.md) – BSD-Compatible socket-API</span><span class="sxs-lookup"><span data-stu-id="e48c0-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="e48c0-116">[Bilaga E](appendix-e.md) -ASCII-diagram</span><span class="sxs-lookup"><span data-stu-id="e48c0-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="e48c0-117">Guide konventioner</span><span class="sxs-lookup"><span data-stu-id="e48c0-117">Guide Conventions</span></span>

<span data-ttu-id="e48c0-118">Kursiv stil – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.</span><span class="sxs-lookup"><span data-stu-id="e48c0-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="e48c0-119">**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.</span><span class="sxs-lookup"><span data-stu-id="e48c0-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e48c0-120">Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="e48c0-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="e48c0-121">Varnings symboler drar uppmärksamhet till situationer som utvecklare bör undvika eftersom de kan orsaka allvarliga fel.</span><span class="sxs-lookup"><span data-stu-id="e48c0-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="e48c0-122">Data typer för Azure återställnings tider-NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e48c0-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="e48c0-123">Förutom de anpassade data typerna för Azure återställnings tider NetX Duo-kontrollen finns det flera särskilda data typer som används i Azure återställnings tider NetX Duo-tjänstens anrops gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="e48c0-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="e48c0-124">Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="e48c0-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="e48c0-125">Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer.</span><span class="sxs-lookup"><span data-stu-id="e48c0-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="e48c0-126">Den exakta implementeringen ärvs från ThreadX och kan hittas i filen ***tx_port. h*** som ingår i ThreadX-distributionen.</span><span class="sxs-lookup"><span data-stu-id="e48c0-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="e48c0-127">Följande är en lista över data typerna för Azure återställnings tider NetX Duo-tjänstens anrop och deras associerade betydelser:</span><span class="sxs-lookup"><span data-stu-id="e48c0-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="e48c0-128">**Uint**: Basic-osignerat heltal.</span><span class="sxs-lookup"><span data-stu-id="e48c0-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="e48c0-129">Den här typen måste ha stöd för 32-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen.</span><span class="sxs-lookup"><span data-stu-id="e48c0-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="e48c0-130">**Ulong**: osignerad lång typ.</span><span class="sxs-lookup"><span data-stu-id="e48c0-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="e48c0-131">Den här typen måste ha stöd för 32-bitars osignerade data.</span><span class="sxs-lookup"><span data-stu-id="e48c0-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="e48c0-132">**Void**: nästan alltid likvärdigt med kompilatorns void-typ.</span><span class="sxs-lookup"><span data-stu-id="e48c0-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="e48c0-133">**Char**: oftast en vanlig 8-bitars tecken typ.</span><span class="sxs-lookup"><span data-stu-id="e48c0-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="e48c0-134">Ytterligare data typer används i Azure återställnings tider-NetX Duo-källan.</span><span class="sxs-lookup"><span data-stu-id="e48c0-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="e48c0-135">De finns antingen i ***tx_port. h** _ eller _ *_nx_port. h_** filer.</span><span class="sxs-lookup"><span data-stu-id="e48c0-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="e48c0-136">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="e48c0-136">Customer Support Center</span></span>

<span data-ttu-id="e48c0-137">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="e48c0-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="e48c0-138">Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:</span><span class="sxs-lookup"><span data-stu-id="e48c0-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="e48c0-139">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="e48c0-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="e48c0-140">En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider NetX Duo som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="e48c0-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="e48c0-141">Innehållet i _tx_version_id-och _nx_version_id-strängar som finns i tx_port. h-och nx_port. h-filerna för distributionen.</span><span class="sxs-lookup"><span data-stu-id="e48c0-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="e48c0-142">De här strängarna ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="e48c0-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="e48c0-143">Innehållet i RAM-minnet för följande ULONG-variabler:</span><span class="sxs-lookup"><span data-stu-id="e48c0-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="e48c0-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="e48c0-144">**_tx_build_options**</span></span>

    <span data-ttu-id="e48c0-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="e48c0-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="e48c0-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="e48c0-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="e48c0-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="e48c0-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="e48c0-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="e48c0-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="e48c0-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="e48c0-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="e48c0-150">Dessa variabler ger oss information om hur dina Azure återställnings tider ThreadX-och Azure återställnings tider NetX Duo-bibliotek skapades.</span><span class="sxs-lookup"><span data-stu-id="e48c0-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="e48c0-151">En spårnings-buffert som samlats in omedelbart efter det att problemet upptäcktes.</span><span class="sxs-lookup"><span data-stu-id="e48c0-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="e48c0-152">Detta åstadkommer du genom att skapa Azure återställnings tider-ThreadX och Azure återställnings tider NetX Duo-bibliotek med TX_ENABLE_EVENT_TRACE och anropa tx_trace_enable med information om spårnings-bufferten.</span><span class="sxs-lookup"><span data-stu-id="e48c0-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
