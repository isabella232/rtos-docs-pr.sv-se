---
title: Kapitel 6 – Azure RTOS ThreadX-spårningshändelser
description: I det här kapitlet beskrivs Azure RTOS ThreadX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 9fefc43002d4e0d6df817ad56d79b3e41a3d649504be50f5a39f67c1896b2e9a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116800982"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>Kapitel 6 – Azure RTOS ThreadX-spårningshändelser

I det här kapitlet beskrivs Azure RTOS ThreadX-händelser. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

Följande är en lista över ThreadX-händelser som visas av TraceX:

| **Ikon**                         | **Innebörd** |
| -------------------------------- | ------------------------------------- |
| ![Ikon för internt tråd-CV](./media/user-guide/tx-events/image1.png)    | Återuppta intern tråd  |
| ![Pausikon för intern tråd](./media/user-guide/tx-events/image2.png)    | Pausa intern tråd |
| ![Ikonen Avbryt tjänstrutin Retur](./media/user-guide/tx-events/image3.png)    | Avbryt tjänstrutin (ISR) Ange |
| ![Ikonen Avbryt tjänstrutinens avslut](./media/user-guide/tx-events/image4.png)    | Isr-avslut (Interrupt Service Routine)  |
| ![Ikon för internt tidssegment](./media/user-guide/tx-events/image5.png)    | Intern tidssegment |
| ![Ikonen Körs](./media/user-guide/tx-events/image6.png)    | Körs |
| ![Ikonen Blockera allokera pool](./media/user-guide/tx-events/image7.png)    | **Blockera allokera pool** (*tx_block_allocate*)  |
| ![Ikonen Skapa blockpool](./media/user-guide/tx-events/image8.png)    | **Blockera pool create** (*tx_block_pool_create*) |
| ![Ikonen Blockera borttagning av pool](./media/user-guide/tx-events/image9.png)    | **Blockera borttagning av pool** (*tx_block_pool_delete*) |
| ![Hämta-ikonen Blockera poolinformation](./media/user-guide/tx-events/image10.png)    | **Blockpoolinformation hämta** (*tx_block_pool_info_get*) |
| ![Block pool performance information get con](./media/user-guide/tx-events/image11.png)    | **Block pool performance information get** (*tx_block_pool_performance_info_get*) |
| ![Hämta ikon för blockpoolsystemsprestanda](./media/user-guide/tx-events/image12.png)    | **Block pool system performance information get** (*tx_block_pool_performance_system_info_get*) |
| ![Ikonen Blockera poolprioritering](./media/user-guide/tx-events/image13.png)    | **Blockera poolprioritering** (*tx_block_pool_prioritize*) |
| ![Ikonen Blockera version till pool](./media/user-guide/tx-events/image14.png)    | **Blockera version till pool** (*tx_block_release*) |
| ![Ikonen Allokera minne för bytepool](./media/user-guide/tx-events/image15.png)    | **Bytepoolen allokerar minne** (*tx_byte_allocate*) |
| ![Ikon för att skapa bytepool](./media/user-guide/tx-events/image16.png)    | **Skapa bytepool** (*tx_byte_pool_create*) |
| ![Ikon för borttagning av bytepool](./media/user-guide/tx-events/image17.png)    | **Ta bort bytepool** (*tx_byte_pool_delete*) |
| ![Hämta ikon för bytepoolsinformation](./media/user-guide/tx-events/image18.png)    | **Bytepoolsinformation hämta** (*tx_byte_pool_info_get*) |
| ![Hämta ikon för prestandainformation för bytepool](./media/user-guide/tx-events/image19.png)    | **Prestandainformation för bytepoolen hämtar** (*tx_byte_pool_performance_info_get*) |
| ![Hämta ikon för systemprestanda för bytepool](./media/user-guide/tx-events/image20.png)    | **Prestandainformation för bytepooler hämtar** (*tx_byte_pool_performance_system_info_get*) |
| ![*Prioritera ikon för bytepool](./media/user-guide/tx-events/image21.png)    | **Prioritera bytepool** (*tx_byte_pool_prioritize*) |
| ![Ikon för byteminnes frisläppning till pool](./media/user-guide/tx-events/image22.png)    | **Byteminnesutgågås till pool** (*tx_byte_release*) |
| ![Ikonen Skapa händelseflaggor](./media/user-guide/tx-events/image23.png)    | **Händelseflaggor skapar** (*tx_event_flags_create*) |
| ![Ikonen Ta bort händelseflaggor](./media/user-guide/tx-events/image24.png)    | **Ta bort händelseflaggor** (*tx_event_flags_delete*) |
| ![Ikonen Hämta händelseflaggor](./media/user-guide/tx-events/image25.png)    | **Händelseflaggor hämtar** (*tx_event_flags_get*) |
| ![Information om händelseflaggor – hämta ikon](./media/user-guide/tx-events/image26.png)    | **Information om händelseflaggor hämta** (*tx_event_flags_info_get*) |
| ![Ikonen Hämta prestandainformation för händelseflaggor](./media/user-guide/tx-events/image27.png)    | **Prestandainformation för händelseflaggor hämtar** (*tx_event_flags_performance_info_get*) |
| ![Ikonen Hämta information om systemprestanda för händelseflaggor](./media/user-guide/tx-events/image28.png)    | **Händelseflaggor systemprestandainformation hämta** (*tx_event_flags_performance_system_info_get*) |
| ![Ikon för uppsättning av händelseflaggor](./media/user-guide/tx-events/image29.png)    | **Händelseflaggor (** *tx_event_flags_set*) |
| ![Händelseflaggor ange av meddela-ikon](./media/user-guide/tx-events/image30.png)    | **Händelseflaggor anger notify** (*tx_event_flags_set_notify*) |
| ![Ikonen Aktivera/inaktivera avbrott](./media/user-guide/tx-events/image31.png)    | **Aktivera/inaktivera avbrott** (*tx_interrupt_control*) |
| ![Ikon för att skapa Mutex](./media/user-guide/tx-events/image32.png)    | **Mutex create** (*tx_mutex_create*) |
| ![Ta bort mutex-ikon](./media/user-guide/tx-events/image33.png)    | **Mutex delete** (*tx_mutex_delete*) |
| ![Mutex-hämta-ikon](./media/user-guide/tx-events/image34.png)    | **Mutex get** (*tx_mutex_get*) |
| ![Ikon för att hämta Mutex-information](./media/user-guide/tx-events/image35.png)    | **Mutex-information get** (*tx_mutex_info_get*) |
| ![Information om Mutex-prestanda – hämta ikon](./media/user-guide/tx-events/image36.png)    | **Information om Mutex-prestanda får** (*tx_mutex_performance_info_get*) |
| ![Ikon för att hämta information om Mutex-systemprestanda](./media/user-guide/tx-events/image37.png)    | **Information om Mutex-systemprestanda får** (*tx_mutex_performance_system_info_get*) |
| ![Ikonen För att prioritera Mutex](./media/user-guide/tx-events/image38.png)    | **Mutex prioritize** (*tx_mutex_prioritize*) |
| ![Mutex-put-ikon](./media/user-guide/tx-events/image39.png)    | **Mutex put** (*tx_mutex_put*) |
| ![Ikon för att skapa kö](./media/user-guide/tx-events/image40.png)    | **Skapa kö** (*tx_queue_create*) |
| ![Ikonen Ta bort kö](./media/user-guide/tx-events/image41.png)    | **Ta bort kö** (*tx_queue_delete*) |
| ![Ikon för att tömma köer](./media/user-guide/tx-events/image42.png)    | **Kö flush** (*tx_queue_flush*) |
| ![Ikonen För att skicka i kö fram](./media/user-guide/tx-events/image43.png)    | **Queue front send** (*tx_queue_front_send*) |
| ![Hämta ikon för köinformation](./media/user-guide/tx-events/image44.png)    | **Köinformation get** (*tx_queue_info_get*) |
| ![Information om köprestanda – hämta ikon](./media/user-guide/tx-events/image45.png)    | **Information om köprestanda hämta** (*tx_queue_performance_info_get*) |
| ![Information om prestandainformation för kösystem – hämta ikon](./media/user-guide/tx-events/image46.png)    | **Information om prestanda för kösystem får** (*tx_queue_performance_system_info_get*) |
| ![Köprioriteringsikon](./media/user-guide/tx-events/image47.png)    | **Köprioritera** (*tx_queue_prioritize*) |
| ![Ikon för att ta emot meddelande i kö](./media/user-guide/tx-events/image48.png)    | **Ta emot meddelande i kö** (*tx_queue_receive*) |
| ![Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image49.png)    | **Skicka meddelande i kö** (*tx_queue_send*) |
| ![Meddelandeikon för att skicka kö](./media/user-guide/tx-events/image50.png)    | **Meddelande om att skicka kö** (*tx_queue_send_notify*) |
| ![Ikon för att sätta ett tak i Semaphore](./media/user-guide/tx-events/image51.png)    | **Semaphore ceiling put** (*tx_semaphore_ceiling_put*) |
| ![Ikonen För att skapa Semaphore](./media/user-guide/tx-events/image52.png)    | **Semaphore create** (*tx_semaphore_create*) |
| ![Ikonen Ta bort Semaphore](./media/user-guide/tx-events/image53.png)    | **Ta bort Semaphore** (*tx_semaphore_delete*) |
| ![Ikonen Semaphore get](./media/user-guide/tx-events/image54.png)    | **Semaphore get** (*tx_semaphore_get*) |
| ![Hämta information om Semaphore-ikonen](./media/user-guide/tx-events/image55.png)    | **Semaphore information get** (*tx_semaphore_info_get*) |
| ![Hämta ikon för semaphore-prestandainformation](./media/user-guide/tx-events/image56.png)    | **Semaphore performance information get** (*tx_semaphroe_performance_info_get*) |
| ![Information om semaphore-systemprestanda – hämta ikon](./media/user-guide/tx-events/image57.png)    | **Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*) |
| ![Ikonen Prioritera Semaphore](./media/user-guide/tx-events/image58.png)    | **Semaphore prioritize** (*tx_semaphore_prioritize*) |
| ![Semaphore put-ikon](./media/user-guide/tx-events/image59.png)    | **Semaphore put** (*tx_semaphore_put*) |
| ![Aviseringsikon för Semaphore put](./media/user-guide/tx-events/image60.png)    | **Semaphore put notify** (*tx_semaphore_put_notify*) |
| ![Ikon för att skapa tråd](./media/user-guide/tx-events/image61.png)    | **Tråd skapa** (*tx_thread_create*) |
| ![Ikonen Ta bort tråd](./media/user-guide/tx-events/image62.png)    | **Borttagning av tråd** (*tx_thread_delete*) |
| ![Meddelandeikon för avslut/inmatning av tråd](./media/user-guide/tx-events/image63.png)    | **Avslut/inmatning av tråd** (*tx_thread_entry_exit_notify*) |
| ![Ikon för tråd-identifiering](./media/user-guide/tx-events/image64.png)    | **Tråd-identifiera** (*tx_thread_identify*) |
| ![Ikonen Hämta trådinformation](./media/user-guide/tx-events/image65.png)    | **Trådinformation get** (*tx_thread_info_get*) |
| ![Ikonen Hämta trådprestandainformation](./media/user-guide/tx-events/image66.png)    | **Trådprestandainformation hämta** (*tx_thread_performance_info_get*) |
| ![Ikonen Hämta information om trådprestandasystem](./media/user-guide/tx-events/image67.png)    | **Systeminformation för trådprestanda hämta** (*tx_thread_performance_system_info_get*) |
| ![Ikon för ändring av trådförsening](./media/user-guide/tx-events/image68.png)    | **Ändring av trådförsening** (*tx_thread_preemption_change*) |
| ![Ikon för ändring av trådprioritet](./media/user-guide/tx-events/image69.png)    | **Ändring av trådprioritet** (*tx_thread_priority_change*) |
| ![Ikon för trådrelinering](./media/user-guide/tx-events/image70.png)    | **Trådrelinquish** *(tx_thread_relinquish)* |
| ![Ikon för trådåterställning](./media/user-guide/tx-events/image71.png)    | **Trådåterställning** (*tx_thread_reset*) |
| ![*Ikon för tråd återuppta](./media/user-guide/tx-events/image72.png)    | **Tråd-RESUME** (**tx_thread_resume*) |
| ![Ikon för tråd strömsparläge](./media/user-guide/tx-events/image73.png)    | **Trådsparläge** (*tx_thread_sleep*)* |
| ![Meddelandeikon för trådstacksfel](./media/user-guide/tx-events/image74.png)    | **Meddela om trådstacksfel** (*tx_thread_stack_error_notify*) |
| ![Ikonen För att pausa trådar](./media/user-guide/tx-events/image75.png)    | **Tråd paus** (*tx_thread_suspend*) |
| ![Ikonen Avsluta tråd](./media/user-guide/tx-events/image76.png)    | **Tråd avslutas** (*tx_thread_terminate*) |
| ![Ikon för ändring av trådtidssegment](./media/user-guide/tx-events/image77.png)    | **Ändring av trådtidssegment** (*tx_thread_time_slice_change*) |
| ![Ikon för väntande av tråd](./media/user-guide/tx-events/image78.png)    | **Trådvänte abort** (*tx_thread_wait_abort*) |
| ![Ikonen För tids get](./media/user-guide/tx-events/image79.png)    | **Time get** (*tx_time_get*) |
| ![Ikon för tidsuppsättning](./media/user-guide/tx-events/image80.png)    | **Tidsuppsättning** (*tx_time_set*) |
| ![*Aktiveringsikon för timer](./media/user-guide/tx-events/image81.png)    | **Aktivera timer** (*tx_timer_activate*) |
| ![Ikon för timerändring](./media/user-guide/tx-events/image82.png)    | **Timerändring** (*tx_timer_change*) |
| ![Ikon för att skapa timer](./media/user-guide/tx-events/image83.png)    | **Skapa timer** (*tx_timer_create*) |
| ![Inaktivera timerikon](./media/user-guide/tx-events/image84.png)    | **Timeraktivering** (*tx_timer_deactivate*) |
| ![Borttagningsikon för timer](./media/user-guide/tx-events/image85.png)    | **Ta bort timer** (*tx_timer_delete*) |
| ![Hämta ikon för timerinformation](./media/user-guide/tx-events/image86.png)    | **Timerinformation hämta** (*tx_timer_info_get*) |
| ![Information om timerprestanda – hämta ikon](./media/user-guide/tx-events/image87.png)    | **Information om timerprestanda hämta** (*tx_timer_performance_info_get*) |
| ![*Information om timerprestandasystem – hämta ikon](./media/user-guide/tx-events/image88.png)    | **Information om timerprestandasystem få** (*tx_timer_performance_system_info_get*) |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | **Användardefinierad händelse** (se kapitel 10)    |

