---
title: Kapitel 6 – Azure återställnings tider ThreadX trace Events
description: I det här kapitlet beskrivs Azure återställnings tider ThreadX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827555"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>Kapitel 6 – Azure återställnings tider ThreadX trace Events

I det här kapitlet beskrivs Azure återställnings tider ThreadX-händelser. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

Följande är en lista över ThreadX-händelser som visas av TraceX:

| **Ikon**                         | **Innebörd** |
| -------------------------------- | ------------------------------------- |
| ![Aktiverings ikon för intern tråd](./media/user-guide/tx-events/image1.png)    | Återuppta intern tråd  |
| ![Inaktivera ikon för intern tråd](./media/user-guide/tx-events/image2.png)    | Inaktive ring av intern tråd |
| ![Ikon för att avbryta tjänstens rutin retur](./media/user-guide/tx-events/image3.png)    | Avbrotts service rutin (ISR)-retur |
| ![Avbrotts ikon för tjänst rutin](./media/user-guide/tx-events/image4.png)    | Avbryta service rutin (ISR)-avsluta  |
| ![Intern Time-slice-ikon](./media/user-guide/tx-events/image5.png)    | Intern tid-sektor |
| ![Kör ikon](./media/user-guide/tx-events/image6.png)    | Körs |
| ![Ikonen för att blockera pool tilldelning](./media/user-guide/tx-events/image7.png)    | **Blockera allokering av pool** (*tx_block_allocate*)  |
| ![Skapa ikon för att blockera pool](./media/user-guide/tx-events/image8.png)    | **Blockera skapande av pool** (*tx_block_pool_create*) |
| ![Ta bort ikon för borttagning av pool](./media/user-guide/tx-events/image9.png)    | **Blockera borttagning av pool** (*tx_block_pool_delete*) |
| ![Hämta ikon för Hämta pool information](./media/user-guide/tx-events/image10.png)    | **Blockera pool information get** (*tx_block_pool_info_get*) |
| ![Blockera prestanda information för pool Hämta con](./media/user-guide/tx-events/image11.png)    | **Blockera prestanda information för pool Hämta** (*tx_block_pool_performance_info_get*) |
| ![Hämta ikon för Hämta pool system prestanda information](./media/user-guide/tx-events/image12.png)    | **Blockera pool system prestanda information get** (*tx_block_pool_performance_system_info_get*) |
| ![Prioritets ikon för att blockera pool](./media/user-guide/tx-events/image13.png)    | **Blockera poolens prioritet** (*tx_block_pool_prioritize*) |
| ![Ikonen blockera att släppa till poolen](./media/user-guide/tx-events/image14.png)    | **Blockera version till pool** (*tx_block_release*) |
| ![Ikon för allokera minne för byte pool](./media/user-guide/tx-events/image15.png)    | **Byte pool allokera minne** (*tx_byte_allocate*) |
| ![Ikon för att skapa byte pool](./media/user-guide/tx-events/image16.png)    | **Skapa byte-pool** (*tx_byte_pool_create*) |
| ![Borttagnings ikon för byte pool](./media/user-guide/tx-events/image17.png)    | **Borttagning av byte pool** (*tx_byte_pool_delete*) |
| ![Ikon för hämta information om byte pool](./media/user-guide/tx-events/image18.png)    | **Information om byte pool get** (*tx_byte_pool_info_get*) |
| ![Ikon för hämta prestanda information för byte-pool](./media/user-guide/tx-events/image19.png)    | **Hämta prestanda information för byte-pool** (*tx_byte_pool_performance_info_get*) |
| ![Ikon för Hämta byte i byte pool system prestanda information](./media/user-guide/tx-events/image20.png)    | **Hämta information om byte pool system prestanda information** (*tx_byte_pool_performance_system_info_get*) |
| ![* Prioritets ikon för byte pool](./media/user-guide/tx-events/image21.png)    | **Prioritering av byte-pool** (*tx_byte_pool_prioritize*) |
| ![Ikon för att frigöra byte minne](./media/user-guide/tx-events/image22.png)    | **Byte minnes version till pool** (*tx_byte_release*) |
| ![Ikonen Skapa händelse flaggor](./media/user-guide/tx-events/image23.png)    | **Skapa händelse flaggor** (*tx_event_flags_create*) |
| ![Borttagnings ikon för händelse flaggor](./media/user-guide/tx-events/image24.png)    | **Ta bort händelse flaggor** (*tx_event_flags_delete*) |
| ![Ikonen Hämta händelse flaggor](./media/user-guide/tx-events/image25.png)    | **Händelse flaggor Hämta** (*tx_event_flags_get*) |
| ![Ikonen Hämta information om händelse flaggor](./media/user-guide/tx-events/image26.png)    | **Händelse flaggor information get** (*tx_event_flags_info_get*) |
| ![Händelse flaggor prestanda information Hämta ikon](./media/user-guide/tx-events/image27.png)    | **Händelse flaggor prestanda information get** (*tx_event_flags_performance_info_get*) |
| ![Händelse flaggor system prestanda information Hämta ikon](./media/user-guide/tx-events/image28.png)    | **Händelse flaggor system prestanda information get** (*tx_event_flags_performance_system_info_get*) |
| ![Ikonen händelse flaggor uppsättning](./media/user-guide/tx-events/image29.png)    | **Angivna händelse flaggor** (*tx_event_flags_set*) |
| ![Händelse flaggor ange aviserings ikon](./media/user-guide/tx-events/image30.png)    | **Meddelande om inställd händelse flaggor** (*tx_event_flags_set_notify*) |
| ![Avbryt aktivering/inaktivera ikon](./media/user-guide/tx-events/image31.png)    | **Avbryt aktivering/inaktive ring** (*tx_interrupt_control*) |
| ![Ikon för mutex-skapande](./media/user-guide/tx-events/image32.png)    | **Mutex-skapande** (*tx_mutex_create*) |
| ![Ikon för mutex-borttagning](./media/user-guide/tx-events/image33.png)    | **Mutex-borttagning** (*tx_mutex_delete*) |
| ![Ikon för att hämta mutex](./media/user-guide/tx-events/image34.png)    | **Mutex get** (*tx_mutex_get*) |
| ![Get-ikon för mutex information](./media/user-guide/tx-events/image35.png)    | **Mutex information get** (*tx_mutex_info_get*) |
| ![Ikon för hämta information om mutex-prestanda](./media/user-guide/tx-events/image36.png)    | **Information om mutex-prestanda Hämta** (*tx_mutex_performance_info_get*) |
| ![Ikon för att hämta mutex-system prestanda information](./media/user-guide/tx-events/image37.png)    | **Mutex system prestanda information get** (*tx_mutex_performance_system_info_get*) |
| ![Ikon för mutex-prioritet](./media/user-guide/tx-events/image38.png)    | **Mutex-prioritering** (*tx_mutex_prioritize*) |
| ![Ikon för mutex-placering](./media/user-guide/tx-events/image39.png)    | **Mutex-placering** (*tx_mutex_put*) |
| ![Ikon för att skapa kö](./media/user-guide/tx-events/image40.png)    | **Skapa kö** (*tx_queue_create*) |
| ![Borttagnings ikon för kö](./media/user-guide/tx-events/image41.png)    | **Köa borttagning** (*tx_queue_delete*) |
| ![Ikon för köa tömning](./media/user-guide/tx-events/image42.png)    | **Köa rensning** (*tx_queue_flush*) |
| ![Ikon för att skicka kön direkt](./media/user-guide/tx-events/image43.png)    | **Kö-sändning** (*tx_queue_front_send*) |
| ![Hämta ikon för köa information](./media/user-guide/tx-events/image44.png)    | **Köa information get** (*tx_queue_info_get*) |
| ![Hämta ikon för köns prestanda information](./media/user-guide/tx-events/image45.png)    | **Hämta prestanda information för kö** (*tx_queue_performance_info_get*) |
| ![Hämta ikon för prestanda information för Queue system](./media/user-guide/tx-events/image46.png)    | **Hämta information om köa system prestanda information** (*tx_queue_performance_system_info_get*) |
| ![Ikon för köa prioritet](./media/user-guide/tx-events/image47.png)    | **Prioritet för kön** (*tx_queue_prioritize*) |
| ![Ikon för mottagnings meddelande i kö](./media/user-guide/tx-events/image48.png)    | **Mottagnings meddelande i kö** (*tx_queue_receive*) |
| ![Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image49.png)    | **Köa sändnings meddelande** (*tx_queue_send*) |
| ![Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image50.png)    | **Köa sändnings meddelande** (*tx_queue_send_notify*) |
| ![Ikon för Semaforens tak placering](./media/user-guide/tx-events/image51.png)    | **Utplacering av semafor-tak** (*tx_semaphore_ceiling_put*) |
| ![Ikon för att skapa semafor](./media/user-guide/tx-events/image52.png)    | **Skapa semafor** (*tx_semaphore_create*) |
| ![Ikon för borttagning av semafor](./media/user-guide/tx-events/image53.png)    | **Semafors borttagning** (*tx_semaphore_delete*) |
| ![Ikon för Hämta semafor](./media/user-guide/tx-events/image54.png)    | **Hämta semafor** (*tx_semaphore_get*) |
| ![Ikon för Hämta semafors information](./media/user-guide/tx-events/image55.png)    | **Hämta semafors information** (*tx_semaphore_info_get*) |
| ![Ikon för Hämta semafor-prestanda information](./media/user-guide/tx-events/image56.png)    | **Information om semafor-prestanda** (*tx_semaphroe_performance_info_get*) |
| ![Ikon för Hämta semafor-system prestanda information](./media/user-guide/tx-events/image57.png)    | **Prestanda information om semafor-systemet get** (*tx_semaphore_performance_system_info_get*) |
| ![Ikon för semafor-prioritet](./media/user-guide/tx-events/image58.png)    | **Semafor-prioritet** (*tx_semaphore_prioritize*) |
| ![Ikon för semafor-placering](./media/user-guide/tx-events/image59.png)    | **Semafor-placering** (*tx_semaphore_put*) |
| ![Varnings ikon för semafor-placering](./media/user-guide/tx-events/image60.png)    | **Meddelande om semafor-placering** (*tx_semaphore_put_notify*) |
| ![Ikon för tråd skapande](./media/user-guide/tx-events/image61.png)    | **Skapa tråd** (*tx_thread_create*) |
| ![Ikon för tråd borttagning](./media/user-guide/tx-events/image62.png)    | **Tråd borttagning** (*tx_thread_delete*) |
| ![Aviserings ikon för tråds utträde/Entry](./media/user-guide/tx-events/image63.png)    | **Avisering om slut punkt/inmatning av tråd** (*tx_thread_entry_exit_notify*) |
| ![Ikon för tråd identifiering](./media/user-guide/tx-events/image64.png)    | **Identifiera tråd** (*tx_thread_identify*) |
| ![Ikon för Hämta tråd information](./media/user-guide/tx-events/image65.png)    | **Hämta tråd information** (*tx_thread_info_get*) |
| ![Ikon för att hämta tråd prestanda information](./media/user-guide/tx-events/image66.png)    | **Hämta information om tråd prestanda information** (*tx_thread_performance_info_get*) |
| ![Hämta ikon för tråd prestanda system information](./media/user-guide/tx-events/image67.png)    | **Tråd prestanda system information get** (*tx_thread_performance_system_info_get*) |
| ![Ändra ikon för tråd avstängningen](./media/user-guide/tx-events/image68.png)    | **Avstängningen ändring av tråd** (*tx_thread_preemption_change*) |
| ![Ändrings ikon för tråd prioritet](./media/user-guide/tx-events/image69.png)    | **Ändring av tråd prioritet** (*tx_thread_priority_change*) |
| ![Ikon för tråd som låser sig](./media/user-guide/tx-events/image70.png)    | **Tråd överkörning** (*tx_thread_relinquish*) |
| ![Ikon för tråd återställning](./media/user-guide/tx-events/image71.png)    | **Återställning av tråd** (*tx_thread_reset*) |
| ![* Trådens återställnings ikon](./media/user-guide/tx-events/image72.png)    | **Tråd återupptagning** (**tx_thread_resume*) |
| ![Ikon för trådens ström spar läge](./media/user-guide/tx-events/image73.png)    | **Ström spar läge för tråd** (*tx_thread_sleep*) * |
| ![Aviserings ikon för tråds tack](./media/user-guide/tx-events/image74.png)    | **Fel meddelande om tråds tack** (*tx_thread_stack_error_notify*) |
| ![Ikon för att pausa tråd](./media/user-guide/tx-events/image75.png)    | **Paus av tråd** (*tx_thread_suspend*) |
| ![Avsluta ikon för tråd](./media/user-guide/tx-events/image76.png)    | **Tråden avslutas** (*tx_thread_terminate*) |
| ![Tråd tids segmentets ändrings ikon](./media/user-guide/tx-events/image77.png)    | **Trådens tids sektor ändring** (*tx_thread_time_slice_change*) |
| ![Ikon för Avbryt väntan](./media/user-guide/tx-events/image78.png)    | **Avbryt väntan på avbrott** (*tx_thread_wait_abort*) |
| ![Ikonen Hämta tid](./media/user-guide/tx-events/image79.png)    | **Hämtnings tid** (*tx_time_get*) |
| ![Ikon för tids uppsättning](./media/user-guide/tx-events/image80.png)    | **Tids uppsättning** (*tx_time_set*) |
| ![* Ikon för timer-aktivering](./media/user-guide/tx-events/image81.png)    | **Aktivera timer** (*tx_timer_activate*) |
| ![Ändrings ikon för timer](./media/user-guide/tx-events/image82.png)    | **Ändring av timer** (*tx_timer_change*) |
| ![Ikon för timer-skapande](./media/user-guide/tx-events/image83.png)    | **Skapa timer** (*tx_timer_create*) |
| ![Ikonen timer-inaktivera](./media/user-guide/tx-events/image84.png)    | **Timer-inaktive rad** (*tx_timer_deactivate*) |
| ![Ikon för timer-borttagning](./media/user-guide/tx-events/image85.png)    | **Borttagning av timer** (*tx_timer_delete*) |
| ![Hämta ikon för timer-information](./media/user-guide/tx-events/image86.png)    | **Visa timer-information** (*tx_timer_info_get*) |
| ![Ikon för hämtning av timer-prestanda information](./media/user-guide/tx-events/image87.png)    | **Hämta information om timer-prestanda** (*tx_timer_performance_info_get*) |
| ![* Timer för prestanda system information Hämta ikon](./media/user-guide/tx-events/image88.png)    | **Timer Performance system information get** (*tx_timer_performance_system_info_get*) |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | **Användardefinierad händelse** (se kapitel 10)    |

