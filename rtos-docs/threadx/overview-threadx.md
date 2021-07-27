---
title: Förstå Azure RTOS ThreadX
description: Läs mer om Azure ThreadX, ett avancerat realtidsoperativsystemet (RTOS) som utformats särskilt för djupt inbäddade program.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 8c0bec2bb3b699b3a8d39d85eb322f3bbd95515a
ms.sourcegitcommit: 8b03df42920bdd544fb4195ab818043f6c71969e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2021
ms.locfileid: "114436754"
---
# <a name="overview-of-azure-rtos-threadx"></a>Översikt över Azure RTOS ThreadX

Azure RTOS ThreadX är Microsofts avancerade industriella Real-Time RTOS (Operating System). Den är särskilt utformad för djupt inbäddade, realtidsbaserade och IoT-program. Azure RTOS ThreadX tillhandahåller avancerad schemaläggning, kommunikation, synkronisering, timer, minneshantering och avbrottshantering. Dessutom har Azure RTOS ThreadX många avancerade funktioner: inklusive dess picokernel™-arkitektur, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics och system event tracing. I kombination med den förstklassiga användarvänligheten är Azure RTOS ThreadX det perfekta valet för de mest krävande inbäddade programmen. Azure RTOS ThreadX har miljarder distributioner över en mängd olika produkter, inklusive konsumentenheter, medicinsk elektronik och industriell kontrollutrustning.

## <a name="threadx-footprint"></a>ThreadX-fotavtryck

Azure RTOS ThreadX har ett mycket litet 2 KB-instruktionsområde och 1 kB RAM-minimalt fotavtryck. Den här lilla storleken beror till stor del på dess arkitektur för picokernel utan lager och automatisk skalning. Automatisk skalning innebär att endast de tjänster (och stödinfrastruktur) som används av programmet ingår i den slutliga avbildningen vid länktiden.

Här är några vanliga Azure RTOS för ThreadX-storlek.

|Azure RTOS ThreadX-tjänsten  |Normal storlek i byte  |
|---------|---------|
|Core Services (Kräv) |2 000  |
|Queue Services  |900  |
|Event Flag Services  |900  |
|Semaphore Services  |450  |
|Mutex-tjänster  |1 200  |
|Block Memory Services  |550  |
|Byte Memory Services  |900  |

## <a name="threadx-execution-speed"></a>Körningshastighet för ThreadX

Azure RTOS ThreadX uppnår en submicmiccond-kontextväxel på de flesta populära processorer och är snabbare totalt sett än andra kommersiella RTOS.er. Förutom att vara snabb är Azure RTOS ThreadX också mycket deterministiskt. Det ger samma snabba prestanda oavsett om det finns 200 trådar redo eller bara en.

Här är några vanliga prestandaegenskaper för Azure RTOS ThreadX:

* Snabb start: Azure RTOS ThreadX startar i färre än 120 cykler.
* Valfri borttagning av grundläggande felkontroll: Grundläggande Azure RTOS ThreadX-felkontroll kan hoppas över vid kompileringen. Detta kan vara användbart när programkoden har verifierats och inte längre kräver felkontroll för varje parameter. Felkontroll överhoppning kan göras på en kompileringsenhet i stället för i hela systemet.
* Picokernel-design: Tjänsterna är inte skiktade på varandra, vilket eliminerar onödigt arbete med funktionsanrop.
* Optimerad avbrottsbearbetning: Endast scratch-register sparas/återställs vid ISR-in- och utpassering, om inte avinption krävs.
* Optimerad API-bearbetning:

    |Azure RTOS ThreadX-tjänsten  |Servicetid i mikrosekunder*  |
    |---------|---------|
    |Tråd pausa  |0,6  |
    |Tråd-ÅTERUPPTA  |0,6  |
    |Skicka i kö  |0.3  |
    |Kö ta emot  |0.3  |
    |Hämta Semaphore  |0,2  |
    |Placera Semaphore  |0,2  |
    |Kontextväxel  |0,4  |
    |Avbrottssvar  |0.0 – 0.6  |

    **Prestandasiffror som baseras på en typisk processor som körs på 200 MHz.*

## <a name="advanced-technology"></a>Avancerad teknik

Azure RTOS ThreadX är viktigt för schemaläggning före avbokningströskel. Den här funktionen är unik för Azure RTOS ThreadX och har varit föremål för omfattande akademisk forskning. Du kan lära dig mer i dokumentet [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), av Yun Wang (Miaia University) och Manas Saksena (University of Dallas).

Viktiga funktioner i Azure RTOS ThreadX:

* Kompletta och omfattande multitasking-anläggningar
  * Trådar, programtimerar, meddelandeköer, räkna semaforer, mutexer, händelseflaggor, block- och byteminnespooler
