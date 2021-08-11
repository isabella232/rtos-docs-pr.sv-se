---
title: Kapitel 2 – Installation och användning av Azure RTOS ThreadX
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av den högpresterande Azure RTOS ThreadX-kerneln.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a88dc75c3b01e8054f72b3e1475791f064eac0ded02b22ccd18dd46da8c7200a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785047"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>Kapitel 2 – Installation och användning av Azure RTOS ThreadX

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av den högpresterande Azure RTOS ThreadX-kerneln.

## <a name="host-considerations"></a>Värdöverväganden

Inbäddad programvara utvecklas vanligtvis på Windows- eller Linux-värddatorer (Unix). När programmet har kompilerats, länkats och finns på värden laddas det ned till målmaskinvaran för körning.

Vanligtvis görs målnedladdningen inifrån felsökningsprogrammet för utvecklingsverktyget. När nedladdningen är klar ansvarar felsökningsprogrammet för att tillhandahålla målkörningskontroll (go, halt, brytpunkt osv.) samt åtkomst till minne och processorregister.

De flesta felsökningsverktyg kommunicerar med målmaskinvaran via OCD-anslutningar (On-Chip Debug), till exempel JTAG (IEEE 1149.1) och Bakgrundsfelsökningsläge (BDM). Felsökare kommunicerar också med målmaskinvaran via In-Circuit(ICE)-anslutningar. Både OCD- och ICE-anslutningar ger robusta lösningar med minimal intrång på målprogramvaran.

Precis som för resurser som används på värden levereras källkoden för ThreadX i ASCII-format och kräver cirka 1 MB utrymme på värddatorns hårddisk.

## <a name="target-considerations"></a>Målöverväganden

ThreadX kräver mellan 2 KByte och 20 KByte skrivskyddad minne (ROM) på målet. Det krävs även ytterligare 1 till 2 KByte av målets RAM-minne (Random Access Memory) för ThreadX-systemstacken och andra globala datastrukturer.

För timerrelaterade funktioner som time out-time-out för tjänstanrop, tidsslikning och programtimer för att fungera måste den underliggande målmaskinvaran tillhandahålla en periodisk avbrottskälla. Om processorn har den här funktionen används den av ThreadX. Om målprocessorn inte har möjlighet att generera ett regelbundet avbrott måste användarens maskinvara ange det. Installation och konfiguration av timeravbrottet finns vanligtvis i tx_initialize_low_level ***i*** ThreadX-distributionen.

> [!NOTE]
> *ThreadX fungerar fortfarande även om det inte finns någon källa för periodiskt timeravbrott. Ingen av de timerrelaterade tjänsterna fungerar dock.*

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS ThreadX kan hämtas från vår offentliga källkodsdatabas på <https://github.com/azure-rtos/threadx/> .

Följande är en lista över flera viktiga filer på lagringsplatsen.

| Filnamn | Description |
|------------------- | ----------- |
| **tx_api.h**                      | C-rubrikfilen som innehåller alla system är lika med, datastrukturer och tjänstprototyper.                                                             |
| **tx_port.h**                     | C-rubrikfil som innehåller alla utvecklingsverktyget och målspecifika datadefinitioner och strukturer.                                                 |
| **demo_threadx.c**                | C-fil som innehåller ett litet demoprogram.                                                                                                       |
| **tx.a (eller tx.lib)**              | Binär version av ThreadX C-biblioteket som distribueras med *standardpaketet.*                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>*Alla filnamn har gemener. Den här namngivningskonventionen gör det enklare att konvertera kommandona till Linux-utvecklingsplattformar (Unix).*

## <a name="threadx-installation"></a>ThreadX-installation

ThreadX installeras genom att klona GitHub på den lokala datorn. Följande är en vanlig syntax för att skapa en klon av ThreadX-lagringsplatsen på datorn.

```c
    git clone https://github.com/azure-rtos/threadx
```

Du kan också ladda ned en kopia av lagringsplatsen med hjälp av nedladdningsknappen GitHub på huvudsidan.

