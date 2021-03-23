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
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Kapitel 2 – installation och användning av Azure återställnings tider LevelX

Installation och användning av Azure återställnings tider LevelX är enkelt och beskrivs i följande avsnitt i det här kapitlet.

## <a name="distribution"></a>Distribution

LevelX distribueras i ANSI C där varje funktion finns i en egen separat C-fil. Filerna i LevelX-distributionen är följande.
- lx_api. h
- lx_nand_flash_256byte_ecc_check. c
- lx_nand_flash_256byte_ecc_compute. c
- lx_nand_flash_block_full_update. c
- lx_nand_flash_block_reclaim. c
- lx_nand_flash_close. c
- lx_nand_flash_defragment. c  
- lx_nand_flash_extended_cache_enable. c
- lx_nand_flash_initialize. c
- lx_nand_flash_logical_sector_find. c
- lx_nand_flash_next_block_to_erase_find. c
- lx_nand_flash_open. c
- lx_nand_flash_page_ecc_check. c
- lx_nand_flash_page_ecc_compute. c  
- lx_nand_flash_partial_defragment. c
- lx_nand_flash_physical_page_allocate. c
- lx_nand_flash_sector_mapping_cache_invalidate. c
- lx_nand_flash_sector_read. c
- lx_nand_flash_sector_release. c
- lx_nand_flash_sector_write. c
- lx_nand_flash_system_error. c
- lx_nor_flash_block_reclaim. c
- lx_nor_flash_close. c
- lx_nor_flash_defragment. c  
- lx_nor_flash_extended_cache_enable. c
- lx_nor_flash_initialize. c
- lx_nor_flash_logical_sector_find. c
- lx_nor_flash_next_block_to_erase_find. c
- lx_nor_flash_open. c
- lx_nor_flash_partial_defragment. c
- lx_nor_flash_physical_sector_allocate. c
- lx_nor_flash_sector_mapping_cache_invalidate. c
- lx_nor_flash_sector_read. c
- lx_nor_flash_sector_release. c
- lx_nor_flash_sector_write. c
- lx_nor_flash_system_error. c

Det finns också exempel på driv rutins-och FileX för både LevelX NAND och-instanser, enligt följande.

- demo_filex_nand_flash. c  
- fx_nand_flash_simulated_driver. c
- lx_nand_flash_simulator. c
- demo_filex_nor_flash. c  
- fx_nor_flash_simulated_driver. c
- lx_nor_flash_simulator. c

Om det bara behövs NAND Flash krävs bara Flash-filerna LevelX NAND (***lx_nand_ \* . c***). Om det bara behövs eller blinkar krävs endast eller Flash-filer (* *_lx_nor_ \_ . c * * *).

## <a name="configuration-options"></a>Konfigurations alternativ

LevelX kan konfigureras vid kompilering via de villkors definitioner som beskrivs nedan. Lägg bara till önskad definition i kompileringen av varje LevelX-källa för att använda alternativet.

- **LX_DIRECT_READ**: med det här alternativet åsidosätter det här alternativet driv rutinen för eller Flash-drivrutinen i stället för att prioritera eller läsa in eller minne direkt, vilket resulterar i en betydande prestanda ökning.
- **LX_FREE_SECTOR_DATA_VERIFY**: det här innebär att LevelX eller instansen öppen logik för att verifiera kostnads fria eller sektorer är alla.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: som standard är det här värdet 16 och definierar cache-storleken för den logiska sektor mappningen. Stora värden ger bättre prestanda, men kostnads minnet. Den minsta storleken är 8 och alla värden måste vara en exponent på 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: det här skapar en cache för direkt mappning, så att det inte finns några Cachemissar. Det kräver också att LX_NAND_SECTOR_MAPPING_CACHE_SIZE representerar det exakta antalet sidor i din flash-enhet.
- **LX_NOR_DISABLE_EXTENDED_CACHE**: definierad, detta inaktiverade det utökade eller cachelagrade.
- **LX_NOR_EXTENDED_CACHE_SIZE**: som standard är det här värdet 8, vilket motsvarar högst 8 sektorer som kan cachelagras i en-eller-instans.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: som standard är det här värdet 16 och definierar cache-storleken för den logiska sektor mappningen. Stora värden ger bättre prestanda, men kostnads minnet. Den minsta storleken är 8 och alla värden måste vara en exponent på 2.
- **LX_THREAD_SAFE_ENABLE**: Detta gör LevelX tråd säkert genom att använda ett ThreadX mutex-objekt i hela API: et.

## <a name="using-levelx"></a>Använda LevelX

Om du vill använda LevelX, antingen av sig själv eller med FileX, inkluderar du filen ***lx_api. h** _ i koden som refererar till LevelX-API: et. Se också till att objekt koden LevelX är tillgänglig vid länk tillfället. Kontrol lera filerna _*_demo_filex_nand_flash. c_*_ och _ *_demo_filex_nor_flash. c_** för exempel på hur du använder LevelX.
