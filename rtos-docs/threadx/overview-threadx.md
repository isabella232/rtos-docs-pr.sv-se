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
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="e887d-103">Översikt över Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="e887d-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="e887d-104">Azure RTOS ThreadX är Microsofts avancerade branschklass Real-Time RTOS (Operating System) som utformats särskilt för djupt inbäddade, realtidsbaserade och IoT-program.</span><span class="sxs-lookup"><span data-stu-id="e887d-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="e887d-105">Azure RTOS ThreadX tillhandahåller avancerad schemaläggning, kommunikation, synkronisering, timer, minneshantering och avbrottshantering.</span><span class="sxs-lookup"><span data-stu-id="e887d-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="e887d-106">Dessutom har Azure RTOS ThreadX många avancerade funktioner, inklusive dess picokernel™-arkitektur, preemption-threshold™ scheduling, event-chaining, ™ execution profiling, performance metrics och system event tracing.</span><span class="sxs-lookup"><span data-stu-id="e887d-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="e887d-107">I kombination med den förstklassiga användarvänligheten är Azure RTOS ThreadX det perfekta valet för de mest krävande inbäddade programmen.</span><span class="sxs-lookup"><span data-stu-id="e887d-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="e887d-108">Från och med 2017 har Azure RTOS ThreadX över 6,2 miljarder distributioner i en mängd olika produkter, inklusive konsumentenheter, medicinsk elektronik och industriell kontrollutrustning.</span><span class="sxs-lookup"><span data-stu-id="e887d-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="e887d-109">API-protokoll</span><span class="sxs-lookup"><span data-stu-id="e887d-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="e887d-110">Azure RTOS ThreadX Services</span><span class="sxs-lookup"><span data-stu-id="e887d-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="e887d-111">Skapa dynamiska trådar</span><span class="sxs-lookup"><span data-stu-id="e887d-111">Dynamic thread creation</span></span>
* <span data-ttu-id="e887d-112">Inga gränser för antalet trådar</span><span class="sxs-lookup"><span data-stu-id="e887d-112">No limits on the number of threads</span></span>
* <span data-ttu-id="e887d-113">Huvudtråd-API:er är:</span><span class="sxs-lookup"><span data-stu-id="e887d-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="e887d-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="e887d-114">tx_thread_create</span></span>
  * <span data-ttu-id="e887d-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-115">tx_thread_delete</span></span>
  * <span data-ttu-id="e887d-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="e887d-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="e887d-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="e887d-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="e887d-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="e887d-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="e887d-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="e887d-119">tx_thread_reset</span></span>
  * <span data-ttu-id="e887d-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="e887d-120">tx_thread_resume</span></span>
  * <span data-ttu-id="e887d-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="e887d-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="e887d-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="e887d-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="e887d-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="e887d-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="e887d-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="e887d-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="e887d-125">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="e887d-126">Meddelandeköer</span><span class="sxs-lookup"><span data-stu-id="e887d-126">Message Queues</span></span>

* <span data-ttu-id="e887d-127">Skapa dynamisk kö</span><span class="sxs-lookup"><span data-stu-id="e887d-127">Dynamic queue creation</span></span>
* <span data-ttu-id="e887d-128">Inga gränser för antalet köer</span><span class="sxs-lookup"><span data-stu-id="e887d-128">No limits on the number of queues</span></span>
* <span data-ttu-id="e887d-129">Meddelanden som kopieras efter värde (eller som referens via pekare)</span><span class="sxs-lookup"><span data-stu-id="e887d-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="e887d-130">Meddelandestorlekar från 1 till 16 32-bitars ord</span><span class="sxs-lookup"><span data-stu-id="e887d-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="e887d-131">Valfri tråduppstängning är tom och full</span><span class="sxs-lookup"><span data-stu-id="e887d-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="e887d-132">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="e887d-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e887d-133">API:er för meddelandeköer är:</span><span class="sxs-lookup"><span data-stu-id="e887d-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="e887d-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="e887d-134">tx_queue_create</span></span>
  * <span data-ttu-id="e887d-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-135">tx_queue_delete</span></span>
  * <span data-ttu-id="e887d-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="e887d-136">tx_queue_flush</span></span>
  * <span data-ttu-id="e887d-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="e887d-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="e887d-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="e887d-138">tx_queue_receive</span></span>
  * <span data-ttu-id="e887d-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="e887d-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="e887d-140">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="e887d-141">Räkna semaforer</span><span class="sxs-lookup"><span data-stu-id="e887d-141">Counting Semaphores</span></span>

