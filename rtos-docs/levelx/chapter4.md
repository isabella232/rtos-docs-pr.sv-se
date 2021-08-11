---
title: Kapitel 4 – Azure RTOS LEVELX FÖRD-API:er
description: Den Azure RTOS LevelX FÖRD-API:er som är tillgängliga för programmet.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d92b6c10921b4d04345610e139101e93c7a439ff695a89a79245894ad9ef1fec
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790296"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Kapitel 4 – Azure RTOS LEVELX FÖRD-API:er

De Azure RTOS LEVELX KPI:er som är tillgängliga för programmet är:

- ***lx_nand_flash_close** _: _Close FLASH-instans*
- ***lx_nand_flash_defragment** _: _Defragment FLASH-instans*
- ***lx_nand_flash_extended_cache_enable** _: _Enable/inaktivera utökad UTÖKADD-cache*
- ***lx_nand_flash_initialize** _: _Initialize FÖR FLASH-stöd*
- ***lx_nand_flash_open** _: _Open FLASH-instans*
- ***lx_nand_flash_page_ecc_check** _: _Check sida för ECC-fel med korrigering*
- ***lx_nand_flash_page_ecc_compute** _: _Computes ECC för sida*
- ***lx_nand_flash_partial_defragment** _: _Partial defragmentering av FLASH-flashinstansen FLASH*
- ***lx_nand_flash_sector_read** _: _Read FLASH-sektor*
- ***lx_nand_flash_sector_release** _: _Release FLASH-sektor*
- ***lx_nand_flash_sector_write** _: _Write FLASH-sektor*

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Stäng FLASH-instansen

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Description

Den här tjänsten stänger den tidigare öppnade FLASH-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid stängning av flash-instans.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

Defragmentering AV FLASH-instans

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Description

Den här tjänsten defragmenteras den tidigare öppnade FLASH-instansen. Defragmenteringsprocessen maximerar antalet kostnadsfria sidor och block.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid defragmentering av flash-instans.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

Aktivera/inaktivera utökad INVALIDD-cache

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Description

Den här tjänsten implementerar ett cachelager i RAM med hjälp av det minne som tillhandahålls av programmet. Den totala mängden minne som krävs för en fullständig cacheåtgärd kan beräknas på följande sätt:

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

Om det angivna minnet inte är tillräckligt stort för att få plats med den fullständigaEDD-cachen aktiverar den här rutinen så mycket av FLASHD-flashcachen som möjligt baserat på det angivna minnet.

CACHEminnet FÖR KAN INAKTIVERAS om den angivna minnesadressen är NULL. DÄRFÖR kan CACHEMINNEt FÖR DATALAGRING användas på ett tillfälligt sätt.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.  
- **memory**: Startadress för cacheminne justerat för ULONG-åtkomst. Värdet för LX_NULL inaktiverar cachen.  
- **size**: Storleken i byte för det angivna minnet.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Det finns inte tillräckligt med minne för ett element i CACHEMINNET FÖR DATALAGRING.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

Initiera FLASH-stöd för FLASH

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Description

Den här tjänsten initierar Flash-stöd för LevelX FLASH. Den måste anropas före andra LevelX- OCH BED-API:er.

### <a name="input-parameters"></a>Indataparametrar

- **Ingen**

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR:**(0x01) Fel vid initiering av FLASH-stöd.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

Öppna FLASH-instansen

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Description

Den här tjänsten öppnar en FLASH-instans med det angivna FLASH-kontrollblocket och initieringsfunktionen för drivrutiner. Observera att initieringsfunktionen för drivrutiner ansvarar för att installera olika funktionspekare för läsning, skrivning och radering av block/sidor i DEN UTF-maskinvara som är associerad med den här FLASH-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- **name**: Namnet på FLASH-instansen.
- **nand_driver_initialize: Funktionspekaren** till INITIERINGsfunktionen för FLASH-drivrutin. Se kapitel 3 i den här guiden för mer information om ansvar för FLASH-drivrutiner.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid öppning av FLASH-instansen.
- **LX_NO_MEMORY**: (0x08) Drivrutinen har inte en buffert för att läsa in en sida i RAM-minnet.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

