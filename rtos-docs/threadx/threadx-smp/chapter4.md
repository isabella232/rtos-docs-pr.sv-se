---
title: Kapitel 4 – Beskrivning av Azure återställnings tider ThreadX SMP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider ThreadX SMP-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828023"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="e1c06-103">Kapitel 4 – Beskrivning av Azure återställnings tider ThreadX SMP-tjänster</span><span class="sxs-lookup"><span data-stu-id="e1c06-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="e1c06-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider ThreadX SMP-tjänster i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="e1c06-105">Deras namn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="e1c06-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="e1c06-106">I avsnittet "retur värden" i följande beskrivningar påverkas inte värden i **fetstil** av **TX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-kontrollen. värden som visas i fet stil är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e1c06-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="e1c06-107">Dessutom visar rubriken "**Ja**" som visas under rubriken "**avstängningen möjlig**" att anrop till tjänsten kan återuppta en tråd med högre prioritet, vilket innebär att den anropande tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="e1c06-108">**tx_block_allocate**: *allokera minnes block med fast storlek*</span><span class="sxs-lookup"><span data-stu-id="e1c06-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="e1c06-109">**tx_block_pool_create**: *Skapa pool med minnes block med fast storlek*</span><span class="sxs-lookup"><span data-stu-id="e1c06-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="e1c06-110">**tx_block_pool_delete**: *ta bort minnes block pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="e1c06-111">**tx_block_pool_info_get**: *Hämta information om block pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="e1c06-112">**tx_block_pool_performance_info_get**: *Hämta prestanda information för block pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="e1c06-113">**tx_block_pool_performance_system_info_get**: *Hämta information om system prestanda för block pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="e1c06-114">**tx_block_pool_prioritize**: *prioritera avstängnings lista för block-pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="e1c06-115">**tx_block_release**: *frigör block med fast storlek i minnet*</span><span class="sxs-lookup"><span data-stu-id="e1c06-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="e1c06-116">**tx_byte_allocate**: *allokera byte minne*</span><span class="sxs-lookup"><span data-stu-id="e1c06-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="e1c06-117">**tx_byte_pool_create**: *skapa en lagringspool med byte*</span><span class="sxs-lookup"><span data-stu-id="e1c06-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="e1c06-118">**tx_byte_pool_delete**: *ta bort minnes byte pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="e1c06-119">**tx_byte_pool_info_get**: *Hämta information om en byte-pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="e1c06-120">**tx_byte_pool_performance_info_get**: *prestanda information för Hämta byte-pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="e1c06-121">**tx_byte_pool_performance_system_info_get**: *Hämta information om prestanda för byte pool system*</span><span class="sxs-lookup"><span data-stu-id="e1c06-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="e1c06-122">**tx_byte_pool_prioritize**: *prioritera överskjutande lista för byte-pool*</span><span class="sxs-lookup"><span data-stu-id="e1c06-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="e1c06-123">**tx_byte_release**: *release byte tillbaka till mediepoolen*</span><span class="sxs-lookup"><span data-stu-id="e1c06-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="e1c06-124">**tx_event_flags_create**: *Skapa händelse flaggor grupp*</span><span class="sxs-lookup"><span data-stu-id="e1c06-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="e1c06-125">**tx_event_flags_delete**: *ta bort händelse flaggor grupp*</span><span class="sxs-lookup"><span data-stu-id="e1c06-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="e1c06-126">**tx_event_flags_get**: *Hämta händelse flaggor från gruppen med händelse flaggor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="e1c06-127">**tx_event_flags_info_get**: *Hämta information om händelse flaggor gruppen*</span><span class="sxs-lookup"><span data-stu-id="e1c06-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="e1c06-128">**tx_event_flags_performance_info_get**: *Hämta händelse flaggor grupp prestanda information*</span><span class="sxs-lookup"><span data-stu-id="e1c06-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="e1c06-129">**tx_event_flags_performance_system_info_get**: *Hämta information om prestanda systemet*</span><span class="sxs-lookup"><span data-stu-id="e1c06-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="e1c06-130">**tx_event_flags_set**: *Ange händelse flaggor i en grupp med händelse flaggor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="e1c06-131">**tx_event_flags_set_notify**: *meddela program när händelse flaggor anges*</span><span class="sxs-lookup"><span data-stu-id="e1c06-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="e1c06-132">**tx_interrupt_control**: *Aktivera och inaktivera avbrott*</span><span class="sxs-lookup"><span data-stu-id="e1c06-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="e1c06-133">**tx_mutex_create**: *skapa ömsesidigt uteslutande mutex*</span><span class="sxs-lookup"><span data-stu-id="e1c06-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="e1c06-134">**tx_mutex_delete**: *ta bort ömsesidigt uteslutande mutex*</span><span class="sxs-lookup"><span data-stu-id="e1c06-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="e1c06-135">**tx_mutex_get**: *få ägande rätt till mutex*</span><span class="sxs-lookup"><span data-stu-id="e1c06-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="e1c06-136">**tx_mutex_info_get**: *Hämta information om mutex*</span><span class="sxs-lookup"><span data-stu-id="e1c06-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="e1c06-137">**tx_mutex_performance_info_get**: *Hämta information om mutex-prestanda*</span><span class="sxs-lookup"><span data-stu-id="e1c06-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="e1c06-138">**tx_mutex_performance_system_info_get**: *Hämta information om prestanda för mutex-system*</span><span class="sxs-lookup"><span data-stu-id="e1c06-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="e1c06-139">**tx_mutex_prioritize**: *prioritera mutex SUS pensions lista*</span><span class="sxs-lookup"><span data-stu-id="e1c06-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="e1c06-140">**tx_mutex_put**: *frigör ägarskap för mutex*</span><span class="sxs-lookup"><span data-stu-id="e1c06-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="e1c06-141">**tx_queue_create**: *skapa meddelandekö*</span><span class="sxs-lookup"><span data-stu-id="e1c06-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="e1c06-142">**tx_queue_delete**: *ta bort meddelande kön*</span><span class="sxs-lookup"><span data-stu-id="e1c06-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="e1c06-143">**tx_queue_flush**: *tomma meddelanden i meddelande kön*</span><span class="sxs-lookup"><span data-stu-id="e1c06-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="e1c06-144">**tx_queue_front_send**: *Skicka meddelande till kön längst fram*</span><span class="sxs-lookup"><span data-stu-id="e1c06-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="e1c06-145">**tx_queue_info_get**: *Hämta information om kö*</span><span class="sxs-lookup"><span data-stu-id="e1c06-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="e1c06-146">**tx_queue_performance_info_get**: *Hämta prestanda information för kö*</span><span class="sxs-lookup"><span data-stu-id="e1c06-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="e1c06-147">**tx_queue_performance_system_info_get**: *Hämta prestanda information för Queue system*</span><span class="sxs-lookup"><span data-stu-id="e1c06-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="e1c06-148">**tx_queue_prioritize**: *prioritera en lista över återkallade köer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="e1c06-149">**tx_queue_receive**: *Hämta meddelande från meddelandekö*</span><span class="sxs-lookup"><span data-stu-id="e1c06-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="e1c06-150">**tx_queue_send**: *Skicka meddelande till meddelande kön*</span><span class="sxs-lookup"><span data-stu-id="e1c06-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="e1c06-151">**tx_queue_send_notify**: *meddela programmet när ett meddelande skickas till kön*</span><span class="sxs-lookup"><span data-stu-id="e1c06-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="e1c06-152">**tx_semaphore_ceiling_put**: *Placera en instans i räkna semaforen med tak*</span><span class="sxs-lookup"><span data-stu-id="e1c06-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="e1c06-153">**tx_semaphore_create**: *skapa inventering av semafor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="e1c06-154">**tx_semaphore_delete**: *ta bort inventering semafor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="e1c06-155">**tx_semaphore_get**: *Hämta instans från semafor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="e1c06-156">**tx_semaphore_info_get**: *Hämta information om semaforen*</span><span class="sxs-lookup"><span data-stu-id="e1c06-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="e1c06-157">**tx_semaphore_performance_info_get**: *Hämta information om semafor-prestanda*</span><span class="sxs-lookup"><span data-stu-id="e1c06-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="e1c06-158">**tx_semaphore_performance_system_info_get**: *Hämta information om prestanda för semafor-systemet*</span><span class="sxs-lookup"><span data-stu-id="e1c06-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="e1c06-159">**tx_semaphore_prioritize**: *prioritera semafor SUS Pension lista*</span><span class="sxs-lookup"><span data-stu-id="e1c06-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="e1c06-160">**tx_semaphore_put**: *Placera en instans i inventering av semafor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="e1c06-161">**tx_semaphore_put_notify**: *meddela programmet när semaforen placeras*</span><span class="sxs-lookup"><span data-stu-id="e1c06-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="e1c06-162">**tx_thread_create**: *skapa program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="e1c06-163">**tx_thread_delete**: *ta bort program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="e1c06-164">**tx_thread_entry_exit_notify**: *meddela programmet vid tråd inmatning och avsluta*</span><span class="sxs-lookup"><span data-stu-id="e1c06-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="e1c06-165">**tx_thread_identify**: *hämtar pekare till tråd som körs för tillfället*</span><span class="sxs-lookup"><span data-stu-id="e1c06-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="e1c06-166">**tx_thread_info_get**: *Hämta information om tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="e1c06-167">**tx_thread_performance_info_get**: *Hämta information om tråd prestanda*</span><span class="sxs-lookup"><span data-stu-id="e1c06-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="e1c06-168">**tx_thread_performance_system_info_get**: *Hämta information om tråd system prestanda*</span><span class="sxs-lookup"><span data-stu-id="e1c06-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="e1c06-169">**tx_thread_preemption_change**: *ändra avstängningen-tröskel för program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="e1c06-170">**tx_thread_priority_change**: *ändra prioritet för program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="e1c06-171">**tx_thread_relinquish**: lämna *kontroll över andra program trådar*</span><span class="sxs-lookup"><span data-stu-id="e1c06-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="e1c06-172">**tx_thread_reset**: *Återställ tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="e1c06-173">**tx_thread_resume**: *återuppta inaktive rad program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="e1c06-174">**tx_thread_sleep**: *pausa den aktuella tråden för angiven tid*</span><span class="sxs-lookup"><span data-stu-id="e1c06-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="e1c06-175">**tx_thread_smp_core_exclude**: *exkludera tråd körning på en uppsättning kärnor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="e1c06-176">**tx_thread_smp_core_exclude_get**: *hämtar trådens aktuella kärn undantag*</span><span class="sxs-lookup"><span data-stu-id="e1c06-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="e1c06-177">**tx_thread_smp_core_get**: *Hämta kärnan för anroparen som körs*</span><span class="sxs-lookup"><span data-stu-id="e1c06-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="e1c06-178">**tx_thread_stack_error_notify**: *Registrera ett återanrop i tråds tack* rings meddelande</span><span class="sxs-lookup"><span data-stu-id="e1c06-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="e1c06-179">**tx_thread_suspend**: *pausa program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="e1c06-180">**tx_thread_terminate**: *avslutar program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="e1c06-181">**tx_thread_time_slice_change**: *ändrar time-slice för program tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="e1c06-182">**tx_thread_wait_abort**: *Avbryt avstängning av angiven tråd*</span><span class="sxs-lookup"><span data-stu-id="e1c06-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="e1c06-183">**tx_time_get**: *hämtar aktuell tid*</span><span class="sxs-lookup"><span data-stu-id="e1c06-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="e1c06-184">**tx_time_set**: *anger aktuell tid*</span><span class="sxs-lookup"><span data-stu-id="e1c06-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="e1c06-185">**tx_timer_activate**: *Aktivera programtimer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="e1c06-186">**tx_timer_change**: *ändra programmets timer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="e1c06-187">**tx_timer_create**: *skapa programtimer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="e1c06-188">**tx_timer_deactivate**: *inaktivera Application timer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="e1c06-189">**tx_timer_delete**: *ta bort program timer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="e1c06-190">**tx_timer_info_get**: *Hämta information om en program-timer*</span><span class="sxs-lookup"><span data-stu-id="e1c06-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="e1c06-191">**tx_timer_performance_info_get**: *Hämta information om timer-prestanda*</span><span class="sxs-lookup"><span data-stu-id="e1c06-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="e1c06-192">**tx_timer_performance_system_info_get**: *Hämta timer-systemets prestanda information*</span><span class="sxs-lookup"><span data-stu-id="e1c06-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="e1c06-193">**tx_timer_smp_core_exclude**: *utesluta timer-körning i en uppsättning kärnor*</span><span class="sxs-lookup"><span data-stu-id="e1c06-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="e1c06-194">**tx_timer_smp_core_exclude_get**: *hämtar timerns aktuella kärn undantag*</span><span class="sxs-lookup"><span data-stu-id="e1c06-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="e1c06-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-195">tx_block_allocate</span></span>
<span data-ttu-id="e1c06-196">Allokera minnes block med fast storlek</span><span class="sxs-lookup"><span data-stu-id="e1c06-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-197">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-198">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-198">Description</span></span>

<span data-ttu-id="e1c06-199">Den här tjänsten allokerar ett minnes block med fast storlek från den angivna lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="e1c06-200">Minnes blockets faktiska storlek bestäms när minnesbufferten skapas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="e1c06-201">Det är viktigt att se till att program koden inte skriver utanför det allokerade minnes blocket.</span><span class="sxs-lookup"><span data-stu-id="e1c06-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="e1c06-202">Om detta inträffar inträffar skada i ett intilliggande (vanligt vis) minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="e1c06-203">Resultatet är oförutsägbart och är ofta allvarligt!</span><span class="sxs-lookup"><span data-stu-id="e1c06-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-204">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-204">Parameters</span></span>

- <span data-ttu-id="e1c06-205">**pool_ptr**: pekar mot en tidigare skapad pool för minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="e1c06-206">**block_ptr**: pekar mot en mål Blocks pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="e1c06-207">Vid lyckad allokering placeras adressen till det allokerade minnes blocket där den här parametern pekar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="e1c06-208">**wait_option**: definierar hur tjänsten fungerar om det inte finns några tillgängliga minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="e1c06-209">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-210">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-212">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="e1c06-213">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="e1c06-214">Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="e1c06-215">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden i oändlighet tills ett minnes block är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="e1c06-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="e1c06-216">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på ett minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-217">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-217">Return Values</span></span>

- <span data-ttu-id="e1c06-218">**TX_SUCCESS**: (0X00) lyckad minnes Blocks tilldelning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="e1c06-219">**TX_DELETED**: (0X01) minnes Blocks gruppen togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-220">**TX_NO_MEMORY**: (0X10) tjänsten kunde inte allokera ett minnes block inom den angivna tiden till väntan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-221">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="e1c06-222">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="e1c06-223">TX_PTR_ERROR: (0x03) ogiltig pekare till mål pekaren.</span><span class="sxs-lookup"><span data-stu-id="e1c06-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="e1c06-224">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-225">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-225">Allowed From</span></span>

<span data-ttu-id="e1c06-226">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-227">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-227">Preemption Possible</span></span>

<span data-ttu-id="e1c06-228">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-229">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-229">Example</span></span>

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="e1c06-230">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-230">See Also</span></span>

- <span data-ttu-id="e1c06-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-231">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="e1c06-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-238">tx_block_pool_create</span></span>
<span data-ttu-id="e1c06-239">Skapa pool med minnes block med fast storlek</span><span class="sxs-lookup"><span data-stu-id="e1c06-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-240">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="e1c06-241">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-241">Description</span></span>

<span data-ttu-id="e1c06-242">Den här tjänsten skapar en pool med minnes block med fast storlek.</span><span class="sxs-lookup"><span data-stu-id="e1c06-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="e1c06-243">Det angivna minnes området är indelat i så många minnes block med fast storlek som möjligt med hjälp av formeln:</span><span class="sxs-lookup"><span data-stu-id="e1c06-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="e1c06-244">**Totalt antal block** = (**Totalt antal byte**)/(**block storlek** + sizeof (void \*))</span><span class="sxs-lookup"><span data-stu-id="e1c06-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-245">Varje minnes block innehåller en pekare som är dold för användaren och representeras av "sizeof (void \*)" i föregående formel.</span><span class="sxs-lookup"><span data-stu-id="e1c06-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-246">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-246">Parameters</span></span>

- <span data-ttu-id="e1c06-247">**pool_ptr**: pekar mot ett kontroll block för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="e1c06-248">**name_ptr**: pekar mot namnet på minnes Blocks-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="e1c06-249">**block_size**: antal byte i varje minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="e1c06-250">**pool_start**: Start adress för minnes Blocks gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="e1c06-251">Start adressen måste vara justerad till storleken på data typen ULONG..</span><span class="sxs-lookup"><span data-stu-id="e1c06-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="e1c06-252">**pool_size**: totalt antal byte som är tillgängliga för minnes Blocks gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-253">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-253">Return Values</span></span>

- <span data-ttu-id="e1c06-254">**TX_SUCCESS**: (0X00) lyckad generering av minnes Blocks pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="e1c06-255">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="e1c06-256">Antingen är pekaren NULL eller också har poolen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="e1c06-257">TX_PTR_ERROR: (0x03) ogiltig start adress för poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="e1c06-258">TX_SIZE_ERROR: (0x05) storleken på poolen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="e1c06-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="e1c06-259">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-260">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-260">Allowed From</span></span>

<span data-ttu-id="e1c06-261">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-262">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-262">Preemption Possible</span></span>

<span data-ttu-id="e1c06-263">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-263">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-264">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-264">Example</span></span>

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-265">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-265">See Also</span></span>

- <span data-ttu-id="e1c06-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-266">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="e1c06-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-273">tx_block_pool_delete</span></span>

<span data-ttu-id="e1c06-274">Ta bort pool för minnes block</span><span class="sxs-lookup"><span data-stu-id="e1c06-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-275">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-276">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-276">Description</span></span>

<span data-ttu-id="e1c06-277">Den här tjänsten tar bort den angivna block minnes poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="e1c06-278">Alla trådar som pausas i väntan på ett minnes block från den här poolen återupptas och får en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="e1c06-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-279">Det är programmets ansvar att hantera det minnes område som är associerat med poolen, vilket är tillgängligt när tjänsten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="e1c06-280">Dessutom måste programmet förhindra att en borttagen pool eller de tidigare minnes blocken används.</span><span class="sxs-lookup"><span data-stu-id="e1c06-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-281">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-281">Parameters</span></span>

- <span data-ttu-id="e1c06-282">**pool_ptr**: pekar mot en tidigare skapad pool för minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-283">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-283">Return Values</span></span>

- <span data-ttu-id="e1c06-284">**TX_SUCCESS**: (0X00) lyckad borttagning av minnes Blocks pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="e1c06-285">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="e1c06-286">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-287">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-287">Allowed From</span></span>

<span data-ttu-id="e1c06-288">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-289">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-289">Preemption Possible</span></span>

<span data-ttu-id="e1c06-290">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-291">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-291">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-292">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-292">See Also</span></span>

- <span data-ttu-id="e1c06-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-293">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-294">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="e1c06-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="e1c06-301">Hämta information om blockera pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-302">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="e1c06-303">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-303">Description</span></span>

<span data-ttu-id="e1c06-304">Den här tjänsten hämtar information om den angivna block minnes poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-305">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-305">Parameters</span></span>

- <span data-ttu-id="e1c06-306">**pool_ptr**: pekare till tidigare skapade minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="e1c06-307">**Name**: pekare till målet för visaren i block poolens namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="e1c06-308">**tillgängligt**: pekare till målet för antalet tillgängliga block i den blockerande poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="e1c06-309">**total_blocks**: pekar mot mål för det totala antalet block i block poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="e1c06-310">**first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över avbrytande av den här block-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="e1c06-311">**suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på den här block-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="e1c06-312">**next_pool**: pekar mot destinationen för en pekare på nästa skapade block-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-313">Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e1c06-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-314">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-314">Return Values</span></span>

