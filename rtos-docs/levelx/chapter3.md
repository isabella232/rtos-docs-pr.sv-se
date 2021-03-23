---
title: Stöd för Azure återställnings tider LevelX-NAND
description: NAND Flash-minne används ofta i LevelX för stor data lagring, vilket är typiskt för fil system.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826268"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>Kapitel 3 – Azure återställnings tider LevelX NAND support

NAND Flash-minne används ofta för stor data lagring, vilket är typiskt för fil system. NAND-minnet består av *block*. I varje NAND-block finns en serie *sidor*. NAND-block kan raderas, vilket innebär att alla sidor i NAND-blocket raderas (inställda på alla). Varje NAND block-sida har en uppsättning med *extra byte* som används av Azure återställnings tider-LevelX för bokföring, felaktig block hantering och fel identifiering. NAND block Pages är tillgängliga i olika storlekar. De vanligaste sid storlekarna är: 

| **Sid storlek** | **Lediga byte** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

NAND-minnet skiljer sig från eller minne eftersom det inte finns någon direkt åtkomst, d.v.s. NAND-minnet kan inte läsas direkt från processorn som eller minne. NAND-minne kan bara skrivas till efter en radering av ett begränsat antal gånger. Återigen skiljer detta sig från eller minne som kan skrivas ett obegränsat antal gånger som ger skrivbegäran att ta bort uppsättnings bitar. Slutligen är de extra byte som är kopplade till varje sida unika för NAND Flash. Vanliga konfigurationer för extra byte är som visas i tabellen nedan.

| **Lediga byte** | **Byte-nummer** | **Konfiguration**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | Byte 0-2:     | ECC-byte             |
|                           | Byte 3, 4, 6, 7: | LevelX sektor mappning |
|                           | Byte 5:        | Felaktig block flagga        |
| 16                        | Byte 0-3, 6-7: | ECC-byte             |
|                           | Byte 8-11:    | LevelX sektor mappning |
|                           | Byte 12-15:   | Outnyttja                |
|                           | Byte 5:        | Felaktig block flagga        |
| 64                        | Byte 0:        | Felaktig block flagga        |
|                           | Byte 2-5:     | LevelX sektor mappning |
|                           | Byte 6-39:    | Outnyttja                |
|                           | Byte 40-63:   | ECC-byte             |

LevelX använder 4 av de extra bytena på varje NAND-sida för att hålla reda på den logiska sektor som är mappad till den fysiska NAND-sidan. Dessa 4 byte används för att implementera ett 32-bitars heltal utan tecken med ett LevelX-patentskyddat format. Den övre biten i 32-bitars fältet (bit 31) används för att ange att den logiska sektor-till-sidan-mappningen är giltig. Om den här biten är 0 är informationen på den här sidan inte längre giltig. Nästa bit – bit 30 – används för att ange att den här sidan håller på att bli föråldrad och att en ny sektor skrivs. Bit 29 används för att ange när mappnings post skrivningen är klar. Om bit 29 är 0, skrivs mappnings posten som färdig. Om bit 29 anges beskrevs mappnings posten under processen. BITS 30 och 29 används för återställning från en potentiell ström förlust när en ny Flash-sida uppdateras. Slutligen innehåller de lägre 29 bitarna (28-0) det logiska sektor numret för sidan.

**Mappnings post för LevelX**

| Bitar | Innebörd |
| ------ | ------- |
| 31     | Giltig flagga. Om uppsättningen och den logiska sektorn inte är alla anger att mappning är giltig |
| 30     | Föråldrad flagga. När det är klart är den här mappningen antingen föråldrad eller håller på att bli föråldrad. |
| 29     | Skrivning av mappnings post är slutförd när denna bit är 0 |
| 0-28   | Logisk sektor som är mappad till den här fysiska sidan – om de inte är alla. |

LevelX använder också den första sidan i varje NAND-block för antalet block radering och listan över mappade sidor när blocket är full. Formatet på den första sidan i ett NAND-block i LevelX visas nedan:

| LevelX block sid 0-format |
|:--------------------------:|
| [Antal block rader]        |
| [Mappning av sida 1-sektor]    |
| ...                        |
| [Sida "n" sektor mappning]  |
| [0xF0F0F0F0]               |

> [!NOTE]
> Sid mappnings informationen skrivs bara när blocket är full, d.v.s. alla sidor i blocket har skrivits till. Detta möjliggör snabbare sökning efter kostnads fria sidor och logisk sektor mappning under körnings tid.

## <a name="nand-bad-block-support"></a>NAND-stöd för dåligt block

NAND-minnet är också mer troligt för skadade block än eller minne. Detta beror på stora orsaker till att NAND-tillverkare kan öka kapaciteten genom att tillåta dåliga block och kräva att program varan fungerar runt sådana dåliga block. LevelX hanterar NAND felaktig block hantering genom att helt enkelt mappa runt felaktiga block.

LevelX innehåller också API: er för 256-byte Hamming fel korrigerings koder (ECC) för den underliggande LevelX-drivrutinen som används för att beräkna nya ECC-koder eller utföra 1-bitars fel korrigering på sid läsning i varje 256-byte-avsnitt på sidan.

