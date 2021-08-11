---
title: Förstå Azure RTOS FileX
description: Azure RTOS FileX är ett FAT-kompatibelt filsystem (File Allocation Table) med höga prestanda som är helt integrerat med Azure RTOS ThreadX och tillgängligt för alla processorer som stöds. Precis som Azure RTOS ThreadX är Azure RTOS FileX utformat för att ha ett litet fotavtryck och höga prestanda, vilket gör det idealiskt för dagens djupt inbäddade program som kräver filhanteringsåtgärder. FileX stöder de flesta fysiska media, inklusive RAM, Azure RTOS USBX, SD-KORT och NÄTVERKSKORT/NOR flashminnen via Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 399586eca18ef9345b94cc577bdacbf3c3a591bcd22b474b4e3d4ca4eefb4432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782862"
---
# <a name="overview-of-azure-rtos-filex"></a>Översikt över Azure RTOS FileX

Azure RTOS FileX Embedded-filsystemet är Azure RTOS avancerade lösning i branschklass för Microsoft FAT-filformat, särskilt utformad för djupt inbäddade, realtidsbaserade och IoT-program. Azure RTOS FileX stöder alla Microsofts filformat, inklusive FAT12, FAT16, FAT32 och exFAT. FileX erbjuder även valfri feltolerans och FLASH-utslitning via en tilläggsprodukt som [kallas Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Allt detta i kombination med ett litet fotavtryck, snabb körning och överlägsen användarvänlighet gör Azure RTOS FileX till det perfekta valet för de mest krävande inbäddade IoT-programmen.

## <a name="api-protocols"></a>API-protokoll

### <a name="media-services"></a>Media Services

- FAT 12/16/32 och exFAT-stöd
- Minimalt 6 kB FLASH, 2,5 kB RAM
- Slutföra tjänster för medieåtkomst
- Obegränsat antal medieinstanser
- Enkelt gränssnitt för läs-/skrivdrivrutiner för logisk sektor
- Stöd för flera partitioner
- Cache för logisk sektor
- FAT-postcache
- Valfritt stöd för feltolerans
- Uppskjuten sekundär FAT-uppdatering
- Spårning på systemnivå via Azure RTOS TraceX
- Intuitiva API:er för medieåtkomst, inklusive:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>Directory Services

- Upp till 256 bytesökvägar
- Långa och 8.3-katalognamn som stöds
- Katalog create & delete
- Katalognavigering och traverserning
- Hantering av katalogattribut
- Spårning på systemnivå via Azure RTOS TraceX
- Intuitiva katalogåtkomst-API:er, inklusive:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>Filtjänster

- Minimal 3,3 kB FLASH
- Obegränsade öppna filer
- Skrivskyddade filer kan öppnas flera gånger
- Långa och 8.3-katalognamn som stöds
- Stöd för sammanhängande filer
- Logik för snabbsökning
- Förallokering av kluster
- Skapa, ta bort och byt namn på fil
- Filläsning, skrivning och läsning
- Hantering av filattribut
- Spårning på systemnivå via Azure RTOS TraceX
- Intuitiva API:er för filåtkomst, inklusive:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="advanced-technology"></a>Avancerad teknik

Azure RTOS FileX är avancerad teknik, inklusive följande.

- FAT 12/16/32 och exFAT-stöd
- Stöd för flera partitioner
- Automatisk skalning
- Endiansk neutral
- Långt filnamn och stöd för 8.3
- Valfritt stöd för feltolerans
- Cache för logisk sektor
- FAT-postcache
- Förallokering av kluster
- Stöd för sammanhängande filer
- Valfria prestandamått
- Azure RTOS TraceX-systemanalysstöd

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>NOR/SÅDD-slitningsnivå (Azure RTOS LevelX)

Azure RTOS LevelX är Microsofts PRODUKT FÖR FLASH-förslitning eller FLASH-utslitning. Azure RTOS LevelX kan användas tillsammans med FileX eller som ett fristående FLASH-sektorbibliotek med direkt läsning/skrivning för programmet.
