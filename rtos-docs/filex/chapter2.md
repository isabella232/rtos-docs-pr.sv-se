---
title: Kapitel 2 – Installation och användning av Azure RTOS FileX
description: Det här kapitlet innehåller en introduktion Azure RTOS FileX och en beskrivning av installationsvillkor, procedurer och användning, inklusive följande
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2f064fc65ef8445ea33590f23d5a040ed8b07c6c651ea4cf5c4aaef4b6c4fa7b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783857"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>Kapitel 2 – Installation och användning av Azure RTOS FileX

Det här kapitlet innehåller en introduktion Azure RTOS FileX och en beskrivning av installationsvillkor, procedurer och användning. 

## <a name="host-considerations"></a>Värdöverväganden

### <a name="computer-type"></a>Datortyp

Inbäddad utveckling utförs vanligtvis på Windows- eller Linux-värddatorer (Unix). När programmet har kompilerats, länkats och finns på värden laddas det ned till målmaskinvaran för körning.

### <a name="download-interfaces"></a>Ladda ned gränssnitt

Vanligtvis görs målnedladdningen från felsökningsverktygets felsökningsverktyg. Efter nedladdningen ansvarar felsökningsprogrammet för att tillhandahålla målkörningskontroll (go, halt, brytpunkt osv.) samt åtkomst till minne och processorregister.

### <a name="debugging-tools"></a>Felsökningsverktyg

De flesta felsökningsverktyg kommunicerar med målmaskinvaran via OCD-anslutningar (On-Chip Debug), till exempel JTAG (IEEE 1149.1) och Bakgrundsfelsökningsläge (BDM). Felsökningsprogrammet kommunicerar också med målmaskinvaran via In-Circuit(ICE) anslutningar. Både OCD- och ICE-anslutningar ger robusta lösningar med minimalt intrång på målprogramvaran.

### <a name="required-hard-disk-space"></a>Nödvändigt hårddiskutrymme

Källkoden för FileX levereras i ASCII-format och kräver cirka 500 KByte utrymme på värddatorns hårddisk

## <a name="target-considerations"></a>Målöverväganden

FileX kräver mellan 6 Kbyte och 30 Kbyte Read-Only (ROM) på målet. Ytterligare 100 byte av målets RAM-minne (Random Access Memory) krävs för globala FileX-datastrukturer. Varje öppet medium kräver också 1,5 KBYTE RAM för kontrollblocket, förutom RAM-minne för lagring av data för en sektor (vanligtvis 512 byte).

För att datum-/tidsstämplar ska fungera korrekt förlitar sig FileX på ThreadX-timerfunktioner. Detta implementeras genom att skapa en FileX-specifik timer under FileX-initieringen. FileX förlitar sig också på ThreadX-semaforer för skydd av flera trådar och I/O-stängning.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS FileX kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/filex/> .

Följande är en lista över flera viktiga filer på lagringsplatsen:

- ***fx_api.h:*** Den här C-huvudfilen innehåller alla systemekvat, datastrukturer och tjänstprototyper.
- ***fx_port.h:*** Den här C-huvudfilen innehåller alla datadefinitioner och strukturer som är specifika för utvecklingsverktyg.
- ***demo_filex.c:*** Den här C-filen innehåller ett litet demoprogram.
- ***fx.a (eller fx.lib):*** Det här är den binära versionen av FileX C-biblioteket. Den distribueras med standardpaketet.

> [!IMPORTANT]
> *Alla filnamn har gemener. Den här namngivningskonventionen gör det enklare att konvertera kommandona till Linux-utvecklingsplattformar (Unix).*

## <a name="filex-installation"></a>FileX-installation

FileX installeras genom att klona GitHub till din lokala dator. Följande är en vanlig syntax för att skapa en klon av FileX-lagringsplatsen på datorn:

```c
    git clone https://github.com/azure-rtos/filex
```

Du kan också ladda ned en kopia av lagringsplatsen med hjälp av nedladdningsknappen GitHub på huvudsidan.

Du hittar också anvisningar för att skapa FileX-biblioteket på startsidan för onlinedatabasen.

> [!IMPORTANT]
> Programprogramvaran behöver åtkomst till FileX-biblioteksfilen (kallas vanligtvis* vanligtvis ***fx.a** _ eller _*_fx.lib_*_) _and C innehåller **filerna fx_api.h** **och fx_port.h**. Detta åstadkoms antingen genom att ange lämplig sökväg för utvecklingsverktygen eller genom att kopiera dessa filer till programutvecklingsområdet.

## <a name="using-filex"></a>Använda FileX

