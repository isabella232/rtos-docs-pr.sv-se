---
title: Kapitel 6 – demonstrations system för Azure återställnings tider ThreadX
description: Det här kapitlet innehåller en beskrivning av demonstrations systemet som levereras med alla Azure återställnings tider ThreadX-processor support paket.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825452"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="d5bd5-103">Kapitel 6 – demonstrations system för Azure återställnings tider ThreadX</span><span class="sxs-lookup"><span data-stu-id="d5bd5-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="d5bd5-104">Det här kapitlet innehåller en beskrivning av demonstrations systemet som levereras med alla Azure återställnings tider ThreadX-processor support paket.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="d5bd5-105">Översikt</span><span class="sxs-lookup"><span data-stu-id="d5bd5-105">Overview</span></span>

<span data-ttu-id="d5bd5-106">Varje ThreadX produkt distribution innehåller ett demonstrations system som körs på alla mikroprocessorer som stöds.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="d5bd5-107">Det här exempel systemet definieras i distributions filen ***demo_threadx. c*** och är utformat för att illustrera hur ThreadX används i en inbäddad flertrådstestning-miljö.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="d5bd5-108">Demonstrationen består av initiering, åtta trådar, en byte-pool, en blockerande pool, en kö, en semafor, en mutex och en grupp med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="d5bd5-109">*Med undantag för trådens stack storlek är demonstrations programmet identiskt på alla ThreadX-processorer som stöds.*</span><span class="sxs-lookup"><span data-stu-id="d5bd5-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="d5bd5-110">Den fullständiga listan över ***demo_threadx. c***, inklusive rad numren som refereras till i resten av det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="d5bd5-111">Tillämpnings definition</span><span class="sxs-lookup"><span data-stu-id="d5bd5-111">Application Define</span></span>

<span data-ttu-id="d5bd5-112">Funktionen ***tx_application_define*** körs när den grundläggande ThreadX har initierats.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="d5bd5-113">Den ansvarar för att konfigurera alla de första system resurserna, inklusive trådar, köer, semaforer, mutexer, händelse flaggor och lagringspooler.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="d5bd5-114">Demonstrations systemet \***tx_application_define** _ (_line numren 60-164 \*) skapar demonstrations objekt i följande ordning:</span><span class="sxs-lookup"><span data-stu-id="d5bd5-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="d5bd5-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-115">byte_pool_0</span></span>
- <span data-ttu-id="d5bd5-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-116">thread_0</span></span>
- <span data-ttu-id="d5bd5-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="d5bd5-117">thread_1</span></span>
- <span data-ttu-id="d5bd5-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="d5bd5-118">thread_2</span></span>
- <span data-ttu-id="d5bd5-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="d5bd5-119">thread_3</span></span>
- <span data-ttu-id="d5bd5-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="d5bd5-120">thread_4</span></span>
- <span data-ttu-id="d5bd5-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="d5bd5-121">thread_5</span></span>
- <span data-ttu-id="d5bd5-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="d5bd5-122">thread_6</span></span>
- <span data-ttu-id="d5bd5-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="d5bd5-123">thread_7</span></span>
- <span data-ttu-id="d5bd5-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-124">queue_0</span></span>
- <span data-ttu-id="d5bd5-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-125">semaphore_0</span></span>
- <span data-ttu-id="d5bd5-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-126">event_flags_0</span></span>
- <span data-ttu-id="d5bd5-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-127">mutex_0</span></span>
- <span data-ttu-id="d5bd5-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-128">block_pool_0</span></span>

<span data-ttu-id="d5bd5-129">Demonstrations systemet skapar inga andra ytterligare ThreadX-objekt.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="d5bd5-130">Ett faktiskt program kan dock skapa system objekt under körningen i för att köra trådar.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="d5bd5-131">Första körning</span><span class="sxs-lookup"><span data-stu-id="d5bd5-131">Initial Execution</span></span>

