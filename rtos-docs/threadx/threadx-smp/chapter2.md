---
title: Kapitel 2 – installation & användning av Azure återställnings tider ThreadX SMP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av HighPerformance Azure återställnings tider ThreadX SMP kernel.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cc352ebd7965c84c341d25dfa7bff2671dfb5e66
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550260"
---
# <a name="chapter-2---installation--use-of-azure-rtos-threadx-smp"></a>Kapitel 2 – installation & användning av Azure återställnings tider ThreadX SMP

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av HighPerformance Azure återställnings tider ThreadX SMP kernel.

## <a name="host-considerations"></a>Värd överväganden

Inbäddad program vara utvecklas vanligt vis på Windows-eller Linux-värddatorer (UNIX). När programmet har kompilerats, länkats och finns på värden laddas den ned till mål maskin varan för körning.

Normalt görs mål hämtningen från utvecklings verktygets fel sökare. Efter nedladdningen ansvarar fel sökaren för att tillhandahålla mål körnings kontroll (gå till, stoppa, Bryt punkt osv.) samt åtkomst till minne och processor register.

De flesta utvecklings verktyg för fel sökning kommunicerar med mål maskin varan via OCD-anslutningar (on-chip debug) som JTAG (IEEE 1149,1) och fel söknings läge för bakgrunden (BDM). Fel sökare kommunicerar också med mål maskin vara via ICE-anslutningar (In-Circuit emulation). Både OCD-och ICE-anslutningar ger robusta lösningar med minimalt intrång på den inhemske program varan.

För resurser som används på värden levereras käll koden för ThreadX SMP i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hård disk.

> [!IMPORTANT]
> Granska den tillhandahållna **readme_threadx.txt** -filen för ytterligare överväganden och alternativ för värd systemet.

## <a name="target-considerations"></a>Mål överväganden

ThreadX SMP kräver mellan 2 KByte och 20 KB skrivskyddat minne (ROM) på målet. Ytterligare 1 till 2 KByte av målets RAM-minne (Random Access Memory) krävs för den ThreadX SMP-systemstacken och andra globala data strukturer.

För timer-relaterade funktioner som tids gränser för tjänst anrop, tids segmentering och programtimers för att fungera, måste den underliggande mål maskin varan tillhandahålla en regelbunden avbrotts källa. Om processorn har den här funktionen används den av ThreadX SMP. Annars, om mål processorn inte har möjlighet att generera ett periodiskt avbrott måste användarens maskin vara tillhandahålla den. Installation och konfiguration av timer-avbrott finns vanligt vis i ***tx_initialize_low_level*** sammansättnings filen i ThreadX SMP-distribution.

> [!IMPORTANT]
> ThreadX SMP fungerar fortfarande även om ingen återkommande timer-källa för avbrott är tillgänglig. Men ingen av de timer-relaterade tjänsterna fungerar. Granska den tillhandahållna **readme_threadx.txt** -filen för eventuella ytterligare överväganden och/eller alternativ i värd systemet.

## <a name="product-distribution"></a>Produkt distribution

Det exakta innehållet på distributions disken beror på mål processorn, utvecklingsverktyg och ThreadX SMP-paketet som köpts. Följande är dock en lista över flera viktiga filer som är gemensamma för de flesta produkt distributioner:

### <a name="threadx_express_startuppdf"></a>ThreadX_Express_Startup.pdf

Den här PDF-filen innehåller en enkel, fyra stegs procedur för att få ThreadX SMP som körs på en speciell mål processor/tavla och specifika utvecklingsverktyg.

### <a name="readme_threadxtxt"></a>readme_threadx.txt

Textfil som innehåller detaljerad information om ThreadX SMP-port, inklusive information om mål processorn och utvecklingsverktyg.

| Verktyg | Beskrivning |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **tx_api. h**  | C-huvudfilen som innehåller alla system likställda, data strukturer och tjänst prototyper.             |
| **tx_port. h** | C-huvudfil som innehåller alla utvecklings verktyg och targetspecific data definitioner och strukturer. |
|**demo_threadx. c**| C-fil som innehåller ett litet demo program.|
|**TX. a (eller TX. lib)**| Binär version av ThreadX SMP C-biblioteket som distribueras med *standard* paketet.|