## <a name="nand-driver-requirements"></a>NAND driv Rutins krav

LevelX kräver en underliggande NAND-Flash-drivrutin som är speciell för underliggande Flash-del och maskin varu implementering. Driv rutinen anges för LevelX vid initiering via API- ***lx_nand_flash_open***. Prototypen av LevelX-drivrutinen är följande.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

*Instans* parametern anger kontroll blocket LevelX NAND. Driv Rutinens initierings funktion ansvarar för att konfigurera alla andra tjänster på driv rutins nivå för den associerade LevelX-instansen. De tjänster som krävs för varje LevelX NAND-instans visas i listan nedan.

- Läs sida
- Skriv sida
- Blockera radering
- Blockera raderad verifiering
- Sidan togs bort, verifiera
- Blockera status Hämta
- Blockera status uppsättning
- Blockera extra byte Hämta
- Blockera extra byte, uppsättning
- System fel hanterare

## <a name="driver-initialization"></a>Driv rutins initiering

Dessa tjänster konfigureras genom att ställa in funktions pekare i **LX_NAND_FLASH** instansen i driv Rutinens initierings funktion. Driv Rutinens initierings funktion anger även det totala antalet block, sidor per block, byte per sida och ett RAM-utrymme som är tillräckligt stort för att läsa en sida i minnet. Initierings funktionen för driv rutiner utför troligen även ytterligare ytterligare enhets-och/eller implementerings åtgärder innan du returnerar **LX_SUCCESS**.

## <a name="driver-read-page"></a>Sidan driv rutins läsning

Tjänsten LevelX NAND driver "Read Page" ansvarar för att läsa en speciell sida i ett särskilt block i NAND-Flash. All fel kontroll och korrigerings logik är ansvaret för driv rutins tjänsten. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av LevelX NAND-drivrutinen "Read Page" anges nedan.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

Där *block* och *sida* identifierar vilken sida som ska läsas *och anges* var du ska placera sid *innehållet och hur* många 32-bitars ord som ska läsas.

## <a name="driver-write-page"></a>Sidan driv rutins skrivning

LevelX NAND-driv rutinen "Skriv Page" ansvarar för att skriva en specifik sida till det angivna blocket av NAND-Flash. All fel kontroll och ECC-beräkning är ansvaret för driv rutins tjänsten. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten LevelX NAND driver "Skriv Page" visas nedan.

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

Där *block* och *sida* identifierar vilken sida som ska skrivas och *källa* och *ord* anger källan för skrivning och hur många 32-bitars ord som ska skrivas.

> [!NOTE]
> LevelX förlitar sig på driv rutinen för identifiering av fel på låg nivå vid skrivning till Flash-sidan, vilket vanligt vis innebär att läsa sidan och jämföra med Write buffer för att säkerställa att skrivningen lyckades.

## <a name="driver-block-erase"></a>Radera driv rutins block

LevelX NAND-driv rutinen "blockera radering" ansvarar för att radera det angivna blocket av NAND-Flash. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten LevelX NAND driv rutin "blockera radering" är följande.

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Där *block* identifierar vilket block som ska raderas. Parametern *erase_count* anges i diagnostiskt syfte. Driv rutinen kan till exempel vilja varna en annan del av program varan när antalet rader överskrider ett angivet tröskelvärde.

> [!NOTE]
> LevelX förlitar sig på driv rutinen för fel avkänning på låg nivå när blocket raderas, vilket vanligt vis innebär att alla sidor i blocket är alla.

## <a name="driver-block-erased-verify"></a>Borttagning av driv rutins block

LevelX NAND-driv rutinen "blockera raderad verifiering" ansvarar för att verifiera att det angivna blocket av NAND-blixten raderas. Om den raderas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om blocket inte raderas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av LevelX NAND-drivrutinen "blockera raderad verifiering" är:

```c
INT nand_driver_block_erased_verify(ULONG block);
```

Where- *block* anger vilket block som ska kontrol lera att den raderas.

> [!NOTE]
> LevelX förlitar sig på driv rutinen för att undersöka alla sidor och alla byte på varje sida, inklusive reserv-och data byte – så att de raderas (innehåller alla).

## <a name="driver-page-erased-verify"></a>Kontrollen av driv rutins sidan har raderats

Sidan LevelX NAND-driv rutinen är inte ansvarig för att verifiera att den angivna sidan i det angivna blocket av NAND-Flash raderas. Om den raderas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om sidan inte raderas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av LevelX NAND-driv rutinen "sida som rensats" är:

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
Where- *block* anger vilket block och vilken *sida* som anger sidan för att kontrol lera att den raderas.

> [!NOTE]
> LevelX förlitar sig på driv rutinen för att undersöka alla byte på den angivna sidan, inklusive reserv-och data byte, för att se till att de raderas (innehåller alla).

## <a name="driver-block-status-get"></a>Status för driv rutins block