<span data-ttu-id="d5bd5-132">Alla trådar skapas med alternativet **TX_AUTO_START** .</span><span class="sxs-lookup"><span data-stu-id="d5bd5-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="d5bd5-133">Detta gör att de ursprungligen kan köras.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="d5bd5-134">När ***tx_application_define*** har slutförts överförs kontrollen till thread Scheduler och därifrån till varje enskild tråd.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="d5bd5-135">Den ordning som trådarna körs på bestäms av deras prioritet och i vilken ordning de skapades.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="d5bd5-136">I demonstrations systemet körs ***thread_0*** först eftersom det har högst prioritet (*det skapades med prioritet 1*).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="d5bd5-137">När ***thread_0*** har pausats körs ***thread_5*** följt av körningen av ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _* _thread_7_\* \*, \***thread_1**_ och slutligen _ *_thread_2_* \*.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="d5bd5-138">*Även om **thread_3** och **thread_4** har samma prioritet (båda har skapats med prioritet 8) börjar **thread_3** köras först. Detta beror på att **thread_3** skapats och blivit klart innan **thread_4**. Trådar med samma prioritet körs på en FIFO-miljö.*</span><span class="sxs-lookup"><span data-stu-id="d5bd5-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="d5bd5-139">Tråd 0</span><span class="sxs-lookup"><span data-stu-id="d5bd5-139">Thread 0</span></span>

<span data-ttu-id="d5bd5-140">Funktionen ***thread_0_entry*** markerar trådens start punkt *(rader 167-190*).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="d5bd5-141">***Thread_0*** är den första tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="d5bd5-142">Bearbetningen är enkel: den ökar räknaren, väntar på 10 timer-Tick, ställer in en händelse flagga för att väcka ***thread_5*** och upprepar sedan sekvensen.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="d5bd5-143">***Thread_0*** är den högsta prioritets tråden i systemet.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="d5bd5-144">När den begärda vilo tiden går ut, kommer det att finnas någon annan körnings tråd i demonstrationen.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="d5bd5-145">Tråd 1</span><span class="sxs-lookup"><span data-stu-id="d5bd5-145">Thread 1</span></span>

<span data-ttu-id="d5bd5-146">Funktionen \***thread_1_entry** _ anger start punkten för tråden _(rader 193-216 *). ***Thread_1*** är den andra-till-sista-tråden i demonstrations systemet som ska köras. Bearbetningen består i att öka räknarens räknare, skicka ett meddelande till ***thread_2*** (* till och med \* ***queue_0***) och upprepa sekvensen. Observera att \***thread_1**_ pausas när _*_queue_0_*_ blir full (_line 207 \*).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="d5bd5-147">Tråd 2</span><span class="sxs-lookup"><span data-stu-id="d5bd5-147">Thread 2</span></span>

<span data-ttu-id="d5bd5-148">Funktionen ***thread_2_entry*** markerar trådens start punkt *(rader 219-243*).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="d5bd5-149">***Thread_2*** är den sista tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="d5bd5-150">Bearbetningen består av att öka räknaren, hämta ett meddelande från ***thread_1*** (via ***queue_0***) och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="d5bd5-151">Observera att ***thread_2** _ pausas när _*_queue_0_\*_ blir tomt (_line 233 \*).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="d5bd5-152">Även om ***thread_1** _ och _ *_thread_2_** delar den lägsta prioriteten i demonstrations systemet (\* prioritet 16 \*), *trådarna 3 och 4*</span><span class="sxs-lookup"><span data-stu-id="d5bd5-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="d5bd5-153">är också de enda trådar som är redo att köras i den här tiden.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="d5bd5-154">De är också de enda trådarna som skapas med tids segmentering (*raderna 87 och 93*).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="d5bd5-155">Varje tråd kan köras med högst 4 timer-Tick innan den andra tråden körs.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="d5bd5-156">Trådar 3 och 4</span><span class="sxs-lookup"><span data-stu-id="d5bd5-156">Threads 3 and 4</span></span>

<span data-ttu-id="d5bd5-157">Funktionen ***thread_3_and_4_entry*** markerar start punkten för både ***thread_3** _ och _ *_thread_4_** (rader 246-280).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="d5bd5-158">Båda trådarna har prioriteten 8, vilket gör dem till de tredje och fjärde trådarna i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="d5bd5-159">Bearbetningen för varje tråd är detsamma: att öka räknarens räknare, Hämta ***semaphore_0***, vilande för 2 timer-Tick, släppa ***semaphore_0*** och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="d5bd5-160">Observera att varje tråd pausas när ***semaphore_0*** inte är tillgängligt (rad 264).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="d5bd5-161">Båda trådarna använder också samma funktion för sin huvudsakliga bearbetning.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="d5bd5-162">Detta ger inga problem eftersom de båda har sin egen unika stack, och C är naturlig reentrant.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="d5bd5-163">Varje tråd avgör vilken som är av genom att undersöka trådens indataparametrar (rad 258), som är en inställning när de skapas (rader 102 och 109).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="d5bd5-164">*Det är också rimligt att du får den aktuella tråd punkten under tråd körning och jämför den med kontroll blockets adress för att fastställa tråd identitet.*</span><span class="sxs-lookup"><span data-stu-id="d5bd5-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="d5bd5-165">Tråd 5</span><span class="sxs-lookup"><span data-stu-id="d5bd5-165">Thread 5</span></span>

