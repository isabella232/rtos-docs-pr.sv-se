---
title: Kapitel 2 – Installation & användning av Azure RTOS ThreadX SMP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS ThreadX SMP-kernel.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d0a63f3798adbc634a43cdda7e9d44941de655d9333f9ae0fb4181f1a6c0566e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801911"
---
# <a name="chapter-2---installation--use-of-azure-rtos-threadx-smp"></a>Kapitel 2 – Installation & användning av Azure RTOS ThreadX SMP

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS ThreadX SMP-kernel.

## <a name="host-considerations"></a>Värdöverväganden

Inbäddad programvara utvecklas vanligtvis på Windows- eller Linux-värddatorer (Unix). När programmet har kompilerats, länkats och finns på värden laddas det ned till målmaskinvaran för körning.

Vanligtvis görs målnedladdningen inifrån felsökningsprogrammet för utvecklingsverktyget. Efter nedladdningen ansvarar felsökningsprogrammet för att tillhandahålla målkörningskontroll (go, halt, brytpunkt osv.) samt åtkomst till minne och processorregister.

De flesta felsökningsverktyg kommunicerar med målmaskinvaran via OCD-anslutningar (on-chip debug), till exempel JTAG (IEEE 1149.1) och Bakgrundsfelsökningsläge (BDM). Felsökare kommunicerar också med målmaskinvaran via In-Circuit(ICE)-anslutningar. Både OCD- och ICE-anslutningar ger robusta lösningar med minimal intrång på målprogramvaran.

Precis som för resurser som används på värden levereras källkoden för ThreadX SMP i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hårddisk.

> [!IMPORTANT]
> Granska den angivna **readme_threadx.txt** ytterligare överväganden och alternativ för värdsystem.

## <a name="target-considerations"></a>Målöverväganden

ThreadX SMP kräver mellan 2 KByte och 20 KByte skrivskyddad minne (ROM) på målet. Ytterligare 1 till 2 KByte av målets RAM-minne (Random Access Memory) krävs för ThreadX SMP-systemstacken och andra globala datastrukturer.

För timerrelaterade funktioner som time out-time-out för tjänstanrop, tidsslikning och programtimer för att fungera måste den underliggande målmaskinvaran tillhandahålla en periodisk avbrottskälla. Om processorn har den här funktionen används den av ThreadX SMP. Om målprocessorn inte har möjlighet att generera ett regelbundet avbrott måste användarens maskinvara ange det. Installation och konfiguration av timeravbrottet finns vanligtvis i tx_initialize_low_level ***i*** ThreadX SMP-distributionen.

> [!IMPORTANT]
> ThreadX SMP fungerar fortfarande även om det inte finns någon källa för periodiskt timeravbrott. Ingen av de timerrelaterade tjänsterna fungerar dock. Granska den angivna **readme_threadx.txt** ytterligare värdsystemöverväganden och/eller alternativ.

## <a name="product-distribution"></a>Produktdistribution

Det exakta innehållet på distributionsdisken beror på målprocessorn, utvecklingsverktygen och det ThreadX SMP-paket som köpts. Följande är dock en lista över flera viktiga filer som är gemensamma för de flesta produktdistributioner:

### <a name="threadx_express_startuppdf"></a>ThreadX_Express_Startup.pdf

Den här PDF-filen innehåller en enkel procedur i fyra steg för att få ThreadX SMP att köras på en specifik målprocessor/-tavla och specifika utvecklingsverktyg.

### <a name="readme_threadxtxt"></a>readme_threadx.txt

Textfil som innehåller specifik information om ThreadX SMP-porten, inklusive information om målprocessorn och utvecklingsverktygen.

| Verktyg | Beskrivning |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **tx_api.h**  | C-rubrikfilen som innehåller alla system är lika med, datastrukturer och tjänstprototyper.             |
| **tx_port.h** | C-rubrikfil som innehåller alla utvecklingsverktyget och målspecifika datadefinitioner och strukturer. |
|**demo_threadx.c**| C-fil som innehåller ett litet demoprogram.|
|**tx.a (eller tx.lib)**| Binär version av ThreadX SMP C-biblioteket som distribueras med *standardpaketet.*|

> [!IMPORTANT]
> Alla filnamn har gemener. Den här namngivningskonventionen gör det enklare att konvertera kommandona till Linux-utvecklingsplattformar (Unix).

## <a name="threadx-smp-installation"></a>ThreadX SMP-installation

Det är enkelt att installera ThreadX SMP. Se filen ***ThreadX_Express_Startup.pdf** _ och filen _ *_readme_threadx.txt_** för specifik information om hur du installerar ThreadX SMP för din specifika miljö.

> [!IMPORTANT]
> Se till att backa upp ThreadX SMP-distributionsdisken och lagra den på en säker plats.

