---
title: Kapitel 6 – Azure RTOS LevelX NOR API:er
description: Den Azure RTOS LevelX NOR API:er som är tillgängliga för programmet.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e109f5916a9e903aa3341f2855ade085e9d9a22b80ec7cb2e0c310e43ff3eac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790249"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Kapitel 6 – Azure RTOS LevelX NOR API:er

De Azure RTOS LevelX NOR API som är tillgängliga för programmet är följande.

- ***lx_nor_flash_close** _: _Close ELLER flash-instans*
- ***lx_nor_flash_defragment** _: _Defragment NOR flash instance*
- ***lx_nor_flash_extended_cache_enable** _: _Enable/inaktivera utökad NOR-cache*
- ***lx_nor_flash_initialize** _: _Initialize NOR flash support*
- ***lx_nor_flash_open** _: _Open NOR flash instance*
- ***lx_nor_flash_partial_defragment** _: _Partial defragmentering av NOR Flash-instansen*
- ***lx_nor_flash_sector_read** _: _Read NOR flash sector*
- ***lx_nor_flash_sector_release** _: _Release NOR flash sector*
- ***lx_nor_flash_sector_write** _: _Write ELLER flash-sektor*

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Stäng NOR Flash-instansen

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Description

Den här tjänsten stänger den tidigare öppnade NOR Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash:* NOR flash instance pointer.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid stängning av flash-instans.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

Flash-instans för defragmentering ELLER

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Description

Den här tjänsten defragmentar den tidigare öppnade NOR Flash-instansen. Defragmenteringsprocessen maximerar antalet lediga sektorer och block.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash:* NOR flash instance pointer.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid defragmentering av flash-instans.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

Aktivera/inaktivera utökad NOR-cache

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Description

Den här tjänsten implementerar ett NOR-sektorcachelager i RAM med hjälp av det minne som tillhandahålls av programmet. Varje mängd minne på 512 byte översätts till en NOR-sektor som kan cachelagras. De sektorer som cachelagras är de som innehåller blockkontrollinformation, t.ex. radering av antal, kostnadsfri sektorkarta och sektormappningsinformation. Datasektorer lagras inte i den här cachen.

### <a name="input-parameters"></a>Indataparametrar

- **nor_flash:** NOR flash instance pointer.  
- **memory**: Startadress för cacheminne, justerat för ULONG-åtkomst. Värdet för LX_NULL inaktiverar cachen.  
- **storlek:** Storleken i byte för det angivna minnet (ska vara flera av 512 byte).

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Det finns inte tillräckligt med minne för en NOR-sektor.
- **LX_DISABLED:**(0x09) ELLER utökad cache inaktiverad av konfigurationsalternativet.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

Initiera NOR Flash-stöd

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Description

Den här tjänsten initierar Flash-stöd för LevelX NOR. Den måste anropas före andra LevelX NOR-API:er.

### <a name="input-parameters"></a>Indataparametrar

- **Ingen**

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR:**(0x01) Fel vid initiering av NOR Flash-stöd.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_partial_defragment
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

Öppna NOR Flash-instansen

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Description

Den här tjänsten öppnar en NOR-flash-instans med angiven INITIERINGsfunktion för NOR-flash-kontrollblock och drivrutin. Observera att initieringsfunktionen för drivrutiner ansvarar för att installera olika funktionspekare för läsning, skrivning och radering av block i NOR-maskinvaran som är associerad med den här NOR Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash:* NOR flash instance pointer.
- *name*: Namnet på NOR flash-instansen.
- *nor_driver_initialize: Funktionspekaren* till FUNKTIONEN INITIERING AV FLASH-drivrutin. Mer information om ansvaret för FLASH-drivrutiner finns i kapitel 5 i den här guiden.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR:**(0x01) Det gick inte att öppna NOR Flash-instansen.
- **LX_NO_MEMORY**: (0x08) Drivrutin tillhandahåller inte buffert för läsning av ingen sektor till RAM-minne.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

Partiell defragmentering av NOR-flashinstans

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Description

Den här tjänsten defragmenterade den tidigare öppnade NOR Flash-instansen upp till det maximala antalet block som angetts. Defragmenteringsprocessen maximerar antalet lediga sektorer och block.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash:* NOR flash instance pointer.
- *max_blocks:* Maximalt antal block.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid defragmentering av flash-instans.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

Läs ELLER flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Den här tjänsten läser den logiska sektorn från NOR Flash-instansen och returnerar om det lyckas innehållet i den angivna bufferten. Observera att NOR-sektorstorleken alltid är 512 byte.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash* PEKARe för FLASH-instans.
- *logical_sector:* Logisk sektor att läsa.
- *buffer*: Pekare till mål för innehållet i den logiska sektorn. Observera att bufferten antas vara 512 byte och justerad för ULONG-åtkomst.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att läsa NOR Flash-sektorn.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

Släpp ELLER flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Description

Den här tjänsten släpper mappningen av den logiska sektorn i FLASH-instansen NOR. Om du frigör en logisk sektor när den inte används blir nivå X-förslitningen effektivare.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash:* NOR flash instance pointer.
- *logical_sector:* Logisk sektor som ska släppas.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR:**(0x01) Fel VID skrivning av FLASH-sektor.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

Skriv NOR Flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Den här tjänsten skriver den angivna logiska sektorn i NOR Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash:* NOR flash instance pointer.
- *logical_sector:* Logisk sektor att skriva.
- *buffer*: Pekare till innehållet i den logiska sektorn. Observera att bufferten antas vara 512 byte justerad för ULONG-åtkomst.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_NO_SECTORS**: (0x02) Inga fler lediga sektorer är tillgängliga för att utföra skrivning.
- **LX_ERROR**: (0x01) Fel vid lanserar NOR Flash-sektor.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Se även

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
