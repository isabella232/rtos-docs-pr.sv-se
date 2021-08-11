---
title: Kapitel 5 – Azure RTOS LevelX NOR-stöd
description: FLASH-minnet består inte av block som vanligtvis är jämnt delbara med 512 byte. Azure RTOS LevelX delar in varje NOR-flashblock i logiska sektorer med 512 byte.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5d06fa66f0cae29eeb2a89560704b2ef510597e44a565499bf672a75555f208
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790572"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>Kapitel 5 – Azure RTOS LevelX NOR-stöd

FLASH-minnet består inte av *block* som vanligtvis är jämnt delbara med 512 byte. Det finns inget begrepp för en *flash-sida i* NOR-flashminnet. Dessutom finns det inga *reservbyte* i NOR flashminnet, Azure RTOS levelX måste använda själva NOR-flashminnet för all hanteringsinformation. Direkt läsåtkomst är möjligt i NOR-flashminnet. Skrivåtkomst kräver vanligtvis en särskild sekvens med åtgärder. FLASH-minnet kan inte skrivas till flera gånger, förutsatt att bitar rensas. Bits in NOR flash memory can only be set once, via the erase block operation.

LevelX delar in varje NOR-flashblock i logiska sektorer på 512 *byte.* Dessutom använder LevelX de första "n"-sektorerna i varje NOR-flashblock för att lagra hanteringsinformation. Formatet för informationen om flashminneshantering på LevelX NOR är:

**Blockformat för LevelX NOR**

| Byteförskjutning  | Innehåll                     |
| ------------ | ---------------------------- |
| 0            | [Block Erase Count]          |
| 4            | [Minsta mappade sektor]      |
| 8            | [Maximal mappad sektor]      |
| 12           | [Bitkarta för kostnadsfri sektor]        |
| m            | [Mappningspost för sektor 0]     |
|              | …                            |
| m+4*(n-1)    | [Sektormappningspost "n" ]   |
|              | …                            |
| s            | [Sektor 0-innehåll]          |
|              | …                            |
| s+512*(n-1) | [Sektorinnehåll "n" ]         |

32-bitars *blockraderingsantalet* innehåller antalet gånger som blocket har raderats. Huvudmålet med LevelX är att hålla raderingsantalet av alla block relativt nära för att förhindra att ett enda block används i förtid. Fälten 32-bitars *lägsta mappade* sektor och Högsta *mappade sektor* skrivs bara när alla logiska sektorer i blocket har mappats och skrivits till. De här fälten är användbara för optimering av sektorläsningsåtgärden. Posten *Bitkarta för den kostnadsfria* sektorn är en bitmappning där varje bit som anges motsvarar en omappad sektor i blocket. Det här fältet används för att göra sökningen i den kostnadsfria sektorn effektivare. Det här är ett fält med variabel längd som kräver ett ord för var 32:e sektor i blocket. Matrisen *Sektormappningspost* innehåller mappningsinformation för varje sektor i blocket. Varje post har följande format:

**Post för sektormappning**

| Bitar | Innebörd  |
| ------ | -------- |
| 31     | Giltig flagga. När den här uppsättningen och den logiska sektorn inte alla indikerar att mappningen är giltig |
| 30     | Föråldrad flagga. När det är klart är mappningen antingen föråldrad eller håller på att bli föråldrad. |
| 29     | Skrivning av mappningspost är klar när den här biten är 0 |
| 0-28   | Logisk sektor mappad till den här fysiska sektorn – när inte alla. |

Den övre delen av 32-bitarsfältet (bit 31) används för att ange att mappningen av den logiska sektorn är giltig. Om den här biten är 0 är informationen i den här posten (och motsvarande sektorinnehåll) inte längre giltig. Nästa bit – bit 30 – används för att ange att den här sektorn håller på att bli föråldrad och att en ny sektor skrivs. Bit 29 används för att ange när mappningspostskrivningen är klar. Om bit 29 är 0 är mappningspostskrivningen slutförd. Om bit 29 har angetts håller mappningsposten på att skrivas. Bitarna 30 och 29 används för att återställa från en potentiell strömförlust när en ny sektormappning uppdateras. Slutligen innehåller de lägre 29-bitars (28–0) det logiska sektornumret för sektorn. Om en sektor inte har mappats anges alla bitar, det vill säga att den har värdet 0xFFFFFFFF.

