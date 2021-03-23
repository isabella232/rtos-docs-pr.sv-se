---
title: Kapitel 2 – installation och användning av Azure återställnings tider LevelX
description: Installation och användning av LevelX är enkelt och beskrivs i följande avsnitt i det här kapitlet.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 575776875452cfc718401556a6440d787cb18893
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827066"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="9592e-103">Kapitel 2 – installation och användning av Azure återställnings tider LevelX</span><span class="sxs-lookup"><span data-stu-id="9592e-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="9592e-104">Installation och användning av Azure återställnings tider LevelX är enkelt och beskrivs i följande avsnitt i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="9592e-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="9592e-105">Distribution</span><span class="sxs-lookup"><span data-stu-id="9592e-105">Distribution</span></span>

<span data-ttu-id="9592e-106">LevelX distribueras i ANSI C där varje funktion finns i en egen separat C-fil.</span><span class="sxs-lookup"><span data-stu-id="9592e-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="9592e-107">Filerna i LevelX-distributionen är följande.</span><span class="sxs-lookup"><span data-stu-id="9592e-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="9592e-108">lx_api. h</span><span class="sxs-lookup"><span data-stu-id="9592e-108">lx_api.h</span></span>
- <span data-ttu-id="9592e-109">lx_nand_flash_256byte_ecc_check. c</span><span class="sxs-lookup"><span data-stu-id="9592e-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="9592e-110">lx_nand_flash_256byte_ecc_compute. c</span><span class="sxs-lookup"><span data-stu-id="9592e-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="9592e-111">lx_nand_flash_block_full_update. c</span><span class="sxs-lookup"><span data-stu-id="9592e-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="9592e-112">lx_nand_flash_block_reclaim. c</span><span class="sxs-lookup"><span data-stu-id="9592e-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="9592e-113">lx_nand_flash_close. c</span><span class="sxs-lookup"><span data-stu-id="9592e-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="9592e-114">lx_nand_flash_defragment. c</span><span class="sxs-lookup"><span data-stu-id="9592e-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="9592e-115">lx_nand_flash_extended_cache_enable. c</span><span class="sxs-lookup"><span data-stu-id="9592e-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="9592e-116">lx_nand_flash_initialize. c</span><span class="sxs-lookup"><span data-stu-id="9592e-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="9592e-117">lx_nand_flash_logical_sector_find. c</span><span class="sxs-lookup"><span data-stu-id="9592e-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="9592e-118">lx_nand_flash_next_block_to_erase_find. c</span><span class="sxs-lookup"><span data-stu-id="9592e-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="9592e-119">lx_nand_flash_open. c</span><span class="sxs-lookup"><span data-stu-id="9592e-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="9592e-120">lx_nand_flash_page_ecc_check. c</span><span class="sxs-lookup"><span data-stu-id="9592e-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="9592e-121">lx_nand_flash_page_ecc_compute. c</span><span class="sxs-lookup"><span data-stu-id="9592e-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="9592e-122">lx_nand_flash_partial_defragment. c</span><span class="sxs-lookup"><span data-stu-id="9592e-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="9592e-123">lx_nand_flash_physical_page_allocate. c</span><span class="sxs-lookup"><span data-stu-id="9592e-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="9592e-124">lx_nand_flash_sector_mapping_cache_invalidate. c</span><span class="sxs-lookup"><span data-stu-id="9592e-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="9592e-125">lx_nand_flash_sector_read. c</span><span class="sxs-lookup"><span data-stu-id="9592e-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="9592e-126">lx_nand_flash_sector_release. c</span><span class="sxs-lookup"><span data-stu-id="9592e-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="9592e-127">lx_nand_flash_sector_write. c</span><span class="sxs-lookup"><span data-stu-id="9592e-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="9592e-128">lx_nand_flash_system_error. c</span><span class="sxs-lookup"><span data-stu-id="9592e-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="9592e-129">lx_nor_flash_block_reclaim. c</span><span class="sxs-lookup"><span data-stu-id="9592e-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="9592e-130">lx_nor_flash_close. c</span><span class="sxs-lookup"><span data-stu-id="9592e-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="9592e-131">lx_nor_flash_defragment. c</span><span class="sxs-lookup"><span data-stu-id="9592e-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="9592e-132">lx_nor_flash_extended_cache_enable. c</span><span class="sxs-lookup"><span data-stu-id="9592e-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="9592e-133">lx_nor_flash_initialize. c</span><span class="sxs-lookup"><span data-stu-id="9592e-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="9592e-134">lx_nor_flash_logical_sector_find. c</span><span class="sxs-lookup"><span data-stu-id="9592e-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="9592e-135">lx_nor_flash_next_block_to_erase_find. c</span><span class="sxs-lookup"><span data-stu-id="9592e-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="9592e-136">lx_nor_flash_open. c</span><span class="sxs-lookup"><span data-stu-id="9592e-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="9592e-137">lx_nor_flash_partial_defragment. c</span><span class="sxs-lookup"><span data-stu-id="9592e-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="9592e-138">lx_nor_flash_physical_sector_allocate. c</span><span class="sxs-lookup"><span data-stu-id="9592e-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="9592e-139">lx_nor_flash_sector_mapping_cache_invalidate. c</span><span class="sxs-lookup"><span data-stu-id="9592e-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="9592e-140">lx_nor_flash_sector_read. c</span><span class="sxs-lookup"><span data-stu-id="9592e-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="9592e-141">lx_nor_flash_sector_release. c</span><span class="sxs-lookup"><span data-stu-id="9592e-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="9592e-142">lx_nor_flash_sector_write. c</span><span class="sxs-lookup"><span data-stu-id="9592e-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="9592e-143">lx_nor_flash_system_error. c</span><span class="sxs-lookup"><span data-stu-id="9592e-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="9592e-144">Det finns också exempel på driv rutins-och FileX för både LevelX NAND och-instanser, enligt följande.</span><span class="sxs-lookup"><span data-stu-id="9592e-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="9592e-145">demo_filex_nand_flash. c</span><span class="sxs-lookup"><span data-stu-id="9592e-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="9592e-146">fx_nand_flash_simulated_driver. c</span><span class="sxs-lookup"><span data-stu-id="9592e-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="9592e-147">lx_nand_flash_simulator. c</span><span class="sxs-lookup"><span data-stu-id="9592e-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="9592e-148">demo_filex_nor_flash. c</span><span class="sxs-lookup"><span data-stu-id="9592e-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="9592e-149">fx_nor_flash_simulated_driver. c</span><span class="sxs-lookup"><span data-stu-id="9592e-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="9592e-150">lx_nor_flash_simulator. c</span><span class="sxs-lookup"><span data-stu-id="9592e-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="9592e-151">Om det bara behövs NAND Flash krävs bara Flash-filerna LevelX NAND (***lx_nand_ \* . c***).</span><span class="sxs-lookup"><span data-stu-id="9592e-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="9592e-152">Om det bara behövs eller blinkar krävs endast eller Flash-filer (\* \*_lx_nor_ \_ . c \* \* \*).</span><span class="sxs-lookup"><span data-stu-id="9592e-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="9592e-153">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="9592e-153">Configuration Options</span></span>