## <a name="event-descriptions"></a>Händelse beskrivningar

### <a name="internal-thread-resume"></a>Återuppta intern tråd

#### <a name="internal-thread-resume"></a>Återuppta intern tråd

**Ikonen** ![ Aktiverings ikon för intern tråd](./media/user-guide/tx-events/image1.png)

**Beskrivning**

Den här händelsen representerar intern bearbetning i ThreadX som återupptar en tråd för körning. Om den angivna tråden är den högsta prioriteten och avstängningen-tröskelvärdet inte blockerar körningen kommer systemet att starta den nya färdiga tråden.

**Informations fält**

- Info fält 1: visar en pekare till tråden som återupptas.
- Info fält 2: föregående tillstånd för tråden som återupptas, enligt följande:

  |  Tråd tillstånd                     | Värde        |
  |---------------------------------- | --------|
  |  TX_READY                         | 0       |
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Info-fält 3: stack pekarens värde under anropet. 
- Info fält 4: pekare till näst högsta prioritets tråd att köra.

### <a name="internal-thread-suspend"></a>Inaktive ring av intern tråd

#### <a name="internal-thread-suspend"></a>Inaktive ring av intern tråd

**Ikonen** ![ Inaktivera ikon för intern tråd](./media/user-guide/tx-events/image2.png)