> [!IMPORTANT]
> Alla fil namn är i gemener. Med den här namngivnings konventionen blir det enklare att konvertera kommandon till plattformar med Linux (UNIX).

## <a name="threadx-smp-installation"></a>ThreadX SMP-installation

Det är enkelt att installera ThreadX SMP. Se ***ThreadX_Express_Startup.pdf** _-filen och _ *_readme_threadx.txt_**-filen för information om hur du installerar ThreadX SMP för din speciella miljö.

> [!IMPORTANT]
> Se till att säkerhetskopiera ThreadX SMP-postdistributionsgrupp och lagra den på en säker plats.

> [!IMPORTANT]
> Program varan behöver åtkomst till ThreadX SMP-biblioteks fil (vanligt vis **TX. a** eller **TX. lib**) och C include-filerna **tx_api. h** och **tx_port. h**. Detta åstadkommer du genom att ange lämplig sökväg för utvecklingsverktyg eller genom att kopiera filerna till program utvecklings ytan.

## <a name="using-threadx-smp"></a>Använda ThreadX SMP

Det är enkelt att använda ThreadX SMP. I princip måste program koden innehålla ***tx_api. h** _ under kompileringen och länkas med ThreadX SMP-testbiblioteket _*_TX. a_*_ (eller _ *_TX. lib)_* *.

Det krävs fyra steg för att bygga ett ThreadX SMP-program:

Inkludera filen ***tx_api. h*** i alla filer som använder ThreadX SMP-tjänster eller data strukturer.

Skapa standard C *-funktionen **main** _. Den här funktionen måste slutligen anropa _ *_tx_kernel_enter_** för att starta ThreadX SMP. Programspecifik initiering som inte omfattar ThreadX SMP kan läggas till innan du anger kärnan.

> [!IMPORTANT]
> ThreadX SMP-funktionen **tx_kernel_enter** returnerar inte. Se därför till att inte placera några bearbetnings-eller funktions anrop efter det.

Skapa funktionen ***tx_application_define*** . Det är här som de ursprungliga system resurserna skapas. Exempel på system resurser är trådar, köer, minnesmoduler, händelse flaggor grupper, mutexer och semaforer.

Kompilera program källan och länka med ThreadX SMP körnings bibliotek ***TX. lib***. Den resulterande bilden kan laddas ned till målet och köras!

## <a name="small-example-system"></a>Litet exempel system

I det lilla exempel systemet i bild 1 på sidan 28 visas skapandet av en enskild tråd med prioritet 3. Tråden körs, ökar en räknare och sedan vilo läge för ett klock streck. Den här processen fortsätter för alltid.

```c
#include              "tx_api.h"

unsigned long         my_thread_counter = 0;
TX_THREAD             my_thread;

main( )
{
      /* Enter the ThreadX SMP kernel. */
      tx_kernel_enter( );
}

void tx_application_define(void *first_unused_memory)
{

      /* Create my_thread! */
      tx_thread_create(&my_thread, "My Thread",
          my_thread_entry, 0x1234, first_unused_memory, 1024,
             3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}

void my_thread_entry(ULONG thread_input)
{
      /* Enter into a forever loop. */
      while(1)
      {

            /* Increment thread counter. */
            my_thread_counter++;

            /* Sleep for 1 tick. */
            tx_thread_sleep(1);
      }
}
```
**BILD 1. Mall för program utveckling**

Även om det här är ett enkelt exempel ger det en lämplig mall för verklig program utveckling. Se ***readme_threadx.txt*** -filen igen om du vill ha mer information.

## <a name="troubleshooting"></a>Felsökning

Varje ThreadX SMP-port levereras med ett demonstrations program. Det är alltid en bra idé att först se till att demonstrations systemet körs, antingen på faktiskt mål maskin vara eller simulerad miljö.

> [!IMPORTANT]
> Mer information om demonstrations systemet finns i **readme_threadx.txt** -filen som medföljer distributionen.

