---
title: Om den här guiden
description: Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX SMP, den inbyggda real tids kärnan i real tid i Microsoft.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2399666b5b4d7c34db50d539e200c90f06f7235f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825446"
---
# <a name="about-this-guide"></a><span data-ttu-id="22f10-103">Om den här guiden</span><span class="sxs-lookup"><span data-stu-id="22f10-103">About This Guide</span></span>

<span data-ttu-id="22f10-104">Den här guiden innehåller omfattande information om Azure återställnings tider ThreadX SMP, den inbyggda real tids kärnan i real tid i Microsoft.</span><span class="sxs-lookup"><span data-stu-id="22f10-104">This guide provides comprehensive information about Azure RTOS ThreadX SMP, the Microsoft high-performance embedded real-time kernel.</span></span>

<span data-ttu-id="22f10-105">Den är avsedd för den inbäddade programutvecklaren i real tid.</span><span class="sxs-lookup"><span data-stu-id="22f10-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="22f10-106">Utvecklaren bör vara bekant med vanliga operativ system funktioner i real tid och programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="22f10-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="22f10-107">Organisation</span><span class="sxs-lookup"><span data-stu-id="22f10-107">Organization</span></span>

| <span data-ttu-id="22f10-108">Kapitel</span><span class="sxs-lookup"><span data-stu-id="22f10-108">Chapter</span></span>       | <span data-ttu-id="22f10-109">Översikt</span><span class="sxs-lookup"><span data-stu-id="22f10-109">Overview</span></span>                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="22f10-110">**Kapitel 1**</span><span class="sxs-lookup"><span data-stu-id="22f10-110">**Chapter 1**</span></span> | <span data-ttu-id="22f10-111">Innehåller en grundläggande översikt över ThreadX SMP och dess relation till inbäddad real tids utveckling.</span><span class="sxs-lookup"><span data-stu-id="22f10-111">Provides a basic overview of ThreadX SMP and its relationship to real-time embedded development.</span></span>           |
| <span data-ttu-id="22f10-112">**Kapitel 2**</span><span class="sxs-lookup"><span data-stu-id="22f10-112">**Chapter 2**</span></span> | <span data-ttu-id="22f10-113">Innehåller grundläggande steg för att installera och använda ThreadX SMP i ditt program direkt från *lådan*.</span><span class="sxs-lookup"><span data-stu-id="22f10-113">Gives the basic steps to install and use ThreadX SMP in your application right *out of the box*.</span></span>           |
| <span data-ttu-id="22f10-114">**Kapitel 3**</span><span class="sxs-lookup"><span data-stu-id="22f10-114">**Chapter 3**</span></span> | <span data-ttu-id="22f10-115">Beskriver i detalj den funktionella driften av ThreadX SMP, den högpresterande SMP-kärnan i real tid.</span><span class="sxs-lookup"><span data-stu-id="22f10-115">Describes in detail the functional operation of ThreadX SMP, the high-performance real-time SMP kernel.</span></span>    |
| <span data-ttu-id="22f10-116">**Kapitel 4**</span><span class="sxs-lookup"><span data-stu-id="22f10-116">**Chapter 4**</span></span> | <span data-ttu-id="22f10-117">Information om programmets gränssnitt till ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="22f10-117">Details the application’s interface to ThreadX SMP.</span></span>                                                        |
| <span data-ttu-id="22f10-118">**Kapitel 5**</span><span class="sxs-lookup"><span data-stu-id="22f10-118">**Chapter 5**</span></span> | <span data-ttu-id="22f10-119">Beskriver hur du skriver I/O-drivrutiner för ThreadX SMP-program.</span><span class="sxs-lookup"><span data-stu-id="22f10-119">Describes writing I/O drivers for ThreadX SMP applications.</span></span>                                                |
| <span data-ttu-id="22f10-120">**Kapitel 6**</span><span class="sxs-lookup"><span data-stu-id="22f10-120">**Chapter 6**</span></span> | <span data-ttu-id="22f10-121">Beskriver det demonstrations program som medföljer varje ThreadX SMP-processors support paket.</span><span class="sxs-lookup"><span data-stu-id="22f10-121">Describes the demonstration application that is supplied with every ThreadX SMP processor support package.</span></span> |
| <span data-ttu-id="22f10-122">**Bilaga A**</span><span class="sxs-lookup"><span data-stu-id="22f10-122">**Appendix A**</span></span> | <span data-ttu-id="22f10-123">ThreadX SMP-API</span><span class="sxs-lookup"><span data-stu-id="22f10-123">ThreadX SMP API</span></span>        |
| <span data-ttu-id="22f10-124">**Bilaga B**</span><span class="sxs-lookup"><span data-stu-id="22f10-124">**Appendix B**</span></span> | <span data-ttu-id="22f10-125">ThreadX SMP-konstanter</span><span class="sxs-lookup"><span data-stu-id="22f10-125">ThreadX SMP constants</span></span>  |
| <span data-ttu-id="22f10-126">**Bilaga C**</span><span class="sxs-lookup"><span data-stu-id="22f10-126">**Appendix C**</span></span> | <span data-ttu-id="22f10-127">ThreadX SMP-datatyper</span><span class="sxs-lookup"><span data-stu-id="22f10-127">ThreadX SMP data types</span></span> |
| <span data-ttu-id="22f10-128">**Bilaga D**</span><span class="sxs-lookup"><span data-stu-id="22f10-128">**Appendix D**</span></span> | <span data-ttu-id="22f10-129">ASCII-diagram</span><span class="sxs-lookup"><span data-stu-id="22f10-129">ASCII chart</span></span>            |