* <span data-ttu-id="e887d-142">Dynamiskt skapande av semaphore</span><span class="sxs-lookup"><span data-stu-id="e887d-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="e887d-143">Inga gränser för antalet semaforer</span><span class="sxs-lookup"><span data-stu-id="e887d-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="e887d-144">Semaforer för 32-bitars räkning (0 till 4 294 967 295)</span><span class="sxs-lookup"><span data-stu-id="e887d-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="e887d-145">Stöd för konsumentproducent eller resursskydd</span><span class="sxs-lookup"><span data-stu-id="e887d-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="e887d-146">Valfri trådavstängning när semaphore inte är tillgänglig</span><span class="sxs-lookup"><span data-stu-id="e887d-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="e887d-147">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="e887d-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e887d-148">De viktigaste semafor-API:erna är:</span><span class="sxs-lookup"><span data-stu-id="e887d-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="e887d-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="e887d-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="e887d-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="e887d-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="e887d-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="e887d-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="e887d-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="e887d-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="e887d-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="e887d-154">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="e887d-155">Mutexes</span><span class="sxs-lookup"><span data-stu-id="e887d-155">Mutexes</span></span>

* <span data-ttu-id="e887d-156">Dynamiskt skapande av mutex</span><span class="sxs-lookup"><span data-stu-id="e887d-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="e887d-157">Inga begränsningar för antalet mutexer</span><span class="sxs-lookup"><span data-stu-id="e887d-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="e887d-158">Kapslat resursskydd stöds</span><span class="sxs-lookup"><span data-stu-id="e887d-158">Nested resource protection supported</span></span>
* <span data-ttu-id="e887d-159">Valfritt prioritetsarv som stöds</span><span class="sxs-lookup"><span data-stu-id="e887d-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="e887d-160">Valfri tråduppstängning när mutex inte är tillgängligt</span><span class="sxs-lookup"><span data-stu-id="e887d-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="e887d-161">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="e887d-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e887d-162">De viktigaste mutex-API:erna är:</span><span class="sxs-lookup"><span data-stu-id="e887d-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="e887d-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="e887d-163">tx_mutex_create</span></span>
  * <span data-ttu-id="e887d-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="e887d-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="e887d-165">tx_mutex_get</span></span>
  * <span data-ttu-id="e887d-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="e887d-166">tx_mutex_put</span></span>
* <span data-ttu-id="e887d-167">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="e887d-168">Händelseflaggor</span><span class="sxs-lookup"><span data-stu-id="e887d-168">Event Flags</span></span>

* <span data-ttu-id="e887d-169">Skapa dynamisk händelseflaggan</span><span class="sxs-lookup"><span data-stu-id="e887d-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="e887d-170">Inga gränser för antalet händelseflaggasgrupper</span><span class="sxs-lookup"><span data-stu-id="e887d-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="e887d-171">Synkronisering av en tråd eller flera trådar</span><span class="sxs-lookup"><span data-stu-id="e887d-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="e887d-172">Atomic get and clear stöds</span><span class="sxs-lookup"><span data-stu-id="e887d-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="e887d-173">Valfri multitrådsavstängning vid AND/OR-uppsättning händelser</span><span class="sxs-lookup"><span data-stu-id="e887d-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="e887d-174">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="e887d-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e887d-175">Huvudhändelseflaggans API:er är:</span><span class="sxs-lookup"><span data-stu-id="e887d-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="e887d-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="e887d-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="e887d-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="e887d-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="e887d-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="e887d-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="e887d-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="e887d-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="e887d-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="e887d-181">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="e887d-182">Blockminnespooler</span><span class="sxs-lookup"><span data-stu-id="e887d-182">Block Memory Pools</span></span>

