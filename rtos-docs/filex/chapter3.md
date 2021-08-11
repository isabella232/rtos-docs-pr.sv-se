---
title: Kapitel 3 – Funktionella komponenter i Azure RTOS FileX
description: Det här kapitlet innehåller en beskrivning av de högpresterande Azure RTOS FileX Embedded-filsystemet ur ett funktionellt perspektiv
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bb2e1d7f10d71ed01a040cea63e9e469855525d89dd6318f3147c61ed166ee4c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783083"
---
# <a name="chapter-3---functional-components-of-azure-rtos-filex"></a>Kapitel 3 – Funktionella komponenter i Azure RTOS FileX

Det här kapitlet innehåller en beskrivning av högpresterande filsystem Azure RTOS FileX Embedded-filsystem ur ett funktionellt perspektiv.

## <a name="media-description"></a>Mediebeskrivning

FileX är ett högpresterande inbäddat filsystem som överensstämmer med FAT-filformatet. FileX visar det fysiska mediet som en matris med logiska sektorer. Hur dessa sektorer mappas till det underliggande fysiska mediet bestäms av I/O-drivrutinen som är ansluten till FileX-mediet ***under fx_media_open anropet.***

### <a name="fat121632-logical-sectors"></a>FAT12/16/32 Logiska sektorer

Den exakta organisationen av mediets logiska sektorer bestäms av innehållet i det fysiska mediets startpost. Den allmänna layouten för mediets logiska sektorer visas i bild 1.

Logiska FileX-sektorer börjar med logisk sektor 1, som pekar på den första reserverade sektorn för mediet. Reserverade sektorer är valfria, men när de används innehåller de vanligtvis systeminformation, till exempel startkod.

### <a name="fat121632-media-boot-record"></a>FAT12/16/32 Media Boot Record

Den exakta sektorförskjutningen för de andra områdena i den logiska sektorvyn för mediet härleds från innehållet i *mediestartposten*. Startpostens plats är vanligtvis inom sektor 0. Men om mediet har *dolda sektorer* måste förskjutningen till startsektorn ta hänsyn till dem (de finns omedelbart FÖRE startsektorn). Tabell 1 listar mediets startpostkomponenter och komponenterna beskrivs i styckena.

- **Jump Instruction** *Hoppinstruktionsfältet* är ett fält med tre byte som representerar en Intel x86-datorinstruktion för ett processorhopp. Det här är ett äldre fält i de flesta situationer.

  ![FileX Media Logical Sector View](./media/user-guide/filex-media-logical-sector-view.png)

  **BILD 1. FileX Media Logical Sector View**

- **OEM-namn** *Oem-namnfältet* är reserverat för tillverkare som ska ange ett namn på enheten.
- **Byte per sektor** Fältet *byte per sektor* i media boot record definierar hur många byte som finns i varje sektor – det grundläggande elementet i mediet.
- **Sektorer per kluster** Sektorerna *per klusterfält* i mediestartposten definierar antalet sektorer som tilldelats till ett kluster. Klustret är det grundläggande allokeringselementet i ett FAT-kompatibelt filsystem. All filinformation och underkataloger allokeras från mediets tillgängliga kluster enligt vad som bestäms av filallokeringstabellen (FAT).

    **TABELL 1. FileX Media Boot Record**
    
    |Offset  |Fält  |Antal byte|
    |----------|-----------|------------|
    |0x00|Jump Instruction (e9,xx,xx eller eb,xx,90)|3|
    |0x03|OEM-namn|8|
    |0x0B|Byte per sektor|2|
    |0x0D|Sektorer per kluster|1|
    |0x0E|Antal reserverade sektorer|2|
    |0x10|Antal vanliga frågor och svar|1|
    |0x11|Storlek på rotkatalogen|2|
    |0x13|Antal sektorer FAT-12 &amp; FAT-16|2|
    |0x15|Medietyp|1|
    |0x16|Antal sektorer per FAT|2|
    |0x18|Sektorer per spår|2|
    |0x1A|Antal krona|2|
    |0x1C|Antal dolda sektorer|4|
    |0x20|Antal sektorer – FAT-32|4|
    |0x24|Sektorer per FAT (FAT-32)|4|
    |0x2C|Rotkatalogkluster|4|
    |0x3E|Startkod för system|448
    |0x1FE|0x55AA|2|

