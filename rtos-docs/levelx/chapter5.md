---
title: Kapitel 5 – Azure återställnings tider LevelX eller support
description: ELLER Flash-minnet består av block som vanligt vis är jämnt delbar med 512 byte. Azure återställnings tider LevelX delar upp varje eller Flash-block i logiska sektorer i 512 byte.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3a0c73c2b45c32bf3f1ef56de684fa83c334b59e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826259"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>Kapitel 5 – Azure återställnings tider LevelX eller support

ELLER Flash-minnet består av *block* som vanligt vis är jämnt delbar med 512 byte. Det finns inget begrepp för en Flash- *sida* i eller Flash-minne. Det finns inte heller några *extra* byte i eller Flash-minne, och därför måste Azure återställnings tider-LevelX använda sig av själva Flash-minnet för all hanterings information. Direkt Läs behörighet är möjlig i eller Flash-minne. Skriv åtkomst kräver vanligt vis en speciell sekvens med åtgärder. ELLER så kan Flash-minnet skrivas till flera gånger, vilket innebär att BITS rensas. BITS i eller Flash-minne kan bara anges en gång, via åtgärden Radera block.

LevelX delar upp varje eller Flash-block i logiska *sektorer* i 512 byte. Dessutom använder LevelX de första "n" sektorerna för varje eller Flash-block för att lagra hanterings information. Formatet på LevelX eller Flash minnes hanterings information är:

**LevelX eller block format**

| Byte förskjutning  | Innehåll                     |
| ------------ | ---------------------------- |
| 0            | [Antal block rader]          |
| 4            | [Minsta mappad sektor]      |
| 8            | [Maximal mappad sektor]      |
| 12           | [Bit karta över kostnads fri sektor]        |
| m            | [Mappnings post för sektor 0]     |
|              | …                            |
| m + 4 * (n-1)    | [Sektor "n"-mappnings post]   |
|              | …                            |
| s            | [Innehåll i sektor 0]          |
|              | …                            |
| s + 512 * (n-1) | [Sektor "n"-innehåll]         |

*Antalet rader* i 32-bitars block innehåller antalet gånger som blocket har raderats. Huvud målet för LevelX är att behålla antalet rader för att ta bort alla block relativt nära för att förhindra att ett block utnyttjas för tidigt. De 32-bitars *lägsta mappade* sektorerna och de *maximalt mappade sektor* fälten skrivs bara när alla logiska sektorer i blocket har mappats och skrivits till. Dessa fält är användbara för optimering av Läs åtgärden för sektorn. *Bit mappnings posten för den kostnads fria sektorn* är en bit karta där varje uppsättning bit motsvarar en omappad sektor i blocket. Det här fältet används för att göra den kostnads fria sektors sökningen mer effektiv. Det här är ett fält för variabel längd som kräver ett ord för varje 32-sektor i blocket. Matrisen för *sektor mappnings posten* innehåller mappnings information för varje sektor i blocket. Varje post har följande format:

**Mappnings post för sektor**

| Bitar | Innebörd  |
| ------ | -------- |
| 31     | Giltig flagga. När Ställ in och logisk sektor inte alla anger att mappning är giltig |
| 30     | Föråldrad flagga. När det är klart är den här mappningen antingen föråldrad eller håller på att bli föråldrad. |
| 29     | Skrivning av mappnings post är slutförd när denna bit är 0 |
| 0-28   | Logisk sektor mappad till den här fysiska sektorn – om inte alla. |

Den övre biten i 32-bitars fältet (bit 31) används för att ange att den logiska sektor mappningen är giltig. Om den här biten är 0 är informationen i den här posten (och motsvarande sektor innehåll) inte längre giltig. Nästa bit-bit 30-används för att ange att denna sektor håller på att bli föråldrad och att en ny sektor skrivs. Bit 29 används för att ange när mappnings post skrivningen är klar. Om bit 29 är 0, skrivs mappnings posten som färdig. Om bit 29 anges beskrevs mappnings posten under processen. BITS 30 och 29 används för återställning från en potentiell ström förlust när en ny sektor mappning uppdateras. Slutligen innehåller de lägre 29 bitarna (28-0) det logiska sektor numret för sektorn. Om en sektor inte har mappats kommer alla bitar att ställas in, d.v.s. den har värdet 0xFFFFFFFF.