* <span data-ttu-id="e887d-183">Skapa dynamisk blockpool</span><span class="sxs-lookup"><span data-stu-id="e887d-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="e887d-184">Inga begränsningar för antalet blockpooler</span><span class="sxs-lookup"><span data-stu-id="e887d-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="e887d-185">Inga gränser för storleken på block med fast storlek eller storleken på poolen</span><span class="sxs-lookup"><span data-stu-id="e887d-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="e887d-186">Snabbaste möjliga minnesallokering/avtalsplats</span><span class="sxs-lookup"><span data-stu-id="e887d-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="e887d-187">Valfri tråduppstängning på tom pool</span><span class="sxs-lookup"><span data-stu-id="e887d-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="e887d-188">Valfri tidsgräns vid all låsning</span><span class="sxs-lookup"><span data-stu-id="e887d-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e887d-189">HUVUD-API:er för blockpooler är:</span><span class="sxs-lookup"><span data-stu-id="e887d-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="e887d-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="e887d-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="e887d-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="e887d-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="e887d-192">tx_block_allocate</span></span>
  * <span data-ttu-id="e887d-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="e887d-193">tx_block_release</span></span>
* <span data-ttu-id="e887d-194">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="e887d-195">Byteminnespooler</span><span class="sxs-lookup"><span data-stu-id="e887d-195">Byte Memory Pools</span></span>

* <span data-ttu-id="e887d-196">Skapa dynamisk bytepool</span><span class="sxs-lookup"><span data-stu-id="e887d-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="e887d-197">Inga gränser för antalet bytepooler</span><span class="sxs-lookup"><span data-stu-id="e887d-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="e887d-198">Inga gränser för bytepoolens storlek</span><span class="sxs-lookup"><span data-stu-id="e887d-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="e887d-199">Mest flexibel minnesallokering/avallokering med variabel längd</span><span class="sxs-lookup"><span data-stu-id="e887d-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="e887d-200">Allokeringsstorlek som stöds</span><span class="sxs-lookup"><span data-stu-id="e887d-200">Allocation size locality supported</span></span>
* <span data-ttu-id="e887d-201">Valfri tråduppstängning i tom pool</span><span class="sxs-lookup"><span data-stu-id="e887d-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="e887d-202">Valfri tidsgräns för all låsning</span><span class="sxs-lookup"><span data-stu-id="e887d-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e887d-203">API:er för huvudbytepooler är:</span><span class="sxs-lookup"><span data-stu-id="e887d-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="e887d-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="e887d-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="e887d-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="e887d-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="e887d-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="e887d-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="e887d-207">tx_byte_release</span></span>
* <span data-ttu-id="e887d-208">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="e887d-209">Programtimerar</span><span class="sxs-lookup"><span data-stu-id="e887d-209">Application Timers</span></span>

* <span data-ttu-id="e887d-210">Skapa dynamisk timer</span><span class="sxs-lookup"><span data-stu-id="e887d-210">Dynamic timer creation</span></span>
* <span data-ttu-id="e887d-211">Inga begränsningar för antalet timers</span><span class="sxs-lookup"><span data-stu-id="e887d-211">No limits on the number of timers</span></span>
* <span data-ttu-id="e887d-212">Periodiska timers eller one-shot-timers som stöds</span><span class="sxs-lookup"><span data-stu-id="e887d-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="e887d-213">Periodiska timers kan ha olika initiala förfallovärden</span><span class="sxs-lookup"><span data-stu-id="e887d-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="e887d-214">Ingen sökning efter timeraktivering eller inaktivering</span><span class="sxs-lookup"><span data-stu-id="e887d-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="e887d-215">Alla timers som körs från ett avbrott i maskinvarutimern</span><span class="sxs-lookup"><span data-stu-id="e887d-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="e887d-216">Huvudtimerns API:er är:</span><span class="sxs-lookup"><span data-stu-id="e887d-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="e887d-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="e887d-217">tx_timer_create</span></span>
  * <span data-ttu-id="e887d-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="e887d-218">tx_timer_delete</span></span>
  * <span data-ttu-id="e887d-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="e887d-219">tx_timer_activate</span></span>
  * <span data-ttu-id="e887d-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="e887d-220">tx_timer_change</span></span>
  * <span data-ttu-id="e887d-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="e887d-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="e887d-222">Ytterligare information och prestanda-API:er</span><span class="sxs-lookup"><span data-stu-id="e887d-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="e887d-223">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="e887d-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="e887d-224">Minimalt RAM-fotavtryck på 2 kB FLASH,1 kB</span><span class="sxs-lookup"><span data-stu-id="e887d-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="e887d-225">Snabb kontextsekonväxel under mikrosekunder</span><span class="sxs-lookup"><span data-stu-id="e887d-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="e887d-226">Helt deterministiskt oavsett antalet trådar</span><span class="sxs-lookup"><span data-stu-id="e887d-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="e887d-227">Prioritetsbaserad, helt förebyggande schemaläggning</span><span class="sxs-lookup"><span data-stu-id="e887d-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="e887d-228">32 standardprioritetsnivåer, valfritt upp till 1 024 nivåer</span><span class="sxs-lookup"><span data-stu-id="e887d-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="e887d-229">Schemaläggning av schemaläggning inom prioritetsnivå (FIFO)</span><span class="sxs-lookup"><span data-stu-id="e887d-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="e887d-230">Teknik för tröskelvärde för avbrott</span><span class="sxs-lookup"><span data-stu-id="e887d-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="e887d-231">Valfria timertjänster, inklusive:</span><span class="sxs-lookup"><span data-stu-id="e887d-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="e887d-232">Valfri tidssegment per tråd</span><span class="sxs-lookup"><span data-stu-id="e887d-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="e887d-233">Valfri tidsgräns för all blockering</span><span class="sxs-lookup"><span data-stu-id="e887d-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="e887d-234">API:er kräver avbrott i maskinvarutimern</span><span class="sxs-lookup"><span data-stu-id="e887d-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="e887d-235">Körningsprofilering</span><span class="sxs-lookup"><span data-stu-id="e887d-235">Execution profiling</span></span>
