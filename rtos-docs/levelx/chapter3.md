---
title: Azure RTOS LevelX SÅDD-stöd
description: FLASH-minne används ofta i LevelX för stor datalagring, vilket är typiskt för filsystem.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 950a4f260d032ebe032aca79ac99cc8217915a3b21b230be9475d82b267da18c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790589"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>Kapitel 3 – Azure RTOS LevelXSKAPAD-stöd

FLASH-minne används ofta för stor datalagring, vilket är typiskt för filsystem. TIDSD-minne består av *block*. Inom varje BLOCKETD-block finns en serie *sidor*. PORD-block kan raderas, vilket innebär att alla sidor i BLOCKD-blocket raderas (inställt på alla). Varje KANT-blocksida har  en uppsättning reservbyte som används av Azure RTOS LevelX för bokföring, felaktig blockhantering och felidentifiering. UTT-blocksidor är tillgängliga i olika storlekar. De vanligaste sidstorlekarna är: 

| **Sidstorlek** | **Reservbyte** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

TIDSD-minnet skiljer sig från NOR-minnet på så sätt att det inte finns någon direkt åtkomst, det vill säga att KAN INTE LÄSA MINNE direkt från processorn, t.ex. NOR-minne. MAND-minne kan bara skrivas till efter en radering ett begränsat antal gånger. Detta skiljer sig återigen från NOR-minnet som kan skrivas ett obegränsat antal gånger, förutsatt att skrivbegäran rensar uppsättningen bitar. Slutligen är de reservbyte som är associerade med varje sida unika för UTSP-flash. Vanliga reservbyteskonfigurationer visas i tabellen nedan.

| **Reservbyte** | **Bytenummer** | **Konfiguration**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | Byte 0–2:     | ECC-byte             |
|                           | Byte 3,4,6,7: | LevelX-sektormappning |
|                           | Byte 5:        | Felaktig blockflagga        |
| 16                        | Byte 0-3,6-7: | ECC-byte             |
|                           | Byte 8–11:    | LevelX-sektormappning |
|                           | Byte 12–15:   | Oanvända                |
|                           | Byte 5:        | Felaktig blockflagga        |
| 64                        | Byte 0:        | Felaktig blockflagga        |
|                           | Byte 2–5:     | LevelX-sektormappning |
|                           | Byte 6–39:    | Oanvända                |
|                           | Byte 40–63:   | ECC-byte             |

LevelX använder 4 av reservbytena för varje UTSP-sida för att hålla reda på den logiska sektorn som är mappad till den fysiska UTSP-sidan. Dessa 4 byte används för att implementera ett 32-bitars heltal utan tecken med ett levelX-upphovsrättsskyddat format. Den övre delen av 32-bitarsfältet (bit 31) används för att ange att den logiska sektor-till-sidan-mappningen är giltig. Om den här biten är 0 är informationen på den här sidan inte längre giltig. Nästa bit – bit 30 – används för att visa att den här sidan håller på att bli föråldrad och att en ny sektor håller på att skrivas. Bit 29 används för att ange när mappningspostskrivningen är klar. Om bit 29 är 0 är mappningspostskrivningen slutförd. Om bit 29 har angetts håller mappningsposten på att skrivas. Bitarna 30 och 29 används för att återställa från en potentiell strömförlust när du uppdaterar en ny flash-sida. Slutligen innehåller de lägre 29-bitars (28–0) sidans logiska sektornummer.

**LevelX-mappningspost**

| Bitar | Innebörd |
| ------ | ------- |
| 31     | Giltig flagga. När den här uppsättningen och den logiska sektorn inte är alla indikerar mappningen är giltig |
| 30     | Föråldrad flagga. När det är klart är mappningen antingen föråldrad eller håller på att bli föråldrad. |
| 29     | Skrivning av mappningspost är klar när den här biten är 0 |
| 0-28   | Logisk sektor mappad till den här fysiska sidan – när inte alla. |

