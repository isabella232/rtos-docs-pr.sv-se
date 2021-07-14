---
title: Förstå Azure RTOS ThreadX
description: Azure ThreadX är ett avancerat realtidsoperativsystemet (RTOS) som utformats specifikt för djupt inbäddade program.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 938619170ef51d354fa970134328c17407ae846a
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754870"
---
# <a name="overview-of-azure-rtos-threadx"></a>Översikt över Azure RTOS ThreadX

Azure RTOS ThreadX är Microsofts avancerade branschklass Real-Time RTOS (Operating System) som utformats särskilt för djupt inbäddade, realtidsbaserade och IoT-program. Azure RTOS ThreadX tillhandahåller avancerad schemaläggning, kommunikation, synkronisering, timer, minneshantering och avbrottshantering. Dessutom har Azure RTOS ThreadX många avancerade funktioner, inklusive dess picokernel™-arkitektur, preemption-threshold™ scheduling, event-chaining, ™ execution profiling, performance metrics och system event tracing. I kombination med den förstklassiga användarvänligheten är Azure RTOS ThreadX det perfekta valet för de mest krävande inbäddade programmen. Från och med 2017 har Azure RTOS ThreadX över 6,2 miljarder distributioner i en mängd olika produkter, inklusive konsumentenheter, medicinsk elektronik och industriell kontrollutrustning.

## <a name="api-protocols"></a>API-protokoll

### <a name="azure-rtos-threadx-services"></a>Azure RTOS ThreadX Services

* Skapa dynamiska trådar
* Inga gränser för antalet trådar
* Huvudtråd-API:er är:
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* Ytterligare information och prestanda-API:er

### <a name="message-queues"></a>Meddelandeköer

* Skapa dynamisk kö
* Inga gränser för antalet köer
* Meddelanden som kopieras efter värde (eller som referens via pekare)
* Meddelandestorlekar från 1 till 16 32-bitars ord
* Valfri tråduppstängning är tom och full
* Valfri tidsgräns vid all låsning
* API:er för meddelandeköer är:
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* Ytterligare information och prestanda-API:er

### <a name="counting-semaphores"></a>Räkna semaforer

* Dynamiskt skapande av semaphore
* Inga gränser för antalet semaforer
* Semaforer för 32-bitars räkning (0 till 4 294 967 295)
* Stöd för konsumentproducent eller resursskydd
* Valfri trådavstängning när semaphore inte är tillgänglig
* Valfri tidsgräns vid all låsning
* De viktigaste semafor-API:erna är:
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* Ytterligare information och prestanda-API:er

### <a name="mutexes"></a>Mutexes

* Dynamiskt skapande av mutex
* Inga begränsningar för antalet mutexer
* Kapslat resursskydd stöds
* Valfritt prioritetsarv som stöds
* Valfri tråduppstängning när mutex inte är tillgängligt
* Valfri tidsgräns vid all låsning
* De viktigaste mutex-API:erna är:
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* Ytterligare information och prestanda-API:er

### <a name="event-flags"></a>Händelseflaggor

* Skapa dynamisk händelseflaggan
* Inga gränser för antalet händelseflaggasgrupper
* Synkronisering av en tråd eller flera trådar
* Atomic get and clear stöds
* Valfri multitrådsavstängning vid AND/OR-uppsättning händelser
* Valfri tidsgräns vid all låsning
* Huvudhändelseflaggans API:er är:
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* Ytterligare information och prestanda-API:er

### <a name="block-memory-pools"></a>Blockminnespooler

* Skapa dynamisk blockpool
* Inga begränsningar för antalet blockpooler
* Inga gränser för storleken på block med fast storlek eller storleken på poolen
* Snabbaste möjliga minnesallokering/avtalsplats
* Valfri tråduppstängning på tom pool
* Valfri tidsgräns vid all låsning
* HUVUD-API:er för blockpooler är:
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* Ytterligare information och prestanda-API:er

### <a name="byte-memory-pools"></a>Byteminnespooler

* Skapa dynamisk bytepool
* Inga gränser för antalet bytepooler
* Inga gränser för bytepoolens storlek
* Mest flexibel minnesallokering/avallokering med variabel längd
* Allokeringsstorlek som stöds
* Valfri tråduppstängning i tom pool
* Valfri tidsgräns för all låsning
* API:er för huvudbytepooler är:
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* Ytterligare information och prestanda-API:er

### <a name="application-timers"></a>Programtimerar