* <span data-ttu-id="e887d-236">Spårning på systemnivå</span><span class="sxs-lookup"><span data-stu-id="e887d-236">System-level Trace</span></span>
* <span data-ttu-id="e887d-237">Säkerhet certifierad enligt många standarder</span><span class="sxs-lookup"><span data-stu-id="e887d-237">Safety certified to many standards</span></span>

## <a name="threadx-footprint"></a><span data-ttu-id="e887d-238">ThreadX-fotavtryck</span><span class="sxs-lookup"><span data-stu-id="e887d-238">ThreadX footprint</span></span>

<span data-ttu-id="e887d-239">Azure RTOS ThreadX kräver ett mycket litet 2 KB-instruktionsområde och 1 kB RAM-minne för det minimala fotavtrycket.</span><span class="sxs-lookup"><span data-stu-id="e887d-239">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="e887d-240">Detta beror till stor del på dess picokernel utan lager™ arkitektur och automatisk skalning.</span><span class="sxs-lookup"><span data-stu-id="e887d-240">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="e887d-241">Automatisk skalning innebär att endast de tjänster (och stödinfrastruktur) som används av programmet ingår i den slutliga avbildningen vid länktiden.</span><span class="sxs-lookup"><span data-stu-id="e887d-241">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="e887d-242">Här är några vanliga Azure RTOS för ThreadX-storlek.</span><span class="sxs-lookup"><span data-stu-id="e887d-242">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="e887d-243">Azure RTOS ThreadX-tjänsten</span><span class="sxs-lookup"><span data-stu-id="e887d-243">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="e887d-244">Normal storlek i byte</span><span class="sxs-lookup"><span data-stu-id="e887d-244">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="e887d-245">Kärntjänster (Kräv)</span><span class="sxs-lookup"><span data-stu-id="e887d-245">Core Services (Require)</span></span> |<span data-ttu-id="e887d-246">2 000</span><span class="sxs-lookup"><span data-stu-id="e887d-246">2,000</span></span>  |
|<span data-ttu-id="e887d-247">Queue Services</span><span class="sxs-lookup"><span data-stu-id="e887d-247">Queue Services</span></span>  |<span data-ttu-id="e887d-248">900</span><span class="sxs-lookup"><span data-stu-id="e887d-248">900</span></span>  |
|<span data-ttu-id="e887d-249">Event Flag Services</span><span class="sxs-lookup"><span data-stu-id="e887d-249">Event Flag Services</span></span>  |<span data-ttu-id="e887d-250">900</span><span class="sxs-lookup"><span data-stu-id="e887d-250">900</span></span>  |
|<span data-ttu-id="e887d-251">Semaphore Services</span><span class="sxs-lookup"><span data-stu-id="e887d-251">Semaphore Services</span></span>  |<span data-ttu-id="e887d-252">450</span><span class="sxs-lookup"><span data-stu-id="e887d-252">450</span></span>  |
|<span data-ttu-id="e887d-253">Mutex-tjänster</span><span class="sxs-lookup"><span data-stu-id="e887d-253">Mutex Services</span></span>  |<span data-ttu-id="e887d-254">1 200</span><span class="sxs-lookup"><span data-stu-id="e887d-254">1,200</span></span>  |
|<span data-ttu-id="e887d-255">Block Memory Services</span><span class="sxs-lookup"><span data-stu-id="e887d-255">Block Memory Services</span></span>  |<span data-ttu-id="e887d-256">550</span><span class="sxs-lookup"><span data-stu-id="e887d-256">550</span></span>  |
|<span data-ttu-id="e887d-257">Byte Memory Services</span><span class="sxs-lookup"><span data-stu-id="e887d-257">Byte Memory Services</span></span>  |<span data-ttu-id="e887d-258">900</span><span class="sxs-lookup"><span data-stu-id="e887d-258">900</span></span>  |