LevelX använder också den första sidan i varje UTT-block för antalet radering av block samt listan över mappade sidor när blocket är fullt. Formatet på den första sidan i ett UTTR-block i LevelX visas nedan:

| LevelX Block Page 0-format |
|:--------------------------:|
| [Block Erase Count]        |
| [Sektormappning på sida 1]    |
| ...                        |
| [Sida "n" Sektormappning]  |
| [0xF0F0F0F0]               |

> [!NOTE]
> Sidmappningsinformationen skrivs bara när blocket är fullt, det vill säga att alla sidor i blocket har skrivits till. Detta möjliggör snabbare sökning efter kostnadsfria sidor och logisk sektormappning under körning.

## <a name="nand-bad-block-support"></a>INTR-stöd för felaktigt block

DET är också mer troligt att det finns skadade block än NOR-minne. Detta beror till stor del på att MAND-tillverkare kan öka avkastningen genom att tillåta dåliga block och kräva att programvara kan komma runt sådana dåliga block. LevelX hanterar DENDD-dåliga blockhanteringen genom att helt enkelt mappa runt dåliga block.

LevelX tillhandahåller även API:er för ECC (256 byte Hamming Error Correction Codes) för den underliggande LevelX-drivrutinen för beräkning av nya ECC-koder eller för att utföra 1-bitars felkorrigering på sidläsning inom varje 256 byte-avsnitt på sidan.

## <a name="nand-driver-requirements"></a>INFORMATIONSFÖRD-drivrutinskrav

LevelX kräver en underliggande FLASH-drivrutin som är specifik för den underliggande flash-delen och maskinvaruimplementering. Drivrutinen anges till LevelX under initieringen via ***API:et lx_nand_flash_open***. Prototypen av LevelX-drivrutinen är följande.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

*Instansparametern* anger kontrollblocket LevelXSTYRT. Initieringsfunktionen för drivrutinen ansvarar för att konfigurera alla andra tjänster på drivrutinsnivå för den associerade LevelX-instansen. De tjänster som krävs för varje LevelX UTT-instans visas i listan nedan.

- Lässida
- Skrivsida
- Blockera radering
- Blockera raderad verifiering
- Raderad sida Verifiera
- Blockera status hämta
- Blockera statusuppsättning
- Block Extra Bytes Get
- Blockera extra byte som angetts
- Systemfelhanterare

## <a name="driver-initialization"></a>Drivrutinsinitiering

Dessa tjänster konfigureras via inställning av **funktionspekare i LX_NAND_FLASH instansen** i drivrutinens initieringsfunktion. Funktionen för drivrutinsinitiering anger också det totala antalet block, sidor per block, byte per sida och ett RAM-område som är tillräckligt stort för att läsa en sida i minnet. Initieringsfunktionen för drivrutinen utför sannolikt även ytterligare enhets- och/eller implementeringsspecifika initieringsuppgifter innan den returnerar **LX_SUCCESS**.

## <a name="driver-read-page"></a>Läsa drivrutinssida

LevelXLICD-drivrutinens "lässida"-tjänst ansvarar för att läsa en specifik sida i ett visst block av FLASH-flashminnet. All felkontroll och korrigeringslogik är drivrutinstjänstens ansvar. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till levelX HART-drivrutinstjänsten "read page" anges nedan.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

Där *block* och *sida identifierar*  vilken  sida som ska läsas och mål och ord anger var sidinnehållet ska placeras och hur många 32-bitars ord som ska läsas.

## <a name="driver-write-page"></a>Skrivsida för drivrutin

LevelXLICD-drivrutinens "skrivsida"-tjänst ansvarar för att skriva en specifik sida till det angivna block av FLASH-flash-blocket. All felkontroll och ECC-beräkning är drivrutinstjänstens ansvar. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen av levelX HART-drivrutinstjänsten för "skrivsida" visas nedan.

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