Du hittar också anvisningar för att skapa ThreadX-biblioteket på startsidan för onlinedatabasen.

> [!NOTE]
> *Programprogramvaran behöver åtkomst till ThreadX-biblioteksfilen (vanligtvis **tx.a** eller **tx.lib**) och C innehåller filerna **_tx_api.h_* _ _*_och tx_port.h_*_. Detta åstadkoms antingen genom att ange lämplig sökväg för utvecklingsverktygen eller genom att kopiera dessa filer till area._

## <a name="using-threadx"></a>Använda ThreadX

Om du vill använda ThreadX måste programkoden innehålla ***tx_api.h** _ under kompileringen och länka till ThreadX-körningsbiblioteket _*_tx.a_*_ (eller _*_tx.lib_**).

Det krävs fyra steg för att skapa ett ThreadX-program.

1. Inkludera filen ***tx_api.h*** i alla programfiler som använder ThreadX-tjänster eller datastrukturer.

1. Skapa standardfunktionen C ***main** _ . Den här funktionen måste så småningom anropa _ *_tx_kernel_enter_** för att starta ThreadX. Programspecifik initiering som inte omfattar ThreadX kan läggas till innan du anger kerneln.

      > [!IMPORTANT]
      > *ThreadX-postfunktionen ***tx_kernel_enter** _ returnerar inte. Se därför till att inte placera några bearbetnings- eller funktionsanrop efter it._

1. Skapa ***tx_application_define*** funktion. Det är här som de första systemresurserna skapas. Exempel på systemresurser är trådar, köer, minnespooler, händelseflaggor, mutexes och semaforer.

1. Kompilera programkällan och länka till ThreadX-körningsbiblioteket ***tx.lib***. Den resulterande avbildningen kan laddas ned till målet och köras!

## <a name="small-example-system"></a>Litet exempelsystem

Det lilla exempelsystemet i bild 1 visar skapandet av en enda tråd med prioritet 3. Tråden körs, ökar en räknare och för viloläger sedan för en klock tick.
Den här processen fortsätter för alltid.

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
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

Även om det här är ett enkelt exempel är det en bra mall för verklig programutveckling.

## <a name="troubleshooting"></a>Felsökning

Varje ThreadX-port levereras med ett demonstrationsprogram. Det är alltid en bra idé att först få igång demonstrationssystemet – antingen på faktisk målmaskinvara eller simulerad miljö.

Om demonstrationssystemet inte körs korrekt är följande några felsökningstips.

1. Fastställ hur mycket av demonstrationen som körs.
1. Öka stackstorlekarna (detta är viktigare i den faktiska programkoden än i demonstrationen).
1. Återskapa ThreadX-biblioteket med TX_ENABLE_STACK_CHECKING definierat. Detta aktiverar den inbyggda ThreadX-stackkontrollen.
1. Kringgå tillfälligt de senaste ändringarna för att se om problemet försvinner eller ändras. Sådan information bör vara användbar för supporttekniker.