## <a name="nor-driver-requirements"></a>Driv Rutins krav

LevelX kräver en underliggande driv rutin eller en Flash-drivrutin som är speciell för underliggande Flash-del och maskin varu implementering. Driv rutinen anges för LevelX vid initiering via API- ***lx_nor_flash_open***. Prototypen av LevelX-driv rutinen är:

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

Parametern "*instance*" anger LevelX eller kontroll blocket. Driv Rutinens initierings funktion ansvarar för att konfigurera alla andra tjänster på driv rutins nivå för den associerade LevelX-instansen. De tjänster som krävs för varje LevelX eller instans är:

- Läs sektor
- Skriv sektor
- Blockera radering
- Blockera raderad verifiering
- System fel hanterare

## <a name="driver-initialization"></a>Driv rutins initiering

Dessa tjänster konfigureras genom att ställa in funktions pekare i **LX_NOR_FLASH** instansen i driv Rutinens initierings funktion. Initierings funktionen för driv rutiner ansvarar också för:

1. Ange bas adressen för blixten.
1. Ange det totala antalet block och antalet ord per block.
1. En RAM-buffert för läsning av en sektor av Flash (512 byte) och justerad för ULONG-åtkomst.

Initierings funktionen för driv rutiner utför troligen även ytterligare ytterligare enhets-och/eller implementerings åtgärder innan du returnerar **LX_SUCCESS**.

## <a name="driver-read-sector"></a>Driv rutins Läs sektor

LevelX-eller driv rutins tjänsten "Läs sektor" ansvarar för att läsa en särskild sektor i ett särskilt block i eller Flash. All fel kontroll och korrigerings logik är ansvaret för driv rutins tjänsten. Om det lyckas returnerar LevelX eller driv rutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX eller driv rutinen *LX_ERROR*. Prototypen av tjänsten LevelX eller driv rutin "Läs sektor" är:

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

Där "*flash_address*" anger adressen till en logisk sektor i ett eller ett Flash-block med minne och "*mål*" och "*ord*" anger var du vill placera sektor innehållet och hur många 32-bitars ord som ska läsas.

## <a name="driver-write-sector"></a>Driv rutins skrivnings sektor

LevelX-eller driv rutins tjänsten "Write sektor" ansvarar för att skriva en särskild sektor till ett block med eller Flash. Alla fel kontroller är ansvaret för driv rutins tjänsten. Om det lyckas returnerar LevelX eller driv rutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX eller driv rutinen **LX_ERROR**. Prototypen av tjänsten LevelX eller driv rutin "Write sektor" är:

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

Där "*flash_address*" anger adressen till en logisk sektor i ett eller ett Flash-block med minne och "*källa*" och "*ord*" anger källan för skrivning och hur många 32-bitars ord som ska skrivas.

> [!NOTE]
> LevelX är beroende av driv rutinen för att verifiera att skrivnings sektorn lyckades. Detta görs vanligt vis genom att du läser tillbaka det programmerade värdet för att se till att det matchar det begärda värdet som ska skrivas.

## <a name="driver-block-erase"></a>Radera driv rutins block

LevelX-eller driv rutins tjänsten för att blockera rader är ansvarig för radering av det angivna blocket eller Flash. Om det lyckas returnerar LevelX eller driv rutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX eller driv rutinen **LX_ERROR**. Prototypen av tjänsten LevelX eller driv rutinen blockera radering är:

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Där "*block*" identifierar vilket eller blockerar som ska raderas. Parametern "*erase_count*" tillhandahålls för diagnostiska syfte. Driv rutinen kan till exempel vilja varna en annan del av program varan när antalet rader överskrider ett angivet tröskelvärde.