LevelX NAND-drivrutin för "blockera status" är ansvarig för att hämta den felaktiga block flaggan för det angivna blocket av NAND-Flash. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten LevelX NAND driver "Get" är: visas nedan.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

Where- *block* anger vilka block och *bad_block_byte* anger målet för den felaktiga block flaggan.

## <a name="driver-block-status-set"></a>Status uppsättning för driv rutins block

Tjänsten LevelX NAND driver "block status uppsättning" ansvarar för att ställa in flaggan för felaktig block för det angivna blocket av NAND-Flash. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten LevelX NAND driver "block status uppsättning" är:

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

Where- *block* anger vilka block och *bad_block_byte* anger värdet för den felaktiga block flaggan.

## <a name="driver-block-extra-bytes-get"></a>Extra byte Hämta driv rutins block

LevelX NAND driv rutinen "blockera extra bytes get" ansvarar för att hämta extra byte som är kopplade till en speciell sida i ett särskilt block i NAND-Flash. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten LevelX NAND driver "blockera extra bytes get" är:

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

Where- *block* anger vilket block, *sidan* anger den särskilda sidan och *målet* anger målet för extra byte. Parameter *storleken* anger hur många extra byte som ska hämtas.

## <a name="driver-block-extra-bytes-set"></a>Extra byte som har angetts för driv rutins block

LevelX NAND driv rutinen "blockera extra bytes set" ansvarar för att ställa in extra byte på en speciell sida i ett särskilt block av NAND-Flash. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten LevelX NAND driv rutin "blockera extra byte uppsättning" är:

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

Where- *block* anger vilket block, *sidan* anger den särskilda sidan och *källan* anger källan för de extra byte. Parameter *storleken* anger hur många extra byte som ska anges.

## <a name="driver-system-error"></a>Driv rutins system fel

LevelX NAND-drivrutinen för system fel hanterare ansvarar för att ställa in hantering av systemfel som upptäckts av LevelX. Bearbetningen i den här rutinen är beroende av program. Om det lyckas returnerar driv rutinen LevelX NAND **LX_SUCCESS**. Om det inte lyckas returnerar driv rutinen LevelX NAND **LX_ERROR**. Prototypen av tjänsten System Error för LevelX NAND-drivrutinen är:

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

Where- *block* anger vilket block, och *sidan* anger den sida som felet representeras av *error_code* uppstod.

## <a name="nand-simulated-driver"></a>NAND-simulerad driv rutin

LevelX tillhandahåller en simulerad NAND-Flash-drivrutin som bara använder RAM för att simulera åtgärden för en NAND-Flash-del. Som standard tillhandahåller den NAND simulerade driv rutinen 8 NAND Flash-block med 16 sidor per block och 2048 byte per sida.

Initierings funktionen för den simulerade NAND-Flash-drivrutinen är ***lx_nand_flash_simulator_initialize** _ och definieras i _ *_lx_nand_flash_simulator. c_* *. Den här driv rutinen innehåller också en lämplig mall för att skriva vissa Flash-drivrutiner för NAND.

## <a name="nand-filex-integration"></a>NAND FileX-integrering

Som tidigare nämnts förlitar sig LevelX inte på FileX för åtgärd. Alla LevelX-API: er kan anropas direkt av program varan för att lagra/Hämta rå data till de logiska sektorerna som tillhandahålls av LevelX. LevelX stöder dock också FileX.

Filen ***fx_nand_flash_simulated_driver. c*** innehåller ett exempel på en FileX-drivrutin för användning med Flash-simuleringen NAND. En intressant aspekt av den här driv rutinen är att den kombinerar 512 bytes logiska sektorer som vanligt vis används av FileX i en enda logisk sektor Läs-/skriv förfrågningar till LevelX-simulatorn med hjälp av 2048 byte-sidor. Detta ger en mer effektiv användning av NAND Flash-minnet. NAND Flash FileX-drivrutinen för LevelX är en välstarts punkt för att skriva anpassade FileX-drivrutiner.  
  
> [!NOTE]
> FileX NAND Flash-formatet bör vara en fullständig block storlek på sektorer som är mindre än NAND Flash. Detta bidrar till att garantera bästa prestanda under belastnings nivån för slitage. Ytterligare metoder för att förbättra skriv prestanda i LevelX-slitage är följande.

1. Se till att alla skrivningar är exakt ett eller flera kluster i storlek och starta på exakta kluster gränser.
1. Förallokera kluster innan du utför stora fil skrivnings åtgärder via FileX ***fx_file_allocate*** -klassen för API: er.
1. Se till att FileX-drivrutinen är aktive rad för att ta emot information om versions sektorn och förfrågningar som görs till driv rutinen för att frigöra sektorer i driv rutinen genom att anropa ***lx_nor_flash_sector_release***.
1. Regelbunden användning av ***lx_nand_flash_defragment*** för att frigöra så många NAND block som möjligt och därmed förbättra skriv prestanda.
1. Använd ***lx_nand_flash_extended_cache_enable*** API för att tillhandahålla en ram-cache med olika NAND-block resurser för snabbare prestanda.