## <a name="nor-driver-requirements"></a>DRIVRUTINSKRAV FÖR NOR

LevelX kräver en underliggande NOR-flashdrivrutin som är specifik för den underliggande flash-delen och maskinvaruimplementering. Drivrutinen anges till LevelX under initieringen via ***API-lx_nor_flash_open***. Prototypen för LevelX-drivrutinen är:

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

Parametern "*instans*" anger nivåX NOR-kontrollblocket. Initieringsfunktionen för drivrutiner ansvarar för att konfigurera alla andra tjänster på drivrutinsnivå för den associerade LevelX-instansen. De tjänster som krävs för varje LevelX NOR-instans är:

- Lässektor
- Skrivsektor
- Blockera radering
- Blockera raderad verifiering
- Systemfelhanterare

## <a name="driver-initialization"></a>Initiering av drivrutin

Dessa tjänster konfigureras via inställning av **funktionspekare LX_NOR_FLASH** instansen i drivrutinens initieringsfunktion. Initieringsfunktionen för drivrutinen ansvarar också för:

1. Ange flash-basadressen.
1. Ange det totala antalet block och antalet ord per block.
1. En RAM-buffert för läsning av en flash-sektor (512 byte) och justerad för ULONG-åtkomst.

Initieringsfunktionen för drivrutinen utför sannolikt även ytterligare enhets- och/eller implementeringsspecifika initieringsuppgifter innan den returnerar **LX_SUCCESS**.

## <a name="driver-read-sector"></a>Sektor för drivrutinsläsning

LevelX NOR-drivrutinens "lässektor"-tjänst ansvarar för läsning av en specifik sektor i ett visst block av FLASH-flash- eller flash-programmet. All felkontroll och korrigeringslogik är drivrutinstjänstens ansvar. Om det lyckas returnerar LevelX NOR-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX NOR-drivrutinen *LX_ERROR*. Prototypen för levelX NOR-drivrutinens "lässektor"-tjänst är:

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

Där "*flash_address*" anger adressen till en logisk sektor inom ett NOR flash-block av minne och "*mål*" och *"* ord " anger var sektorinnehållet ska placeras och hur många 32-bitars ord som ska läsas.

## <a name="driver-write-sector"></a>Skrivsektor för drivrutin

LevelX NOR-drivrutinens "skrivsektor"-tjänst ansvarar för att skriva en specifik sektor till ett block av NOR Flash. All felkontroll är drivrutinstjänstens ansvar. Om det lyckas returnerar LevelX NOR-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX NOR-drivrutinen **LX_ERROR**. Prototypen till levelX NOR-drivrutinens "skrivsektor"-tjänst är:

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

Där "*flash_address*" anger adressen till en logisk sektor inom ett NOR flash-block av minne och *"* källa " och *"* ord " anger källan för skriven och hur många 32-bitars ord som ska skrivas.

> [!NOTE]
> LevelX förlitar sig på drivrutinen för att verifiera att skrivsektorn lyckades. Detta görs vanligtvis genom att läsa tillbaka det programmerade värdet för att se till att det matchar det begärda värdet som ska skrivas.

## <a name="driver-block-erase"></a>Radera drivrutinsblock

LevelX NOR-drivrutinens "blockradering"-tjänst ansvarar för att radera det angivna blocket av NOR-flash. Om det lyckas returnerar LevelX NOR-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX NOR-drivrutinen **LX_ERROR**. Prototypen för LevelX NOR-drivrutinens "blockradering"-tjänst är:

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Där *"block"* identifierar vilket NOR-block som ska raderas. Parametern "*erase_count*" anges i diagnostiskt syfte. Drivrutinen kanske till exempel vill varna en annan del av programprogramvaran när raderingsantalet överskrider ett visst tröskelvärde.

