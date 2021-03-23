---
title: Kapitel 2 – installation och användning av GUIX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av HighPerformance-GUIX för användar gränssnittet.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826391"
---
# <a name="chapter-2---installation-and-use-of-guix"></a>Kapitel 2 – installation och användning av GUIX

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av HighPerformance-GUIX för användar gränssnittet.  

## <a name="host-considerations"></a>Värd överväganden

Inbäddad utveckling utförs vanligt vis på Windows-eller Linux-värddatorer (UNIX). När programmet har kompilerats, länkats och den körbara filen genereras på värden laddas den ned till mål maskin varan för körning.

Normalt görs mål hämtningen från utvecklings verktygets fel sökare. Efter nedladdningen ansvarar fel sökaren för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.

De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM). Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation). Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.

För resurser som används på värden levereras käll koden för GUXI i ASCII-format och kräver cirka 30 MB utrymme på värddatorns hård disk.

## <a name="target-considerations"></a>Mål överväganden

GUIX kräver mellan 5 KByte och 80 KB Read-Only minne (ROM) på målet. En annan 5 till 10KBytes av målets RAM-minne (Random Access Memory) krävs för GUIX-trådens stack och andra globala data strukturer.

Dessutom kräver GUIX användningen av en ThreadX-timer och ett ThreadX mutex-objekt. Dessa funktioner används för periodiska bearbetnings behov och tråd skydd i GUIX.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-GUIX kan hämtas från vår offentliga käll kods lagrings plats på <https://github.com/azure-rtos/guix/> .

Följande är en lista över viktiga filer som är vanliga för de flesta produkt distributioner:

| Sökväg&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Beskrivning   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gx_api. h        | Den här C-huvudfilen innehåller alla system likställda, data strukturer och tjänst prototyper. |
| gx_port. h       | Den här C-huvudfilen innehåller alla språkspecifika och utvecklingsverktyg specifika data definitioner och strukturer.                                                                                                                                         |
| GX. a (eller GX. lib) | Det här är den binära versionen av GUIX C-biblioteket. Detta skapas vanligt vis genom att kompilera och arkivera den tillhandahållna GUIX biblioteks-källfilerna, men det här biblioteket kan finnas i fördefinierat format beroende på maskin varu mål och licens typ. |
|

> [!IMPORTANT]
> *Alla filer är i gemener, vilket gör det enkelt att konvertera kommandon till plattforms utvecklings plattformarna för Linux (UNIX).*

## <a name="guix-installation"></a>GUIX-installation

GUIX installeras genom att klona GitHub-lagringsplatsen till den lokala datorn. Följande är en typisk syntax för att skapa en klon av GUIX-lagringsplatsen på din dator:

```c
    git clone https://github.com/azure-rtos/guix
```

Alternativt kan du ladda ned en kopia av lagrings platsen med hjälp av knappen Ladda ned på GitHub-huvud sidan.

Du hittar också instruktioner för att skapa GUIX-biblioteket på den första sidan i online-lagringsplatsen.

>[!NOTE]  
> *Program varan behöver åtkomst till biblioteks filen GUIX, vanligt vis kallad **GX. a** (eller **GX. lib**) och C include-filerna **gx_api. h** och **gx_port. h**. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklings ytan.*

## <a name="using-guix"></a>Använda GUIX

Det är enkelt att använda GUIX. I princip måste program koden innehålla ***gx_api. h** _ under kompilering och länk med GUIX-biblioteket _*_GX. a_*_ (eller _ *_GX. lib_*) *.

Det finns fyra enkla steg som krävs för att bygga ett GUIX-program:

| Steg   | Beskrivning    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Steg &nbsp; 1: | Inkludera filen ***gx_api. h*** i alla filer som använder GUIX Services eller data strukturer.                                                               |
| Steg &nbsp; 2: | Initiera GUIX-systemet genom att anropa ***gx_system_initialize** _ från funktionen _ *_tx_application_define_** eller en program tråd.                       |
| Steg &nbsp; 3: | Skapa en visnings instans, skapa en arbets yta för visningen och skapa rot fönstret och alla andra Windows-och widgetar som behövs.                                 |
| Steg &nbsp; 4: | Kompilera program källan och länka med GUIX runtime library ***GX. a** _ (eller _ *_GX. lib_* *). Den resulterande bilden kan laddas ned till målet och köras! |

## <a name="troubleshooting"></a>Felsökning

Varje GUIX-port levereras med ett demonstrations program som körs på specifik skärm maskin vara. Samma grundläggande demonstration levereras med alla versioner av GUIX. Det är alltid en bra idé att få demonstrations systemet igång först.

Om demonstrations systemet inte körs korrekt utför du följande åtgärder för att begränsa problemet:

1. Ta reda på hur mycket av demonstrationen som körs.

2. Öka stack storleken för GUIX-tråden genom att ändra den konstant **GX_THREAD_STACK_SIZE** och kompilera om GUIX-biblioteket

3. Kompilera om biblioteket GUIX med lämpliga fel söknings alternativ som anges i avsnittet konfigurations alternativ.

4. Granska retur status från alla API-anrop.

5. Ta reda på om det finns ett internt systemfel genom att ange en Bryt punkt i funktionen ***_gx_system_error_process***. Felkoden och anroparen bör ge LED trådar för vad som kan gå fel.

6. Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för Microsofts support tekniker.

Följ de procedurer som beskrivs i avsnittet "vad vi behöver från dig" för att skicka den information som samlas in från fel söknings stegen.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar GUIX-biblioteket och programmet med GUIX. De här alternativen används för att justera bibliotekets storlek och funktions sätt för att passa dina program krav bäst. Om ditt program till exempel bara har en tråd som använder GUIX API-tjänster, bör konfigurations flaggan **GX_DISABLE_MULTITHREAD_SUPPORT** definieras för att eliminera den kostnad som är kopplad till att skydda viktiga kod avsnitt från Rekvirering av flera trådar. De olika konfigurations flaggorna kan definieras i program källan, på kommando raden eller i filen **_gx_user. h_** include.

När GUIX-bibliotekets konfigurations flaggor ändras måste du återskapa både GUIX-biblioteket och programmodulerna för att konfigurations ändringarna ska börja gälla.

Den fullständiga listan över konfigurations flaggor finns dokumenterad i bilaga H: GUIX Build-Time konfigurations flaggor.

## <a name="guix-version-id"></a>GUIX versions-ID

Den aktuella versionen av GUIX är tillgänglig för både användaren och program varan under körning. Programmerare kan hämta GUIX-versionen från undersökningen av filen ***gx_port. h** _. Dessutom innehåller den här filen även en versions historik för motsvarande program program för port program som kan hämta GUIX-versionen genom att undersöka den globala strängen _ *_ _gx_version_id_* _ i _ *_gx_port. h_* *.

Program varan kan också hämta versions information från de konstanter som visas nedan definierade i ***gx_api. h**. * Dessa konstanter identifierar den aktuella produkt versionen efter namn och produktens huvud-och del version.

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
