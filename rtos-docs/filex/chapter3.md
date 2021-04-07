---
title: Kapitel 3 – funktionella komponenter i Azure återställnings tider FileX
description: Det här kapitlet innehåller en beskrivning av det inbäddade fil systemet för Azure återställnings tider-FileX med höga prestanda från ett funktionellt perspektiv
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a94344a7079e3f0e3e451bc678c369fee543aef6
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550175"
---
# <a name="chapter-3---functional-components-of-azure-rtos-filex"></a>Kapitel 3 – funktionella komponenter i Azure återställnings tider FileX

Det här kapitlet innehåller en beskrivning av det inbäddade fil systemet för Azure återställnings tider-FileX med höga prestanda från ett funktionellt perspektiv.

## <a name="media-description"></a>Medie Beskrivning

FileX är ett inbäddat fil system med hög prestanda som överensstämmer med fil system formatet FAT. FileX visar det fysiska mediet som en matris med logiska sektorer. Hur dessa sektorer mappas till de underliggande fysiska medierna bestäms av den I/O-drivrutin som är ansluten till FileX-mediet under ***fx_media_open*** -anropet.

### <a name="fat121632-logical-sectors"></a>FAT12/16/32 logiska sektorer

Den exakta organisationen av mediets logiska sektorer bestäms av innehållet i det fysiska mediets start post. Den allmänna layouten för mediets logiska sektorer visas i bild 1.

FileX logiska sektorer börjar på logisk sektor 1, som pekar på den första reserverade sektorn i mediet. Reserverade sektorer är valfria, men när de används brukar de innehålla system information, till exempel start kod.

### <a name="fat121632-media-boot-record"></a>FAT12/16/32 Media Boot Record

Den exakta sektor förskjutningen för de andra områdena i den logiska sektor vyn av mediet härleds från innehållet i *medie start posten*. Platsen för start posten är vanligt vis på sektor 0. Men om mediet har *dolda sektorer* måste förskjutningen till Start sektorn beaktas för dem (de placeras omedelbart före start sektorn). Tabell 1 visar mediets start post-komponenter och komponenterna beskrivs i stycken.

- **Hopp instruktion** *Hopp instruktions* fältet är ett fält med tre byte som representerar en Intel x86-dator-instruktion för ett processor hopp. Detta är ett äldre fält i de flesta situationer.

  ![FileX media, logisk sektor vy](./media/user-guide/filex-media-logical-sector-view.png)

  **BILD 1. FileX media, logisk sektor vy**

- **OEM-namn** Fältet *OEM-namn* är reserverat för tillverkare att placera sitt namn eller ett namn på enheten.
- **Byte per sektor** Fältet *byte per sektor* i medie start posten definierar hur många byte som finns i varje sektor – det grundläggande mediet för mediet.
- **Sektorer per kluster** I fältet *sektorer per kluster* i medie start posten definieras antalet sektorer som tilldelats ett kluster. Klustret är det grundläggande fördelnings elementet i ett FAT-kompatibelt fil system. All Filinformation och under kataloger tilldelas från mediets tillgängliga kluster som definieras av filallokeringstabellen (FAT).

    **TABELL 1. FileX Media Boot Record**
    
    |Offset  |Fält  |Antal byte|
    |----------|-----------|------------|
    |0x00|Hopp instruktion (E9, XX, XX eller EB, XX, 90)|3|
    |0x03|OEM-namn|8|
    |0x0B|Byte per sektor|2|
    |0x0D|Sektorer per kluster|1|
    |0x0E|Antal reserverade sektorer|2|
    |0x10|Antal fetter|1|
    |0x11|Storlek på rot Katalog|2|
    |0x13|Antal sektorer FAT-12 &amp; FAT-16|2|
    |0x15|Medietyp|1|
    |0x16|Antal sektorer per FAT|2|
    |0x18|Sektorer per spår|2|
    |0x1A|Antal huvuden|2|
    |0x1C|Antal dolda sektorer|4|
    |0x20|Antal sektorer-FAT-32|4|
    |0x24|Sektorer per FAT (FAT-32)|4|
    |0x2C|Rot Katalog kluster|4|
    |0x3E|System starts kod|448
    |0x1FE|0x55AA|2|

