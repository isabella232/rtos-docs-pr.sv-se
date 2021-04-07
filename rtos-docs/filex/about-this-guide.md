---
title: Användar handbok för Azure återställnings tider FileX
description: Den här guiden innehåller omfattande information om Azure återställnings tider FileX, real tids fil systemet med höga prestanda från Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 640d9ed4c8037d3af6c5f45158c9496ad1258a3c
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550107"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="5bb1d-103">Om den här användar handboken för FileX</span><span class="sxs-lookup"><span data-stu-id="5bb1d-103">About This FileX User Guide</span></span>

<span data-ttu-id="5bb1d-104">Den här guiden innehåller omfattande information om Azure återställnings tider FileX, det högpresterande inbäddade fil systemet i real tid från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="5bb1d-105">För att få ut mesta möjliga av den här guiden bör du vara bekant med standard operativ system funktioner i real tid, FAT-filsystemtjänster och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="5bb1d-106">Organisation</span><span class="sxs-lookup"><span data-stu-id="5bb1d-106">Organization</span></span>

<span data-ttu-id="5bb1d-107">[Kapitel 1](chapter1.md) – introducerar Azure återställnings tider FileX</span><span class="sxs-lookup"><span data-stu-id="5bb1d-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="5bb1d-108">[Kapitel 2](chapter2.md) – innehåller grundläggande steg för att installera och använda Azure återställnings tider-FileX med ditt Azure återställnings tider ThreadX-program</span><span class="sxs-lookup"><span data-stu-id="5bb1d-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="5bb1d-109">[Kapitel 3](chapter3.md) – innehåller en funktionell översikt över Azure återställnings tider FileX-systemet och grundläggande information om fat-format för fil system</span><span class="sxs-lookup"><span data-stu-id="5bb1d-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="5bb1d-110">[Kapitel 4](chapter4.md) – information om programmets gränssnitt till Azure återställnings tider FileX</span><span class="sxs-lookup"><span data-stu-id="5bb1d-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="5bb1d-111">[Kapitel 5](chapter5.md) – beskriver den tillhandahållna Azure återställnings tider FileX ram-drivrutinen och hur du skriver egna anpassade Azure återställnings tider FileX-drivrutiner</span><span class="sxs-lookup"><span data-stu-id="5bb1d-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="5bb1d-112">[Kapitel 6](chapter6.md) – beskriver den feltoleranta modulen för Azure återställnings tider FileX</span><span class="sxs-lookup"><span data-stu-id="5bb1d-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="5bb1d-113">[Bilaga A](appendix-a.md) – Azure återställnings tider FileX-tjänster</span><span class="sxs-lookup"><span data-stu-id="5bb1d-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="5bb1d-114">[Bilaga B](appendix-b.md) – Azure återställnings tider FileX-konstanter</span><span class="sxs-lookup"><span data-stu-id="5bb1d-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="5bb1d-115">[Bilaga C](appendix-c.md) – data typer för Azure återställnings tider-FileX</span><span class="sxs-lookup"><span data-stu-id="5bb1d-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="5bb1d-116">[Bilaga D](appendix-d.md) – ASCII-diagram</span><span class="sxs-lookup"><span data-stu-id="5bb1d-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="5bb1d-117">Guide konventioner</span><span class="sxs-lookup"><span data-stu-id="5bb1d-117">Guide Conventions</span></span>

<span data-ttu-id="5bb1d-118">*Kursiv stil* – teckensnittet noterar bok titlar, betonar viktiga ord och indikerar variabler.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="5bb1d-119">**Fetstil** – typsnitt anger fil namn, viktiga ord och betonar viktiga ord och variabler.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="5bb1d-120">Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bb1d-121">Varnings symboler drar uppmärksamhet till situationer som utvecklare bör undvika eftersom de kan orsaka allvarliga fel.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="5bb1d-122">FileX data typer</span><span class="sxs-lookup"><span data-stu-id="5bb1d-122">FileX Data Types</span></span>

<span data-ttu-id="5bb1d-123">Förutom de anpassade data typerna för kontroll strukturen i Azure återställnings tider-FileX, finns det en serie särskilda data typer som används i Azure återställnings tider FileX service Call-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="5bb1d-124">Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="5bb1d-125">Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="5bb1d-126">Den exakta implementeringen ärvs från Azure återställnings tider ThreadX och finns i filen tx_port. h som ingår i Azure återställnings tider ThreadX-distributionen.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="5bb1d-127">Följande är en lista över data typer för Azure återställnings tider FileX service Call och deras associerade betydelser.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>

| <span data-ttu-id="5bb1d-128">Typ</span><span class="sxs-lookup"><span data-stu-id="5bb1d-128">Type</span></span>  | <span data-ttu-id="5bb1d-129">Description</span><span class="sxs-lookup"><span data-stu-id="5bb1d-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="5bb1d-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-130">**UINT**</span></span> | <span data-ttu-id="5bb1d-131">Basic-osignerat heltal.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-131">Basic unsigned integer.</span></span> <span data-ttu-id="5bb1d-132">Den här typen måste ha stöd för 8-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="5bb1d-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-133">**ULONG**</span></span> | <span data-ttu-id="5bb1d-134">Osignerad lång typ.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-134">Unsigned long type.</span></span> <span data-ttu-id="5bb1d-135">Den här typen måste ha stöd för 32-bitars osignerade data.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="5bb1d-136">**VOID**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-136">**VOID**</span></span> | <span data-ttu-id="5bb1d-137">Nästan alltid ekvivalent med kompilatorns void-typ.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="5bb1d-138">**HÄNGANDE**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-138">**CHAR**</span></span> | <span data-ttu-id="5bb1d-139">Oftast en vanlig 8-bitars tecken typ.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="5bb1d-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-140">**ULONG64**</span></span> | <span data-ttu-id="5bb1d-141">64-bit data typ med osignerat heltal.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="5bb1d-142">Ytterligare data typer används i FileX-källan.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="5bb1d-143">De finns antingen i ***tx_port. h** _ eller _ *_fx_port. h_** filer.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="5bb1d-144">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="5bb1d-144">Customer Support Center</span></span>

<span data-ttu-id="5bb1d-145">Skicka in ett support ärende via Azure Portal om du har frågor eller hjälp med att följa stegen här.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="5bb1d-146">Lämna oss med följande information i ett e-postmeddelande så att vi kan lösa ditt support ärende mer effektivt.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="5bb1d-147">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="5bb1d-148">En detaljerad beskrivning av eventuella ändringar i programmet och/eller FileX som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="5bb1d-149">Innehållet i _tx_version_id-och _fx_version_id-strängar som finns i \***tx_port. h**_ -och _ \*_fx_port. h_\*\*-filerna i distributionen.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="5bb1d-150">De här strängarna ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="5bb1d-151">Innehållet i RAM-minnet för följande **ulong** -variabler.</span><span class="sxs-lookup"><span data-stu-id="5bb1d-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="5bb1d-152">Dessa variabler ger oss information om hur dina ThreadX-och FileX-bibliotek skapades:</span><span class="sxs-lookup"><span data-stu-id="5bb1d-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="5bb1d-153">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-153">**_tx_build_options**</span></span>

    <span data-ttu-id="5bb1d-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="5bb1d-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="5bb1d-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="5bb1d-156">**_fx_system_build_options3**</span></span>