- **Reserverade sektorer** Fältet *reserverade sektorer* i media boot record definierar antalet sektorer som är reserverade mellan startposten och den första sektorn i FAT-området. Den här posten är i de flesta fall noll.
- **Antal vanliga frågor och svar** Antalet *FAT-poster* i media boot record definierar antalet FAT på mediet. Det måste alltid finnas minst ett FAT i ett medium. Ytterligare FAT:er är bara dubbletter av den primära (första) FAT och används vanligtvis av diagnostik- eller återställningsprogram.
- **Rotkatalogstorlek** Posten *rotkatalogstorlek* i media boot record definierar det fasta antalet poster i rotkatalogen för mediet. Det här fältet gäller inte för underkataloger och FAT-32-rotkatalogen eftersom båda allokeras från mediets kluster.
- **Antal sektorer FAT-12 & FAT-16** Fältet *number of sectors* (antal sektorer) i media boot record (mediestartposten) innehåller det totala antalet sektorer i mediet. Om det här fältet är noll finns det totala antalet sektorer i fältet *FAT-32* för sektorer senare i startposten.
- **Medietyp** Fältet *medietyp* används för att identifiera vilken typ av media som finns för enhetsdrivrutinen. Det här är ett äldre fält.
- **Sektorer per FAT** Sektorerna *per FAT som* registreras i media boot record innehåller antalet sektorer som är associerade med varje FAT i FAT-området. Antalet FAT-sektorer måste vara tillräckligt stort för att ta hänsyn till det maximala möjliga antalet kluster som kan allokeras i mediet.
- **Sektorer per spår** Sektorerna *per spårfält* i mediestartsposten definierar antalet sektorer per spår. Detta är vanligtvis endast relevant för faktiska medier av disktyp. FLASH-enheter använder inte den här mappningen.
- **Antal krona** Antalet *krona-fältet* i mediestartposten definierar antalet krona i mediet. Detta är vanligtvis endast relevant för faktiska medier av disktyp. FLASH-enheter använder inte den här mappningen.
- **Dolda sektorer** Fältet *dolda sektorer* i mediestartposten definierar antalet sektorer före startposten. Det här fältet  finns i FX_MEDIA-kontrollblocket och måste redovisas i FileX I/O-drivrutiner i alla läs- och skrivbegäranden som görs av FileX.
- **Antal sektorer FAT-32** Fältet *antal sektorer i* mediestartposten är endast giltigt om fältet med två byte antal *sektorer* är noll. I sådana fall innehåller det här fältet med fyra byte antalet sektorer i mediet.
- **Sektorer per FAT (FAT-32)** Fältet *för sektorer per FAT (FAT-32)* är endast giltigt i FAT-32-format och innehåller antalet sektorer som allokerats för varje FAT för mediet.
- **Rotkatalogkluster** Fältet *för rotkatalogklustret* är endast giltigt i FAT-32-format och innehåller rotkatalogens startklusternummer.
- **Systemstartkod** Fältet *system boot code* är ett område där en liten del av startkoden ska lagras. I de flesta enheter i dag är detta ett äldre fält.
- **Signatur 0x55AA** *Signaturfältet* är ett datamönster som används för att identifiera startposten. Om det här fältet inte finns är startposten inte giltig.

### <a name="exfat"></a>Exfat

Den maximala filstorleken i FAT32 är 4 GB, vilket begränsar det breda införandet av högupplösta multimediafiler. Som standard stöder FAT32 lagringsmedia på upp till 32 GB. Med ökande flash- och SD-kortkapacitet blir FAT32 mindre effektivt vid hantering av stora volymer. exFAT är utformat för att lösa dessa begränsningar. exFAT stöder filstorlek upp till en Exabyte (EB), vilket är cirka en miljard GB. En annan viktig skillnad mellan exFAT och FAT32 är att exFAT använder bitmapp för att hantera tillgängligt utrymme i volymen, vilket gör exFAT mer effektivt för att hitta tillgängligt utrymme när data skrivs till filen. För filer som lagras i sammanhängande kluster eliminerar exFAT att gå nedåt i FAT-kedjan för att hitta alla kluster, vilket gör det mer effektivt vid åtkomst till stora filer. exFAT krävs för flash-lagring och SD-kort som är större än 32 GB.

### <a name="exfat-logical-sectors"></a>exFAT logiska sektorer

Den allmänna layouten för medias logiska sektorer i exFAT illustreras i bild 2. I exFAT tillhör startblocket och FAT-området systemområdet. Resten av klustren är Användarområde. Även om det inte krävs rekommenderar exFAT-standarden att allokeringsmappen är i början av användarområdet, följt av up-case-tabellen och rotkatalogen.

### <a name="exfat-media-boot-record"></a>exFAT Media Boot Record

Innehållet i Media Boot Record i exFAT skiljer sig från innehållet i FAT12/16/32. De visas i tabell 2. För att undvika förvirring markeras området mellan 0x0B och 0x40, som innehåller olika medieparametrar i FAT12/16/32 som *Reserverad* i exFAT. Det här reserverade området måste programmeras med nollor, så att du inte kan feltolka Media Boot Record.

![exFAT logiska sektorer](./media/user-guide/exfat-logical-sectors.png)

**BILD 2. exFAT logiska sektorer**

- **Jump-instruktion** *Hoppinstruktionsfältet* är ett fält med tre byte som representerar en Intel x86-datorinstruktion för ett processorhopp. Det här är ett äldre fält i de flesta situationer.

    **TABELL 2. exFAT Media Boot Record**

    |Offset  |Fält  |Antal byte|
    |----------|-----------|------------|
    |0x00|Jump-instruktion|3|
    |0x03|Namn på filsystem|8|
    |0x0B|Reserverat|53|
    |0x40|Partitionsförskjutning|8|
    |0x48|Volymlängd|8|
    |0x50|FAT-förskjutning|4|
    |0x54|FAT-längd|4|
    |0x58|Förskjutning av kluster heap|4|
    |0x5C|Antal kluster|4|
    |0x60|Första klustret i rotkatalogen|4|
    |0x64|Volymserienummer|4|
    |0x68|File System Revision|2|
    |0x6A|Volymflaggor|2|
    |0x6C|Byte per sektorskifte|1|
    |0x6D|Sektor per klusterskifte|1|
    |0x6E|Antal vanliga frågor och svar|1|
    |0x6F|Välj enhet|1|
    |0x70|Procent i användning|7|
    |0x71|Reserverat|1|
    |0x78|Startkod|390|
    |0x1FE|Startsignatur|2|