- **Reserverade sektorer** Fältet *reserverade sektorer* i medie start posten definierar antalet sektorer som reserver ATS mellan start posten och den första sektorn i fat-området. Den här posten är noll i de flesta fall.
- **Antal fetter** *Antalet fett* poster i medie start posten definierar antalet fetter i mediet. Det måste alltid finnas minst en FAT i ett medium. Ytterligare fetter är bara dubbla kopior av primär (första) FAT och används vanligt vis av diagnostik-eller återställnings program.
- **Rot Katalog storlek** *Rot katalogens storleks* post i medie start posten definierar det fasta antalet poster i rot katalogen på mediet. Det här fältet gäller inte för-underkataloger och rot katalogen FAT-32 eftersom båda är allokerade från mediets kluster.
- **Antal sektorer FAT-12 & FAT-16** Fältet *antal sektorer* i medie start posten innehåller det totala antalet sektorer i mediet. Om det här fältet är noll finns det totala antalet sektorer i fältet *antal sektorer FAT-32* som finns senare i Start posten.
- **Medietyp** Fältet *medietyp* används för att identifiera vilken medietyp som finns för enhets driv rutinen. Det här är ett bakåtkompatibelt fält.
- **Sektorer per fat** *Sektorerna per fat* som har arkiverats i medie start posten innehåller antalet sektorer som är kopplade till varje FAT i fat-området. Antalet FAT-sektorer måste vara tillräckligt stort för att kunna användas för maximalt antal kluster som kan allokeras i mediet.
- **Sektorer per spår** *Sektorerna per spårnings* fält i medie start posten definierar antalet sektorer per spår. Detta är vanligt vis bara relevant för faktiska disk typs medier. FLASH-enheter använder inte den här mappningen.
- **Antal huvuden** I fältet *Antal huvuden* i medie start posten definieras antalet huvuden i mediet. Detta är vanligt vis bara relevant för faktiska disk typs medier. FLASH-enheter använder inte den här mappningen.
- **Dolda sektorer** Fältet för *dolda sektorer* i medie start posten definierar antalet sektorer innan start posten. Det här fältet finns kvar i **FX_MEDIA** kontroll block och måste redovisas i FileX i/O-drivrutiner i alla Läs-och skriv förfrågningar som görs av FileX.
- **Antal sektorer FAT – 32** Fältet *antal sektorer* i medie start posten är bara giltigt om *antalet sektorer* i två byte är noll. I sådana fall innehåller detta fält med fyra byte antalet sektorer i mediet.
- **Sektorer per fat (FAT-32)** Fältet *sektorer per fat (FAT-32)* är endast giltigt i FAT-32-format och innehåller antalet sektorer som har allokerats för varje fat av mediet.
- **Rot Katalog kluster** Fältet *rot Katalog kluster* är endast giltigt i FAT-32-format och innehåller start kluster numret för rot katalogen.
- **System starts kod** Fältet *system start Code* är ett område för att lagra en liten del av start koden. I de flesta enheter idag är detta ett äldre fält.
- **0x55AA för signatur** Fältet *signatur* är ett data mönster som används för att identifiera start posten. Om det här fältet inte finns är start posten ogiltig.

### <a name="exfat"></a>exFAT

Den maximala fil storleken i FAT32 är 4 GB, vilket begränsar det omfattande införandet av högupplösta multimediafiler. Som standard stöder FAT32 lagrings mediet upp till 32 GB. Med ökande kapacitet för Flash-och SD-kort blir FAT32 mindre effektivt i hanteringen av stora volymer. exFAT har utformats för att lösa dessa begränsningar. exFAT stöder fil storleken upp till en exabyte (EB), vilket är ungefär 1 000 000 000 GB. En annan viktig skillnad mellan exFAT och FAT32 är att exFAT använder bitmapp för att hantera tillgängligt utrymme på volymen, vilket gör att exFAT effektivare hittar tillgängligt utrymme vid skrivning av data till filen. För filer som lagras i sammanhängande kluster eliminerar exFAT den genom gången av FAT-kedjan för att hitta alla kluster, vilket gör det mer effektivt vid åtkomst till stora filer. exFAT krävs för Flash Storage och SD-kort som är större än 32 GB.

### <a name="exfat-logical-sectors"></a>exFAT logiska sektorer

Den allmänna layouten för mediets logiska sektorer i exFAT illustreras i bild 2. I exFAT startas startblocket och FAT-ytan till system-ytan. Resten av klustren är User Area. Även om det inte krävs rekommenderar exFAT standard att insamlarens bitmapp är i början av användarområdet, följt av up-Case-tabellen och rot katalogen.

### <a name="exfat-media-boot-record"></a>exFAT Media Boot Record

Innehållet i medie start posten i exFAT skiljer sig från de i FAT12/16/32. De visas i tabell 2. För att förhindra förvirring är arean mellan 0x0B och 0x40, som innehåller olika medie parametrar i FAT12/16/32 markerat som *reserverad* i exFAT. Det reserverade utrymmet måste programmeras med nollor, vilket gör att det inte går att tolka medie start posten.

![exFAT logiska sektorer](./media/user-guide/exfat-logical-sectors.png)

**BILD 2. exFAT logiska sektorer**

- **Hopp instruktion** *Hopp instruktions* fältet är ett fält med tre byte som representerar en Intel x86-dator-instruktion för ett processor hopp. Detta är ett äldre fält i de flesta situationer.

    **TABELL 2. exFAT Media Boot Record**

    |Offset  |Fält  |Antal byte|
    |----------|-----------|------------|
    |0x00|Hopp instruktion|3|
    |0x03|Fil system namn|8|
    |0x0B|Reserverat|53|
    |0x40|Förskjutning av partition|8|
    |0x48|Volym längd|8|
    |0x50|FAT-förskjutning|4|
    |0x54|FAT-längd|4|
    |0x58|Offset för kluster-heap|4|
    |0x5C|Antal kluster|4|
    |0x60|Första klustret i rot katalogen|4|
    |0x64|Volymens serie nummer|4|
    |0x68|Fil system revision|2|
    |0x6A|Volym flaggor|2|
    |0x6C|Byte per sektors växling|1|
    |0x6D|Sektor per kluster Skift|1|
    |0x6E|Antal fetter|1|
    |0x6F|Välj enhet|1|
    |0x70|Procent används|7|
    |0x71|Reserverat|1|
    |0x78|Start kod|390|
    |0x1FE|Start-signatur|2|