> [!NOTE]
> LevelX använder driv rutinen för att undersöka alla byte i blocket för att se till att de raderas (innehåller alla).

## <a name="driver-block-erased-verify"></a>Borttagning av driv rutins block

LevelX eller driv rutinen "blockera raderad verifiering" ansvarar för att verifiera att det angivna blocket av eller blixten raderas. Om den raderas, returnerar LevelX eller driv rutinen **LX_SUCCESS**. Om blocket inte raderas, returnerar LevelX eller driv rutinen **LX_ERROR**. Prototypen av LevelX eller driv rutinen blockera raderad verifiera-tjänst är:

```c
INT nor_driver_block_erased_verify(ULONG block);
```

Där "*block*" anger vilket block som ska kontrol lera att den raderas.

> [!NOTE]
> LevelX förlitar sig på driv rutinen för att undersöka alla byte som anges för att se till att de raderas (innehåller alla).

## <a name="driver-system-error"></a>Driv rutins system fel

LevelX-eller driv rutins tjänsten för system fel hanterare ansvarar för att ställa in hantering av systemfel som identifieras av LevelX. Bearbetningen i den här rutinen är beroende av program. Om det lyckas returnerar LevelX eller driv rutinen **LX_SUCCESS**. Om det inte lyckas returnerar LevelX eller driv rutinen **LX_ERROR**. Prototypen av LevelX-eller driv rutins tjänsten "System Error" är:

```c
INT nor_driver_system_error(UINT error_code);
```

Där "*error_code*" representerar felet som har inträffat.

## <a name="nor-simulated-driver"></a>ELLER simulerad driv rutin

LevelX tillhandahåller en simulerad eller Flash-drivrutin som bara använder RAM för att simulera en eller Flash-del. Som standard tillhandahåller den eller simulerade driv rutinen 8-eller Flash-block med 16 512 byte-sektorer per block.

Initierings funktionen för den simulerade driv rutinen eller Flash-drivrutinen är ***lx_nor_flash_simulator_initialize** _ och definieras i _ *_lx_nor_flash_simulator. c_* *. Den här driv rutinen innehåller också en lämplig mall för att skriva vissa eller Flash-drivrutiner.

## <a name="nor-filex-integration"></a>ELLER FileX-integrering

Som tidigare nämnts förlitar sig LevelX inte på FileX för åtgärd. Alla LevelX-API: er kan anropas direkt av program varan för att lagra/Hämta rå data till de logiska sektorerna som tillhandahålls av LevelX. LevelX stöder dock också FileX.

Filen ***fx_nor_flash_simulated_driver. c*** innehåller ett exempel på en FileX-drivrutin för användning med Flash-simuleringen. Driv rutinen för FileX för LevelX ger en start punkt för att skriva anpassade FileX-drivrutiner.

> [!NOTE]
> FileX-eller Flash-formatet bör vara en fullständig block storlek på sektorer som är mindre än eller Flash. Detta bidrar till att garantera bästa prestanda under belastnings nivån för slitage. Ytterligare metoder för att förbättra skriv prestanda i LevelX-slitage:
> 1. Se till att alla skrivningar är exakt ett eller flera kluster i storlek och starta på exakta kluster gränser.
> 2. Förallokera kluster innan du utför stora fil skrivnings åtgärder via FileX ***fx_file_allocate*** -klassen för API: er.
> 3.  Regelbunden användning av ***lx_nor_flash_defragment*** för att frigöra så många eller blockera som möjligt och därmed förbättra skriv prestanda.
> 4. Se till att FileX-drivrutinen är aktive rad för att ta emot information om versions sektorn och förfrågningar som görs till driv rutinen för att frigöra sektorer i driv rutinen genom att anropa ***lx_nor_flash_sector_release***.