## <a name="threadx-execution-speed"></a><span data-ttu-id="e887d-259">Körningshastighet för ThreadX</span><span class="sxs-lookup"><span data-stu-id="e887d-259">ThreadX execution speed</span></span>

<span data-ttu-id="e887d-260">Azure RTOS ThreadX uppnår en kontextväxel på under mikrosekunder på de flesta populära processorer och är betydligt snabbare totalt än andra kommersiella RTOS:er.</span><span class="sxs-lookup"><span data-stu-id="e887d-260">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="e887d-261">Förutom att vara snabb är Azure RTOS ThreadX också mycket deterministiskt.</span><span class="sxs-lookup"><span data-stu-id="e887d-261">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="e887d-262">Det ger samma snabba prestanda oavsett om det finns 200 trådar redo eller bara en.</span><span class="sxs-lookup"><span data-stu-id="e887d-262">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="e887d-263">Här är några vanliga prestandaegenskaper för Azure RTOS ThreadX:</span><span class="sxs-lookup"><span data-stu-id="e887d-263">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="e887d-264">Snabb start: Azure RTOS ThreadX startar på mindre än 120 cykler.</span><span class="sxs-lookup"><span data-stu-id="e887d-264">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="e887d-265">Valfri borttagning av grundläggande felkontroll: Grundläggande Azure RTOS ThreadX-felkontroll kan hoppas över vid kompileringen.</span><span class="sxs-lookup"><span data-stu-id="e887d-265">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="e887d-266">Detta kan vara användbart när programkoden har verifierats och inte längre kräver felkontroll på varje parameter.</span><span class="sxs-lookup"><span data-stu-id="e887d-266">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="e887d-267">Observera att detta kan göras på en kompileringsenhet i stället för i hela systemet.</span><span class="sxs-lookup"><span data-stu-id="e887d-267">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="e887d-268">Picokernel™ Design: Tjänsterna är inte skiktade på varandra, vilket eliminerar onödigt arbete med funktionsanrop.</span><span class="sxs-lookup"><span data-stu-id="e887d-268">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="e887d-269">\*Optimerad avbrottsbearbetning: Endast tillfälligt register sparas/återställs vid ISR-inmatning/-avslut, om inte avslut krävs.</span><span class="sxs-lookup"><span data-stu-id="e887d-269">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="e887d-270">Optimerad API-bearbetning:</span><span class="sxs-lookup"><span data-stu-id="e887d-270">Optimized API Processing:</span></span>

    |<span data-ttu-id="e887d-271">Azure RTOS ThreadX-tjänsten</span><span class="sxs-lookup"><span data-stu-id="e887d-271">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="e887d-272">Servicetid i mikrosekunder\*</span><span class="sxs-lookup"><span data-stu-id="e887d-272">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="e887d-273">Tråd pausa</span><span class="sxs-lookup"><span data-stu-id="e887d-273">Thread Suspend</span></span>  |<span data-ttu-id="e887d-274">0,6</span><span class="sxs-lookup"><span data-stu-id="e887d-274">0.6</span></span>  |
    |<span data-ttu-id="e887d-275">Tråd-RESUME</span><span class="sxs-lookup"><span data-stu-id="e887d-275">Thread Resume</span></span>  |<span data-ttu-id="e887d-276">0,6</span><span class="sxs-lookup"><span data-stu-id="e887d-276">0.6</span></span>  |
    |<span data-ttu-id="e887d-277">Skicka kö</span><span class="sxs-lookup"><span data-stu-id="e887d-277">Queue Send</span></span>  |<span data-ttu-id="e887d-278">0.3</span><span class="sxs-lookup"><span data-stu-id="e887d-278">0.3</span></span>  |
    |<span data-ttu-id="e887d-279">Kö ta emot</span><span class="sxs-lookup"><span data-stu-id="e887d-279">Queue Receive</span></span>  |<span data-ttu-id="e887d-280">0.3</span><span class="sxs-lookup"><span data-stu-id="e887d-280">0.3</span></span>  |
    |<span data-ttu-id="e887d-281">Hämta Semaphore</span><span class="sxs-lookup"><span data-stu-id="e887d-281">Get Semaphore</span></span>  |<span data-ttu-id="e887d-282">0,2</span><span class="sxs-lookup"><span data-stu-id="e887d-282">0.2</span></span>  |
    |<span data-ttu-id="e887d-283">Placera Semaphore</span><span class="sxs-lookup"><span data-stu-id="e887d-283">Put Semaphore</span></span>  |<span data-ttu-id="e887d-284">0,2</span><span class="sxs-lookup"><span data-stu-id="e887d-284">0.2</span></span>  |
    |<span data-ttu-id="e887d-285">Kontextväxel</span><span class="sxs-lookup"><span data-stu-id="e887d-285">Context Switch</span></span>  |<span data-ttu-id="e887d-286">0,4</span><span class="sxs-lookup"><span data-stu-id="e887d-286">0.4</span></span>  |
    |<span data-ttu-id="e887d-287">Avbrottssvar</span><span class="sxs-lookup"><span data-stu-id="e887d-287">Interrupt Response</span></span>  |<span data-ttu-id="e887d-288">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="e887d-288">0.0 – 0.6</span></span>  |

    <span data-ttu-id="e887d-289">\**Prestandasiffror baserade på en typisk processor som körs på 200 MHz.*</span><span class="sxs-lookup"><span data-stu-id="e887d-289">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="e887d-290">Avancerad teknik</span><span class="sxs-lookup"><span data-stu-id="e887d-290">Advanced technology</span></span>