- **Fil system namn** För exFAT måste *fil systemets namn* fält vara "exFAT" följt av tre avslutande blank steg.
- **Reserverade** Innehållet i det *reserverade* fältet måste vara noll. Den här regionen överlappar start posterna i FAT12/16/32. Om du gör det här fältet noll undviks fil system från att mis-tolkar volymen.
- **Förskjutning av partition** Fältet *offset (partition offset* ) visar början på den här partitionen.
- **Volym längd** Fältet *volym längd* definierar storlek, i antal sektorer, för den här partitionen.
- **Fat-förskjutning** Fältet *fat-förskjutning* definierar start sektors numret i förhållande till början av den här partitionen, i fat-tabellen för den här partitionen.
- **Fat-längd** I fältet *fat-längd* definieras storleken på fat-tabellen i antal sektorer.
- **Offset för kluster-heap** Fältet *förskjutning i klustrets heap* definierar start sektors numret i förhållande till början av partitionen, i klustrets heap. Kluster-heap är det utrymme där katalog informationen och fil data lagras.
- **Antal kluster** Fältet *antal kluster* definierar antalet kluster som den här partitionen har.
- **Första klustret i rot katalogen** Det *första klustret i fältet rot Katalog* definierar start platsen för rot katalogen, vilket rekommenderas att vara rätt efter allokering-bitmappen och tabellen med anmälan.
- **Volymens serie nummer** Fältet *volymens serie nummer* definierar serie numret för den här partitionen.
- **Fil system revision** I fältet *fil system revision* definieras huvud-och del versionen av exFAT.
- **Volym flaggor** Fältet *volym flaggor* innehåller flaggor som visar den här volymens tillstånd.
- **Byte per sektors växling** I fältet *byte per sektor Skift* definieras antalet byte per sektor, i log2 (n), där n är antalet byte per sektor. I SD-kortet är till exempel sektor storleken 512 byte. Därför är det här fältet 9 (log2 (512) = 9).
- **Sektorer per kluster Skift** Fältet *sektorer per kluster Skift* definierar antalet sektorer i ett kluster, i log2 (n) där n är antalet sektorer per kluster.
- **Antal fetter** Fältet *antal fetter* definierar antalet fat-tabeller i den här partitionen. För exFAT rekommenderas värdet 1 för en FAT-tabell.
- **Välj enhet** I fältet *driv rutins val* definieras det utökade int 13h-enhets numret.
- **Procent används** Procent andelen *i användnings* fältet definierar procent andelen kluster i klustrets heap som allokeras. Giltiga värden är mellan 0 och 100.
- **Reserverade** Det här fältet är reserverat för framtida användning.
- **Start kod** Fältet *Start kod* är ett område för att lagra en liten del av start koden. I de flesta enheter idag är detta ett äldre fält.
- **0x55AA för signatur** Fältet *Boot signatur* är ett data mönster som används för att identifiera start posten. Om det här fältet inte finns är start posten ogiltig.

### <a name="file-allocation-table-fat"></a>Filallokeringstabell (FAT)

*Filen Allocation Table (fat)* startar efter de reserverade sektorerna i mediet. FAT-området är i grunden en matris med 12-bitars, 16-bitars eller 32-bitars poster som avgör om klustret tilldelas eller ingår i en kedja av kluster som består av en under katalog eller en fil. Storleken på varje FAT-post bestäms av antalet kluster som måste representeras. Om antalet kluster (härledda från de totala sektorerna dividerat med sektorerna per kluster) är mindre än eller lika med 4 086 används 12-bitars FAT-poster. Om det totala antalet kluster är större än 4 086 och mindre än 65 525, används 16-bitars FAT-poster. Annars används, om det totala antalet kluster är större än eller lika med 65 525, 32-bitars FAT eller exFAT.

För FAT12/16/32 upprätthåller FAT-tabellen inte bara kluster kedjan. den innehåller även information om kluster tilldelning: huruvida ett kluster är tillgängligt eller inte. I exFAT underhålls kluster tilldelnings informationen av en katalog post för en allokering av katalogen. Varje partition har sin egen allokerings-bitmapp. Storleken på bitmappen är tillräckligt stor för att alla tillgängliga kluster ska gälla. Om ett kluster är tillgängligt för allokering anges motsvarande bit i allokeringsenheten till 0. Annars är biten inställt på 1. För en fil som upptar flera kluster kräver exFAT inte en FAT-kedja för att hålla reda på alla kluster. Men för en fil som inte upptar flera kluster måste en FAT-kedja fortsätta.

### <a name="fat-entry-contents"></a>Innehåll i FAT-post

De två första posterna i FAT-tabellen används inte och har vanligt vis följande innehåll.

|FAT-post |12-bitars FAT|16-bitars FAT|32-bitars FAT| exFAT|
|----------|-----------|------------|-------|------|
|Post 0|0x0F0|0x00F0|0x000000F0|0xF8FFFFFF|
|Post 1|0xFFF|0xFFFF|0x0FFFFFFF|0xFFFFFFFF|

FAT-post nummer 2 representerar det första klustret i mediets data området. Innehållet i varje kluster post bestämmer om det är kostnads fritt eller inte ingår i en länkad lista över kluster som har allokerats för en fil eller under katalog. Om kluster posten innehåller en annan giltig kluster post allokeras klustret och dess värde pekar på nästa kluster som allokeras i kluster kedjan.

Möjliga kluster poster definieras enligt följande.