Där *block* och *sida* identifierar  vilken  sida som ska skrivas och källa och ord anger källan för skrivning och hur många 32-bitars ord som ska skrivas.

> [!NOTE]
> LevelX förlitar sig på drivrutinen för felidentifiering på låg nivå vid skrivning till flash-sidan, vilket vanligtvis innebär att läsa tillbaka sidan och jämföra med skrivbufferten för att säkerställa att skrivningen lyckades.

## <a name="driver-block-erase"></a>Radera drivrutinsblock

LevelXLICD-drivrutinens "blockradering"-tjänst ansvarar för att radera det angivna block av FLASH-flashminnet. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till LevelX HARRD-drivrutinens "blockraderingstjänst" är följande.

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Där *blocket* identifierar vilket block som ska raderas. Parametern *erase_count* anges i diagnostiskt syfte. Drivrutinen kanske till exempel vill varna en annan del av programprogramvaran när raderingsantalet överskrider ett visst tröskelvärde.

> [!NOTE]
> LevelX förlitar sig på drivrutinen för felidentifiering på låg nivå när blocket raderas, vilket vanligtvis innebär att alla sidor i blocket är ett enda.

## <a name="driver-block-erased-verify"></a>Drivrutinsblock – Raderad verifiering

LevelXLICD-drivrutinens tjänst "blockera bort raderad verifiering" ansvarar för att verifiera att det angivna block av FLASH-flashminnet raderas. Om den raderas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om blocket inte raderas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till LevelX HARRD-drivrutinens tjänst "blockera bort raderad verifiering":

```c
INT nand_driver_block_erased_verify(ULONG block);
```

Där *blocket* anger vilket block som ska verifieras att det raderas.

> [!NOTE]
> LevelX förlitar sig på att drivrutinen undersöker alla sidor och alla byte på varje sida, inklusive reserv- och databyte, för att säkerställa att de raderas (innehåller alla ettor).

## <a name="driver-page-erased-verify"></a>Kontrollera att drivrutinssidan har raderats

LevelXLICD-drivrutinens tjänst "page erased verify" ansvarar för att verifiera att den angivna sidan i det angivna blocket i FLASH-flashminnet raderas. Om den raderas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om sidan inte raderas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till levelX HARTR-drivrutinens tjänst "page erased verify" är:

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
Där *block* anger vilket block och *vilken sida* som anger vilken sida som ska verifieras att den raderas.

> [!NOTE]
> LevelX förlitar sig på att drivrutinen undersöker alla byte på den angivna sidan, inklusive reserv- och databyte, för att säkerställa att de raderas (innehåller alla ettor).

## <a name="driver-block-status-get"></a>Status för drivrutinsblock hämta

LevelXLICD-drivrutinens "block status get"-tjänst ansvarar för att hämta den skadliga blockflaggan för det angivna blocket i FLASH-flash- och flashminnet. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till levelX HART-drivrutinens "blockstatus get"-tjänst: visas nedan.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

Där *block* anger vilket block och *bad_block_byte* anger målet för den dåliga blockflaggan.

## <a name="driver-block-status-set"></a>Statusuppsättning för drivrutinsblock

LevelXLICD-drivrutinens "blockstatusuppsättning"-tjänst ansvarar för att ange felaktig blockflagga för det angivna block av FLASH-flash-blocket. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till LevelX HARTD-drivrutinens "blockstatusuppsättning"-tjänst är:

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

Där *block* anger vilket block och *bad_block_byte* anger värdet för den dåliga blockflaggan.

## <a name="driver-block-extra-bytes-get"></a>Extra byte för drivrutinsblock hämta

LevelXLICD-drivrutinens tjänst "block extra bytes get" ansvarar för att hämta extra byte som är associerade med en specifik sida i ett visst block av FLASH-flash. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till LevelX FÖRD-drivrutinens "block extra byte get"-tjänst är:

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

Om *blocket* anger vilket *block, anger* sidan den specifika sidan och *målet* målet för de extra bytena. Parameterstorleken *anger* hur många extra byte som ska fås.