<span data-ttu-id="9592e-154">LevelX kan konfigureras vid kompilering via de villkors definitioner som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="9592e-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="9592e-155">Lägg bara till önskad definition i kompileringen av varje LevelX-källa för att använda alternativet.</span><span class="sxs-lookup"><span data-stu-id="9592e-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="9592e-156">**LX_DIRECT_READ**: med det här alternativet åsidosätter det här alternativet driv rutinen för eller Flash-drivrutinen i stället för att prioritera eller läsa in eller minne direkt, vilket resulterar i en betydande prestanda ökning.</span><span class="sxs-lookup"><span data-stu-id="9592e-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="9592e-157">**LX_FREE_SECTOR_DATA_VERIFY**: det här innebär att LevelX eller instansen öppen logik för att verifiera kostnads fria eller sektorer är alla.</span><span class="sxs-lookup"><span data-stu-id="9592e-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="9592e-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: som standard är det här värdet 16 och definierar cache-storleken för den logiska sektor mappningen.</span><span class="sxs-lookup"><span data-stu-id="9592e-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="9592e-159">Stora värden ger bättre prestanda, men kostnads minnet.</span><span class="sxs-lookup"><span data-stu-id="9592e-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="9592e-160">Den minsta storleken är 8 och alla värden måste vara en exponent på 2.</span><span class="sxs-lookup"><span data-stu-id="9592e-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="9592e-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: det här skapar en cache för direkt mappning, så att det inte finns några Cachemissar.</span><span class="sxs-lookup"><span data-stu-id="9592e-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="9592e-162">Det kräver också att LX_NAND_SECTOR_MAPPING_CACHE_SIZE representerar det exakta antalet sidor i din flash-enhet.</span><span class="sxs-lookup"><span data-stu-id="9592e-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="9592e-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: definierad, detta inaktiverade det utökade eller cachelagrade.</span><span class="sxs-lookup"><span data-stu-id="9592e-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="9592e-164">**LX_NOR_EXTENDED_CACHE_SIZE**: som standard är det här värdet 8, vilket motsvarar högst 8 sektorer som kan cachelagras i en-eller-instans.</span><span class="sxs-lookup"><span data-stu-id="9592e-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="9592e-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: som standard är det här värdet 16 och definierar cache-storleken för den logiska sektor mappningen.</span><span class="sxs-lookup"><span data-stu-id="9592e-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="9592e-166">Stora värden ger bättre prestanda, men kostnads minnet.</span><span class="sxs-lookup"><span data-stu-id="9592e-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="9592e-167">Den minsta storleken är 8 och alla värden måste vara en exponent på 2.</span><span class="sxs-lookup"><span data-stu-id="9592e-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="9592e-168">**LX_THREAD_SAFE_ENABLE**: Detta gör LevelX tråd säkert genom att använda ett ThreadX mutex-objekt i hela API: et.</span><span class="sxs-lookup"><span data-stu-id="9592e-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="9592e-169">Använda LevelX</span><span class="sxs-lookup"><span data-stu-id="9592e-169">Using LevelX</span></span>

<span data-ttu-id="9592e-170">Om du vill använda LevelX, antingen av sig själv eller med FileX, inkluderar du filen \***lx_api. h** _ i koden som refererar till LevelX-API: et.</span><span class="sxs-lookup"><span data-stu-id="9592e-170">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="9592e-171">Se också till att objekt koden LevelX är tillgänglig vid länk tillfället.</span><span class="sxs-lookup"><span data-stu-id="9592e-171">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="9592e-172">Kontrol lera filerna _*_demo_filex_nand_flash. c_*_ och _ *_demo_filex_nor_flash. c_*\* för exempel på hur du använder LevelX.</span><span class="sxs-lookup"><span data-stu-id="9592e-172">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