<span data-ttu-id="d5bd5-166">Funktionen ***thread_5_entry*** markerar trådens start punkt (rader 283-305).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="d5bd5-167">***Thread_5*** är den andra tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="d5bd5-168">Bearbetningen består av en stegvis ökning av räknaren, hämtar en händelse flagga från ***thread_0*** (via ***event_flags_0***) och upprepar sekvensen.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="d5bd5-169">Observera att ***thread_5*** pausas när händelse flaggan i ***event_flags_0*** inte är tillgänglig (rad 298).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="d5bd5-170">Trådar 6 och 7</span><span class="sxs-lookup"><span data-stu-id="d5bd5-170">Threads 6 and 7</span></span>

<span data-ttu-id="d5bd5-171">Funktionen ***thread_6_and_7_entry*** markerar start punkten för både ***thread_6** _ och _ *_thread_7_** (rader 307-358).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="d5bd5-172">Båda trådarna har prioriteten 8, vilket gör dem till de femte och sjätte trådarna i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="d5bd5-173">Bearbetningen för varje tråd är detsamma: att öka räknaren, få ***mutex_0*** två gånger, i vilo läge för 2 timer-Tick, släppa ***mutex_0*** två gånger och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="d5bd5-174">Observera att varje tråd pausas när ***mutex_0*** inte är tillgängligt (rad 325).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="d5bd5-175">Båda trådarna använder också samma funktion för sin huvudsakliga bearbetning.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="d5bd5-176">Detta ger inga problem eftersom de båda har sin egen unika stack, och C är naturlig reentrant.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="d5bd5-177">Varje tråd avgör vilken som är av genom att undersöka trådens indataparametrar (rad 319), som är en inställning när de skapas (rader 126 och 133).</span><span class="sxs-lookup"><span data-stu-id="d5bd5-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="d5bd5-178">Att iaktta demonstrationen</span><span class="sxs-lookup"><span data-stu-id="d5bd5-178">Observing the Demonstration</span></span>

<span data-ttu-id="d5bd5-179">Varje demonstrations tråd ökar sin egen unika räknare.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="d5bd5-180">Följande räknare kan undersökas för att kontrol lera demoets åtgärd:</span><span class="sxs-lookup"><span data-stu-id="d5bd5-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="d5bd5-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-181">thread_0_counter</span></span>
- <span data-ttu-id="d5bd5-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-182">thread_1_counter</span></span>
- <span data-ttu-id="d5bd5-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-183">thread_2_counter</span></span>
- <span data-ttu-id="d5bd5-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-184">thread_3_counter</span></span>
- <span data-ttu-id="d5bd5-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-185">thread_4_counter</span></span>
- <span data-ttu-id="d5bd5-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-186">thread_5_counter</span></span>
- <span data-ttu-id="d5bd5-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-187">thread_6_counter</span></span>
- <span data-ttu-id="d5bd5-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="d5bd5-188">thread_7_counter</span></span>

<span data-ttu-id="d5bd5-189">Var och en av dessa räknare bör fortsätta att öka när demonstrationen körs, med ***thread_1_counter** _ och _ *_thread_2_counter_** ökar med den snabbaste hastigheten.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="d5bd5-190">Distributions fil: demo_threadx. c</span><span class="sxs-lookup"><span data-stu-id="d5bd5-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="d5bd5-191">I det här avsnittet visas en fullständig lista över ***demo_threadx. c***, inklusive de rad nummer som refereras till i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="d5bd5-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
void thread_0_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {

        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}


void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}


void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;


    /* This function is executed from thread 3 and thread 4. As the loop
    below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;


    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
            &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
        below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