> [!IMPORTANT]
> Programprogramvaran behöver åtkomst till ThreadX SMP-biblioteksfilen (vanligtvis **tx.a** eller **tx.lib**) och C innehåller filerna **tx_api.h** **och tx_port.h**. Detta åstadkoms antingen genom att ange lämplig sökväg för utvecklingsverktygen eller genom att kopiera dessa filer till programutvecklingsområdet.

## <a name="using-threadx-smp"></a>Använda ThreadX SMP

Det är enkelt att använda ThreadX SMP. I princip måste programkoden innehålla ***tx_api.h** _ under kompileringen och länka till ThreadX SMP-körningsbiblioteket _*_tx.a_*_ (eller _*_tx.lib)_**.

Det krävs fyra steg för att skapa ett ThreadX SMP-program:

Inkludera filen ***tx_api.h i*** alla programfiler som använder ThreadX SMP-tjänster eller datastrukturer.

Skapa standardfunktionen C ***main** _ . Den här funktionen måste så småningom anropa _ *_tx_kernel_enter_** för att starta ThreadX SMP. Programspecifik initiering som inte omfattar ThreadX SMP kan läggas till innan kerneln matas in.

> [!IMPORTANT]
> Funktionen ThreadX **SMP-tx_kernel_enter** returnerar inte. Se därför till att inte placera några bearbetnings- eller funktionsanrop efter den.

Skapa ***tx_application_define*** funktion. Det är här som de första systemresurserna skapas. Exempel på systemresurser är trådar, köer, minnespooler, händelseflaggor, mutexes och semaforer.

Kompilera programkällan och länka till ThreadX SMP-körningsbiblioteket ***tx.lib***. Den resulterande avbildningen kan laddas ned till målet och köras!

## <a name="small-example-system"></a>Litet exempelsystem

Det lilla exempelsystemet i bild 1 på sidan 28 visar skapandet av en enda tråd med prioriteten 3. Tråden körs, ökar en räknare och för viloläger sedan för en klock tick. Den här processen fortsätter för alltid.

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
**BILD 1. Mall för programutveckling**

Även om det här är ett enkelt exempel är det en bra mall för verklig programutveckling. Mer information finns i ***readme_threadx.txt*** filen.

## <a name="troubleshooting"></a>Felsökning

Varje ThreadX SMP-port levereras med ett demonstrationsprogram. Det är alltid en bra idé att först få igång demonstrationssystemet – antingen på faktisk målmaskinvara eller simulerad miljö.

> [!IMPORTANT]
> Mer **readme_threadx.txt** information om demonstrationssystemet finns i filenreadme_threadx.txtsom medföljer distributionen.

Om demonstrationssystemet inte körs korrekt är följande några felsökningstips:

  - Fastställ hur mycket av demonstrationen som körs.

  - Öka stackstorlekarna (det här är viktigare i den faktiska programkoden än i demonstrationen).

  - Återskapa ThreadX SMP-biblioteket med TX_ENABLE_STACK_CHECKING definierat. Detta aktiverar den inbyggda ThreadX SMP-stackkontrollen.

  - Kringgå tillfälligt de senaste ändringarna för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för supporttekniker.

Följ procedurerna som beskrivs i "What We Need From You" på sidan 12 för att skicka den information som samlats in från felsökningsstegen.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar ThreadX SMP-biblioteket och programmet med ThreadX SMP. Alternativen nedan kan definieras i programkällan, på kommandoraden eller i filen ***tx_user.h*** include.

> [!IMPORTANT]
> Alternativ som **definieras i tx_user.h** tillämpas endast om programmet och ThreadX SMP-biblioteket har skapats med **TX_INCLUDE_USER_DEFINE_FILE** definieras.

### <a name="smallest-configuration"></a>Minsta konfiguration
För den minsta kodstorleken bör följande ThreadX SMP-konfigurationsalternativ övervägas (utan alla andra alternativ):

- TX_DISABLE_ERROR_CHECKING
- TX_DISABLE_PREEMPTION_THRESHOLD
- TX_DISABLE_NOTIFY_CALLBACKS 
- TX_DISABLE_REDUNDANT_CLEARING 
- TX_DISABLE_STACK_FILLING 
- TX_NOT_INTERRUPTABLE 
- TX_TIMER_PROCESS_IN_ISR

### <a name="fastest-configuration"></a>Snabbaste konfiguration 
För den snabbaste körningen bör samma konfigurationsalternativ som användes för den minsta konfigurationen tidigare, men med det här alternativet också övervägas:

- TX_REACTIVATE_INLINE

Granska ***readme_threadx.txt*** ytterligare alternativ för din specifika version av ThreadX SMP. Detaljerade konfigurationsalternativ beskrivs från och med sidan 28.