## <a name="event-descriptions"></a>Händelsebeskrivningar

### <a name="internal-thread-resume"></a>Återuppta intern tråd

#### <a name="internal-thread-resume"></a>Återuppta intern tråd

**Ikon** ![ Ikon för internt tråd-CV](./media/user-guide/tx-events/image1.png)

**Beskrivning**

Den här händelsen representerar den interna bearbetningen i ThreadX som återupptar en tråd för körning. Om den angivna tråden har högst prioritet och preemption-threshold inte blockerar körningen börjar systemet köra den nya tråden.

**Informationsfält**

- Informationsfält 1: Pekare till tråden som återupptas.
- Informationsfält 2: Föregående tillstånd för tråden som återupptas, enligt följande:

  |  Trådtillstånd                     | Värde        |
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

- Informationsfält 3: Stackpekarvärde under anropet. 
- Informationsfält 4: Pekare till nästa tråd med näst högsta prioritet att köra.

### <a name="internal-thread-suspend"></a>Pausa intern tråd

#### <a name="internal-thread-suspend"></a>Pausa intern tråd

**Ikon** ![ Pausikon för intern tråd](./media/user-guide/tx-events/image2.png)

**Beskrivning**

Den här händelsen representerar den interna bearbetningen i ThreadX som pausar körningen av en tråd. Den näst högsta prioritetstråden som är redo för körning placeras i det fjärde informationsfältet. Om det här värdet är NULL finns det ingen annan tråd som är redo för körning och systemet är inaktivt.