|Innebörd|12-bitars FAT|16-bitars FAT|32-bitars FAT| exFAT|
|----------|-----------|------------|-------|------|
|Kostnads fritt kluster|0x000|0x0000|0x00000000|0x00000000|
|Används inte|0x001|0x0001|0x00000001|0x00000001|
|Reserverat|0xFF0-FF6|0xFFF0-FFF6|0x0FFFFFF0-6|ClusterCounter + 2 till 0xFFFFFFF6|
|Felaktigt kluster|0xFF7|0xFFF7|0x0FFFFFF7|0xFFFFFFF7|
|Reserverat| - | - | - | 0xFFFFFFF8 – E|
|Senaste kluster| 0xFF8-FFF| 0xFFF8-FFFF| 0x0FFFFFF8-F| 0xFFFFFFFF|
|Kluster länk| 0x002-0xFEF| 0x0002-FFEF| 0x2-0x0FFFFFEF | 0x2-ClusterCount + 1|

Det sista klustret i en allokerad kluster kedja innehåller det sista kluster värdet (definieras ovan). Det första kluster numret finns i fil-eller under katalogens katalog post.

### <a name="internal-logical-cache"></a>Internt logiskt cacheminne

FileX har ett *mest nyligen använt* logiskt sektor-cacheminne för varje öppnat medium. Den maximala storleken för cachen för logiska sektorer definieras av konstant **FX_MAX_SECTOR_CACHE** och finns i **_fx_api. h_**. Det här är den första faktorn som avgör storleken på den interna logiska sektorns cache.

Den andra faktorn som avgör storleken på den logiska sektorns cache är mängden minne som anges till ***fx_media_open** _ anrop från programmet. Det måste finnas tillräckligt med minne för minst en logisk sektor. Om fler än _ *FX_MAX_SECTOR_CACHE** logiska sektorer krävs måste konstanten ändras i **_fx_api. h_** och hela FileX-biblioteket måste återskapas.

> [!IMPORTANT]
> *Alla öppna media i FileX kan ha olika cachestorlek beroende på vilket minne som angavs under Open-anropet.*

### <a name="write-protect"></a>Skriv skydd

FileX tillhandahåller program driv rutinen möjlighet att dynamiskt ange skriv skydd på mediet. Om Skriv skydd krävs, anger driv rutinen FX_TRUE *fx_media_driver_write_protect* fältet i den associerade FX_MEDIA strukturen. När det är inställt avvisas alla försök av programmet att ändra mediet samt försök att öppna filer som ska skrivas. Driv rutinen kan också inaktivera Skriv skyddet genom att rensa det här fältet.

### <a name="free-sector-update"></a>Kostnads fri sektor uppdatering

FileX tillhandahåller en mekanism för att informera program driv rutinen när sektorer inte längre används. Detta är särskilt användbart för minnes hanterare i FLASH som hanterar alla logiska sektorer som används av FileX.

Om det krävs ett meddelande om kostnads fria sektorer, anges program driv rutinen för att FX_TRUE fältet *fx_media_driver_free_sector_update* i den associerade FX_MEDIA strukturen. Den här tilldelningen utförs vanligt vis vid initiering av driv rutinen.

Om du anger det här fältet blir FileX ett **FX_DRIVER_RELEASE_SECTORS** driv rutins anrop som anger när en eller flera sektorer i följd blir kostnads fria.

### <a name="media-control-block-fx_media"></a>Medie kontroll block FX_MEDIA

Egenskaperna för varje öppet medium i FileX finns i medie kontroll blocket. Den här strukturen definieras i filen ***fx_api. h***.

Medie kontroll blocket kan finnas var som helst i minnet, men det är vanligt att kontrol lera att kontrollen blockerar en global struktur genom att definiera den utanför omfånget för en funktion.

Att hitta kontroll blocket i andra områden kräver lite mer omsorg, precis som allt dynamiskt allokerat minne. Om ett kontroll block tilldelas i en C-funktion är det minne som är associerat med det en del av den anropande trådens stack.

> [!WARNING]
>*I allmänhet bör du undvika att använda lokal lagring för kontroll block eftersom när funktionen returnerar, så släpps hela det lokala variabel stack utrymmet – oavsett om det fortfarande används!*

## <a name="fat121632-directory-description"></a>**FAT12/16/32 katalog Beskrivning**

FileX stöder namn formaten både 8,3 och Windows Long File name (LFN). Förutom namnet innehåller varje katalog post postens attribut, senast ändrad tid och datum, start kluster indexet och storleken i byte för posten. Tabell 3 visar innehållet och storleken för en FileX 8,3-katalog post.

- **Katalog namn**

    FileX stöder fil namn i storlek mellan 1 och 255 tecken. Vanliga fil namn för åtta tecken representeras i en enda katalog post på mediet. De är kvar i fältet katalog namn och är tomma. Dessutom är ASCII-tecknen som utgör namnet alltid versaler.

    Långa fil namn (LFNs) representeras av sammanhängande katalog poster i omvänd ordning, följt av ett 8,3 standard fil namn. Det skapade 8,3-namnet innehåller all meningsfull katalog information som är associerad med namnet. Tabell 4 visar innehållet i de katalog poster som används för att lagra den långa fil namns informationen och tabell 5 visar ett exempel på en LFN på 39 tecken som kräver totalt fyra katalog poster.

> [!IMPORTANT]
> *Konstanten **FX_MAX_LONG_NAME_LEN**, som definieras i **fx_api. h**, innehåller den maximala längd som stöds av FileX.*