- **Namn på filsystem** För exFAT *måste filsystemets* namnfält vara "EXFAT" följt av tre avslutande blanksteg.
- **Reserverad** Innehållet i det *reserverade fältet* måste vara noll. Den här regionen överlappar startposterna i FAT12/16/ 32. Om du gör det här området noll undviker du att filsystem tolkar volymen fel.
- **Partitionsförskjutning** Fältet *partitionsförskjutning* anger början av den här partitionen.
- **Volymlängd** Fältet *volymlängd* definierar storleken, i antal sektorer, för den här partitionen.
- **FAT-förskjutning** *Förskjutningsfältet FAT* definierar startsektornumret i förhållande till början av partitionen i FAT-tabellen för den här partitionen.
- **FAT-längd** Fältet *FAT-längd* definierar storleken på FAT-tabellen i antal sektorer.
- **Förskjutning av kluster heap** *Förskjutningsfältet för* kluster heap definierar startsektornumret i förhållande till början av partitionen för kluster heapen. Kluster heap är det område där kataloginformation och fildata lagras.
- **Antal kluster** Fältet *klusterantal* definierar antalet kluster som partitionen har.
- **Första kluster i rotkatalogen** Det *första klustret i rotkatalogfältet* definierar startplatsen för rotkatalogen, vilket rekommenderas att vara direkt efter allokeringsmappen och starttabellen.
- **Volymserienummer** Fältet *volymserienummer* definierar serienumret för den här partitionen.
- **Filsystemrevision** Fältet *för filsystemrevision* definierar den större och lägre versionen av exFAT.
- **Volymflaggor** Fältet *volume flags* innehåller flaggor som anger volymens tillstånd.
- **Byte per sektorskifte** Fältet *byte per sektorväxling* definierar antalet byte per sektor i log2(n), där n är antalet byte per sektor. I till exempel SD-kortet är sektorstorleken 512 byte. Det här fältet ska därför vara 9 (log2(512) = 9).
- **Sektorer per klusterskifte** Sektorerna *per klusterskiftefält* definierar antalet sektorer i ett kluster, i log2(n) där n är antalet sektorer per kluster.
- **Antal vanliga frågor och svar** Antalet *fat-fält definierar* antalet FAT-tabeller i den här partitionen. För exFAT rekommenderas värdet vara 1 för en FAT-tabell.
- **Välj enhet** Fältet *för drivrutinsvälj* definierar det utökade INT 13h-enhetsnumret.
- **Procent i användning** Fältet *procent i användning* definierar procentandelen av klustren i kluster heapen som allokeras. Giltiga värden är mellan 0 och 100, inklusivt.
- **Reserverad** Det här fältet är reserverat för framtida användning.
- **Startkod** *Startkodfältet* är ett område där en liten del av startkoden ska lagras. I de flesta enheter i dag är detta ett äldre fält.
- **Signatur 0x55AA** Fältet *för startsignatur* är ett datamönster som används för att identifiera startposten. Om det här fältet inte finns är startposten inte giltig.

### <a name="file-allocation-table-fat"></a>Filallokeringstabell (FAT)

*Filallokeringstabellen (FAT)* startar efter de reserverade sektorerna i mediet. FAT-området är i princip en matris med 12-bitars, 16-bitars eller 32-bitars poster som avgör om klustret allokeras eller ingår i en kedja av kluster som består av en underkatalog eller en fil. Storleken på varje FAT-post bestäms av antalet kluster som måste representeras. Om antalet kluster (härlett från de totala sektorerna dividerat med sektorerna per kluster) är mindre än eller lika med 4 086 används 12-bitars FAT-poster. Om det totala antalet kluster är större än 4 086 och mindre än 65 525 används 16-bitars FAT-poster. Om det totala antalet kluster är större än eller lika med 65 525 används annars 32-bitars FAT eller exFAT.

För FAT12/16/32 underhåller FAT-tabellen inte bara klusterkedjan, den innehåller också information om klusterallokering: om ett kluster är tillgängligt eller inte. I exFAT underhålls klusterallokeringsinformationen av en katalogpost för allokeringsmappen. Varje partition har sin egen allokeringsmapp. Storleken på bitmappen är tillräckligt stor för att täcka alla tillgängliga kluster. Om ett kluster är tillgängligt för allokering anges motsvarande bit i allokeringsmappen till 0. Annars är biten inställd på 1. För en fil som upptar efterföljande kluster kräver exFAT inte någon FAT-kedja för att hålla reda på alla kluster. Men för en fil som inte upptar kluster i följd måste en FAT-kedja fortfarande underhållas.

### <a name="fat-entry-contents"></a>FAT-postinnehåll

De två första posterna i FAT-tabellen används inte och har vanligtvis följande innehåll.

|FAT-post |12-bitars FAT|16-bitars FAT|32-bitars FAT| Exfat|
|----------|-----------|------------|-------|------|
|Post 0|0x0F0|0x00F0|0x000000F0|0xF8FFFFFF|
|Post 1|0xFFF|0xFFFF|0x0FFFFFFF|0xFFFFFFFF|

FAT-postnummer 2 representerar det första klustret i mediets dataområde. Innehållet i varje klusterpost avgör om den är kostnadsfri eller en del av en länkad lista över kluster som allokerats för en fil eller en underkatalog. Om klusterposten innehåller en annan giltig klusterpost allokeras klustret och dess värde pekar på nästa kluster som allokeras i klusterkedjan.

Möjliga klusterposter definieras på följande sätt.

|Innebörd|12-bitars FAT|16-bitars FAT|32-bitars FAT| Exfat|
|----------|-----------|------------|-------|------|
|Kostnadsfritt kluster|0x000|0x0000|0x00000000|0x00000000|
|Används inte|0x001|0x0001|0x00000001|0x00000001|
|Reserverat|0xFF0-FF6|0xFFF0-FFF6|0x0FFFFFF0-6|ClusterCounter +2 till 0xFFFFFFF6|
|Felaktigt kluster|0xFF7|0xFFF7|0x0FFFFFF7|0xFFFFFFF7|
|Reserverat| - | - | - | 0xFFFFFFF8-E|
|Senaste kluster| 0xFF8-FFF| 0xFFF8-FFFF| 0x0FFFFFF8-F| 0xFFFFFFFF|
|Klusterlänk| 0x002-0xFEF| 0x0002-FFEF| 0x2-0x0FFFFFEF | 0x2 – ClusterCount + 1|