**Informationsfält**

- Informationsfält 1: Pekare till tråden som pausas.
- Informationsfält 2: Nytt tillstånd för tråden som pausas enligt följande:

  |  Trådtillstånd                     | Värde        |
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

- Informationsfält 3: Stackpekarvärde under anropet. Informationsfält 4: Pekare till nästa tråd med näst högsta prioritet att köra. Om NULL är systemet inaktivt.

### <a name="interrupt-service-routine-isr-enter"></a>Avbryt tjänstrutin (ISR) ange 

#### <a name="enter-isr"></a>Ange ISR 

**Ikon** ![ Ange I S R-ikon](./media/user-guide/tx-events/image3.png)

**Beskrivning**

Den här händelsen representerar att en ISR (Interrupt Service Routine) matas in i programmet. Avbrottstjänstens rutinkörning fortsätter tills ISR-avslutshändelsen äger rum.

**Informationsfält**

- Informationsfält 1: Stackpekarvärde under anropet.
- Informationsfält 2: Programdefinierat ISR-nummer (valfritt).
- Informationsfält 3: Kapslat avbrottsantal.
- Informationsfält 4: Inaktiveringsflagga för intern avstängning.

### <a name="interrupt-service-routine-isr-exit"></a>Avbryta ISR-avslut (Service Routine) 

#### <a name="exit-isr"></a>Avsluta ISR

**Ikon** ![ Ikonen Avsluta I SR](./media/user-guide/tx-events/image4.png)

**Beskrivning**

Den här händelsen representerar att en ISR (Interrupt Service Routine) avslutas i programmet.

**Informationsfält**

- Informationsfält 1: Stackpekarvärde under anropet.
- Informationsfält 2: Programdefinierat ISR-nummer (valfritt).
- Informationsfält 3: Kapslat avbrottsantal.
- Informationsfält 4: Inaktiveringsflagga för intern avstängning.

### <a name="internal-time-slice"></a>Intern tidssegment

#### <a name="internal-time-slice"></a>Intern tidssegment

**Ikon** ![ Ikon för internt tidssegment](./media/user-guide/tx-events/image5.png)

**Beskrivning**

Den här händelsen representerar den interna bearbetningen i ThreadX som utför åtgärden för ett tidssegment. Nästa tråd med samma prioritet placeras i det första informationsfältet. Om det här värdet är samma som den aktuella tråden utfördes ingen tidssegment.

- Informationsfält 1: Pekare till nästa tråd som ska köras.
- Informationsfält 2: Kapslat avbrottsantal.
- Informationsfält 3: Inaktiveringsflagga för intern avstängning.
- Informationsfält 4: Stackpekarvärde under anropet.

### <a name="running"></a>Körs

#### <a name="running-in-context"></a>Köra i kontext

**Ikon** ![ Ikonen Körs](./media/user-guide/tx-events/image6.png)

**Beskrivning**

Den här händelsen representerar körning i en trådkontext eller ett inaktivt system. Den används för att illustrera efterföljande ändringar i kontexten som ett resultat av ett avbrott.

**Informationsfält**
- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="block-allocate"></a>Blockera allokera 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**Ikon** ![ Ikonen Blockera allokera](./media/user-guide/tx-events/image7.png)

**Beskrivning**

Den här händelsen representerar allokering av ett minnesblock via tx_block_allocate. Om det lyckas returneras adressen till det allokerade blocket i det andra informationsfältet.

**Informationsfält**
- Informationsfält 1: Pekare till motsvarande blockpool.
- Informationsfält 2: Pekare till det minnesblock som returneras (om det lyckas).
- Informationsfält 3: Väntealternativet som anges till tx_block_allocate anropet.
- Informationsfält 4: Återstående tillgängliga block i poolen efter den här allokeringen.

### <a name="block-pool-create"></a>Skapa blockpool

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**Ikon** ![ Ikonen Skapa poolblock](./media/user-guide/tx-events/image8.png)

**Beskrivning**