- **Katalog fil namns tillägg**

    För standard 8,3-filnamn stöder FileX också det valfria *katalog fil* namns tillägget med tre tecken. Precis som fil namnet för åtta tecken är fil namns tilläggen marginaljusterade i fältet katalog fil namns tillägg, Tom utfyllnad och alltid versaler.

    **TABELL 3. FileX 8,3-katalog post**

    |Offset|Fält|Antal byte|
    |------------|-----------|------------|
    |0x00|Katalog post namn|8|
    |0x08|Katalog tillägg|3|
    |0x0B|Attribut|1|
    |0x0C|NT (introducerat av långt fil namns format och är reserverat för NT [Always-0])|1|
    |0x0D|Tid i millisekunder (introducerat av långt fil namns format och representerar antalet millisekunder när filen skapades).|1|
    |0x0E|Skapad tid i timmar &amp; minuter (infört av långt fil namns format och representerar den timme och minut som filen skapades)|2|
    |0x10|Skapat datum (infört av det långa fil namns formatet och representerar det datum då filen skapades.)|2|
    |0x12|Datum för senaste åtkomst (som introducerades av det långa fil namns formatet och representerar det datum då filen senast användes.)|2|
    |0x14|Startar kluster (högst 16 bitar FAT-32)|2|
    |0x16|Ändrings tid|2|
    |0x18|Ändringsdatum|2|
    |0x1A|Starta kluster (lägre 16 bitar FAT-32 eller FAT-12 eller FAT-16)|2|
    |0x1C|Filstorlek|4|


- **Katalogattribut**

    Fält posten med en byte- *katalog* innehåller en serie bitar som anger olika egenskaper för katalog posten. Definitioner av katalogens attribut är som följer:

    |Attribut-bit|Innebörd|
    |------------|-----------|
    |0x01|Posten är skrivskyddad.|
    |0x02|Posten är dold.|
    |0x04|Posten är en system post.|
    |0x08|Posten är en volym etikett|
    |0x10|Posten är en katalog.|
    |0x20|Posten har ändrats.|

    Eftersom alla attribut för attribut är ömsesidigt uteslutande kan det finnas mer än en bit uppsättning i taget.

- **Katalog tid**

    Fältet för *katalog tid* med två byte innehåller timmar, minuter och sekunder för den senaste ändringen av den angivna katalog posten. Bitarna 15 till 11 innehåller timmarna, bitarna 10 och 5 innehåller minuterna och bitarna 4 även om 0 innehåller halv sekunder. Faktiska sekunder delas av två innan de skrivs till det här fältet.

- **Katalog datum**

    Datum fältet för *katalog* med två byte innehåller året (förskjutning från 1980), månad och dag för den senaste ändringen av den angivna katalog posten. Bitarna 15 till 9 innehåller årets förskjutning, bitarna 8 till 5 innehåller månads förskjutningen och bitarna 4 till 0 innehåller dagen.

- **Katalog som startar kluster**

    I det här fältet upptas 2 byte för FAT-12 och FAT-16. För FAT-32 upptar det här fältet 4 byte. Det här fältet innehåller det första kluster nummer som tilldelas posten (under katalog eller fil).

    > [!NOTE]
    > * Observera att FileX skapar nya filer utan ett första kluster (som är lika med noll) så att användarna kan välja att allokera ett sammanhängande antal kluster för en nyligen skapad fil. *

- **Katalog fils storlek**

    Fältet storlek för *katalog* *fil* med fyra byte innehåller antalet byte i filen. Om posten verkligen är en under katalog är fältet storlek noll.

### <a name="long-file-name-directory"></a>Katalog för långt fil namn

- **Ordningstal**

    Det enbyte- *ordnings* fält som anger numret för LFN-posten. Eftersom LFN-poster placeras i omvänd ordning, kommer ordnings värden för LFN Directory-poster som består av en enda LFN att minska med ett. Dessutom måste ordnings talet för LFN vara direkt före 8,3-fil namnet.

    **TABELL 4. Katalog post för långt fil namn**

    | Offset | Fält | Antal byte |
    |------------|-----------|------------|
    | 0x00 | Ordnings fält | 1 |
    | 0x01 | Unicode-tecken 1 | 2 |
    | 0x03 | Unicode-tecken 2 | 2 |
    | 0x05 | Unicode-tecken 3 | 2 |
    | 0x07 | Unicode-tecken 4 | 2 |
    | 0x09 | Unicode-tecken 5 | 2 |
    | 0x0B | LFN-attribut | 1 |
    | 0x0C | LFN-typ (reserverad Always Always 0) | 1 |
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

    *Unicode-tecken* i två byte är utformade för att stödja tecken från många olika språk. ASCII-standardtecken representeras med ASCII-tecknet som lagras i den första byten i Unicode-tecknet följt av ett blank stegs tecken.

- **LFN-attribut**

    Fältet *LFN-attribut* med en byte innehåller attribut som identifierar katalog posten som en LFN-katalog post. Detta åstadkommer du genom att använda attributen skrivskyddad, system, Dold och volym.

- **Typ av LFN**

    Typ fältet med en byte- *LFN* är reserverat och är alltid 0.

- **LFN-kontrollsumma**

    Fältet för *kontroll Summa* för en byte-LFN representerar en kontroll summa för de 11 tecknen i det associerade fil namnet för MSDOS 8,3. Den här kontroll summan lagras i varje LFN-post för att se till att LFN-posten motsvarar lämpligt 8,3-filnamn.

- **LFN-kluster**

    *LFN kluster* fält med två byte används inte och är alltid 0.

    **TABELL 5. Katalog poster som består av en 39-teckenuppsättning LFN**

    |Post|Innebörd|
    |------------|-----------|
    |1|LFN katalog post 3|
    |2|LFN katalog post 2|
    |3|LFN katalog post 1|
    |4|8,3 katalog post (ttttt ~ n. xx)|