Kontrollera sidan för ECC-fel med korrigering

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Description

Den här tjänsten verifierar integriteten för den angivna UTF-sidbufferten med den angivna ECC:en. Sidstorleken (definieras i FLASH-instans pekaren) antas vara en multipel på 256 byte och DEN ECC-kod som anges kan korrigera ett 1-bitarsfel i varje 256 byte-del av sidan.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- page_buffer : **Pekare** till UTFRÅD-flash-sidbuffert.
- **ecc_buffer:** Pekare till ECC för UTF-flash-sida. Observera att det finns 3 ECC-byte per 256 byte på sidan.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) UTTD-sidan har inga fel.
- **LX_NAND_ERROR_CORRECTED:**(0x06) Ett eller flera 1-bitars fel har korrigerats på SIDAN UTSE – korrigeringar finns i sidbufferten.
- **LX_NAND_ERROR_NOT_CORRECTED**: (0x07) För många fel för att korrigera på SIDAN UTT.

### <a name="allowed-from"></a>Tillåts från

LevelX-drivrutin

### <a name="example"></a>Exempel

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

Compute ECC för sida

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Description

Den här tjänsten beräknar ECC för den angivnaEDD-sidbufferten och returnerar ECC i den angivna ECC-bufferten. Sidstorleken förutsätts vara en multipel på 256 byte (definieras i FLASH-instans pekaren). ECC-koden används för att verifiera sidans integritet när den läses vid ett senare tillfälle.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- page_buffer : **Pekare** till UTFRÅD-flash-sidbuffert.
- **ecc_buffer:** Pekare till mål för ECC för FLASH-flash-sidan. Observera att måste vara 3 byte ECC-lagring per 256 byte på sidan. En 2 048 byte-sida skulle till exempel kräva 24 byte för ECC.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS:**(0x00) ECC har beräknats.
- **LX_ERROR**: (0x01) Fel vid beräkning av ECC.

### <a name="allowed-from"></a>Tillåts från

LevelX-drivrutin

### <a name="example"></a>Exempel

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

Partiell defragmentering av FLASH-instansen

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Description

Den här tjänsten defragmenteras den tidigare öppnade FLASH-flash-instansen upp till det maximala antalet block som har angetts. Defragmenteringsprocessen maximerar antalet kostnadsfria sidor och block.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- **max_blocks:** Maximalt antal block.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid defragmentering av flash-instans.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

Läsa FLASH-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Den här tjänsten läser den logiska sektorn från FLASH-instansen och returnerar innehållet i den angivna bufferten om det lyckas. Observera att DATORD-sektorstorleken alltid är sidstorleken för den underliggande DATORD-maskinvaran.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- **logical_sector:** Logisk sektor att läsa.
- **buffer**: Pekare till mål för innehållet i den logiska sektorn. Observera att bufferten antas vara storleken på DENDD-flashsidans storlek och justerad för ULONG-åtkomst.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel vid läsning av FLASH-sektor FÖR FLASH.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

Släpp FLASH-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Description

Den här tjänsten släpper mappningen av den logiska sektorn i FLASH-instansen AVD. Om du frigör en logisk sektor när den inte används blir nivå X-förslitningen effektivare.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- **logical_sector:** Logisk sektor som ska släppas.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_ERROR**: (0x01) Fel VID skrivning till FLASH-sektor.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

Skriva FLASH-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Den här tjänsten skriver den angivna logiska sektorn i FLASH-instansen AVD.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash:** FLASH-instans pekare.
- **logical_sector:** Logisk sektor att skriva.
- **buffer**: Pekare till innehållet i den logiska sektorn. Observera att bufferten antas vara storleken på DENDD-flashsidans storlek och justerad för ULONG-åtkomst.

### <a name="return-values"></a>Returvärden

- **LX_SUCCESS**: (0x00) Lyckad begäran.
- **LX_NO_SECTORS**: (0x02) Inga fler lediga sektorer är tillgängliga för att utföra skrivning.
- **LX_ERROR**: (0x01) Fel vid frisläppning av FLASH-sektor.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Se även

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