Den här händelsen representerar skapandet av en minnesblockpool via tx_block_pool_create.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande blockpoolskontrollblock.
- Informationsfält 2: Pekare till poolens startminnesområde.
- Informationsfält 3: Antalet block i poolen. Informationsfält 4: Storleken på varje block i poolen i byte.

### <a name="block-pool-delete"></a>Blockera borttagning av pool

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**Ikon** ![ Ikonen Blockera borttagning av pool](./media/user-guide/tx-events/image9.png)

**Beskrivning**

Den här händelsen representerar borttagning av en minnesblockpool via tx_block_pool_delete.

**Informationsfält**

- Informationsfält 1: Pekare till blockpoolens kontrollblock.
- Informationsfält 2: Stack pekarvärde under anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="block-pool-information-get"></a>Hämta information om blockpooler 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**Ikon** ![ Hämta-ikonen Blockera poolinformation](./media/user-guide/tx-events/image10.png)

**Beskrivning**

Den här händelsen representerar att hämta information om en minnesblockpool via tx_block_pool_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till blockpoolens kontrollblock.
- Informationsfält 2: Stack pekarvärde under anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="block-pool-performance-information-get"></a>Hämta information om blockpoolsprestanda

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**Ikon** ![ Hämta ikon för att blockera poolprestanda](./media/user-guide/tx-events/image11.png)

**Beskrivning**

Den här händelsen representerar att få prestandainformation om en minnesblockpool via tx_block_pool_performance_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till blockpoolens kontrollblock.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="block-pool-performance-system-information-get"></a>Block Pool Performance Systeminformation Get

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**Ikon** ![ Hämta ikon för blockpoolsprestandasystem](./media/user-guide/tx-events/image12.png)

**Beskrivning**

Den här händelsen representerar att få prestandainformation om alla minnesblockpooler via tx_block_pool_performance_system_info_get.

**Informationsfält**
- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="block-pool-prioritize"></a>Prioritera blockpool

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**Ikon** ![ Prioritetsikonen Blockera pool](./media/user-guide/tx-events/image13.png)

**Beskrivning**

Den här händelsen representerar att placera den högstprioritetsavstängda tråden framför blockeringslistan för blockpoolen. Om detta görs innan du anropar tx_block_release tråd med högst prioritet inaktiveras det utgivna blocket.

**Informationsfält**
- Informationsfält 1: Pekare för minnesblockpool.
- Informationsfält 2: Antal trådar som pausas i den här blockpoolen.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="block-release"></a>Blockera version 

#### <a name="tx_block_release"></a>tx_block_release

**Ikon** ![ Ikonen Blockera version](./media/user-guide/tx-events/image14.png)

**Beskrivning**

Den här händelsen representerar lanserar ett tidigare allokerat block tillbaka till blockpoolen.

**Informationsfält**

- Informationsfält 1: Pekare för minnesblockpool.
- Informationsfält 2: Pekare för att blockera till lansering.
- Informationsfält 3: Antal trådar som pausas i den här blockpoolen.
- Informationsfält 4: Stack pekare vid tidpunkten för anropet.

### <a name="byte-allocate"></a>Allokera byte 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**Ikon** ![ Ikon för bytealaler](./media/user-guide/tx-events/image15.png)

**Beskrivning**

Den här händelsen representerar allokering av minne via tx_byte_allocate. Om det lyckas returneras adressen till det allokerade minnet i det andra informationsfältet.

**Informationsfält**
- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Pekare till det returnerade minnet (om det lyckas).
- Informationsfält 3: Antal byte som begärts. Informationsfält 4: Väntealternativet som anges till tx_byte_allocate anropet.

### <a name="byte-pool-create"></a>Skapa bytepool

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**Ikon** ![ Ikon för att skapa bytepool](./media/user-guide/tx-events/image16.png)

**Beskrivning**

Den här händelsen representerar skapandet av en bytepool via tx_byte_pool_create.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Pekare till början av minnesområdet. Informationsfält 3: Antal byte i bytepoolen.
- Informationsfält 4: Stackpekaren vid tidpunkten för anropet.

### <a name="byte-pool-delete"></a>Ta bort bytepool 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**Ikon** ![ Ikonen Ta bort bytepool](./media/user-guide/tx-events/image17.png)

**Beskrivning**