<span data-ttu-id="e887d-291">Azure RTOS ThreadX är avancerad teknik vars viktigaste funktion är schemaläggning före avbrottströskel.</span><span class="sxs-lookup"><span data-stu-id="e887d-291">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="e887d-292">Den här funktionen är unik Azure RTOS ThreadX och har varit föremål för omfattande akademisk forskning.</span><span class="sxs-lookup"><span data-stu-id="e887d-292">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="e887d-293">Se till exempel [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), av Yun Wang, Juliaia University och Manas Saksena, University of Dallas.</span><span class="sxs-lookup"><span data-stu-id="e887d-293">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="e887d-294">Överväg funktionerna i Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e887d-294">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="e887d-295">Kompletta och omfattande multitasking-anläggningar</span><span class="sxs-lookup"><span data-stu-id="e887d-295">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="e887d-296">Trådar, programtimerar, meddelandeköer, räkna semaforer, mutexer, händelseflaggor, block- och byteminnespooler</span><span class="sxs-lookup"><span data-stu-id="e887d-296">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="e887d-297">Priority-Based förebyggande schemaläggning</span><span class="sxs-lookup"><span data-stu-id="e887d-297">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="e887d-298">Prioritetsflexibilitet – upp till 1 024 prioritetsnivåer</span><span class="sxs-lookup"><span data-stu-id="e887d-298">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="e887d-299">Schemaläggning av schemaläggning</span><span class="sxs-lookup"><span data-stu-id="e887d-299">Cooperative Scheduling</span></span>
* <span data-ttu-id="e887d-300">Preemption-Threshold™ – unikt för Azure RTOS ThreadX, hjälper till att minska kontextbyten och bidra till att garantera schedulability (per akademisk forskning)</span><span class="sxs-lookup"><span data-stu-id="e887d-300">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="e887d-301">Minnesskydd via Azure RTOS ThreadX-MODULER</span><span class="sxs-lookup"><span data-stu-id="e887d-301">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="e887d-302">Helt deterministisk</span><span class="sxs-lookup"><span data-stu-id="e887d-302">Fully Deterministic</span></span>
* <span data-ttu-id="e887d-303">Händelsespårning – samla in de senaste system-/programhändelserna </span><span class="sxs-lookup"><span data-stu-id="e887d-303">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="e887d-304">Event Chaining™ – Registrera en programspecifik "meddela"-återanropsfunktion för varje Azure RTOS ThreadX-kommunikations- eller synkroniseringsobjekt</span><span class="sxs-lookup"><span data-stu-id="e887d-304">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="e887d-305">Azure RTOS ThreadX-MODULER med valfritt minnesskydd</span><span class="sxs-lookup"><span data-stu-id="e887d-305">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="e887d-306">Run-Time prestandamått</span><span class="sxs-lookup"><span data-stu-id="e887d-306">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="e887d-307">Antal trådantaganden</span><span class="sxs-lookup"><span data-stu-id="e887d-307">Number of thread resumptions</span></span>
  * <span data-ttu-id="e887d-308">Antal tråduppstängningar</span><span class="sxs-lookup"><span data-stu-id="e887d-308">Number of thread suspensions</span></span>
  * <span data-ttu-id="e887d-309">Antal begärda tråd-preemptions</span><span class="sxs-lookup"><span data-stu-id="e887d-309">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="e887d-310">Antal asynkrona trådavbrottsavbrott</span><span class="sxs-lookup"><span data-stu-id="e887d-310">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="e887d-311">Antal trådprioritetsinversioner</span><span class="sxs-lookup"><span data-stu-id="e887d-311">Number of thread priority inversions</span></span>
  * <span data-ttu-id="e887d-312">Antal trådrelineringar</span><span class="sxs-lookup"><span data-stu-id="e887d-312">Number of thread relinquishes</span></span>