**Beskrivning**

Den här händelsen representerar intern bearbetning i ThreadX som pausar körningen av en tråd. Den näst högsta prioritets tråden som är klar för körning placeras i det fjärde informations fältet. Om det här värdet är NULL finns det ingen annan tråd klar för körning och systemet är inaktivt.

**Informations fält**

- Info fält 1: pekar på tråden som pausas.
- Informations fält 2: det nya tillståndet för tråden som pausas, enligt följande:

  |  Tråd tillstånd                     | Värde        |
  |---------------------------------- | --------|
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Info-fält 3: stack pekarens värde under anropet. Info fält 4: pekare till näst högsta prioritets tråd att köra. Om värdet är NULL är systemet inaktivt.

### <a name="interrupt-service-routine-isr-enter"></a>Avbrotts service rutin (ISR)-retur 

#### <a name="enter-isr"></a>Ange ISR 

**Ikonen** ![ Ange en R-ikon](./media/user-guide/tx-events/image3.png)

**Beskrivning**

Den här händelsen representerar att ange en avbrotts tjänst rutin (ISR) i programmet. Interrupt Service Routine körningen fortsätter tills den ISR-avsluts händelse äger rum.

**Informations fält**

- Informations fält 1: stack pekarens värde under anropet.
- Info fält 2: Programdefinierat ISR-nummer (valfritt).
- Informations fält 3: kapslat avbrotts antal.
- Info fält 4: intern avstängningen-inaktivera flagga.

### <a name="interrupt-service-routine-isr-exit"></a>Avbryta service rutin (ISR)-avsluta 

#### <a name="exit-isr"></a>Avsluta ISR

**Ikonen** ![ Avsluta I S-ikon](./media/user-guide/tx-events/image4.png)

**Beskrivning**

Den här händelsen representerar att avsluta en avbrotts tjänst rutin (ISR) i programmet.

**Informations fält**

- Informations fält 1: stack pekarens värde under anropet.
- Info fält 2: Programdefinierat ISR-nummer (valfritt).
- Informations fält 3: kapslat avbrotts antal.
- Info fält 4: intern avstängningen-inaktivera flagga.

### <a name="internal-time-slice"></a>Intern tid-sektor

#### <a name="internal-time-slice"></a>Intern tid-sektor

**Ikonen** ![ Intern Time-slice-ikon](./media/user-guide/tx-events/image5.png)

**Beskrivning**

Den här händelsen representerar den interna bearbetningen i ThreadX som utför tids segments åtgärden. Nästa tråd av samma prioritet placeras i det första informations fältet. Om det här värdet är samma som den aktuella tråden utfördes ingen tid-sektor.

- Info fält 1: pekar mot nästa tråd som ska köras.
- Informations fält 2: kapslat avbrotts antal.
- Info-fält 3: intern avstängningen-inaktivera flagga.
- Info-fält 4: stack pekarens värde under anropet.

### <a name="running"></a>Körs

#### <a name="running-in-context"></a>Körs i kontext

**Ikonen** ![ Kör ikon](./media/user-guide/tx-events/image6.png)

**Beskrivning**

Den här händelsen representerar körning i en tråd kontext eller inaktivt system. Den används för att illustrera efterföljande ändringar i sammanhanget som ett resultat av ett avbrott.

**Informations fält**
- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="block-allocate"></a>Blockera tilldelning 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**Ikonen** ![ Ikonen blockera tilldelning](./media/user-guide/tx-events/image7.png)

**Beskrivning**

Den här händelsen representerar att allokera ett minnes block via tx_block_allocate. Om det lyckas returneras adressen för det tilldelade blocket i det andra informations fältet.

**Informations fält**
- Info fält 1: pekar mot motsvarande block-pool.
- Info fält 2: visar en pekare till det minnes block som returnerades (om det lyckades).
- Informations fält 3: vänte alternativet som angavs i tx_block_allocate-anropet.
- Info fält 4: återstående tillgängliga block i poolen efter den här allokeringen.

### <a name="block-pool-create"></a>Blockera skapande av pool

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**Ikonen** ![ Skapa ikon för att blockera pool](./media/user-guide/tx-events/image8.png)

**Beskrivning**

Den här händelsen representerar skapandet av en Memory block-pool via tx_block_pool_create.

**Informations fält**

- Informations fält 1: pekar mot motsvarande block pool kontroll block.
- Info fält 2: pekar på poolens start minne.
- Informations fält 3: antalet block i poolen. Info fält 4: storleken på varje block i poolen i byte.