Den här händelsen representerar borttagning av en bytepool via tx_byte_pool_delete.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Stackpekaren vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="byte-pool-information-get"></a>Hämta information om bytepool

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikon** ![ Hämta ikon för bytepoolsinformation](./media/user-guide/tx-events/image18.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om bytepoolen via tx_byte_pool_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="byte-pool-performance-info-get"></a>Information om bytepoolsprestanda hämta 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ikon** ![ Hämta ikon för prestandainformation för bytepool](./media/user-guide/tx-events/image19.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestandainformation för bytepoolen via tx_byte_pool_performance_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="byte-pool-performance-system-info-get"></a>Hämta information om prestandasystem för bytepooler 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**Ikon** ![ Ikon för systeminformation om bytepoolsprestanda](./media/user-guide/tx-events/image20.png)

**Beskrivning**

Den här händelsen representerar hämtning av systeminformation om bytepoolsprestanda via tx_byte_pool_performance_system_info_get.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="byte-pool-prioritize"></a>Prioritera bytepool

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**Ikon** ![ Prioritera ikon för bytepool](./media/user-guide/tx-events/image21.png)

**Beskrivning**

Den här händelsen representerar prioritering av bytepoolens stängningslista via tx_byte_pool_prioritize.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Antalet trådar som för närvarande pausas i bytepoolen.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="byte-release"></a>Byte-version

#### <a name="tx_byte_release"></a>tx_byte_release

**Ikon** ![ Ikon för byte-version](./media/user-guide/tx-events/image22.png)

**Beskrivning**

Den här händelsen representerar att frigöra ett minnesblock som allokerats från en bytepool via tx_byte_release.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande bytepool.
- Informationsfält 2: Pekare till tidigare allokerat bytepoolminne.
- Informationsfält 3: Antal trådar som pausas på den här bytepoolen.
- Informationsfält 4: Antal tillgängliga byte minne.

### <a name="event-flags-create"></a>Skapa händelseflaggor 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**Ikon** ![ Ikonen Skapa händelseflaggor](./media/user-guide/tx-events/image23.png)

**Beskrivning**

Den här händelsen representerar skapandet av en ny händelseflaggasgrupp via tx_event_flags_create.

**Informationsfält** 
- Informationsfält 1: Pekare till händelseflaggor gruppkontrollblock.
- Informationsfält 2: Stack pekare vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="event-flags-delete"></a>Ta bort händelseflaggor 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**Ikon** ![ Ikonen Ta bort händelseflaggor](./media/user-guide/tx-events/image24.png)

**Beskrivning**

Den här händelsen representerar borttagning av en händelseflaggor via tx_event_flags_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till händelseflaggor.
- Informationsfält 2: Stack pekare vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="event-flags-get"></a>Event Flags Get 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**Ikon** ![ Ikon för händelseflaggor gt](./media/user-guide/tx-events/image25.png)

**Beskrivning**

Den här händelsen representerar hämtning av händelseflaggor från en befintlig händelseflaggor via tx_event_flags_get.

**Informationsfält**

- Informationsfält 1: Pekare till händelseflaggor.
- Informationsfält 2: Händelseflaggor begärda.
- Informationsfält 3: Händelseflaggor som för närvarande anges i gruppen.
- Informationsfält 4: Alternativet som begärdes för händelseflaggorna hämtar.

### <a name="event-flags-information-get"></a>Information om händelseflaggor hämta

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**Ikon** ![ Information om händelseflaggor – hämta ikon](./media/user-guide/tx-events/image26.png)

**Beskrivning**

Den här händelsen representerar hämtning av information om en befintlig händelseflaggasgrupp via tx_event_flags_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till händelseflaggor.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="event-flags-performance-information-get"></a>Prestandainformation för händelseflaggor hämta 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**Ikon** ![ Ikonen Hämta prestandainformation för händelseflaggor](./media/user-guide/tx-events/image27.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestandainformation om en befintlig händelseflaggor via tx_event_flags_performance_info_get.

**Informationsfält** 
- Informationsfält 1: Pekare till händelseflaggor.
- Informationsfält 2: Används inte
- Informationsfält 3: Används inte
- Informationsfält 4: Används inte

### <a name="event-flags-performance-system-info-get"></a>Event Flags Performance System Info Get

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**Ikon** ![ Ikonen Hämta information om prestandasystem för händelseflaggor](./media/user-guide/tx-events/image28.png)

**Beskrivning**

Den här händelsen representerar hämtning av prestandainformation om en befintlig händelseflaggor via tx_event_flags_performance_system_info_get.

**Informationsfält**
- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="event-flags-set"></a>Ange händelseflaggor 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**Ikon** ![ Ikon för uppsättning av händelseflaggor](./media/user-guide/tx-events/image29.png)

**Beskrivning**

Den här händelsen representerar flaggor för inställning (eller rensning) i en befintlig händelseflaggor via tx_event_flags_set.

**Informationsfält**

- Informationsfält 1: Pekare till händelseflaggor.
- Informationsfält 2: Händelseflaggor som ska anges (eller rensas).
- Informationsfält 3: Alternativet AND eller OR event flag.
- Informationsfält 4: Antal trådar som pausas i händelseflaggan.

### <a name="event-flags-set-notify"></a>Meddelande om händelseflaggor

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**Ikon** ![ Händelseflaggor ange av meddela-ikon](./media/user-guide/tx-events/image30.png)

**Beskrivning**

Den här händelsen representerar registrering av ett återanrop av meddelanden för en åtgärd för händelseflaggan i en befintlig händelseflaggor via tx_event_flags_set_notify.

**Informationsfält**

- Informationsfält 1: Pekare till händelseflaggor.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="interrupt-control"></a>Avbrottskontroll 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**Ikon** ![ Ikon för avbrottskontroll](./media/user-guide/tx-events/image31.png)

**Beskrivning**

Den här händelsen representerar ändring av processorns avbrottslåsningsstatus via tx_interrupt_control.

**Informationsfält**

- Informationsfält 1: Ny avbrottsstatus.
- Informationsfält 2: Stack pekare vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="mutex-create"></a>Mutex–skapa 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**Ikon** ![ Ikon för att skapa Mutex](./media/user-guide/tx-events/image32.png)

**Beskrivning**

Den här händelsen representerar skapandet av en mutex via tx_mutex_create.

**Informationsfält**

- Informationsfält 1: Pekare till mutex-kontrollblock.
- Informationsfält 2: Alternativ för prioritetsarv
- (TX_INHERIT eller TX_NO_INHERIT).
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="mutex-delete"></a>Mutex Delete 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**Ikon** ![ Ta bort mutex-ikon](./media/user-guide/tx-events/image33.png)

**Beskrivning**

Den här händelsen representerar borttagning av en mutex via tx_mutex_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till mutex.
- Informationsfält 2: Stack pekare vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="mutex-get"></a>Mutex Get 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**Ikon** ![ Mutex-hämta-ikon](./media/user-guide/tx-events/image34.png)

**Beskrivning**

Den här händelsen representerar att du får en mutex via tx_mutex_get.

**Informationsfält**

- Informationsfält 1: Pekare till mutex.
- Informationsfält 2: Väntealternativet som anges till tx_mutex_get anropet.
- Informationsfält 3: Pekare till tråd som äger mutex (NULL antyder att mutex inte ägs).
- Informationsfält 4: Antal gånger som den äger tråden har anropat tx_mutex_get.

### <a name="mutex-information-get"></a>Mutex-information Hämta

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**Ikon** ![ Ikon för att hämta Mutex-information](./media/user-guide/tx-events/image35.png)

**Beskrivning**

Den här händelsen representerar hämtning av mutex-information via tx_mutex_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till mutex.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="mutex-performance-information-get"></a>Information om Mutex-prestanda hämta 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**Ikon** ![ Information om Mutex-prestanda – hämta ikon](./media/user-guide/tx-events/image36.png)

**Beskrivning**

Den här händelsen representerar hämtning av mutex-prestandainformation via tx_mutex_performance_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till mutex.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="mutex-performance-system-info-get"></a>Information om Mutex-prestandasystem – Hämta

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**Ikon** ![ Ikon för att hämta information om Mutex-prestandasystem](./media/user-guide/tx-events/image37.png)

**Beskrivning**

Den här händelsen representerar hämtning av mutex-systemprestandainformation via tx_mutex_performance_system_info_get.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="mutex-prioritize"></a>Mutex Prioritize 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**Ikon** ![ Ikonen För att prioritera Mutex](./media/user-guide/tx-events/image38.png)

**Beskrivning**

Den här händelsen representerar prioritering av mutex-stängningslistan via tx_mutex_prioritize.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande mutex.
- Informationsfält 2: Antalet trådar som för närvarande pausas på mutex.
- Informationsfält 3: Stackpekare vid anrop.
- Informationsfält 4: Används inte.

### <a name="mutex-put"></a>Mutex Put 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**Ikon** ![ Mutex-put-ikon](./media/user-guide/tx-events/image39.png)

**Beskrivning**

Den här händelsen representerar lanserar en tidigare ägd mutex via tx_mutex_put.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande mutex.
- Informationsfält 2: Pekare av tråden som äger mutex.
- Informationsfält 3: Antal utestående mutex get-begäranden.
- Informationsfält 4: Stackpekare vid anrop.

### <a name="queue-create"></a>Skapa kö 

#### <a name="tx_queue_create"></a>tx_queue_create

**Ikon** ![ Ikon för att skapa kö](./media/user-guide/tx-events/image40.png)

**Beskrivning**

Den här händelsen representerar skapandet av en meddelandekö via tx_queue_create.

**Informationsfält**

- Informationsfält 1: Pekare till kökontrollblock.
- Informationsfält 2: Meddelandestorlek – i termer av 32-bitars ord.
- Informationsfält 3: Pekare för att starta köminnesområdet.
- Informationsfält 4: Antal byte i köminnesområdet.

### <a name="queue-delete"></a>Ta bort kö 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**Ikon** ![ Ikonen Ta bort kö](./media/user-guide/tx-events/image41.png)

**Beskrivning**

Den här händelsen representerar borttagning av en kö via tx_queue_delete.

**Informationsfält**

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Stackpekare vid anrop.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="queue-flush"></a>Queue Flush 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**Ikon** ![ Ikon för att tömma köer](./media/user-guide/tx-events/image42.png)

**Beskrivning**

Den här händelsen representerar tömning (rensa allt köinnehåll) i en kö via tx_queue_flush.

**Informationsfält**

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Stackpekare vid anrop.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="queue-front-send"></a>Queue Front Send 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**Ikon** ![ Ikonen För att skicka i kö fram](./media/user-guide/tx-events/image43.png)

**Beskrivning**

Den här händelsen representerar sändning av ett meddelande framför en kö via tx_queue_front_send.

**Informationsfält**

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Pekare till meddelandestart.
- Informationsfält 3: Väntealternativet har angetts till
- tx_queue_front_send anropa.
- Informationsfält 4: Antalet meddelanden som redan har förts i kontakt.

### <a name="queue-information-get"></a>Hämta köinformation 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**Ikon** ![ Hämta ikon för köinformation](./media/user-guide/tx-events/image44.png)

**Beskrivning**

Den här händelsen representerar att hämta information om en kö via tx_queue_info_get.

**Informationsfält** 
- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="queue-performance-info-get"></a>Information om köprestanda hämta 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**Ikon** ![ Hämta ikon för information om köprestanda](./media/user-guide/tx-events/image45.png)

**Beskrivning**

Den här händelsen representerar att hämta prestandainformation om en kö via tx_queue_performance_info_get.

**Informationsfält** 

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="queue-performance-system-info-get"></a>Information om köprestandasystem – Hämta 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**Ikon** ![ Hämta ikon för systeminformation för köprestanda](./media/user-guide/tx-events/image46.png)

**Beskrivning**

Den här händelsen representerar att hämta systemprestandainformation om alla köer i systemet.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="queue-prioritize"></a>Köprioritera 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**Ikon** ![ Köprioriteringsikon](./media/user-guide/tx-events/image47.png)

**Beskrivning**

Den här händelsen representerar prioritering av köns stängningslista via tx_queue_prioritize.

**Informationsfält** 

- Informationsfält 1: Pekare till motsvarande kö.
- Informationsfält 2: Antalet trådar som för närvarande pausas i kön.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

#### <a name="queue-receive"></a>Kö ta emot 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**Ikon** ![ Ikon för kö mottagning](./media/user-guide/tx-events/image48.png)

**Beskrivning**

Den här händelsen representerar mottagandet av ett meddelande från en kö via tx_queue_receive.

**Informationsfält** 

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Pekare till mål för meddelande. Informationsfält 3: Väntealternativet anges till anropet.
- Informationsfält 4: Antalet meddelanden som för närvarande är i kö.

### <a name="queue-send"></a>Skicka i kö 

#### <a name="tx_queue_send"></a>tx_queue_send

**Ikon** ![ Ikonen För att skicka kö](./media/user-guide/tx-events/image49.png)

**Beskrivning**

Den här händelsen representerar att ett meddelande skickas till en kö via tx_queue_send.

**Informationsfält** 

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Pekare till meddelande.
- Informationsfält 3: Väntealternativet anges till anropet.
- Informationsfält 4: Antalet meddelanden som för närvarande är i kö.

### <a name="queue-send-notify"></a>Queue Send Notify 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**Ikon** ![ Meddelandeikon för att skicka i kö](./media/user-guide/tx-events/image50.png)

**Beskrivning**

<p>Den här händelsen representerar registrering av ett återanrop via tx_queue_send_notify som anropas när ett meddelande skickas till en kö.

**Informationsfält** 

- Informationsfält 1: Pekare till kö.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="semaphore-ceiling-put"></a>Semaphore Ceiling Put 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**Ikon** ![ Put-ikon för semaphore-tak](./media/user-guide/tx-events/image51.png)

**Beskrivning**

Den här händelsen representerar en semafor via tx_semaphore_ceiling_put. Detta skiljer sig tx_semaphore_put eftersom det högsta värdet för semaphore undersöks så att put-åtgärden inte får överskrida det högsta värdet eller taket.

**Informationsfält**

- Informationsfält 1: Pekare till semaphore.
- Informationsfält 2: Aktuellt semaforantal.
- Informationsfält 3: Antal trådar som pausas på semaphore.
- Informationsfält 4: Takgräns som anges för anropet.

#### <a name="semaphore-create"></a>Skapa Semaphore 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**Ikon** ![ Ikonen För att skapa Semaphore](./media/user-guide/tx-events/image52.png)

**Beskrivning**

Den här händelsen representerar skapandet av en semafor via tx_semaphore_create.

**Informationsfält**

- Informationsfält 1: Pekare till semaphore-kontrollblock.
- Informationsfält 2: Inledande semaforantal.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="semaphore-delete"></a>Ta bort semaphore 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**Ikon** ![ Ta bort semaphore-ikon](./media/user-guide/tx-events/image53.png)

**Beskrivning**

Den här händelsen representerar borttagning av en semafor via tx_semaphore_delete.

**Informationsfält**

- Informationsfält 1: Pekare till semaphore.
- nfo Fält 2: Stack pekare vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="semaphore-get"></a>Semaphore Get 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**Ikon** ![ Ikonen Hämta semaphore](./media/user-guide/tx-events/image54.png)

**Beskrivning**

Den här händelsen representerar att få en semaphore via tx_semaphore_get.

**Informationsfält**

- Informationsfält 1: Pekare till semaphore.
- Informationsfält 2: Väntealternativet anges till anropet.
- Informationsfält 3: Aktuellt semaphore-antal.
- Informationsfält 4: Stack pekare vid tidpunkten för anropet.

### <a name="semaphore-information-get"></a>Semaphore Information Get 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**Ikon** ![ Hämta information om Semaphore](./media/user-guide/tx-events/image55.png)

**Beskrivning**

Den här händelsen representerar att få information om en semafor via tx_semaphore_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till semaphore.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="semaphore-performance-info-get"></a>Semaphore Performance Info Get 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**Ikon** ![ Hämta ikon för Semaphore-prestandainformation](./media/user-guide/tx-events/image56.png)

**Beskrivning**

Den här händelsen representerar att hämta prestandainformation om en semafor via tx_semaphore_performance_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till semaphore.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="semaphore-performance-system-info"></a>Semaphore Performance System Info 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**Ikon** ![ Informationsikon för Semaphore-prestandasystem](./media/user-guide/tx-events/image57.png)

**Beskrivning**

Den här händelsen representerar att hämta prestandainformation om alla semaforer i systemet via tx_semaphore_performance_system_info_get.

**Informationsfält** 

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="semaphore-prioritize"></a>Prioritera Semaphore 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**Ikon** ![ Ikonen Prioritera Semaphore](./media/user-guide/tx-events/image58.png)

**Beskrivning**

Den här händelsen representerar prioritering av semaphores uppstängningslista via tx_semaphore_prioritize.

**Informationsfält**

- Informationsfält 1: Pekare till motsvarande semafor.
- Informationsfält 2: Antalet trådar som för närvarande pausas på semaphore.
- Informationsfält 3: Stackpekare vid anrop.
- Informationsfält 4: Används inte.

### <a name="semaphore-put"></a>Semaphore Put 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**Ikon** ![ Semaphore put-ikon](./media/user-guide/tx-events/image59.png)

**Beskrivning**

Den här händelsen lanserar en semaphore-instans via tx_semaphore_put.

**Informationsfält** 

- Informationsfält 1: Pekare till motsvarande semafor. Informationsfält 2: Aktuellt semaphore-antal.
- Informationsfält 3: Antal trådar som pausas på semaphore.
- Informationsfält 4: Stackpekare vid anrop.

### <a name="semaphore-put-notify"></a>Semaphore Put Notify 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**Ikon** ![ Aviseringsikon för Semaphore put](./media/user-guide/tx-events/image60.png)

**Beskrivning**

Den här händelsen representerar registrering av ett återanrop via tx_semaphore_put_notify som anropas när en semaphore-instans läggs till.

**Informationsfält** 

- Informationsfält 1: Pekare till semaphore.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-create"></a>Skapa tråd 

#### <a name="tx_thread_create"></a>tx_thread_create

**Ikon** ![ Ikon för att skapa tråd](./media/user-guide/tx-events/image61.png)

**Beskrivning**

Den här händelsen representerar skapandet av en tråd via tx_thread_create.

**Informationsfält**

- Informationsfält 1: Pekare till trådkontrollblock.
- Informationsfält 2: Trådprioritet.
- Informationsfält 3: Stackpekare för tråd.
- nfo Field 4: Storlek på stack i byte.

### <a name="thread-delete"></a>Ta bort tråd 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**Ikon** ![ Ikonen Ta bort tråd](./media/user-guide/tx-events/image62.png)

**Beskrivning**

Den här händelsen representerar borttagning av en tråd via tx_thread_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Stackpekare vid anrop.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-entryexit-notify"></a>Meddelande om trådinmatning/avslut 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**Ikon** ![ Meddelandeikon för trådinmatning/avslut](./media/user-guide/tx-events/image63.png)

**Beskrivning**

Den här händelsen representerar registrering av ett återanrop via tx_thread_entry_exit_notify som anropas när en tråd anges eller avslutas.

**Informationsfält** 

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Trådtillstånd vid tidpunkten för registreringen.
- Informationsfält 3: Pekare till stack vid anrop.
- Informationsfält 4: Används inte.

#### <a name="thread-identify"></a>Tråd-identifiera 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**Ikon** ![ Ikon för tråd-identifiering](./media/user-guide/tx-events/image64.png)

**Beskrivning**

Den här händelsen representerar att hämta den aktuella tråd pekaren via tx_thread_identify.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-information-get"></a>Trådinformation hämta 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**Ikon** ![ Ikonen Hämta trådinformation](./media/user-guide/tx-events/image65.png)

**Beskrivning**

Den här händelsen representerar att hämta information om den angivna tråden via tx_thread_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Trådtillstånd vid anrop.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

#### <a name="thread-performance-information-get"></a>Hämta trådprestandainformation 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**Ikon** ![ Ikon för att hämta trådprestandainformation](./media/user-guide/tx-events/image66.png)

**Beskrivning**

Den här händelsen representerar att få prestandainformation om den angivna tråden via tx_thread_performance_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Trådtillstånd vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-performance-system-info-get"></a>Thread Performance System Info Get 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**Ikon** ![ Ikonen Hämta information om trådprestandasystem](./media/user-guide/tx-events/image67.png)

**Beskrivning**

Den här händelsen representerar att få prestandainformation om alla trådar via tx_thread_performance_system_info_get.

**Informationsfält** 

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-preemption-change"></a>Ändring av trådförseing 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**Ikon** ![ Ikon för ändring av trådförsening](./media/user-guide/tx-events/image68.png)

**Beskrivning**

Den här händelsen representerar ändring av en tråds tröskel för avförbrukning via tx_thread_preemption_change.

**Informationsfält** 

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Nytt tröskelvärde för avspärrning.
- Informationsfält 3: Föregående tröskelvärde för avspärrning.
- Informationsfält 4: Trådens tillstånd vid tidpunkten för anropet.

### <a name="thread-priority-change"></a>Ändring av trådprioritet 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**Ikon** ![ Ikon för ändring av trådprioritet](./media/user-guide/tx-events/image69.png)

**Beskrivning**

Den här händelsen representerar ändring av en tråds prioritet via tx_thread_priority_change.

- Informationsfält 
- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Ny prioritet.
- Informationsfält 3: Föregående prioritet.
- Informationsfält 4: Trådens tillstånd vid tidpunkten för anropet.

### <a name="thread-relinquish"></a>Trådrelinquish 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**Ikon** ![ Ikonen för att ta bort trådar](./media/user-guide/tx-events/image70.png)

**Beskrivning**

Den här händelsen representerar avslut av processorn från en tråd via tx_thread_relinquish.

**Informationsfält**

- Informationsfält 1: Stack pekare vid tidpunkten för anropet.
- Informationsfält 2: Pekare till nästa tråd som ska köras.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-reset"></a>Trådåterställning 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**Ikon** ![ Ikon för trådåterställning](./media/user-guide/tx-events/image71.png)

**Beskrivning**

Den här händelsen representerar återställning av en slutförd eller avslutad tråd via tx_thread_reset.

**Informationsfält**

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

#### <a name="thread-resume"></a>Tråd-ÅTERUPPTA 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**Ikon** ![ Ikon för tråd-CV](./media/user-guide/tx-events/image72.png)

**Beskrivning**

Den här händelsen representerar att en pausad tråd återupptas via tx_thread_resume.

**Informationsfält**

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="thread-sleep"></a>Tråd strömsparläge 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**Ikon** ![ Ikon för strömsparläge för tråd](./media/user-guide/tx-events/image73.png)

**Beskrivning**

Den här händelsen innebär att den aktuella tråden pausas för ett angivet antal timer tick via tx_thread_sleep.

**Informationsfält**

- Informationsfält 1: Antal tick att pausa för.
- Informationsfält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="thread-stack-error-notify"></a>Meddelande om fel i trådstack 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**Ikon** ![ Meddelandeikon för fel i trådstack](./media/user-guide/tx-events/image74.png)

**Beskrivning**

Den här händelsen representerar registrering av en meddelanderutin för trådstacksfel via tx_thread_stack_error_notify_event.

**Informationsfält** 

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="thread-suspend"></a>Tråd pausa 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**Ikon** ![ Ikonen För att pausa trådar](./media/user-guide/tx-events/image75.png)

**Beskrivning**

Den här händelsen representerar att en tråd pausas via tx_thread_suspend.

**Informationsfält** 

- Informationsfält 1: Pekare till tråd för att pausa.
- Informationsfält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informationsfält 3: Stack pekare vid tidpunkten för anropet.
- Informationsfält 4: Används inte.

### <a name="thread-terminate"></a>Tråd avslutas 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**Ikon** ![ Ikonen Avsluta tråd](./media/user-guide/tx-events/image76.png)

**Beskrivning**

Den här händelsen representerar avslutande av en tråd via tx_thread_terminate.

**Informationsfält** 

- Informationsfält 1: Pekare till tråd för att avsluta.
- Informationsfält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informationsfält 3: Stackpekare vid anrop.
- Informationsfält 4: Används inte.

### <a name="thread-time-slice-change"></a>Ändring Time-Slice tråd 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**Ikon** ![ Ikon för ändring av trådtidssegment](./media/user-guide/tx-events/image77.png)

**Beskrivning**

Den här händelsen representerar ändring av en tråds tidssegment via tx_thread_time_slice_change.

**Informationsfält**

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Ny tidssegment.
- Informationsfält 3: Föregående tidssegment.
- Informationsfält 4: Används inte.

### <a name="thread-wait-abort"></a>Trådvänte abort 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**Ikon** ![ Ikon för väntande av tråd](./media/user-guide/tx-events/image78.png)

**Beskrivning**

Den här händelsen representerar att en tråds brytning avbryts via tx_thread_wait_abort.

**Informationsfält**

- Informationsfält 1: Pekare till tråd.
- Informationsfält 2: Trådens tillstånd vid tidpunkten för anropet.
- Informationsfält 3: Stackpekare vid anrop.
- Informationsfält 4: Används inte.

### <a name="time-get"></a>Time Get 

#### <a name="tx_time_get"></a>tx_time_get

**Ikon** ![ Ikonen För tids get](./media/user-guide/tx-events/image79.png)

**Beskrivning**

Den här händelsen representerar att det aktuella antalet timer tick skickas via tx_time_get.

**Informationsfält**

- Informationsfält 1: Aktuellt antal timer tick.
- Informationsfält 2: Stackpekare vid anrop.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="time-set"></a>Tidsuppsättning 

#### <a name="tx_time_set"></a>tx_time_set

**Ikon** ![ Ikon för tidsuppsättning](./media/user-guide/tx-events/image80.png)

**Beskrivning**

Den här händelsen representerar inställningen av det aktuella antalet timer tick via tx_time_set.

**Informationsfält**

- Informationsfält 1: Nytt antal timer tick.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="timer-activate"></a>Aktivera timer 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**Ikon** ![ Aktiveringsikon för timer](./media/user-guide/tx-events/image81.png)

**Beskrivning**

Den här händelsen representerar aktivering av den angivna timern via tx_timer_activate.

**Informationsfält**

- Informationsfält 1: Pekare till timer.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="timer-change"></a>Ändring av timer 

#### <a name="tx_timer_change"></a>tx_timer_change

**Ikon** ![ Ikon för timerändring](./media/user-guide/tx-events/image82.png)

**Beskrivning**

Den här händelsen representerar ändring av den angivna timern via tx_timer_change.

**Informationsfält**

- Informationsfält 1: Pekare till timer.
- Informationsfält 2: Inledande förfallotid tick.
- Informationsfält 3: Tids tick för omplanerade förfallotid.
- Informationsfält 4: Används inte.

### <a name="timer-create"></a>Skapa timer 

#### <a name="tx_timer_create"></a>tx_timer_create

**Ikon** ![ Ikon för att skapa timer](./media/user-guide/tx-events/image83.png)

**Beskrivning**

Den här händelsen representerar skapandet av en timer via tx_timer_create.

**Informationsfält**

- Informationsfält 1: Pekare till timerkontrollblock.
- Informationsfält 2: Inledande förfallotid tick.
- Informationsfält 3: Tids tick för omplanerade förfallotid.
- Informationsfält 4: Automatiskt aktivera värde – antingen TX_AUTO_ACTIVATE (1) eller TX_NO_ACTIVATE (0).

### <a name="timer-deactivate"></a>Timer– inaktivera 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**Ikon** ![ Inaktivera timerikon](./media/user-guide/tx-events/image84.png)

**Beskrivning**

Den här händelsen representerar inaktivering av en timer via tx_timer_deactivate.

**Informationsfält**

- Informationsfält 1: Pekare till timer.
- Informationsfält 2: Stackpekare vid anrop.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="timer-delete"></a>Ta bort timer 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**Ikon** ![ Borttagningsikon för timer](./media/user-guide/tx-events/image85.png)

**Beskrivning**

Den här händelsen representerar borttagning av en timer via tx_timer_delete.

**Informationsfält** 

- Informationsfält 1: Pekare till timer.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="timer-information-get"></a>Hämta information om timer 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**Ikon** ![ Ikon för timer för att hämta information](./media/user-guide/tx-events/image86.png)

**Beskrivning**

Den här händelsen representerar att timerinformation skickas via tx_timer_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till timer.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="timer-performance-information-get"></a>Information om timerprestanda hämta 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**Ikon** ![ Information om timerprestanda – hämta ikon](./media/user-guide/tx-events/image87.png)

**Beskrivning** 

Den här händelsen visar hur du hämtar information om timerprestanda via tx_timer_performance_info_get.

**Informationsfält**

- Informationsfält 1: Pekare till timer.
- Informationsfält 2: Stack pekare vid tidpunkten för anropet.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="timer-system-performance-info-get"></a>Information om prestanda för timersystem – Hämta 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**Ikon** ![ Information om timersystemprestanda – hämta ikon](./media/user-guide/tx-events/image88.png)


**Beskrivning** 

Den här händelsen visar hur du hämtar all information om timerprestanda via tx_timer_performance_system_info_get.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.