Om demonstrations systemet inte körs korrekt är följande fel söknings tips:

  - Ta reda på hur mycket av demonstrationen som körs-ning.

  - Öka stack storlekarna (detta är mer viktigt i den faktiska program koden än för demonstrationen).

  - Återskapa ThreadX SMP-biblioteket med TX_ENABLE_STACK_CHECKING definierat. Detta aktiverar den inbyggda SMP-ThreadX.

  - Kringgå tillfälligt eventuella nyligen gjorda ändringar för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för support tekniker.

Följ de procedurer som beskrivs i "vad vi behöver från dig" på sidan 12 för att skicka informationen som samlas in från fel söknings stegen.

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ när du skapar ThreadX SMP-biblioteket och programmet med ThreadX SMP. Alternativen nedan kan definieras i program källan, på kommando raden eller i filen ***tx_user. h*** include.

> [!IMPORTANT]
> Alternativ som definieras i **tx_user. h** tillämpas endast om program-och ThreadX SMP-biblioteket har skapats med **TX_INCLUDE_USER_DEFINE_FILE** definierade.

### <a name="smallest-configuration"></a>Minsta konfiguration
För den minsta tecken storleken bör följande konfigurations alternativ för ThreadX SMP anses vara (i avsaknad av alla andra alternativ):

- TX_DISABLE_ERROR_CHECKING
- TX_DISABLE_PREEMPTION_THRESHOLD
- TX_DISABLE_NOTIFY_CALLBACKS 
- TX_DISABLE_REDUNDANT_CLEARING 
- TX_DISABLE_STACK_FILLING 
- TX_NOT_INTERRUPTABLE 
- TX_TIMER_PROCESS_IN_ISR

### <a name="fastest-configuration"></a>Snabbast konfiguration 
För den snabbaste körningen har samma konfigurations alternativ som används för den minsta konfigurationen, men med det här alternativet övervägs även:

- TX_REACTIVATE_INLINE

Granska ***readme_threadx.txt*** -filen för ytterligare alternativ för din aktuella version av ThreadX SMP. Detaljerade konfigurations alternativ beskrivs i början på sidan 28.

### <a name="global-time-source"></a>Global tids källa  
För andra Azure återställnings tider-produkter (FileX, NetX, GUIX, USBX osv.), definierar ThreadX SMP antalet ThreadX SMP timer-Tick som representerar en sekund. Andra uppfyller sina tids krav baserat på denna konstant. Som standard är värdet 100, vilket förutsätter ett periodiskt avbrott i 10ms. Användaren kan åsidosätta det här värdet genom att definiera TX_TIMER_TICKS_PER_SECOND med det önskade värdet i ***tx_port. h*** eller i IDE-eller kommando raden.

### <a name="detailed-configuration-options"></a>Detaljerade konfigurations alternativ

- **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** : när den definieras, aktiverar insamling av prestanda information på blockera pooler. Som standard är det här alternativet inte definierat.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** : när den definieras, aktiverar insamling av prestanda information i byte-pooler. Som standard är det här alternativet inte definierat.
- **TX_DISABLE_ERROR_CHECKING**: kringgår grundläggande fel kontroll av tjänst anrop. När den är definierad i program källan är all grundläggande parameter fel kontroll inaktive rad. Detta kan förbättra prestandan med så mycket som 30% och kan också minska bild storleken.

> [!NOTE]
> *Det är bara säkert att inaktivera fel kontrollen om programmet kan vara absolut garantera att alla indataparametrar alltid är giltiga under alla omständigheter, inklusive indataparametrar härledda från externa ingångar. Om ogiltiga indata har angetts i API: et med fel kontrollen inaktive rad, är det resulterande beteendet odefinierat och kan leda till minnes skada eller system krasch.*

