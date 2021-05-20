---
title: Kapitel 2 – Installation och användning av Azure RTOS LevelX
description: Installation och användning av LevelX är enkelt och beskrivs i följande avsnitt i det här kapitlet.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223323"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="00bf1-103">Kapitel 2 – Installation och användning av Azure RTOS LevelX</span><span class="sxs-lookup"><span data-stu-id="00bf1-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="00bf1-104">Installation och användning av Azure RTOS LevelX är enkelt och beskrivs i följande avsnitt i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="00bf1-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="00bf1-105">Distribution</span><span class="sxs-lookup"><span data-stu-id="00bf1-105">Distribution</span></span>

<span data-ttu-id="00bf1-106">LevelX distribueras i ANSI C där varje funktion finns i en egen separat C-fil.</span><span class="sxs-lookup"><span data-stu-id="00bf1-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="00bf1-107">Filerna i LevelX-distributionen är följande.</span><span class="sxs-lookup"><span data-stu-id="00bf1-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="00bf1-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="00bf1-108">lx_api.h</span></span>
- <span data-ttu-id="00bf1-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="00bf1-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="00bf1-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="00bf1-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="00bf1-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="00bf1-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="00bf1-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="00bf1-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="00bf1-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="00bf1-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="00bf1-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="00bf1-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="00bf1-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="00bf1-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="00bf1-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="00bf1-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="00bf1-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="00bf1-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="00bf1-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="00bf1-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="00bf1-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="00bf1-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="00bf1-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="00bf1-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="00bf1-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="00bf1-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="00bf1-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="00bf1-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="00bf1-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="00bf1-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="00bf1-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="00bf1-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="00bf1-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="00bf1-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="00bf1-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="00bf1-144">Det finns även simulator- och FileX-drivrutinsexempel för både LevelX PROVEND- och NOR-instanser enligt följande.</span><span class="sxs-lookup"><span data-stu-id="00bf1-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="00bf1-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="00bf1-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="00bf1-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="00bf1-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="00bf1-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="00bf1-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="00bf1-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="00bf1-151">Om det bara är FLASHD-flash-minne som krävs behövs naturligtvis endast Flash-filerna i LevelX LX_NAND_ ***\* .c.***</span><span class="sxs-lookup"><span data-stu-id="00bf1-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="00bf1-152">På samma sätt krävs endast NOR flash-filer _(\*\*_ lx_nor .c\*\*) om endast FLASH-minne \_ krävs.</span><span class="sxs-lookup"><span data-stu-id="00bf1-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="00bf1-153">Konfigurationsalternativ</span><span class="sxs-lookup"><span data-stu-id="00bf1-153">Configuration Options</span></span>

<span data-ttu-id="00bf1-154">LevelX kan konfigureras vid kompileringen via de villkorliga definierar som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="00bf1-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="00bf1-155">Lägg bara till önskad definition i kompileringen av varje LevelX-källa för att använda alternativet .</span><span class="sxs-lookup"><span data-stu-id="00bf1-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="00bf1-156">**LX_DIRECT_READ:** Det här alternativet kringgår NOR-flashdrivrutinens läsrutin till förmån för eller läsning av NOR-minnet direkt, vilket resulterar i en betydande prestandaökning.</span><span class="sxs-lookup"><span data-stu-id="00bf1-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="00bf1-157">**LX_FREE_SECTOR_DATA_VERIFY:** Detta gör att LevelX NOR-instansens öppna logik för att verifiera att alla kostnadsfria NOR-sektorer är sådana.</span><span class="sxs-lookup"><span data-stu-id="00bf1-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="00bf1-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE:** Som standard är det här värdet 16 och definierar cachestorleken för mappning av logisk sektor.</span><span class="sxs-lookup"><span data-stu-id="00bf1-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="00bf1-159">Stora värden förbättrar prestanda, men kostar minne.</span><span class="sxs-lookup"><span data-stu-id="00bf1-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="00bf1-160">Den minsta storleken är 8 och alla värden måste vara 2.</span><span class="sxs-lookup"><span data-stu-id="00bf1-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="00bf1-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Definieras, detta skapar en direkt mappningscache, så att det inte finns några cachemissar.</span><span class="sxs-lookup"><span data-stu-id="00bf1-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="00bf1-162">Det kräver också att LX_NAND_SECTOR_MAPPING_CACHE_SIZE representerar det exakta antalet totalt antal sidor i flash-enheten.</span><span class="sxs-lookup"><span data-stu-id="00bf1-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="00bf1-163">**LX_NOR_DISABLE_EXTENDED_CACHE:** Här inaktiverades den utökade NOR-cachen.</span><span class="sxs-lookup"><span data-stu-id="00bf1-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="00bf1-164">**LX_NOR_EXTENDED_CACHE_SIZE:** Som standard är det här värdet 8, vilket representerar högst 8 sektorer som kan cachelagras i en NOR-instans.</span><span class="sxs-lookup"><span data-stu-id="00bf1-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="00bf1-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE:** Som standard är det här värdet 16 och definierar cachestorleken för mappning av logisk sektor.</span><span class="sxs-lookup"><span data-stu-id="00bf1-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="00bf1-166">Stora värden förbättrar prestandan, men kostar minne.</span><span class="sxs-lookup"><span data-stu-id="00bf1-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="00bf1-167">Den minsta storleken är 8 och alla värden måste vara 2.</span><span class="sxs-lookup"><span data-stu-id="00bf1-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="00bf1-168">**LX_THREAD_SAFE_ENABLE**: Definieras gör detta LevelX-trådsäkert genom att använda ett ThreadX mutex-objekt i hela API:et.</span><span class="sxs-lookup"><span data-stu-id="00bf1-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="00bf1-169">**LX_STANDALONE_ENABLE:** Definierad gör att LevelX kan användas i fristående läge (utan Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="00bf1-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="00bf1-170">Som standard definieras inte den här symbolen.</span><span class="sxs-lookup"><span data-stu-id="00bf1-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00bf1-171">När du använder LevelX i fristående läge (**LX_STANDALONE_ENABLE** måste definieras), krävs inte ThreadX-filer/bibliotek.</span><span class="sxs-lookup"><span data-stu-id="00bf1-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="00bf1-172">LevelX-trådsäker funktion är inaktiverad i det här läget.</span><span class="sxs-lookup"><span data-stu-id="00bf1-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="00bf1-173">Använda LevelX</span><span class="sxs-lookup"><span data-stu-id="00bf1-173">Using LevelX</span></span>

<span data-ttu-id="00bf1-174">Om du vill använda LevelX, antingen i sig själv eller med FileX, inkluderar du filen \***lx_api.h** _ i koden som refererar till LevelX-API:et.</span><span class="sxs-lookup"><span data-stu-id="00bf1-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="00bf1-175">Kontrollera också att LevelX-objektkoden är tillgänglig vid länktiden.</span><span class="sxs-lookup"><span data-stu-id="00bf1-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="00bf1-176">Granska filerna i _*_demo_filex_nand_flash.c och_*_ _ *_demo_filex_nor_flash.c_*\* för exempel på hur du använder LevelX.</span><span class="sxs-lookup"><span data-stu-id="00bf1-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