### <a name="block-pool-delete"></a>Blockera borttagning av pool

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**Ikonen** ![ Ta bort ikon för borttagning av pool](./media/user-guide/tx-events/image9.png)

**Beskrivning**

Den här händelsen representerar borttagning av en Memory block-pool via tx_block_pool_delete.

**Informations fält**

- Informations fält 1: pekar mot kontroll block för block-pool.
- Info-fält 2: stack pekarens värde under anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="block-pool-information-get"></a>Blockera information om poolen Hämta 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**Ikonen** ![ Hämta ikon för Hämta pool information](./media/user-guide/tx-events/image10.png)

**Beskrivning**

Den här händelsen representerar att hämta information om en Memory block-pool via tx_block_pool_info_get.

**Informations fält**

- Informations fält 1: pekar mot kontroll block för block-pool.
- Info-fält 2: stack pekarens värde under anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="block-pool-performance-information-get"></a>Blockera prestanda information för pool

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**Ikonen** ![ Hämta ikon för att blockera poolens prestanda information](./media/user-guide/tx-events/image11.png)

**Beskrivning**

Den här händelsen representerar prestanda information om en Memory block-pool via tx_block_pool_performance_info_get.

**Informations fält**

- Informations fält 1: pekar mot kontroll block för block-pool.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="block-pool-performance-system-information-get"></a>Blockera prestanda system information för poolen Hämta

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**Ikonen** ![ Blockera pool prestanda system information get-ikon](./media/user-guide/tx-events/image12.png)

**Beskrivning**

Den här händelsen representerar prestanda information om alla minnes Blocks pooler via tx_block_pool_performance_system_info_get.

**Informations fält**
- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="block-pool-prioritize"></a>Prioritera block pool

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**Ikonen** ![ Prioritets ikon för att blockera pool](./media/user-guide/tx-events/image13.png)

**Beskrivning**

Den här händelsen representerar placeringen av den HighestPriority suspenderade tråden längst fram i listan över blockerade SUS-listor. Om detta görs innan du anropar tx_block_release, tar den inaktiverade tråden med högsta prioritet det släppta blocket.

**Informations fält**
- Informations fält 1: pekare för minnes Blocks-pool.
- Informations fält 2: antal pausade trådar i den här block poolen.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="block-release"></a>Blockera version 

#### <a name="tx_block_release"></a>tx_block_release

**Ikonen** ![ Ikonen blockera version](./media/user-guide/tx-events/image14.png)

**Beskrivning**

Den här händelsen representerar att släppa ett tidigare allokerat block tillbaka till block-poolen.

**Informations fält**

- Informations fält 1: pekare för minnes Blocks-pool.
- Info fält 2: pekare för att blockera till version.
- Informations fält 3: antal pausade trådar i den här block poolen.
- Info-fält 4: stack pekare vid tidpunkten för anropet.

### <a name="byte-allocate"></a>Allokera byte 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**Ikonen** ![ Ikon för byte tilldelning](./media/user-guide/tx-events/image15.png)

**Beskrivning**

Den här händelsen representerar allokering av minne via tx_byte_allocate. Om det lyckas returneras adressen för det tilldelade minnet i det andra informations fältet.

**Informations fält**
- Info fält 1: pekar mot motsvarande byte-pool.
- Info fält 2: pekar på det returnerade minnet (om det lyckades).
- Informations fält 3: antal byte som har begärts. Info fält 4: vänte alternativet som angavs för tx_byte_allocate-anropet.

### <a name="byte-pool-create"></a>Skapa byte pool

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**Ikonen** ![ Ikon för att skapa byte pool](./media/user-guide/tx-events/image16.png)

**Beskrivning**

Den här händelsen representerar att skapa en byte-pool via tx_byte_pool_create.

**Informations fält**

- Info fält 1: pekar mot motsvarande byte-pool.
- Info fält 2: pekar mot början av minnes området. Informations fält 3: antal byte i byte-poolen.
- Info-fält 4: stack pekaren vid tidpunkten för anropet.

### <a name="byte-pool-delete"></a>Borttagning av byte pool 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**Ikonen** ![ Borttagnings ikon för byte pool](./media/user-guide/tx-events/image17.png)

**Beskrivning**

Den här händelsen representerar borttagning av en byte-pool via tx_byte_pool_delete.

**Informations fält**