- <span data-ttu-id="e1c06-315">**TX_SUCCESS**: (0x00) Det gick inte att hämta information om block pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="e1c06-316">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-317">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-317">Allowed From</span></span>

<span data-ttu-id="e1c06-318">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-319">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-319">Example</span></span>

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-320">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-320">See Also</span></span>

- <span data-ttu-id="e1c06-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-321">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-322">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="e1c06-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="e1c06-330">Hämta prestanda information för block pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-331">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="e1c06-332">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-332">Description</span></span>

<span data-ttu-id="e1c06-333">Den här tjänsten hämtar prestanda information om den angivna Memory block-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-334">ThreadX SMP-biblioteket och programmet måste skapas med **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-335">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-335">Parameters</span></span>

- <span data-ttu-id="e1c06-336">**pool_ptr**: pekare till tidigare skapade minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="e1c06-337">**allokerar**: pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="e1c06-338">**versioner**: pekare till målet för antalet release-begäranden som har utförts på den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="e1c06-339">**SUS pensioner**: pekare till målet för antalet avbrott i tråd tilldelningen för den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="e1c06-340">**timeout**: pekar mot målets antal tids gräns värden för att allokera uppehåll i poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-341">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-342">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-342">Return Values</span></span>

- <span data-ttu-id="e1c06-343">**TX_SUCCESS**: (0x00) prestanda för slutförd block pool har hämtats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="e1c06-344">**TX_PTR_ERROR**: (0X03) ogiltig pekare för att blockera poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="e1c06-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-346">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-346">Allowed From</span></span>

<span data-ttu-id="e1c06-347">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-348">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-348">Example</span></span>

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-349">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-349">See Also</span></span>

- <span data-ttu-id="e1c06-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-350">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-351">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="e1c06-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="e1c06-358">Hämta information om system prestanda för block pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-359">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-360">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-360">Description</span></span>

<span data-ttu-id="e1c06-361">Den här tjänsten hämtar prestanda information om alla minnes Blocks pooler i programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-362">ThreadX SMP-biblioteket och programmet måste skapas med **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-363">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-363">Parameters</span></span>

- <span data-ttu-id="e1c06-364">**allokerar**: pekar mot mål för det totala antalet allokerade begär Anden som utförts på alla blockerade pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="e1c06-365">**versioner**: pekare till målet för det totala antalet begär Anden som har utförts på alla blockerade pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="e1c06-366">**SUS pensioner**: pekar mot mål för det totala antalet SUS pensioner i alla block-pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="e1c06-367">**timeout**: pekar mot mål för det totala antalet tids gränser för att allokera uppehåll i alla block-pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-368">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-369">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-369">Return Values</span></span>

- <span data-ttu-id="e1c06-370">**TX_SUCCESS**: (0X00) slutförd blockering av system prestanda för poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="e1c06-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-372">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-372">Allowed From</span></span>

<span data-ttu-id="e1c06-373">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-374">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-374">Example</span></span>

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-375">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-375">See Also</span></span>

- <span data-ttu-id="e1c06-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-376">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-377">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="e1c06-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="e1c06-384">Prioritera spärr lista för block-pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-385">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-386">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-386">Description</span></span>

<span data-ttu-id="e1c06-387">Den här tjänsten placerar tråden med högsta prioritet inaktive rad för ett minnes block på den här poolen längst fram i listan över SUS pensioner.</span><span class="sxs-lookup"><span data-stu-id="e1c06-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="e1c06-388">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-389">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-389">Parameters</span></span> 

- <span data-ttu-id="e1c06-390">**pool_ptr**: pekar mot ett kontroll block för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-391">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-391">Return Values</span></span>

- <span data-ttu-id="e1c06-392">**TX_SUCCESS**: (0x00) prioritet för att blockera poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="e1c06-393">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-394">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-394">Allowed From</span></span>

<span data-ttu-id="e1c06-395">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-396">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-396">Preemption Possible</span></span>

<span data-ttu-id="e1c06-397">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-397">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-398">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-398">Example</span></span>

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-399">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-399">See Also</span></span>

- <span data-ttu-id="e1c06-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-400">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-401">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="e1c06-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-407">tx_block_release</span></span>

<span data-ttu-id="e1c06-408">Frigör block med fast storlek i minnet</span><span class="sxs-lookup"><span data-stu-id="e1c06-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-409">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-410">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-410">Description</span></span>

<span data-ttu-id="e1c06-411">Den här tjänsten släpper ett tidigare allokerat block tillbaka till den kopplade poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="e1c06-412">Om det finns en eller flera trådar som pausas i väntan på minnes block från den här poolen, är den första tråden inaktive rad det här minnes blocket och återupptas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-413">Programmet måste förhindra att ett minnes Blocks utrymme används när det har släppts tillbaka till poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-414">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-414">Parameters</span></span>

- <span data-ttu-id="e1c06-415">**block_ptr**: pekar mot det tidigare allokerade minnes blocket.</span><span class="sxs-lookup"><span data-stu-id="e1c06-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-416">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-416">Return Values</span></span>

- <span data-ttu-id="e1c06-417">**TX_SUCCESS**: (0X00) lyckad minnes Blocks version.</span><span class="sxs-lookup"><span data-stu-id="e1c06-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="e1c06-418">TX_PTR_ERROR: (0x03) ogiltig pekare till minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-419">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-419">Allowed From</span></span>

<span data-ttu-id="e1c06-420">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-421">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-421">Preemption Possible</span></span>

<span data-ttu-id="e1c06-422">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-423">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-423">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-424">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-424">See Also</span></span>

- <span data-ttu-id="e1c06-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-425">tx_block_allocate</span></span>
- <span data-ttu-id="e1c06-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-426">tx_block_pool_create</span></span>
- <span data-ttu-id="e1c06-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="e1c06-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="e1c06-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="e1c06-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-432">tx_byte_allocate</span></span>

<span data-ttu-id="e1c06-433">Allokera byte minne</span><span class="sxs-lookup"><span data-stu-id="e1c06-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-434">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-435">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-435">Description</span></span>

<span data-ttu-id="e1c06-436">Den här tjänsten allokerar det angivna antalet byte från den angivna Memory byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="e1c06-437">Det är viktigt att se till att program koden inte skriver utanför det allokerade minnes blocket.</span><span class="sxs-lookup"><span data-stu-id="e1c06-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="e1c06-438">Om detta inträffar inträffar skada i ett intilliggande (vanligt vis) minnes block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="e1c06-439">Resultatet är oförutsägbart och är ofta allvarligt!</span><span class="sxs-lookup"><span data-stu-id="e1c06-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-440">Prestanda för den här tjänsten är en funktion i block storlek och fragmenteringen i poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="e1c06-441">Därför bör den här tjänsten inte användas under tids kritiska körnings trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-442">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-442">Parameters</span></span>

- <span data-ttu-id="e1c06-443">**pool_ptr**: pekar mot en tidigare skapad lagringspool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="e1c06-444">**memory_ptr**: pekar mot en mål minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="e1c06-445">Vid lyckad allokering placeras adressen till det allokerade minnes området där parametern pekar på.</span><span class="sxs-lookup"><span data-stu-id="e1c06-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="e1c06-446">**memory_size**: antal byte som har begärts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="e1c06-447">**wait_option**: definierar hur tjänsten fungerar om det inte finns tillräckligt med minne tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="e1c06-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="e1c06-448">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-449">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-451">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-452">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-453">*Detta är det enda giltiga alternativet om tjänsten anropas från initiering.*</span><span class="sxs-lookup"><span data-stu-id="e1c06-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="e1c06-454">Om du väljer TX_WAIT_FOREVER avbryts anrops tråden till oändligt tills tillräckligt med minne är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="e1c06-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="e1c06-455">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på minnet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-456">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-456">Return Values</span></span>

- <span data-ttu-id="e1c06-457">**TX_SUCCESS**: (0X00) lyckad minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="e1c06-458">**TX_DELETED**: (0x01)-mediepoolen togs bort medan tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-459">**TX_NO_MEMORY**: tjänsten (0x10) kunde inte allokera minne inom den angivna tiden till väntan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-460">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-461">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="e1c06-462">TX_PTR_ERROR: (0x03) ogiltig pekare till mål pekaren.</span><span class="sxs-lookup"><span data-stu-id="e1c06-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="e1c06-463">TX_SIZE_ERROR: (0X05) den begärda storleken är noll eller större än poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="e1c06-464">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="e1c06-465">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-466">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-466">Allowed From</span></span>

<span data-ttu-id="e1c06-467">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-468">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-468">Preemption Possible</span></span>

<span data-ttu-id="e1c06-469">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-470">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-470">Example</span></span>

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-471">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-471">See Also</span></span>

- <span data-ttu-id="e1c06-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="e1c06-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-479">tx_byte_pool_create</span></span>

<span data-ttu-id="e1c06-480">Skapa minnes-pool med byte</span><span class="sxs-lookup"><span data-stu-id="e1c06-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-481">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="e1c06-482">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-482">Description</span></span>

<span data-ttu-id="e1c06-483">Den här tjänsten skapar en pool för minnes byte i det angivna området.</span><span class="sxs-lookup"><span data-stu-id="e1c06-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="e1c06-484">Från början består poolen av i princip ett mycket stort ledigt block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="e1c06-485">Poolen är dock bruten i mindre block som tilldelningar görs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-486">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-486">Parameters</span></span>

- <span data-ttu-id="e1c06-487">**pool_ptr**: pekar mot ett kontroll block för minnes-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="e1c06-488">**name_ptr**: pekar mot namnet på mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="e1c06-489">**pool_start**: Start adress för mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="e1c06-490">Start adressen måste vara justerad till storleken på data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="e1c06-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="e1c06-491">**pool_size**: totalt antal byte som är tillgängliga för lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-492">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-492">Return Values</span></span>

- <span data-ttu-id="e1c06-493">**TX_SUCCESS**: (0X00) lyckad minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="e1c06-494">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="e1c06-495">Antingen är pekaren NULL eller också har poolen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="e1c06-496">TX_PTR_ERROR: (0x03) ogiltig start adress för poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="e1c06-497">TX_SIZE_ERROR: (0x05) storleken på poolen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="e1c06-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="e1c06-498">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-499">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-499">Allowed From</span></span>

<span data-ttu-id="e1c06-500">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-501">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-501">Preemption Possible</span></span>

<span data-ttu-id="e1c06-502">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-502">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-503">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-503">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-504">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-504">See Also</span></span>

- <span data-ttu-id="e1c06-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-505">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="e1c06-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="e1c06-513">Ta bort minnes byte pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-514">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-515">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-515">Description</span></span>

<span data-ttu-id="e1c06-516">Den här tjänsten tar bort den angivna minnes bytes poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="e1c06-517">Alla trådar som pausas i väntan på minne från den här poolen återupptas och har en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="e1c06-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-518">Det är programmets ansvar att hantera det minnes område som är associerat med poolen, vilket är tillgängligt när tjänsten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="e1c06-519">Dessutom måste programmet förhindra användning av en borttagen pool eller minne som tidigare har allokerats från den.</span><span class="sxs-lookup"><span data-stu-id="e1c06-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-520">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-520">Parameters</span></span> 

- <span data-ttu-id="e1c06-521">**pool_ptr**: pekar mot en tidigare skapad lagringspool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-522">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-522">Return Values</span></span>

- <span data-ttu-id="e1c06-523">**TX_SUCCESS**: (0X00) slutförd borttagning av minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="e1c06-524">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="e1c06-525">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-526">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-526">Allowed From</span></span>

<span data-ttu-id="e1c06-527">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-528">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-528">Preemption Possible</span></span>

<span data-ttu-id="e1c06-529">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-530">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-531">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-531">See Also</span></span>

- <span data-ttu-id="e1c06-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-532">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="e1c06-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="e1c06-540">Hämta information om byte-poolen</span><span class="sxs-lookup"><span data-stu-id="e1c06-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-541">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="e1c06-542">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-542">Description</span></span>

<span data-ttu-id="e1c06-543">Den här tjänsten hämtar information om den angivna minnes bytes poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-544">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-544">Parameters</span></span>

- <span data-ttu-id="e1c06-545">**pool_ptr**: pekare till den tidigare skapade lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="e1c06-546">**Name**: pekare till målet för visaren i byte-poolens namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="e1c06-547">**tillgängligt**: pekare till målet för antalet tillgängliga byte i poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="e1c06-548">**fragment**: pekar mot mål för det totala antalet minnes fragment i byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="e1c06-549">**first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över återkallade byte för denna byte-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="e1c06-550">**suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats i den här byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="e1c06-551">**next_pool**: pekar mot destinationen för en pekare på nästa skapade byte-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-552">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-553">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-553">Return Values</span></span>

- <span data-ttu-id="e1c06-554">**TX_SUCCESS**: (0X00) lyckades hämta information om poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="e1c06-555">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-556">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-556">Allowed From</span></span>

<span data-ttu-id="e1c06-557">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-558">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-558">Preemption Possible</span></span>

<span data-ttu-id="e1c06-559">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-559">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-560">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-560">Example</span></span>

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-561">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-561">See Also</span></span>

- <span data-ttu-id="e1c06-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-562">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="e1c06-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="e1c06-570">Hämta prestanda information för byte-pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-571">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-572">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-572">Description</span></span>

<span data-ttu-id="e1c06-573">Den här tjänsten hämtar prestanda information om den angivna minnes bytes poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-574">ThreadX SMP-biblioteket och programmet måste skapas med **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-575">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-575">Parameters</span></span>

- <span data-ttu-id="e1c06-576">**pool_ptr**: pekar mot tidigare skapade minnes byte pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="e1c06-577">**allokerar**: pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="e1c06-578">**versioner**: pekare till målet för antalet release-begäranden som har utförts på den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="e1c06-579">**fragments_searched**: pekar mot mål för antalet interna minnes fragment som genomsöks under tilldelnings begär anden i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="e1c06-580">**sammanslagningar**: pekare till målet för antalet interna minnes block som sammanfogas under tilldelnings begär anden i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="e1c06-581">**delningar**: pekare till målet för antalet interna minnes block delning (fragment) som skapas vid tilldelnings begär anden i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="e1c06-582">**SUS pensioner**: pekare till målet för antalet avbrott i tråd tilldelningen för den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="e1c06-583">**timeout**: pekar mot målets antal tids gräns värden för att allokera uppehåll i poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-584">Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e1c06-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-585">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-585">Return Values</span></span>

- <span data-ttu-id="e1c06-586">TX_SUCCESS: (0x00) prestanda för slutförd byte-pool har hämtats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="e1c06-587">**TX_PTR_ERROR**: (0X03) ogiltig pekare för byte-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="e1c06-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-589">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-589">Allowed From</span></span>

<span data-ttu-id="e1c06-590">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-591">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-591">Example</span></span>

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-592">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-592">See Also</span></span>

- <span data-ttu-id="e1c06-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-593">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="e1c06-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="e1c06-601">Hämta information om prestanda för byte pool system</span><span class="sxs-lookup"><span data-stu-id="e1c06-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-602">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="e1c06-603">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-603">Description</span></span>

<span data-ttu-id="e1c06-604">Den här tjänsten hämtar prestanda information om alla minnes byte pooler i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-605">ThreadX SMP-biblioteket och programmet måste skapas med **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-606">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-606">Parameters</span></span>

- <span data-ttu-id="e1c06-607">**allokerar**: pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="e1c06-608">**versioner**: pekare till målet för antalet release-begäranden som har utförts på den här poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="e1c06-609">**fragments_searched**: pekar mot mål för det totala antalet interna minnes fragment som genomsöks under tilldelnings begär Anden för alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="e1c06-610">**sammanslagningar**: pekare till mål för det totala antalet interna minnes block som sammanfogas under tilldelnings begär Anden för alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="e1c06-611">**delningar**: pekar mot mål för det totala antalet interna minnes block delning (fragment) som skapas vid tilldelnings begär Anden för alla byte pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="e1c06-612">**SUS pensioner**: pekar mot mål för det totala antalet SUS pensioner i alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="e1c06-613">**tids gränser**: pekar mot mål för det totala antalet tids gränser för att allokera uppehåll i alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="e1c06-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-614">Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e1c06-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-615">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-615">Return Values</span></span>

- <span data-ttu-id="e1c06-616">**TX_SUCCESS**: (0x00) prestanda för slutförd byte-pool har hämtats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="e1c06-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-618">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-618">Allowed From</span></span>

<span data-ttu-id="e1c06-619">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-620">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-620">Example</span></span>

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-621">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-621">See Also</span></span>

- <span data-ttu-id="e1c06-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-622">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="e1c06-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="e1c06-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="e1c06-630">Prioritera överskjutande lista för byte-pool</span><span class="sxs-lookup"><span data-stu-id="e1c06-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-631">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-632">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-632">Description</span></span>

<span data-ttu-id="e1c06-633">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för minne på den här poolen överst i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="e1c06-634">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-635">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-635">Parameters</span></span> 

- <span data-ttu-id="e1c06-636">**pool_ptr**: pekar mot ett kontroll block för minnes-pool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-637">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-637">Return Values</span></span>

