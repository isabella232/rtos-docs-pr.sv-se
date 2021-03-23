---
title: 'Kapitel 6 – Azure återställnings tider-LevelX eller API: er'
description: 'Azure återställnings tider-LevelX eller API: er som är tillgängliga för programmet.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827051"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Kapitel 6 – Azure återställnings tider-LevelX eller API: er

Azure återställnings tider-LevelX eller API-funktionerna som är tillgängliga för programmet är följande.

- ***lx_nor_flash_close** _: _Close eller Flash-instans *
- ***lx_nor_flash_defragment** _: _Defragment eller Flash-instans *
- ***lx_nor_flash_extended_cache_enable** _: _Enable/Disable utökad eller cache *
- ***lx_nor_flash_initialize** _: _INITIALIZE-eller Flash-Support *
- ***lx_nor_flash_open** _: _Open eller Flash-instans *
- ***lx_nor_flash_partial_defragment** _: _Partial defragmentera eller Flash-instansen *
- ***lx_nor_flash_sector_read** _: _Read eller Flash-sektor *
- ***lx_nor_flash_sector_release** _: _Release eller Flash-sektor *
- ***lx_nor_flash_sector_write** _: _Write eller Flash-sektor *

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Stäng eller Flash-instans

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger den tidigare öppnade eller Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash*: eller Flash instance-pekare.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att stänga Flash-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Defragmentera eller Flash-instans

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Beskrivning

Den här tjänsten defragmenterar den tidigare öppnade eller Flash-instansen. Defragmenteringen maximerar antalet kostnads fria sektorer och block.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash*: eller Flash instance-pekare.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Aktivera/inaktivera utökad eller cachelagring

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten implementerar ett-eller sektor cache-skikt i RAM-minnet med det minne som tillhandahålls av programmet. Varje 512 byte minne som tillhandahålls översätts till en eller sektor som kan cachelagras. De cachelagrade sektorerna är de som innehåller block kontroll information, t. ex., antal rader, kostnads fri sektor karta och information om sektor mappning. Data sektorer lagras inte i det här cacheminnet.

### <a name="input-parameters"></a>Indataparametrar

- **nor_flash**: eller Flash instance-pekare.  
- **minne**: Start adress för cache-minne, justerat för ulong-åtkomst. Värdet LX_NULL inaktiverar cacheminnet.  
- **storlek**: storleken i byte för det angivna minnet (bör vara flera av 512 byte).

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) det finns inte tillräckligt med minne för en eller sektor.
- **LX_DISABLED**: (0X09) eller utökad cache inaktiverat av konfigurations alternativ.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Initiera eller stöd för Flash

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar LevelX eller Flash-stöd. Den måste anropas före andra LevelX eller API: er.

### <a name="input-parameters"></a>Indataparametrar

- **Ingen**

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att initiera eller Flash-stöd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

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

Öppna eller Flash-instans

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Beskrivning

Den här tjänsten öppnar en eller Flash-instans med angivet eller Flash-kontroll block och driv rutins initierings funktionen. Observera att driv Rutinens initierings funktion ansvarar för att installera olika funktions pekare för att läsa, skriva och radera block av den eller maskin vara som är associerad med den här eller Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash*: eller Flash instance-pekare.
- *namn*: namnet på eller Flash-instansen.
- *nor_driver_initialize*: funktions pekare till eller Flash driver initierings funktion. Se kapitel 5 i den här hand boken om du vill ha mer information om eller driv rutins ansvar för Flash.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att öppna eller Flash-instansen.
- **LX_NO_MEMORY**: (0X08) driv rutinen tillhandahöll ingen buffert för att läsa någon sektor i RAM-minnet.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Partiell defragmentering av eller Flash-instans

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Beskrivning

Den här tjänsten defragmenterar den tidigare öppnade eller Flash-instansen upp till det maximala antalet block som anges. Defragmenteringen maximerar antalet kostnads fria sektorer och block.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash*: eller Flash instance-pekare.
- *max_blocks*: maximalt antal block.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Läs eller Flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser den logiska sektorn från eller Flash-instansen och returnerar innehållet i den angivna bufferten om det lyckas. Observera att eller sektor storlek alltid är 512 byte.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash* ELLER Flash instance-pekare.
- *logical_sector*: logisk sektor som ska läsas.
- *buffert*: pekare till målet för innehållet i den logiska sektorn. Observera att bufferten antas vara 512 byte och justerad för ULONG-åtkomst.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0x01) Det gick inte att läsa eller Flash-sektorn.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Utgåva eller Flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Beskrivning

Den här tjänsten släpper den logiska sektor mappningen i eller Flash-instansen. Att släppa en logisk sektor när den inte används gör att LevelX slitaget är mer effektivt.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash*: eller Flash instance-pekare.
- *logical_sector*: logisk sektor som ska frisläppas.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_ERROR**: (0X01) fel eller Flash-sektor skrivning.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Skriv-eller Flash-sektor

### <a name="prototype"></a>Prototyp

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skriver den angivna logiska sektorn i eller Flash-instansen.

### <a name="input-parameters"></a>Indataparametrar

- *nor_flash*: eller Flash instance-pekare.
- *logical_sector*: logisk sektor som ska skrivas.
- *Buffer*: pekar mot innehållet i den logiska sektorn. Observera att bufferten antas vara 512 byte justerad för ULONG-åtkomst.

### <a name="return-values"></a>Retur värden

- **LX_SUCCESS**: (0X00) lyckad begäran.
- **LX_NO_SECTORS**: (protokollnumret 0x02) det finns inga fler kostnads fria sektorer att utföra skrivningen.
- **LX_ERROR**: (0X01) fel vid fri släppning eller Flash-sektor.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
