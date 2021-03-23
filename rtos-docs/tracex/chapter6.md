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
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="f66c1-103">Kapitel 6 – Azure återställnings tider ThreadX trace Events</span><span class="sxs-lookup"><span data-stu-id="f66c1-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="f66c1-104">I det här kapitlet beskrivs Azure återställnings tider ThreadX-händelser.</span><span class="sxs-lookup"><span data-stu-id="f66c1-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="f66c1-105">Lista över händelser och ikoner</span><span class="sxs-lookup"><span data-stu-id="f66c1-105">List of Events and Icons</span></span>

<span data-ttu-id="f66c1-106">Följande är en lista över ThreadX-händelser som visas av TraceX:</span><span class="sxs-lookup"><span data-stu-id="f66c1-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="f66c1-107">**Ikon**</span><span class="sxs-lookup"><span data-stu-id="f66c1-107">**Icon**</span></span>                         | <span data-ttu-id="f66c1-108">**Innebörd**</span><span class="sxs-lookup"><span data-stu-id="f66c1-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![Aktiverings ikon för intern tråd](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="f66c1-110">Återuppta intern tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-110">Internal thread resume</span></span>  |
| ![Inaktivera ikon för intern tråd](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="f66c1-112">Inaktive ring av intern tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-112">Internal thread suspend</span></span> |
| ![Ikon för att avbryta tjänstens rutin retur](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="f66c1-114">Avbrotts service rutin (ISR)-retur</span><span class="sxs-lookup"><span data-stu-id="f66c1-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![Avbrotts ikon för tjänst rutin](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="f66c1-116">Avbryta service rutin (ISR)-avsluta</span><span class="sxs-lookup"><span data-stu-id="f66c1-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![Intern Time-slice-ikon](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="f66c1-118">Intern tid-sektor</span><span class="sxs-lookup"><span data-stu-id="f66c1-118">Internal time-slice</span></span> |
| ![Kör ikon](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="f66c1-120">Körs</span><span class="sxs-lookup"><span data-stu-id="f66c1-120">Running</span></span> |
| ![Ikonen för att blockera pool tilldelning](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="f66c1-122">**Blockera allokering av pool** (*tx_block_allocate*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![Skapa ikon för att blockera pool](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="f66c1-124">**Blockera skapande av pool** (*tx_block_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![Ta bort ikon för borttagning av pool](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="f66c1-126">**Blockera borttagning av pool** (*tx_block_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![Hämta ikon för Hämta pool information](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="f66c1-128">**Blockera pool information get** (*tx_block_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![Blockera prestanda information för pool Hämta con](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="f66c1-130">**Blockera prestanda information för pool Hämta** (*tx_block_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![Hämta ikon för Hämta pool system prestanda information](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="f66c1-132">**Blockera pool system prestanda information get** (*tx_block_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![Prioritets ikon för att blockera pool](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="f66c1-134">**Blockera poolens prioritet** (*tx_block_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![Ikonen blockera att släppa till poolen](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="f66c1-136">**Blockera version till pool** (*tx_block_release*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![Ikon för allokera minne för byte pool](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="f66c1-138">**Byte pool allokera minne** (*tx_byte_allocate*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![Ikon för att skapa byte pool](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="f66c1-140">**Skapa byte-pool** (*tx_byte_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![Borttagnings ikon för byte pool](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="f66c1-142">**Borttagning av byte pool** (*tx_byte_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![Ikon för hämta information om byte pool](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="f66c1-144">**Information om byte pool get** (*tx_byte_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![Ikon för hämta prestanda information för byte-pool](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="f66c1-146">**Hämta prestanda information för byte-pool** (*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![Ikon för Hämta byte i byte pool system prestanda information](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="f66c1-148">**Hämta information om byte pool system prestanda information** (*tx_byte_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![\* Prioritets ikon för byte pool](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="f66c1-150">**Prioritering av byte-pool** (*tx_byte_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![Ikon för att frigöra byte minne](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="f66c1-152">**Byte minnes version till pool** (*tx_byte_release*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![Ikonen Skapa händelse flaggor](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="f66c1-154">**Skapa händelse flaggor** (*tx_event_flags_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![Borttagnings ikon för händelse flaggor](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="f66c1-156">**Ta bort händelse flaggor** (*tx_event_flags_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![Ikonen Hämta händelse flaggor](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="f66c1-158">**Händelse flaggor Hämta** (*tx_event_flags_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![Ikonen Hämta information om händelse flaggor](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="f66c1-160">**Händelse flaggor information get** (*tx_event_flags_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![Händelse flaggor prestanda information Hämta ikon](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="f66c1-162">**Händelse flaggor prestanda information get** (*tx_event_flags_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![Händelse flaggor system prestanda information Hämta ikon](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="f66c1-164">**Händelse flaggor system prestanda information get** (*tx_event_flags_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![Ikonen händelse flaggor uppsättning](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="f66c1-166">**Angivna händelse flaggor** (*tx_event_flags_set*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![Händelse flaggor ange aviserings ikon](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="f66c1-168">**Meddelande om inställd händelse flaggor** (*tx_event_flags_set_notify*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![Avbryt aktivering/inaktivera ikon](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="f66c1-170">**Avbryt aktivering/inaktive ring** (*tx_interrupt_control*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![Ikon för mutex-skapande](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="f66c1-172">**Mutex-skapande** (*tx_mutex_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![Ikon för mutex-borttagning](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="f66c1-174">**Mutex-borttagning** (*tx_mutex_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![Ikon för att hämta mutex](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="f66c1-176">**Mutex get** (*tx_mutex_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![Get-ikon för mutex information](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="f66c1-178">**Mutex information get** (*tx_mutex_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![Ikon för hämta information om mutex-prestanda](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="f66c1-180">**Information om mutex-prestanda Hämta** (*tx_mutex_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![Ikon för att hämta mutex-system prestanda information](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="f66c1-182">**Mutex system prestanda information get** (*tx_mutex_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![Ikon för mutex-prioritet](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="f66c1-184">**Mutex-prioritering** (*tx_mutex_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![Ikon för mutex-placering](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="f66c1-186">**Mutex-placering** (*tx_mutex_put*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![Ikon för att skapa kö](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="f66c1-188">**Skapa kö** (*tx_queue_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![Borttagnings ikon för kö](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="f66c1-190">**Köa borttagning** (*tx_queue_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![Ikon för köa tömning](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="f66c1-192">**Köa rensning** (*tx_queue_flush*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![Ikon för att skicka kön direkt](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="f66c1-194">**Kö-sändning** (*tx_queue_front_send*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![Hämta ikon för köa information](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="f66c1-196">**Köa information get** (*tx_queue_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![Hämta ikon för köns prestanda information](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="f66c1-198">**Hämta prestanda information för kö** (*tx_queue_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![Hämta ikon för prestanda information för Queue system](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="f66c1-200">**Hämta information om köa system prestanda information** (*tx_queue_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![Ikon för köa prioritet](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="f66c1-202">**Prioritet för kön** (*tx_queue_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![Ikon för mottagnings meddelande i kö](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="f66c1-204">**Mottagnings meddelande i kö** (*tx_queue_receive*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="f66c1-206">**Köa sändnings meddelande** (*tx_queue_send*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="f66c1-208">**Köa sändnings meddelande** (*tx_queue_send_notify*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![Ikon för Semaforens tak placering](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="f66c1-210">**Utplacering av semafor-tak** (*tx_semaphore_ceiling_put*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![Ikon för att skapa semafor](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="f66c1-212">**Skapa semafor** (*tx_semaphore_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![Ikon för borttagning av semafor](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="f66c1-214">**Semafors borttagning** (*tx_semaphore_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![Ikon för Hämta semafor](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="f66c1-216">**Hämta semafor** (*tx_semaphore_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![Ikon för Hämta semafors information](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="f66c1-218">**Hämta semafors information** (*tx_semaphore_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![Ikon för Hämta semafor-prestanda information](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="f66c1-220">**Information om semafor-prestanda** (*tx_semaphroe_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![Ikon för Hämta semafor-system prestanda information](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="f66c1-222">**Prestanda information om semafor-systemet get** (*tx_semaphore_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![Ikon för semafor-prioritet](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="f66c1-224">**Semafor-prioritet** (*tx_semaphore_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![Ikon för semafor-placering](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="f66c1-226">**Semafor-placering** (*tx_semaphore_put*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![Varnings ikon för semafor-placering](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="f66c1-228">**Meddelande om semafor-placering** (*tx_semaphore_put_notify*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![Ikon för tråd skapande](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="f66c1-230">**Skapa tråd** (*tx_thread_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![Ikon för tråd borttagning](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="f66c1-232">**Tråd borttagning** (*tx_thread_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![Aviserings ikon för tråds utträde/Entry](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="f66c1-234">**Avisering om slut punkt/inmatning av tråd** (*tx_thread_entry_exit_notify*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![Ikon för tråd identifiering](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="f66c1-236">**Identifiera tråd** (*tx_thread_identify*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![Ikon för Hämta tråd information](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="f66c1-238">**Hämta tråd information** (*tx_thread_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![Ikon för att hämta tråd prestanda information](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="f66c1-240">**Hämta information om tråd prestanda information** (*tx_thread_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![Hämta ikon för tråd prestanda system information](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="f66c1-242">**Tråd prestanda system information get** (*tx_thread_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![Ändra ikon för tråd avstängningen](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="f66c1-244">**Avstängningen ändring av tråd** (*tx_thread_preemption_change*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![Ändrings ikon för tråd prioritet](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="f66c1-246">**Ändring av tråd prioritet** (*tx_thread_priority_change*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![Ikon för tråd som låser sig](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="f66c1-248">**Tråd överkörning** (*tx_thread_relinquish*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![Ikon för tråd återställning](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="f66c1-250">**Återställning av tråd** (*tx_thread_reset*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\* Trådens återställnings ikon](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="f66c1-252">**Tråd återupptagning** (\**tx_thread_resume*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![Ikon för trådens ström spar läge](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="f66c1-254">**Ström spar läge för tråd** (*tx_thread_sleep*) \*</span><span class="sxs-lookup"><span data-stu-id="f66c1-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![Aviserings ikon för tråds tack](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="f66c1-256">**Fel meddelande om tråds tack** (*tx_thread_stack_error_notify*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![Ikon för att pausa tråd](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="f66c1-258">**Paus av tråd** (*tx_thread_suspend*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![Avsluta ikon för tråd](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="f66c1-260">**Tråden avslutas** (*tx_thread_terminate*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![Tråd tids segmentets ändrings ikon](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="f66c1-262">**Trådens tids sektor ändring** (*tx_thread_time_slice_change*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![Ikon för Avbryt väntan](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="f66c1-264">**Avbryt väntan på avbrott** (*tx_thread_wait_abort*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![Ikonen Hämta tid](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="f66c1-266">**Hämtnings tid** (*tx_time_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-266">**Time get** (*tx_time_get*)</span></span> |
| ![Ikon för tids uppsättning](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="f66c1-268">**Tids uppsättning** (*tx_time_set*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-268">**Time set** (*tx_time_set*)</span></span> |
| ![\* Ikon för timer-aktivering](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="f66c1-270">**Aktivera timer** (*tx_timer_activate*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![Ändrings ikon för timer](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="f66c1-272">**Ändring av timer** (*tx_timer_change*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![Ikon för timer-skapande](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="f66c1-274">**Skapa timer** (*tx_timer_create*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![Ikonen timer-inaktivera](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="f66c1-276">**Timer-inaktive rad** (*tx_timer_deactivate*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![Ikon för timer-borttagning](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="f66c1-278">**Borttagning av timer** (*tx_timer_delete*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![Hämta ikon för timer-information](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="f66c1-280">**Visa timer-information** (*tx_timer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![Ikon för hämtning av timer-prestanda information](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="f66c1-282">**Hämta information om timer-prestanda** (*tx_timer_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\* Timer för prestanda system information Hämta ikon](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="f66c1-284">**Timer Performance system information get** (*tx_timer_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="f66c1-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="f66c1-286">**Användardefinierad händelse** (se kapitel 10)</span><span class="sxs-lookup"><span data-stu-id="f66c1-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="f66c1-287">Händelse beskrivningar</span><span class="sxs-lookup"><span data-stu-id="f66c1-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="f66c1-288">Återuppta intern tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="f66c1-289">Återuppta intern tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-289">Internal thread resume</span></span>

<span data-ttu-id="f66c1-290">**Ikonen** ![ Aktiverings ikon för intern tråd](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="f66c1-291">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-291">**Description**</span></span>

<span data-ttu-id="f66c1-292">Den här händelsen representerar intern bearbetning i ThreadX som återupptar en tråd för körning.</span><span class="sxs-lookup"><span data-stu-id="f66c1-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="f66c1-293">Om den angivna tråden är den högsta prioriteten och avstängningen-tröskelvärdet inte blockerar körningen kommer systemet att starta den nya färdiga tråden.</span><span class="sxs-lookup"><span data-stu-id="f66c1-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="f66c1-294">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-294">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-295">Info fält 1: visar en pekare till tråden som återupptas.</span><span class="sxs-lookup"><span data-stu-id="f66c1-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="f66c1-296">Info fält 2: föregående tillstånd för tråden som återupptas, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="f66c1-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="f66c1-297">Tråd tillstånd</span><span class="sxs-lookup"><span data-stu-id="f66c1-297">Thread state</span></span>                     | <span data-ttu-id="f66c1-298">Värde</span><span class="sxs-lookup"><span data-stu-id="f66c1-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f66c1-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="f66c1-299">TX_READY</span></span>                         | <span data-ttu-id="f66c1-300">0</span><span class="sxs-lookup"><span data-stu-id="f66c1-300">0</span></span>       |
  |  <span data-ttu-id="f66c1-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="f66c1-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="f66c1-302">1</span><span class="sxs-lookup"><span data-stu-id="f66c1-302">1</span></span>       |
  |  <span data-ttu-id="f66c1-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="f66c1-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="f66c1-304">2</span><span class="sxs-lookup"><span data-stu-id="f66c1-304">2</span></span>       |
  |  <span data-ttu-id="f66c1-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="f66c1-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="f66c1-306">3</span><span class="sxs-lookup"><span data-stu-id="f66c1-306">3</span></span>       |
  |  <span data-ttu-id="f66c1-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="f66c1-307">TX_SLEEP</span></span>                         | <span data-ttu-id="f66c1-308">4</span><span class="sxs-lookup"><span data-stu-id="f66c1-308">4</span></span>       |
  |  <span data-ttu-id="f66c1-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="f66c1-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="f66c1-310">5</span><span class="sxs-lookup"><span data-stu-id="f66c1-310">5</span></span>       |
  |  <span data-ttu-id="f66c1-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="f66c1-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="f66c1-312">6</span><span class="sxs-lookup"><span data-stu-id="f66c1-312">6</span></span>       |
  |  <span data-ttu-id="f66c1-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="f66c1-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="f66c1-314">7</span><span class="sxs-lookup"><span data-stu-id="f66c1-314">7</span></span>       |
  |  <span data-ttu-id="f66c1-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="f66c1-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="f66c1-316">8</span><span class="sxs-lookup"><span data-stu-id="f66c1-316">8</span></span>       |
  |  <span data-ttu-id="f66c1-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="f66c1-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="f66c1-318">9</span><span class="sxs-lookup"><span data-stu-id="f66c1-318">9</span></span>       |
  |  <span data-ttu-id="f66c1-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="f66c1-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="f66c1-320">12</span><span class="sxs-lookup"><span data-stu-id="f66c1-320">12</span></span>      |
  |  <span data-ttu-id="f66c1-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="f66c1-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="f66c1-322">13</span><span class="sxs-lookup"><span data-stu-id="f66c1-322">13</span></span>      |

- <span data-ttu-id="f66c1-323">Info-fält 3: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="f66c1-324">Info fält 4: pekare till näst högsta prioritets tråd att köra.</span><span class="sxs-lookup"><span data-stu-id="f66c1-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="f66c1-325">Inaktive ring av intern tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="f66c1-326">Inaktive ring av intern tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-326">Internal thread suspend</span></span>

<span data-ttu-id="f66c1-327">**Ikonen** ![ Inaktivera ikon för intern tråd](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="f66c1-328">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-328">**Description**</span></span>

<span data-ttu-id="f66c1-329">Den här händelsen representerar intern bearbetning i ThreadX som pausar körningen av en tråd.</span><span class="sxs-lookup"><span data-stu-id="f66c1-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="f66c1-330">Den näst högsta prioritets tråden som är klar för körning placeras i det fjärde informations fältet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="f66c1-331">Om det här värdet är NULL finns det ingen annan tråd klar för körning och systemet är inaktivt.</span><span class="sxs-lookup"><span data-stu-id="f66c1-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="f66c1-332">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-332">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-333">Info fält 1: pekar på tråden som pausas.</span><span class="sxs-lookup"><span data-stu-id="f66c1-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="f66c1-334">Informations fält 2: det nya tillståndet för tråden som pausas, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="f66c1-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="f66c1-335">Tråd tillstånd</span><span class="sxs-lookup"><span data-stu-id="f66c1-335">Thread state</span></span>                     | <span data-ttu-id="f66c1-336">Värde</span><span class="sxs-lookup"><span data-stu-id="f66c1-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="f66c1-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="f66c1-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="f66c1-338">1</span><span class="sxs-lookup"><span data-stu-id="f66c1-338">1</span></span>       |
  |  <span data-ttu-id="f66c1-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="f66c1-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="f66c1-340">2</span><span class="sxs-lookup"><span data-stu-id="f66c1-340">2</span></span>       |
  |  <span data-ttu-id="f66c1-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="f66c1-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="f66c1-342">3</span><span class="sxs-lookup"><span data-stu-id="f66c1-342">3</span></span>       |
  |  <span data-ttu-id="f66c1-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="f66c1-343">TX_SLEEP</span></span>                         | <span data-ttu-id="f66c1-344">4</span><span class="sxs-lookup"><span data-stu-id="f66c1-344">4</span></span>       |
  |  <span data-ttu-id="f66c1-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="f66c1-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="f66c1-346">5</span><span class="sxs-lookup"><span data-stu-id="f66c1-346">5</span></span>       |
  |  <span data-ttu-id="f66c1-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="f66c1-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="f66c1-348">6</span><span class="sxs-lookup"><span data-stu-id="f66c1-348">6</span></span>       |
  |  <span data-ttu-id="f66c1-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="f66c1-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="f66c1-350">7</span><span class="sxs-lookup"><span data-stu-id="f66c1-350">7</span></span>       |
  |  <span data-ttu-id="f66c1-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="f66c1-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="f66c1-352">8</span><span class="sxs-lookup"><span data-stu-id="f66c1-352">8</span></span>       |
  |  <span data-ttu-id="f66c1-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="f66c1-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="f66c1-354">9</span><span class="sxs-lookup"><span data-stu-id="f66c1-354">9</span></span>       |
  |  <span data-ttu-id="f66c1-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="f66c1-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="f66c1-356">12</span><span class="sxs-lookup"><span data-stu-id="f66c1-356">12</span></span>      |
  |  <span data-ttu-id="f66c1-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="f66c1-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="f66c1-358">13</span><span class="sxs-lookup"><span data-stu-id="f66c1-358">13</span></span>      |

- <span data-ttu-id="f66c1-359">Info-fält 3: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="f66c1-360">Info fält 4: pekare till näst högsta prioritets tråd att köra.</span><span class="sxs-lookup"><span data-stu-id="f66c1-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="f66c1-361">Om värdet är NULL är systemet inaktivt.</span><span class="sxs-lookup"><span data-stu-id="f66c1-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="f66c1-362">Avbrotts service rutin (ISR)-retur</span><span class="sxs-lookup"><span data-stu-id="f66c1-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="f66c1-363">Ange ISR</span><span class="sxs-lookup"><span data-stu-id="f66c1-363">Enter ISR</span></span> 

<span data-ttu-id="f66c1-364">**Ikonen** ![ Ange en R-ikon](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="f66c1-365">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-365">**Description**</span></span>

<span data-ttu-id="f66c1-366">Den här händelsen representerar att ange en avbrotts tjänst rutin (ISR) i programmet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="f66c1-367">Interrupt Service Routine körningen fortsätter tills den ISR-avsluts händelse äger rum.</span><span class="sxs-lookup"><span data-stu-id="f66c1-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="f66c1-368">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-368">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-369">Informations fält 1: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="f66c1-370">Info fält 2: Programdefinierat ISR-nummer (valfritt).</span><span class="sxs-lookup"><span data-stu-id="f66c1-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="f66c1-371">Informations fält 3: kapslat avbrotts antal.</span><span class="sxs-lookup"><span data-stu-id="f66c1-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="f66c1-372">Info fält 4: intern avstängningen-inaktivera flagga.</span><span class="sxs-lookup"><span data-stu-id="f66c1-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="f66c1-373">Avbryta service rutin (ISR)-avsluta</span><span class="sxs-lookup"><span data-stu-id="f66c1-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="f66c1-374">Avsluta ISR</span><span class="sxs-lookup"><span data-stu-id="f66c1-374">Exit ISR</span></span>

<span data-ttu-id="f66c1-375">**Ikonen** ![ Avsluta I S-ikon](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="f66c1-376">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-376">**Description**</span></span>

<span data-ttu-id="f66c1-377">Den här händelsen representerar att avsluta en avbrotts tjänst rutin (ISR) i programmet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="f66c1-378">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-378">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-379">Informations fält 1: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="f66c1-380">Info fält 2: Programdefinierat ISR-nummer (valfritt).</span><span class="sxs-lookup"><span data-stu-id="f66c1-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="f66c1-381">Informations fält 3: kapslat avbrotts antal.</span><span class="sxs-lookup"><span data-stu-id="f66c1-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="f66c1-382">Info fält 4: intern avstängningen-inaktivera flagga.</span><span class="sxs-lookup"><span data-stu-id="f66c1-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="f66c1-383">Intern tid-sektor</span><span class="sxs-lookup"><span data-stu-id="f66c1-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="f66c1-384">Intern tid-sektor</span><span class="sxs-lookup"><span data-stu-id="f66c1-384">Internal time-slice</span></span>

<span data-ttu-id="f66c1-385">**Ikonen** ![ Intern Time-slice-ikon](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="f66c1-386">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-386">**Description**</span></span>

<span data-ttu-id="f66c1-387">Den här händelsen representerar den interna bearbetningen i ThreadX som utför tids segments åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f66c1-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="f66c1-388">Nästa tråd av samma prioritet placeras i det första informations fältet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="f66c1-389">Om det här värdet är samma som den aktuella tråden utfördes ingen tid-sektor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="f66c1-390">Info fält 1: pekar mot nästa tråd som ska köras.</span><span class="sxs-lookup"><span data-stu-id="f66c1-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="f66c1-391">Informations fält 2: kapslat avbrotts antal.</span><span class="sxs-lookup"><span data-stu-id="f66c1-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="f66c1-392">Info-fält 3: intern avstängningen-inaktivera flagga.</span><span class="sxs-lookup"><span data-stu-id="f66c1-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="f66c1-393">Info-fält 4: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="f66c1-394">Körs</span><span class="sxs-lookup"><span data-stu-id="f66c1-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="f66c1-395">Körs i kontext</span><span class="sxs-lookup"><span data-stu-id="f66c1-395">Running in context</span></span>

<span data-ttu-id="f66c1-396">**Ikonen** ![ Kör ikon](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="f66c1-397">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-397">**Description**</span></span>

<span data-ttu-id="f66c1-398">Den här händelsen representerar körning i en tråd kontext eller inaktivt system.</span><span class="sxs-lookup"><span data-stu-id="f66c1-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="f66c1-399">Den används för att illustrera efterföljande ändringar i sammanhanget som ett resultat av ett avbrott.</span><span class="sxs-lookup"><span data-stu-id="f66c1-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="f66c1-400">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-400">**Information Fields**</span></span>
- <span data-ttu-id="f66c1-401">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-402">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-403">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-404">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="f66c1-405">Blockera tilldelning</span><span class="sxs-lookup"><span data-stu-id="f66c1-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="f66c1-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f66c1-406">tx_block_allocate</span></span>

<span data-ttu-id="f66c1-407">**Ikonen** ![ Ikonen blockera tilldelning](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="f66c1-408">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-408">**Description**</span></span>

<span data-ttu-id="f66c1-409">Den här händelsen representerar att allokera ett minnes block via tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="f66c1-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="f66c1-410">Om det lyckas returneras adressen för det tilldelade blocket i det andra informations fältet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="f66c1-411">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-411">**Information Fields**</span></span>
- <span data-ttu-id="f66c1-412">Info fält 1: pekar mot motsvarande block-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="f66c1-413">Info fält 2: visar en pekare till det minnes block som returnerades (om det lyckades).</span><span class="sxs-lookup"><span data-stu-id="f66c1-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="f66c1-414">Informations fält 3: vänte alternativet som angavs i tx_block_allocate-anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="f66c1-415">Info fält 4: återstående tillgängliga block i poolen efter den här allokeringen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="f66c1-416">Blockera skapande av pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="f66c1-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-417">tx_block_pool_create</span></span>

<span data-ttu-id="f66c1-418">**Ikonen** ![ Skapa ikon för att blockera pool](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="f66c1-419">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-419">**Description**</span></span>

<span data-ttu-id="f66c1-420">Den här händelsen representerar skapandet av en Memory block-pool via tx_block_pool_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="f66c1-421">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-421">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-422">Informations fält 1: pekar mot motsvarande block pool kontroll block.</span><span class="sxs-lookup"><span data-stu-id="f66c1-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="f66c1-423">Info fält 2: pekar på poolens start minne.</span><span class="sxs-lookup"><span data-stu-id="f66c1-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="f66c1-424">Informations fält 3: antalet block i poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="f66c1-425">Info fält 4: storleken på varje block i poolen i byte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="f66c1-426">Blockera borttagning av pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="f66c1-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-427">tx_block_pool_delete</span></span>

<span data-ttu-id="f66c1-428">**Ikonen** ![ Ta bort ikon för borttagning av pool](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="f66c1-429">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-429">**Description**</span></span>

<span data-ttu-id="f66c1-430">Den här händelsen representerar borttagning av en Memory block-pool via tx_block_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="f66c1-431">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-431">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-432">Informations fält 1: pekar mot kontroll block för block-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="f66c1-433">Info-fält 2: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="f66c1-434">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-435">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="f66c1-436">Blockera information om poolen Hämta</span><span class="sxs-lookup"><span data-stu-id="f66c1-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="f66c1-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="f66c1-438">**Ikonen** ![ Hämta ikon för Hämta pool information](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="f66c1-439">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-439">**Description**</span></span>

<span data-ttu-id="f66c1-440">Den här händelsen representerar att hämta information om en Memory block-pool via tx_block_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="f66c1-441">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-441">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-442">Informations fält 1: pekar mot kontroll block för block-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="f66c1-443">Info-fält 2: stack pekarens värde under anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="f66c1-444">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-445">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="f66c1-446">Blockera prestanda information för pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="f66c1-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="f66c1-448">**Ikonen** ![ Hämta ikon för att blockera poolens prestanda information](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="f66c1-449">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-449">**Description**</span></span>

<span data-ttu-id="f66c1-450">Den här händelsen representerar prestanda information om en Memory block-pool via tx_block_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="f66c1-451">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-451">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-452">Informations fält 1: pekar mot kontroll block för block-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="f66c1-453">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-454">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-455">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="f66c1-456">Blockera prestanda system information för poolen Hämta</span><span class="sxs-lookup"><span data-stu-id="f66c1-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="f66c1-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-458">**Ikonen** ![ Blockera pool prestanda system information get-ikon](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="f66c1-459">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-459">**Description**</span></span>

<span data-ttu-id="f66c1-460">Den här händelsen representerar prestanda information om alla minnes Blocks pooler via tx_block_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-461">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-461">**Information Fields**</span></span>
- <span data-ttu-id="f66c1-462">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-463">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-464">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-465">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="f66c1-466">Prioritera block pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="f66c1-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f66c1-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="f66c1-468">**Ikonen** ![ Prioritets ikon för att blockera pool](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="f66c1-469">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-469">**Description**</span></span>

<span data-ttu-id="f66c1-470">Den här händelsen representerar placeringen av den HighestPriority suspenderade tråden längst fram i listan över blockerade SUS-listor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="f66c1-471">Om detta görs innan du anropar tx_block_release, tar den inaktiverade tråden med högsta prioritet det släppta blocket.</span><span class="sxs-lookup"><span data-stu-id="f66c1-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="f66c1-472">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-472">**Information Fields**</span></span>
- <span data-ttu-id="f66c1-473">Informations fält 1: pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="f66c1-474">Informations fält 2: antal pausade trådar i den här block poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="f66c1-475">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="f66c1-476">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="f66c1-477">Blockera version</span><span class="sxs-lookup"><span data-stu-id="f66c1-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="f66c1-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f66c1-478">tx_block_release</span></span>

<span data-ttu-id="f66c1-479">**Ikonen** ![ Ikonen blockera version](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="f66c1-480">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-480">**Description**</span></span>

<span data-ttu-id="f66c1-481">Den här händelsen representerar att släppa ett tidigare allokerat block tillbaka till block-poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="f66c1-482">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-482">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-483">Informations fält 1: pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="f66c1-484">Info fält 2: pekare för att blockera till version.</span><span class="sxs-lookup"><span data-stu-id="f66c1-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="f66c1-485">Informations fält 3: antal pausade trådar i den här block poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="f66c1-486">Info-fält 4: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="f66c1-487">Allokera byte</span><span class="sxs-lookup"><span data-stu-id="f66c1-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="f66c1-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f66c1-488">tx_byte_allocate</span></span>

<span data-ttu-id="f66c1-489">**Ikonen** ![ Ikon för byte tilldelning](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="f66c1-490">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-490">**Description**</span></span>

<span data-ttu-id="f66c1-491">Den här händelsen representerar allokering av minne via tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="f66c1-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="f66c1-492">Om det lyckas returneras adressen för det tilldelade minnet i det andra informations fältet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="f66c1-493">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-493">**Information Fields**</span></span>
- <span data-ttu-id="f66c1-494">Info fält 1: pekar mot motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-495">Info fält 2: pekar på det returnerade minnet (om det lyckades).</span><span class="sxs-lookup"><span data-stu-id="f66c1-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="f66c1-496">Informations fält 3: antal byte som har begärts.</span><span class="sxs-lookup"><span data-stu-id="f66c1-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="f66c1-497">Info fält 4: vänte alternativet som angavs för tx_byte_allocate-anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="f66c1-498">Skapa byte pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="f66c1-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-499">tx_byte_pool_create</span></span>

<span data-ttu-id="f66c1-500">**Ikonen** ![ Ikon för att skapa byte pool](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="f66c1-501">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-501">**Description**</span></span>

<span data-ttu-id="f66c1-502">Den här händelsen representerar att skapa en byte-pool via tx_byte_pool_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="f66c1-503">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-503">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-504">Info fält 1: pekar mot motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-505">Info fält 2: pekar mot början av minnes området.</span><span class="sxs-lookup"><span data-stu-id="f66c1-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="f66c1-506">Informations fält 3: antal byte i byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="f66c1-507">Info-fält 4: stack pekaren vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="f66c1-508">Borttagning av byte pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="f66c1-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="f66c1-510">**Ikonen** ![ Borttagnings ikon för byte pool](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="f66c1-511">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-511">**Description**</span></span>

<span data-ttu-id="f66c1-512">Den här händelsen representerar borttagning av en byte-pool via tx_byte_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="f66c1-513">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-513">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-514">Info fält 1: pekar mot motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-515">Info fält 2: stack pekaren vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="f66c1-516">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-517">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="f66c1-518">Hämta information om byte pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="f66c1-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="f66c1-520">**Ikonen** ![ Ikon för hämta information om byte pool](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="f66c1-521">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-521">**Description**</span></span>

<span data-ttu-id="f66c1-522">Den här händelsen representerar hämtning av information om byte-pool via tx_byte_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="f66c1-523">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-523">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-524">Info fält 1: pekar mot motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-525">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-526">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-527">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="f66c1-528">Hämta prestanda information för byte-pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="f66c1-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="f66c1-530">**Ikonen** ![ Ikon för hämta prestanda information för byte-pool](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="f66c1-531">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-531">**Description**</span></span>

<span data-ttu-id="f66c1-532">Den här händelsen representerar hämtning av prestanda information för byte-pool via tx_byte_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="f66c1-533">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-533">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-534">Info fält 1: pekar mot motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-535">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-536">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-537">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="f66c1-538">Hämta prestanda system information för byte-pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="f66c1-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-540">**Ikonen** ![ Hämta ikon för prestanda system information för byte pool](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="f66c1-541">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-541">**Description**</span></span>

<span data-ttu-id="f66c1-542">Den här händelsen representerar hämtning av prestanda system information för byte-pool via tx_byte_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-543">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-543">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-544">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-545">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-546">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-547">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="f66c1-548">Prioritet för byte pool</span><span class="sxs-lookup"><span data-stu-id="f66c1-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="f66c1-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f66c1-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="f66c1-550">**Ikonen** ![ Prioritets ikon för byte pool](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="f66c1-551">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-551">**Description**</span></span>

<span data-ttu-id="f66c1-552">Den här händelsen representerar prioritering av byte-poolens SUS Pension-lista via tx_byte_pool_prioritize.</span><span class="sxs-lookup"><span data-stu-id="f66c1-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="f66c1-553">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-553">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-554">Info fält 1: pekare till motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-555">Informations fält 2: antal trådar som för närvarande har pausats i byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="f66c1-556">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-557">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="f66c1-558">Byte-version</span><span class="sxs-lookup"><span data-stu-id="f66c1-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="f66c1-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f66c1-559">tx_byte_release</span></span>

<span data-ttu-id="f66c1-560">**Ikonen** ![ Ikon för byte-version](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="f66c1-561">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-561">**Description**</span></span>

<span data-ttu-id="f66c1-562">Den här händelsen representerar att släppa ett minnes block som tilldelas från en byte-pool via tx_byte_release.</span><span class="sxs-lookup"><span data-stu-id="f66c1-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="f66c1-563">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-563">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-564">Info fält 1: pekare till motsvarande byte-pool.</span><span class="sxs-lookup"><span data-stu-id="f66c1-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="f66c1-565">Info fält 2: pekare till tidigare allokerat minne i byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="f66c1-566">Informations fält 3: antal pausade trådar i den här byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="f66c1-567">Info fält 4: antal tillgängliga byte i minnet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="f66c1-568">Händelse flaggor skapa</span><span class="sxs-lookup"><span data-stu-id="f66c1-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="f66c1-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-569">tx_event_flags_create</span></span>

<span data-ttu-id="f66c1-570">**Ikonen** ![ Ikonen Skapa händelse flaggor](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="f66c1-571">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-571">**Description**</span></span>

<span data-ttu-id="f66c1-572">Den här händelsen representerar att skapa en ny grupp med händelse flaggor via tx_event_flags_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="f66c1-573">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-573">**Information Fields**</span></span> 
- <span data-ttu-id="f66c1-574">Info fält 1: pekar på händelse flaggor grupp kontroll block.</span><span class="sxs-lookup"><span data-stu-id="f66c1-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="f66c1-575">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-576">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-577">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="f66c1-578">Ta bort händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="f66c1-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="f66c1-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-579">tx_event_flags_delete</span></span>

<span data-ttu-id="f66c1-580">**Ikonen** ![ Borttagnings ikon för händelse flaggor](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="f66c1-581">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-581">**Description**</span></span>

<span data-ttu-id="f66c1-582">Den här händelsen representerar att ta bort en grupp med händelse flaggor via tx_event_flags_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="f66c1-583">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-583">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-584">Info fält 1: pekar på händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="f66c1-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="f66c1-585">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-586">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-587">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="f66c1-588">Händelse flaggor Hämta</span><span class="sxs-lookup"><span data-stu-id="f66c1-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="f66c1-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-589">tx_event_flags_get</span></span>

<span data-ttu-id="f66c1-590">**Ikonen** ![ Ikon för händelse flaggor gt](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="f66c1-591">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-591">**Description**</span></span>

<span data-ttu-id="f66c1-592">Den här händelsen representerar hämtning av händelse flaggor från en befintlig grupp för händelse flaggor via tx_event_flags_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="f66c1-593">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-593">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-594">Info fält 1: pekar på händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="f66c1-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="f66c1-595">Informations fält 2: händelse flaggor begärs.</span><span class="sxs-lookup"><span data-stu-id="f66c1-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="f66c1-596">Info-fält 3: händelse flaggor som för närvarande anges i gruppen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="f66c1-597">Info Field 4: alternativet som begärdes för händelse flaggorna get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="f66c1-598">Händelse flaggor information Hämta</span><span class="sxs-lookup"><span data-stu-id="f66c1-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="f66c1-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="f66c1-600">**Ikonen** ![ Ikonen Hämta information om händelse flaggor](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="f66c1-601">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-601">**Description**</span></span>

<span data-ttu-id="f66c1-602">Den här händelsen representerar hämtning av information om en befintlig händelse flaggor grupp via tx_event_flags_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="f66c1-603">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-603">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-604">Info fält 1: pekar på händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="f66c1-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="f66c1-605">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-606">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-607">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="f66c1-608">Händelse flaggor prestanda information Hämta</span><span class="sxs-lookup"><span data-stu-id="f66c1-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="f66c1-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="f66c1-610">**Ikonen** ![ Händelse flaggor prestanda information Hämta ikon](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="f66c1-611">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-611">**Description**</span></span>

<span data-ttu-id="f66c1-612">Den här händelsen representerar hämtning av prestanda information om en befintlig händelse flaggor grupp via tx_event_flags_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="f66c1-613">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-613">**Information Fields**</span></span> 
- <span data-ttu-id="f66c1-614">Info fält 1: pekar på händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="f66c1-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="f66c1-615">Informations fält 2: används inte</span><span class="sxs-lookup"><span data-stu-id="f66c1-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="f66c1-616">Informations fält 3: används inte</span><span class="sxs-lookup"><span data-stu-id="f66c1-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="f66c1-617">Info fält 4: används inte</span><span class="sxs-lookup"><span data-stu-id="f66c1-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="f66c1-618">Händelse flaggor prestanda system information get</span><span class="sxs-lookup"><span data-stu-id="f66c1-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="f66c1-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-620">**Ikonen** ![ Händelse flaggor prestanda system information Hämta ikon](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="f66c1-621">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-621">**Description**</span></span>

<span data-ttu-id="f66c1-622">Den här händelsen representerar hämtning av prestanda information om en befintlig händelse flaggor grupp via tx_event_flags_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-623">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-623">**Information Fields**</span></span>
- <span data-ttu-id="f66c1-624">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-625">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-626">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-627">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="f66c1-628">Angivna händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="f66c1-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="f66c1-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f66c1-629">tx_event_flags_set</span></span>

<span data-ttu-id="f66c1-630">**Ikonen** ![ Ikonen händelse flaggor uppsättning](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="f66c1-631">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-631">**Description**</span></span>

<span data-ttu-id="f66c1-632">Den här händelsen representerar att ange (eller avmarkera) händelse flaggor i en befintlig grupp för händelse flaggor via tx_event_flags_set.</span><span class="sxs-lookup"><span data-stu-id="f66c1-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="f66c1-633">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-633">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-634">Info fält 1: pekar på händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="f66c1-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="f66c1-635">Info-fält 2: händelse flaggor som ska anges (eller rensas).</span><span class="sxs-lookup"><span data-stu-id="f66c1-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="f66c1-636">Informations fält 3: och eller eller alternativ för händelse flagga.</span><span class="sxs-lookup"><span data-stu-id="f66c1-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="f66c1-637">Info fält 4: antal pausade trådar i händelse flaggas gruppen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="f66c1-638">Meddelande om inställd händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="f66c1-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="f66c1-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f66c1-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="f66c1-640">**Ikonen** ![ Händelse flaggor ange aviserings ikon](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="f66c1-641">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-641">**Description**</span></span>

<span data-ttu-id="f66c1-642">Den här händelsen representerar registrering av ett meddelande återanrop för en händelse flagga som har åtgärd ATS i en befintlig grupp för händelse flaggor via tx_event_flags_set_notify.</span><span class="sxs-lookup"><span data-stu-id="f66c1-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="f66c1-643">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-643">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-644">Info fält 1: pekar på händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="f66c1-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="f66c1-645">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-646">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-647">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="f66c1-648">Avbrotts kontroll</span><span class="sxs-lookup"><span data-stu-id="f66c1-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="f66c1-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="f66c1-649">tx_interrupt_control</span></span>

<span data-ttu-id="f66c1-650">**Ikonen** ![ Avbrotts kontroll ikon](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="f66c1-651">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-651">**Description**</span></span>

<span data-ttu-id="f66c1-652">Den här händelsen representerar ändring av position för avbrotts utelåsning via tx_interrupt_control.</span><span class="sxs-lookup"><span data-stu-id="f66c1-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="f66c1-653">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-653">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-654">Informations fält 1: nytt avbrotts position.</span><span class="sxs-lookup"><span data-stu-id="f66c1-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="f66c1-655">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-656">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-657">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="f66c1-658">Skapa mutex</span><span class="sxs-lookup"><span data-stu-id="f66c1-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="f66c1-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-659">tx_mutex_create</span></span>

<span data-ttu-id="f66c1-660">**Ikonen** ![ Ikon för mutex-skapande](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="f66c1-661">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-661">**Description**</span></span>

<span data-ttu-id="f66c1-662">Den här händelsen representerar skapandet av en mutex via tx_mutex_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="f66c1-663">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-663">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-664">Info fält 1: pekar mot mutex-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="f66c1-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="f66c1-665">Informations fält 2: alternativet prioritera arv</span><span class="sxs-lookup"><span data-stu-id="f66c1-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="f66c1-666">(TX_INHERIT eller TX_NO_INHERIT).</span><span class="sxs-lookup"><span data-stu-id="f66c1-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="f66c1-667">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-668">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="f66c1-669">Ta bort mutex</span><span class="sxs-lookup"><span data-stu-id="f66c1-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="f66c1-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-670">tx_mutex_delete</span></span>

<span data-ttu-id="f66c1-671">**Ikonen** ![ Ikon för mutex-borttagning](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="f66c1-672">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-672">**Description**</span></span>

<span data-ttu-id="f66c1-673">Den här händelsen representerar borttagning av en mutex via tx_mutex_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="f66c1-674">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-674">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-675">Info fält 1: pekar mot mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="f66c1-676">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-677">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-678">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="f66c1-679">Hämta mutex</span><span class="sxs-lookup"><span data-stu-id="f66c1-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="f66c1-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-680">tx_mutex_get</span></span>

<span data-ttu-id="f66c1-681">**Ikonen** ![ Ikon för att hämta mutex](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="f66c1-682">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-682">**Description**</span></span>

<span data-ttu-id="f66c1-683">Den här händelsen representerar hämtning av en mutex via tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="f66c1-684">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-684">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-685">Info fält 1: pekar mot mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="f66c1-686">Informations fält 2: vänte alternativet som angavs för tx_mutex_get-anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="f66c1-687">Informations fält 3: en pekare till tråd som äger mutex (NULL betyder att mutex inte ägs).</span><span class="sxs-lookup"><span data-stu-id="f66c1-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="f66c1-688">Info fält 4: antal gånger som den ägande tråden har anropat tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="f66c1-689">Hämtning av mutex-information</span><span class="sxs-lookup"><span data-stu-id="f66c1-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="f66c1-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-690">tx_mutex_info_get</span></span>

<span data-ttu-id="f66c1-691">**Ikonen** ![ Get-ikon för mutex information](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="f66c1-692">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-692">**Description**</span></span>

<span data-ttu-id="f66c1-693">Den här händelsen representerar hämtning av mutex-information via tx_mutex_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="f66c1-694">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-694">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-695">Info fält 1: pekar mot mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="f66c1-696">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-697">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-698">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="f66c1-699">Information om mutex-prestanda</span><span class="sxs-lookup"><span data-stu-id="f66c1-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="f66c1-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="f66c1-701">**Ikonen** ![ Ikon för hämta information om mutex-prestanda](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="f66c1-702">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-702">**Description**</span></span>

<span data-ttu-id="f66c1-703">Den här händelsen representerar hämtning av information om mutex-prestanda via tx_mutex_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="f66c1-704">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-704">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-705">Info fält 1: pekar mot mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="f66c1-706">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-707">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-708">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="f66c1-709">Information om att hämta mutex-prestanda</span><span class="sxs-lookup"><span data-stu-id="f66c1-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="f66c1-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-711">**Ikonen** ![ Mutex Performance system information get-ikon](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="f66c1-712">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-712">**Description**</span></span>

<span data-ttu-id="f66c1-713">Den här händelsen representerar hämtning av information om mutex-systemets prestanda via tx_mutex_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-714">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-714">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-715">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-716">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-717">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-718">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="f66c1-719">Mutex-prioritering</span><span class="sxs-lookup"><span data-stu-id="f66c1-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="f66c1-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f66c1-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="f66c1-721">**Ikonen** ![ Ikon för mutex-prioritet](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="f66c1-722">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-722">**Description**</span></span>

<span data-ttu-id="f66c1-723">Den här händelsen representerar prioritering av mutexens SUS Pension-lista via tx_mutex_prioritize.</span><span class="sxs-lookup"><span data-stu-id="f66c1-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="f66c1-724">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-724">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-725">Info fält 1: pekare till motsvarande mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="f66c1-726">Informations fält 2: antal trådar som för närvarande har pausats på mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="f66c1-727">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-728">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="f66c1-729">Mutex-placering</span><span class="sxs-lookup"><span data-stu-id="f66c1-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="f66c1-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f66c1-730">tx_mutex_put</span></span>

<span data-ttu-id="f66c1-731">**Ikonen** ![ Ikon för mutex-placering](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="f66c1-732">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-732">**Description**</span></span>

<span data-ttu-id="f66c1-733">Den här händelsen representerar att släppa en tidigare ägd mutex via tx_mutex_put.</span><span class="sxs-lookup"><span data-stu-id="f66c1-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="f66c1-734">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-734">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-735">Info fält 1: pekare till motsvarande mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="f66c1-736">Info fält 2: en pekare på en tråd som äger mutex.</span><span class="sxs-lookup"><span data-stu-id="f66c1-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="f66c1-737">Informations fält 3: antal utestående mutex get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="f66c1-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="f66c1-738">Info-fält 4: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="f66c1-739">Skapa kö</span><span class="sxs-lookup"><span data-stu-id="f66c1-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="f66c1-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-740">tx_queue_create</span></span>

<span data-ttu-id="f66c1-741">**Ikonen** ![ Ikon för att skapa kö](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="f66c1-742">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-742">**Description**</span></span>

<span data-ttu-id="f66c1-743">Den här händelsen representerar att skapa en meddelandekö via tx_queue_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="f66c1-744">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-744">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-745">Info fält 1: pekar på kontroll block för kö.</span><span class="sxs-lookup"><span data-stu-id="f66c1-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="f66c1-746">Info fält 2: meddelandets storlek – i termer av 32-bitars ord.</span><span class="sxs-lookup"><span data-stu-id="f66c1-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="f66c1-747">Info-fält 3: pekar till början av kös Memory Area.</span><span class="sxs-lookup"><span data-stu-id="f66c1-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="f66c1-748">Info-fält 4: antal byte i köns minnes område.</span><span class="sxs-lookup"><span data-stu-id="f66c1-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="f66c1-749">Köa borttagning</span><span class="sxs-lookup"><span data-stu-id="f66c1-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="f66c1-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-750">tx_queue_delete</span></span>

<span data-ttu-id="f66c1-751">**Ikonen** ![ Borttagnings ikon för kö](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="f66c1-752">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-752">**Description**</span></span>

<span data-ttu-id="f66c1-753">Den här händelsen representerar borttagning av en kö via tx_queue_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="f66c1-754">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-754">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-755">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-756">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-757">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-758">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="f66c1-759">Köa rensning</span><span class="sxs-lookup"><span data-stu-id="f66c1-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="f66c1-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f66c1-760">tx_queue_flush</span></span>

<span data-ttu-id="f66c1-761">**Ikonen** ![ Ikon för köa tömning](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="f66c1-762">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-762">**Description**</span></span>

<span data-ttu-id="f66c1-763">Den här händelsen representerar tömning (rensa allt innehåll i kön) i en kö via tx_queue_flush.</span><span class="sxs-lookup"><span data-stu-id="f66c1-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="f66c1-764">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-764">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-765">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-766">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-767">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-768">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="f66c1-769">Skicka kö, klient</span><span class="sxs-lookup"><span data-stu-id="f66c1-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="f66c1-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f66c1-770">tx_queue_front_send</span></span>

<span data-ttu-id="f66c1-771">**Ikonen** ![ Ikon för att skicka kön direkt](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="f66c1-772">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-772">**Description**</span></span>

<span data-ttu-id="f66c1-773">Den här händelsen representerar att skicka ett meddelande längst fram i kön via tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="f66c1-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="f66c1-774">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-774">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-775">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-776">Info fält 2: pekare till början av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="f66c1-777">Informations fält 3: vänte alternativ har angetts till</span><span class="sxs-lookup"><span data-stu-id="f66c1-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="f66c1-778">tx_queue_front_send-anrop.</span><span class="sxs-lookup"><span data-stu-id="f66c1-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="f66c1-779">Info fält 4: antal meddelanden som redan har placerats i kö.</span><span class="sxs-lookup"><span data-stu-id="f66c1-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="f66c1-780">Hämta information om kön</span><span class="sxs-lookup"><span data-stu-id="f66c1-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="f66c1-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-781">tx_queue_info_get</span></span>

<span data-ttu-id="f66c1-782">**Ikonen** ![ Hämta ikon för köa information](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="f66c1-783">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-783">**Description**</span></span>

<span data-ttu-id="f66c1-784">Den här händelsen representerar att hämta information om en kö via tx_queue_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="f66c1-785">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-785">**Information Fields**</span></span> 
- <span data-ttu-id="f66c1-786">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-787">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-788">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-789">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="f66c1-790">Hämta prestanda information för kö</span><span class="sxs-lookup"><span data-stu-id="f66c1-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="f66c1-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="f66c1-792">**Ikonen** ![ Hämta ikon för köns prestanda information](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="f66c1-793">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-793">**Description**</span></span>

<span data-ttu-id="f66c1-794">Den här händelsen representerar prestanda information om en kö via tx_queue_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="f66c1-795">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-795">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-796">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-797">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-798">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-799">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="f66c1-800">Hämta prestanda system information för kö</span><span class="sxs-lookup"><span data-stu-id="f66c1-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="f66c1-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-802">**Ikonen** ![ Hämta ikon för prestanda system information i kö](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="f66c1-803">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-803">**Description**</span></span>

<span data-ttu-id="f66c1-804">Den här händelsen representerar system prestanda information om alla köer i systemet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="f66c1-805">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-805">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-806">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-807">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-808">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-809">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="f66c1-810">Prioritet för kö</span><span class="sxs-lookup"><span data-stu-id="f66c1-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="f66c1-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f66c1-811">tx_queue_prioritize</span></span>

<span data-ttu-id="f66c1-812">**Ikonen** ![ Ikon för köa prioritet](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="f66c1-813">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-813">**Description**</span></span>

<span data-ttu-id="f66c1-814">Den här händelsen representerar prioritering av köns SUS Pension-lista via tx_queue_prioritize.</span><span class="sxs-lookup"><span data-stu-id="f66c1-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="f66c1-815">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-815">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-816">Info fält 1: pekare till motsvarande kö.</span><span class="sxs-lookup"><span data-stu-id="f66c1-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="f66c1-817">Informations fält 2: antal trådar som för närvarande har pausats i kön.</span><span class="sxs-lookup"><span data-stu-id="f66c1-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="f66c1-818">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-819">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="f66c1-820">Ta emot kön</span><span class="sxs-lookup"><span data-stu-id="f66c1-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="f66c1-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f66c1-821">tx_queue_receive</span></span>

<span data-ttu-id="f66c1-822">**Ikonen** ![ Ikon för köa mottagning](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="f66c1-823">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-823">**Description**</span></span>

<span data-ttu-id="f66c1-824">Den här händelsen representerar att ta emot ett meddelande från en kö via tx_queue_receive.</span><span class="sxs-lookup"><span data-stu-id="f66c1-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="f66c1-825">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-825">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-826">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-827">Info fält 2: pekare till målet för meddelandet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="f66c1-828">Info-fält 3: vänte alternativ har angetts för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="f66c1-829">Info fält 4: antal meddelanden som för närvarande finns i kö.</span><span class="sxs-lookup"><span data-stu-id="f66c1-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="f66c1-830">Köa sändning</span><span class="sxs-lookup"><span data-stu-id="f66c1-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="f66c1-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f66c1-831">tx_queue_send</span></span>

<span data-ttu-id="f66c1-832">**Ikonen** ![ Ikon för Queue-sändning](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="f66c1-833">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-833">**Description**</span></span>

<span data-ttu-id="f66c1-834">Den här händelsen representerar att skicka ett meddelande till en kö via tx_queue_send.</span><span class="sxs-lookup"><span data-stu-id="f66c1-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="f66c1-835">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-835">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-836">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-837">Info fält 2: pekare till meddelande.</span><span class="sxs-lookup"><span data-stu-id="f66c1-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="f66c1-838">Info-fält 3: vänte alternativ har angetts för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="f66c1-839">Info fält 4: antal meddelanden som för närvarande finns i kö.</span><span class="sxs-lookup"><span data-stu-id="f66c1-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="f66c1-840">Skicka meddelande om kö</span><span class="sxs-lookup"><span data-stu-id="f66c1-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="f66c1-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f66c1-841">tx_queue_send_notify</span></span>

<span data-ttu-id="f66c1-842">**Ikonen** ![ Ikon för att skicka meddelande i kö](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="f66c1-843">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-843">**Description**</span></span>

<p><span data-ttu-id="f66c1-844">Den här händelsen representerar registrering av ett återanrop via tx_queue_send_notify som anropas när ett meddelande skickas till en kö.</span><span class="sxs-lookup"><span data-stu-id="f66c1-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="f66c1-845">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-845">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-846">Info fält 1: pekare till Queue.</span><span class="sxs-lookup"><span data-stu-id="f66c1-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="f66c1-847">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-848">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-849">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="f66c1-850">Utplacering av semafors tak</span><span class="sxs-lookup"><span data-stu-id="f66c1-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="f66c1-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f66c1-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="f66c1-852">**Ikonen** ![ Ikon för Semaforens tak placering](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="f66c1-853">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-853">**Description**</span></span>

<span data-ttu-id="f66c1-854">Den här händelsen representerar att placera en semafor via tx_semaphore_ceiling_put.</span><span class="sxs-lookup"><span data-stu-id="f66c1-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="f66c1-855">Detta skiljer sig från tx_semaphore_put i så fall att det maximala värdet för semaforen kontrol leras så att placerings åtgärden inte får överskrida det högsta värdet eller taket.</span><span class="sxs-lookup"><span data-stu-id="f66c1-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="f66c1-856">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-856">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-857">Info fält 1: pekar mot semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="f66c1-858">Informations fält 2: aktuellt semafor-antal.</span><span class="sxs-lookup"><span data-stu-id="f66c1-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="f66c1-859">Informations fält 3: antal pausade trådar i semaforen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="f66c1-860">Info-fält 4: gräns värdet för tak har angetts till anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="f66c1-861">Skapa semafor</span><span class="sxs-lookup"><span data-stu-id="f66c1-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="f66c1-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-862">tx_semaphore_create</span></span>

<span data-ttu-id="f66c1-863">**Ikonen** ![ Ikon för att skapa semafor](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="f66c1-864">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-864">**Description**</span></span>

<span data-ttu-id="f66c1-865">Den här händelsen representerar skapandet av en semafor via tx_semaphore_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="f66c1-866">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-866">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-867">Informations fält 1: pekar mot semafor-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="f66c1-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="f66c1-868">Informations fält 2: inledande semafor-antal.</span><span class="sxs-lookup"><span data-stu-id="f66c1-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="f66c1-869">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-870">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="f66c1-871">Ta bort semafor</span><span class="sxs-lookup"><span data-stu-id="f66c1-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="f66c1-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-872">tx_semaphore_delete</span></span>

<span data-ttu-id="f66c1-873">**Ikonen** ![ Ikon för borttagning av semafor](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="f66c1-874">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-874">**Description**</span></span>

<span data-ttu-id="f66c1-875">Den här händelsen representerar borttagning av en semafor via tx_semaphore_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="f66c1-876">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-876">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-877">Info fält 1: pekar mot semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="f66c1-878">NFO-fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-879">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-880">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="f66c1-881">Hämta semafor</span><span class="sxs-lookup"><span data-stu-id="f66c1-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="f66c1-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-882">tx_semaphore_get</span></span>

<span data-ttu-id="f66c1-883">**Ikonen** ![ Ikon för Hämta semafor](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="f66c1-884">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-884">**Description**</span></span>

<span data-ttu-id="f66c1-885">Den här händelsen representerar hämtning av en semafor via tx_semaphore_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="f66c1-886">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-886">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-887">Info fält 1: pekar mot semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="f66c1-888">Info fält 2: vänte alternativet angavs för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="f66c1-889">Informations fält 3: Aktuellt antal semaforer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="f66c1-890">Info-fält 4: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="f66c1-891">Hämta semafors information</span><span class="sxs-lookup"><span data-stu-id="f66c1-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="f66c1-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="f66c1-893">**Ikonen** ![ Ikon för Hämta semafors information](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="f66c1-894">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-894">**Description**</span></span>

<span data-ttu-id="f66c1-895">Den här händelsen representerar att hämta information om en semafor via tx_semaphore_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="f66c1-896">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-896">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-897">Info fält 1: pekar mot semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="f66c1-898">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-899">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-900">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="f66c1-901">Hämta information om semafor-prestanda</span><span class="sxs-lookup"><span data-stu-id="f66c1-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="f66c1-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="f66c1-903">**Ikonen** ![ Hämta ikon för semafor-prestanda info](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="f66c1-904">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-904">**Description**</span></span>

<span data-ttu-id="f66c1-905">Den här händelsen representerar att hämta prestanda information om en semafor via tx_semaphore_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="f66c1-906">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-906">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-907">Info fält 1: pekar mot semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="f66c1-908">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-909">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-910">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="f66c1-911">Information om prestanda system för semafor</span><span class="sxs-lookup"><span data-stu-id="f66c1-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="f66c1-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-913">**Ikonen** ![ System informations ikon för semafor-prestanda](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="f66c1-914">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-914">**Description**</span></span>

<span data-ttu-id="f66c1-915">Den här händelsen representerar prestanda information om alla semaforer i systemet via tx_semaphore_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-916">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-916">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-917">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-918">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-919">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-920">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="f66c1-921">Semafor-prioritet</span><span class="sxs-lookup"><span data-stu-id="f66c1-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="f66c1-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f66c1-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="f66c1-923">**Ikonen** ![ Ikon för semafor-prioritet](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="f66c1-924">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-924">**Description**</span></span>

<span data-ttu-id="f66c1-925">Den här händelsen representerar prioriteringen av Semaforens SUS Pension-lista via tx_semaphore_prioritize.</span><span class="sxs-lookup"><span data-stu-id="f66c1-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="f66c1-926">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-926">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-927">Info fält 1: pekare till motsvarande semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="f66c1-928">Informations fält 2: antal trådar som för närvarande har pausats på semaforen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="f66c1-929">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-930">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="f66c1-931">Semafor-placering</span><span class="sxs-lookup"><span data-stu-id="f66c1-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="f66c1-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f66c1-932">tx_semaphore_put</span></span>

<span data-ttu-id="f66c1-933">**Ikonen** ![ Ikon för semafor-placering](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="f66c1-934">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-934">**Description**</span></span>

<span data-ttu-id="f66c1-935">Den här händelsen representerar att släppa en semafor-instans via tx_semaphore_put.</span><span class="sxs-lookup"><span data-stu-id="f66c1-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="f66c1-936">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-936">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-937">Info fält 1: pekare till motsvarande semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="f66c1-938">Informations fält 2: aktuellt semafor-antal.</span><span class="sxs-lookup"><span data-stu-id="f66c1-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="f66c1-939">Informations fält 3: antal pausade trådar i semaforen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="f66c1-940">Info-fält 4: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="f66c1-941">Meddelande om semafors placering</span><span class="sxs-lookup"><span data-stu-id="f66c1-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="f66c1-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f66c1-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="f66c1-943">**Ikonen** ![ Varnings ikon för semafor-placering](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="f66c1-944">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-944">**Description**</span></span>

<span data-ttu-id="f66c1-945">Den här händelsen representerar registrering av ett återanrop via tx_semaphore_put_notify som anropas när en semafors instans placeras.</span><span class="sxs-lookup"><span data-stu-id="f66c1-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="f66c1-946">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-946">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-947">Info fält 1: pekar mot semafor.</span><span class="sxs-lookup"><span data-stu-id="f66c1-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="f66c1-948">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-949">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-950">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="f66c1-951">Skapa tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="f66c1-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-952">tx_thread_create</span></span>

<span data-ttu-id="f66c1-953">**Ikonen** ![ Ikon för tråd skapande](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="f66c1-954">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-954">**Description**</span></span>

<span data-ttu-id="f66c1-955">Den här händelsen representerar skapandet av en tråd via tx_thread_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="f66c1-956">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-956">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-957">Info fält 1: pekare till tråd kontroll block.</span><span class="sxs-lookup"><span data-stu-id="f66c1-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="f66c1-958">Informations fält 2: tråd prioritet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="f66c1-959">Info-fält 3: stack pekare för tråd.</span><span class="sxs-lookup"><span data-stu-id="f66c1-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="f66c1-960">NFO-fält 4: storlek på stack i byte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="f66c1-961">Ta bort tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="f66c1-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-962">tx_thread_delete</span></span>

<span data-ttu-id="f66c1-963">**Ikonen** ![ Ikon för tråd borttagning](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="f66c1-964">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-964">**Description**</span></span>

<span data-ttu-id="f66c1-965">Den här händelsen representerar borttagning av en tråd via tx_thread_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="f66c1-966">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-966">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-967">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-968">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-969">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-970">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="f66c1-971">Avisering om tråd inmatning/avsluta</span><span class="sxs-lookup"><span data-stu-id="f66c1-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="f66c1-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f66c1-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="f66c1-973">**Ikonen** ![ Aviserings ikon för tråd post/avsluta](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="f66c1-974">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-974">**Description**</span></span>

<span data-ttu-id="f66c1-975">Den här händelsen representerar registrering av ett återanrop via tx_thread_entry_exit_notify som anropas när en tråd anges eller avslutas.</span><span class="sxs-lookup"><span data-stu-id="f66c1-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="f66c1-976">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-976">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-977">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-978">Info fält 2: tråd tillstånd vid registreringen.</span><span class="sxs-lookup"><span data-stu-id="f66c1-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="f66c1-979">Info fält 3: pekare till stack vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="f66c1-980">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="f66c1-981">Identifiera tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="f66c1-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f66c1-982">tx_thread_identify</span></span>

<span data-ttu-id="f66c1-983">**Ikonen** ![ Ikon för tråd identifiering](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="f66c1-984">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-984">**Description**</span></span>

<span data-ttu-id="f66c1-985">Den här händelsen representerar hämtning av den aktuella tråd pekaren via tx_thread_identify.</span><span class="sxs-lookup"><span data-stu-id="f66c1-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="f66c1-986">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-986">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-987">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-988">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-989">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-990">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="f66c1-991">Hämta tråd information</span><span class="sxs-lookup"><span data-stu-id="f66c1-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="f66c1-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-992">tx_thread_info_get</span></span>

<span data-ttu-id="f66c1-993">**Ikonen** ![ Ikon för Hämta tråd information](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="f66c1-994">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-994">**Description**</span></span>

<span data-ttu-id="f66c1-995">Den här händelsen representerar att hämta information om den angivna tråden via tx_thread_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="f66c1-996">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-996">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-997">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-998">Informations fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="f66c1-999">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1000">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="f66c1-1001">Hämta information om tråd prestanda</span><span class="sxs-lookup"><span data-stu-id="f66c1-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="f66c1-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="f66c1-1003">**Ikonen** ![ Ikon för att hämta tråd prestanda information](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="f66c1-1004">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1004">**Description**</span></span>

<span data-ttu-id="f66c1-1005">Den här händelsen representerar prestanda information om den angivna tråden via tx_thread_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="f66c1-1006">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1006">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1007">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1008">Informations fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="f66c1-1009">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1010">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="f66c1-1011">Hämta information om tråd prestanda system information</span><span class="sxs-lookup"><span data-stu-id="f66c1-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="f66c1-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-1013">**Ikonen** ![ Hämta ikon för tråd prestanda system information](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="f66c1-1014">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1014">**Description**</span></span>

<span data-ttu-id="f66c1-1015">Den här händelsen representerar prestanda information om alla trådar via tx_thread_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-1016">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1016">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-1017">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-1018">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1019">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1020">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="f66c1-1021">Avstängningen ändring av tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="f66c1-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f66c1-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="f66c1-1023">**Ikonen** ![ Ändra ikon för tråd avstängningen](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="f66c1-1024">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1024">**Description**</span></span>

<span data-ttu-id="f66c1-1025">Den här händelsen representerar ändring av en tråds avstängningen-tröskelvärde via tx_thread_preemption_change.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="f66c1-1026">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1026">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-1027">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1028">Info fält 2: ny avstängningen-tröskel.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="f66c1-1029">Info-fält 3: föregående avstängningen-tröskel.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="f66c1-1030">Info Field 4: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="f66c1-1031">Ändring av tråd prioritet</span><span class="sxs-lookup"><span data-stu-id="f66c1-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="f66c1-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f66c1-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="f66c1-1033">**Ikonen** ![ Ändrings ikon för tråd prioritet](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="f66c1-1034">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1034">**Description**</span></span>

<span data-ttu-id="f66c1-1035">Den här händelsen representerar att ändra en tråds prioritet via tx_thread_priority_change.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="f66c1-1036">Informations fält</span><span class="sxs-lookup"><span data-stu-id="f66c1-1036">Information Fields</span></span> 
- <span data-ttu-id="f66c1-1037">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1038">Info fält 2: ny prioritet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="f66c1-1039">Info-fält 3: föregående prioritet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="f66c1-1040">Info Field 4: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="f66c1-1041">Tråd som låser sig</span><span class="sxs-lookup"><span data-stu-id="f66c1-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="f66c1-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f66c1-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="f66c1-1043">**Ikonen** ![ Ikon för tråd som låser sig](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="f66c1-1044">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1044">**Description**</span></span>

<span data-ttu-id="f66c1-1045">Den här händelsen representerar att lämna processorn från en tråd via tx_thread_relinquish.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="f66c1-1046">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1046">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1047">Info-fält 1: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1048">Info fält 2: pekar mot nästa tråd som ska köras.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="f66c1-1049">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1050">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="f66c1-1051">Återställ tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="f66c1-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f66c1-1052">tx_thread_reset</span></span>

<span data-ttu-id="f66c1-1053">**Ikonen** ![ Ikon för tråd återställning](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="f66c1-1054">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1054">**Description**</span></span>

<span data-ttu-id="f66c1-1055">Den här händelsen representerar återställning av en slutförd eller avslutad tråd via tx_thread_reset.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="f66c1-1056">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1056">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1057">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1058">Info fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="f66c1-1059">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1060">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="f66c1-1061">Återuppta tråd</span><span class="sxs-lookup"><span data-stu-id="f66c1-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="f66c1-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f66c1-1062">tx_thread_resume</span></span>

<span data-ttu-id="f66c1-1063">**Ikonen** ![ Återställnings ikon för tråd](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="f66c1-1064">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1064">**Description**</span></span>

<span data-ttu-id="f66c1-1065">Den här händelsen representerar återuppta en pausad tråd via tx_thread_resume.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="f66c1-1066">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1066">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1067">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1068">Info fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="f66c1-1069">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1070">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="f66c1-1071">Trådens vilo läge</span><span class="sxs-lookup"><span data-stu-id="f66c1-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="f66c1-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f66c1-1072">tx_thread_sleep</span></span>

<span data-ttu-id="f66c1-1073">**Ikonen** ![ Ikon för trådens ström spar läge](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="f66c1-1074">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1074">**Description**</span></span>

<span data-ttu-id="f66c1-1075">Den här händelsen representerar uppehåll i den aktuella tråden för ett angivet antal timer-Tick via tx_thread_sleep.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="f66c1-1076">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1076">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1077">Informations fält 1: antal markeringar som ska pausas.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="f66c1-1078">Info fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="f66c1-1079">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1080">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="f66c1-1081">Meddelande om tråds tack</span><span class="sxs-lookup"><span data-stu-id="f66c1-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="f66c1-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="f66c1-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="f66c1-1083">**Ikonen** ![ Aviserings ikon för tråds tack](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="f66c1-1084">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1084">**Description**</span></span>

<span data-ttu-id="f66c1-1085">Den här händelsen representerar registrering av ett fel meddelande i en tråd stack via tx_thread_stack_error_notify_event.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="f66c1-1086">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1086">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-1087">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-1088">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1089">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1090">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="f66c1-1091">Tråden pausar</span><span class="sxs-lookup"><span data-stu-id="f66c1-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="f66c1-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f66c1-1092">tx_thread_suspend</span></span>

<span data-ttu-id="f66c1-1093">**Ikonen** ![ Ikon för att pausa tråd](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="f66c1-1094">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1094">**Description**</span></span>

<span data-ttu-id="f66c1-1095">Den här händelsen representerar paus av en tråd via tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="f66c1-1096">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1096">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-1097">Info fält 1: pekare till tråd för att pausa.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="f66c1-1098">Info fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="f66c1-1099">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1100">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="f66c1-1101">Tråden avslutas</span><span class="sxs-lookup"><span data-stu-id="f66c1-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="f66c1-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f66c1-1102">tx_thread_terminate</span></span>

<span data-ttu-id="f66c1-1103">**Ikonen** ![ Avsluta ikon för tråd](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="f66c1-1104">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1104">**Description**</span></span>

<span data-ttu-id="f66c1-1105">Den här händelsen representerar att avsluta en tråd via tx_thread_terminate.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="f66c1-1106">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1106">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-1107">Info fält 1: pekare till tråd för att avsluta.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="f66c1-1108">Info fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="f66c1-1109">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1110">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="f66c1-1111">Ändring av tråd Time-Slice</span><span class="sxs-lookup"><span data-stu-id="f66c1-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="f66c1-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f66c1-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="f66c1-1113">**Ikonen** ![ Tråd tids segmentets ändrings ikon](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="f66c1-1114">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1114">**Description**</span></span>

<span data-ttu-id="f66c1-1115">Den här händelsen representerar ändring av en tråds Time-slice via tx_thread_time_slice_change.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="f66c1-1116">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1116">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1117">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1118">Info fält 2: ny Time-slice.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="f66c1-1119">Info-fält 3: föregående Time-slice.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="f66c1-1120">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="f66c1-1121">Avbryt väntan på konversation</span><span class="sxs-lookup"><span data-stu-id="f66c1-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="f66c1-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f66c1-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="f66c1-1123">**Ikonen** ![ Ikon för Avbryt väntan](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="f66c1-1124">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1124">**Description**</span></span>

<span data-ttu-id="f66c1-1125">Den här händelsen representerar avbrott i en tråds fjädring via tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="f66c1-1126">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1126">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1127">Info fält 1: pekare till Thread.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="f66c1-1128">Info fält 2: Trådens tillstånd vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="f66c1-1129">Info-fält 3: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1130">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="f66c1-1131">Hämta tid</span><span class="sxs-lookup"><span data-stu-id="f66c1-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="f66c1-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-1132">tx_time_get</span></span>

<span data-ttu-id="f66c1-1133">**Ikonen** ![ Ikonen Hämta tid](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="f66c1-1134">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1134">**Description**</span></span>

<span data-ttu-id="f66c1-1135">Den här händelsen representerar det aktuella antalet timer-Tick via tx_time_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="f66c1-1136">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1136">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1137">Informations fält 1: Aktuellt antal timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="f66c1-1138">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1139">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1140">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="f66c1-1141">Tids uppsättning</span><span class="sxs-lookup"><span data-stu-id="f66c1-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="f66c1-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="f66c1-1142">tx_time_set</span></span>

<span data-ttu-id="f66c1-1143">**Ikonen** ![ Ikon för tids uppsättning](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="f66c1-1144">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1144">**Description**</span></span>

<span data-ttu-id="f66c1-1145">Den här händelsen representerar att ange det aktuella antalet timer-Tick via tx_time_set.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="f66c1-1146">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1146">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1147">Informations fält 1: nytt antal timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="f66c1-1148">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1149">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1150">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="f66c1-1151">Aktivera timer</span><span class="sxs-lookup"><span data-stu-id="f66c1-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="f66c1-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f66c1-1152">tx_timer_activate</span></span>

<span data-ttu-id="f66c1-1153">**Ikonen** ![ Ikon för aktivering av timer](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="f66c1-1154">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1154">**Description**</span></span>

<span data-ttu-id="f66c1-1155">Den här händelsen representerar aktivering av angiven timer via tx_timer_activate.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="f66c1-1156">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1156">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1157">Info-fält 1: pekar mot timer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="f66c1-1158">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1159">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1160">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="f66c1-1161">Ändring av timer</span><span class="sxs-lookup"><span data-stu-id="f66c1-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="f66c1-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f66c1-1162">tx_timer_change</span></span>

<span data-ttu-id="f66c1-1163">**Ikonen** ![ Ändrings ikon för timer](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="f66c1-1164">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1164">**Description**</span></span>

<span data-ttu-id="f66c1-1165">Den här händelsen representerar att ändra den angivna timern via tx_timer_change.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="f66c1-1166">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1166">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1167">Info-fält 1: pekar mot timer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="f66c1-1168">Info fält 2: Start-utgångs-Tick.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="f66c1-1169">Info-fält 3: schemalägga om förfallo Tick.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="f66c1-1170">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="f66c1-1171">Skapa timer</span><span class="sxs-lookup"><span data-stu-id="f66c1-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="f66c1-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f66c1-1172">tx_timer_create</span></span>

<span data-ttu-id="f66c1-1173">**Ikonen** ![ Ikon för timer-skapande](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="f66c1-1174">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1174">**Description**</span></span>

<span data-ttu-id="f66c1-1175">Den här händelsen representerar skapandet av en timer via tx_timer_create.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="f66c1-1176">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1176">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1177">Informations fält 1: pekar mot timer-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="f66c1-1178">Info fält 2: Start-utgångs-Tick.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="f66c1-1179">Info-fält 3: schemalägga om förfallo Tick.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="f66c1-1180">Info fält 4: automatiskt aktiverings värde – antingen TX_AUTO_ACTIVATE (1) eller TX_NO_ACTIVATE (0).</span><span class="sxs-lookup"><span data-stu-id="f66c1-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="f66c1-1181">Inaktivera timer</span><span class="sxs-lookup"><span data-stu-id="f66c1-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="f66c1-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f66c1-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="f66c1-1183">**Ikonen** ![ Ikonen timer-inaktivera](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="f66c1-1184">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1184">**Description**</span></span>

<span data-ttu-id="f66c1-1185">Den här händelsen representerar inaktive ring av en timer via tx_timer_deactivate.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="f66c1-1186">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1186">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1187">Info-fält 1: pekar mot timer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="f66c1-1188">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1189">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1190">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="f66c1-1191">Borttagning av timer</span><span class="sxs-lookup"><span data-stu-id="f66c1-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="f66c1-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f66c1-1192">tx_timer_delete</span></span>

<span data-ttu-id="f66c1-1193">**Ikonen** ![ Ikon för timer-borttagning](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="f66c1-1194">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1194">**Description**</span></span>

<span data-ttu-id="f66c1-1195">Den här händelsen representerar borttagning av en timer via tx_timer_delete.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="f66c1-1196">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1196">**Information Fields**</span></span> 

- <span data-ttu-id="f66c1-1197">Info-fält 1: pekar mot timer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="f66c1-1198">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1199">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1200">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="f66c1-1201">Hämta timer-information</span><span class="sxs-lookup"><span data-stu-id="f66c1-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="f66c1-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-1202">tx_timer_info_get</span></span>

<span data-ttu-id="f66c1-1203">**Ikonen** ![ Ikon för att hämta information om timer](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="f66c1-1204">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1204">**Description**</span></span>

<span data-ttu-id="f66c1-1205">Den här händelsen representerar information om tidtagare via tx_timer_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="f66c1-1206">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1206">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1207">Info-fält 1: pekar mot timer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="f66c1-1208">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1209">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1210">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="f66c1-1211">Hämta information om timer-prestanda</span><span class="sxs-lookup"><span data-stu-id="f66c1-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="f66c1-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="f66c1-1213">**Ikonen** ![ Ikon för hämtning av timer-prestanda information](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="f66c1-1214">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1214">**Description**</span></span> 

<span data-ttu-id="f66c1-1215">Den här händelsen representerar hämtning av information om timer-prestanda via tx_timer_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="f66c1-1216">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1216">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1217">Info-fält 1: pekar mot timer.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="f66c1-1218">Info fält 2: stack pekare vid tidpunkten för anropet.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="f66c1-1219">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1220">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="f66c1-1221">Hämta timer system prestanda information</span><span class="sxs-lookup"><span data-stu-id="f66c1-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="f66c1-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f66c1-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="f66c1-1223">**Ikonen** ![ Hämta ikon för timer-systemets prestanda information](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="f66c1-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="f66c1-1224">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1224">**Description**</span></span> 

<span data-ttu-id="f66c1-1225">Den här händelsen representerar hämtning av all information om timer-prestanda via tx_timer_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="f66c1-1226">**Informations fält**</span><span class="sxs-lookup"><span data-stu-id="f66c1-1226">**Information Fields**</span></span>

- <span data-ttu-id="f66c1-1227">Informations fält 1: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="f66c1-1228">Informations fält 2: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="f66c1-1229">Informations fält 3: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="f66c1-1230">Info fält 4: används inte.</span><span class="sxs-lookup"><span data-stu-id="f66c1-1230">Info Field 4: Not used.</span></span>