## <a name="driver-block-extra-bytes-set"></a>Extra byte för drivrutinsblock har angetts

Servicen "block extra byte set" för LevelXLICD-drivrutinen ansvarar för att ställa in extra byte på en specifik sida i ett visst block av FLASH-blocket. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till levelX HART-drivrutinens "block extra byte set"-tjänst är:

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

Där *block* anger vilket block, *anger* sidan den specifika sidan och *källan* anger källan för de extra bytena. Parameterstorleken *anger* hur många extra byte som ska anges.

## <a name="driver-system-error"></a>Drivrutinssystemfel

Servicen "systemfelhanterare" för LevelXUPPD-drivrutinen ansvarar för att ställa in hantering av systemfel som identifieras av LevelX. Bearbetningen i den här rutinen är programberoende. Om det lyckas returnerar LevelX HARD-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX HARD-drivrutinen **LX_ERROR**. Prototypen till LevelX HARGD-drivrutinens "systemfel"-tjänst är:

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

Där *block* anger vilket block och *sida anger* den specifika sida som felet som representeras av *error_code* inträffade.

## <a name="nand-simulated-driver"></a>SIMULERAD simulerad drivrutin

LevelX tillhandahåller en simulerad FLASH-drivrutin som helt enkelt använder RAM-minne för att simulera driften av en FLASH-del. Som standard tillhandahåller DEN simulerade DRIVRUTINEN 8 FLASH-block MED 16 sidor per block och 2 048 byte per sida.

Initieringsfunktionen för simulerad FLASH-drivrutin är ***lx_nand_flash_simulator_initialize** _ och definieras i _*_lx_nand_flash_simulator.c_**. Den här drivrutinen är också en bra mall för att skriva specifika FLASH-drivrutiner.

## <a name="nand-filex-integration"></a>KAND FileX-integrering

Som tidigare nämnts förlitar sig LevelX inte på FileX för drift. Alla LevelX-API:er kan anropas direkt av programmet för att lagra/hämta rådata till de logiska sektorer som tillhandahålls av LevelX. LevelX stöder dock även FileX.

Filen ***fx_nand_flash_simulated_driver.c innehåller ett*** exempel på en FileX-drivrutin för användning med FLASH-simuleringen AV FLASH. En intressant aspekt av drivrutinen är att den kombinerar logiska 512 byte-sektorer som vanligtvis används av FileX till skriv-/läs-/skrivbegäranden för en logisk sektor till LevelX-simulatorn med 2 048 byte-sidor. Detta resulterar i en effektivare användning av FLASH-minnet. FLASH FileX-drivrutinen för LevelX är en bra utgångspunkt för att skriva anpassade FileX-drivrutiner.  
  
> [!NOTE]
> Flash-formatet FileX USBD ska vara en full blockstorlek på sektorer som är mindre än VAD SOM flash-blinkar. På så sätt får du bästa möjliga prestanda under bearbetningen av förslitningsnivån. Ytterligare tekniker för att förbättra skrivprestanda i LevelX-algoritmen för utslitning är följande.

1. Se till att alla skrivningar är exakt ett eller flera kluster i storlek och starta vid exakta klustergränser.
1. Allokera kluster i förväg innan du utför stora  filskrivningsåtgärder via FileX-fx_file_allocate av API:er.
1. Se till att FileX-drivrutinen är aktiverad för att ta emot information om utgivningssektor och att begäranden som görs till drivrutinen för att frigöra sektorer hanteras i drivrutinen genom att ***anropa lx_nor_flash_sector_release***.
1. Regelbunden användning av ***lx_nand_flash_defragment*** att frigöra så många BLOCKD-block som möjligt och därmed förbättra skrivprestanda.
1. Använd  lx_nand_flash_extended_cache_enable-API:et för att tillhandahålla en RAM-cache med olika CACHE-blockresurser för snabbare prestanda.