* Skapa dynamisk timer
* Inga begränsningar för antalet timers
* Periodiska timers eller one-shot-timers som stöds
* Periodiska timers kan ha olika initiala förfallovärden
* Ingen sökning efter timeraktivering eller inaktivering
* Alla timers som körs från ett avbrott i maskinvarutimern
* Huvudtimerns API:er är:
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* Ytterligare information och prestanda-API:er

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure RTOS ThreadX Core Scheduler

* Minimalt RAM-fotavtryck på 2 kB FLASH,1 kB
* Snabb kontextsekonväxel under mikrosekunder
* Helt deterministiskt oavsett antalet trådar
* Prioritetsbaserad, helt förebyggande schemaläggning
* 32 standardprioritetsnivåer, valfritt upp till 1 024 nivåer
* Schemaläggning av schemaläggning inom prioritetsnivå (FIFO)
* Teknik för tröskelvärde för avbrott
* Valfria timertjänster, inklusive:
  * Valfri tidssegment per tråd
  * Valfri tidsgräns för all blockering
  * API:er kräver avbrott i maskinvarutimern
* Körningsprofilering
* Spårning på systemnivå
* Säkerhet certifierad enligt många standarder

## <a name="threadx-footprint"></a>ThreadX-fotavtryck

Azure RTOS ThreadX kräver ett mycket litet 2 KB-instruktionsområde och 1 kB RAM-minne för det minimala fotavtrycket. Detta beror till stor del på dess picokernel utan lager™ arkitektur och automatisk skalning. Automatisk skalning innebär att endast de tjänster (och stödinfrastruktur) som används av programmet ingår i den slutliga avbildningen vid länktiden.

Här är några vanliga Azure RTOS för ThreadX-storlek.

|Azure RTOS ThreadX-tjänsten  |Normal storlek i byte  |
|---------|---------|
|Kärntjänster (Kräv) |2 000  |
|Queue Services  |900  |
|Event Flag Services  |900  |
|Semaphore Services  |450  |
|Mutex-tjänster  |1 200  |
|Block Memory Services  |550  |
|Byte Memory Services  |900  |

## <a name="threadx-execution-speed"></a>Körningshastighet för ThreadX

Azure RTOS ThreadX uppnår en kontextväxel på under mikrosekunder på de flesta populära processorer och är betydligt snabbare totalt än andra kommersiella RTOS:er. Förutom att vara snabb är Azure RTOS ThreadX också mycket deterministiskt. Det ger samma snabba prestanda oavsett om det finns 200 trådar redo eller bara en.

Här är några vanliga prestandaegenskaper för Azure RTOS ThreadX:

* Snabb start: Azure RTOS ThreadX startar på mindre än 120 cykler.
* Valfri borttagning av grundläggande felkontroll: Grundläggande Azure RTOS ThreadX-felkontroll kan hoppas över vid kompileringen. Detta kan vara användbart när programkoden har verifierats och inte längre kräver felkontroll på varje parameter. Observera att detta kan göras på en kompileringsenhet i stället för i hela systemet.
* Picokernel™ Design: Tjänsterna är inte skiktade på varandra, vilket eliminerar onödigt arbete med funktionsanrop.
* *Optimerad avbrottsbearbetning: Endast tillfälligt register sparas/återställs vid ISR-inmatning/-avslut, om inte avslut krävs.
* Optimerad API-bearbetning:

    |Azure RTOS ThreadX-tjänsten  |Servicetid i mikrosekunder*  |
    |---------|---------|
    |Tråd pausa  |0,6  |
    |Tråd-RESUME  |0,6  |
    |Skicka kö  |0.3  |
    |Kö ta emot  |0.3  |
    |Hämta Semaphore  |0,2  |
    |Placera Semaphore  |0,2  |
    |Kontextväxel  |0,4  |
    |Avbrottssvar  |0.0 – 0.6  |

    **Prestandasiffror baserade på en typisk processor som körs på 200 MHz.*

## <a name="advanced-technology"></a>Avancerad teknik

Azure RTOS ThreadX är avancerad teknik vars viktigaste funktion är schemaläggning före avbrottströskel. Den här funktionen är unik Azure RTOS ThreadX och har varit föremål för omfattande akademisk forskning. Se till exempel [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), av Yun Wang, Juliaia University och Manas Saksena, University of Dallas.

Överväg funktionerna i Azure RTOS ThreadX.

* Kompletta och omfattande multitasking-anläggningar
  * Trådar, programtimerar, meddelandeköer, räkna semaforer, mutexer, händelseflaggor, block- och byteminnespooler