## <a name="guide-conventions"></a><span data-ttu-id="22f10-130">Guide konventioner</span><span class="sxs-lookup"><span data-stu-id="22f10-130">Guide Conventions</span></span>

- <span data-ttu-id="22f10-131">*Kursiv stil*  -  *teckensnittet anger bok titlar, betonar viktiga ord och indikerar variabler.*</span><span class="sxs-lookup"><span data-stu-id="22f10-131">*Italics* - *typeface denotes book titles, emphasizes important words, and indicates variables.*</span></span>
- <span data-ttu-id="22f10-132">**Fetstil**  -  **teckensnittet anger fil namn, viktiga ord och betonar viktiga ord och variabler.**</span><span class="sxs-lookup"><span data-stu-id="22f10-132">**Boldface** - **typeface denotes file names, key words, and further emphasizes important words and variables.**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22f10-133">Informations symboler drar uppmärksamheten till viktig eller ytterligare information som kan påverka prestandan eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="22f10-133">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="22f10-134">Varnings symboler drar uppmärksamhet till situationer där utvecklare bör ta hand om att undvika att de kan orsaka allvarliga fel.</span><span class="sxs-lookup"><span data-stu-id="22f10-134">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="threadx-smp-data-types"></a><span data-ttu-id="22f10-135">ThreadX SMP-datatyper</span><span class="sxs-lookup"><span data-stu-id="22f10-135">ThreadX SMP Data Types</span></span>

<span data-ttu-id="22f10-136">Förutom de anpassade data typerna för SMP-ThreadX, finns det en serie särskilda data typer som används i ThreadX SMP-tjänstens anrops gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="22f10-136">In addition to the custom ThreadX SMP control structure data types, there are a series of special data types that are used in ThreadX SMP service call interfaces.</span></span> <span data-ttu-id="22f10-137">Dessa särskilda data typer mappar direkt till data typer för den underliggande C-kompilatorn.</span><span class="sxs-lookup"><span data-stu-id="22f10-137">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="22f10-138">Detta görs för att säkerställa portabilitet mellan olika C-kompilatorer.</span><span class="sxs-lookup"><span data-stu-id="22f10-138">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="22f10-139">Du hittar den exakta implementeringen i filen ***tx_port. h*** som finns på distributions disken.</span><span class="sxs-lookup"><span data-stu-id="22f10-139">The exact implementation can be found in the ***tx_port.h*** file included on the distribution disk.</span></span>

<span data-ttu-id="22f10-140">Följande är en lista över ThreadX-data typer för SMP-tjänsten och deras associerade betydelser:</span><span class="sxs-lookup"><span data-stu-id="22f10-140">The following is a list of ThreadX SMP service call data types and their associated meanings:</span></span>

| <span data-ttu-id="22f10-141">Datatyp</span><span class="sxs-lookup"><span data-stu-id="22f10-141">Data Type</span></span>          | <span data-ttu-id="22f10-142">Innebörd</span><span class="sxs-lookup"><span data-stu-id="22f10-142">Meaning</span></span>                                                          |
| --------- | --------------------------------------------------------- |
| <span data-ttu-id="22f10-143">**UINT**</span><span class="sxs-lookup"><span data-stu-id="22f10-143">**UINT**</span></span>  | <span data-ttu-id="22f10-144">Basic-osignerat heltal.</span><span class="sxs-lookup"><span data-stu-id="22f10-144">Basic unsigned integer.</span></span> <span data-ttu-id="22f10-145">Den här typen måste ha stöd för 8-bitars osignerade data. den är dock mappad till den mest användbara osignerade data typen.</span><span class="sxs-lookup"><span data-stu-id="22f10-145">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="22f10-146">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="22f10-146">**ULONG**</span></span> | <span data-ttu-id="22f10-147">Osignerad lång typ.</span><span class="sxs-lookup"><span data-stu-id="22f10-147">Unsigned long type.</span></span> <span data-ttu-id="22f10-148">Den här typen måste ha stöd för 32-bitars osignerade data.</span><span class="sxs-lookup"><span data-stu-id="22f10-148">This type must support 32-bit unsigned data.</span></span>                                                                     |
| <span data-ttu-id="22f10-149">**VOID**</span><span class="sxs-lookup"><span data-stu-id="22f10-149">**VOID**</span></span>  | <span data-ttu-id="22f10-150">Nästan alltid ekvivalent med kompilatorns void-typ.</span><span class="sxs-lookup"><span data-stu-id="22f10-150">Almost always equivalent to the compiler’s void type.</span></span>                                                                                |
| <span data-ttu-id="22f10-151">**HÄNGANDE**</span><span class="sxs-lookup"><span data-stu-id="22f10-151">**CHAR**</span></span>  | <span data-ttu-id="22f10-152">Oftast en vanlig 8-bitars tecken typ.</span><span class="sxs-lookup"><span data-stu-id="22f10-152">Most often a standard 8-bit character type.</span></span>                                                                                          |

