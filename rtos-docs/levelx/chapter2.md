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
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Kapitel 2 – Installation och användning av Azure RTOS LevelX

Installation och användning av Azure RTOS LevelX är enkelt och beskrivs i följande avsnitt i det här kapitlet.

## <a name="distribution"></a>Distribution

LevelX distribueras i ANSI C där varje funktion finns i en egen separat C-fil. Filerna i LevelX-distributionen är följande.
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

Det finns även simulator- och FileX-drivrutinsexempel för både LevelX PROVEND- och NOR-instanser enligt följande.

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

Om det bara är FLASHD-flash-minne som krävs behövs naturligtvis endast Flash-filerna i LevelX LX_NAND_ ***\* .c.*** På samma sätt krävs endast NOR flash-filer _(**_ lx_nor .c**) om endast FLASH-minne \_ krävs.

## <a name="configuration-options"></a>Konfigurationsalternativ

LevelX kan konfigureras vid kompileringen via de villkorliga definierar som beskrivs nedan. Lägg bara till önskad definition i kompileringen av varje LevelX-källa för att använda alternativet .

- **LX_DIRECT_READ:** Det här alternativet kringgår NOR-flashdrivrutinens läsrutin till förmån för eller läsning av NOR-minnet direkt, vilket resulterar i en betydande prestandaökning.
- **LX_FREE_SECTOR_DATA_VERIFY:** Detta gör att LevelX NOR-instansens öppna logik för att verifiera att alla kostnadsfria NOR-sektorer är sådana.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE:** Som standard är det här värdet 16 och definierar cachestorleken för mappning av logisk sektor. Stora värden förbättrar prestanda, men kostar minne. Den minsta storleken är 8 och alla värden måste vara 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Definieras, detta skapar en direkt mappningscache, så att det inte finns några cachemissar. Det kräver också att LX_NAND_SECTOR_MAPPING_CACHE_SIZE representerar det exakta antalet totalt antal sidor i flash-enheten.
- **LX_NOR_DISABLE_EXTENDED_CACHE:** Här inaktiverades den utökade NOR-cachen.
- **LX_NOR_EXTENDED_CACHE_SIZE:** Som standard är det här värdet 8, vilket representerar högst 8 sektorer som kan cachelagras i en NOR-instans.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE:** Som standard är det här värdet 16 och definierar cachestorleken för mappning av logisk sektor. Stora värden förbättrar prestandan, men kostar minne. Den minsta storleken är 8 och alla värden måste vara 2.
- **LX_THREAD_SAFE_ENABLE**: Definieras gör detta LevelX-trådsäkert genom att använda ett ThreadX mutex-objekt i hela API:et.
- **LX_STANDALONE_ENABLE:** Definierad gör att LevelX kan användas i fristående läge (utan Azure RTOS). Som standard definieras inte den här symbolen.

> [!IMPORTANT]
> När du använder LevelX i fristående läge (**LX_STANDALONE_ENABLE** måste definieras), krävs inte ThreadX-filer/bibliotek. LevelX-trådsäker funktion är inaktiverad i det här läget.

## <a name="using-levelx"></a>Använda LevelX

Om du vill använda LevelX, antingen i sig själv eller med FileX, inkluderar du filen ***lx_api.h** _ i koden som refererar till LevelX-API:et. Kontrollera också att LevelX-objektkoden är tillgänglig vid länktiden. Granska filerna i _*_demo_filex_nand_flash.c och_*_ _ *_demo_filex_nor_flash.c_** för exempel på hur du använder LevelX.