* Priority-Based förebyggande schemaläggning
* Prioritetsflexibilitet – upp till 1 024 prioritetsnivåer
* Schemaläggning av schemaläggning
* Preemption-Threshold™ – unikt för Azure RTOS ThreadX, hjälper till att minska kontextbyten och bidra till att garantera schedulability (per akademisk forskning)
* Minnesskydd via Azure RTOS ThreadX-MODULER
* Helt deterministisk
* Händelsespårning – samla in de senaste system-/programhändelserna 
* Event Chaining™ – Registrera en programspecifik "meddela"-återanropsfunktion för varje Azure RTOS ThreadX-kommunikations- eller synkroniseringsobjekt
* Azure RTOS ThreadX-MODULER med valfritt minnesskydd
* Run-Time prestandamått
  * Antal trådantaganden
  * Antal tråduppstängningar
  * Antal begärda tråd-preemptions
  * Antal asynkrona trådavbrottsavbrott
  * Antal trådprioritetsinversioner
  * Antal trådrelineringar
* Execution Profile Kit (EPK)
* Separat avbrottsstack
* Run-Time Stack-analys
* Optimerad avbrottsbearbetning av timer

## <a name="multicore-support-amp--smp"></a>Stöd för flera kärnor (AMP & SMP)

Standard Azure RTOS ThreadX används ofta på ett asymmetriskt sätt med flera processer (AMP), där en separat kopia av Azure RTOS ThreadX och programmet (eller Linux) körs på varje kärna och kommunicerar med varandra via delat minne eller en kommunikationsmekanism mellan processorer som OpenAMP (Azure RTOS ThreadX stöder OpenAMP). Det här är den mest typiska konfigurationen med Azure RTOS ThreadX och kan vara det mest effektiva om programmet effektivt kan läsa in processorerna.

För miljöer där inläsningen av processorerna är mycket dynamisk Azure RTOS ThreadX Symetric Multiprocessing (SMP) tillgänglig för följande processorfamiljer:

* ARM-Cortex-Ax
* ARM-Cortex-Rx
* ARM Cortex-A5x 64-bitars
* MIPS 34K, 1004K och interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP utför dynamisk belastningsutjämning över *n* processorer och tillåter att alla Azure RTOS ThreadX-resurser (köer, semaforer, händelseflaggor, minnespooler osv.) kan nås av alla trådar på valfri kärna. Azure RTOS ThreadX SMP aktiverar det fullständiga Azure RTOS ThreadX-API:et på alla kärnor och introducerar följande nya API:er som gäller för SMP-åtgärder:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Minnesskydd via Azure RTOS ThreadX-moduler

Med en tilläggsprodukt som kallas Azure RTOS ThreadX MODULES kan en eller flera programtrådar paketeras i en "Modul" som kan läsas in dynamiskt och köras (eller köras på plats) på målet.

Moduler möjliggör fältuppgradering, felkorrigeringar och programpartitionering så att stora program endast kan uppta det minne som behövs av aktiva trådar.

Moduler har också ett helt separat adressutrymme från Azure RTOS ThreadX. Detta gör Azure RTOS ThreadX kan placera minnesskydd (via MPU eller MMU) runt modulen så att oavsiktlig åtkomst utanför modulen inte kan skada någon annan programvarukomponent.

## <a name="misra-compliant"></a>MISRA-kompatibel

Azure RTOS ThreadX och Azure RTOS ThreadX SMP-källkoden är kompatibel med MISRA-C:2004 och MISRA C:2012. MISRA C är en uppsättning programmeringsriktlinjer för kritiska system som använder programmeringsspråket C. De ursprungliga riktlinjerna för MISRA C var främst avsedda för fordonstillämpningar. MEN MISRA C är nu allmänt känt som tillämpligt för alla säkerhetskritiska program. Azure RTOS ThreadX är kompatibel med alla obligatoriska och obligatoriska regler för MISRA-C:2004 och MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Felcertifiering":::

## <a name="supports-most-popular-tools"></a>Stöder de populäraste verktygen

Azure RTOS ThreadX har stöd för de flesta populära inbäddade utvecklingsverktyg, inklusive IAR:s Embedded Workbench™, som även har den mest omfattande Azure RTOS ThreadX-kernelmedvetenhet. Ytterligare verktygsintegrering omfattar GNU (GCC), ARM DS-5/uVision®, Green Universal MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterlt TRACE32®, TI Code-Composer Studio, CrossCore och alla analoga enheter.

## <a name="adaptation-layer-for-threadx"></a>Anpassningslager för ThreadX

Azure RTOS ThreadX är ett avancerat realtidsoperativsystem (RTOS) som är särskilt utformat för djupt inbäddade program. För att underlätta programmigrering till Auzre RTOS tillhandahåller ThreadX [anpassningslager](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) för olika äldre RTOS-API:er (FreeRTOS, POSIX, OSEK osv.)