- <span data-ttu-id="e1c06-638">**TX_SUCCESS**: (0X00) lyckad minnes uppsättnings prioritet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="e1c06-639">TX_POOL_ERROR: (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="e1c06-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-640">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-640">Allowed From</span></span>

<span data-ttu-id="e1c06-641">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-642">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-642">Preemption Possible</span></span>

<span data-ttu-id="e1c06-643">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-643">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-644">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-644">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-645">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-645">See Also</span></span>

- <span data-ttu-id="e1c06-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-646">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="e1c06-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e1c06-653">tx_byte_release</span></span>

<span data-ttu-id="e1c06-654">Frisläpp byte tillbaka till minnesbuffert</span><span class="sxs-lookup"><span data-stu-id="e1c06-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-655">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-656">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-656">Description</span></span>

<span data-ttu-id="e1c06-657">Den här tjänsten frigör ett tidigare allokerat minnes utrymme tillbaka till den associerade poolen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="e1c06-658">Om en eller flera trådar pausas i väntan på minne från den här poolen, tilldelas varje pausad tråd minne och återupptas tills minnet är slut eller tills det inte finns några fler pausade trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="e1c06-659">Den här processen för att allokera minne till pausade trådar börjar alltid med den första tråden inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-660">Programmet måste förhindra att minnes området används när det har släppts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-661">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-661">Parameters</span></span>

- <span data-ttu-id="e1c06-662">**memory_ptr**: pekar på det tidigare allokerade minnes området.</span><span class="sxs-lookup"><span data-stu-id="e1c06-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-663">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-663">Return Values</span></span>

- <span data-ttu-id="e1c06-664">**TX_SUCCESS**: (0X00) lyckad minnes version.</span><span class="sxs-lookup"><span data-stu-id="e1c06-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="e1c06-665">TX_PTR_ERROR: (0x03) ogiltig minnes områdets pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="e1c06-666">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-667">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-667">Allowed From</span></span>

<span data-ttu-id="e1c06-668">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-669">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-669">Preemption Possible</span></span>

<span data-ttu-id="e1c06-670">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-671">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-672">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-672">See Also</span></span>

- <span data-ttu-id="e1c06-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e1c06-673">tx_byte_allocate</span></span>
- <span data-ttu-id="e1c06-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="e1c06-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="e1c06-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="e1c06-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="e1c06-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="e1c06-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-680">tx_event_flags_create</span></span>

<span data-ttu-id="e1c06-681">Skapa händelse flaggor grupp</span><span class="sxs-lookup"><span data-stu-id="e1c06-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-682">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-683">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-683">Description</span></span>

<span data-ttu-id="e1c06-684">Den här tjänsten skapar en grupp med 32 händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="e1c06-685">Alla händelse flaggor i 32 i gruppen initieras till noll.</span><span class="sxs-lookup"><span data-stu-id="e1c06-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="e1c06-686">Varje händelse flagga representeras av en enskild bit.</span><span class="sxs-lookup"><span data-stu-id="e1c06-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-687">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-687">Parameters</span></span>

- <span data-ttu-id="e1c06-688">**group_ptr**: pekar på en grupp kontroll block för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="e1c06-689">**name_ptr**: pekar på namnet på gruppen med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-690">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-690">Return Values</span></span>

- <span data-ttu-id="e1c06-691">**TX_SUCCESS**: (0x00) en lyckad händelse grupp skapades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="e1c06-692">TX_GROUP_ERROR: (0x06) ogiltig händelse grupp pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="e1c06-693">Antingen är pekaren NULL eller också har händelse gruppen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="e1c06-694">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-695">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-695">Allowed From</span></span>

<span data-ttu-id="e1c06-696">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-697">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-697">Preemption Possible</span></span>

<span data-ttu-id="e1c06-698">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-698">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-699">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-700">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-700">See Also</span></span>

- <span data-ttu-id="e1c06-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-702">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-706">tx_event_flags_set</span></span>
- <span data-ttu-id="e1c06-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="e1c06-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-708">tx_event_flags_delete</span></span>

<span data-ttu-id="e1c06-709">Ta bort händelse flaggor grupp</span><span class="sxs-lookup"><span data-stu-id="e1c06-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-711">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-711">Description</span></span>

<span data-ttu-id="e1c06-712">Den här tjänsten tar bort den angivna händelse flaggas gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="e1c06-713">Alla trådar som pausas i väntan på att händelser från den här gruppen återupptas och får en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="e1c06-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-714">Programmet måste se till att en Set notify motringning för den här händelse flaggor gruppen är slutförd (eller inaktive rad) innan du tar bort händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="e1c06-715">Dessutom måste programmet förhindra all framtida användning av en borttagen händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="e1c06-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-716">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-716">Parameters</span></span> 

- <span data-ttu-id="e1c06-717">**group_ptr**: pekar mot en tidigare skapad händelse flagg grupp.</span><span class="sxs-lookup"><span data-stu-id="e1c06-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-718">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-718">Return Values</span></span>

- <span data-ttu-id="e1c06-719">**TX_SUCCESS**: (0x00) händelse flaggor grupp borttagning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="e1c06-720">TX_GROUP_ERROR: (0x06) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="e1c06-721">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-722">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-722">Allowed From</span></span>

<span data-ttu-id="e1c06-723">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-724">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-724">Preemption Possible</span></span>

<span data-ttu-id="e1c06-725">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-726">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-726">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-727">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-727">See Also</span></span>

- <span data-ttu-id="e1c06-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-728">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-729">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-733">tx_event_flags_set</span></span>
- <span data-ttu-id="e1c06-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="e1c06-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-735">tx_event_flags_get</span></span>

<span data-ttu-id="e1c06-736">Hämta händelse flaggor från gruppen med händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="e1c06-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-737">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-738">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-738">Description</span></span>

<span data-ttu-id="e1c06-739">Den här tjänsten hämtar händelse flaggor från den angivna händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="e1c06-740">Varje händelse flaggor grupp innehåller 32 händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="e1c06-741">Varje flagga representeras av en enskild bit.</span><span class="sxs-lookup"><span data-stu-id="e1c06-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="e1c06-742">Den här tjänsten kan hämta en rad olika kombinationer av händelse flaggor som valts av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="e1c06-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-743">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-743">Parameters</span></span>

- <span data-ttu-id="e1c06-744">**group_ptr**: pekar mot en tidigare skapad händelse flagg grupp.</span><span class="sxs-lookup"><span data-stu-id="e1c06-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="e1c06-745">**requested_flags**: 32-bitars osignerad variabel som representerar de begärda händelse flaggorna.</span><span class="sxs-lookup"><span data-stu-id="e1c06-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="e1c06-746">**get_option**: anger om alla eller någon av de begärda händelse flaggorna krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="e1c06-747">Följande är giltiga val:</span><span class="sxs-lookup"><span data-stu-id="e1c06-747">The following are valid selections:</span></span>
    - <span data-ttu-id="e1c06-748">**TX_AND**: (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="e1c06-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="e1c06-749">**TX_AND_CLEAR**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="e1c06-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="e1c06-750">**TX_OR**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="e1c06-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="e1c06-751">**TX_OR_CLEAR**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="e1c06-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="e1c06-752">Om du väljer TX_AND eller TX_AND_CLEAR anger det att alla händelse flaggor måste finnas i gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="e1c06-753">Om du väljer TX_OR eller TX_OR_CLEAR anges att en händelse flagga är tillfredsställande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="e1c06-754">Händelse flaggor som uppfyller begäran rensas (anges till noll) om TX_AND_CLEAR eller TX_OR_CLEAR har angetts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="e1c06-755">**actual_flags_ptr**: pekar mot målet där de hämtade händelse flaggorna placeras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="e1c06-756">Observera att de faktiska flaggor som erhålls kan innehålla flaggor som inte har begärts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="e1c06-757">**wait_option**: definierar hur tjänsten beter sig om de valda händelse flaggorna inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="e1c06-758">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-759">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-761">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-762">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-763">Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="e1c06-764">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills händelse flaggorna är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="e1c06-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="e1c06-765">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-766">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-766">Return Values</span></span>

- <span data-ttu-id="e1c06-767">**TX_SUCCESS**: (0x00) händelse flaggorna get.</span><span class="sxs-lookup"><span data-stu-id="e1c06-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="e1c06-768">**TX_DELETED**: (0X01) händelse flaggor gruppen togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-769">**TX_NO_EVENTS**: tjänsten (0x07) kunde inte hämta de angivna händelserna inom den angivna tiden till väntan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-770">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-771">TX_GROUP_ERROR: (0x06) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="e1c06-772">TX_PTR_ERROR: (0x03) ogiltig pekare för faktiska händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="e1c06-773">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="e1c06-774">TX_OPTION_ERROR: (0x08) ogiltigt get-option angavs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-775">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-775">Allowed From</span></span>

<span data-ttu-id="e1c06-776">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-777">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-777">Preemption Possible</span></span>

<span data-ttu-id="e1c06-778">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-779">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-779">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-780">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-780">See Also</span></span>

- <span data-ttu-id="e1c06-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-781">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-786">tx_event_flags_set</span></span>
- <span data-ttu-id="e1c06-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="e1c06-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="e1c06-789">Hämta information om händelse flaggor gruppen</span><span class="sxs-lookup"><span data-stu-id="e1c06-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-790">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="e1c06-791">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-791">Description</span></span>

<span data-ttu-id="e1c06-792">Den här tjänsten hämtar information om den angivna händelse flagg gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-793">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-793">Parameters</span></span>

- <span data-ttu-id="e1c06-794">**group_ptr**: pekar på en grupp kontroll block för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="e1c06-795">**Name**: pekare till målet för visaren i namnet på händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="e1c06-796">**current_flags**: pekar mot mål för aktuella uppsättnings flaggor i gruppen med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="e1c06-797">**first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över uppskjutnings listor för den här händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="e1c06-798">**suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på den här händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="e1c06-799">**next_group**: pekar på destinations visaren för nästa skapade händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="e1c06-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-800">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-801">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-801">Return Values</span></span>

- <span data-ttu-id="e1c06-802">**TX_SUCCESS**: (0X00) lyckades hämta information om händelse grupps information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="e1c06-803">TX_GROUP_ERROR: (0x06) ogiltig händelse grupp pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-804">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-804">Allowed From</span></span>

<span data-ttu-id="e1c06-805">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-806">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-806">Preemption Possible</span></span>

<span data-ttu-id="e1c06-807">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-807">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-808">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-808">Example</span></span>

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-809">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-809">See Also</span></span>

- <span data-ttu-id="e1c06-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-810">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-812">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-815">tx_event_flags_set</span></span>
- <span data-ttu-id="e1c06-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="e1c06-817">tx_event_flags_performance info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="e1c06-818">Hämta information om händelse flaggor grupp prestanda information</span><span class="sxs-lookup"><span data-stu-id="e1c06-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-819">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-820">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-820">Description</span></span>

<span data-ttu-id="e1c06-821">Den här tjänsten hämtar prestanda information om den angivna händelse flagg gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-822">ThreadX SMP-bibliotek och program måste skapas med **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-823">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-823">Parameters</span></span>

- <span data-ttu-id="e1c06-824">**group_ptr**: pekar mot tidigare skapade händelse flagg grupper.</span><span class="sxs-lookup"><span data-stu-id="e1c06-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="e1c06-825">**uppsättningar**: pekare till målet för antalet händelse flaggor Ställ förfrågningar som utförs på den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="e1c06-826">**hämtar**: pekare till målet för antalet händelse flaggor Hämta begär Anden som utförs i den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="e1c06-827">**SUS pensioner**: pekare till målet för antalet trådar i tråden som ska skjuta upp den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="e1c06-828">**tids gränser**: pekare till målet för antalet händelse flaggor få timeout för inaktive ring för den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-829">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-830">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-830">Return Values</span></span>

- <span data-ttu-id="e1c06-831">**TX_SUCCESS**: (0X00) lyckade händelse flaggor grupp prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="e1c06-832">**TX_PTR_ERROR**: (0X03) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="e1c06-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-834">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-834">Allowed From</span></span>

<span data-ttu-id="e1c06-835">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-836">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-836">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-837">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-837">See Also</span></span>

- <span data-ttu-id="e1c06-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-838">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-840">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-843">tx_event_flags_set</span></span>
- <span data-ttu-id="e1c06-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="e1c06-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="e1c06-846">Hämta information om prestanda systemet</span><span class="sxs-lookup"><span data-stu-id="e1c06-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-847">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-848">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-848">Description</span></span>

<span data-ttu-id="e1c06-849">Den här tjänsten hämtar prestanda information om alla händelse flaggor grupper i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-850">ThreadX SMP-bibliotek och program måste skapas med **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-851">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-851">Parameters</span></span>

- <span data-ttu-id="e1c06-852">**anger**: pekar mot mål för det totala antalet händelse flaggor som har utförts i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="e1c06-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="e1c06-853">**hämtar**: pekare till målet för det totala antalet händelse flaggor begär Anden som utförs på alla grupper.</span><span class="sxs-lookup"><span data-stu-id="e1c06-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="e1c06-854">**SUS pensioner**: pekare till mål för det totala antalet tråd händelse flaggor som får uppehåll i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="e1c06-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="e1c06-855">**tids gränser**: pekare till målet för det totala antalet händelse flaggor få timeout för inaktive ring i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="e1c06-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-856">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-857">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-857">Return Values</span></span>

- <span data-ttu-id="e1c06-858">**TX_SUCCESS**: (0X00) lyckade händelse flaggor system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="e1c06-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-860">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-860">Allowed From</span></span>

<span data-ttu-id="e1c06-861">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-862">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-862">Example</span></span>

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-863">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-863">See Also</span></span>

- <span data-ttu-id="e1c06-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-864">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-866">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-869">tx_event_flags_set</span></span>
- <span data-ttu-id="e1c06-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="e1c06-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-871">tx_event_flags_set</span></span>

<span data-ttu-id="e1c06-872">Ange händelse flaggor i en grupp med händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="e1c06-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-873">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-874">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-874">Description</span></span>

<span data-ttu-id="e1c06-875">Den här tjänsten anger eller rensar händelse flaggor i en grupp med händelse flaggor, beroende på det angivna set-alternativet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="e1c06-876">Alla pausade trådar vars begär Anden om Event Flags nu är uppfyllda återupptas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-877">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-877">Parameters</span></span>

- <span data-ttu-id="e1c06-878">**group_ptr**: pekar mot de tidigare skapade händelse flaggorna grupp kontroll block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="e1c06-879">**flags_to_set**: anger vilka händelse flaggor som ska ställas in eller avmarkeras baserat på set-alternativet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="e1c06-880">**set_option**: anger om de angivna händelse flaggorna är ANDed eller Ored till gruppens aktuella händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="e1c06-881">Följande är giltiga val:</span><span class="sxs-lookup"><span data-stu-id="e1c06-881">The following are valid selections:</span></span>
    - <span data-ttu-id="e1c06-882">**TX_AND**: (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="e1c06-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="e1c06-883">**TX_OR**: (0x00) om du väljer TX_AND anger att de angivna händelse flaggorna är **och** Erik i de aktuella händelse flaggorna i gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="e1c06-884">Det här alternativet används ofta för att rensa händelse flaggor i en grupp.</span><span class="sxs-lookup"><span data-stu-id="e1c06-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="e1c06-885">Annars, om TX_OR anges, är de angivna händelse flaggorna **eller** Erik med den aktuella händelsen i gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-886">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-886">Return Values</span></span>

- <span data-ttu-id="e1c06-887">**TX_SUCCESS**: (0X00) lyckade händelse flaggor angavs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="e1c06-888">TX_GROUP_ERROR: (0x06) ogiltig pekare till händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="e1c06-889">TX_OPTION_ERROR: (0x08) ogiltigt set-alternativ angavs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-890">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-890">Allowed From</span></span>

<span data-ttu-id="e1c06-891">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-892">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-892">Preemption Possible</span></span>

<span data-ttu-id="e1c06-893">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-894">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-894">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-895">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-895">See Also</span></span>

- <span data-ttu-id="e1c06-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-896">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-898">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="e1c06-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="e1c06-904">Meddela program när händelse flaggor anges</span><span class="sxs-lookup"><span data-stu-id="e1c06-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-905">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="e1c06-906">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-906">Description</span></span>

<span data-ttu-id="e1c06-907">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när en eller flera händelse flaggor anges i den angivna händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="e1c06-908">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-909">Programmets händelse flaggor ange återanrop för meddelanden är inte tillåtet för att anropa ThreadX SMP-API med ett uppehålls alternativ.</span><span class="sxs-lookup"><span data-stu-id="e1c06-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-910">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-910">Parameters</span></span> 
- <span data-ttu-id="e1c06-911">**group_ptr**: pekar mot tidigare skapade händelse flagg grupper.</span><span class="sxs-lookup"><span data-stu-id="e1c06-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="e1c06-912">**events_set_notify**: pekar på programmets händelse flaggor ange meddelande funktion.</span><span class="sxs-lookup"><span data-stu-id="e1c06-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="e1c06-913">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-914">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-914">Return Values</span></span>

- <span data-ttu-id="e1c06-915">**TX_SUCCESS**: (0x00) registreringen av event Flags set-aviseringar har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="e1c06-916">TX_GROUP_ERROR: (0x06) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="e1c06-917">TX_FEATURE_NOT_ENABLED: (0xFF) systemet kompilerades med aviserings funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e1c06-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-918">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-918">Allowed From</span></span>

<span data-ttu-id="e1c06-919">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-920">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-920">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-921">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-921">See Also</span></span>

- <span data-ttu-id="e1c06-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-922">tx_event_flags_create</span></span>
- <span data-ttu-id="e1c06-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="e1c06-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-924">tx_event_flags_get</span></span>
- <span data-ttu-id="e1c06-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="e1c06-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="e1c06-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="e1c06-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="e1c06-929">tx_interrupt_control</span></span>

<span data-ttu-id="e1c06-930">Aktivera och inaktivera avbrott</span><span class="sxs-lookup"><span data-stu-id="e1c06-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-931">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="e1c06-932">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-932">Description</span></span>

<span data-ttu-id="e1c06-933">Den här tjänsten aktiverar eller inaktiverar avbrott som anges i indataparametern **new_posture**.</span><span class="sxs-lookup"><span data-stu-id="e1c06-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-934">Om den här tjänsten anropas från en program tråd förblir avbrotts position en del av trådens kontext.</span><span class="sxs-lookup"><span data-stu-id="e1c06-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="e1c06-935">Om tråden till exempel anropar den här rutinen för att inaktivera avbrott och sedan pausar, så inaktive ras avbrott på nytt när de återupptas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="e1c06-936">Den här tjänsten bör inte användas för att aktivera avbrott under initiering!</span><span class="sxs-lookup"><span data-stu-id="e1c06-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="e1c06-937">Om du gör det kan det orsaka oförutsägbara resultat.</span><span class="sxs-lookup"><span data-stu-id="e1c06-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-938">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-938">Parameters</span></span>

- <span data-ttu-id="e1c06-939">**new_posture**: den här parametern anger om avbrott är inaktiverade eller aktiverade.</span><span class="sxs-lookup"><span data-stu-id="e1c06-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="e1c06-940">Giltiga värden är **TX_INT_DISABLE och TX_INT_ENABLE.**</span><span class="sxs-lookup"><span data-stu-id="e1c06-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="e1c06-941">De faktiska värdena för dessa parametrar är specifika för porten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="e1c06-942">Dessutom kan vissa bearbetnings arkitekturer stödja ytterligare avbrott inaktivera postures.</span><span class="sxs-lookup"><span data-stu-id="e1c06-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="e1c06-943">Mer information finns i **_readme_threadx.txt_** information som angavs på distributions disken.</span><span class="sxs-lookup"><span data-stu-id="e1c06-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-944">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-944">Return Values</span></span>

- <span data-ttu-id="e1c06-945">tidigare position: den här tjänsten returnerar föregående avbrotts position till anroparen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="e1c06-946">Detta gör att användare av tjänsten kan återställa de tidigare position när avbrott har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-947">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-947">Allowed From</span></span>

<span data-ttu-id="e1c06-948">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-949">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-949">Preemption Possible</span></span>

<span data-ttu-id="e1c06-950">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-950">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-951">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="e1c06-952">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-952">See Also</span></span>

<span data-ttu-id="e1c06-953">Inget</span><span class="sxs-lookup"><span data-stu-id="e1c06-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="e1c06-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-954">tx_mutex_create</span></span>

<span data-ttu-id="e1c06-955">Skapa ömsesidigt uteslutande mutex</span><span class="sxs-lookup"><span data-stu-id="e1c06-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-956">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="e1c06-957">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-957">Description</span></span>
    
<span data-ttu-id="e1c06-958">Den här tjänsten skapar ett mutex för ömsesidigt undantag mellan trådar för resurs skydd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-959">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-959">Parameters</span></span>

- <span data-ttu-id="e1c06-960">**mutex_ptr**: pekar på ett mutex-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="e1c06-961">**name_ptr**: pekar mot namnet på mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="e1c06-962">**priority_inherit**: anger om denna mutex stöder arv av prioriteter.</span><span class="sxs-lookup"><span data-stu-id="e1c06-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="e1c06-963">Om det här värdet är TX_INHERIT stöds prioriterat arv.</span><span class="sxs-lookup"><span data-stu-id="e1c06-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="e1c06-964">Men om TX_NO_INHERIT anges stöds inte prioriterat arv av denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-965">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-965">Return Values</span></span>

- <span data-ttu-id="e1c06-966">**TX_SUCCESS**: (0X00) slutförde mutex-skapande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="e1c06-967">TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="e1c06-968">Antingen är pekaren NULL eller så har mutex redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="e1c06-969">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="e1c06-970">TX_INHERIT_ERROR: (0x1F) ogiltig prioritet Ärv parameter.</span><span class="sxs-lookup"><span data-stu-id="e1c06-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-971">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-971">Allowed From</span></span>

<span data-ttu-id="e1c06-972">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-973">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-973">Preemption Possible</span></span>

<span data-ttu-id="e1c06-974">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-974">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-975">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-975">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-976">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-976">See Also</span></span>

- <span data-ttu-id="e1c06-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-977">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-978">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="e1c06-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="e1c06-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-984">tx_mutex_delete</span></span>

<span data-ttu-id="e1c06-985">Ta bort ömsesidigt uteslutande mutex</span><span class="sxs-lookup"><span data-stu-id="e1c06-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-986">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-987">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-987">Description</span></span>

<span data-ttu-id="e1c06-988">Den här tjänsten tar bort angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="e1c06-989">Alla trådar som pausas i väntan på att mutexen återupptas och har fått en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="e1c06-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-990">Det är programmets ansvar att förhindra användning av en borttagen mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-991">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-991">Parameters</span></span>

- <span data-ttu-id="e1c06-992">**mutex_ptr**: pekar mot en tidigare skapad mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-993">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-993">Return Values</span></span>

- <span data-ttu-id="e1c06-994">**TX_SUCCESS**: (0X00) lyckad borttagning av mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="e1c06-995">TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="e1c06-996">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-997">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-997">Allowed From</span></span>

<span data-ttu-id="e1c06-998">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-999">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-999">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1000">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1001">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1002">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1002">See Also</span></span>

- <span data-ttu-id="e1c06-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1003">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1004">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="e1c06-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="e1c06-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1010">tx_mutex_get</span></span>

<span data-ttu-id="e1c06-1011">Få ägarskap för mutex</span><span class="sxs-lookup"><span data-stu-id="e1c06-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1012">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-1013">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1013">Description</span></span>

<span data-ttu-id="e1c06-1014">Den här tjänsten försöker få exklusiv ägande rätt till angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="e1c06-1015">Om den anropande tråden redan äger mutex, ökar en intern räknare och en lyckad status returneras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="e1c06-1016">Om mutex ägs av en annan tråd och den här tråden är högre prioritet och arv av prioritet har angetts vid mutex Create, kommer den lägre prioritets Trådens prioritet att tillfälligt höjas till den för anrops tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1017">Prioriteten för tråden med lägre prioritet som äger en mutex med priorityinheritance bör aldrig ändras av en extern tråd under mutex-ägarskapet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1018">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1018">Parameters</span></span>

- <span data-ttu-id="e1c06-1019">**mutex_ptr**: pekar mot en tidigare skapad mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="e1c06-1020">**wait_option**: definierar hur tjänsten fungerar om mutex redan ägs av en annan tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="e1c06-1021">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-1022">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-1024">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-1025">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-1026">*Detta är det enda giltiga alternativet om tjänsten anropas från initiering.*</span><span class="sxs-lookup"><span data-stu-id="e1c06-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="e1c06-1027">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills mutex är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="e1c06-1028">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1029">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1029">Return Values</span></span>

- <span data-ttu-id="e1c06-1030">**TX_SUCCESS**: (0X00) lyckad åtgärd för hämtning av mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="e1c06-1031">**TX_DELETED**: (0X01) mutex togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-1032">**TX_NOT_AVAILABLE**: (0x1D) Det gick inte att erhålla ägarskap för mutex inom den angivna tiden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-1033">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-1034">TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="e1c06-1035">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="e1c06-1036">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1037">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1037">Allowed From</span></span>

<span data-ttu-id="e1c06-1038">Initiering och trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1039">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1039">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1040">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1041">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1042">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1042">See Also</span></span>

- <span data-ttu-id="e1c06-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1043">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="e1c06-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="e1c06-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="e1c06-1051">Hämta information om mutex</span><span class="sxs-lookup"><span data-stu-id="e1c06-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1052">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="e1c06-1053">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1053">Description</span></span>

<span data-ttu-id="e1c06-1054">Den här tjänsten hämtar information från angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1055">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1055">Parameters</span></span>

- <span data-ttu-id="e1c06-1056">**mutex_ptr**: pekar på mutex Control Block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="e1c06-1057">**Name**: pekare till målet för visaren i mutexens namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="e1c06-1058">**antal**: pekar mot målets antal ägarskap för mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="e1c06-1059">**ägare**: pekare till målet för den ägande trådens pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="e1c06-1060">**first_suspended**: pekar till målet för visaren till den tråd som först finns i listan över återkallade i denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="e1c06-1061">**suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på den här mutexen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="e1c06-1062">**next_mutex**: pekaren till målet för pekaren över nästa skapade mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1063">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1064">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1064">Return Values</span></span>

- <span data-ttu-id="e1c06-1065">**TX_SUCCESS**: (0X00) lyckades hämtning av mutex-information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="e1c06-1066">TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1067">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1067">Allowed From</span></span>

<span data-ttu-id="e1c06-1068">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1069">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1069">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1070">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1071">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1071">Example</span></span>

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1072">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1072">See Also</span></span>

- <span data-ttu-id="e1c06-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1073">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1075">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="e1c06-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="e1c06-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="e1c06-1081">Hämta information om mutex-prestanda</span><span class="sxs-lookup"><span data-stu-id="e1c06-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1082">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="e1c06-1083">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1083">Description</span></span>

<span data-ttu-id="e1c06-1084">Den här tjänsten hämtar prestanda information om angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1085">ThreadX SMP-biblioteket och programmet måste skapas med **TX_MUTEX_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1086">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1086">Parameters</span></span>

- <span data-ttu-id="e1c06-1087">**mutex_ptr**: pekar mot tidigare skapad mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="e1c06-1088">**placerar**: pekare till målet för antalet placerings begär Anden som utförts på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="e1c06-1089">**hämtar**: pekare till målet för antalet get-begäranden som har utförts på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="e1c06-1090">**SUS pensioner**: pekare till målet för antalet tråd-mutex-återsusering av denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="e1c06-1091">**tids gränser**: pekare till målet för antalet mutex för att få timeout för den här mutexen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="e1c06-1092">**inversioner**: pekar mot mål för antalet tråd prioritets versioner på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="e1c06-1093">**arv**: pekar mot mål för antalet arvs åtgärder för tråd prioritet på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1094">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1095">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1095">Return Values</span></span>

- <span data-ttu-id="e1c06-1096">**TX_SUCCESS**: (0X00) lyckad mutex prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="e1c06-1097">**TX_PTR_ERROR**: (0X03) ogiltig mutex-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="e1c06-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1099">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1099">Allowed From</span></span>

<span data-ttu-id="e1c06-1100">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1101">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1101">Example</span></span>

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1102">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1102">See Also</span></span>

- <span data-ttu-id="e1c06-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1103">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1105">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="e1c06-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="e1c06-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="e1c06-1111">Hämta information om prestanda för mutex-system</span><span class="sxs-lookup"><span data-stu-id="e1c06-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1112">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="e1c06-1113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1113">Description</span></span>

<span data-ttu-id="e1c06-1114">Den här tjänsten hämtar prestanda information om alla mutexer i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1115">ThreadX SMP-biblioteket och programmet måste skapas med **TX_MUTEX_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1116">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1116">Parameters</span></span>

- <span data-ttu-id="e1c06-1117">**placerar**: pekar mot mål för det totala antalet placerings begär Anden som utförts på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="e1c06-1118">**hämtar**: pekare till mål för det totala antalet get-begäranden som utförts på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="e1c06-1119">**SUS pensioner**: pekare till målet för det totala antalet tråd-mutex får SUS pensioner på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="e1c06-1120">**tids gränser**: pekare till målet för det totala antalet mutexs-timeoutar för alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="e1c06-1121">**inversion**: pekar mot mål för det totala antalet tråd prioritets versioner i alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="e1c06-1122">**arv**: pekar mot mål för det totala antalet arvs åtgärder för tråd prioritet på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1123">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1124">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1124">Return Values</span></span>

- <span data-ttu-id="e1c06-1125">**TX_SUCCESS**: (0X00) lyckad mutex system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="e1c06-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1127">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1127">Allowed From</span></span>

<span data-ttu-id="e1c06-1128">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1129">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1129">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1130">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1130">See Also</span></span>

- <span data-ttu-id="e1c06-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1131">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1133">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="e1c06-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="e1c06-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="e1c06-1139">Prioritera mutex SUS pensioner List</span><span class="sxs-lookup"><span data-stu-id="e1c06-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1140">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1141">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1141">Description</span></span>

<span data-ttu-id="e1c06-1142">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för ägarskapet av mutexen längst fram i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="e1c06-1143">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1144">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1144">Parameters</span></span> 

- <span data-ttu-id="e1c06-1145">**mutex_ptr**: pekar mot den tidigare skapade mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1146">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1146">Return Values</span></span>

- <span data-ttu-id="e1c06-1147">**TX_SUCCESS**: (0X00) lyckad mutex-prioritering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="e1c06-1148">TX_MUTEX_ERROR: (0x1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1149">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1149">Allowed From</span></span>

<span data-ttu-id="e1c06-1150">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1151">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1151">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1152">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1153">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1153">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1154">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1154">See Also</span></span>

- <span data-ttu-id="e1c06-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1155">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1157">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="e1c06-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1162">tx_mutex_put</span></span>

<span data-ttu-id="e1c06-1163">Frigör ägarskap för mutex</span><span class="sxs-lookup"><span data-stu-id="e1c06-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1164">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1165">Description</span></span>

<span data-ttu-id="e1c06-1166">Den här tjänsten minskar ägarskaps antalet för angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="e1c06-1167">Om antalet ägarskap är noll görs mutex tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1168">Om prioritets arv valdes när en mutex skapades återställs prioriteten för den frisläppta tråden till den prioritet den hade när den ursprungligen fick ägandet av mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="e1c06-1169">Alla andra prioritets ändringar som görs i den sammanställda tråden under ägarskapet av mutex kan återställas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1170">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1170">Parameters</span></span>

- <span data-ttu-id="e1c06-1171">**mutex_ptr**: pekar mot den tidigare skapade mutex.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1172">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1172">Return Values</span></span>

- <span data-ttu-id="e1c06-1173">**TX_SUCCESS**: (0X00) lyckad mutex-version.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="e1c06-1174">**TX_NOT_OWNED**: (0X1E) mutex ägs inte av anroparen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="e1c06-1175">TX_MUTEX_ERROR: (0x1C) ogiltig pekare till MUTEX.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="e1c06-1176">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1177">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1177">Allowed From</span></span>

<span data-ttu-id="e1c06-1178">Initiering och trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1179">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1179">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1180">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1181">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1182">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1182">See Also</span></span>

- <span data-ttu-id="e1c06-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1183">tx_mutex_create</span></span>
- <span data-ttu-id="e1c06-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="e1c06-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1185">tx_mutex_get</span></span>
- <span data-ttu-id="e1c06-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="e1c06-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="e1c06-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1190">tx_queue_create</span></span>

<span data-ttu-id="e1c06-1191">Skapa meddelandekö</span><span class="sxs-lookup"><span data-stu-id="e1c06-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="e1c06-1193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1193">Description</span></span>

<span data-ttu-id="e1c06-1194">Tjänsten skapar en meddelandekö som vanligt vis används för kommunikation mellan trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="e1c06-1195">Det totala antalet meddelanden beräknas från angiven meddelande storlek och det totala antalet byte i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1196">Om det totala antalet byte som anges i köns minnes området inte är jämnt delbar med den angivna meddelande storleken, används inte återstående byte i minnes området.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1197">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1197">Parameters</span></span>

- <span data-ttu-id="e1c06-1198">**queue_ptr**: pekar på ett kontroll block för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="e1c06-1199">**name_ptr**: pekar mot namnet på meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="e1c06-1200">**message_size**: anger storleken på varje meddelande i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="e1c06-1201">Meddelande storlekar sträcker sig från 1 32-bitars ord till 16 32-bitars ord.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="e1c06-1202">Giltiga alternativ för meddelande storlek är numeriska värden från 1 till 16.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="e1c06-1203">**queue_start**: meddelande köns start adress.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="e1c06-1204">Start adressen måste vara justerad till storleken på data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="e1c06-1205">**queue_size**: totalt antal byte som är tillgängliga för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1206">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1206">Return Values</span></span>

- <span data-ttu-id="e1c06-1207">**TX_SUCCESS**: (0X00) lyckad meddelande kön har skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="e1c06-1208">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="e1c06-1209">Antingen är pekaren NULL eller också har kön redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="e1c06-1210">TX_PTR_ERROR: (0x03) ogiltig start adress för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="e1c06-1211">TX_SIZE_ERROR: (0x05) storleken på meddelande kön är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="e1c06-1212">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1213">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1213">Allowed From</span></span>

<span data-ttu-id="e1c06-1214">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1215">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1215">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1216">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1217">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1217">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1218">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1218">See Also</span></span>

- <span data-ttu-id="e1c06-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1219">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1220">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1226">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1227">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="e1c06-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1229">tx_queue_delete</span></span>

<span data-ttu-id="e1c06-1230">Ta bort meddelande kön</span><span class="sxs-lookup"><span data-stu-id="e1c06-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1231">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1232">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1232">Description</span></span>

<span data-ttu-id="e1c06-1233">Den här tjänsten tar bort den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="e1c06-1234">Alla trådar som pausas i väntan på ett meddelande från den här kön återupptas och ger en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1235">Programmet måste se till att alla skicka aviserings återanrop för den här kön har slutförts (eller inaktiverats) innan kön tas bort.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="e1c06-1236">Dessutom måste programmet förhindra framtida användning av en borttagen kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="e1c06-1237">*Det är också programmets ansvar att hantera det minnes område som är associerat med kön, vilket är tillgängligt när tjänsten har slutförts.*</span><span class="sxs-lookup"><span data-stu-id="e1c06-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1238">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1238">Parameters</span></span> 

- <span data-ttu-id="e1c06-1239">**queue_ptr**: pekar mot en tidigare skapad meddelande kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1240">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1240">Return Values</span></span>

- <span data-ttu-id="e1c06-1241">**TX_SUCCESS**: (0X00) lyckad borttagning av meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="e1c06-1242">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="e1c06-1243">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1244">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1244">Allowed From</span></span>

<span data-ttu-id="e1c06-1245">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1246">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1246">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1247">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1248">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1248">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1249">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1249">See Also</span></span>

- <span data-ttu-id="e1c06-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1250">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1251">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1257">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1258">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="e1c06-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1260">tx_queue_flush</span></span>

<span data-ttu-id="e1c06-1261">Tomma meddelanden i meddelande kön</span><span class="sxs-lookup"><span data-stu-id="e1c06-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1262">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1263">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1263">Description</span></span>

<span data-ttu-id="e1c06-1264">Den här tjänsten tar bort alla meddelanden som lagras i den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="e1c06-1265">Om kön är full ignoreras meddelanden från alla pausade trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="e1c06-1266">Varje pausad tråd återupptas sedan med en retur status som anger att meddelandet skickades lyckades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="e1c06-1267">Om kön är tom gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1268">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1268">Parameters</span></span> 

- <span data-ttu-id="e1c06-1269">**queue_ptr**: pekar mot en tidigare skapad meddelande kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1270">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1270">Return Values</span></span>

- <span data-ttu-id="e1c06-1271">**TX_SUCCESS**: (0X00) klar med att tömma meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="e1c06-1272">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1273">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1273">Allowed From</span></span>

<span data-ttu-id="e1c06-1274">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1275">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1275">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1276">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1277">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1277">Example</span></span>

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1278">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1278">See Also</span></span>

- <span data-ttu-id="e1c06-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1279">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1280">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1286">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1287">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="e1c06-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1289">tx_queue_front_send</span></span>

<span data-ttu-id="e1c06-1290">Skicka meddelande till kön längst fram</span><span class="sxs-lookup"><span data-stu-id="e1c06-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1291">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-1292">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1292">Description</span></span>

<span data-ttu-id="e1c06-1293">Den här tjänsten skickar ett meddelande till den första platsen i den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="e1c06-1294">Meddelandet **kopieras** till platsen längst fram i kön från det minnes området som anges av käll pekaren.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1295">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1295">Parameters</span></span>

- <span data-ttu-id="e1c06-1296">**queue_ptr**: pekar på ett kontroll block för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="e1c06-1297">**source_ptr**: pekar mot meddelandet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="e1c06-1298">**wait_option**: definierar hur tjänsten fungerar om meddelande kön är full.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="e1c06-1299">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-1300">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-1302">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-1303">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-1304">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*</span><span class="sxs-lookup"><span data-stu-id="e1c06-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="e1c06-1305">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden i oändlighet tills det finns utrymme i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="e1c06-1306">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på plats i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1307">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1307">Return Values</span></span>

- <span data-ttu-id="e1c06-1308">**TX_SUCCESS**: (0x00) överföringen av meddelandet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="e1c06-1309">**TX_DELETED**: (0X01) meddelande kön togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-1310">**TX_QUEUE_FULL**: (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna tids perioden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-1311">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-1312">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="e1c06-1313">TX_PTR_ERROR: (0x03) ogiltig käll pekare för meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="e1c06-1314">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1315">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1315">Allowed From</span></span>

<span data-ttu-id="e1c06-1316">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1317">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1317">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1318">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1319">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1319">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1320">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1320">See Also</span></span>

- <span data-ttu-id="e1c06-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1321">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1322">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1323">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1328">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1329">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="e1c06-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1331">tx_queue_info_get</span></span>

<span data-ttu-id="e1c06-1332">Hämta information om kö</span><span class="sxs-lookup"><span data-stu-id="e1c06-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="e1c06-1334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1334">Description</span></span>

<span data-ttu-id="e1c06-1335">Den här tjänsten hämtar information om den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1336">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1336">Parameters</span></span>

- <span data-ttu-id="e1c06-1337">**queue_ptr**: pekar mot en tidigare skapad meddelande kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="e1c06-1338">**namn**: pekar mot målets pekare till köns namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="e1c06-1339">i **kö**: pekare till målet för antalet meddelanden som för närvarande finns i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="e1c06-1340">**available_storage**: pekar mot mål för det antal meddelanden som kön för närvarande har utrymme för.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="e1c06-1341">**first_suspended**: pekar till målet för visaren i den tråd som är överst på listan över återkallade i den här kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="e1c06-1342">**suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="e1c06-1343">**next_queue**: pekar mot mål som pekar på nästa skapade kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1344">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1345">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1345">Return Values</span></span>

- <span data-ttu-id="e1c06-1346">**TX_SUCCESS**: (0x00) information om lyckade köer hämtades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="e1c06-1347">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1348">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1348">Allowed From</span></span>

<span data-ttu-id="e1c06-1349">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1350">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1350">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1351">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1352">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1352">Example</span></span>

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1353">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1353">See Also</span></span>

- <span data-ttu-id="e1c06-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1354">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1355">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1356">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1361">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1362">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="e1c06-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="e1c06-1365">Hämta prestanda information för kö</span><span class="sxs-lookup"><span data-stu-id="e1c06-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1366">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-1367">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1367">Description</span></span>

<span data-ttu-id="e1c06-1368">Den här tjänsten hämtar prestanda information om den angivna kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1369">ThreadX SMP-biblioteket och programmet måste skapas med **TX_QUEUE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1370">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1370">Parameters</span></span>

- <span data-ttu-id="e1c06-1371">**queue_ptr**: pekare till kön som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="e1c06-1372">**messages_sent**: pekare till målet för antalet sändnings begär Anden som utförts i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="e1c06-1373">**messages_received**: pekar mot mål för antalet mottagna mottagnings begär anden i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="e1c06-1374">**empty_suspensions**: pekar mot mål för antalet tomma köer i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="e1c06-1375">**full_suspensions**: pekar mot målets antal fullständiga uppehåll i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="e1c06-1376">**full_errors**: pekar mot mål för antalet fullständiga fel i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="e1c06-1377">**tids gränser**: pekar mot målet för antalet tids gränser för tråd SUS Pension i den här kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1378">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1379">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1379">Return Values</span></span>

- <span data-ttu-id="e1c06-1380">**TX_SUCCESS**: (0x00) prestanda för slutförd kö hämtas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="e1c06-1381">**TX_PTR_ERROR**: (0X03) ogiltig Queue pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="e1c06-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1383">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1383">Allowed From</span></span>

<span data-ttu-id="e1c06-1384">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1385">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1385">Example</span></span>

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1386">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1386">See Also</span></span>

- <span data-ttu-id="e1c06-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1387">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1388">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1389">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1394">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1395">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="e1c06-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="e1c06-1398">Hämta prestanda information för Queue system</span><span class="sxs-lookup"><span data-stu-id="e1c06-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1399">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-1400">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1400">Description</span></span>

<span data-ttu-id="e1c06-1401">Den här tjänsten hämtar prestanda information om alla köer i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1402">ThreadX SMP-biblioteket och programmet måste skapas med **TX_QUEUE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1403">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1403">Parameters</span></span>

- <span data-ttu-id="e1c06-1404">**messages_sent**: pekar mot mål för det totala antalet sändnings begär Anden som utförts på alla köer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="e1c06-1405">**messages_received**: pekar mot mål för det totala antalet mottagnings begär Anden som utförts på alla köer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="e1c06-1406">**empty_suspensions**: pekar mot mål för det totala antalet tomma köer i kö i alla köer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="e1c06-1407">**full_suspensions**: pekar mot mål för det totala antalet fulla uppehåll i kön på alla köer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="e1c06-1408">**full_errors**: pekar mot mål för det totala antalet fullständiga fel i kön i alla köer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="e1c06-1409">**timeout**: pekar mot mål för det totala antalet tids gränser för tråd SUS pensioner i alla köer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1410">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1411">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1411">Return Values</span></span>

- <span data-ttu-id="e1c06-1412">**TX_SUCCESS**: (0X00) lyckat system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="e1c06-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1414">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1414">Allowed From</span></span>

<span data-ttu-id="e1c06-1415">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1416">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1416">Example</span></span>

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1417">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1417">See Also</span></span>

- <span data-ttu-id="e1c06-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1418">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1419">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1420">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1425">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1426">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="e1c06-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="e1c06-1429">Prioritera lista över återkallade köer</span><span class="sxs-lookup"><span data-stu-id="e1c06-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1430">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="e1c06-1431">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1431">Description</span></span>

<span data-ttu-id="e1c06-1432">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för ett meddelande (eller för att placera ett meddelande) i den här kön överst i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="e1c06-1433">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1434">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1434">Parameters</span></span> 

- <span data-ttu-id="e1c06-1435">**queue_ptr**: pekar mot en tidigare skapad meddelande kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1436">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1436">Return Values</span></span>

- <span data-ttu-id="e1c06-1437">**TX_SUCCESS**: (0X00) lyckad prioritet för kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="e1c06-1438">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1439">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1439">Allowed From</span></span>

<span data-ttu-id="e1c06-1440">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1441">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1441">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1442">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1443">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1443">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1444">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1444">See Also</span></span>

- <span data-ttu-id="e1c06-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1445">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1446">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1447">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1452">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1453">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="e1c06-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1455">tx_queue_receive</span></span>

<span data-ttu-id="e1c06-1456">Hämta meddelande från meddelandekö</span><span class="sxs-lookup"><span data-stu-id="e1c06-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1457">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-1458">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1458">Description</span></span>

<span data-ttu-id="e1c06-1459">Den här tjänsten hämtar ett meddelande från den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="e1c06-1460">Det hämtade meddelandet **kopieras** från kön till det minnes utrymme som anges av mål pekaren.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="e1c06-1461">Meddelandet tas sedan bort från kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="e1c06-1462">Det angivna mål minnes området måste vara tillräckligt stort för att rymma meddelandet. det vill säga att meddelande målet som refereras till av **destination_ptr** måste vara minst lika stort som meddelande storleken för den här kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="e1c06-1463">Annars, om målet inte är tillräckligt stort, sker minnes skada i följande minnes områden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1464">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1464">Parameters</span></span>

- <span data-ttu-id="e1c06-1465">**queue_ptr**: pekar mot en tidigare skapad meddelande kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="e1c06-1466">**destination_ptr**: platsen där meddelandet ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="e1c06-1467">**wait_option**: definierar hur tjänsten fungerar om meddelande kön är tom.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="e1c06-1468">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-1469">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="e1c06-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="e1c06-1471">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-1472">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-1473">Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="e1c06-1474">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills ett meddelande är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="e1c06-1475">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det högsta antalet timer-Tick som ska vara pausat under väntan på ett meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1476">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1476">Return Values</span></span>

- <span data-ttu-id="e1c06-1477">**TX_SUCCESS**: (0X00) lyckad hämtning av meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="e1c06-1478">**TX_DELETED**: (0X01) meddelande kön togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-1479">**TX_QUEUE_EMPTY**: (0X0a) tjänsten kunde inte hämta ett meddelande eftersom kön var tom under den angivna tiden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-1480">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-1481">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="e1c06-1482">TX_PTR_ERROR: (0x03) ogiltig mål pekare för meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="e1c06-1483">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1484">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1484">Allowed From</span></span>

<span data-ttu-id="e1c06-1485">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1486">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1486">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1487">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1488">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1488">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1489">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1489">See Also</span></span>

- <span data-ttu-id="e1c06-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1490">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1491">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1492">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1498">tx_queue_send</span></span>
- <span data-ttu-id="e1c06-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="e1c06-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1500">tx_queue_send</span></span>

<span data-ttu-id="e1c06-1501">Skicka meddelande till meddelandekö</span><span class="sxs-lookup"><span data-stu-id="e1c06-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1502">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="e1c06-1503">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1503">Description</span></span>

<span data-ttu-id="e1c06-1504">Den här tjänsten skickar ett meddelande till den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="e1c06-1505">Det skickade meddelandet **kopieras** till kön från det minnes utrymme som anges av käll pekaren.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1506">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1506">Parameters</span></span>

- <span data-ttu-id="e1c06-1507">**queue_ptr**: pekar mot en tidigare skapad meddelande kö.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="e1c06-1508">**source_ptr**: pekar mot meddelandet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="e1c06-1509">**wait_option**: definierar hur tjänsten fungerar om meddelande kön är full.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="e1c06-1510">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-1511">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-1513">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-1514">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-1515">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*</span><span class="sxs-lookup"><span data-stu-id="e1c06-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="e1c06-1516">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden i oändlighet tills det finns utrymme i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="e1c06-1517">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på plats i kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1518">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1518">Return Values</span></span>

- <span data-ttu-id="e1c06-1519">**TX_SUCCESS**: (0x00) överföringen av meddelandet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="e1c06-1520">**TX_DELETED**: (0X01) meddelande kön togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-1521">**TX_QUEUE_FULL**: (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna tids perioden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="e1c06-1522">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-1523">TX_QUEUE_ERROR: (0x09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="e1c06-1524">TX_PTR_ERROR: (0x03) ogiltig käll pekare för meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="e1c06-1525">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1526">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1526">Allowed From</span></span>

<span data-ttu-id="e1c06-1527">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1528">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1528">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1529">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1530">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1530">Example</span></span>

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1531">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1531">See Also</span></span>

- <span data-ttu-id="e1c06-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1532">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1533">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1534">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1540">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="e1c06-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="e1c06-1543">Meddela program när ett meddelande skickas till kön</span><span class="sxs-lookup"><span data-stu-id="e1c06-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1544">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="e1c06-1545">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1545">Description</span></span>

<span data-ttu-id="e1c06-1546">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när ett meddelande skickas till den angivna kön.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="e1c06-1547">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-1548">Det går inte att anropa någon ThreadX SMP-API med ett uppehålls alternativ i programmets kö för att skicka meddelanden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1549">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1549">Parameters</span></span> 

- <span data-ttu-id="e1c06-1550">**queue_ptr**: pekare till kön som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="e1c06-1551">**queue_send_notify**: pekare till programmets kö skicka meddelande funktion.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="e1c06-1552">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1553">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1553">Return Values</span></span>

- <span data-ttu-id="e1c06-1554">**TX_SUCCESS**: (0x00) registreringen av kö-sändnings meddelande har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="e1c06-1555">TX_QUEUE_ERROR: (0x09) ogiltig Queue pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="e1c06-1556">TX_FEATURE_NOT_ENABLED: (0xFF) systemet kompilerades med aviserings funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1557">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1557">Allowed From</span></span>

<span data-ttu-id="e1c06-1558">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1559">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1559">Example</span></span>

```C
TX_QUEUE         my_queue;

/* Register the "my_queue_send_notify" function for monitoring
   messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
   successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
/* A message was just sent to this queue! */
}
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1560">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1560">See Also</span></span>

- <span data-ttu-id="e1c06-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1561">tx_queue_create</span></span>
- <span data-ttu-id="e1c06-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1562">tx_queue_delete</span></span>
- <span data-ttu-id="e1c06-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e1c06-1563">tx_queue_flush</span></span>
- <span data-ttu-id="e1c06-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="e1c06-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="e1c06-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="e1c06-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e1c06-1569">tx_queue_receive</span></span>
- <span data-ttu-id="e1c06-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="e1c06-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="e1c06-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="e1c06-1572">Placera en instans vid räkning av semafor med tak</span><span class="sxs-lookup"><span data-stu-id="e1c06-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1573">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="e1c06-1574">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1574">Description</span></span>

<span data-ttu-id="e1c06-1575">Den här tjänsten placerar en instans i den angivna räknaren semafor, som i verkligheten ökar inventerings semaforen med en.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="e1c06-1576">Om det aktuella värdet för Count-semaforen är större än eller lika med det angivna taket, kommer instansen inte att placeras och ett TX_CEILING_EXCEEDED fel kommer att returneras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1577">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1577">Parameters</span></span> 

- <span data-ttu-id="e1c06-1578">**semaphore_ptr**: pekar mot tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="e1c06-1579">**tak**: Max gränsen som tillåts för semaforen (giltiga värden är mellan 1 och 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="e1c06-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1580">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1580">Return Values</span></span>

- <span data-ttu-id="e1c06-1581">**TX_SUCCESS**: (0X00) slutförde semafor tak.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="e1c06-1582">**TX_CEILING_EXCEEDED**: (0X21) placerings förfrågan överskrider tak.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="e1c06-1583">TX_INVALID_CEILING: (0x22) ett ogiltigt nollvärde angavs för tak.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="e1c06-1584">TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1585">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1585">Allowed From</span></span>

<span data-ttu-id="e1c06-1586">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1587">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1588">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1588">See Also</span></span>

- <span data-ttu-id="e1c06-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="e1c06-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1598">tx_semaphore_create</span></span>

<span data-ttu-id="e1c06-1599">Skapa inventering av semafor</span><span class="sxs-lookup"><span data-stu-id="e1c06-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1600">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="e1c06-1601">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1601">Description</span></span>

<span data-ttu-id="e1c06-1602">Den här tjänsten skapar en inventerings semafor för synkronisering mellan trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="e1c06-1603">Det inledande antalet semaforer anges som en indataparameter.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1604">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1604">Parameters</span></span> 

- <span data-ttu-id="e1c06-1605">**semaphore_ptr**: pekar mot ett semafors kontroll block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="e1c06-1606">**name_ptr**: pekar mot Semaforens namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="e1c06-1607">**initial_count**: anger det inledande antalet för denna semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="e1c06-1608">Juridiska värden sträcker sig från 0x00000000 till 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1609">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1609">Return Values</span></span>

- <span data-ttu-id="e1c06-1610">**TX_SUCCESS**: (0X00) lyckad generering av semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="e1c06-1611">TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="e1c06-1612">Antingen är pekaren NULL eller så har semaforen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="e1c06-1613">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1614">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1614">Allowed From</span></span>

<span data-ttu-id="e1c06-1615">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1616">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1616">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1617">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1618">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1618">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1619">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1619">See Also</span></span>

- <span data-ttu-id="e1c06-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="e1c06-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="e1c06-1630">Ta bort inventering av semafor</span><span class="sxs-lookup"><span data-stu-id="e1c06-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1631">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1632">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1632">Description</span></span>

<span data-ttu-id="e1c06-1633">Den här tjänsten tar bort den angivna uppräknings semaforen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="e1c06-1634">Alla trådar som pausats i väntan på en semafors instans återupptas och har fått en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1635">Programmet måste se till att en skicka avisering om återanrop för den här semaforen har slutförts (eller inaktiverats) innan du tar bort semaforen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="e1c06-1636">Dessutom måste programmet förhindra all framtida användning av en borttagen semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1637">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1637">Parameters</span></span> 

- <span data-ttu-id="e1c06-1638">**semaphore_ptr**: pekar mot en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1639">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1639">Return Values</span></span>

- <span data-ttu-id="e1c06-1640">**TX_SUCCESS**: (0X00) lyckad inventering av borttagning av semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="e1c06-1641">TX_SEMAPHORE_ERROR: (0x0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="e1c06-1642">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1643">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1643">Allowed From</span></span>

<span data-ttu-id="e1c06-1644">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1645">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1645">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1646">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1647">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1648">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1648">See Also</span></span>

- <span data-ttu-id="e1c06-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="e1c06-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1658">tx_semaphore_get</span></span>

<span data-ttu-id="e1c06-1659">Hämta instans från semafor</span><span class="sxs-lookup"><span data-stu-id="e1c06-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1660">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="e1c06-1661">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1661">Description</span></span>

<span data-ttu-id="e1c06-1662">Den här tjänsten hämtar en instans (ett enda antal) från den angivna semaforen i beräkningen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="e1c06-1663">Därför minskar antalet angivna semaforer med ett.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1664">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1664">Parameters</span></span>

- <span data-ttu-id="e1c06-1665">**semaphore_ptr**: pekar mot en tidigare skapad inventerings semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="e1c06-1666">**wait_option**: definierar hur tjänsten fungerar om det inte finns några instanser av semaforen. det vill säga antalet semaforer är noll.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="e1c06-1667">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e1c06-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="e1c06-1668">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="e1c06-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="e1c06-1670">timeout-värde: (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="e1c06-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="e1c06-1671">Om du väljer TX_NO_WAIT resulterar det i en omedelbar återgång från den här tjänsten oavsett om den lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="e1c06-1672">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*</span><span class="sxs-lookup"><span data-stu-id="e1c06-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="e1c06-1673">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills det finns en instans av semaforen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="e1c06-1674">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på en semafors instans.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1675">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1675">Return Values</span></span>

- <span data-ttu-id="e1c06-1676">**TX_SUCCESS**: (0X00) lyckad hämtning av en semafors instans.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="e1c06-1677">**TX_DELETED**: (0X01) inventering av semafor togs bort medan tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="e1c06-1678">**TX_NO_INSTANCE**: (0x0D) Det gick inte att hämta en instans av inventerings semaforen (antalet semaforer är noll inom den angivna tiden för att vänta).</span><span class="sxs-lookup"><span data-stu-id="e1c06-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="e1c06-1679">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-1680">TX_SEMAPHORE_ERROR: (0x0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="e1c06-1681">TX_WAIT_ERROR: (0x04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1682">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1682">Allowed From</span></span>

<span data-ttu-id="e1c06-1683">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1684">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1684">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1685">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1686">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1686">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1687">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1687">See Also</span></span>

- <span data-ttu-id="e1c06-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="e1c06-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="e1c06-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="e1c06-1697">Hämta information om semafor</span><span class="sxs-lookup"><span data-stu-id="e1c06-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1698">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="e1c06-1699">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1699">Description</span></span>

<span data-ttu-id="e1c06-1700">Den här tjänsten hämtar information om den angivna semaforen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1701">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1701">Parameters</span></span>

- <span data-ttu-id="e1c06-1702">**semaphore_ptr**: pekar mot semafor-kontroll block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="e1c06-1703">**Name**: pekare till målet för visaren i Semaforens namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="e1c06-1704">**Current_value**: pekar mot mål för den aktuella Semaforens antal.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="e1c06-1705">**first_suspended**: pekar till målet för visaren i den tråd som är överst i listan över återkallade semaforer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="e1c06-1706">**suspended_count**: pekar mot mål för antalet trådar som för närvarande har pausats på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="e1c06-1707">**next_semaphore**: pekaren till målet för pekaren över nästa skapade semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1708">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1709">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1709">Return Values</span></span>

- <span data-ttu-id="e1c06-1710">**TX_SUCCESS**: (0X00) lyckad semafors informations hämtning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="e1c06-1711">TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1712">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1712">Allowed From</span></span>

<span data-ttu-id="e1c06-1713">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1714">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1714">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1715">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1716">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1716">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1717">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1717">See Also</span></span>

- <span data-ttu-id="e1c06-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="e1c06-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="e1c06-1728">Hämta information om semafor-prestanda</span><span class="sxs-lookup"><span data-stu-id="e1c06-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1729">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-1730">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1730">Description</span></span>

<span data-ttu-id="e1c06-1731">Den här tjänsten hämtar prestanda information om den angivna semaforen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-1732">ThreadX SMP-biblioteket och programmet måste skapas med **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1733">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1733">Parameters</span></span>

- <span data-ttu-id="e1c06-1734">**semaphore_ptr**: pekar mot tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="e1c06-1735">**placerar**: pekare till målet för antalet begär Anden som utförts på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="e1c06-1736">**hämtar**: pekare till målet för antalet get-begäranden som utförts på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="e1c06-1737">**SUS pensioner**: pekare till målet för antalet tråd avbrott i denna semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="e1c06-1738">**tids gränser**: pekar mot målet för antalet tids gränser för tråd SUS Pension på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1739">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1740">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1740">Return Values</span></span>

- <span data-ttu-id="e1c06-1741">**TX_SUCCESS**: (0X00) lyckad semafor-prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="e1c06-1742">**TX_PTR_ERROR**: (0X03) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="e1c06-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1744">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1744">Allowed From</span></span>

<span data-ttu-id="e1c06-1745">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1746">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1746">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1747">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1747">See Also</span></span>

- <span data-ttu-id="e1c06-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="e1c06-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="e1c06-1758">Hämta information om prestanda för semafor-systemet</span><span class="sxs-lookup"><span data-stu-id="e1c06-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1759">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="e1c06-1760">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1760">Description</span></span>

<span data-ttu-id="e1c06-1761">Den här tjänsten hämtar prestanda information om alla semaforer i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1762">ThreadX SMP-biblioteket och programmet måste skapas med **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1763">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1763">Parameters</span></span>

- <span data-ttu-id="e1c06-1764">**placerar**: pekar mot mål för det totala antalet begär Anden som utförts på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="e1c06-1765">**hämtar**: pekare till mål för det totala antalet get-begäranden som utförts på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="e1c06-1766">**SUS pensioner**: pekar mot mål för det totala antalet tråd SUS pensioner på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="e1c06-1767">**timeout**: pekar mot mål för det totala antalet tids gränser för tråd SUS Pension på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1768">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1769">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1769">Return Values</span></span>

- <span data-ttu-id="e1c06-1770">TX_SUCCESS: (0x00) lyckad semafor system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="e1c06-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1772">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1772">Allowed From</span></span>

<span data-ttu-id="e1c06-1773">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1774">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1774">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1775">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1775">See Also</span></span>

- <span data-ttu-id="e1c06-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="e1c06-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="e1c06-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="e1c06-1786">Prioritera lista över återkallade semaforer</span><span class="sxs-lookup"><span data-stu-id="e1c06-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1787">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1788">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1788">Description</span></span>

<span data-ttu-id="e1c06-1789">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för en instans av semaforen överst i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="e1c06-1790">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1791">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1791">Parameters</span></span> 

- <span data-ttu-id="e1c06-1792">**semaphore_ptr**: pekar mot en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1793">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1793">Return Values</span></span>

- <span data-ttu-id="e1c06-1794">**TX_SUCCESS**: (0X00) lyckad semafor-prioritering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="e1c06-1795">TX_SEMAPHORE_ERROR: (0x0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1796">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1796">Allowed From</span></span>

<span data-ttu-id="e1c06-1797">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1798">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1798">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1799">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1800">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1800">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1801">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1801">See Also</span></span>

- <span data-ttu-id="e1c06-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="e1c06-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1807">tx_semaphore_put</span></span>

<span data-ttu-id="e1c06-1808">Placera en instans i inventering av semafor</span><span class="sxs-lookup"><span data-stu-id="e1c06-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1809">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1810">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1810">Description</span></span>

<span data-ttu-id="e1c06-1811">Den här tjänsten placerar en instans i den angivna räknaren semafor, som i verkligheten ökar inventerings semaforen med en.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1812">Om den här tjänsten anropas när semaforen är alla (OxFFFFFFFF) gör den nya åtgärden att semaforen återställs till noll.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1813">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1813">Parameters</span></span>

- <span data-ttu-id="e1c06-1814">**semaphore_ptr**: pekar mot det tidigare skapade semafors kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1815">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1815">Return Values</span></span>

- <span data-ttu-id="e1c06-1816">**TX_SUCCESS**: (0X00) lyckad semafor-placering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="e1c06-1817">TX_SEMAPHORE_ERROR: (0x0C) ogiltig pekare för att räkna semaforen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1818">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1818">Allowed From</span></span>

<span data-ttu-id="e1c06-1819">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1820">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1820">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1821">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1822">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1823">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1823">See Also</span></span>

- <span data-ttu-id="e1c06-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="e1c06-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="e1c06-1834">Meddela program när semaforen placeras</span><span class="sxs-lookup"><span data-stu-id="e1c06-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1835">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="e1c06-1836">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1836">Description</span></span>

<span data-ttu-id="e1c06-1837">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när den angivna semaforen placeras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="e1c06-1838">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-1839">Det går inte att anropa någon ThreadX SMP-API med ett uppehålls alternativ i programmets SMP-motanrop.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1840">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1840">Parameters</span></span> 

- <span data-ttu-id="e1c06-1841">**semaphore_ptr**: pekar mot tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="e1c06-1842">**semaphore_put_notify**: pekar på programmets varnings funktion för semafors placering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="e1c06-1843">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1844">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1844">Return Values</span></span>

- <span data-ttu-id="e1c06-1845">**TX_SUCCESS**: (0X00) lyckad registrering av semafors meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="e1c06-1846">TX_SEMAPHORE_ERROR: (0x0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="e1c06-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet kompilerades med aviserings funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1848">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1848">Allowed From</span></span>

<span data-ttu-id="e1c06-1849">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1850">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1850">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1851">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1851">See Also</span></span>

- <span data-ttu-id="e1c06-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="e1c06-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="e1c06-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="e1c06-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="e1c06-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="e1c06-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="e1c06-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="e1c06-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e1c06-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="e1c06-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1861">tx_thread_create</span></span>

<span data-ttu-id="e1c06-1862">Skapa program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1863">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="e1c06-1864">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1864">Description</span></span>

<span data-ttu-id="e1c06-1865">Den här tjänsten skapar en program tråd som startar körningen vid den angivna aktivitets inmatnings funktionen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="e1c06-1866">Stack, Priority, avstängningen-Threshold och Time-slice är bland de attribut som anges av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="e1c06-1867">Dessutom anges även det första körnings läget för tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1868">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1868">Parameters</span></span>

- <span data-ttu-id="e1c06-1869">**thread_ptr**: pekar mot ett tråd kontroll block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="e1c06-1870">**name_ptr**: pekar mot namnet på tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="e1c06-1871">**entry_function**: anger den inledande C-funktionen för tråd körning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="e1c06-1872">När en tråd returnerar från den här post funktionen placeras den i ett slutfört tillstånd och inaktive ras på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="e1c06-1873">**entry_input**: ett 32-bitars värde som skickas till trådens post funktion första gången den körs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="e1c06-1874">Användningen av den här indatamängden fastställs exklusivt av programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="e1c06-1875">**stack_start**: Start adress för stackens minnes områden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="e1c06-1876">**stack_size**: antal byte i stack minnes området.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="e1c06-1877">Trådens stack område måste vara tillräckligt stort för att hantera dess värsta fall funktions anrop till kapsling och lokal variabel användning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="e1c06-1878">**prioritet**: numerisk prioritet för tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="e1c06-1879">Giltiga värden är mellan 0 och (TX_MAX_PRIORITES-1), där värdet 0 representerar den högsta prioriteten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="e1c06-1880">**preempt_threshold**: högsta prioritets nivå (0 till (TX_MAX_PRIORITIES-1)) av inaktiverade avstängningen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="e1c06-1881">Endast prioriteter som är större än den här nivån tillåts för den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="e1c06-1882">Värdet måste vara mindre än eller lika med den angivna prioriteten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="e1c06-1883">Ett värde som är lika med tråd prioriteten inaktiverar avstängningen-Threshold.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="e1c06-1884">**time_slice**: antalet timer-Tick som den här tråden tillåts köra innan andra redo trådar med samma prioritet ges möjlighet att köra.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="e1c06-1885">Observera att med avstängningen-tröskelvärdet inaktive ras tids segmentering.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="e1c06-1886">Legal Time-slice-värden sträcker sig från 1 till 0xFFFFFFFF (inklusive).</span><span class="sxs-lookup"><span data-stu-id="e1c06-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="e1c06-1887">Värdet **TX_NO_TIME_SLICE** (värdet 0) inaktiverar tids segmentering av tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e1c06-1888">Om du använder tids segmentering blir det en liten del av systemets kostnader.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="e1c06-1889">Eftersom tids segmentering bara är användbart i fall där flera trådar delar samma prioritet, ska trådar som har en unik prioritet inte tilldelas en tid-sektor.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="e1c06-1890">**auto_start**: anger om tråden startar omedelbart eller om den placeras i ett uppehålls läge.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="e1c06-1891">Juridiska alternativ är **TX_AUTO_START** (0x01) och **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="e1c06-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="e1c06-1892">Om TX_DONT_START anges måste programmet senare anropa tx_thread_resume för att tråden ska kunna köras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1893">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1893">Return Values</span></span>

- <span data-ttu-id="e1c06-1894">**TX_SUCCESS**: (0X00) lyckad tråd skapande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="e1c06-1895">TX_THREAD_ERROR: (0x0E) ogiltig tråd kontroll pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="e1c06-1896">Antingen är pekaren NULL eller också har tråden redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="e1c06-1897">TX_PTR_ERROR: (0x03) ogiltig start adress för start punkten eller stackområdet är ogiltigt, vanligt vis NULL.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="e1c06-1898">TX_SIZE_ERROR: (0x05) storleken på stackområdet är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="e1c06-1899">Trådar måste ha minst **TX_MINIMUM_STACK** byte för att kunna köras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="e1c06-1900">TX_PRIORITY_ERROR: (0x0F) ogiltig tråd prioritet, vilket är ett värde utanför intervallet (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="e1c06-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="e1c06-1901">TX_THRESH_ERROR: (0x18) ogiltig preemptionthreshold har angetts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="e1c06-1902">Värdet måste vara en giltig prioritet som är mindre än eller lika med trådens inledande prioritet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="e1c06-1903">TX_START_ERROR: (0x10) ogiltig markering för automatisk start.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="e1c06-1904">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1905">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1905">Allowed From</span></span>

<span data-ttu-id="e1c06-1906">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1907">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1907">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1908">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1909">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1909">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
                my_thread_entry, 0x1234,
                (VOID *) 0x400000, 1000,
                15, 15, TX_NO_TIME_SLICE,
                TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
   for execution! */
...

/* Thread’s entry function. When "my_thread" actually
   begins execution, control is transferred to this
   function. */
VOID my_thread_entry (ULONG initial_input)
{

    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */

    /* The real work of the thread, including calls to
    other function should be called from here! */

    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1910">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1910">See Also</span></span>

- <span data-ttu-id="e1c06-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1911">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1913">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-1920">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-1921">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="e1c06-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1928">tx_thread_delete</span></span>

<span data-ttu-id="e1c06-1929">Ta bort program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1930">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-1931">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1931">Description</span></span>

<span data-ttu-id="e1c06-1932">Den här tjänsten tar bort den angivna program tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="e1c06-1933">Eftersom den angivna tråden måste vara i ett avslutat eller slutfört tillstånd, kan den här tjänsten inte anropas från en tråd som försöker ta bort sig själv.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-1934">Det är programmets ansvar att hantera det minnes område som är associerat med trådens stack, vilket är tillgängligt när tjänsten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="e1c06-1935">Dessutom måste programmet förhindra att en borttagen tråd används.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1936">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1936">Parameters</span></span>

- <span data-ttu-id="e1c06-1937">**thread_ptr**: pekar mot en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1938">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1938">Return Values</span></span>

- <span data-ttu-id="e1c06-1939">**TX_SUCCESS**: (0X00) lyckad tråd borttagning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="e1c06-1940">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-1941">**TX_DELETE_ERROR**: (0x11) den angivna tråden är inte i ett avslutat eller slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="e1c06-1942">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1943">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1943">Allowed From</span></span>

<span data-ttu-id="e1c06-1944">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-1945">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-1945">Preemption Possible</span></span>

<span data-ttu-id="e1c06-1946">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1947">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1947">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-1948">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1948">See Also</span></span>

- <span data-ttu-id="e1c06-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1949">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1951">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-1958">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-1959">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="e1c06-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="e1c06-1967">Meddela programmet vid tråd inmatning och avsluta</span><span class="sxs-lookup"><span data-stu-id="e1c06-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-1968">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="e1c06-1969">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-1969">Description</span></span>

<span data-ttu-id="e1c06-1970">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när den angivna tråden anges eller avslutas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="e1c06-1971">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-1972">Det går inte att anropa någon ThreadX SMP-API med ett uppehålls alternativ i programmets tråd post-eller avslutnings meddelande återanrop.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-1973">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-1973">Parameters</span></span>

- <span data-ttu-id="e1c06-1974">**thread_ptr**: pekare till en tidigare skapad tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="e1c06-1975">**entry_exit_notify**: pekare till programmets tråd post/avslutnings meddelande funktion.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="e1c06-1976">Den andra parametern för funktionen post-/avslutnings meddelande anger om en post eller Exit finns.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="e1c06-1977">Värdet TX_THREAD_ENTRY (0x00) anger att tråden angavs, medan värdet TX_THREAD_EXIT (0x01) anger att tråden avslutades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="e1c06-1978">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-1979">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-1979">Return Values</span></span>

- <span data-ttu-id="e1c06-1980">**TX_SUCCESS**: (0X00) lyckad registrering av aviserings funktionen för tråd post/avslutning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="e1c06-1981">TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="e1c06-1982">**TX_FEATURE_NOT_ENABLED (0xFF)** Systemet kompilerades med aviserings funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="e1c06-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-1983">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-1983">Allowed From</span></span>

<span data-ttu-id="e1c06-1984">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-1985">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-1985">Example</span></span>

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
                my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
   successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{

    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
                 /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
         /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="e1c06-1986">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-1986">See Also</span></span>

- <span data-ttu-id="e1c06-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-1987">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-1988">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-1990">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-1997">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-1998">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="e1c06-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2005">tx_thread_identify</span></span>

<span data-ttu-id="e1c06-2006">Hämtar pekare till tråd som körs för tillfället</span><span class="sxs-lookup"><span data-stu-id="e1c06-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2007">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="e1c06-2008">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2008">Description</span></span>

<span data-ttu-id="e1c06-2009">Den här tjänsten returnerar en pekare till den aktuella tråden som körs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="e1c06-2010">Om ingen tråd körs returnerar den här tjänsten en null-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2011">Om den här tjänsten anropas från en ISR representerar returvärdet den tråd som körs innan avbrotts hanteraren körs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2012">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2012">Parameters</span></span>

<span data-ttu-id="e1c06-2013">Ingen</span><span class="sxs-lookup"><span data-stu-id="e1c06-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2014">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2014">Return Values</span></span>

- <span data-ttu-id="e1c06-2015">tråd pekare: pekare till den aktuella tråden som körs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="e1c06-2016">Om ingen tråd körs TX_NULL det returnerade värdet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2017">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2017">Allowed From</span></span>

<span data-ttu-id="e1c06-2018">Trådar och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2019">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2019">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2020">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2021">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2021">Example</span></span>

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2022">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2022">See Also</span></span>

- <span data-ttu-id="e1c06-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2023">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2024">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2032">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2033">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="e1c06-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2040">tx_thread_info_get</span></span>

<span data-ttu-id="e1c06-2041">Hämta information om tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2042">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="e1c06-2043">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2043">Description</span></span>

<span data-ttu-id="e1c06-2044">Den här tjänsten hämtar information om den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2045">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2045">Parameters</span></span> 

- <span data-ttu-id="e1c06-2046">**thread_ptr**: pekar på tråd kontroll block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="e1c06-2047">**Name**: pekare till målet för visaren till trådens namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="e1c06-2048">**tillstånd**: pekare till målet för trådens aktuella körnings tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="e1c06-2049">Möjliga värden är:</span><span class="sxs-lookup"><span data-stu-id="e1c06-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="e1c06-2050">**TX_READY**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="e1c06-2051">**TX_COMPLETED**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="e1c06-2052">**TX_TERMINATED**: (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="e1c06-2053">**TX_SUSPENDED**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="e1c06-2054">**TX_SLEEP**: (0x04)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="e1c06-2055">**TX_QUEUE_SUSP**: (0x05)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="e1c06-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="e1c06-2057">**TX_EVENT_FLAG**: (0x07)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="e1c06-2058">**TX_BLOCK_MEMORY**: (0x08)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="e1c06-2059">**TX_BYTE_MEMORY**: (0x09)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="e1c06-2060">**TX_MUTEX_SUSP**: (0x0D)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="e1c06-2061">**run_count**: pekar mot målet för trådens antal körningar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="e1c06-2062">**prioritet**: pekar mot målets prioritet för tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="e1c06-2063">**preemption_threshold**: pekar mot mål för trådens avstängningen-tröskelvärde.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="e1c06-2064">**time_slice**: pekar mot målet för trådens tids segment.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="e1c06-2065">**next_thread**: pekare till mål för nästa skapade tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="e1c06-2066">**suspended_thread**: pekare till destination för pekare till nästa tråd i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2067">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2068">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2068">Return Values</span></span>

- <span data-ttu-id="e1c06-2069">**TX_SUCCESS**: (0X00) lyckad tråd informations hämtning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="e1c06-2070">TX_THREAD_ERROR: (0x0E) ogiltig tråd kontroll pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2071">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2071">Allowed From</span></span>

<span data-ttu-id="e1c06-2072">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2073">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2073">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2074">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2075">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2075">Example</span></span>

```C
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
   thread "my_thread." */
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2076">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2076">See Also</span></span>

- <span data-ttu-id="e1c06-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2077">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2078">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2080">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2086">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2087">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="e1c06-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="e1c06-2095">Hämta information om tråd prestanda</span><span class="sxs-lookup"><span data-stu-id="e1c06-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2096">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="e1c06-2097">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2097">Description</span></span>

<span data-ttu-id="e1c06-2098">Den här tjänsten hämtar prestanda information om den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2099">ThreadX SMP-biblioteket och programmet måste ha skapats med **TX_THREAD_ENABLE_PERFORMANCE_INFO** definierat för att den här tjänsten ska returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2100">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2100">Parameters</span></span> 

- <span data-ttu-id="e1c06-2101">**thread_ptr**: pekare till en tidigare skapad tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="e1c06-2102">**återupptar**: pekare till målet för antalet återupptagningar av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="e1c06-2103">**SUS pensioner**: pekare till målet för antalet SUS pensioner av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="e1c06-2104">**solicited_preemptions**: pekare till målet för antalet preemptions till följd av ett ThreadX API-tjänst anrop som gjorts av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="e1c06-2105">**interrupt_preemptions**: pekar mot mål för antalet preemptions för den här tråden som ett resultat av avbrotts bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="e1c06-2106">**priority_inversions**: pekar mot mål för antalet prioritets versioner av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="e1c06-2107">**time_slices**: pekare till målet för antalet timeslices för den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="e1c06-2108">**låser** sig: pekare till målet för antalet trådar som utförs av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="e1c06-2109">**timeout**: pekar mot målets antal tids gräns värden för tids gränsen på den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="e1c06-2110">**wait_aborts**: pekar mot mål för antalet väntande avbrott som utförs på den här tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="e1c06-2111">**last_preempted_by**: pekar mot mål för tråd pekaren som senast blockerade tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2112">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2113">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2113">Return Values</span></span>

- <span data-ttu-id="e1c06-2114">**TX_SUCCESS**: (0X00) lyckad tråd prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="e1c06-2115">**TX_PTR_ERROR**: (0X03) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="e1c06-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2117">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2117">Allowed From</span></span>

<span data-ttu-id="e1c06-2118">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2119">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2119">Example</span></span>

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

/* Retrieve performance information on the previously created
   thread. */
status = tx_thread_performance_info_get(&my_thread, &resumptions,
               &suspensions,
               &solicited_preemptions, &interrupt_preemptions,
               &priority_inversions, &time_slices,
               &relinquishes, &timeouts,
               &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2120">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2120">See Also</span></span>

- <span data-ttu-id="e1c06-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2121">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2122">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2124">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2130">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2131">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="e1c06-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="e1c06-2139">Hämta information om tråd system prestanda</span><span class="sxs-lookup"><span data-stu-id="e1c06-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2140">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="e1c06-2141">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2141">Description</span></span>

<span data-ttu-id="e1c06-2142">Den här tjänsten hämtar prestanda information om alla trådar i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2143">ThreadX SMP-biblioteket och programmet måste ha skapats med **TX_THREAD_ENABLE_PERFORMANCE_INFO** definierat för att den här tjänsten ska returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2144">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2144">Parameters</span></span>

- <span data-ttu-id="e1c06-2145">**återupptar**: pekar mot mål för det totala antalet trådar som återupptas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="e1c06-2146">**SUS pensioner**: pekar mot mål för det totala antalet tråd SUS pensioner.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="e1c06-2147">**solicited_preemptions**: pekar mot mål för det totala antalet tråd-preemptions som ett resultat av en tråd som anropar en THREADX-API-tjänst.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="e1c06-2148">**interrupt_preemptions**: pekar mot mål för det totala antalet tråd-preemptions som ett resultat av avbrotts bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="e1c06-2149">**priority_inversions**: pekar mot mål för det totala antalet tråd prioritets versioner.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="e1c06-2150">**time_slices**: pekar mot mål för det totala antalet tråd-Time-Slices.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="e1c06-2151">**låser** sig: pekare till målet för det totala antalet trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="e1c06-2152">**timeout**: pekar mot mål för det totala antalet tids gränser för tråd upphängning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="e1c06-2153">**wait_aborts**: pekar mot mål för det totala antalet avbrott i tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="e1c06-2154">**non_idle_returns**: pekar mot mål för antalet gånger som en tråd återgår till systemet när en annan tråd är redo att köras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="e1c06-2155">**idle_returns**: pekar mot mål för antalet gånger som en tråd återgår till systemet när ingen annan tråd är redo att köras (inaktivt system).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2156">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2157">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2157">Return Values</span></span>

- <span data-ttu-id="e1c06-2158">**TX_SUCCESS**: (0X00) lyckad tråd system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="e1c06-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2160">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2160">Allowed From</span></span>

<span data-ttu-id="e1c06-2161">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2162">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2162">Example</span></span>

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

/* Retrieve performance information on all previously created
   thread. */
status = tx_thread_performance_system_info_get(&resumptions,
                &suspensions,
                &solicited_preemptions, &interrupt_preemptions,
                &priority_inversions, &time_slices, &relinquishes,
                &timeouts, &wait_aborts, &non_idle_returns,
                &idle_returns);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2163">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2163">See Also</span></span>

- <span data-ttu-id="e1c06-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2164">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2165">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2167">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2173">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2174">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="e1c06-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="e1c06-2182">Ändra avstängningen-tröskel för program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2183">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="e1c06-2184">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2184">Description</span></span>

<span data-ttu-id="e1c06-2185">Den här tjänsten ändrar avstängningen-tröskeln för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="e1c06-2186">Avstängningen-Threshold förhindrar avstängningen av den angivna tråden efter trådar som är lika med eller lägre än värdet för avstängningen-tröskelvärdet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2187">Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2188">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2188">Parameters</span></span>

- <span data-ttu-id="e1c06-2189">**thread_ptr**: pekar mot en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="e1c06-2190">**new_threshold**: ny avstängningen prioritets nivå (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="e1c06-2191">**old_threshold**: pekar på en plats för att returnera föregående avstängningen-tröskelvärde.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2192">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2192">Return Values</span></span>

- <span data-ttu-id="e1c06-2193">**TX_SUCCESS**: (0X00) lyckades avstängningen-tröskel ändring.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="e1c06-2194">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2195">**TX_THRESH_ERROR**: (0X18) angiven ny avstängningen-tröskel är inte en giltig tråd prioritet (ett annat värde än (0 till (TX_MAX_PRIORITIES-1)) eller är större än (lägre prioritet) än den aktuella tråd prioriteten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="e1c06-2196">TX_PTR_ERROR: (0x03) ogiltig pekare till den tidigare preemptionthreshold lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="e1c06-2197">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2198">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2198">Allowed From</span></span>

<span data-ttu-id="e1c06-2199">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2200">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2200">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2201">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2202">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2202">Example</span></span>

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

/* Disable all preemption of the specified thread. The
   current preemption-threshold is returned in
   "my_old_threshold". Assume that "my_thread" has
   already been created. */
status = tx_thread_preemption_change(&my_thread,
                             0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
   non-preemptable by another thread. Note that ISRs are
   not prevented by preemption disabling. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2203">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2203">See Also</span></span>

- <span data-ttu-id="e1c06-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2204">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2205">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2207">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2213">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2214">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="e1c06-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="e1c06-2222">Ändra prioritet för program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2223">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="e1c06-2224">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2224">Description</span></span>

<span data-ttu-id="e1c06-2225">Den här tjänsten ändrar prioriteten för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="e1c06-2226">Giltiga prioriteter är mellan 0 och (TX_MAX_PRIORITES-1), där 0 representerar den högsta prioritets nivån.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2227">Avstängningen-tröskelvärdet för den angivna tråden anges automatiskt till den nya prioriteten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="e1c06-2228">Om ett nytt tröskelvärde önskas måste **tx_thread_preemption_changes** tjänsten användas efter det här anropet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2229">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2229">Parameters</span></span>

- <span data-ttu-id="e1c06-2230">**thread_ptr**: pekar mot en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="e1c06-2231">**new_priority**: ny tråd prioritets nivå (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="e1c06-2232">**old_priority**: pekar på en plats för att returnera trådens föregående prioritet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2233">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2233">Return Values</span></span>

- <span data-ttu-id="e1c06-2234">**TX_SUCCESS**: (0X00) lyckad prioritets ändring.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="e1c06-2235">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2236">TX_PRIORITY_ERROR: (0x0F) angiven ny prioritet är inte giltig (ett värde annat än (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="e1c06-2237">TX_PTR_ERROR: (0x03) ogiltig pekare till den tidigare prioritets lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="e1c06-2238">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2239">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2239">Allowed From</span></span>

<span data-ttu-id="e1c06-2240">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2241">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2241">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2242">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2243">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2243">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2244">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2244">See Also</span></span>

- <span data-ttu-id="e1c06-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2245">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2246">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2248">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2254">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2255">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="e1c06-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="e1c06-2263">Lämna kontroll till andra program trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2264">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="e1c06-2265">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2265">Description</span></span>

<span data-ttu-id="e1c06-2266">Den här tjänsten övervärderar processor kontroll till andra trådar som är redo att köra med samma eller högre prioritet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2267">Förutom att förhindra kontroll till trådar med samma prioritet, förhindrar den här tjänsten också kontroll till att tråden med högsta prioritet förhindras från att köras på grund av den aktuella trådens avstängningen-inställning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2268">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2268">Parameters</span></span>

<span data-ttu-id="e1c06-2269">Ingen</span><span class="sxs-lookup"><span data-stu-id="e1c06-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2270">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2270">Return Values</span></span>

<span data-ttu-id="e1c06-2271">Inget</span><span class="sxs-lookup"><span data-stu-id="e1c06-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2272">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2272">Allowed From</span></span>

<span data-ttu-id="e1c06-2273">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2274">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2274">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2275">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2276">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2276">Example</span></span>

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {

        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2277">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2277">See Also</span></span>

- <span data-ttu-id="e1c06-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2278">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2279">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2281">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2287">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2288">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="e1c06-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2295">tx_thread_reset</span></span>

<span data-ttu-id="e1c06-2296">Återställ tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2297">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2298">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2298">Description</span></span>

<span data-ttu-id="e1c06-2299">Den här tjänsten återställer den angivna tråden så att den körs vid den Start punkt som definieras vid skapandet av tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="e1c06-2300">Tråden måste vara antingen i ett **TX_COMPLETED** eller **TX_TERMINATED** tillstånd för att den ska kunna återställas</span><span class="sxs-lookup"><span data-stu-id="e1c06-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2301">Tråden måste återupptas för att den ska kunna köras igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2302">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2302">Parameters</span></span> 

- <span data-ttu-id="e1c06-2303">**thread_ptr**: pekar mot en tidigare skapad tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2304">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2304">Return Values</span></span>

- <span data-ttu-id="e1c06-2305">**TX_SUCCESS**: (0X00) lyckad tråd återställning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="e1c06-2306">**TX_NOT_DONE**: (0x20) den angivna tråden är inte i ett TX_COMPLETED eller TX_TERMINATED tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="e1c06-2307">TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="e1c06-2308">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2309">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2309">Allowed From</span></span>

<span data-ttu-id="e1c06-2310">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2311">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2312">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2312">See Also</span></span>

- <span data-ttu-id="e1c06-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2313">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2314">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2316">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2323">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="e1c06-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2330">tx_thread_resume</span></span>

<span data-ttu-id="e1c06-2331">Återuppta inaktive rad program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2332">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2333">Description</span></span>

<span data-ttu-id="e1c06-2334">Den här tjänsten återupptar eller förbereder körning av en tråd som tidigare har avbrutits av ett ***tx_thread_suspend*** -anrop.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="e1c06-2335">Dessutom återupptar den här tjänsten trådar som skapats utan automatisk start.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2336">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2336">Parameters</span></span>

- <span data-ttu-id="e1c06-2337">**thread_ptr**: pekar mot en inaktive rad program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2338">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2338">Return Values</span></span>

- <span data-ttu-id="e1c06-2339">**TX_SUCCESS**: (0X00) lyckad tråd återgång.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="e1c06-2340">**TX_SUSPEND_LIFTED**: (0x19) fastställde tidigare fördröjd avstängning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="e1c06-2341">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2342">**TX_RESUME_ERROR**: (0x12) den angivna tråden har inte pausats eller har tidigare avbrutits av en annan tjänst än **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2343">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2343">Allowed From</span></span>

<span data-ttu-id="e1c06-2344">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2345">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2345">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2346">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2347">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2348">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2348">See Also</span></span>

- <span data-ttu-id="e1c06-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2349">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2350">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2352">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2359">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="e1c06-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2366">tx_thread_sleep</span></span>

<span data-ttu-id="e1c06-2367">Pausa den aktuella tråden för angiven tid</span><span class="sxs-lookup"><span data-stu-id="e1c06-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2368">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="e1c06-2369">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2369">Description</span></span>

<span data-ttu-id="e1c06-2370">Den här tjänsten gör att den anropande tråden pausas för det angivna antalet timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="e1c06-2371">Mängden fysiskt klock slag som är associerad med ett timer-Tick är programspecifik.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="e1c06-2372">Den här tjänsten kan endast anropas från en program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2373">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2373">Parameters</span></span>

- <span data-ttu-id="e1c06-2374">**timer_ticks**: antalet timer-Tick för att pausa den anropande program tråden, mellan 0 och 0xffffffff.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="e1c06-2375">Om 0 anges returnerar tjänsten omedelbart.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2376">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2376">Return Values</span></span>

- <span data-ttu-id="e1c06-2377">**TX_SUCCESS**: (0X00) lyckad tråd ström.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="e1c06-2378">**TX_WAIT_ABORTED**: (0X1A) SUS pensionen avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="e1c06-2379">**TX_CALLER_ERROR**: (0X13)-tjänsten anropades från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2380">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2380">Allowed From</span></span>

<span data-ttu-id="e1c06-2381">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2382">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2382">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2383">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2384">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2385">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2385">See Also</span></span>

- <span data-ttu-id="e1c06-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2386">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2387">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2389">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2396">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2397">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="e1c06-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="e1c06-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="e1c06-2404">Exkludera tråd körning i en uppsättning kärnor</span><span class="sxs-lookup"><span data-stu-id="e1c06-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2405">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="e1c06-2406">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2406">Description</span></span>

<span data-ttu-id="e1c06-2407">Den här funktionen utesluter den angivna tråden från att köras på den eller de kärnor som anges i bit kartan som kallas "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="e1c06-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="e1c06-2408">Varje bit i "*exclusion_map*" representerar en kärna (bit 0 representerar Core 0 osv.).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="e1c06-2409">Om biten anges undantas motsvarande kärna från att köra den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2410">Användningen av processor undantag kan orsaka ytterligare bearbetning i tråden till kärn mappnings logik för att hitta den optimala matchningen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="e1c06-2411">Den här bearbetningen har bundits av antalet färdiga trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2412">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2412">Parameters</span></span> 

- <span data-ttu-id="e1c06-2413">**thread_ptr**: pekare till tråd för att ändra kärn undantag.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="e1c06-2414">**exclusion_map**: bit karta där en Sit-bit visar att kärnan är exkluderad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="e1c06-2415">Genom att ange ett 0-värde kan tråden köras på alla kärnor (standard).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2416">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2416">Return Values</span></span>

- <span data-ttu-id="e1c06-2417">TX_SUCCESS: (0x00) lyckad kärn undantag.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="e1c06-2418">TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2419">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2419">Allowed From</span></span>

<span data-ttu-id="e1c06-2420">Initiering, ISR: er, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2421">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="e1c06-2422">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2422">See Also</span></span>

- <span data-ttu-id="e1c06-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="e1c06-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="e1c06-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="e1c06-2426">Hämtar trådens aktuella kärn undantag</span><span class="sxs-lookup"><span data-stu-id="e1c06-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2427">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2428">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2428">Description</span></span>

<span data-ttu-id="e1c06-2429">Den här funktionen returnerar den aktuella huvud undantags listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2430">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2430">Parameters</span></span>

- <span data-ttu-id="e1c06-2431">**thread_ptr**: pekare till tråd från vilken du vill hämta kärn undantaget.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="e1c06-2432">**exclusion_map_ptr**: målet för den aktuella Core exkluderings-bitars kartan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2433">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2433">Return Values</span></span>

- <span data-ttu-id="e1c06-2434">TX_SUCCESS: (0x00) lyckad hämtning av trådens kärn undantag.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="e1c06-2435">TX_THREAD_ERROR: (0x0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="e1c06-2436">TX_PTR_ERROR: (0x03) ogiltig utelämnande destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2437">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2437">Allowed From</span></span>

<span data-ttu-id="e1c06-2438">Initiering, ISR: er, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2439">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="e1c06-2440">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2440">See Also</span></span>

- <span data-ttu-id="e1c06-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="e1c06-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="e1c06-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="e1c06-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="e1c06-2444">Hämta kärnan i anroparen som körs</span><span class="sxs-lookup"><span data-stu-id="e1c06-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2445">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="e1c06-2446">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2446">Description</span></span>

<span data-ttu-id="e1c06-2447">Den här funktionen returnerar kärn-ID för den kärna som kör den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2448">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2448">Parameters</span></span>

<span data-ttu-id="e1c06-2449">Ingen</span><span class="sxs-lookup"><span data-stu-id="e1c06-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2450">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2450">Return Values</span></span>

- <span data-ttu-id="e1c06-2451">core_id: ID för den aktuella körnings kärnan (0 till TX_THREAD_SMP_MAX_CORES-1)</span><span class="sxs-lookup"><span data-stu-id="e1c06-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2452">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2452">Allowed From</span></span>

<span data-ttu-id="e1c06-2453">Initiering, ISR: er, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2454">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2455">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2455">See Also</span></span>

- <span data-ttu-id="e1c06-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="e1c06-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="e1c06-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="e1c06-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="e1c06-2459">Registrera återanrop för tråds tack rings meddelande</span><span class="sxs-lookup"><span data-stu-id="e1c06-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2460">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="e1c06-2461">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2461">Description</span></span>

<span data-ttu-id="e1c06-2462">Den här tjänsten registrerar en funktion för motringning av meddelanden för hantering av tråds tack fel.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="e1c06-2463">När ThreadX SMP identifierar ett tråds tack fel under körningen, anropar den denna aviserings funktion för att bearbeta felet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="e1c06-2464">Bearbetningen av felet har definierats fullständigt av programmet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="e1c06-2465">Allt från att pausa den överträdande tråden för att återställa hela systemet kan göras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2466">ThreadX SMP-biblioteket måste ha skapats med **TX_ENABLE_STACK_CHECKING** definierat för att den här tjänsten ska returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2467">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2467">Parameters</span></span>

- <span data-ttu-id="e1c06-2468">**error_handler**: pekar mot programmets stack fel hanterings funktion.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="e1c06-2469">Om det här värdet är TX_NULL inaktive ras meddelandet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2470">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2470">Return Values</span></span>

- <span data-ttu-id="e1c06-2471">**TX_SUCCESS**: (0X00) lyckad tråd återställning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="e1c06-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2473">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2473">Allowed From</span></span>

<span data-ttu-id="e1c06-2474">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2475">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2476">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2476">See Also</span></span>

- <span data-ttu-id="e1c06-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2477">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2478">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2480">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2487">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2488">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="e1c06-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2494">tx_thread_suspend</span></span>

<span data-ttu-id="e1c06-2495">Pausa program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2496">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2497">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2497">Description</span></span>

<span data-ttu-id="e1c06-2498">Den här tjänsten pausar den angivna program tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="e1c06-2499">En tråd kan anropa den här tjänsten för att inaktivera den.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2500">Om den angivna tråden redan har pausats av en annan anledning hålls denna SUS Pension internt tills den föregående uppskjutningen har lyfts upp.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="e1c06-2501">När detta sker utförs denna avbrytande avstängning av den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="e1c06-2502">Ytterligare avstängnings begär Anden utan tillstånd har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="e1c06-2503">Efter inaktive rad måste tråden återupptas genom att ***tx_thread_resume*** köras igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="e1c06-2504">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2504">Parameters</span></span>

- <span data-ttu-id="e1c06-2505">**thread_ptr**: pekar mot en program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2506">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2506">Return Values</span></span>

- <span data-ttu-id="e1c06-2507">**TX_SUCCESS**: (0x00) en lyckad tråd har pausats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="e1c06-2508">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2509">**TX_SUSPEND_ERROR**: (0x14) den angivna tråden är i ett avslutat eller slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="e1c06-2510">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2511">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2511">Allowed From</span></span>

<span data-ttu-id="e1c06-2512">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2513">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2513">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2514">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2515">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2516">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2516">See Also</span></span>

- <span data-ttu-id="e1c06-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2517">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2518">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2520">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2527">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2528">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="e1c06-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2534">tx_thread_terminate</span></span>

<span data-ttu-id="e1c06-2535">Avslutar program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2536">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2537">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2537">Description</span></span>

<span data-ttu-id="e1c06-2538">Den här tjänsten avslutar den angivna program tråden oavsett om tråden är inaktive rad eller inte.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="e1c06-2539">En tråd kan anropa den här tjänsten för att avsluta sig själv.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2540">Efter att ha avslut ATS måste tråden återställas för att den ska kunna köras igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="e1c06-2541">Det är programmets ansvar att se till att tråden är i ett tillstånd som är lämpligt för uppsägning.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="e1c06-2542">En tråd bör till exempel inte avslutas under kritisk program bearbetning eller i andra komponenter för mellanprogram där den kan lämna sådan bearbetning i ett okänt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2543">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2543">Parameters</span></span>

- <span data-ttu-id="e1c06-2544">**thread_ptr**: pekar på program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2545">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2545">Return Values</span></span>

- <span data-ttu-id="e1c06-2546">**TX_SUCCESS**: (0X00) lyckad tråd avslutas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="e1c06-2547">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2548">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2549">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2549">Allowed From</span></span>

<span data-ttu-id="e1c06-2550">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2551">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2551">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2552">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2553">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2554">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2554">See Also</span></span>

- <span data-ttu-id="e1c06-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2555">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2556">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2558">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2565">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2566">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="e1c06-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="e1c06-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="e1c06-2573">Ändra tid – sektor för program tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2574">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="e1c06-2575">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2575">Description</span></span>

<span data-ttu-id="e1c06-2576">Den här tjänsten ändrar tids segmentet för den angivna program tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="e1c06-2577">Om du väljer en tids gräns för en tråd är det inte säkert att det kör fler än det angivna antalet timer-Tick innan andra trådar av samma eller högre prioritet har möjlighet att köra.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2578">Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2579">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2579">Parameters</span></span>

- <span data-ttu-id="e1c06-2580">**thread_ptr**: pekar på program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="e1c06-2581">**new_time_slice**: nytt tids segment värde.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="e1c06-2582">Giltiga värden är TX_NO_TIME_SLICE och numeriska värden från 1 till 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="e1c06-2583">**old_time_slice**: pekar på plats för lagring av föregående timeslice-värde för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2584">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2584">Return Values</span></span>

- <span data-ttu-id="e1c06-2585">**TX_SUCCESS**: (0X00) slutförd Time-slice-chans.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="e1c06-2586">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2587">TX_PTR_ERROR: (0x03) ogiltig pekare till föregående tid – sektor lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="e1c06-2588">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2589">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2589">Allowed From</span></span>

<span data-ttu-id="e1c06-2590">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2591">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2591">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2592">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2593">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2593">Example</span></span>

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

/* Change the time-slice of the thread associated with
   "my_thread" to 20. This will mean that "my_thread"
   can only run for 20 timer-ticks consecutively before
   other threads of equal or higher priority get a chance
   to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
                             &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
   has been changed to 20 and the previous time-slice is
   in "my_old_time_slice." */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2594">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2594">See Also</span></span>

- <span data-ttu-id="e1c06-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2595">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2596">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2598">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2605">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2606">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="e1c06-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e1c06-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="e1c06-2613">Avbryt avstängning av angiven tråd</span><span class="sxs-lookup"><span data-stu-id="e1c06-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2614">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="e1c06-2615">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2615">Description</span></span>

<span data-ttu-id="e1c06-2616">Den här tjänsten avbryter vilo läge eller andra objekt avbrott i den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="e1c06-2617">Om vänte tiden avbryts returneras ett TX_WAIT_ABORTED-värde från den tjänst som tråden väntade på.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2618">Den här tjänsten frigör inte explicit avstängning som görs av tjänsten tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2619">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2619">Parameters</span></span>

- <span data-ttu-id="e1c06-2620">**thread_ptr**: pekar mot en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2621">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2621">Return Values</span></span>

- <span data-ttu-id="e1c06-2622">**TX_SUCCESS**: (0X00) lyckad tråd väntan avbryts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="e1c06-2623">TX_THREAD_ERROR: (0x0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="e1c06-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) den angivna tråden är inte i ett vänte läge.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2625">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2625">Allowed From</span></span>

<span data-ttu-id="e1c06-2626">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2627">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2627">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2628">Ja</span><span class="sxs-lookup"><span data-stu-id="e1c06-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2629">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2630">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2630">See Also</span></span>

- <span data-ttu-id="e1c06-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2631">tx_thread_create</span></span>
- <span data-ttu-id="e1c06-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2632">tx_thread_delete</span></span>
- <span data-ttu-id="e1c06-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="e1c06-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2634">tx_thread_identify</span></span>
- <span data-ttu-id="e1c06-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="e1c06-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="e1c06-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="e1c06-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="e1c06-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e1c06-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="e1c06-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e1c06-2641">tx_thread_reset</span></span>
- <span data-ttu-id="e1c06-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e1c06-2642">tx_thread_resume</span></span>
- <span data-ttu-id="e1c06-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e1c06-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="e1c06-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="e1c06-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="e1c06-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e1c06-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="e1c06-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="e1c06-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="e1c06-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2648">tx_time_get</span></span>

<span data-ttu-id="e1c06-2649">Hämtar aktuell tid</span><span class="sxs-lookup"><span data-stu-id="e1c06-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2650">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="e1c06-2651">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2651">Description</span></span>

<span data-ttu-id="e1c06-2652">Den här tjänsten returnerar innehållet i den interna system klockan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="e1c06-2653">Varje timertick ökar den interna system klockan med ett.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="e1c06-2654">System klockan är inställd på noll under initieringen och kan ändras till ett särskilt värde av tjänsten ***tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2655">Den faktiska tiden som varje timer-Tick representerar är programspecifik.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2656">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2656">Parameters</span></span>

<span data-ttu-id="e1c06-2657">Ingen</span><span class="sxs-lookup"><span data-stu-id="e1c06-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2658">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2658">Return Values</span></span>

- <span data-ttu-id="e1c06-2659">system klock streck: värde för intern, kostnads fri körning, system klocka.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2660">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2660">Allowed From</span></span>

<span data-ttu-id="e1c06-2661">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2662">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2662">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2663">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2664">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2665">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2665">See Also</span></span>

- <span data-ttu-id="e1c06-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="e1c06-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="e1c06-2667">tx_time_set</span></span>

<span data-ttu-id="e1c06-2668">Anger aktuell tid</span><span class="sxs-lookup"><span data-stu-id="e1c06-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2669">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="e1c06-2670">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2670">Description</span></span>

<span data-ttu-id="e1c06-2671">Den här tjänsten anger den interna system klockan för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="e1c06-2672">Varje timer-Ticket ökar den interna system klockan med ett.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2673">Den faktiska tiden som varje timer-Tick representerar är programspecifik.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2674">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2674">Parameters</span></span>

- <span data-ttu-id="e1c06-2675">**new_time**: en ny tid för att ställa system klockan, giltiga värden är mellan 0 och 0xffffffff.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2676">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2676">Return Values</span></span>

<span data-ttu-id="e1c06-2677">Inget</span><span class="sxs-lookup"><span data-stu-id="e1c06-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2678">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2678">Allowed From</span></span>

<span data-ttu-id="e1c06-2679">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2680">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2680">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2681">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2682">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2683">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2683">See Also</span></span>

- <span data-ttu-id="e1c06-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="e1c06-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2685">tx_timer_activate</span></span>

<span data-ttu-id="e1c06-2686">Aktivera program-timer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2687">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2688">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2688">Description</span></span>

<span data-ttu-id="e1c06-2689">Den här tjänsten aktiverar den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="e1c06-2690">Utgångs rutinerna för timers som går ut samtidigt körs i den ordning som de aktiverades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-2691">Att en förfallen timer med en bild måste återställas via **tx_timer_change** innan den kan aktive ras igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2692">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2692">Parameters</span></span>

- <span data-ttu-id="e1c06-2693">**timer_ptr**: pekar mot en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2694">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2694">Return Values</span></span>

- <span data-ttu-id="e1c06-2695">**TX_SUCCESS**: (0X00) lyckad aktivering av programtimer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="e1c06-2696">**TX_TIMER_ERROR**: (0X15) ogiltig Application timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="e1c06-2697">**TX_ACTIVATE_ERROR**: (0X17) timern var redan aktiv eller är en timer för en bild som redan har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2698">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2698">Allowed From</span></span>

<span data-ttu-id="e1c06-2699">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2700">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2700">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2701">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2702">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2703">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2703">See Also</span></span>

- <span data-ttu-id="e1c06-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2704">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2705">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2707">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="e1c06-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2711">tx_timer_change</span></span>

<span data-ttu-id="e1c06-2712">Ändra programmets timer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2713">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="e1c06-2714">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2714">Description</span></span>

<span data-ttu-id="e1c06-2715">Den här tjänsten ändrar utgångs egenskaperna för den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="e1c06-2716">Timern måste inaktive ras innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2717">Ett anrop till tjänsten **tx_timer_activate** krävs efter den här tjänsten för att starta timern igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2718">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2718">Parameters</span></span>

- <span data-ttu-id="e1c06-2719">**timer_ptr**: pekar mot ett timer Control-Block.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="e1c06-2720">**initial_ticks**: anger det ursprungliga antalet Tick för förfallo datum för timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="e1c06-2721">Giltiga värden är mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="e1c06-2722">**reschedule_ticks**: anger antalet Tick för alla timer-förfaller efter den första.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="e1c06-2723">En noll för den här parametern gör timern till en timer med en bild.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="e1c06-2724">Annars, för periodiska timers, är de juridiska värdena mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e1c06-2725">Att en förfallen timer med en bild måste återställas via **tx_timer_change** innan den kan aktive ras igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2726">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2726">Return Values</span></span>

- <span data-ttu-id="e1c06-2727">**TX_SUCCESS**: (0X00) lyckad ändring av programtimern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="e1c06-2728">TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="e1c06-2729">TX_TICK_ERROR: (0x16) ogiltigt värde (noll) angavs för inledande Tick.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="e1c06-2730">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2731">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2731">Allowed From</span></span>

<span data-ttu-id="e1c06-2732">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2733">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2733">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2734">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2735">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2735">Example</span></span>

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2736">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2736">See Also</span></span>

- <span data-ttu-id="e1c06-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2737">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2738">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2740">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="e1c06-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2744">tx_timer_create</span></span>

<span data-ttu-id="e1c06-2745">Skapa programtimer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2746">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="e1c06-2747">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2747">Description</span></span>

<span data-ttu-id="e1c06-2748">Den här tjänsten skapar en programtimer med angiven förfallo funktion och periodisk.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2749">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2749">Parameters</span></span>

- <span data-ttu-id="e1c06-2750">**timer_ptr**: pekar mot ett timer Control-Block</span><span class="sxs-lookup"><span data-stu-id="e1c06-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="e1c06-2751">**name_ptr**: pekar mot namnet på timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="e1c06-2752">**expiration_function**: program funktion som anropas när timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="e1c06-2753">**expiration_input**: indatamängden för att skicka till Expires-funktionen när timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="e1c06-2754">**initial_ticks**: anger det ursprungliga antalet Tick för förfallo datum för timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="e1c06-2755">Giltiga värden är mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="e1c06-2756">**reschedule_ticks**: anger antalet Tick för alla timer-förfaller efter den första.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="e1c06-2757">En noll för den här parametern gör timern till en timer med en bild.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="e1c06-2758">Annars, för periodiska timers, är de juridiska värdena mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e1c06-2759">När en timer för en bild har gått ut måste den återställas via tx_timer_change innan den kan aktive ras igen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="e1c06-2760">**auto_activate**: anger om timern aktive ras automatiskt när den skapas.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="e1c06-2761">Om det här värdet är **TX_AUTO_ACTIVATE** (0x01) blir timern aktiv.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="e1c06-2762">Annars, om värdet **TX_NO_ACTIVATE** (0x00) är markerat, skapas timern i ett icke-aktivt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="e1c06-2763">I det här fallet är ett efterföljande **_tx_timer_activate_** tjänst anrop nödvändigt för att hämta den timer som faktiskt startades.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2764">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2764">Return Values</span></span>

- <span data-ttu-id="e1c06-2765">**TX_SUCCESS**: (0X00) lyckad programgenerering av program.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="e1c06-2766">TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="e1c06-2767">Antingen är pekaren NULL eller också har timern redan skapats.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="e1c06-2768">TX_TICK_ERROR: (0x16) ogiltigt värde (noll) angavs för inledande Tick.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="e1c06-2769">TX_ACTIVATE_ERROR: (0x17) ogiltig aktivering har valts.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="e1c06-2770">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2771">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2771">Allowed From</span></span>

<span data-ttu-id="e1c06-2772">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2773">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2773">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2774">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2775">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2775">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2776">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2776">See Also</span></span>

- <span data-ttu-id="e1c06-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2777">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2778">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2780">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="e1c06-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="e1c06-2785">Inaktivera Application timer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2786">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="e1c06-2787">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2787">Description</span></span>

<span data-ttu-id="e1c06-2788">Den här tjänsten inaktiverar den angivna programtimern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="e1c06-2789">Om timern redan är inaktive rad har den här tjänsten ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2790">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2790">Parameters</span></span> 

- <span data-ttu-id="e1c06-2791">**timer_ptr**: pekar mot en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2792">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2792">Return Values</span></span>

- <span data-ttu-id="e1c06-2793">**TX_SUCCESS**: (0X00) slutförde inaktive ring av program.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="e1c06-2794">TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2795">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2795">Allowed From</span></span>

<span data-ttu-id="e1c06-2796">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2797">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2797">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2798">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2799">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2800">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2800">See Also</span></span>

- <span data-ttu-id="e1c06-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2801">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2802">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2803">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2804">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="e1c06-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2808">tx_timer_delete</span></span>

<span data-ttu-id="e1c06-2809">Ta bort program timer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2810">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2811">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2811">Description</span></span>

<span data-ttu-id="e1c06-2812">Den här tjänsten tar bort den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2813">Det är programmets ansvar att förhindra användning av en borttagen timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2814">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2814">Parameters</span></span> 

- <span data-ttu-id="e1c06-2815">**timer_ptr**: pekar mot en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2816">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2816">Return Values</span></span>

- <span data-ttu-id="e1c06-2817">**TX_SUCCESS**: (0x00) en slutförd borttagning av program timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="e1c06-2818">TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="e1c06-2819">TX_CALLER_ERROR: (0x13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2820">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2820">Allowed From</span></span>

<span data-ttu-id="e1c06-2821">Konversation</span><span class="sxs-lookup"><span data-stu-id="e1c06-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2822">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2822">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2823">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2824">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2825">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2825">See Also</span></span>

- <span data-ttu-id="e1c06-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2826">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2827">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2828">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="e1c06-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2833">tx_timer_info_get</span></span>

<span data-ttu-id="e1c06-2834">Hämta information om en programtimer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2835">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="e1c06-2836">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2836">Description</span></span>

<span data-ttu-id="e1c06-2837">Den här tjänsten hämtar information om den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2838">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2838">Parameters</span></span>

- <span data-ttu-id="e1c06-2839">**timer_ptr**: pekar mot en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="e1c06-2840">**Name**: pekare till målet för visaren till timerns namn.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="e1c06-2841">**aktiv**: pekare till målet för den timer-aktiva indikeringen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="e1c06-2842">Om timern är inaktiv eller om den här tjänsten anropas från själva timern returneras ett TX_FALSE-värde.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="e1c06-2843">Annars returneras ett TX_TRUE-värde om timern är aktiv.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="e1c06-2844">**remaining_ticks**: pekar mot mål för antalet timer-Tick kvar innan timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="e1c06-2845">**reschedule_ticks**: pekar mot mål för antalet timer-Tick som ska användas för att automatiskt schemalägga denna timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="e1c06-2846">Om värdet är noll är timern en One-bild och kommer inte att omplaneras.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="e1c06-2847">**next_timer**: pekar på destinationen för visaren för nästa skapade program-timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c06-2848">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2849">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2849">Return Values</span></span>

- <span data-ttu-id="e1c06-2850">**TX_SUCCESS**: (0x00) information om slutförd timer-information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="e1c06-2851">TX_TIMER_ERROR: (0x15) ogiltig Application timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2852">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2852">Allowed From</span></span>

<span data-ttu-id="e1c06-2853">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="e1c06-2854">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="e1c06-2854">Preemption Possible</span></span>

<span data-ttu-id="e1c06-2855">Inga</span><span class="sxs-lookup"><span data-stu-id="e1c06-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2856">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2856">Example</span></span>

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2857">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2857">See Also</span></span>

- <span data-ttu-id="e1c06-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2858">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2859">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2860">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2862">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="e1c06-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="e1c06-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="e1c06-2867">Hämta information om timer-prestanda</span><span class="sxs-lookup"><span data-stu-id="e1c06-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2868">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="e1c06-2869">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2869">Description</span></span>

<span data-ttu-id="e1c06-2870">Den här tjänsten hämtar prestanda information om den angivna program tids gränsen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2871">ThreadX SMP-biblioteket och programmet måste skapas med **TX_TIMER_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2872">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2872">Parameters</span></span> 

- <span data-ttu-id="e1c06-2873">**timer_ptr**: pekare till tidigare skapad timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="e1c06-2874">**aktiverar**: pekar mot mål för antalet aktiverings begär Anden som utförts i denna timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="e1c06-2875">**återaktiverar**: pekare till målet för antalet automatiska återaktiveringar som utförs på denna periodiska timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="e1c06-2876">**inaktive ras**: pekare till målet för antalet förfrågningar om inaktivitet som utförts på denna timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="e1c06-2877">**förfaller**: pekar mot mål för antalet förfallo datum för den här timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="e1c06-2878">**expiration_adjusts**: pekar mot mål för antalet interna utgångs justeringar som utförts i denna timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="e1c06-2879">De här justeringarna görs i den tids lösa bearbetningen för timers som är större än standard storleken för timer-listan (som standard timers med förfallo datum som är större än 32 Tick).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2880">Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2881">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2881">Return Values</span></span>

- <span data-ttu-id="e1c06-2882">**TX_SUCCESS**: (0x00) prestanda för slutförd timer.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="e1c06-2883">**TX_PTR_ERROR**: (0X03) ogiltig timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="e1c06-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2885">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2885">Allowed From</span></span>

<span data-ttu-id="e1c06-2886">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2887">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2887">Example</span></span>

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2888">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2888">See Also</span></span>

- <span data-ttu-id="e1c06-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2889">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2890">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2891">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2893">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="e1c06-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="e1c06-2897">Hämta information om system prestanda för timer</span><span class="sxs-lookup"><span data-stu-id="e1c06-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2898">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="e1c06-2899">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2899">Description</span></span>

<span data-ttu-id="e1c06-2900">Den här tjänsten hämtar prestanda information om alla program timers i systemet.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2901">ThreadX SMP-biblioteket och programmet måste skapas med **TX_TIMER_ENABLE_PERFORMANCE_INFO** som definierats för den här tjänsten för att returnera prestanda information.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2902">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2902">Parameters</span></span>

- <span data-ttu-id="e1c06-2903">**aktiverar**: pekar mot mål för det totala antalet aktiverings begär Anden som utförts på alla timers.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="e1c06-2904">**återaktiverar**: pekar mot mål för det totala antalet automatiska återaktivitet som utförts på alla periodiska timers.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="e1c06-2905">**inaktive ras**: pekare till mål för det totala antalet begär Anden om inaktive ring som utförts för alla timers.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="e1c06-2906">**förfaller**: pekar mot mål för det totala antalet förfallo datum för alla timers.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="e1c06-2907">**expiration_adjusts**: pekar mot mål för det totala antalet interna utgångs justeringar som utförts för alla timers.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="e1c06-2908">De här justeringarna görs i den tids lösa bearbetningen för timers som är större än standard storleken för timer-listan (som standard timers med förfallo datum som är större än 32 Tick).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2909">Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2910">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2910">Return Values</span></span>

- <span data-ttu-id="e1c06-2911">**TX_SUCCESS**: (0X00) lyckades system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="e1c06-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) systemet har inte kompilerats med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2913">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2913">Allowed From</span></span>

<span data-ttu-id="e1c06-2914">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="e1c06-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2915">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2915">Example</span></span>

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2916">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2916">See Also</span></span>

- <span data-ttu-id="e1c06-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2917">tx_timer_activate</span></span>
- <span data-ttu-id="e1c06-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e1c06-2918">tx_timer_change</span></span>
- <span data-ttu-id="e1c06-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e1c06-2919">tx_timer_create</span></span>
- <span data-ttu-id="e1c06-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e1c06-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="e1c06-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e1c06-2921">tx_timer_delete</span></span>
- <span data-ttu-id="e1c06-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="e1c06-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="e1c06-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="e1c06-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="e1c06-2925">Uteslut timer-körning i en uppsättning kärnor</span><span class="sxs-lookup"><span data-stu-id="e1c06-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2926">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="e1c06-2927">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2927">Description</span></span>

<span data-ttu-id="e1c06-2928">Den här funktionen utesluter den angivna timern från att köras på de kärnor som anges i bit kartan med namnet "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="e1c06-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="e1c06-2929">Varje bit i "*exclusion_map*" representerar en kärna (bit 0 representerar Core 0 osv.).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="e1c06-2930">Om biten anges undantas motsvarande kärna från att köra den angivna timern.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1c06-2931">Användningen av processor undantag kan orsaka ytterligare bearbetning i tråden till kärn mappnings logik för att hitta den optimala matchningen.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="e1c06-2932">Den här bearbetningen har bundits av antalet färdiga trådar.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2933">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2933">Parameters</span></span>

- <span data-ttu-id="e1c06-2934">**timer_ptr**: pekar mot timer för att ändra kärn undantag.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="e1c06-2935">**exclusion_map**: bit karta där en Sit-bit visar att kärnan är exkluderad.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="e1c06-2936">Om du anger ett 0-värde kan timern köras på alla kärnor (standard).</span><span class="sxs-lookup"><span data-stu-id="e1c06-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2937">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2937">Return Values</span></span>

- <span data-ttu-id="e1c06-2938">**TX_SUCCESS** (0X00) lyckad kärn undantag.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="e1c06-2939">**TX_TIMER_ERROR** (0X0E) ogiltig timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2940">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2940">Allowed From</span></span>

<span data-ttu-id="e1c06-2941">Initiering, ISR: er, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2942">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="e1c06-2943">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2943">See Also</span></span>

- <span data-ttu-id="e1c06-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="e1c06-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="e1c06-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="e1c06-2946">Hämtar timerns aktuella kärn undantag</span><span class="sxs-lookup"><span data-stu-id="e1c06-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="e1c06-2947">Prototyp</span><span class="sxs-lookup"><span data-stu-id="e1c06-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="e1c06-2948">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1c06-2948">Description</span></span>

<span data-ttu-id="e1c06-2949">Den här funktionen returnerar den aktuella huvud undantags listan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1c06-2950">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e1c06-2950">Parameters</span></span>

- <span data-ttu-id="e1c06-2951">**timer_ptr**: pekare till timer från vilken du vill hämta kärn undantaget.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="e1c06-2952">**exclusion_map_ptr**: målet för den aktuella Core exkluderings-bitars kartan.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1c06-2953">Retur värden</span><span class="sxs-lookup"><span data-stu-id="e1c06-2953">Return Values</span></span>

- <span data-ttu-id="e1c06-2954">TX_SUCCESS: (0x00) lyckad hämtning av timerns kärn undantag.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="e1c06-2955">TX_TIMER_ERROR: (0x0E) ogiltig timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="e1c06-2956">TX_PTR_ERROR: (0x03) ogiltig utelämnande destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="e1c06-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1c06-2957">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="e1c06-2957">Allowed From</span></span>

<span data-ttu-id="e1c06-2958">Initiering, ISR: er, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="e1c06-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="e1c06-2959">Exempel</span><span class="sxs-lookup"><span data-stu-id="e1c06-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="e1c06-2960">Se även</span><span class="sxs-lookup"><span data-stu-id="e1c06-2960">See Also</span></span>

- <span data-ttu-id="e1c06-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="e1c06-2961">tx_timer_smp_core_exclude</span></span>