Följ de procedurer som beskrivs i[Kundsupportcenter för att](about-this-guide.md#customer-support-center)skicka den information som samlats in från felsökningsstegen.

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ när du skapar ThreadX-biblioteket och programmet med ThreadX. Alternativen nedan kan definieras i programkällan, på kommandoraden eller i filen ***tx_user.h*** include.

> [!IMPORTANT]
> *Alternativ som ***definieras i tx_user.h** _ tillämpas endast om programmet och ThreadX-biblioteket har skapats med _ *TX_INCLUDE_USER_DEFINE_FILE** definierat.*

### <a name="smallest-configuration"></a>Minsta konfiguration

För den minsta kodstorleken bör följande ThreadX-konfigurationsalternativ övervägas (utan alla andra alternativ).

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a>Snabbaste konfiguration

För den snabbaste körningen, samma konfigurationsalternativ som användes för den minsta konfigurationen tidigare, men med dessa alternativ också övervägas.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

[Detaljerade konfigurationsalternativ](#detailed-configuration-options) beskrivs.

### <a name="global-time-source"></a>Global tidskälla

För andra Microsoft Azure RTOS-produkter (FileX, NetX, GUIX, USBX osv.) definierar ThreadX antalet ThreadX-timer tick som representerar en sekund. Andra härleder sina tidskrav baserat på den här konstanten. Som standard är värdet 100, förutsatt ett periodiskt avbrott på 10 ms. Användaren kan åsidosätta det här värdet genom TX_TIMER_TICKS_PER_SECOND definiera med önskat ***värde i tx_port.h*** eller i IDE eller kommandoraden.

### <a name="detailed-configuration-options"></a>Detaljerade konfigurationsalternativ

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

När det här alternativet definieras kan du samla in prestandainformation om bytepooler. Det här alternativet är inte definierat som standard.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

När det här alternativet definieras kan du samla in prestandainformation om bytepooler. Det här alternativet är inte definierat som standard.

**TX_DISABLE_ERROR_CHECKING**

Kringgår grundläggande felkontroll av tjänstsamtal. När den definieras i programkällan inaktiveras all grundläggande parameterfelkontroll. Detta kan förbättra prestandan med upp till 30 % och kan också minska bildstorleken.

> [!NOTE]
> *Det är bara säkert att inaktivera felkontroll om programmet absolut kan garantera att alla indataparametrar alltid är giltiga under alla omständigheter, inklusive indataparametrar som härletts från externa indata. Om ogiltiga indata har angetts till API:et med felkontroll inaktiverat, är det resulterande beteendet odefinierat och kan resultera i minnesfel eller systemkrasch.*

> [!NOTE]
> *ThreadX API-returvärden som inte påverkas av inaktivering av felkontroll visas i fetstil i avsnittet "Returvärden" i varje API-beskrivning i kapitel 4. Returvärdena för icke-boliska värden annulleras om felkontrollen inaktiveras med hjälp TX_DISABLE_ERROR_CHECKING alternativet.*

**TX_DISABLE_NOTIFY_CALLBACKS**

När detta definieras inaktiveras återanrop av avanrop för olika ThreadX-objekt. Om du använder det här alternativet minskar kodstorleken något och prestandan förbättras. Det här alternativet är inte definierat som standard.

**TX_DISABLE_PREEMPTION_THRESHOLD**

När funktionen preemption-threshold definieras minskar den kodstorleken något och förbättrar prestandan. Naturligtvis är funktionerna för tröskelvärden för avspärrning inte längre tillgängliga. Det här alternativet är inte definierat som standard.

**TX_DISABLE_REDUNDANT_CLEARING**

När du definierar tar bort logiken för att initiera ThreadX globala C-datastrukturer till noll. Detta bör endast användas om kompilatorns initieringskod anger alla o initialiserade globala C-data till noll. Om du använder det här alternativet minskar kodstorleken något och prestandan förbättras under initieringen. Det här alternativet är inte definierat som standard.

**TX_DISABLE_STACK_FILLING**

När det här definieras inaktiverar 0xEF värdet i varje byte i varje trådstack när den skapas. Det här alternativet är inte definierat som standard.

**TX_ENABLE_EVENT_TRACE**

När Det här definieras aktiverar ThreadX händelseinsamlingskoden för att skapa en TraceX-spårningsbuffert.

**TX_ENABLE_STACK_CHECKING**

När det här definieras aktiverar threadx-körningsstackkontroll, vilket innefattar analys av hur mycket stack som har använts och undersökning av datamönstret "stängsel" före och efter stackområdet. Om ett stackfel identifieras anropas felhanteraren för den registrerade programstacken. Det här alternativet resulterar i något högre omkostnader och kodstorlek. Mer ***information finns i tx_thread_stack_error_notify*** API-funktionen. Det här alternativet är inte definierat som standard.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

När detta definieras möjliggör insamling av prestandainformation om händelseflaggor grupper. Det här alternativet är inte definierat som standard.

**TX_INLINE_THREAD_RESUME_SUSPEND**

När Det här definieras förbättrar ThreadX ***tx_thread_resume** _ och _ *_tx_thread_suspend_** API-anrop via in-line-kod. Detta ökar kodstorleken men förbättrar prestandan för dessa två API-anrop.

**TX_MAX_PRIORITIES**

Definierar prioritetsnivåer för ThreadX. Juridiska värden sträcker sig från 32 till 1024 (inklusive) och måste vara jämnt delbara med 32.  Genom att öka antalet prioritetsnivåer som stöds ökar RAM-användningen med 128 byte för varje grupp med 32 prioriteringar. Det finns dock bara en försumbar effekt på prestanda. Som standard är det här värdet inställt på 32 prioritetsnivåer.

**TX_MINIMUM_STACK**

Definierar den minsta stackstorleken (i byte). Den används för felkontroll när trådar skapas. Standardvärdet är portspecifikt och finns i ***tx_port.h***.

**TX_MISRA_ENABLE**

När threadX definieras använder de konventioner som följer MISRA C. Se  ***ThreadX_MISRA_Compliance.pdf*** för mer information.

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

När detta definieras möjliggör insamling av prestandainformation om mutexer. Det här alternativet är inte definierat som standard.

**TX_NO_TIMER**

När det här definieras är ThreadX-timerlogiken helt inaktiverad. Detta är användbart i fall där ThreadX-timerfunktionerna (trådströmsparläge, API-timeouter, tidsslicering och programtimer) inte används. Om **TX_NO_TIMER** har angetts måste **TX_TIMER_PROCESS_IN_ISR** också definieras.

**TX_NOT_INTERRUPTABLE**

När det här definieras försöker ThreadX inte minimera avbrottsutlåsningstiden. Detta resulterar i snabbare körning men ökar något avbrottslåsningstiden.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

När detta definieras möjliggör insamling av prestandainformation i köer. Det här alternativet är inte definierat som standard.

**TX_REACTIVATE_INLINE**

När detta definieras utför återaktivering av ThreadX-timers infogade i stället för att använda ett funktionsanrop. Detta förbättrar prestandan men ökar kodstorleken något. Det här alternativet är inte definierat som standard.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

När detta definieras möjliggör insamling av prestandainformation på semaforer. Det här alternativet är inte definierat som standard.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

När detta definieras möjliggör insamling av prestandainformation om trådar. Det här alternativet är inte definierat som standard.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

När detta definieras möjliggör insamling av prestandainformation på timers. Det här alternativet är inte definierat som standard.

**TX_TIMER_PROCESS_IN_ISR**

När detta definieras eliminerar den interna systemtimertråden för ThreadX. Detta resulterar i bättre prestanda för timerhändelser och mindre RAM-krav eftersom timerstacken och kontrollblocket inte längre behövs. Om du använder det här alternativet flyttas dock all förfallotidsbearbetning till timer-ISR-nivån. Det här alternativet är inte definierat som standard.

> [!NOTE]
> *Tjänster som tillåts från timers kanske inte tillåts från ISR:er och därför kanske inte tillåts när du använder det här alternativet.*

**TX_TIMER_THREAD_PRIORITY**

Definierar prioriteten för den interna ThreadX-systemtimertråden. Standardvärdet är prioritet 0 – den högsta prioriteten i ThreadX. Standardvärdet definieras i ***tx_port.h***.

**TX_TIMER_THREAD_STACK_SIZE**

Definierar stackstorleken (i byte) för den interna ThreadX-systemtimertråden. Den här tråden bearbetar alla trådströmsparbegäranden samt alla tidsgränser för tjänstanrop. Dessutom anropas alla rutiner för återanrop av programtimer från den här kontexten. Standardvärdet är portspecifikt och finns i ***tx_port.h***.

## <a name="threadx-version-id"></a>Version-ID för ThreadX

Programmeraren kan hämta ThreadX-versionen från undersökningen av filen ***tx_port.h** _. Dessutom innehåller den här filen även en versionshistorik för motsvarande port. Programprogramvara kan hämta ThreadX-versionen genom att undersöka den globala strängen _*_tx_version_id**.