Det sista klustret i en allokerad klusterkedja innehåller det sista klustervärdet (definieras ovan). Det första klusternumret finns i fil- eller underkatalogens katalogpost.

### <a name="internal-logical-cache"></a>Intern logisk cache

FileX har en *senast använd logisk sektorcache* för varje öppnat medium. Den maximala storleken för den logiska sektorcachen definieras av **konstanten FX_MAX_SECTOR_CACHE** och finns **_i fx_api.h_**. Det här är den första faktorn som avgör storleken på den interna logiska sektorcachen.

Den andra faktorn som avgör storleken på den logiska sektorcachen är mängden minne som anges till anropet ***fx_media_open** _ av programmet. Det måste finnas tillräckligt med minne för minst en logisk sektor. Om fler än _ *FX_MAX_SECTOR_CACHE** logiska sektorer krävs måste konstanten ändras **_i fx_api.h_** och hela FileX-biblioteket måste återskapas.

> [!IMPORTANT]
> *Varje öppnat medium i FileX kan ha olika cachestorlek beroende på vilket minne som anges under det öppna anropet.*

### <a name="write-protect"></a>Skrivskydd

FileX ger programdrivrutinen möjlighet att dynamiskt ange skrivskydd på mediet. Om skrivskydd krävs anges drivrutinen till FX_TRUE *fx_media_driver_write_protect* i den associerade FX_MEDIA strukturen. När detta anges avvisas alla försök av programmet att ändra mediet samt försök att öppna filer för skrivning. Drivrutinen kan också inaktivera skrivskydd genom att rensa det här fältet.

### <a name="free-sector-update"></a>Uppdatering av kostnadsfri sektor

FileX tillhandahåller en mekanism för att informera programdrivrutinen när sektorer inte längre används. Detta är särskilt användbart för FLASH-minneshanterare som hanterar alla logiska sektorer som används av FileX.

Om meddelanden om kostnadsfria sektorer krävs anger programdrivrutinen att FX_TRUE *fx_media_driver_free_sector_update* i den associerade FX_MEDIA strukturen. Den här tilldelningen görs vanligtvis under drivrutinsinitieringen.

Om du anger det här fältet gör FileX **ett FX_DRIVER_RELEASE_SECTORS** föraranrop som anger när en eller flera efterföljande sektorer blir lediga.

### <a name="media-control-block-fx_media"></a>Media Control Block FX_MEDIA

Egenskaperna för varje öppet medium i FileX finns i mediakontrollblocket. Den här strukturen definieras i filen ***fx_api.h***.

Mediakontrollblocket kan finnas var som helst i minnet, men det är vanligast att göra kontrollblocket till en global struktur genom att definiera det utanför omfånget för en funktion.

Att hitta kontrollblocket i andra områden kräver lite mer försiktighet, precis som allt dynamiskt allokerat minne. Om ett kontrollblock allokeras i en C-funktion är det minne som är associerat med det en del av den anropande trådens stack.

> [!WARNING]
>*I allmänhet bör du undvika att använda lokal lagring för kontrollblock eftersom när funktionen returnerar släpps alla dess lokala variabelstackar – oavsett om den fortfarande används!*

## <a name="fat121632-directory-description"></a>**FAT12/16/32 Katalogbeskrivning**

FileX stöder både 8.3- Windows long file name(LFN)-namnformat. Förutom namnet innehåller varje katalogpost postens attribut, tid och datum för senaste ändring, startklusterindexet och postens storlek i byte. Tabell 3 visar innehållet och storleken på en FileX 8.3-katalogpost.

- **Katalognamn**

    FileX stöder filnamn i storlek från 1 till 255 tecken. Standardfilnamn med åtta tecken representeras i en enda katalogpost på mediet. De är vänsterjusterade i katalognamnsfältet och är tomma ut vadderade. Dessutom är de ASCII-tecken som utgör namnet alltid versaler.

    Långa filnamn (LFN) representeras av efterföljande katalogposter, i omvänd ordning, följt av ett standardfilnamn på 8,3. Det skapade 8.3-namnet innehåller all meningsfull kataloginformation som är associerad med namnet. Tabell 4 visar innehållet i katalogposterna som används för att lagra informationen om det långa filnamnet, och tabell 5 visar ett exempel på ett 39 tecken långt LFN som kräver totalt fyra katalogposter.

> [!IMPORTANT]
> *Konstanten **FX_MAX_LONG_NAME_LEN**, som definieras **i fx_api.h**, innehåller den maximala längd som stöds av FileX.*