### <a name="exfat-directory-description"></a>Beskrivning av exFAT-katalog

exFAT fil system lagrar katalog post och fil namn på olika sätt. Katalog posten innehåller postens attribut, olika tidsstämplar på när posten skapades, ändrades och öppnades. Annan information, till exempel fil storlek och start kluster, lagras i katalog posten Stream-tillägg som omedelbart följer den primära katalog posten. exFAT stöder endast fil namns formatet Long File name (LFN). som lagras i katalog posten fil namn omedelbart efter katalog posten Stream Extension, som visas i tabell 2.

### <a name="exfat-file-directory-entry"></a>exFAT fil katalog post

En beskrivning av exFAT-filkatalogens post och dess innehåll ingår i följande tabell och stycken.

- **Typ av post**

    I fältet typ av post visas typen för den här posten. För fil katalog post måste det här fältet vara 0x85.

- **Antal sekundära poster**

    I fältet *antal för sekundär post* anges antalet sekundära poster omedelbart efter den här primära posten. Sekundära poster som är associerade med fil katalog posten inkluderar en katalog post för Stream-tillägg och ett eller flera fil namns katalog poster.

    **TABELL 6. exFAT fil katalog post**

    |Offset|Fält|Antal byte|
    |----|-----------|-|
    |0x00|Typ av post|1|
    |0x01|Sekundär post|1|
    |0x02|Kontrollsumma|2|
    |0x04|Filattribut|2|
    |0x06|Reserverade 1|2|
    |0x08|Skapa tidsstämpel|4|
    |0x0C|Tidsstämpel för senaste ändring|4|
    |0x10|Tidsstämpel för senaste åtkomst|4|
    |0x14|Skapa 10ms-ökning|1|
    |0x15|Senaste ändrade 10ms-ökning|1|
    |0x16|Skapa UTC-förskjutning|1|
    |0x17|UTC-förskjutning senast ändrad|1|
    |0x18|UTC-förskjutning för senaste åtkomst|1|
    |0x19|Reserverad 2|7|

- **Lastning**

    Fältet *kontroll Summa* innehåller värdet för kontroll summan för alla poster i katalog post uppsättningen (fil katalog posten och dess sekundära poster).

- **Filattribut**

    Fält posten med en byte-attribut innehåller en serie bitar som anger olika egenskaper för katalog posten. Definitionen av de flesta attribut-bitar är identisk med FAT 12/16/32. Definitioner av katalogens attribut är följande:

    |Attribut-bit|Innebörd|
    |------------|-----------|
    |0x01| Posten är skrivskyddad|
    |0x02|Posten är dold|
    |0x04|Posten är en system post|
    |0x08|Posten är reserverad|
    |0x10|Posten är en katalog|
    |0x20|Posten har ändrats|
    |Alla andra bitar|Reserverat|

- **Reserved1**

    Det här fältet ska vara noll.

- **Skapa tidsstämpel**

    Fältet *skapa tidsstämpel* , som kombinerar information från fältet *skapa 10ms ökning* , beskriver det lokala datumet och tiden då filen eller katalogen skapades.

- **Tidsstämpel för senaste ändring**

    Fältet *senast ändrad timestamp* , som kombinerar information från fältet *senaste ändrade 10ms ökning* , beskriver det lokala datumet och tiden då filen eller katalogen senast ändrades. Se anteckningar nedan i tidsstämplar.

- **Tidsstämpel för senaste åtkomst**

    I fältet *senast använda tidsstämpel* beskrivs det lokala datumet och tiden då filen eller katalogen senast användes. Se anteckningar nedan i tidsstämplar.

- **Skapa 10ms-ökning**

    Fältet *skapa 10ms ökning* , som kombinerar information från fältet *skapa tidsstämpel* , beskriver det lokala datumet och tiden då filen eller katalogen skapades. Se anteckningar nedan i tidsstämplar.

- **Senaste ändrade 10ms-ökning**

    Fältet *senast ändrad 10ms ökning* , som kombinerar information från fältet *senast ändrad timestamp* , beskriver det lokala datumet och tiden då filen eller katalogen senast ändrades. Se anteckningar nedan i tidsstämplar.

- **Skapa UTC-förskjutning**

    I fältet *skapa UTC-förskjutning* beskrivs skillnaden mellan lokal tid och UTC-tid när filen eller katalogen skapades. Se anteckningar nedan i tidsstämplar.

- **UTC-förskjutning senast ändrad**

    Fältet *senast ändrad UTC-förskjutning* beskriver skillnaden mellan lokal tid och UTC-tid när filen eller katalogen senast ändrades. Se anteckningar nedan i tidsstämplar.

- **UTC-förskjutning senast vid åtkomst**

    I fältet *senaste åtkomst till UTC-förskjutning* beskrivs skillnaden mellan lokal tid och UTC-tid när filen eller katalogen senast öppnades. Se anteckningar nedan i tidsstämplar.

- **Reserved2**

    Det här fältet ska vara noll.

### <a name="notes-on-timestamps"></a>Anteckningar om tidsstämplar

- **Tidsstämpel-post** Tidsstämplar-fälten tolkas enligt följande:

- **10Ms öknings fält** Värdet i fältet 10ms Increment ger bättre granularitet till värdet för tidsstämpeln. Giltiga värden är mellan 0 (0ms) och 199 (1990ms).

     ![10ms öknings fält](./media/user-guide/10ms-increment-fields.png)