* <span data-ttu-id="e887d-313">Execution Profile Kit (EPK)</span><span class="sxs-lookup"><span data-stu-id="e887d-313">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="e887d-314">Separat avbrottsstack</span><span class="sxs-lookup"><span data-stu-id="e887d-314">Separate Interrupt Stack</span></span>
* <span data-ttu-id="e887d-315">Run-Time Stack-analys</span><span class="sxs-lookup"><span data-stu-id="e887d-315">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="e887d-316">Optimerad avbrottsbearbetning av timer</span><span class="sxs-lookup"><span data-stu-id="e887d-316">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="e887d-317">Stöd för flera kärnor (AMP & SMP)</span><span class="sxs-lookup"><span data-stu-id="e887d-317">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="e887d-318">Standard Azure RTOS ThreadX används ofta på ett asymmetriskt sätt med flera processer (AMP), där en separat kopia av Azure RTOS ThreadX och programmet (eller Linux) körs på varje kärna och kommunicerar med varandra via delat minne eller en kommunikationsmekanism mellan processorer som OpenAMP (Azure RTOS ThreadX stöder OpenAMP).</span><span class="sxs-lookup"><span data-stu-id="e887d-318">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="e887d-319">Det här är den mest typiska konfigurationen med Azure RTOS ThreadX och kan vara det mest effektiva om programmet effektivt kan läsa in processorerna.</span><span class="sxs-lookup"><span data-stu-id="e887d-319">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="e887d-320">För miljöer där inläsningen av processorerna är mycket dynamisk Azure RTOS ThreadX Symetric Multiprocessing (SMP) tillgänglig för följande processorfamiljer:</span><span class="sxs-lookup"><span data-stu-id="e887d-320">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="e887d-321">ARM-Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="e887d-321">ARM Cortex-Ax</span></span>
* <span data-ttu-id="e887d-322">ARM-Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="e887d-322">ARM Cortex-Rx</span></span>
* <span data-ttu-id="e887d-323">ARM Cortex-A5x 64-bitars</span><span class="sxs-lookup"><span data-stu-id="e887d-323">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="e887d-324">MIPS 34K, 1004K och interAptiv</span><span class="sxs-lookup"><span data-stu-id="e887d-324">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="e887d-325">PowerPC</span><span class="sxs-lookup"><span data-stu-id="e887d-325">PowerPC</span></span>
* <span data-ttu-id="e887d-326">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="e887d-326">Synopsys ARC HS</span></span>
* <span data-ttu-id="e887d-327">x86</span><span class="sxs-lookup"><span data-stu-id="e887d-327">x86</span></span>