### <a name="global-time-source"></a>Global tidskälla  
För andra Azure RTOS produkter (FileX, NetX, GUIX, USBX osv.) definierar ThreadX SMP antalet ThreadX SMP-timer tick som representerar en sekund. Andra härleder sina tidskrav baserat på den här konstanten. Som standard är värdet 100, förutsatt ett periodiskt avbrott på 10 ms. Användaren kan åsidosätta det här värdet genom TX_TIMER_TICKS_PER_SECOND definiera med önskat ***värde i tx_port.h*** eller i IDE eller kommandoraden.

### <a name="detailed-configuration-options"></a>Detaljerade konfigurationsalternativ

- **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation för blockpooler. Det här alternativet är inte definierat som standard.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation för bytepooler. Det här alternativet är inte definierat som standard.
- **TX_DISABLE_ERROR_CHECKING: Kringgår** grundläggande felkontroll av tjänstsamtal. När den definieras i programkällan inaktiveras all grundläggande parameterfelkontroll. Detta kan förbättra prestandan med upp till 30 % och kan också minska bildstorleken.

> [!NOTE]
> *Det är bara säkert att inaktivera felkontroll om programmet absolut kan garantera att alla indataparametrar alltid är giltiga under alla omständigheter, inklusive indataparametrar som härletts från externa indata. Om ogiltiga indata har angetts till API:et med felkontroll inaktiverat är det resulterande beteendet odefinierat och kan resultera i minnesfel eller systemkrasch.*