- **Fält för UTC-förskjutning**

     ![Fält för UTC-förskjutning](./media/user-guide/utc-offset-field.png)

- **Förskjutnings värde**

    7-bitars signerat heltal representerar förskjutning från UTC-tid, i 15 minuters steg.

- **Ogiltigt**

    Huruvida värdet i fältet Offset är giltigt eller inte. 0 anger att värdet i fältet förskjutnings värde är ogiltigt. 1 anger att värdet är giltigt.

### <a name="stream-extension-directory-entry"></a>Katalog post för Stream-tillägg

En beskrivning av katalog posten för Stream-tillägget och dess innehåll finns i följande tabell.

**TABELL 7. Katalog post för Stream-tillägg**

|Offset|Fält| Antal byte|
|------------|-----------|-------|
|0x00|Typ av post|1|
|0x01|Flagg|1|
|0x02|Reserverade 1|1|
|0x03|Namn längd|1|
|0x04|Namn-hash|2|
|0x06|Reserverad 2|2|
|0x08|Giltig data längd|8|
|0x10|Reserverad 3|4|
|0x14|Första klustret|4|
|0x18|Data längd|8|

- **Typ av post**

    I fältet *typ av post* visas typen för den här posten. För katalog post för strömnings tillägg måste det här fältet vara 0xC0.

- **Flagg**

    Det här fältet innehåller en serie bitar som anger olika egenskaper:
    
    |Flagg bit|Innebörd    |
    |-----------------|-----------|
    |0x01            |Det här fältet anger om tilldelning av kluster är möjlig eller inte. Det här fältet ska vara 1.|
    |0x02            |Det här fältet anger om de associerade klustren är sammanhängande. Värdet 0 innebär att FAT-posten är giltig och att FileX ska följa FAT-kedjan. Värdet 1 innebär att FAT-posten är ogiltig och att klustren är sammanhängande.|
    |Alla andra bitar    |Reserverat.|

- **Reserverade 1**

    Det här fältet ska vara 0.

- **Namn längd**

    Fältet *namn längd* innehåller längden på Unicode-strängen i fil namns katalog posterna som sammantaget innehåller. Fil namns katalog posterna ska omedelbart följa katalog posten för Stream-tillägget.

- **Namn-hash**

    *Namn-hash* -fältet är en post med 2 byte, som innehåller hash-värdet för det bokstäver fil namnet. Hash-värdet tillåter snabbare fil-/katalog namns ökning: om hash-värdena inte matchar är fil namnet som är associerat med posten inte en matchning.

- **Reserverad 2**

    Det här fältet ska vara 0.

- **Giltig data längd**

    Fältet *giltig data längd* visar mängden giltiga data i filen.

- **Reserverad 3**

    Detta arkiverade ska vara 0.

- **Första klustret**

    Det *första kluster* fältet innehåller index för det första klustret i data strömmen.

- **Data längd**

    Fältet *data längd* innehåller det totala antalet byte i de allokerade klustren. Det här värdet kan vara större än *giltig data längd* eftersom exFAT tillåter för allokering av data kluster.

### <a name="root-directory"></a>Rotkatalog

I FAT 12-och 16-bitars format finns *rot katalogen* omedelbart efter alla fat-sektorer i mediet och kan hittas genom att undersöka ***fx_media_root_sector_start** _ i ett öppnat _ *FX_MEDIA** kontroll block. Storleken på rot katalogen, i antal katalog poster (varje 32 byte i storlek), bestäms av motsvarande post i medie start posten.

Rot katalogen i FAT-32-och exFAT kan finnas var som helst i de tillgängliga klustren. Plats och storlek bestäms från start posten när mediet öppnas. När mediet har öppnats kan fältet ***fx_media_root_sector_start*** användas för att hitta start klustret för rot katalogen FAT-32 eller exFAT.

### <a name="subdirectories"></a>Under kataloger

Det finns ett valfritt antal under kataloger i ett FAT-system. Namnet på under katalogen finns i en katalog post precis som ett fil namn. Men 0x10 (Directory Attribute Specification) är inställt på att ange att posten är en under katalog och att fil storleken alltid är noll.
Bild 3 visar hur en typisk under katalog struktur ser ut som för en ny singlecluster-underkatalog med namnet ***exempel. DIR** _ med en fil med namnet _ *_FILE.TXT_* *.
På de flesta sätt är under kataloger mycket likt fil poster. Det första kluster fältet pekar på det första klustret i en länkad lista över kluster. När en under katalog skapas, innehåller de första två katalog posterna standard kataloger, nämligen "."-katalogen och ".."-katalogen. Katalogen "." pekar till själva under katalogen, medan katalogen ".." pekar på den tidigare eller överordnade katalogen.

### <a name="global-default-path"></a>Global standard Sök väg

FileX tillhandahåller en global standard Sök väg för mediet. Standard Sök vägen används i alla fil-eller katalog tjänster som inte uttryckligen anger en fullständig sökväg.

Den globala standard katalogen är inlednings vis inställd på mediets rot Katalog. Detta kan ändras av programmet genom att anropa ***fx_directory_default_set***.

Den aktuella standard Sök vägen för mediet kan undersökas genom att anropa ***fx_directory_default_get** _. Den här rutinen innehåller en sträng pekare till standard Sök vägs strängen i _ *FX_MEDIA** Control Block.

### <a name="local-default-path"></a>Lokal standard Sök väg