<span data-ttu-id="22f10-153">Ytterligare data typer används i ThreadX SMP-källa.</span><span class="sxs-lookup"><span data-stu-id="22f10-153">Additional data types are used within the ThreadX SMP source.</span></span> <span data-ttu-id="22f10-154">De finns också i filen ***tx_port. h*** .</span><span class="sxs-lookup"><span data-stu-id="22f10-154">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="22f10-155">Kund Support Center</span><span class="sxs-lookup"><span data-stu-id="22f10-155">Customer Support Center</span></span>

<span data-ttu-id="22f10-156">Support-e-post: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) webb sida: Azure.com/RTOS</span><span class="sxs-lookup"><span data-stu-id="22f10-156">Support email: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Web page: azure.com/rtos</span></span>

### <a name="latest-product-information"></a><span data-ttu-id="22f10-157">Senaste produkt information</span><span class="sxs-lookup"><span data-stu-id="22f10-157">Latest Product Information</span></span>

<span data-ttu-id="22f10-158">Besök azure.com/rtos-webbplatsen och välj meny alternativet support för att hitta den senaste informationen om onlinesupport, inklusive information om de senaste ThreadX SMP-produktsortimenten.</span><span class="sxs-lookup"><span data-stu-id="22f10-158">Visit the azure.com/rtos web site and select the “Support” menu option to find the latest online support information, including information about the latest ThreadX SMP product releases.</span></span>

### <a name="what-we-need-from-you"></a><span data-ttu-id="22f10-159">Vad vi behöver från dig</span><span class="sxs-lookup"><span data-stu-id="22f10-159">What We Need From You</span></span>

<span data-ttu-id="22f10-160">Lämna oss med följande information i ett e-postmeddelande så att vi effektivare kan lösa support förfrågan:</span><span class="sxs-lookup"><span data-stu-id="22f10-160">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="22f10-161">En detaljerad beskrivning av problemet, inklusive frekvensen av händelser och huruvida det kan återskapas tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="22f10-161">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="22f10-162">En detaljerad beskrivning av eventuella ändringar i programmet och/eller ThreadX-SMP som föregåde problemet.</span><span class="sxs-lookup"><span data-stu-id="22f10-162">A detailed description of any changes to the application and/or ThreadX SMP that preceded the problem.</span></span>
3. <span data-ttu-id="22f10-163">Innehållet i ***_tx_version_id** _-strängen som finns i filen _ *_tx_port. h_** i distributionen.</span><span class="sxs-lookup"><span data-stu-id="22f10-163">The contents of the ***_tx_version_id** _ string found in the _ *_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="22f10-164">Den här strängen ger oss värdefull information om din kör tids miljö.</span><span class="sxs-lookup"><span data-stu-id="22f10-164">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="22f10-165">Innehållet i RAM-minnet för ***_tx_build_options*** ulong-variabeln.</span><span class="sxs-lookup"><span data-stu-id="22f10-165">The contents in RAM of the ***_tx_build_options*** ULONG variable.</span></span> <span data-ttu-id="22f10-166">Den här variabeln ger oss information om hur ditt ThreadX SMP-bibliotek byggdes.</span><span class="sxs-lookup"><span data-stu-id="22f10-166">This variable will give us information on how your ThreadX SMP library was built.</span></span>

### <a name="where-to-send-comments-about-this-guide"></a><span data-ttu-id="22f10-167">Var du ska skicka kommentarer om den här guiden</span><span class="sxs-lookup"><span data-stu-id="22f10-167">Where to Send Comments About This Guide</span></span>

<span data-ttu-id="22f10-168">Skicka kommentarer och förslag till kund Support Center vid [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Skriv "THREADX SMP user guide" på ämnes raden.</span><span class="sxs-lookup"><span data-stu-id="22f10-168">Email any comments and suggestions to the Customer Support Center at [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Enter “ThreadX SMP User Guide” in the subject line.</span></span>
