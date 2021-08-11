---
title: Kapitel 2 – Installation och användning av GUIX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av GUIX för högpresterande användargränssnitt.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a4572dbf4691869d9a1c32d68fbf9cc1c7dbfbee7e58ad69dd944e668e382b76
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784127"
---
# <a name="chapter-2---installation-and-use-of-guix"></a>Kapitel 2 – Installation och användning av GUIX

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av GUIX för högpresterande användargränssnitt.  

## <a name="host-considerations"></a>Värdöverväganden

Inbäddad utveckling utförs vanligtvis på Windows- eller Linux-värddatorer (Unix). När programmet har kompilerats, länkats och den körbara filen har genererats på värden laddas den ned till målmaskinvaran för körning.

Vanligtvis görs målnedladdningen från felsökningsverktygets felsökningsverktyg. Efter nedladdningen ansvarar felsökningsprogrammet för att tillhandahålla målkörningskontroll (go, halt, brytpunkt osv.) samt åtkomst till minne och processorregister.

De flesta felsökningsverktyg kommunicerar med målmaskinvaran via OCD-anslutningar (On-Chip Debug), till exempel JTAG (IEEE 1149.1) och Bakgrundsfelsökningsläge (BDM). Felsökningsprogrammet kommunicerar också med målmaskinvaran via In-Circuit(ICE) anslutningar. Både OCD- och ICE-anslutningar ger robusta lösningar med minimalt intrång i målprogramvaran.

Precis som för resurser som används på värden levereras källkoden för GUXI i ASCII-format och kräver cirka 30 MB utrymme på värddatorns hårddisk.

## <a name="target-considerations"></a>Målöverväganden

GUIX kräver mellan 5 och 80 Kbyte Read-Only (ROM) på målet. Ytterligare 5 till 10 KByte av målets RAM-minne (Random Access Memory) krävs för GUIX-trådstacken och andra globala datastrukturer.

Dessutom kräver GUIX användning av en ThreadX-timer och ett ThreadX mutex-objekt. Dessa anläggningar används för periodiska bearbetningsbehov och trådskydd i GUIX.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS GUIX kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/guix/> .

Följande är en lista över de viktiga filer som är gemensamma för de flesta produktdistributioner:

| Filnamn&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Description   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gx_api.h        | Den här C-huvudfilen innehåller alla systemkällor, datastrukturer och tjänstprototyper. |
| gx_port.h       | Den här C-huvudfilen innehåller alla målspecifika och utvecklingsverktygets specifika datadefinitioner och strukturer.                                                                                                                                         |
| gx.a (eller gx.lib) | Det här är den binära versionen av GUIX C-biblioteket. Detta bygger vanligtvis på att de angivna GUIX-bibliotekskällfilerna kompileras och arkiveras, men det här biblioteket kan tillhandahållas i förbyggt format beroende på maskinvarumål och licenstyp. |
|

> [!IMPORTANT]
> *Alla filer är i gemener, vilket gör det enkelt att konvertera kommandona till Linux-utvecklingsplattformar (Unix).*

## <a name="guix-installation"></a>GUIX-installation

GUIX installeras genom att klona GitHub till din lokala dator. Följande är en vanlig syntax för att skapa en klon av GUIX-lagringsplatsen på datorn:

```c
    git clone https://github.com/azure-rtos/guix
```

Du kan också ladda ned en kopia av lagringsplatsen med hjälp av nedladdningsknappen GitHub på huvudsidan.

Du hittar också anvisningar för att skapa GUIX-biblioteket på startsidan för onlinedatabasen.

>[!NOTE]  
> *Programprogramvaran behöver åtkomst till GUIX-biblioteksfilen, som vanligtvis kallas **gx.a** (eller **gx.lib**), och C innehåller filerna **gx_api.h** **och gx_port.h**. Detta åstadkoms antingen genom att ange lämplig sökväg för utvecklingsverktygen eller genom att kopiera dessa filer till programutvecklingsområdet.*