> [!NOTE]
> *ThreadX SMP API-returvärden som inte påverkas av inaktivering av felkontroll visas i fetstil i avsnittet "Returvärden" i varje API-beskrivning i kapitel 4. Returvärdena för icke-boliska värden annulleras om felkontrollen inaktiveras med hjälp TX_DISABLE_ERROR_CHECKING alternativet.*
- **TX_DISABLE_NOTIFY_CALLBACKS:** Inaktiverar återanrop av avanrop för olika ThreadX SMP-objekt när de har definierats. Om du använder det här alternativet minskar kodstorleken något och prestandan förbättras. Det här alternativet är inte definierat som standard.
- **TX_DISABLE_PREEMPTION_THRESHOLD:** Inaktiverar funktionen för tröskelvärde för avaktivering när den definieras och minskar kodstorleken något och förbättrar prestandan. Funktionen preemptionthreshold är förstås inte längre tillgänglig. Det här alternativet är inte definierat som standard.
- **TX_DISABLE_REDUNDANT_CLEARING** : När det här definieras tar bort logiken för att initiera globala C-datastrukturer i ThreadX SMP till noll. Detta bör endast användas om kompilatorns initieringskod anger alla o initialiserade globala C-data till noll. Om du använder det här alternativet minskar kodstorleken något och prestandan förbättras under initieringen. Det här alternativet är inte definierat som standard.
- **TX_DISABLE_STACK_FILLING:** När det här definieras inaktiverar det 0xEF värdet i varje byte i varje trådstack när den skapas. Det här alternativet är inte definierat som standard.
- **TX_ENABLE_EVENT_TRACE:** När det här definieras aktiverar ThreadX SMP händelseinsamlingskoden för att skapa en TraceX-spårningsbuffert. Mer information finns i användarhandboken för TraceX.
- **TX_ENABLE_STACK_CHECKING:** När det här definieras aktiverar threadX SMP körningsstackkontroll, vilket innefattar analys av hur mycket stack som har använts och undersökning av datamönstret "stängsel" före och efter stackområdet. Om ett stackfel identifieras anropas felhanteraren för den registrerade programstacken. Det här alternativet resulterar i något högre omkostnader och kodstorlek. Läs **_api:et tx_- thread_stack_error_notify_** för mer information. Det här alternativet är inte definierat som standard.
- **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation om händelseflaggor grupper. Det här alternativet är inte definierat som standard.
- **TX_INLINE_THREAD_RESUME_SUSPEND:** När ThreadX SMP definieras förbättrar den tx_thread_resume _ och ***_*** tx_thread_suspend API-anrop via in-line-kod. Detta ökar kodstorleken men förbättrar prestandan för dessa två API-anrop.
- **TX_MAX_PRIORITIES:** Definierar prioritetsnivåer för ThreadX SMP. De juridiska värdena sträcker sig från 32 till 1024 (inklusive) och måste vara jämnt delbara med 32. Om du ökar antalet prioritetsnivåer som stöds ökar RAM-användningen med 128 byte för varje grupp med 32 prioriteringar. Det finns dock bara en försumbar effekt på prestanda. Som standard är det här värdet inställt på 32 prioritetsnivåer.
- **TX_MINIMUM_STACK:** Definierar den minsta stackstorleken (i byte). Den används för felkontroll när trådar skapas. Standardvärdet är portspecifikt och finns i **_tx_port.h._**
- **TX_MISRA_ENABLE:** När det här definieras använder ThreadX SMP MISRA C-kompatibla konventioner. Mer information **_ThreadX_MISRA_Compliance.pdf_** i den här informationen.
- **TX_MUTEX_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation om mutexer. Det här alternativet är inte definierat som standard.
- **TX_NO_TIMER** : När det här definieras är ThreadX SMP-timerlogiken helt inaktiverad. Detta är användbart i fall där ThreadX SMP-timerfunktionerna (trådströmsparläge, API-timeouter, tidsslicering och programtimer) inte används.
- **TX_NOT_INTERRUPTABLE:** När det här definieras försöker Inte ThreadX SMP minimera avbrottslåsningstiden. Detta resulterar i snabbare körning men ökar något avbrottslåsningstiden.
- **TX_QUEUE_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation i köer. Det här alternativet är inte definierat som standard.
- **TX_REACTIVATE_INLINE:** När detta definieras utför återaktivering av ThreadX SMP-timers in-line i stället för att använda ett funktionsanrop. Detta förbättrar prestandan men ökar kodstorleken något. Det här alternativet är inte definierat som standard.
- **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation om semaforer. Det här alternativet är inte definierat som standard.
- **TX_THREAD_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation om trådar. Det här alternativet är inte definierat som standard.
- **TX_THREAD_SMP_CORE_MASK: Definierar** bitkartmask för CORE-exkludering. En 4-kärnig miljö har till exempel värdet 0xF för den här definiera.
- **TX_THREAD_SMP_DEBUG_ENABLE** : När det här definieras sparas Felsökningsinformation för ThreadX SMP i en cirkulär buffert.
- **TX_THREAD_SMP_DYNAMIC_CORE_MAX:** När detta definieras aktiverar det dynamiska maximala antalet kärnor som kan justeras vid körning.
- **TX_THREAD_SMP_EQUAL_PRIORITY:** När det här definieras schemalägger ThreadX SMP endast trådar med samma prioritet parallellt. Detta bör definieras innan du skapar ThreadX SMP-biblioteket.
- **TX_THREAD_SMP_INTER_CORE_INTERRUPT:** När det här definieras genererar ThreadX SMP avbrott mellan kärnor.
- **TX_THREAD_SMP_MAX_CORES:** Definierar det maximala antalet kärnor.
- **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT:** När detta definieras kör ThreadX SMP som standard alla trådar och timers endast på core 0 som standard. Programmet kan åsidosätta detta genom att anropa API:erna för att exkludera kärnor. Detta bör definieras innan du skapar ThreadX SMP-biblioteket.
- **TX_THREAD_SMP_WAKEUP_LOGIC:** När det här definieras anropas programmafafa för att aktivera "i"-kärnan. Detta bör definieras innan du tar med **_tx_port.h._**
- **TX_THREAD_SMP_WAKEUP(i)** : Definierar ett programma makro för att väcka kärnvärden "i". Detta bör definieras innan du tar med **_tx_port.h._**
- **TX_TIMER_ENABLE_PERFORMANCE_INFO:** När detta definieras möjliggör insamling av prestandainformation för timers. Det här alternativet är inte definierat som standard.
- **TX_TIMER_PROCESS_IN_ISR:** Eliminerar den interna systemtimertråden för ThreadX SMP när den definieras. Detta resulterar i bättre prestanda för timerhändelser och mindre RAM-krav eftersom timerstacken och kontrollblocket inte längre behövs. Om du använder det här alternativet flyttas dock all förfallotidsbearbetning till timer-ISR-nivån. Det här alternativet är inte definierat som standard.

    > [!NOTE]
    > Att tjänster som tillåts från timers kanske inte tillåts från ISR:er och därför inte tillåts när du använder det här alternativet.

- **TX_TIMER_THREAD_PRIORITY:** Definierar prioriteten för den interna ThreadX SMP-systemtimertråden. Standardvärdet är prioritet 0 – den högsta prioriteten i ThreadX SMP. Standardvärdet definieras i **_tx_port.h._**
- **TX_TIMER_THREAD_STACK_SIZE:** Definierar stackstorleken (i byte) för den interna ThreadX SMP-systemtimertråden. Den här tråden bearbetar alla trådströmsparbegäranden samt alla tidsgränser för tjänstanrop. Dessutom anropas alla rutiner för återanrop av programtimer från den här kontexten. Standardvärdet är portspecifikt och finns i **_tx_port.h._**

## <a name="threadx-smp-version-id"></a>Version-ID för ThreadX SMP

Versions-ID:t för ThreadX SMP finns i filen ***readme_threadx.txt** _ . Den här filen innehåller också en versionshistorik för motsvarande port. Programprogramvara kan hämta ThreadX SMP-versionen genom att undersöka den globala strängen _ *_ _tx_version_id._**