- Info fält 1: pekar mot motsvarande byte-pool.
- Info fält 2: stack pekaren vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="byte-pool-information-get"></a>Hämta information om byte pool

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikonen** ![ Ikon för hämta information om byte pool](./media/user-guide/tx-events/image18.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om byte-pool via tx_byte_pool_info_get.

**Informations fält**

- Info fält 1: pekar mot motsvarande byte-pool.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="byte-pool-performance-info-get"></a>Hämta prestanda information för byte-pool 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikonen** ![ Ikon för hämta prestanda information för byte-pool](./media/user-guide/tx-events/image19.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestanda information för byte-pool via tx_byte_pool_performance_info_get.

**Informations fält**

- Info fält 1: pekar mot motsvarande byte-pool.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="byte-pool-performance-system-info-get"></a>Hämta prestanda system information för byte-pool 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**Ikonen** ![ Hämta ikon för prestanda system information för byte pool](./media/user-guide/tx-events/image20.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestanda system information för byte-pool via tx_byte_pool_performance_system_info_get.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="byte-pool-prioritize"></a>Prioritet för byte pool

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**Ikonen** ![ Prioritets ikon för byte pool](./media/user-guide/tx-events/image21.png)

**Beskrivning**

Den här händelsen representerar prioritering av byte-poolens SUS Pension-lista via tx_byte_pool_prioritize.

**Informations fält**

- Info fält 1: pekare till motsvarande byte-pool.
- Informations fält 2: antal trådar som för närvarande har pausats i byte-poolen.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="byte-release"></a>Byte-version

#### <a name="tx_byte_release"></a>tx_byte_release

**Ikonen** ![ Ikon för byte-version](./media/user-guide/tx-events/image22.png)

**Beskrivning**

Den här händelsen representerar att släppa ett minnes block som tilldelas från en byte-pool via tx_byte_release.

**Informations fält**

- Info fält 1: pekare till motsvarande byte-pool.
- Info fält 2: pekare till tidigare allokerat minne i byte-poolen.
- Informations fält 3: antal pausade trådar i den här byte-poolen.
- Info fält 4: antal tillgängliga byte i minnet.

### <a name="event-flags-create"></a>Händelse flaggor skapa 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**Ikonen** ![ Ikonen Skapa händelse flaggor](./media/user-guide/tx-events/image23.png)

**Beskrivning**

Den här händelsen representerar att skapa en ny grupp med händelse flaggor via tx_event_flags_create.

**Informations fält** 
- Info fält 1: pekar på händelse flaggor grupp kontroll block.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="event-flags-delete"></a>Ta bort händelse flaggor 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**Ikonen** ![ Borttagnings ikon för händelse flaggor](./media/user-guide/tx-events/image24.png)

**Beskrivning**

Den här händelsen representerar att ta bort en grupp med händelse flaggor via tx_event_flags_delete.

**Informations fält** 

- Info fält 1: pekar på händelse flaggor grupp.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="event-flags-get"></a>Händelse flaggor Hämta 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**Ikonen** ![ Ikon för händelse flaggor gt](./media/user-guide/tx-events/image25.png)

**Beskrivning**

Den här händelsen representerar hämtning av händelse flaggor från en befintlig grupp för händelse flaggor via tx_event_flags_get.

**Informations fält**

- Info fält 1: pekar på händelse flaggor grupp.
- Informations fält 2: händelse flaggor begärs.
- Info-fält 3: händelse flaggor som för närvarande anges i gruppen.
- Info Field 4: alternativet som begärdes för händelse flaggorna get.

### <a name="event-flags-information-get"></a>Händelse flaggor information Hämta

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**Ikonen** ![ Ikonen Hämta information om händelse flaggor](./media/user-guide/tx-events/image26.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om en befintlig händelse flaggor grupp via tx_event_flags_info_get.

**Informations fält**

- Info fält 1: pekar på händelse flaggor grupp.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="event-flags-performance-information-get"></a>Händelse flaggor prestanda information Hämta 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**Ikonen** ![ Händelse flaggor prestanda information Hämta ikon](./media/user-guide/tx-events/image27.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestanda information om en befintlig händelse flaggor grupp via tx_event_flags_performance_info_get.

**Informations fält** 
- Info fält 1: pekar på händelse flaggor grupp.
- Informations fält 2: används inte
- Informations fält 3: används inte
- Info fält 4: används inte

### <a name="event-flags-performance-system-info-get"></a>Händelse flaggor prestanda system information get

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**Ikonen** ![ Händelse flaggor prestanda system information Hämta ikon](./media/user-guide/tx-events/image28.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestanda information om en befintlig händelse flaggor grupp via tx_event_flags_performance_system_info_get.

**Informations fält**
- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="event-flags-set"></a>Angivna händelse flaggor 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**Ikonen** ![ Ikonen händelse flaggor uppsättning](./media/user-guide/tx-events/image29.png)

**Beskrivning**

Den här händelsen representerar att ange (eller avmarkera) händelse flaggor i en befintlig grupp för händelse flaggor via tx_event_flags_set.

**Informations fält**

- Info fält 1: pekar på händelse flaggor grupp.
- Info-fält 2: händelse flaggor som ska anges (eller rensas).
- Informations fält 3: och eller eller alternativ för händelse flagga.
- Info fält 4: antal pausade trådar i händelse flaggas gruppen.

### <a name="event-flags-set-notify"></a>Meddelande om inställd händelse flaggor

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**Ikonen** ![ Händelse flaggor ange aviserings ikon](./media/user-guide/tx-events/image30.png)

**Beskrivning**

Den här händelsen representerar registrering av ett meddelande återanrop för en händelse flagga som har åtgärd ATS i en befintlig grupp för händelse flaggor via tx_event_flags_set_notify.

**Informations fält**

- Info fält 1: pekar på händelse flaggor grupp.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="interrupt-control"></a>Avbrotts kontroll 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**Ikonen** ![ Avbrotts kontroll ikon](./media/user-guide/tx-events/image31.png)

**Beskrivning**

Den här händelsen representerar ändring av position för avbrotts utelåsning via tx_interrupt_control.

**Informations fält**

- Informations fält 1: nytt avbrotts position.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="mutex-create"></a>Skapa mutex 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**Ikonen** ![ Ikon för mutex-skapande](./media/user-guide/tx-events/image32.png)

**Beskrivning**

Den här händelsen representerar skapandet av en mutex via tx_mutex_create.

**Informations fält**

- Info fält 1: pekar mot mutex-kontroll block.
- Informations fält 2: alternativet prioritera arv
- (TX_INHERIT eller TX_NO_INHERIT).
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="mutex-delete"></a>Ta bort mutex 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**Ikonen** ![ Ikon för mutex-borttagning](./media/user-guide/tx-events/image33.png)

**Beskrivning**

Den här händelsen representerar borttagning av en mutex via tx_mutex_delete.

**Informations fält** 

- Info fält 1: pekar mot mutex.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="mutex-get"></a>Hämta mutex 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**Ikonen** ![ Ikon för att hämta mutex](./media/user-guide/tx-events/image34.png)

**Beskrivning**

Den här händelsen representerar hämtning av en mutex via tx_mutex_get.

**Informations fält**

- Info fält 1: pekar mot mutex.
- Informations fält 2: vänte alternativet som angavs för tx_mutex_get-anropet.
- Informations fält 3: en pekare till tråd som äger mutex (NULL betyder att mutex inte ägs).
- Info fält 4: antal gånger som den ägande tråden har anropat tx_mutex_get.

### <a name="mutex-information-get"></a>Hämtning av mutex-information

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**Ikonen** ![ Get-ikon för mutex information](./media/user-guide/tx-events/image35.png)

**Beskrivning**

Den här händelsen representerar hämtning av mutex-information via tx_mutex_info_get.

**Informations fält**

- Info fält 1: pekar mot mutex.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="mutex-performance-information-get"></a>Information om mutex-prestanda 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**Ikonen** ![ Ikon för hämta information om mutex-prestanda](./media/user-guide/tx-events/image36.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om mutex-prestanda via tx_mutex_performance_info_get.

**Informations fält**

- Info fält 1: pekar mot mutex.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="mutex-performance-system-info-get"></a>Information om att hämta mutex-prestanda

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**Ikonen** ![ Mutex Performance system information get-ikon](./media/user-guide/tx-events/image37.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om mutex-systemets prestanda via tx_mutex_performance_system_info_get.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="mutex-prioritize"></a>Mutex-prioritering 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**Ikonen** ![ Ikon för mutex-prioritet](./media/user-guide/tx-events/image38.png)

**Beskrivning**

Den här händelsen representerar prioritering av mutexens SUS Pension-lista via tx_mutex_prioritize.

**Informations fält**

- Info fält 1: pekare till motsvarande mutex.
- Informations fält 2: antal trådar som för närvarande har pausats på mutex.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="mutex-put"></a>Mutex-placering 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**Ikonen** ![ Ikon för mutex-placering](./media/user-guide/tx-events/image39.png)

**Beskrivning**

Den här händelsen representerar att släppa en tidigare ägd mutex via tx_mutex_put.

**Informations fält**

- Info fält 1: pekare till motsvarande mutex.
- Info fält 2: en pekare på en tråd som äger mutex.
- Informations fält 3: antal utestående mutex get-begäranden.
- Info-fält 4: stack pekare vid tidpunkten för anropet.

### <a name="queue-create"></a>Skapa kö 

#### <a name="tx_queue_create"></a>tx_queue_create

**Ikonen** ![ Ikon för att skapa kö](./media/user-guide/tx-events/image40.png)

**Beskrivning**

Den här händelsen representerar att skapa en meddelandekö via tx_queue_create.

**Informations fält**

- Info fält 1: pekar på kontroll block för kö.
- Info fält 2: meddelandets storlek – i termer av 32-bitars ord.
- Info-fält 3: pekar till början av kös Memory Area.
- Info-fält 4: antal byte i köns minnes område.

### <a name="queue-delete"></a>Köa borttagning 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**Ikonen** ![ Borttagnings ikon för kö](./media/user-guide/tx-events/image41.png)

**Beskrivning**

Den här händelsen representerar borttagning av en kö via tx_queue_delete.

**Informations fält**

- Info fält 1: pekare till Queue.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="queue-flush"></a>Köa rensning 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**Ikonen** ![ Ikon för köa tömning](./media/user-guide/tx-events/image42.png)

**Beskrivning**

Den här händelsen representerar tömning (rensa allt innehåll i kön) i en kö via tx_queue_flush.

**Informations fält**

- Info fält 1: pekare till Queue.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="queue-front-send"></a>Skicka kö, klient 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**Ikonen** ![ Ikon för att skicka kön direkt](./media/user-guide/tx-events/image43.png)

**Beskrivning**

Den här händelsen representerar att skicka ett meddelande längst fram i kön via tx_queue_front_send.

**Informations fält**

- Info fält 1: pekare till Queue.
- Info fält 2: pekare till början av meddelandet.
- Informations fält 3: vänte alternativ har angetts till
- tx_queue_front_send-anrop.
- Info fält 4: antal meddelanden som redan har placerats i kö.

### <a name="queue-information-get"></a>Hämta information om kön 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**Ikonen** ![ Hämta ikon för köa information](./media/user-guide/tx-events/image44.png)

**Beskrivning**

Den här händelsen representerar att hämta information om en kö via tx_queue_info_get.

**Informations fält** 
- Info fält 1: pekare till Queue.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="queue-performance-info-get"></a>Hämta prestanda information för kö 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**Ikonen** ![ Hämta ikon för köns prestanda information](./media/user-guide/tx-events/image45.png)

**Beskrivning**

Den här händelsen representerar prestanda information om en kö via tx_queue_performance_info_get.

**Informations fält** 

- Info fält 1: pekare till Queue.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="queue-performance-system-info-get"></a>Hämta prestanda system information för kö 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**Ikonen** ![ Hämta ikon för prestanda system information i kö](./media/user-guide/tx-events/image46.png)

**Beskrivning**

Den här händelsen representerar system prestanda information om alla köer i systemet.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="queue-prioritize"></a>Prioritet för kö 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**Ikonen** ![ Ikon för köa prioritet](./media/user-guide/tx-events/image47.png)

**Beskrivning**

Den här händelsen representerar prioritering av köns SUS Pension-lista via tx_queue_prioritize.

**Informations fält** 

- Info fält 1: pekare till motsvarande kö.
- Informations fält 2: antal trådar som för närvarande har pausats i kön.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

#### <a name="queue-receive"></a>Ta emot kön 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**Ikonen** ![ Ikon för köa mottagning](./media/user-guide/tx-events/image48.png)

**Beskrivning**

Den här händelsen representerar att ta emot ett meddelande från en kö via tx_queue_receive.

**Informations fält** 

- Info fält 1: pekare till Queue.
- Info fält 2: pekare till målet för meddelandet. Info-fält 3: vänte alternativ har angetts för anropet.
- Info fält 4: antal meddelanden som för närvarande finns i kö.

### <a name="queue-send"></a>Köa sändning 

#### <a name="tx_queue_send"></a>tx_queue_send

**Ikonen** ![ Ikon för Queue-sändning](./media/user-guide/tx-events/image49.png)

**Beskrivning**

Den här händelsen representerar att skicka ett meddelande till en kö via tx_queue_send.

**Informations fält** 

- Info fält 1: pekare till Queue.
- Info fält 2: pekare till meddelande.
- Info-fält 3: vänte alternativ har angetts för anropet.
- Info fält 4: antal meddelanden som för närvarande finns i kö.

### <a name="queue-send-notify"></a>Skicka meddelande om kö 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**Ikonen** ![ Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image50.png)

**Beskrivning**

<p>Den här händelsen representerar registrering av ett återanrop via tx_queue_send_notify som anropas när ett meddelande skickas till en kö.

**Informations fält** 

- Info fält 1: pekare till Queue.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="semaphore-ceiling-put"></a>Utplacering av semafors tak 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**Ikonen** ![ Ikon för Semaforens tak placering](./media/user-guide/tx-events/image51.png)

**Beskrivning**

Den här händelsen representerar att placera en semafor via tx_semaphore_ceiling_put. Detta skiljer sig från tx_semaphore_put i så fall att det maximala värdet för semaforen kontrol leras så att placerings åtgärden inte får överskrida det högsta värdet eller taket.

**Informations fält**

- Info fält 1: pekar mot semafor.
- Informations fält 2: aktuellt semafor-antal.
- Informations fält 3: antal pausade trådar i semaforen.
- Info-fält 4: gräns värdet för tak har angetts till anropet.

#### <a name="semaphore-create"></a>Skapa semafor 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**Ikonen** ![ Ikon för att skapa semafor](./media/user-guide/tx-events/image52.png)

**Beskrivning**

Den här händelsen representerar skapandet av en semafor via tx_semaphore_create.

**Informations fält**

- Informations fält 1: pekar mot semafor-kontroll block.
- Informations fält 2: inledande semafor-antal.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="semaphore-delete"></a>Ta bort semafor 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**Ikonen** ![ Ikon för borttagning av semafor](./media/user-guide/tx-events/image53.png)

**Beskrivning**

Den här händelsen representerar borttagning av en semafor via tx_semaphore_delete.

**Informations fält**

- Info fält 1: pekar mot semafor.
- NFO-fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="semaphore-get"></a>Hämta semafor 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**Ikonen** ![ Ikon för Hämta semafor](./media/user-guide/tx-events/image54.png)

**Beskrivning**

Den här händelsen representerar hämtning av en semafor via tx_semaphore_get.

**Informations fält**

- Info fält 1: pekar mot semafor.
- Info fält 2: vänte alternativet angavs för anropet.
- Informations fält 3: Aktuellt antal semaforer.
- Info-fält 4: stack pekare vid tidpunkten för anropet.

### <a name="semaphore-information-get"></a>Hämta semafors information 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**Ikonen** ![ Ikon för Hämta semafors information](./media/user-guide/tx-events/image55.png)

**Beskrivning**

Den här händelsen representerar att hämta information om en semafor via tx_semaphore_info_get.

**Informations fält**

- Info fält 1: pekar mot semafor.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="semaphore-performance-info-get"></a>Hämta information om semafor-prestanda 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**Ikonen** ![ Hämta ikon för semafor-prestanda info](./media/user-guide/tx-events/image56.png)

**Beskrivning**

Den här händelsen representerar att hämta prestanda information om en semafor via tx_semaphore_performance_info_get.

**Informations fält**

- Info fält 1: pekar mot semafor.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="semaphore-performance-system-info"></a>Information om prestanda system för semafor 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**Ikonen** ![ System informations ikon för semafor-prestanda](./media/user-guide/tx-events/image57.png)

**Beskrivning**

Den här händelsen representerar prestanda information om alla semaforer i systemet via tx_semaphore_performance_system_info_get.

**Informations fält** 

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="semaphore-prioritize"></a>Semafor-prioritet 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**Ikonen** ![ Ikon för semafor-prioritet](./media/user-guide/tx-events/image58.png)

**Beskrivning**

Den här händelsen representerar prioriteringen av Semaforens SUS Pension-lista via tx_semaphore_prioritize.

**Informations fält**

- Info fält 1: pekare till motsvarande semafor.
- Informations fält 2: antal trådar som för närvarande har pausats på semaforen.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="semaphore-put"></a>Semafor-placering 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**Ikonen** ![ Ikon för semafor-placering](./media/user-guide/tx-events/image59.png)

**Beskrivning**

Den här händelsen representerar att släppa en semafor-instans via tx_semaphore_put.

**Informations fält** 

- Info fält 1: pekare till motsvarande semafor. Informations fält 2: aktuellt semafor-antal.
- Informations fält 3: antal pausade trådar i semaforen.
- Info-fält 4: stack pekare vid tidpunkten för anropet.

### <a name="semaphore-put-notify"></a>Meddelande om semafors placering 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**Ikonen** ![ Varnings ikon för semafor-placering](./media/user-guide/tx-events/image60.png)

**Beskrivning**

Den här händelsen representerar registrering av ett återanrop via tx_semaphore_put_notify som anropas när en semafors instans placeras.

**Informations fält** 

- Info fält 1: pekar mot semafor.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-create"></a>Skapa tråd 

#### <a name="tx_thread_create"></a>tx_thread_create

**Ikonen** ![ Ikon för tråd skapande](./media/user-guide/tx-events/image61.png)

**Beskrivning**

Den här händelsen representerar skapandet av en tråd via tx_thread_create.

**Informations fält**

- Info fält 1: pekare till tråd kontroll block.
- Informations fält 2: tråd prioritet.
- Info-fält 3: stack pekare för tråd.
- NFO-fält 4: storlek på stack i byte.

### <a name="thread-delete"></a>Ta bort tråd 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**Ikonen** ![ Ikon för tråd borttagning](./media/user-guide/tx-events/image62.png)

**Beskrivning**

Den här händelsen representerar borttagning av en tråd via tx_thread_delete.

**Informations fält** 

- Info fält 1: pekare till Thread.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-entryexit-notify"></a>Avisering om tråd inmatning/avsluta 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**Ikonen** ![ Aviserings ikon för tråd post/avsluta](./media/user-guide/tx-events/image63.png)

**Beskrivning**

Den här händelsen representerar registrering av ett återanrop via tx_thread_entry_exit_notify som anropas när en tråd anges eller avslutas.

**Informations fält** 

- Info fält 1: pekare till Thread.
- Info fält 2: tråd tillstånd vid registreringen.
- Info fält 3: pekare till stack vid tidpunkten för anropet.
- Info fält 4: används inte.

#### <a name="thread-identify"></a>Identifiera tråd 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**Ikonen** ![ Ikon för tråd identifiering](./media/user-guide/tx-events/image64.png)

**Beskrivning**

Den här händelsen representerar hämtning av den aktuella tråd pekaren via tx_thread_identify.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-information-get"></a>Hämta tråd information 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**Ikonen** ![ Ikon för Hämta tråd information](./media/user-guide/tx-events/image65.png)

**Beskrivning**

Den här händelsen representerar att hämta information om den angivna tråden via tx_thread_info_get.

**Informations fält**

- Info fält 1: pekare till Thread.
- Informations fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

#### <a name="thread-performance-information-get"></a>Hämta information om tråd prestanda 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**Ikonen** ![ Ikon för att hämta tråd prestanda information](./media/user-guide/tx-events/image66.png)

**Beskrivning**

Den här händelsen representerar prestanda information om den angivna tråden via tx_thread_performance_info_get.

**Informations fält**

- Info fält 1: pekare till Thread.
- Informations fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-performance-system-info-get"></a>Hämta information om tråd prestanda system information 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**Ikonen** ![ Hämta ikon för tråd prestanda system information](./media/user-guide/tx-events/image67.png)

**Beskrivning**

Den här händelsen representerar prestanda information om alla trådar via tx_thread_performance_system_info_get.

**Informations fält** 

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-preemption-change"></a>Avstängningen ändring av tråd 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**Ikonen** ![ Ändra ikon för tråd avstängningen](./media/user-guide/tx-events/image68.png)

**Beskrivning**

Den här händelsen representerar ändring av en tråds avstängningen-tröskelvärde via tx_thread_preemption_change.

**Informations fält** 

- Info fält 1: pekare till Thread.
- Info fält 2: ny avstängningen-tröskel.
- Info-fält 3: föregående avstängningen-tröskel.
- Info Field 4: Trådens tillstånd vid tidpunkten för anropet.

### <a name="thread-priority-change"></a>Ändring av tråd prioritet 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**Ikonen** ![ Ändrings ikon för tråd prioritet](./media/user-guide/tx-events/image69.png)

**Beskrivning**

Den här händelsen representerar att ändra en tråds prioritet via tx_thread_priority_change.

- Informations fält 
- Info fält 1: pekare till Thread.
- Info fält 2: ny prioritet.
- Info-fält 3: föregående prioritet.
- Info Field 4: Trådens tillstånd vid tidpunkten för anropet.

### <a name="thread-relinquish"></a>Tråd som låser sig 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**Ikonen** ![ Ikon för tråd som låser sig](./media/user-guide/tx-events/image70.png)

**Beskrivning**

Den här händelsen representerar att lämna processorn från en tråd via tx_thread_relinquish.

**Informations fält**

- Info-fält 1: stack pekare vid tidpunkten för anropet.
- Info fält 2: pekar mot nästa tråd som ska köras.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-reset"></a>Återställ tråd 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**Ikonen** ![ Ikon för tråd återställning](./media/user-guide/tx-events/image71.png)

**Beskrivning**

Den här händelsen representerar återställning av en slutförd eller avslutad tråd via tx_thread_reset.

**Informations fält**

- Info fält 1: pekare till Thread.
- Info fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

#### <a name="thread-resume"></a>Återuppta tråd 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**Ikonen** ![ Återställnings ikon för tråd](./media/user-guide/tx-events/image72.png)

**Beskrivning**

Den här händelsen representerar återuppta en pausad tråd via tx_thread_resume.

**Informations fält**

- Info fält 1: pekare till Thread.
- Info fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="thread-sleep"></a>Trådens vilo läge 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**Ikonen** ![ Ikon för trådens ström spar läge](./media/user-guide/tx-events/image73.png)

**Beskrivning**

Den här händelsen representerar uppehåll i den aktuella tråden för ett angivet antal timer-Tick via tx_thread_sleep.

**Informations fält**

- Informations fält 1: antal markeringar som ska pausas.
- Info fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="thread-stack-error-notify"></a>Meddelande om tråds tack 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**Ikonen** ![ Aviserings ikon för tråds tack](./media/user-guide/tx-events/image74.png)

**Beskrivning**

Den här händelsen representerar registrering av ett fel meddelande i en tråd stack via tx_thread_stack_error_notify_event.

**Informations fält** 

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="thread-suspend"></a>Tråden pausar 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**Ikonen** ![ Ikon för att pausa tråd](./media/user-guide/tx-events/image75.png)

**Beskrivning**

Den här händelsen representerar paus av en tråd via tx_thread_suspend.

**Informations fält** 

- Info fält 1: pekare till tråd för att pausa.
- Info fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="thread-terminate"></a>Tråden avslutas 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**Ikonen** ![ Avsluta ikon för tråd](./media/user-guide/tx-events/image76.png)

**Beskrivning**

Den här händelsen representerar att avsluta en tråd via tx_thread_terminate.

**Informations fält** 

- Info fält 1: pekare till tråd för att avsluta.
- Info fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="thread-time-slice-change"></a>Ändring av tråd Time-Slice 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**Ikonen** ![ Tråd tids segmentets ändrings ikon](./media/user-guide/tx-events/image77.png)

**Beskrivning**

Den här händelsen representerar ändring av en tråds Time-slice via tx_thread_time_slice_change.

**Informations fält**

- Info fält 1: pekare till Thread.
- Info fält 2: ny Time-slice.
- Info-fält 3: föregående Time-slice.
- Info fält 4: används inte.

### <a name="thread-wait-abort"></a>Avbryt väntan på konversation 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**Ikonen** ![ Ikon för Avbryt väntan](./media/user-guide/tx-events/image78.png)

**Beskrivning**

Den här händelsen representerar avbrott i en tråds fjädring via tx_thread_wait_abort.

**Informations fält**

- Info fält 1: pekare till Thread.
- Info fält 2: Trådens tillstånd vid tidpunkten för anropet.
- Info-fält 3: stack pekare vid tidpunkten för anropet.
- Info fält 4: används inte.

### <a name="time-get"></a>Hämta tid 

#### <a name="tx_time_get"></a>tx_time_get

**Ikonen** ![ Ikonen Hämta tid](./media/user-guide/tx-events/image79.png)

**Beskrivning**

Den här händelsen representerar det aktuella antalet timer-Tick via tx_time_get.

**Informations fält**

- Informations fält 1: Aktuellt antal timer-Tick.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="time-set"></a>Tids uppsättning 

#### <a name="tx_time_set"></a>tx_time_set

**Ikonen** ![ Ikon för tids uppsättning](./media/user-guide/tx-events/image80.png)

**Beskrivning**

Den här händelsen representerar att ange det aktuella antalet timer-Tick via tx_time_set.

**Informations fält**

- Informations fält 1: nytt antal timer-Tick.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="timer-activate"></a>Aktivera timer 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**Ikonen** ![ Ikon för aktivering av timer](./media/user-guide/tx-events/image81.png)

**Beskrivning**

Den här händelsen representerar aktivering av angiven timer via tx_timer_activate.

**Informations fält**

- Info-fält 1: pekar mot timer.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="timer-change"></a>Ändring av timer 

#### <a name="tx_timer_change"></a>tx_timer_change

**Ikonen** ![ Ändrings ikon för timer](./media/user-guide/tx-events/image82.png)

**Beskrivning**

Den här händelsen representerar att ändra den angivna timern via tx_timer_change.

**Informations fält**

- Info-fält 1: pekar mot timer.
- Info fält 2: Start-utgångs-Tick.
- Info-fält 3: schemalägga om förfallo Tick.
- Info fält 4: används inte.

### <a name="timer-create"></a>Skapa timer 

#### <a name="tx_timer_create"></a>tx_timer_create

**Ikonen** ![ Ikon för timer-skapande](./media/user-guide/tx-events/image83.png)

**Beskrivning**

Den här händelsen representerar skapandet av en timer via tx_timer_create.

**Informations fält**

- Informations fält 1: pekar mot timer-kontroll-block.
- Info fält 2: Start-utgångs-Tick.
- Info-fält 3: schemalägga om förfallo Tick.
- Info fält 4: automatiskt aktiverings värde – antingen TX_AUTO_ACTIVATE (1) eller TX_NO_ACTIVATE (0).

### <a name="timer-deactivate"></a>Inaktivera timer 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**Ikonen** ![ Ikonen timer-inaktivera](./media/user-guide/tx-events/image84.png)

**Beskrivning**

Den här händelsen representerar inaktive ring av en timer via tx_timer_deactivate.

**Informations fält**

- Info-fält 1: pekar mot timer.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="timer-delete"></a>Borttagning av timer 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**Ikonen** ![ Ikon för timer-borttagning](./media/user-guide/tx-events/image85.png)

**Beskrivning**

Den här händelsen representerar borttagning av en timer via tx_timer_delete.

**Informations fält** 

- Info-fält 1: pekar mot timer.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="timer-information-get"></a>Hämta timer-information 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**Ikonen** ![ Ikon för att hämta information om timer](./media/user-guide/tx-events/image86.png)

**Beskrivning**

Den här händelsen representerar information om tidtagare via tx_timer_info_get.

**Informations fält**

- Info-fält 1: pekar mot timer.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="timer-performance-information-get"></a>Hämta information om timer-prestanda 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**Ikonen** ![ Ikon för hämtning av timer-prestanda information](./media/user-guide/tx-events/image87.png)

**Beskrivning** 

Den här händelsen representerar hämtning av information om timer-prestanda via tx_timer_performance_info_get.

**Informations fält**

- Info-fält 1: pekar mot timer.
- Info fält 2: stack pekare vid tidpunkten för anropet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="timer-system-performance-info-get"></a>Hämta timer system prestanda information 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**Ikonen** ![ Hämta ikon för timer-systemets prestanda information](./media/user-guide/tx-events/image88.png)


**Beskrivning** 

Den här händelsen representerar hämtning av all information om timer-prestanda via tx_timer_performance_system_info_get.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.