- **Filnamnstillägg för katalog**

    För 8.3-standardfilnamn stöder FileX även det valfria *filnamnstillägget med tre tecken.* Precis som filnamnet på åtta tecken lämnas filnamnstilläggen justerade i katalogfilstilläggsfältet, tomma vadderade och alltid versaler.

    **TABELL 3. FileX 8.3-katalogpost**

    |Offset|Fält|Antal byte|
    |------------|-----------|------------|
    |0x00|Katalogpostnamn|8|
    |0x08|Katalogtillägg|3|
    |0x0B|Attribut|1|
    |0x0C|NT (introducerades med det långa filnamnsformatet och är reserverat för NT [alltid 0])|1|
    |0x0D|Skapad tid i millisekunder ( introducerades i det långa filnamnsformatet och representerar antalet millisekunder när filen skapades.)|1|
    |0x0E|Skapad tid i &amp; timmar minuter (introducerades med det långa filnamnsformatet och representerar den timme och minut då filen skapades )|2|
    |0x10|Skapad datum (introducerades med det långa filnamnsformatet och representerar det datum då filen skapades.)|2|
    |0x12|Datum för senaste åtkomst ( introducerades av det långa filnamnsformatet och representerar det datum då filen senast fick åtkomst.)|2|
    |0x14|Starta kluster (endast fat-32 för övre 16 bitar)|2|
    |0x16|Ändrad tid|2|
    |0x18|Ändringsdatum|2|
    |0x1A|Startkluster (lägre 16 bitar FAT-32 eller FAT-12 eller FAT-16)|2|
    |0x1C|Filstorlek|4|


- **Katalogattribut**

    Attributfältposten *med en byte-katalog* innehåller en serie bitar som anger olika egenskaper för katalogposten. Katalogattributdefinitioner är följande:

    |Attributbit|Innebörd|
    |------------|-----------|
    |0x01|Posten är skrivskyddade.|
    |0x02|Posten är dold.|
    |0x04|Posten är en systempost.|
    |0x08|Posten är en volymetikett|
    |0x10|Posten är en katalog.|
    |0x20|Posten har ändrats.|

    Eftersom alla attributbitarna är ömsesidigt uteslutande kan det finnas fler än en attributbit i taget.

- **Katalogtid**

    Tidsfältet *för katalogen med två* byte innehåller timmar, minuter och sekunder för den senaste ändringen av den angivna katalogposten. Bitarna 15 till 11 innehåller timmarna, bitar 10 till 5 innehåller minuterna och bitar 4 till 0 innehåller de halvsekunderna. Faktiska sekunder divideras med två innan de skrivs till det här fältet.

- **Katalogdatum**

    Datumfältet för katalogen *med två* byte innehåller året (förskjutet från 1980), månad och dag för den senaste ändringen av den angivna katalogposten. Bitarna 15 till 9 innehåller årsförskjutningen, bitar 8 till 5 innehåller månadsförskjutningen och bitarna 4 till 0 innehåller dagen.

- **Katalogstartskluster**

    Det här fältet tar upp 2 byte för FAT-12 och FAT-16. För FAT-32 tar det här fältet upp 4 byte. Det här fältet innehåller det första klusternumret som allokerats till posten (underkatalog eller fil).

    > [!NOTE]
    > *Observera att FileX skapar nya filer utan ett första kluster (starta klusterfältet lika med noll) så att användarna kan välja att allokera ett sammanhängande antal kluster för en nyligen skapad fil. *

- **Katalogfilstorlek**

    Storleksfältet *för katalogen* *med fyra* byte innehåller antalet byte i filen. Om posten verkligen är en underkatalog är storleksfältet noll.

### <a name="long-file-name-directory"></a>Lång filnamnskatalog

- **Ordningstal**

    Ordningstalsfältet *med en* byte som anger numret för LFN-posten. Eftersom LFN-poster placeras i omvänd ordning, minskar ordningstalen för LFN-katalogposterna som består av en enda LFN med ett. Dessutom måste ordningstalsvärdet för LFN direkt före filnamnet 8.3 vara ett.

    **TABELL 4. Lång post i filnamnskatalogen**

    | Offset | Fält | Antal byte |
    |------------|-----------|------------|
    | 0x00 | Ordningstalsfält | 1 |
    | 0x01 | Unicode-tecken 1 | 2 |
    | 0x03 | Unicode-tecken 2 | 2 |
    | 0x05 | Unicode-tecken 3 | 2 |
    | 0x07 | Unicode-tecken 4 | 2 |
    | 0x09 | Unicode-tecken 5 | 2 |
    | 0x0B | LFN-attribut | 1 |
    | 0x0C | LFN-typ (reserverad alltid 0) | 1 |
    | 0x0D | LFN-kontrollsumma | 1 |
    | 0x0E | Unicode-tecken 6 | 2 | 
    | 0x10 | Unicode-tecken 7 | 2 |
    | 0x12 | Unicode-tecken 8 | 2 |
    | 0x14 | Unicode-tecken 9 | 2 |
    | 0x16 | Unicode-tecken 10 | 2 |
    | 0x18 | Unicode-tecken 11 | 2 |
    | 0x1A | LFN-kluster (används alltid 0) | 2 |
    | 0x1C | Unicode-tecken 12 | 2 |
    | 0x1E | Unicode-tecken 13 | 2 |

- **Unicode-tecken**

    Unicode-teckenfälten *med två* byte har utformats för att stödja tecken från många olika språk. Standard-ASCII-tecken representeras med ASCII-tecknet som lagras i den första byten av Unicode-tecknet följt av ett blanksteg.

- **LFN-attribut**

    Fältet *LFN-attribut med en* byte innehåller attribut som identifierar katalogposten som en LFN-katalogpost. Detta åstadkoms genom att alla skrivskyddade attribut, systemattribut, dolda attribut och volymattribut har angetts.

- **LFN-typ**

    Fältet *LFN-typ med en* byte är reserverat och är alltid 0.

- **LFN-kontrollsumma**

    Fältet *LFN-kontrollsumma* med en byte representerar en kontrollsumma på de 11 tecknen i det associerade MSDOS 8.3-filnamnet. Den här kontrollsumman lagras i varje LFN-post för att säkerställa att LFN-posten motsvarar lämpligt 8.3-filnamn.