* Priority-Based förebyggande schemaläggning
* Prioritetsflexibilitet – upp till 1 024 prioritetsnivåer
* Schemaläggning av schemaläggning
* Preemption-Threshold – Unikt för Azure RTOS ThreadX, hjälper till att minska kontextväxlar och bidra till att garantera schedulability (per akademisk forskning)
* Minnesskydd via Azure RTOS ThreadX-MODULER
* Fullständigt deterministisk
* Händelsespårning – Samla in de senaste system-/programhändelserna 
* Händelsekedja – Registrera en programspecifik "meddela"-återanropsfunktion för varje Azure RTOS ThreadX-kommunikations- eller synkroniseringsobjekt
* Azure RTOS ThreadX-MODULER med valfritt minnesskydd
* Run-Time prestandamått
  * Antal återantaganden av trådar
  * Antal trådavstängningar
  * Antal förinda förinta trådar
  * Antal asynkrona trådavbrott som är fördumningar
  * Antal inversioner av trådprioritet
  * Antal trådrelegater
* Execution Profile Kit (EPK)
* Separat avbrottsstack
* Run-Time Stack-analys
* Optimerad timeravbrottsbearbetning

## <a name="multicore-support-amp--smp"></a>Stöd för flera kärnor (AMP & SMP)

Standard Azure RTOS ThreadX används ofta i asymmetrisk flerbearbetning (AMP), där en separat kopia av Azure RTOS ThreadX och programmet (eller Linux) körs på varje kärna och kommunicerar med varandra via delat minne eller en kommunikationsmekanism mellan processorer som OpenAMP (Azure RTOS ThreadX stöder OpenAMP).

I miljöer där inläsningsprocessorer är mycket dynamiska är Azure RTOS ThreadX Symmetric Multiprocessing (SMP) tillgängligt för följande processorfamiljer:

* ARM-Cortex-Ax
* ARM-Cortex-Rx
* ARM Cortex-A5x 64-bitars
* MIPS 34 K, 1004 K och interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP utför dynamisk belastningsutjämning mellan *n processorer.* Det gör att alla Azure RTOS ThreadX-resurser (köer, semaforer, händelseflaggor, minnespooler osv.) kan nås av alla trådar på valfri kärna. Azure RTOS ThreadX SMP aktiverar det fullständiga Azure RTOS ThreadX-API:et på alla kärnor och introducerar följande nya API:er som gäller för SMP-åtgärder:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Minnesskydd via Azure RTOS ThreadX-moduler

Med en tilläggsprodukt som kallas Azure RTOS ThreadX-moduler kan en eller flera programtrådar paketeras i en "modul" som kan läsas in dynamiskt och köras (eller köras på plats) på målet.

Moduler möjliggör fältuppgradering, felkorrigeringar och programpartitionering så att stora program endast kan uppta det minne som behövs av aktiva trådar.

Moduler har också ett separat adressutrymme från Azure RTOS ThreadX. Detta gör Azure RTOS ThreadX kan placera minnesskydd (via MPU eller MMU) runt modulen så att oavsiktlig åtkomst utanför modulen inte kan skada någon annan programvarukomponent.

## <a name="misra-compliant"></a>MISRA-kompatibel

Azure RTOS ThreadX och Azure RTOS ThreadX SMP-källkoden är KOMPATIBEL MED MISRA-C: 2004 och MISRA C:2012. MISRA C är en uppsättning programmeringsriktlinjer för kritiska system som använder programmeringsspråket C. De ursprungliga riktlinjerna för MISRA C var främst avsedda för fordonstillämpningar. MEN MISRA C är nu allmänt känt som tillämpligt för alla säkerhetskritiska program. Azure RTOS ThreadX är kompatibel med alla obligatoriska och obligatoriska regler i MISRA-C: 2004 och MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Felcertifiering":::

## <a name="supports-most-popular-tools"></a>Stöder de populäraste verktygen

Azure RTOS ThreadX stöder de flesta populära inbäddade utvecklingsverktyg, inklusive IAR:s Embedded Workbench, som även har den mest omfattande Azure RTOS ThreadX-kernelmedvetenhet. Andra verktygsintegrering inkluderar GNU (GCC), ARM DS-5/uVision®, Green Graf MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauter ultimate TRACE32®, TI Code-Composer Studio, CrossCore och alla analoga enheter.

## <a name="adaptation-layer-for-threadx"></a>Anpassningslager för ThreadX

Du kan underlätta problem med programmigrering [](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) Azure RTOS genom att använda ThreadX-anpassningslager för olika äldre RTOS-API:er (FreeRTOS, POSIX, OSEK osv.)

> [!div class="nextstepaction"]
> [Introduktion till Azure RTOS ThreadX](chapter1.md)