<span data-ttu-id="e887d-328">Azure RTOS ThreadX SMP utför dynamisk belastningsutjämning över *n* processorer och tillåter att alla Azure RTOS ThreadX-resurser (köer, semaforer, händelseflaggor, minnespooler osv.) kan nås av alla trådar på valfri kärna.</span><span class="sxs-lookup"><span data-stu-id="e887d-328">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="e887d-329">Azure RTOS ThreadX SMP aktiverar det fullständiga Azure RTOS ThreadX-API:et på alla kärnor och introducerar följande nya API:er som gäller för SMP-åtgärder:</span><span class="sxs-lookup"><span data-stu-id="e887d-329">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="e887d-330">Minnesskydd via Azure RTOS ThreadX-moduler</span><span class="sxs-lookup"><span data-stu-id="e887d-330">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="e887d-331">Med en tilläggsprodukt som kallas Azure RTOS ThreadX MODULES kan en eller flera programtrådar paketeras i en "Modul" som kan läsas in dynamiskt och köras (eller köras på plats) på målet.</span><span class="sxs-lookup"><span data-stu-id="e887d-331">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="e887d-332">Moduler möjliggör fältuppgradering, felkorrigeringar och programpartitionering så att stora program endast kan uppta det minne som behövs av aktiva trådar.</span><span class="sxs-lookup"><span data-stu-id="e887d-332">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="e887d-333">Moduler har också ett helt separat adressutrymme från Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e887d-333">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="e887d-334">Detta gör Azure RTOS ThreadX kan placera minnesskydd (via MPU eller MMU) runt modulen så att oavsiktlig åtkomst utanför modulen inte kan skada någon annan programvarukomponent.</span><span class="sxs-lookup"><span data-stu-id="e887d-334">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="e887d-335">MISRA-kompatibel</span><span class="sxs-lookup"><span data-stu-id="e887d-335">MISRA compliant</span></span>

<span data-ttu-id="e887d-336">Azure RTOS ThreadX och Azure RTOS ThreadX SMP-källkoden är kompatibel med MISRA-C:2004 och MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="e887d-336">Azure RTOS ThreadX and Azure RTOS ThreadX SMP source code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="e887d-337">MISRA C är en uppsättning programmeringsriktlinjer för kritiska system som använder programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="e887d-337">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="e887d-338">De ursprungliga riktlinjerna för MISRA C var främst avsedda för fordonstillämpningar. MEN MISRA C är nu allmänt känt som tillämpligt för alla säkerhetskritiska program.</span><span class="sxs-lookup"><span data-stu-id="e887d-338">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="e887d-339">Azure RTOS ThreadX är kompatibel med alla obligatoriska och obligatoriska regler för MISRA-C:2004 och MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="e887d-339">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Felcertifiering":::

## <a name="supports-most-popular-tools"></a><span data-ttu-id="e887d-341">Stöder de populäraste verktygen</span><span class="sxs-lookup"><span data-stu-id="e887d-341">Supports most popular tools</span></span>

<span data-ttu-id="e887d-342">Azure RTOS ThreadX har stöd för de flesta populära inbäddade utvecklingsverktyg, inklusive IAR:s Embedded Workbench™, som även har den mest omfattande Azure RTOS ThreadX-kernelmedvetenhet.</span><span class="sxs-lookup"><span data-stu-id="e887d-342">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="e887d-343">Ytterligare verktygsintegrering omfattar GNU (GCC), ARM DS-5/uVision®, Green Universal MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterlt TRACE32®, TI Code-Composer Studio, CrossCore och alla analoga enheter.</span><span class="sxs-lookup"><span data-stu-id="e887d-343">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="e887d-344">Anpassningslager för ThreadX</span><span class="sxs-lookup"><span data-stu-id="e887d-344">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="e887d-345">Azure RTOS ThreadX är ett avancerat realtidsoperativsystem (RTOS) som är särskilt utformat för djupt inbäddade program.</span><span class="sxs-lookup"><span data-stu-id="e887d-345">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="e887d-346">För att underlätta programmigrering till Auzre RTOS tillhandahåller ThreadX [anpassningslager](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) för olika äldre RTOS-API:er (FreeRTOS, POSIX, OSEK osv.)</span><span class="sxs-lookup"><span data-stu-id="e887d-346">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
