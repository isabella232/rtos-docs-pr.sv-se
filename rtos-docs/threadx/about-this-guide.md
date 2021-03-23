---
title: Om Azure återställnings tider ThreadX-guiden
description: Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX, Microsoft Real-Performance-kärnan i real tid.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826592"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="fc3e1-103">Om Azure återställnings tider ThreadX-guiden</span><span class="sxs-lookup"><span data-stu-id="fc3e1-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="fc3e1-104">Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX, Microsoft Real-Performance-kärnan i real tid.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="fc3e1-105">Den är avsedd för den inbäddade programutvecklaren i real tid.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="fc3e1-106">Utvecklaren bör vara bekant med vanliga operativ system funktioner i real tid och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="fc3e1-107">Organisation</span><span class="sxs-lookup"><span data-stu-id="fc3e1-107">Organization</span></span>

<span data-ttu-id="fc3e1-108">[Kapitel 1](chapter1.md) – innehåller en grundläggande översikt över Azure återställnings tider-ThreadX och dess relation till inbäddad real tids utveckling</span><span class="sxs-lookup"><span data-stu-id="fc3e1-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="fc3e1-109">[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-ThreadX i ditt program direkt från *lådan*</span><span class="sxs-lookup"><span data-stu-id="fc3e1-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="fc3e1-110">[Kapitel 3](chapter3.md) – beskrivs i detalj den funktionella driften av Azure återställnings tider ThreadX, real tids kärnan i real tid</span><span class="sxs-lookup"><span data-stu-id="fc3e1-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="fc3e1-111">[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider ThreadX</span><span class="sxs-lookup"><span data-stu-id="fc3e1-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="fc3e1-112">[Kapitel 5](chapter5.md) – beskriver hur du skriver I/O-drivrutiner för Azure återställnings tider ThreadX-program</span><span class="sxs-lookup"><span data-stu-id="fc3e1-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="fc3e1-113">[Kapitel 6](chapter6.md) – beskriver demonstrations programmet som medföljer varje Azure återställnings tider ThreadX processor support paket</span><span class="sxs-lookup"><span data-stu-id="fc3e1-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="fc3e1-114">[Bilaga A](appendix-a.md) – Azure återställnings tider THREADX-API</span><span class="sxs-lookup"><span data-stu-id="fc3e1-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="fc3e1-115">[Bilaga B](appendix-b.md) – Azure återställnings tider ThreadX-konstanter</span><span class="sxs-lookup"><span data-stu-id="fc3e1-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="fc3e1-116">[Bilaga C](appendix-c.md) – data typer för Azure återställnings tider-ThreadX</span><span class="sxs-lookup"><span data-stu-id="fc3e1-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="fc3e1-117">[Bilaga D](appendix-d.md) – ASCII-diagram</span><span class="sxs-lookup"><span data-stu-id="fc3e1-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="fc3e1-118">Guide konventioner</span><span class="sxs-lookup"><span data-stu-id="fc3e1-118">Guide Conventions</span></span>

<span data-ttu-id="fc3e1-119">*Kursiv stil* -teckensnitt anger bok titlar, betonar viktiga ord och indikerar parametrar.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="fc3e1-120">**Fetstil** – typsnitt anger nyckelord, konstanter, typ namn, gränssnitts element, variabel namn och betonar viktiga ord.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="fc3e1-121">***Kursiv stil och fetstil*** – typsnitt anger fil namn och funktions namn.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc3e1-122">Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="fc3e1-123">Varnings symboler drar uppmärksamhet till situationer där utvecklare bör ta hand om att undvika att de kan orsaka allvarliga fel.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="fc3e1-124">Data typer för Azure dataåterställnings tiders-ThreadX</span><span class="sxs-lookup"><span data-stu-id="fc3e1-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="fc3e1-125">Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-ThreadX finns det en serie särskilda data typer som används i Azure återställnings tider ThreadX service Call-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="fc3e1-126">Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="fc3e1-127">Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="fc3e1-128">Du hittar den exakta implementeringen i filen ***tx_port. h*** som ingår i källan.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="fc3e1-129">Följande är en lista över data typer för Azure återställnings tider ThreadX service Call och deras associerade betydelser:</span><span class="sxs-lookup"><span data-stu-id="fc3e1-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="fc3e1-130">Datatyp</span><span class="sxs-lookup"><span data-stu-id="fc3e1-130">Data type</span></span>  | <span data-ttu-id="fc3e1-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fc3e1-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="fc3e1-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="fc3e1-132">**UINT**</span></span> | <span data-ttu-id="fc3e1-133">Basic-osignerat heltal.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-133">Basic unsigned integer.</span></span> <span data-ttu-id="fc3e1-134">Den här typen måste ha stöd för 8-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="fc3e1-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="fc3e1-135">**ULONG**</span></span> | <span data-ttu-id="fc3e1-136">Osignerad lång typ.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-136">Unsigned long type.</span></span> <span data-ttu-id="fc3e1-137">Den här typen måste ha stöd för 32-bitars osignerade data.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="fc3e1-138">**VOID**</span><span class="sxs-lookup"><span data-stu-id="fc3e1-138">**VOID**</span></span> | <span data-ttu-id="fc3e1-139">Nästan alltid ekvivalent med kompilatorns void-typ.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="fc3e1-140">**HÄNGANDE**</span><span class="sxs-lookup"><span data-stu-id="fc3e1-140">**CHAR**</span></span> | <span data-ttu-id="fc3e1-141">Oftast en vanlig 8-bitars tecken typ.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="fc3e1-142">Ytterligare data typer används i Azure återställnings tider ThreadX-källan.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="fc3e1-143">De finns också i filen ***tx_port. h*** .</span><span class="sxs-lookup"><span data-stu-id="fc3e1-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="fc3e1-144">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="fc3e1-144">Customer Support Center</span></span>

<span data-ttu-id="fc3e1-145">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="fc3e1-146">Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:</span><span class="sxs-lookup"><span data-stu-id="fc3e1-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="fc3e1-147">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="fc3e1-148">En detaljerad beskrivning av eventuella ändringar i programmet och/eller Azure återställnings tider-ThreadX som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="fc3e1-149">Innehållet i den *_tx_version_id* strängen som finns i filen *tx_port. h* i distributionen.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="fc3e1-150">Den här strängen ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="fc3e1-151">Innehållet i RAM-minnet för **_tx_build_options** **ulong** -variabeln.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="fc3e1-152">Den här variabeln ger oss information om hur ditt Azure återställnings tider ThreadX-bibliotek har skapats.</span><span class="sxs-lookup"><span data-stu-id="fc3e1-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
