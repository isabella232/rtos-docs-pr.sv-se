---
title: Förstå Azure RTOS FileX
description: Azure RTOS FileX är ett FAT-kompatibelt filsystem (File Allocation Table) med höga prestanda som är helt integrerat med Azure RTOS ThreadX och tillgängligt för alla processorer som stöds. Precis Azure RTOS ThreadX är Azure RTOS FileX utformat för att ha ett litet fotavtryck och höga prestanda, vilket gör det idealiskt för dagens djupt inbäddade program som kräver filhanteringsåtgärder. FileX stöder de flesta fysiska media, inklusive RAM, Azure RTOS USBX, SD-KORT och UTFrågeminnen/NOR-flashminnen via Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171361"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="d7e53-105">Översikt över Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="d7e53-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="d7e53-106">Azure RTOS FileX Embedded-filsystemet är Azure RTOS avancerade lösning i branschklass för Microsoft FAT-filformat, särskilt utformad för djupt inbäddade, realtidsbaserade och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="d7e53-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="d7e53-107">Azure RTOS FileX stöder alla Microsofts filformat, inklusive FAT12, FAT16, FAT32 och exFAT.</span><span class="sxs-lookup"><span data-stu-id="d7e53-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="d7e53-108">FileX erbjuder även valfri feltolerans och FLASH-utslitning via en tilläggsprodukt som [kallas Azure RTOS LevelX.](https://docs.microsoft.com/azure/rtos/levelx/)</span><span class="sxs-lookup"><span data-stu-id="d7e53-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="d7e53-109">Allt detta i kombination med ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS FileX till det perfekta valet för de mest krävande inbäddade IoT-programmen.</span><span class="sxs-lookup"><span data-stu-id="d7e53-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="d7e53-110">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="d7e53-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="d7e53-111">Media Services</span><span class="sxs-lookup"><span data-stu-id="d7e53-111">Media Services</span></span>

- <span data-ttu-id="d7e53-112">FAT 12/16/32 och exFAT-stöd</span><span class="sxs-lookup"><span data-stu-id="d7e53-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="d7e53-113">Minimalt 6 kB FLASH, 2,5 kB RAM</span><span class="sxs-lookup"><span data-stu-id="d7e53-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="d7e53-114">Slutföra tjänster för medieåtkomst</span><span class="sxs-lookup"><span data-stu-id="d7e53-114">Complete media access services</span></span>
- <span data-ttu-id="d7e53-115">Obegränsat antal medieinstanser</span><span class="sxs-lookup"><span data-stu-id="d7e53-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="d7e53-116">Enkelt gränssnitt för läs-/skrivdrivrutiner för logisk sektor</span><span class="sxs-lookup"><span data-stu-id="d7e53-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="d7e53-117">Stöd för flera partitioner</span><span class="sxs-lookup"><span data-stu-id="d7e53-117">Multiple partition support</span></span>
- <span data-ttu-id="d7e53-118">Cache för logisk sektor</span><span class="sxs-lookup"><span data-stu-id="d7e53-118">Logical sector cache</span></span>
- <span data-ttu-id="d7e53-119">FAT-postcache</span><span class="sxs-lookup"><span data-stu-id="d7e53-119">FAT entry cache</span></span>
- <span data-ttu-id="d7e53-120">Valfritt stöd för feltolerans</span><span class="sxs-lookup"><span data-stu-id="d7e53-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="d7e53-121">Uppskjuten sekundär FAT-uppdatering</span><span class="sxs-lookup"><span data-stu-id="d7e53-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="d7e53-122">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d7e53-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="d7e53-123">Intuitiva API:er för medieåtkomst, inklusive:</span><span class="sxs-lookup"><span data-stu-id="d7e53-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="d7e53-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="d7e53-124">fx_media_open</span></span>
  - <span data-ttu-id="d7e53-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="d7e53-125">fx_media_close</span></span>
  - <span data-ttu-id="d7e53-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="d7e53-126">fx_media_format</span></span>
  - <span data-ttu-id="d7e53-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="d7e53-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="d7e53-128">Directory Services</span><span class="sxs-lookup"><span data-stu-id="d7e53-128">Directory Services</span></span>

- <span data-ttu-id="d7e53-129">Upp till 256 bytesökvägar</span><span class="sxs-lookup"><span data-stu-id="d7e53-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="d7e53-130">Långa och 8.3-katalognamn som stöds</span><span class="sxs-lookup"><span data-stu-id="d7e53-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="d7e53-131">Katalog create & delete</span><span class="sxs-lookup"><span data-stu-id="d7e53-131">Directory create & delete</span></span>
- <span data-ttu-id="d7e53-132">Katalognavigering och traverserning</span><span class="sxs-lookup"><span data-stu-id="d7e53-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="d7e53-133">Hantering av katalogattribut</span><span class="sxs-lookup"><span data-stu-id="d7e53-133">Directory attributes management</span></span>
- <span data-ttu-id="d7e53-134">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d7e53-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="d7e53-135">Intuitiva katalogåtkomst-API:er, inklusive:</span><span class="sxs-lookup"><span data-stu-id="d7e53-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="d7e53-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="d7e53-136">fx_directory_create</span></span>
  - <span data-ttu-id="d7e53-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="d7e53-137">fx_directory_delete</span></span>
  - <span data-ttu-id="d7e53-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="d7e53-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="d7e53-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="d7e53-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="d7e53-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="d7e53-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="d7e53-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="d7e53-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="d7e53-142">Filtjänster</span><span class="sxs-lookup"><span data-stu-id="d7e53-142">File Services</span></span>

- <span data-ttu-id="d7e53-143">Minimal 3,3 kB FLASH</span><span class="sxs-lookup"><span data-stu-id="d7e53-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="d7e53-144">Obegränsade öppna filer</span><span class="sxs-lookup"><span data-stu-id="d7e53-144">Unlimited open files</span></span>
- <span data-ttu-id="d7e53-145">Skrivskyddade filer kan öppnas flera gånger</span><span class="sxs-lookup"><span data-stu-id="d7e53-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="d7e53-146">Långa och 8.3 katalognamn som stöds</span><span class="sxs-lookup"><span data-stu-id="d7e53-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="d7e53-147">Stöd för sammanhängande filer</span><span class="sxs-lookup"><span data-stu-id="d7e53-147">Contiguous file support</span></span>
- <span data-ttu-id="d7e53-148">Logik för snabbsökning</span><span class="sxs-lookup"><span data-stu-id="d7e53-148">Fast seek logic</span></span>
- <span data-ttu-id="d7e53-149">Förallokering av kluster</span><span class="sxs-lookup"><span data-stu-id="d7e53-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="d7e53-150">Skapa, ta bort och byt namn på fil</span><span class="sxs-lookup"><span data-stu-id="d7e53-150">File create, delete, and rename</span></span>
- <span data-ttu-id="d7e53-151">Filläsning, skrivning och se</span><span class="sxs-lookup"><span data-stu-id="d7e53-151">File read, write, and see</span></span>
- <span data-ttu-id="d7e53-152">Hantering av filattribut</span><span class="sxs-lookup"><span data-stu-id="d7e53-152">File attributes management</span></span>
- <span data-ttu-id="d7e53-153">Spårning på systemnivå via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d7e53-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="d7e53-154">Intuitiva API:er för filåtkomst, inklusive:</span><span class="sxs-lookup"><span data-stu-id="d7e53-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="d7e53-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="d7e53-155">fx_file_create</span></span>
  - <span data-ttu-id="d7e53-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="d7e53-156">fx_file_delete</span></span>
  - <span data-ttu-id="d7e53-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="d7e53-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="d7e53-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="d7e53-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="d7e53-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="d7e53-159">fx_file_read</span></span>
  - <span data-ttu-id="d7e53-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="d7e53-160">fx_file_seek</span></span>
  - <span data-ttu-id="d7e53-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="d7e53-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="d7e53-162">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="d7e53-162">Advanced technology</span></span>

<span data-ttu-id="d7e53-163">Azure RTOS FileX är avancerad teknik, inklusive följande.</span><span class="sxs-lookup"><span data-stu-id="d7e53-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="d7e53-164">FAT 12/16/32 och exFAT-stöd</span><span class="sxs-lookup"><span data-stu-id="d7e53-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="d7e53-165">Stöd för flera partitioner</span><span class="sxs-lookup"><span data-stu-id="d7e53-165">Multiple partition support</span></span>
- <span data-ttu-id="d7e53-166">Automatisk skalning</span><span class="sxs-lookup"><span data-stu-id="d7e53-166">Automatic scaling</span></span>
- <span data-ttu-id="d7e53-167">Endiansk neutral</span><span class="sxs-lookup"><span data-stu-id="d7e53-167">Endian neutral</span></span>
- <span data-ttu-id="d7e53-168">Långt filnamn och stöd för 8.3</span><span class="sxs-lookup"><span data-stu-id="d7e53-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="d7e53-169">Valfritt stöd för feltolerans</span><span class="sxs-lookup"><span data-stu-id="d7e53-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="d7e53-170">Cache för logisk sektor</span><span class="sxs-lookup"><span data-stu-id="d7e53-170">Logical sector cache</span></span>
- <span data-ttu-id="d7e53-171">FAT-postcache</span><span class="sxs-lookup"><span data-stu-id="d7e53-171">FAT entry cache</span></span>
- <span data-ttu-id="d7e53-172">Förallokering av kluster</span><span class="sxs-lookup"><span data-stu-id="d7e53-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="d7e53-173">Stöd för sammanhängande filer</span><span class="sxs-lookup"><span data-stu-id="d7e53-173">Contiguous file support</span></span>
- <span data-ttu-id="d7e53-174">Valfria prestandamått</span><span class="sxs-lookup"><span data-stu-id="d7e53-174">Optional performance metrics</span></span>
- <span data-ttu-id="d7e53-175">Azure RTOS TraceX-systemanalysstöd</span><span class="sxs-lookup"><span data-stu-id="d7e53-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="d7e53-176">NOR/SÅDD-slitningsnivå (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="d7e53-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="d7e53-177">Azure RTOS LevelX är Microsofts PRODUKT FÖR FLASH-förslitning eller FLASH-utslitning.</span><span class="sxs-lookup"><span data-stu-id="d7e53-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="d7e53-178">Azure RTOS LevelX kan användas tillsammans med FileX eller som ett fristående FLASH-sektorbibliotek med direkt läsning/skrivning för programmet.</span><span class="sxs-lookup"><span data-stu-id="d7e53-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