Det är enkelt att använda FileX. I princip måste programkoden innehålla ***fx_api.h** _ under kompileringen och länka till FileX-körningsbiblioteket _*_fx.a_*_ _*_(eller fx.lib_*_). ThreadX-filerna, nämligen _*_tx_api.h_*_ och _*_tx.a_*_ (eller _*_tx.lib_*_)_,* krävs också.

> [!IMPORTANT]
> När du använder FileX i fristående läge (**FX_STANDALONE_ENABLE** måste definieras), krävs inte ThreadX-filer/bibliotek.

Förutsatt att du redan använder ThreadX krävs fyra steg för att skapa ett FileX-program:

1. Inkludera filen ***fx_api.h*** i alla programfiler som använder FileX-tjänster eller datastrukturer.
1. Initiera FileX-systemet genom att anropa ***fx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en programtråd.

    > [!IMPORTANT]
    > När du använder FileX i fristående ***läge fx_system_initialize*** anropas direkt från programkoden.

1. Lägg till ett eller flera ***anrop fx_media_open*** för att konfigurera FileX-mediet. Det här anropet måste göras från kontexten för en programtråd.

    > [!IMPORTANT]
    > *Kom ihåg att **fx_media_open** kräver tillräckligt med RAM-minne för att lagra data för en sektor.*

1. Kompilera programkällan och länka till FileX- och ThreadX-körningsbiblioteken, ***fx.a** _ (eller _*_fx.lib_*_) och _*_tx.a_*_ (eller _*_tx.lib_**). Den resulterande avbildningen kan laddas ned till målet och köras!

## <a name="troubleshooting"></a>Felsökning

Varje FileX-port levereras med ett demonstrationsprogram. Det är alltid en bra idé att få igång demonstrationssystemet först – antingen på målmaskinvaran eller i en specifik demonstrationsmiljö.

Om demonstrationssystemet inte fungerar kan du prova följande för att begränsa problemet:

1. Fastställ hur mycket av demonstrationen som körs.
1. Öka stackstorlekarna (detta är viktigare i den faktiska programkoden än den är för demonstrationen).
1. Se till att det finns tillräckligt med RAM-minne för ram-diskens standardstorlek på 32 KByte. Det grundläggande systemet fungerar på mycket mindre RAM-minne. Men när mer av RAM-disken används uppstår problem om det inte finns tillräckligt med minne.
1. Kringgå de senaste ändringarna tillfälligt för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för Microsofts supporttekniker. Följ procedurerna som beskrivs i "Customer Support Center" för att skicka den information som samlats in från felsökningsstegen.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar FileX-biblioteket och programmet med FileX. Alternativen nedan kan definieras i programkällan, på kommandoraden eller i ***indelningsfilen fx_user.h.***

> [!IMPORTANT]
> Alternativ som definieras ***i fx_user.h** tillämpas endast om programmet och ThreadX-biblioteket har skapats med **_FX_INCLUDE_USER_DEFINE_FILE_*_ defined._*** När du använder FileX i fristående läge ( FX_STANDALONE_ENABLE * måste definieras) krävs inte ThreadX-filer/-bibliotek.

I följande lista beskrivs varje konfigurationsalternativ i detalj:

|Definiera|Innebörd|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |Det här värdet definierar den maximala filnamnslängden, som innehåller det fullständiga sökvägsnamnet. Som standard är det här värdet 256.|
|FX_DONT_UPDATE_OPEN_FILES    |FileX uppdaterar inte redan öppnade filer.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Cacheoptimering för filsökning har definierats inaktiverat.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Cacheoptimering för filsökning har definierats inaktiverat.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |Definierad är direkt läsning sektoruppdatering av cache inaktiverad.|
|FX_MEDIA_STATISTICS_DISABLE |Definierad, insamling av mediestatistik är inaktiverat.|
|FX_SINGLE_OPEN_LEGACY |Definierad, äldre enkel öppen logik för samma fil är aktiverad.|
|FX_RENAME_PATH_INHERIT    |När du byter namn på definieras sökvägsinformation.|
|FX_DISABLE_ERROR_CHECKING    |Tar bort den grundläggande FileX-felkontrollens API och resulterar i bättre prestanda (upp till 30 %) och mindre kodstorlek.|
|FX_MAX_LONG_NAME_LEN    |Anger den maximala filnamnsstorleken för FileX. Standardvärdet är 256, men det kan åsidosättas med en kommandorads definiera. De juridiska värdena ligger mellan 13 och 256.|
|FX_MAX_SECTOR_CACHE|Anger det maximala antalet logiska sektorer som kan cachelagras av FileX. Det faktiska antalet sektorer som kan cachelagras är mindre av den här konstanten och hur många sektorer som får plats i mängden minne som fx_media_open. Standardvärdet är 256. Alla värden måste vara en strömförsörjning på 2.|
|FX_FAT_MAP_SIZE    |Anger antalet sektorer som kan representeras i FAT-uppdateringskartan. Standardvärdet är 256, men det kan åsidosättas med en kommandorads definiera. Större värden bidrar till att minska de uppdateringar som inte behöver uppdateras av sekundära FAT-sektorer.|
|FX_MAX_FAT_CACHE    |Anger antalet poster i den interna FAT-cachen. Standardvärdet är 16, men det kan åsidosättas med en kommandorads definiera. Alla värden måste ha värdet 2.|
|FX_FAULT_TOLERANT    |När FileX definieras skickar det omedelbart skrivbegäranden för alla systemsektorer (start-, FAT- och katalogsektorer) till mediets drivrutin. Detta minskar eventuellt prestandan, men hjälper till att begränsa skador på förlorade kluster. Observera att aktivering av den här funktionen inte automatiskt aktiverar FileX-feltolerant modul, vilket aktiveras genom att definiera|
|FX_FAULT_TOLERANT_DATA    |När FileX definieras skickar det omedelbart alla skrivbegäranden om fildata till mediets drivrutin. Detta minskar eventuellt prestandan, men hjälper till att begränsa förlorade fildata. Observera att aktivering av den här funktionen inte automatiskt aktiverar FileX-feltolerant modul, vilket aktiveras genom att definiera ***FX_ENABLE_FAULT_TOLERANT***|
|FX_NO_LOCAL_PATH|Tar bort logik för lokal sökväg från FileX, vilket resulterar i mindre kodstorlek.|
|FX_NO_TIMER|Eliminerar Installation av ThreadX-timern för att uppdatera FileX-systemets tid och datum. Detta gör att standardtid och -datum placeras på alla filåtgärder.|
|FX_UPDATE_RATE_IN_SECONDS    |Anger med vilken hastighet systemtiden i FileX justeras. Som standard är värdet 10 och anger att FileX-systemtiden uppdateras var 10:e sekund.|
|FX_ENABLE_EXFAT| När detta definieras aktiveras logiken för hantering av exFAT-filsystemet i FileX. Som standard definieras inte den här symbolen.| 
|FX_UPDATE_RATE_IN_TICKS| Anger samma hastighet som FX_UPDATE_RATE_IN_SECONDS ***(se*** ovan), förutom vad gäller den underliggande ThreadX-timerfrekvensen. Standardvärdet är 1 000, vilket förutsätter en 10 ms ThreadX-timerhastighet och ett intervall på 10 sekunder.|
|FX_SINGLE_THREAD|Eliminerar ThreadX-skyddslogik från FileX-källan. Den bör användas om FileX endast används från en tråd eller om FileX används utan ThreadX.|
|FX_DRIVER_USE_64BIT_LBA|När detta definieras aktiverar 64-bitars sektoradresser som används i I/O-drivrutinen. Som standard definieras inte det här alternativet.|
|FX_ENABLE_FAULT_TOLERANT| När detta definieras aktiverar FileX-feltolerant modul. När du aktiverar Feltolerant definieras automatiskt symbolen ***FX_FAULT_TOLERANT** _ och _*_FX_FAULT_TOLERANT_DATA_**. Som standard definieras inte det här alternativet.|
|FX_FAULT_TOLERANT_BOOT_INDEX|Definierar byteförskjutning i startsektorn där klustret för den feltoleranta loggen finns. Som standard är det här värdet 116. Det här fältet tar 4 byte. Byte mellan 116 och 119 väljs eftersom de har markerats som reserverade av FAT-specifikation 12/16/32/exFAT.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|Den här symbolen är inaktuell. Den används inte längre av FileX-feltolerant.|
|FX_STANDALONE_ENABLE|Definierad gör att FileX kan användas i fristående läge (utan Azure RTOS). Som standard definieras inte den här symbolen.|

> [!IMPORTANT]
> När **FX_STANDALONE_ENABLE** har definierats inaktiveras lokal sökvägslogik och Installation av ThreadX-timer.

## <a name="filex-version-id"></a>FileX-versions-ID

Den aktuella versionen av FileX är tillgänglig för både användaren och programprogramvaran under körningen. Programmeraren kan hämta FileX-versionen från undersökningen av **filen fx_port.h.** Dessutom innehåller den här filen även en versionshistorik för motsvarande port. Programprogramvara kan hämta FileX-versionen genom att undersöka den globala **strängen _ _fx_version_id_**.
