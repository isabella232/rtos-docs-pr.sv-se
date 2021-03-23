---
title: Kapitel 2 – installation och användning av Azure återställnings tider FileX
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider FileX och en beskrivning av installations villkor, procedurer och användning, inklusive följande
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6703b10d8e0895984bb92d74d5dff809dca1a7f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825509"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>Kapitel 2 – installation och användning av Azure återställnings tider FileX

Det här kapitlet innehåller en introduktion till Azure återställnings tider FileX och en beskrivning av installations villkor, procedurer och användning. 

## <a name="host-considerations"></a>Värd överväganden

### <a name="computer-type"></a>Typ av dator

Inbäddad utveckling utförs vanligt vis på Windows-eller Linux-värddatorer (UNIX). När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.

### <a name="download-interfaces"></a>Hämta gränssnitt

Normalt görs mål hämtningen från utvecklings verktygets fel sökare. Efter nedladdningen ansvarar fel sökaren för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.

### <a name="debugging-tools"></a>Fel söknings verktyg

De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM). Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation). Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.

### <a name="required-hard-disk-space"></a>Nödvändigt hårddisk utrymme

Käll koden för FileX levereras i ASCII-format och kräver cirka 500 KB utrymme på värddatorns hård disk

## <a name="target-considerations"></a>Mål överväganden

FileX kräver mellan 6 KByte och 30 KByte Read-Only minne (ROM) på målet. En annan 100 byte av målets RAM-minne (Random Access Memory) krävs för FileX globala data strukturer. Alla öppna Media kräver också 1,5 KByte RAM-minne för kontroll blocket, förutom RAM för lagring av data för en sektor (vanligt vis 512 byte).

För att datum-och tidsstämpeln ska fungera korrekt, förlitar sig FileX på ThreadX timer-anläggningar. Detta implementeras genom att skapa en FileX timer under initieringen av FileX. FileX förlitar sig även på ThreadX-semaforer för flera tråd skydd och I/O-inskjutningar.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-FileX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/filex/> .

Följande är en lista över flera viktiga filer i lagrings platsen:

- ***fx_api. h*** : den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper.
- ***fx_port. h*** : den här C-huvudfilen innehåller alla data definitioner och strukturer för utveckling-verktyg.
- ***demo_filex. c*** : den här c-filen innehåller ett litet demo program.
- ***FX. a (eller FX. lib)*** : det här är den binära versionen av FileX C-biblioteket. Den distribueras med standard paketet.

> [!IMPORTANT]
> *Alla fil namn är i gemener. Med den här namngivnings konventionen blir det enklare att konvertera kommandon till plattformar med Linux (UNIX).*

## <a name="filex-installation"></a>FileX-installation

FileX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av FileX-lagringsplatsen på din dator:

```c
    git clone https://github.com/azure-rtos/filex
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa FileX-biblioteket på den första sidan i online-lagringsplatsen.

> [!IMPORTANT]
> Program varan behöver åtkomst till FileX-biblioteks filen (kallas vanligt vis ***FX. a** _ eller _*_FX. lib_*_) _and C include-filerna **fx_api. h** och **fx_port. h**. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklings ytan.

## <a name="using-filex"></a>Använda FileX

Det är enkelt att använda FileX. I princip måste program koden innehålla ***fx_api. h** _ under kompileringen och länkas med FileX för kör tids bibliotek _*_FX. a_*_ (eller _*_FX. lib_*_). Självklart är ThreadX-filerna, nämligen _*_tx_api. h_*_ och _*_TX. a_*_ (eller _*_TX. lib_*_) _, * också obligatoriska.

> [!IMPORTANT]
> När du använder FileX i fristående läge (**FX_STANDALONE_ENABLE** måste definieras) krävs inte ThreadX-filer/-bibliotek.

Förutsatt att du redan använder ThreadX finns det fyra steg som krävs för att bygga ett FileX-program:

1. Inkludera filen ***fx_api. h*** i alla filer som använder FileX Services eller data strukturer.
1. Initiera FileX-systemet genom att anropa ***fx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en program tråd.

    > [!IMPORTANT]
    > När du använder FileX i fristående läge bör ***fx_system_initialize*** anropas direkt från program koden.

1. Lägg till ett eller flera anrop till ***fx_media_open*** för att konfigurera FileX-mediet. Anropet måste göras från en program tråds kontext.

    > [!IMPORTANT]
    > *Kom ihåg att **fx_media_open** -anropet kräver tillräckligt med RAM-minne för att lagra data för en sektor.*

1. Kompilera program källan och länka med FileX-och ThreadX-biblioteken för kör tid, ***FX. a** _ (eller _*_FX. lib_*_) och _*_TX. a_*_ (eller _ *_TX. lib_* *). Den resulterande bilden kan laddas ned till målet och köras!

## <a name="troubleshooting"></a>Felsökning

Varje FileX-port levereras med ett demonstrations program. Det är alltid en bra idé att få demonstrations systemet igång först, antingen på mål maskin varan eller en speciell demonstrations miljö.

Om demonstrations systemet inte fungerar kan du prova följande saker för att lösa problemet:

1. Ta reda på hur mycket av demonstrationen som körs.
1. Öka stack storlekarna (detta är mer viktigt i den faktiska program koden än för demonstrationen).
1. Se till att det finns tillräckligt med RAM-minne för 32KBytes. Det grundläggande systemet fungerar på mycket mindre RAM-minne. men eftersom mer av RAM-disken används, kommer problemen att vara en yta om det inte finns tillräckligt med minne.
1. Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för Microsofts support tekniker. Följ de procedurer som beskrivs i "kund Support Center" för att skicka den information som samlas in från fel söknings stegen.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar FileX-biblioteket och programmet med FileX. Alternativen nedan kan definieras i program källan, på kommando raden eller i filen ***fx_user. h*** include.

> [!IMPORTANT]
> *Alternativ som definieras i **fx_user. h** tillämpas endast om program-och ThreadX-biblioteket har skapats med **_FX_INCLUDE_USER_DEFINE_FILE_* _ Defined._ när du använder FileX i fristående läge (** FX_STANDALONE_ENABLE** måste definieras), ThreadX-filer/-bibliotek krävs inte.

I följande lista beskrivs varje konfigurations alternativ i detalj:

|Definierar|Innebörd|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |Det här värdet definierar den maximala fil namns längden, som innehåller det fullständiga Sök vägs namnet. Som standard är det här värdet 256.|
|FX_DONT_UPDATE_OPEN_FILES    |Definierad, FileX uppdaterar inte redan öppna filer.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Har angetts inaktive ras optimering av fil Sök cacheminnet.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Har angetts inaktive ras optimering av fil Sök cacheminnet.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |Definierad är den direkta läsnings uppdateringen av cachen inaktive rad.|
|FX_MEDIA_STATISTICS_DISABLE |Definierad, insamlingen av medie statistik är inaktive rad.|
|FX_SINGLE_OPEN_LEGACY |Definierad är äldre enkel öppen logik för samma fil aktive rad.|
|FX_RENAME_PATH_INHERIT    |Definierad, byter namn på ärver Sök vägs information.|
|FX_DISABLE_ERROR_CHECKING    |Tar bort API: et för grundläggande FileX-fel kontroll och ger bättre prestanda (så mycket som 30%) och mindre kod storlek.|
|FX_MAX_LONG_NAME_LEN    |Anger maximal storlek för fil namn för FileX. Standardvärdet är 256, men det kan åsidosättas med en kommando rads definition. Giltiga värden är mellan 13 och 256.|
|FX_MAX_SECTOR_CACHE|Anger det maximala antalet logiska sektorer som kan cachelagras av FileX. Det faktiska antalet sektorer som kan cachelagras är mindre av den här konstanten och hur många sektorer som får plats i mängden minne som anges i fx_media_open. Standardvärdet är 256. Alla värden måste vara en potens av 2.|
|FX_FAT_MAP_SIZE    |Anger antalet sektorer som kan representeras i FAT-uppdaterings kartan. Standardvärdet är 256, men det kan åsidosättas med en kommando rads definition. Större värden bidrar till att minska onödiga uppdateringar av sekundära FAT-sektorer.|
|FX_MAX_FAT_CACHE    |Anger antalet poster i intern FAT-cache. Standardvärdet är 16, men det kan åsidosättas med en kommando rads definition. Alla värden måste vara en potens av 2.|
|FX_FAULT_TOLERANT    |När det här alternativet har definierats skickar FileX omedelbart Skriv begär Anden för alla system sektorer (Start-, FAT-och katalog sektorer) till medie driv rutinen. Detta försämrar prestanda, men begränsar skadan till förlorade kluster. Observera att om du aktiverar den här funktionen aktive ras inte FileX feltolerant modul automatiskt, som aktive ras genom att definiera|
|FX_FAULT_TOLERANT_DATA    |När det här alternativet har definierats skickar FileX omedelbart alla fil data Skriv förfrågningar till medie driv rutinen. Detta minskar prestandan, men begränsar förlorade fildata. Observera att om du aktiverar den här funktionen aktive ras inte FileX feltolerant modul automatiskt, som aktive ras genom att definiera ***FX_ENABLE_FAULT_TOLERANT***|
|FX_NO_LOCAL_PATH|Tar bort den lokala Sök vägs logiken från FileX, vilket resulterar i mindre tecken storlek.|
|FX_NO_TIMER|Eliminerar ThreadX timer-installationen för att uppdatera FileX system tid och datum. Detta gör att standard tid och-datum placeras på alla fil åtgärder.|
|FX_UPDATE_RATE_IN_SECONDS    |Anger med vilken hastighet system tiden i FileX justeras. Som standard är värdet 10, vilket anger att system tiden för FileX uppdateras var 10: e sekund.|
|FX_ENABLE_EXFAT| När det är definierat är logiken för hantering av exFAT-filsystem aktive rad i FileX. Den här symbolen är inte definierad som standard.| 
|FX_UPDATE_RATE_IN_TICKS| Anger samma hastighet som ***FX_UPDATE_RATE_IN_SECONDS*** (se ovan), utom i termer av den underliggande frekvensen för ThreadX. Standardvärdet är 1000, vilket förutsätter en tidsbegränsning på 10ms ThreadX och ett 10 sekunders intervall.|
|FX_SINGLE_THREAD|Eliminerar ThreadX-skydds logik från FileX-källan. Den ska användas om FileX endast används från en tråd eller om FileX används utan ThreadX.|
|FX_DRIVER_USE_64BIT_LBA|När det är definierat aktiverar 64-bitars sektor adresser som används i I/O-drivrutinen. Som standard är det här alternativet inte definierat.|
|FX_ENABLE_FAULT_TOLERANT| När det är definierat aktiverar FileX feltolerant modul. När du aktiverar fel tolerans definieras automatiskt symbolen ***FX_FAULT_TOLERANT** _ och _ *_FX_FAULT_TOLERANT_DATA_* *. Som standard är det här alternativet inte definierat.|
|FX_FAULT_TOLERANT_BOOT_INDEX|Definierar byte förskjutning i Start sektorn där klustret för fel tolerans loggen är. Som standard är det här värdet 116. Det här fältet tar 4 byte. Byte 116 till 119 väljs eftersom de har marker ATS som reserverade av FAT 12/16/32/exFAT-specifikationen.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|Den här symbolen är föråldrad. Den används inte längre av FileX fel tolerans.|
|FX_STANDALONE_ENABLE|Definierad, gör att FileX kan användas i fristående läge (utan Azure-återställnings tider). Den här symbolen är inte definierad som standard.|

> [!IMPORTANT]
> När **FX_STANDALONE_ENABLE** har definierats inaktive ras den lokala Sök vägs logiken och ThreadX timer.

## <a name="filex-version-id"></a>FileX versions-ID

Den aktuella versionen av FileX är tillgänglig både för användaren och program varan under körnings tillfället. Programmerare kan hämta FileX-versionen från granskning av filen **fx_port. h** . Dessutom innehåller den här filen även en versions historik för motsvarande port. Program varan kan hämta FileX-versionen genom att undersöka den globala strängen **_ _fx_version_id_**.