> [!NOTE]
> *ThreadX SMP API returnerar värden som inte påverkas av att fel kontroll inaktive ras i fetstil i avsnittet "retur värden" i varje API-beskrivning i kapitel 4. Retur värden i fet stil är ogiltiga om fel kontrollen har inaktiverats med alternativet TX_DISABLE_ERROR_CHECKING.*
- **TX_DISABLE_NOTIFY_CALLBACKS** : när det är definierat inaktive ras aviserings återanrop för olika ThreadX SMP-objekt. Genom att använda det här alternativet minskar du kodens storlek och förbättrar prestandan. Som standard är det här alternativet inte definierat.
- **TX_DISABLE_PREEMPTION_THRESHOLD** : när det är definierat inaktive ras avstängningen-tröskelvärdet, vilket minskar kod storleken och ökar prestandan. Preemptionthreshold-funktionerna är naturligtvis inte längre tillgängliga. Som standard är det här alternativet inte definierat.
- **TX_DISABLE_REDUNDANT_CLEARING** : när du definierar den här koden tas logiken bort för att initiera globala C-datastrukturer för THREADX-SMP till noll. Detta bör endast användas om kompilatorns initierings kod anger alla oinitierade C globala data till noll. Genom att använda det här alternativet minskar du kodens storlek och förbättrar prestandan under initieringen. Som standard är det här alternativet inte definierat.
- **TX_DISABLE_STACK_FILLING** : när det är definierat inaktive ras 0xEF-värdet i varje byte av varje tråds stack när de skapas. Som standard är det här alternativet inte definierat.
- **TX_ENABLE_EVENT_TRACE** : när det är definierat aktiverar ThreadX SMP händelse insamlings koden för att skapa en TraceX-spårningssession. Mer information finns i användar handboken för TraceX.
- **TX_ENABLE_STACK_CHECKING** : när det är definierat aktiverar ThreadX SMP körnings stack kontroll, vilket innefattar analys av hur mycket stack som har använts och granskning av data mönster "avgränsningar" före och efter stackområdet. Om ett stack fel upptäcks, anropas den registrerade program stackens fel hanterare. Det här alternativet resulterar i en något ökad omkostnader och kod storlek. Mer information finns i **_tx_-thread_stack_error_notify_-** API: et. Som standard är det här alternativet inte definierat.
- **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** : när det är definierat, aktiverar insamling av prestanda information på händelse flaggor grupper. Som standard är det här alternativet inte definierat.
- **TX_INLINE_THREAD_RESUME_SUSPEND** : när den har definierats förbättrar ThreadX SMP **_tx_thread_resume_*_ och _*_tx_thread_suspend_** API-anrop via kod i rad. Detta ökar kod storleken men förbättrar prestandan för dessa två API-anrop.
- **TX_MAX_PRIORITIES** : definierar prioritets nivåer för ThreadX SMP. Giltiga värden är mellan 32 och 1024 (inklusive) och måste vara jämnt delbar med 32. Om antalet tillåtna nivåer ökar ökar RAM-användningen med 128 byte för varje grupp med 32 prioriteter. Det finns dock bara en försumbar effekt på prestanda. Som standard är det här värdet inställt på 32 prioritets nivåer.
- **TX_MINIMUM_STACK** : definierar den minsta stack storleken (i byte). Den används för fel kontroll när trådar skapas. Standardvärdet är port-Specific och finns i **_tx_port. h._**
- **TX_MISRA_ENABLE** : när den definieras använder THREADX SMP Misra C-kompatibla konventioner. Mer information finns i **_ThreadX_MISRA_Compliance.pdf_** .
- **TX_MUTEX_ENABLE_PERFORMANCE_INFO** : när det är definierat, aktiverar insamling av prestanda information på mutexer. Som standard är det här alternativet inte definierat.
- **TX_NO_TIMER** : när det är definierat är ThreadX SMP-tidslogiken helt inaktive rad. Detta är användbart i de fall där funktionerna för ThreadX SMP-timer (tråd vila, API-tidsgräns, tids segmentering och program timers) inte används.
- **TX_NOT_INTERRUPTABLE** : när det är definierat försöker ThreadX SMP inte minimera avbrotts utelåsnings tiden. Detta resulterar i snabbare körning men ökar snabbt avbrotts utelåsnings tiden.
- **TX_QUEUE_ENABLE_PERFORMANCE_INFO** : när den definieras, aktiverar insamling av prestanda information i köer. Som standard är det här alternativet inte definierat.
- **TX_REACTIVATE_INLINE** : när det är definierat utför återaktivering av ThreadX SMP timers på rad i stället för att använda ett funktions anrop. Detta förbättrar prestandan, men ökar kod storleken något. Som standard är det här alternativet inte definierat.
- **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** : när det är definierat, aktiverar insamling av prestanda information på semaforer. Som standard är det här alternativet inte definierat.
- **TX_THREAD_ENABLE_PERFORMANCE_INFO** : när den definieras, aktiverar insamling av prestanda information på trådar. Som standard är det här alternativet inte definierat.
- **TX_THREAD_SMP_CORE_MASK** : definierar en bit kart mask för kärn undantag. En 4-kärn-miljö har till exempel värdet 0xF för den här definierar.
- **TX_THREAD_SMP_DEBUG_ENABLE** : när det är definierat sparas ThreadX SMP-felsöknings information i en cirkulär buffert.
- **TX_THREAD_SMP_DYNAMIC_CORE_MAX** : aktiverar det dynamiska maximala antalet kärnor som kan justeras i körnings läge när det har definierats.
- **TX_THREAD_SMP_EQUAL_PRIORITY** : när det är definierat schemalägger ThreadX SMP endast lika prioritets trådar parallellt. Detta bör definieras innan du skapar ThreadX SMP-biblioteket.
- **TX_THREAD_SMP_INTER_CORE_INTERRUPT** : när det är definierat genererar ThreadX SMP ett avbrott mellan kärnor.
- **TX_THREAD_SMP_MAX_CORES** : definierar det maximala antalet kärnor.
- **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT** : när det här definieras används standardvärden för ThreadX SMP alla trådar och timers som ska köras på Core 0 som standard. Programmet kan åsidosätta detta genom att anropa de viktigaste undantags-API: erna. Detta bör definieras innan du skapar ThreadX SMP-biblioteket.
- **TX_THREAD_SMP_WAKEUP_LOGIC** : när det är definierat anropas program makrot för Väcknings Core "i". Detta bör definieras innan du kan inkludera **_tx_port. h._**
- **TX_THREAD_SMP_WAKEUP (i)** : definierar ett program makro för Väcknings Core "i". Detta bör definieras innan du kan inkludera **_tx_port. h._**
- **TX_TIMER_ENABLE_PERFORMANCE_INFO** : när den definieras, aktiverar insamling av prestanda information för timers. Som standard är det här alternativet inte definierat.
- **TX_TIMER_PROCESS_IN_ISR** : om det här alternativet definieras elimineras den interna systemets timer-tråd för ThreadX SMP. Detta resulterar i bättre prestanda vid timer-händelser och mindre RAM-krav eftersom timer-stacken och kontroll blocket inte längre behövs. Om du använder det här alternativet flyttas all timer för förfallo tid till ISR-nivå. Som standard är det här alternativet inte definierat.

    > [!NOTE]
    > De tjänster som tillåts från timers kan inte vara tillåtna från ISR: er och kan därför inte tillåtas när du använder det här alternativet.

- **TX_TIMER_THREAD_PRIORITY** : definierar prioriteten för den interna ThreadX-tråden i SMP-systemet. Standardvärdet är Priority 0, högst prioritet i ThreadX SMP. Standardvärdet är definierat i **_tx_port. h._**
- **TX_TIMER_THREAD_STACK_SIZE** : definierar stack storleken (i byte) för den interna ThreadX-tråden för SMP-systemtimer. Den här tråden bearbetar alla tråd Ströms begär Anden och alla tids gränser för tjänst anrop. Dessutom anropas alla rutiner för återanrop från program timer från den här kontexten. Standardvärdet är port-Specific och finns i **_tx_port. h._**

## <a name="threadx-smp-version-id"></a>ID för ThreadX SMP-version

Du hittar ThreadX SMP-versions-ID i ***readme_threadx.txt** _-filen. Den här filen innehåller också en versions historik för motsvarande port. Program varan kan hämta ThreadX SMP-versionen genom att undersöka den globala strängen _ *_ _tx_version_id._**