> [!NOTE]
> LevelX förlitar sig på att drivrutinen undersöker alla byte i blocket för att säkerställa att de raderas (innehåller alla ettor).

## <a name="driver-block-erased-verify"></a>Raderad verifiering av drivrutinsblock

LevelX NOR-drivrutinens tjänst "blockera raderad verifiering" ansvarar för att verifiera att det angivna flash-blocket NOR raderas. Om den raderas returnerar LevelX NOR-drivrutinen **LX_SUCCESS**. Om blocket inte raderas returnerar LevelX NOR-drivrutinen **LX_ERROR**. Prototypen av levelX NOR-drivrutinens tjänst "block erased verify" (blockera raderad verifiering):

```c
INT nor_driver_block_erased_verify(ULONG block);
```

*"Block"* anger vilket block som ska verifieras att det raderas.

> [!NOTE]
> LevelX förlitar sig på att drivrutinen undersöker alla byte för angivna för att säkerställa att de raderas (innehåller alla ettor).

## <a name="driver-system-error"></a>Drivrutinssystemfel

LevelX NOR-drivrutinens "systemfelhanterare" ansvarar för att ange hantering av systemfel som identifieras av LevelX. Bearbetningen i den här rutinen är programberoende. Om det lyckas returnerar LevelX NOR-drivrutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX NOR-drivrutinen **LX_ERROR**. Prototypen av levelX NOR-drivrutinens "systemfel"-tjänst är:

```c
INT nor_driver_system_error(UINT error_code);
```

Där "*error_code*" representerar det fel som inträffade.

## <a name="nor-simulated-driver"></a>NOR-simulerad drivrutin

LevelX tillhandahåller en simulerad NOR-flashdrivrutin som helt enkelt använder RAM-minne för att simulera driften av en NOR-flash-del. Som standard tillhandahåller den SIMULERADE DRIVRUTINEN NOR 8 NOR-flashblock med 16 512 byte-sektorer per block.

Initieringsfunktionen för den simulerade NOR-flashdrivrutinen är ***lx_nor_flash_simulator_initialize** _ och definieras i _*_lx_nor_flash_simulator.c_**. Den här drivrutinen innehåller också en bra mall för att skriva specifika NOR flash-drivrutiner.

## <a name="nor-filex-integration"></a>NOR FileX-integrering

Som tidigare nämnts förlitar sig LevelX inte på FileX för drift. Alla LevelX-API:er kan anropas direkt av programmets programvara för att lagra/hämta rådata till de logiska sektorer som tillhandahålls av LevelX. LevelX stöder dock även FileX.

Filen ***fx_nor_flash_simulated_driver.c innehåller ett*** exempel på en FileX-drivrutin för användning med FLASH-simuleringEN NOR. NOR Flash FileX-drivrutinen för LevelX är en bra utgångspunkt för att skriva anpassade FileX-drivrutiner.

> [!NOTE]
> Flash-formatet FileX NOR ska vara en fullständig blockstorlek för sektorer som är mindre än VAD SOM finns i NOR Flash. Detta hjälper till att säkerställa bästa prestanda under bearbetningen av förslitningsnivån. Ytterligare tekniker för att förbättra skrivprestanda i LevelX-algoritmen för förslitning är:
> 1. Se till att alla skrivningar är exakt ett eller flera kluster i storlek och börja med exakta klustergränser.
> 2. Allokera kluster i förväg innan du utför stora  filskrivningsåtgärder via FileX-fx_file_allocate av API:er.
> 3.  Regelbunden användning av ***lx_nor_flash_defragment*** att frigöra så många NOR-block som möjligt och därmed förbättra skrivprestanda.
> 4. Se till att FileX-drivrutinen är aktiverad för att ta emot information om utgivningssektor och att begäranden som görs till drivrutinen för att frigöra sektorer hanteras i drivrutinen genom att ***anropa lx_nor_flash_sector_release***.