- **LFN-kluster**

    Fältet *LFN-kluster med två byte* är oanvänd och är alltid 0.

    **TABELL 5. Katalogposter som består av ett 39-teckens LFN**

    |Post|Innebörd|
    |------------|-----------|
    |1|LFN-katalogpost 3|
    |2|LFN Directory Entry 2|
    |3|LFN-katalogpost 1|
    |4|8.3 Katalogpost (ttttt~n.xx)|

### <a name="exfat-directory-description"></a>exFAT-katalogbeskrivning

exFAT-filsystemet lagrar katalogpost och filnamn på olika sätt. Katalogposten innehåller postens attribut, olika tidsstämplar för när posten skapades, ändrades och koms åt. Annan information, till exempel filstorlek och startkluster, lagras i Stream-tilläggets katalogpost som följer direkt efter den primära katalogposten. exFAT stöder endast long file name (LFN) namnformat. som lagras i File Name Directory Entry följer direkt Stream-tilläggets katalogpost, som du ser i tabell 2.

### <a name="exfat-file-directory-entry"></a>exFAT-filkatalogpost

En beskrivning av exFAT-filkatalogposten och dess innehåll ingår i följande tabell och stycken.

- **Typ av post**

    Fältet Posttyp anger typen av den här posten. För Inmatning av filkatalog måste det här fältet 0x85.

- **Antal sekundära inmatningar**

    Fältet *för sekundärt antal* poster anger antalet sekundära poster som följer omedelbart efter den här primära posten. Sekundära poster som är associerade med filkatalogposten inkluderar en dataströmstilläggskatalogpost och en eller flera katalogposter för filnamn.

    **TABELL 6. exFAT-filkatalogpost**

    |Offset|Fält|Antal byte|
    |----|-----------|-|
    |0x00|Typ av post|1|
    |0x01|Sekundär post|1|
    |0x02|Kontrollsumma|2|
    |0x04|Filattribut|2|
    |0x06|Reserverad 1|2|
    |0x08|Skapa tidsstämpel|4|
    |0x0C|Tidsstämpel för senaste ändring|4|
    |0x10|Tidsstämpel för senast använda|4|
    |0x14|Skapa 10 ms inkrement|1|
    |0x15|Inkrement för senaste ändring på 10 ms|1|
    |0x16|Skapa UTC-förskjutning|1|
    |0x17|Senast ändrad UTC-förskjutning|1|
    |0x18|Utc-förskjutning för senaste åtkomst|1|
    |0x19|Reserverad 2|7|

- **Kontrollsumma**

    Fältet *kontrollsumma* innehåller värdet för kontrollsumman över alla poster i katalogpostuppsättningen (filkatalogposten och dess sekundära poster).

- **Filattribut**

    Fältposten attribut med en byte innehåller en serie bitar som anger olika egenskaper för katalogposten. Definitionen av de flesta attribut bitar är identisk med FAT 12/16/32. Katalogattributdefinitioner är följande:

    |Attributbit|Innebörd|
    |------------|-----------|
    |0x01| Posten är skrivskyddade|
    |0x02|Posten är dold|
    |0x04|Posten är en systempost|
    |0x08|Posten är reserverad|
    |0x10|Posten är en katalog|
    |0x20|Posten har ändrats|
    |Alla andra bitar|Reserverat|

- **Reserverad1**

    Det här fältet ska vara noll.

- **Skapa tidsstämpel**

    Fältet *skapa tidsstämpel,* som kombinerar information från fältet skapa *10 ms* inkrement, beskriver det lokala datumet och tiden då filen eller katalogen skapades.

- **Tidsstämpel för senaste ändring**

    Det *senast ändrade tidsstämpelfältet,* som kombinerar information från det senast ändrade *10* ms-inkrementsfältet, beskriver det lokala datumet och tiden då filen eller katalogen senast ändrades. Se anteckningar nedan om tidsstämplar.

- **Tidsstämpel för senast använda**

    Fältet *för senast använda tidsstämpel* beskriver det lokala datumet och tiden då filen eller katalogen senast fick åtkomst. Se anteckningar nedan om tidsstämplar.

- **Skapa 10 ms inkrement**

    I *inkrementsfältet create 10ms,* som kombinerar information från fältet för att skapa tidsstämpel, beskrivs det lokala datumet och tiden då filen eller katalogen skapades.  Se anteckningar nedan om tidsstämplar.

- **Inkrement för senaste ändring på 10 ms**

    Det *senast ändrade 10* ms-inkrementsfältet, som kombinerar information från det senast ändrade *tidsstämpelfältet,* beskriver det lokala datumet och tiden då filen eller katalogen senast ändrades. Se anteckningar nedan om tidsstämplar.

- **Skapa UTC-förskjutning**

    Fältet *för att skapa UTC-förskjutning* beskriver skillnaden mellan den lokala tiden och UTC-tiden, när filen eller katalogen skapades. Se anteckningar nedan om tidsstämplar.

- **Senast ändrad UTC-förskjutning**

    Fältet *för den senast ändrade UTC-förskjutningen* beskriver skillnaden mellan den lokala tiden och UTC-tiden, när filen eller katalogen senast ändrades. Se anteckningar nedan om tidsstämplar.

- **Senast använda UTC-förskjutning**

    Fältet *för senast använda UTC-förskjutning* beskriver skillnaden mellan den lokala tiden och UTC-tiden, när filen eller katalogen senast fick åtkomst. Se anteckningar nedan om tidsstämplar.

- **Reserverad2**

    Det här fältet ska vara noll.

### <a name="notes-on-timestamps"></a>Information om tidsstämplar

- **Tidsstämpelpost** Tidsstämpelfälten tolkas på följande sätt:

- **10 ms ökningsfält** Värdet i inkrementsfältet på 10 ms ger finare kornighet till tidsstämpelvärdet. De giltiga värdena är mellan 0 (0 ms) och 199 (1990 ms).

     ![10 ms ökningsfält](./media/user-guide/10ms-increment-fields.png)

- **UTC-förskjutningsfält**

     ![UTC-förskjutningsfält](./media/user-guide/utc-offset-field.png)

- **Förskjutningsvärde**

    7-bitars heltal som signerats representerar förskjutning från UTC-tid i steg om 15 minuter.

- **Giltig**

    Om värdet i förskjutningsfältet är giltigt eller inte. 0 anger att värdet i fältet för förskjutningsvärdet är ogiltigt. 1 anger att värdet är giltigt.

### <a name="stream-extension-directory-entry"></a>Katalogpost för Stream-tillägg

En beskrivning av Stream-tilläggets katalogpost och dess innehåll ingår i följande tabell.

**TABELL 7. Katalogpost för Stream-tillägg**

|Offset|Fält| Antal byte|
|------------|-----------|-------|
|0x00|Typ av post|1|
|0x01|Flaggor|1|
|0x02|Reserverad 1|1|
|0x03|Namnlängd|1|
|0x04|Namnhash|2|
|0x06|Reserverad 2|2|
|0x08|Giltig datalängd|8|
|0x10|Reserverad 3|4|
|0x14|Första klustret|4|
|0x18|Datalängd|8|

- **Typ av post**

    Fältet *Posttyp* anger typen av den här posten. För katalogpost för direktuppspelningstillägg måste det här fältet 0xC0.

- **Flaggor**

    Det här fältet innehåller en serie bitar som anger olika egenskaper:
    
    |Flagga bit|Innebörd    |
    |-----------------|-----------|
    |0x01            |Det här fältet anger om allokering av kluster är möjlig eller inte. Det här fältet ska vara 1.|
    |0x02            |Det här fältet anger om de associerade klustren är sammanhängande eller inte. Värdet 0 innebär att FAT-posten är giltig och FileX ska följa FAT-kedjan. Värdet 1 innebär att FAT-posten är ogiltig och att klustren är sammanhängande.|
    |Alla andra bitar    |Reserverat.|

- **Reserverad 1**

    Det här fältet ska vara 0.

- **Namnlängd**

    *Namnlängdsfältet* innehåller längden på Unicode-strängen i katalogposterna för filnamnet som tillsammans innehåller. Katalogposterna i filnamnet ska omedelbart följa den här katalogposten för strömtillägget.

- **Namnhash**

    *Namnhashfältet* är en post på 2 byte som innehåller hash-värdet för det up-cased-filnamnet. Hash-värdet tillåter snabbare sökning efter fil-/katalognamn: om hash-värdena inte matchar är filnamnet som är associerat med den här posten inte en matchning.

- **Reserverad 2**

    Det här fältet ska vara 0.

- **Giltig datalängd**

    Fältet *giltig datalängd* anger mängden giltiga data i filen.

- **Reserverad 3**

    Den här arkiverade bör vara 0.

- **Första klustret**

    Det *första klusterfältet* innehåller index för det första klustret i dataströmmen.

- **Datalängd**

    Fältet *datalängd* innehåller det totala antalet byte i de allokerade klustren. Det här värdet kan vara större *än giltig datalängd*, eftersom exFAT tillåter förallokering av datakluster.

### <a name="root-directory"></a>Rotkatalog

I FAT 12- och 16-bitarsformat finns rotkatalogen omedelbart efter alla FAT-sektorer i mediet och kan finnas genom att undersöka ***fx_media_root_sector_start** _ i ett öppet _ *FX_MEDIA** kontrollblock.  Rotkatalogens storlek, sett till antalet katalogposter (var 32 byte i storlek), bestäms av motsvarande post i mediets startpost.

Rotkatalogen i FAT-32 och exFAT kan finnas var som helst i de tillgängliga klustren. Dess plats och storlek bestäms av startposten när mediet öppnas. När mediet har öppnats ***kan fx_media_root_sector_start*** användas för att hitta startklustret i rotkatalogen FAT-32 eller exFAT.

### <a name="subdirectories"></a>Underkataloger

Det finns ett antal underkataloger i ett FAT-system. Namnet på underkatalogen finns i en katalogpost precis som ett filnamn. Specifikationen för katalogattributet (0x10) är dock inställd för att ange att posten är en underkatalog och att filstorleken alltid är noll.
Bild 3 visar hur en typisk underkatalogstruktur ser ut för en ny singlecluster-underkatalog med namnet ***SAMPLE. DIR** _ med en fil med namnet _*_FILE.TXT_**.
På de flesta sätt är underkataloger mycket lika filposter. Det första klusterfältet pekar på det första klustret i en länkad lista med kluster. När en underkatalog skapas innehåller de två första katalogposterna standardkataloger, nämligen katalogen "." och katalogen "..". Katalogen "." pekar på själva underkatalogen, medan katalogen ".." pekar på den föregående eller överordnade katalogen.

### <a name="global-default-path"></a>Global standardsökväg

FileX tillhandahåller en global standardsökväg för mediet. Standardsökvägen används i alla fil- eller katalogtjänster som inte uttryckligen anger en fullständig sökväg.

Inledningsvis är den globala standardkatalogen inställd på mediets rotkatalog. Detta kan ändras av programmet genom att anropa ***fx_directory_default_set***.

Den aktuella standardsökvägen för mediet kan undersökas genom att anropa ***fx_directory_default_get** _. Den här rutinen ger en sträng pekare till standardsökvägsträngen som finns inuti *kontrollblocket* _ FX_MEDIA * .