## <a name="using-guix"></a>Använda GUIX

Det är enkelt att använda GUIX. I princip måste programkoden innehålla ***gx_api.h** _ under kompileringen och länka till GUIX-biblioteket _*_gx.a_*_ (eller _ *_gx.lib_*)*.

Det krävs fyra enkla steg för att skapa ett GUIX-program:

| Steg   | Description    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Steg &nbsp; 1: | Inkludera filen ***gx_api.h i*** alla programfiler som använder GUIX-tjänster eller datastrukturer.                                                               |
| Steg &nbsp; 2: | Initiera GUIX-systemet genom att anropa ***gx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en programtråd.                       |
| Steg &nbsp; 3: | Skapa en visningsinstans, skapa en arbetsyta för visningen och skapa rotfönstret och eventuella andra fönster eller widgetar som behövs.                                 |
| Steg &nbsp; 4: | Kompilera programkällan och länka till GUIX-körningsbiblioteket ***gx.a** _ (eller _*_gx.lib_**). Den resulterande avbildningen kan laddas ned till målet och köras! |

## <a name="troubleshooting"></a>Felsökning

Varje GUIX-port levereras med ett demonstrationsprogram som körs på specifik visningsmaskinvara. Samma grundläggande demonstration levereras med alla versioner av GUIX. Det är alltid en bra idé att få igång demonstrationssystemet först.

Om demonstrationssystemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:

1. Fastställ hur mycket av demonstrationen som körs.

2. Öka stackstorleken för GUIX-tråden genom att ändra konstanten för kompileringstid **GX_THREAD_STACK_SIZE** och kompilera om GUIX-biblioteket

3. Kompilera om GUIX-biblioteket med lämpliga felsökningsalternativ som anges i avsnittet konfigurationsalternativ.

4. Granska returstatusen från alla API-anrop.

5. Kontrollera om det finns ett internt systemfel genom att ange en brytpunkt vid funktionen ***_gx_system_error_process***. Där bör felkoden och anroparen ge ledtrådar om vad som kan gå fel.

6. Kringgå de senaste ändringarna tillfälligt för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för Microsofts supporttekniker.

Följ procedurerna som beskrivs i avsnittet "What We Need From You" (Vad vi behöver från dig) för att skicka den information som samlas in från felsökningsstegen.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar GUIX-biblioteket och programmet med GUIX. De här alternativen används för att justera biblioteksstorleken och funktionsuppsättningen så att de passar dina programkrav på bästa sätt. Om ditt program till exempel bara har en tråd som använder GUIX API-tjänsterna ska konfigurationsflaggan **GX_DISABLE_MULTITHREAD_SUPPORT** definieras för att eliminera det omkostnader som är associerat med att skydda kritiska kodavsnitt från förebyggande av flera trådar. De olika konfigurationsflaggorna kan definieras i programkällan, på kommandoraden eller i **_indelningsfilen gx_user.h._**

När GUIX-bibliotekskonfigurationsflaggorna ändras, krävs det att både GUIX-biblioteket och programmodulerna återskapas för att konfigurationsändringarna ska gälla.

Den fullständiga listan med konfigurationsflaggor finns dokumenterad i Bilaga H: GUIX Build-Time Configuration Flags.

## <a name="guix-version-id"></a>GUIX-versions-ID

Den aktuella versionen av GUIX är tillgänglig för både användaren och programprogramvaran under körning. Programmeraren kan hämta GUIX-versionen från undersökningen av filen ***gx_port.h** _ . Dessutom innehåller den här filen även en versionshistorik för motsvarande port Programprogramvara kan hämta GUIX-versionen genom att undersöka den globala strängen *_ __ gx_version_id_* _ i _*_gx_port.h_**.

Programvaror kan också hämta versionsinformation från konstanterna som visas nedan och som definieras i ***gx_api.h**.* Dessa konstanter identifierar den aktuella produktversionen efter namn och produktens huvudversion och delversion.

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
