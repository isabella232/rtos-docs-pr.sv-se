---
title: 'Kapitel 4 – Azure återställnings tider LevelX NAND-API: er'
description: 'De Azure återställnings tider LevelX-NAND-API: er som är tillgängliga för programmet.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827063"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Kapitel 4 – Azure återställnings tider LevelX NAND-API: er

De Azure återställnings tider LevelX-NAND-API: erna som är tillgängliga för programmet är:

- ***lx_nand_flash_close** _: _Close NAND Flash instance *
- ***lx_nand_flash_defragment** _: _Defragment NAND Flash instance *
- ***lx_nand_flash_extended_cache_enable** _: _Enable/Disable utökad NAND-cache *
- ***lx_nand_flash_initialize** _: _Initialize NAND Flash Support *
- ***lx_nand_flash_open** _: _Open NAND Flash instance *
- ***lx_nand_flash_page_ecc_check** _: _Check sida för ECC-fel med korrigering *
- ***lx_nand_flash_page_ecc_compute** _: _Computes ECC för sida *
- ***lx_nand_flash_partial_defragment** _: _Partial defragmentera NAND Flash instance *
- ***lx_nand_flash_sector_read** _: _Read NAND Flash-sektor *
- ***lx_nand_flash_sector_release** _: _Release NAND Flash-sektor *
- ***lx_nand_flash_sector_write** _: _Write NAND Flash-sektor *

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Stäng NAND Flash instance

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger den tidigare öppnade NAND Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att stänga Flash-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Defragmentera NAND Flash instance

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Beskrivning

Den här tjänsten defragmenterar den tidigare öppnade NAND-Flash-instansen. Defragmenteringen maximerar antalet fria sidor och block.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Aktivera/inaktivera utökad NAND-cache

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten implementerar ett cache-skikt i RAM-minnet med det minne som tillhandahålls av programmet. Den totala mängd minne som krävs för fullständig cache-åtgärd kan beräknas på följande sätt:

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

Om det tillhandahållna minnet inte är tillräckligt stort för att rymma fullständig NAND cache, så gör den här rutinen så att Flash-cachen i NAND är så stor som möjligt baserat på det angivna minnet.

NAND-cachen är inaktive rad om den angivna minnes adressen är NULL. Därför kan NAND-cachen användas på ett tillfälligt sätt.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.  
- **minne**: Start adress för cache-minne som är justerat för ulong-åtkomst. Värdet LX_NULL inaktiverar cacheminnet.  
- **storlek**: storleken i byte för det angivna minnet.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) det finns inte tillräckligt med minne för ett element i NAND-cachen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Initiera stöd för NAND Flash

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar LevelX NAND Flash-stöd. Den måste anropas före andra LevelX NAND-API: er.

### <a name="input-parameters"></a>Indataparametrar

- **Ingen**

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att initiera stöd för NAND Flash.

### <a name="allowed-from"></a>Tillåten från

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

Öppna NAND Flash instance

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten öppnar en NAND Flash-instans med angivet NAND för Flash-kontroll block och driv rutins initiering. Observera att driv Rutinens initierings funktion ansvarar för att installera olika funktions pekare för att läsa, skriva och radera block/sidor för den NAND maskin vara som är associerad med NAND Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **namn**: namnet på NAND-Flash-instansen.
- **nand_driver_initialize**: funktions pekare till NAND för Flash-drivrutinen. Se kapitel 3 i den här guiden för mer information om NAND för Flash-drivrutinen.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att öppna NAND Flash instance.
- **LX_NO_MEMORY**: (0X08) driv rutinen tillhandahöll ingen buffert för att läsa en sida i RAM-minnet.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Kontrol lera sidan för ECC-fel med korrigering

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten verifierar integriteten för den tillhandahållna NAND-bufferten med angiven ECC. Sid storleken (definieras i NAND Flash instance Pointer) antas vara en multipel av 256-byte och den angivna ECC-koden kan korrigera ett 1-bitars fel i varje 256-byte-del av sidan.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **page_buffer**: PEKAREN till NAND Flash Page buffer.
- **ecc_buffer**: pekar på ECC för NAND Flash Page. Observera att det finns 3 ECC-byte per 256 byte-del av sidan.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) NAND-sidan innehåller inga fel.
- **LX_NAND_ERROR_CORRECTED**: (0X06) ett eller flera 1-bitars fel korrigerades på sidan NAND – korrigeringarna finns i kommandobufferten.
- **LX_NAND_ERROR_NOT_CORRECTED**: (0X07) för många fel som ska korrigeras på NAND-sidan.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar ECC för den angivna NAND-kommandobufferten och returnerar ECC i den angivna ECC-bufferten. Sid storleken antas vara en multipel av 256 byte (definieras i NAND Flash instance Pointer). ECC-koden används för att verifiera sidans integritet när den läses vid ett senare tillfälle.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **page_buffer**: PEKAREN till NAND Flash Page buffer.
- **ecc_buffer**: pekare till destination för ECC på Flash-sidan NAND. Observera att måste vara 3 byte ECC-lagring per 256 byte-del av sidan. Till exempel kräver en 2048 byte-sida 24 byte för ECC.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) ECC har beräknats.
- **LX_ERROR**: (0x01) Det gick inte att beräkna ECC.

### <a name="allowed-from"></a>Tillåten från

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

Partiell defragmentering av NAND Flash instance

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Beskrivning

Den här tjänsten defragmenterar den tidigare öppnade NAND Flash-instansen upp till det maximala antalet block som anges. Defragmenteringen maximerar antalet fria sidor och block.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **max_blocks**: maximalt antal block.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Läs NAND-Flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser den logiska sektorn från NAND Flash-instansen och returnerar innehållet i den angivna bufferten om det lyckas. Observera att NAND sektor storlek alltid är sid storleken för den underliggande NAND-maskinvaran.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **logical_sector**: logisk sektor som ska läsas.
- **buffert**: pekare till målet för innehållet i den logiska sektorn. Observera att bufferten antas vara storleken på storleken på NAND Flash-sidan och justeras för ULONG-åtkomst.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att läsa NAND Flash-sektor.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Version NAND Flash sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Beskrivning

Den här tjänsten släpper den logiska sektor mappningen i NAND Flash-instansen. Att släppa en logisk sektor när den inte används gör att LevelX slitaget är mer effektivt.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **logical_sector**: logisk sektor som ska frisläppas.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0X01) fel NAND Flash sektor Write.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Skriv NAND Flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skriver den angivna logiska sektorn i NAND-Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **nand_flash**: NAND Flash instance Pointer.
- **logical_sector**: logisk sektor som ska skrivas.
- **Buffer**: pekar mot innehållet i den logiska sektorn. Observera att bufferten antas vara storleken på storleken på NAND Flash-sidan och justeras för ULONG-åtkomst.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_NO_SECTORS**: (protokollnumret 0x02) det finns inga fler kostnads fria sektorer att utföra skrivningen.
- **LX_ERROR**: (0x01) Det gick inte att frigöra NAND Flash-sektor.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