### <a name="local-default-path"></a>Lokal standardsökväg

FileX tillhandahåller också en trådspecifik standardsökväg som gör att olika trådar kan ha unika sökvägar utan konflikter. Den **FX_LOCAL_PATH** strukturen tillhandahålls av programmet under anrop till fx_directory_local_path_set _ och ***_*_fx_directory_local_path_restore_** för att ändra den lokala sökvägen för den anropande tråden.

Om det finns en lokal sökväg har den lokala sökvägen företräde framför den globala standardmediesökvägen. Om den lokala sökvägen inte har ställts in eller om den ***rensas med fx_directory_local_path_clear tjänsten*** används mediets globala standardsökväg igen.

## <a name="file-description"></a>Filbeskrivning

FileX stöder standardtecken på 8,3 och långa filnamn med filnamnstillägg med tre tecken. Förutom ASCII-namnet innehåller varje filpost postens attribut, tid och datum för senaste ändring, startklusterindexet och storleken i byte för posten.

### <a name="file-allocation"></a>Filallokering

FileX stöder standardschemat för klusterallokering i FAT-format. Dessutom stöder FileX förklusterallokering av sammanhängande kluster. För att hantera detta skapas varje FileX-fil utan allokerade kluster. Kluster allokeras på efterföljande skrivbegäranden ***eller på fx_file_allocate*** som ska allokera sammanhängande kluster i förväg.

Bild 4, "FileX FAT-16 File Example", visar en fil med namnet ***FILE.TXT*** med två sekventiella kluster som allokerats från kluster 101, en storlek på 26 och alfabetet som data i filens första dataklusternummer 101.

### <a name="file-access"></a>Filåtkomst

En FileX-fil kan öppnas flera gånger samtidigt för läsåtkomst. En fil kan dock bara öppnas en gång för skrivning. Den information som används för filåtkomst  finns i FX_FILE filkontrollblocket.

> [!NOTE]
> *Observera att mediedrivrutinen kan ställa in skrivskydd dynamiskt. Om detta händer avvisas alla skrivbegäranden samt försök att öppna en fil för skrivning.*

### <a name="file-layout-in-exfat"></a>Fillayout i exFAT

Utformningen av exFAT kräver inte att FAT-kedjan underhålls för en fil om data lagras i skadliga kluster. *NoFATChain-biten* i streamtilläggskatalogposten anger huruvida FAT-kedjan ska användas vid läsning av data från filen. Om *NoFATChain* har angetts läser FileX sekventiellt från klustret som anges i fältet *Första* kluster i streamtilläggskatalogposten.

Å andra sidan, om *NoFATChain* är klar, följer FileX FAT-kedjan för att bläddra i hela filen, ungefär som FAT-kedjan i FAT12/16/32.

Bild 3 visar två exempelfiler, en kräver inte FAT-kedja och den andra kräver en FAT-kedja.

## <a name="system-information"></a>Systeminformation

FileX-systeminformationen består av att hålla reda på de öppna medieinstanserna och upprätthålla systemets globala tid och datum.

![Fil med sammanhängande kluster jämfört med fil som kräver FAT Link](./media/user-guide/system-information.png)

**BILD 3. Fil med sammanhängande kluster jämfört med fil som kräver FAT Link**

Systemets datum och tid är som standard inställda på det senaste utgivningsdatumet för FileX. För att systemets datum och tid ska vara korrekta måste programmet anropa ***fx_system_time_set** _ och _ *_fx_system_date_set_** under initieringen.

### <a name="system-date"></a>Systemdatum

FileX-systemdatumet behålls i den globala ***_fx_system_date*** variabeln. Bitarna 15 till 9 innehåller årsförskjutningen från 1980, bitar 8 till 5 innehåller månadsförskjutningen och bitarna 4 till 0 innehåller dagen. |

### <a name="system-time"></a>Systemtid

FileX-systemtiden upprätthålls i den globala ***_fx_system_time*** variabeln. Bitarna 15 till 11 innehåller timmarna, bitar 10 till 5 innehåller minuterna och bitar 4 till 0 innehåller de halvsekunderna.

### <a name="periodic-time-update"></a>Periodisk tidsuppdatering

Under systemitieringen skapar FileX en ThreadX-programtimer för att regelbundet uppdatera systemets datum och tid. Systemdatum- och tidsuppdateringens hastighet bestäms av två  konstanter som används av _fx_system_initialize funktionen.

Konstanterna **FX_UPDATE_RATE_IN_SECONDS** **FX_UPDATE_RATE_IN_TICKS** representerar samma tidsperiod. Konstanten **FX_UPDATE_RATE_IN_TICKS** antalet ThreadX-timers som representerar det antal sekunder som anges av konstanten **FX_UPDATE_RATE_IN_SECONDS**. Den **FX_UPDATE_RATE_IN_SECONDS** konstanten anger hur många sekunder mellan varje FileX-tidsuppdatering. Den interna FileX-tiden ökar därför i intervall om **FX_UPDATE_RATE_IN_SECONDS**. Dessa konstanter kan anges under kompileringen av fx_system_initialize _, eller så kan utvecklaren ändra standardvärdena i ***filen _*_fx_port.h_** i FileX-versionen.

Den periodiska FileX-timern används endast för att uppdatera det globala systemets datum och tid, som endast används för tidsstämplar för filer. Om tidsstämplar inte behövs definierar du bara **FX_NO_TIMER** när du **_kompilerar fx_system_initialize.c_** för att eliminera skapandet av den periodiska FileX-timern.

![FileX FAT-16-filexempel](./media/user-guide/fat-16-file-example.png)

**BILD 4. FileX FAT-16-filexempel**