FileX tillhandahåller också en tråd bestämd standard Sök väg som tillåter olika trådar att ha unika sökvägar utan konflikter. **FX_LOCAL_PATHs** strukturen tillhandahålls av programmet under anrop till **_fx_directory_local_path_set_*_ och _*_fx_directory_local_path_restore_** för att ändra den lokala sökvägen för den anropande tråden.

Om det finns en lokal sökväg har den lokala sökvägen företräde framför den globala standard medie Sök vägen. Om den lokala sökvägen inte är konfigurerad eller om den är avmarkerad med ***fx_directory_local_path_clear*** tjänsten används mediets globala standard Sök väg en gång till.

## <a name="file-description"></a>Fil Beskrivning

FileX stöder standard-8,3-tecken och långa fil namn med tre tecken. Förutom ASCII-namnet innehåller varje fil post attributets attribut, senast ändrad tid och datum, start kluster indexet och storleken i byte för posten.

### <a name="file-allocation"></a>Filallokering

FileX stöder standardschemat för minnesallokering i FAT-format. Dessutom stöder FileX för kluster tilldelning av sammanhängande kluster. För att tillgodose detta skapas varje FileX-fil utan allokerade kluster. Kluster allokeras vid efterföljande Skriv förfrågningar eller på ***fx_file_allocate*** begär Anden om att förallokera sammanhängande kluster.

Bild 4, "FileX FAT-16-filexempel", visar en fil med namnet ***FILE.TXT*** med två sekventiella kluster som tilldelas från och med klustret 101, en storlek på 26 och alfabetet som data i filens första data kluster nummer 101.

### <a name="file-access"></a>Fil åtkomst

En FileX-fil kan öppnas flera gånger samtidigt för Läs behörighet. En fil kan dock bara öppnas en gång för skrivning. Informationen som används för att stödja fil åtkomsten finns i fil kontroll blocket ***FX_FILE*** .

> [!NOTE]
> *Observera att medie driv rutinen kan ange Skriv skyddet dynamiskt. Om detta inträffar avvisas alla Skriv förfrågningar och försök att öppna en fil som ska skrivas.*

### <a name="file-layout-in-exfat"></a>Fillayout i exFAT

Designen av exFAT kräver inte att FAT-kedjan upprätthålls för en fil om data lagras i smittsamma kluster. *NoFATChain* -biten i katalog posten för Stream-tillägget anger om fat-kedjan ska användas vid läsning av data från filen. Om *NoFATChain* är inställt läser FileX i turordning från klustret som anges i det *första kluster* fältet i katalog posten för Stream-tillägget.

Å andra sidan, om *NoFATChain* är Clear, kommer FileX att följa fat-kedjan för att gå igenom hela filen, ungefär som fat-kedjan i FAT12/16/32.

Bild 3 visar två exempelfiler, en kräver ingen FAT-kedja och den andra kräver en FAT-kedja.

## <a name="system-information"></a>Systeminformation

FileX system information består av att hålla koll på de öppna medie instanserna och underhålla den globala system tiden och det aktuella datumet.

![Fil med sammanhängande kluster eller fil som kräver FAT-länk](./media/user-guide/system-information.png)

**BILD 3. Fil med sammanhängande kluster eller fil som kräver FAT-länk**

Som standard anges system datum och-tid till senaste versions datum för FileX. För att få korrekt system datum och tid måste programmet anropa ***fx_system_time_set** _ och _ *_fx_system_date_set_** under initieringen.

### <a name="system-date"></a>System datum

System datumet för FileX underhålls i den globala ***_fx_system_date*** -variabeln. Bitarna 15 till 9 innehåller årets förskjutning från 1980, bitarna 8 till 5 innehåller månads förskjutningen och bitarna 4 till 0 innehåller dagen. |

### <a name="system-time"></a>System tid

System tiden för FileX underhålls i den globala ***_fx_system_time*** -variabeln. Bitarna 15 till 11 innehåller timmarna, bitarna 10 och 5 innehåller minuterna och bitarna 4 även om 0 innehåller halv sekunder.

### <a name="periodic-time-update"></a>Periodisk tids uppdatering

Under system initieringen skapar FileX en ThreadX-programtimer för att regelbundet uppdatera system datum och-tid. Den hastighet med vilken system datum och tids uppdatering bestäms av två konstanter som används av funktionen ***_fx_system_initialize*** .

Konstanterna **FX_UPDATE_RATE_IN_SECONDS** och **FX_UPDATE_RATE_IN_TICKS** representerar samma tids period. Konstant **FX_UPDATE_RATE_IN_TICKS** är antalet ThreadX timer-Tick som representerar antalet sekunder som anges av konstanten **FX_UPDATE_RATE_IN_SECONDS**. **FX_UPDATE_RATE_IN_SECONDS** konstant anger hur många sekunder mellan varje FileX tids uppdatering. Det innebär att den interna FileX-tiden ökar i intervall med **FX_UPDATE_RATE_IN_SECONDS**. Dessa konstanter kan anges under kompileringen av **_fx_system_initialize_*_, eller så kan utvecklaren ändra standardvärdena som finns i filen _*_fx_port. h_** i FileX-versionen.

Den periodiska FileX-timern används endast för att uppdatera det globala systemets datum och tid, som endast används för tids stämpling av filer. Om tids stämpling inte behövs definierar du bara **FX_NO_TIMER** när du kompilerar **_fx_system_initialize. c_** för att eliminera skapandet av den periodiska timern för FileX.

![FileX FAT – 16-filexempel](./media/user-guide/fat-16-file-example.png)

**BILD 4. FileX FAT – 16-filexempel**
