---
title: Kapitel 6 – demonstrations system för Azure återställnings tider ThreadX SMP
description: Det här kapitlet innehåller en beskrivning av demonstrations systemet som levereras med alla support paket för Azure återställnings tider ThreadX SMP-processor.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b94dad3c5ec94befd57200049138b184461a9b55
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827993"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx-smp"></a><span data-ttu-id="10670-103">Kapitel 6 – demonstrations system för Azure återställnings tider ThreadX SMP</span><span class="sxs-lookup"><span data-stu-id="10670-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX SMP</span></span>

<span data-ttu-id="10670-104">Det här kapitlet innehåller en beskrivning av demonstrations systemet som levereras med alla support paket för Azure återställnings tider ThreadX SMP-processor.</span><span class="sxs-lookup"><span data-stu-id="10670-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX SMP processor support packages.</span></span> 

## <a name="overview"></a><span data-ttu-id="10670-105">Översikt</span><span class="sxs-lookup"><span data-stu-id="10670-105">Overview</span></span>

<span data-ttu-id="10670-106">Varje ThreadX SMP produkt distribution innehåller ett demonstrations system som körs på alla mikroprocessorer som stöds.</span><span class="sxs-lookup"><span data-stu-id="10670-106">Each ThreadX SMP product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="10670-107">Det här exempel systemet definieras i distributions filen ***demo_threadx. c*** och är utformat för att illustrera hur ThreadX SMP används i en inbäddad flertrådstestning-miljö.</span><span class="sxs-lookup"><span data-stu-id="10670-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX SMP is used in an embedded multithread environment.</span></span> <span data-ttu-id="10670-108">Demonstrationen består av initiering, åtta trådar, en byte-pool, en blockerande pool, en kö, en semafor, en mutex och en grupp med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="10670-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10670-109">Med undantag för trådens stack storlek är demonstrations programmet identiskt på alla processorer som stöds av ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="10670-109">Except for the thread’s stack size, the demonstration application is identical on all ThreadX SMP supported processors.</span></span>

<span data-ttu-id="10670-110">Den fullständiga listan över ***demo_threadx. c***, inklusive de rad nummer som refereras till i resten av det här kapitlet, visas på sidan 324 och följande.</span><span class="sxs-lookup"><span data-stu-id="10670-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter, is displayed on page 324 and following.</span></span>

## <a name="application-define"></a><span data-ttu-id="10670-111">Tillämpnings definition</span><span class="sxs-lookup"><span data-stu-id="10670-111">Application Define</span></span>

<span data-ttu-id="10670-112">Funktionen ***tx_application_define*** körs när den grundläggande ThreadX SMP-initieringen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="10670-112">The ***tx_application_define*** function executes after the basic ThreadX SMP initialization is complete.</span></span> <span data-ttu-id="10670-113">Den ansvarar för att konfigurera alla de första system resurserna, inklusive trådar, köer, semaforer, mutexer, händelse flaggor och lagringspooler.</span><span class="sxs-lookup"><span data-stu-id="10670-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="10670-114">Demonstrations systemet \***tx_application_define** _ (_line numren 60-164 \*) skapar demonstrations objekt i följande ordning:</span><span class="sxs-lookup"><span data-stu-id="10670-114">The demonstration system’s ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

```C
byte_pool_0
thread_0
thread_1
thread_2
thread_3
thread_4
thread_5
thread_6
thread_7
queue_0
semaphore_0
event_flags_0
mutex_0
block_pool_0
```
<span data-ttu-id="10670-115">Demonstrations systemet skapar inga andra ytterligare ThreadX SMP-objekt.</span><span class="sxs-lookup"><span data-stu-id="10670-115">The demonstration system does not create any other additional ThreadX SMP objects.</span></span> <span data-ttu-id="10670-116">Ett faktiskt program kan dock skapa system objekt under körningen i för att köra trådar.</span><span class="sxs-lookup"><span data-stu-id="10670-116">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="10670-117">Första körning</span><span class="sxs-lookup"><span data-stu-id="10670-117">Initial Execution</span></span> 
<span data-ttu-id="10670-118">Alla trådar skapas med alternativet **TX_AUTO_START** .</span><span class="sxs-lookup"><span data-stu-id="10670-118">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="10670-119">Detta gör att de ursprungligen kan köras.</span><span class="sxs-lookup"><span data-stu-id="10670-119">This makes them initially ready for execution.</span></span> <span data-ttu-id="10670-120">När **_tx_application_define_** har slutförts överförs kontrollen till thread Scheduler och därifrån till varje enskild tråd.</span><span class="sxs-lookup"><span data-stu-id="10670-120">After **_tx_application_define_** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="10670-121">Den ordning som trådarna körs på bestäms av deras prioritet och i vilken ordning de skapades.</span><span class="sxs-lookup"><span data-stu-id="10670-121">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="10670-122">I demonstrations systemet måste \***thread_0** _ köras först eftersom det har högst prioritet (_det skapades med prioritet 1 \*). Efter \***thread_0**_ pausas _*_thread_5_*_ utförs, följt av körningen av _*_thread_3_*_, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_*_, _*_thread_1_*_ och slutligen _ *_thread_2_* \*.</span><span class="sxs-lookup"><span data-stu-id="10670-122">In the demonstration system, ***thread_0** _ executes first because it has the highest priority (_it was created with a priority of 1*). After \***thread_0**_ suspends, _*_thread_5_*_ is executed, followed by the execution of _*_thread_3_*_, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_*_, _*_thread_1_*_, and finally _\*_thread_2_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10670-123">Även om **thread_3** och **thread_4** har samma prioritet (båda har skapats med prioritet 8) börjar **thread_3** köras först.</span><span class="sxs-lookup"><span data-stu-id="10670-123">Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first.</span></span> <span data-ttu-id="10670-124">Detta beror på att **thread_3** skapats och blivit klart innan **thread_4**.</span><span class="sxs-lookup"><span data-stu-id="10670-124">This is because **thread_3** was created and became ready before **thread_4**.</span></span> <span data-ttu-id="10670-125">Trådar med samma prioritet körs på en FIFO-miljö.</span><span class="sxs-lookup"><span data-stu-id="10670-125">Threads of equal priority execute in a FIFO fashion.</span></span>

## <a name="thread-0"></a><span data-ttu-id="10670-126">Tråd 0</span><span class="sxs-lookup"><span data-stu-id="10670-126">Thread 0</span></span>

<span data-ttu-id="10670-127">Funktionen \***thread_0_entry** _ anger start punkten för tråden _(raderna 167-190 \*). \***Thread_0**_ är den första tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="10670-127">The function ***thread_0_entry** _ marks the entry point of the thread _(lines 167-190*). \***Thread_0**_ is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="10670-128">Bearbetningen är enkel: den ökar räknaren, väntar på 10 timer-Tick, ställer in en händelse flagga för att väcka _ *_thread_5_* \* och upprepar sedan sekvensen.</span><span class="sxs-lookup"><span data-stu-id="10670-128">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up _\*_thread_5_\*\*, then repeats the sequence.</span></span>

<span data-ttu-id="10670-129">***Thread_0*** är den högsta prioritets tråden i systemet.</span><span class="sxs-lookup"><span data-stu-id="10670-129">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="10670-130">När den begärda vilo tiden går ut, kommer det att finnas någon annan körnings tråd i demonstrationen.</span><span class="sxs-lookup"><span data-stu-id="10670-130">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="10670-131">Tråd 1</span><span class="sxs-lookup"><span data-stu-id="10670-131">Thread 1</span></span>

<span data-ttu-id="10670-132">Funktionen \***thread_1_entry** _ anger start punkten för tråden _(raderna 193-216 \*). \***Thread_1**_ är den andra-till-sista-tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="10670-132">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216*). \***Thread_1**_ is the second-to-last thread in the demonstration system to execute.</span></span> <span data-ttu-id="10670-133">Bearbetningen består i att öka räknarens räknare, skicka ett meddelande till _*_thread_2_*_ (_till och med \* \***queue_0**_) och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="10670-133">Its processing consists of incrementing its counter, sending a message to _*_thread_2_*_ (_through\* \***queue_0**_), and repeating the sequence.</span></span> <span data-ttu-id="10670-134">Observera att _*_thread_1_*_ pausas när _*_queue_0_*_ blir full (_line 207 \*).</span><span class="sxs-lookup"><span data-stu-id="10670-134">Notice that _*_thread_1_*_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="10670-135">Tråd 2</span><span class="sxs-lookup"><span data-stu-id="10670-135">Thread 2</span></span>

<span data-ttu-id="10670-136">Funktionen \***thread_2_entry** _ anger start punkten för tråden _(raderna 219-243 \*). \***Thread_2**_ är den sista tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="10670-136">The function ***thread_2_entry** _ marks the entry point of the thread _(lines 219-243*). \***Thread_2**_ is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="10670-137">Bearbetningen består av att öka räknaren, hämta ett meddelande från _*_thread_1_*_ (via _*_queue_0_*_) och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="10670-137">Its processing consists of incrementing its counter, getting a message from _*_thread_1_*_ (through _*_queue_0_*_), and repeating the sequence.</span></span> <span data-ttu-id="10670-138">Observera att _*_thread_2_*_ pausas när _*_queue_0_*_ blir tomt (_line 233 \*).</span><span class="sxs-lookup"><span data-stu-id="10670-138">Notice that _*_thread_2_*_ suspends whenever _*_queue_0_*_ becomes empty (_line 233\*).</span></span>

<span data-ttu-id="10670-139">Även om ***thread_1** _ och _*_thread_2_\*_ delar den lägsta prioriteten i demonstrations systemet (_priority 16 *), är de även de enda trådar som är redo att köras i de flesta fall. De är också de enda trådarna som skapas med tids segmentering (* raderna 87 och 93 \*).</span><span class="sxs-lookup"><span data-stu-id="10670-139">Although ***thread_1** _ and _*_thread_2_*_ share the lowest priority in the demonstration system (_priority 16 *), they are also the only threads that are ready for execution most of the time. They are also the only threads created with time-slicing (* lines 87 and 93*).</span></span> <span data-ttu-id="10670-140">Varje tråd kan köras med högst 4 timer-Tick innan den andra tråden körs.</span><span class="sxs-lookup"><span data-stu-id="10670-140">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="10670-141">Trådar 3 och 4</span><span class="sxs-lookup"><span data-stu-id="10670-141">Threads 3 and 4</span></span>

<span data-ttu-id="10670-142">Funktionen ***thread_3_and_4_entry** _ markerar start punkten för både _*_thread_3_*_ och _*_thread_4_\*_ _(rader 246-280 \*). Båda trådarna har prioriteten 8, vilket gör dem till de tredje och fjärde trådarna i demonstrations systemet som ska köras. Bearbetningen för varje tråd är detsamma: att öka räknarens räknare, få \***semaphore_0**_, ström spar läge för 2 timer-tick, släppa _*_semaphore_0_*_ och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="10670-142">The function ***thread_3_and_4_entry** _ marks the entry point of both _*_thread_3_*_ and _*_thread_4_*_ _(lines 246-280*). Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute. The processing for each thread is the same: incrementing its counter, getting \***semaphore_0**_, sleeping for 2 timer ticks, releasing _*_semaphore_0_*_, and repeating the sequence.</span></span> <span data-ttu-id="10670-143">Observera att varje tråd pausas när _*_semaphore_0_*_ inte är tillgängligt (_line 264 \*).</span><span class="sxs-lookup"><span data-stu-id="10670-143">Notice that each thread suspends whenever _*_semaphore_0_*_ is unavailable (_line 264\*).</span></span>

<span data-ttu-id="10670-144">Båda trådarna använder också samma funktion för sin huvudsakliga bearbetning.</span><span class="sxs-lookup"><span data-stu-id="10670-144">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="10670-145">Detta ger inga problem eftersom de båda har sin egen unika stack, och C är naturlig reentrant.</span><span class="sxs-lookup"><span data-stu-id="10670-145">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="10670-146">Varje tråd avgör vilken som är av genom att undersöka trådens indataparametrar (*rad 258*), som är en inställning när de skapas (*rader 102 och 109*).</span><span class="sxs-lookup"><span data-stu-id="10670-146">Each thread determines which one it is by examination of the thread input parameter (*line 258*), which is setup when they are created (*lines 102 and 109*).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10670-147">Det är också rimligt att du får den aktuella tråd punkten under tråd körning och jämför den med kontroll blockets adress för att fastställa tråd identitet.</span><span class="sxs-lookup"><span data-stu-id="10670-147">It is also reasonable to obtain the current thread point during thread execution and compare it with the control block’s address to determine thread identity.</span></span>

## <a name="thread-5"></a><span data-ttu-id="10670-148">Tråd 5</span><span class="sxs-lookup"><span data-stu-id="10670-148">Thread 5</span></span>

<span data-ttu-id="10670-149">Funktionen \***thread_5_entry** _ anger start punkten för tråden _(raderna 283-305 \*). \***Thread_5**_ är den andra tråden i demonstrations systemet som ska köras.</span><span class="sxs-lookup"><span data-stu-id="10670-149">The function ***thread_5_entry** _ marks the entry point of the thread _(lines 283-305*). \***Thread_5**_ is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="10670-150">Bearbetningen består av en stegvis ökning av räknaren, hämtar en händelse flagga från _*_thread_0_*_ (via _*_event_flags_0_*_) och upprepar sekvensen.</span><span class="sxs-lookup"><span data-stu-id="10670-150">Its processing consists of incrementing its counter, getting an event flag from _*_thread_0_*_ (through _*_event_flags_0_*_), and repeating the sequence.</span></span> <span data-ttu-id="10670-151">Observera att _*_thread_5_*_ pausas när händelse flaggan i _*_event_flags_0_*_ inte är tillgänglig (_line 298 \*).</span><span class="sxs-lookup"><span data-stu-id="10670-151">Notice that _*_thread_5_*_ suspends whenever the event flag in _*_event_flags_0_*_ is not available (_line 298\*).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="10670-152">Trådar 6 och 7</span><span class="sxs-lookup"><span data-stu-id="10670-152">Threads 6 and 7</span></span>

<span data-ttu-id="10670-153">Funktionen ***thread_6_and_7_entry** _ markerar start punkten för både _*_thread_6_*_ och _*_thread_7_\*_ _(rader 307-358 \*). Båda trådarna har prioriteten 8, vilket gör dem till de femte och sjätte trådarna i demonstrations systemet som ska köras. Bearbetningen för varje tråd är detsamma: att öka räknaren, få \***mutex_0**_ två gånger, i vilo läge för 2 timer-tick, släppa _*_mutex_0_*_ två gånger och upprepa sekvensen.</span><span class="sxs-lookup"><span data-stu-id="10670-153">The function ***thread_6_and_7_entry** _ marks the entry point of both _*_thread_6_*_ and _*_thread_7_*_ _(lines 307-358*). Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute. The processing for each thread is the same: incrementing its counter, getting \***mutex_0**_ twice, sleeping for 2 timer ticks, releasing _*_mutex_0_*_ twice, and repeating the sequence.</span></span> <span data-ttu-id="10670-154">Observera att varje tråd pausas när _*_mutex_0_*_ inte är tillgängligt (_line 325 \*).</span><span class="sxs-lookup"><span data-stu-id="10670-154">Notice that each thread suspends whenever _*_mutex_0_*_ is unavailable (_line 325\*).</span></span>

<span data-ttu-id="10670-155">Båda trådarna använder också samma funktion för sin huvudsakliga bearbetning.</span><span class="sxs-lookup"><span data-stu-id="10670-155">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="10670-156">Detta ger inga problem eftersom de båda har sin egen unika stack, och C är naturlig reentrant.</span><span class="sxs-lookup"><span data-stu-id="10670-156">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="10670-157">Varje tråd avgör vilken som är av genom att undersöka trådens indataparametrar (*rad 319*), som är en inställning när de skapas (*rader 126 och 133*).</span><span class="sxs-lookup"><span data-stu-id="10670-157">Each thread determines which one it is by examination of the thread input parameter (*line 319*), which is setup when they are created (*lines 126 and 133*).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="10670-158">Att iaktta demonstrationen</span><span class="sxs-lookup"><span data-stu-id="10670-158">Observing the Demonstration</span></span>

<span data-ttu-id="10670-159">Varje demonstrations tråd ökar sin egen unika räknare.</span><span class="sxs-lookup"><span data-stu-id="10670-159">Each of the demonstration threads increments its own unique counter.</span></span> <span data-ttu-id="10670-160">Följande räknare kan undersökas för att kontrol lera demoets åtgärd:</span><span class="sxs-lookup"><span data-stu-id="10670-160">The following counters may be examined to check on the demo’s operation:</span></span>

```C
thread_0_counter
thread_1_counter
thread_2_counter
thread_3_counter
thread_4_counter
thread_5_counter
thread_6_counter
thread_7_counter
```

<span data-ttu-id="10670-161">Var och en av dessa räknare bör fortsätta att öka när demonstrationen körs, med ***thread_1_counter** _ och _ *_thread_2_counter_** ökar med den snabbaste hastigheten.</span><span class="sxs-lookup"><span data-stu-id="10670-161">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="10670-162">Distributions fil: demo_threadx. c</span><span class="sxs-lookup"><span data-stu-id="10670-162">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="10670-163">I det här avsnittet visas en fullständig lista över ***demo_threadx. c***, inklusive de rad nummer som refereras till i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="10670-163">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```C
000 /* This is a small demo of the high-performance ThreadX SMP kernel. It includes examples of eight
001 threads of different priorities, using a message queue, semaphore, mutex, event flags group,
002 byte pool, and block pool. */
003
004 #include "tx_api.h"
005
006 #define DEMO_STACK_SIZE         1024
007 #define DEMO_BYTE_POOL_SIZE     9120
008 #define DEMO_BLOCK_POOL_SIZE    100
009 #define DEMO_QUEUE_SIZE         100
010
011 /* Define the ThreadX SMP object control blocks...  */
012
013 TX_THREAD               thread_0;
014 TX_THREAD               thread_1;
015 TX_THREAD               thread_2;
016 TX_THREAD               thread_3;
017 TX_THREAD               thread_4;
018 TX_THREAD               thread_5;
019 TX_THREAD               thread_6;
020 TX_THREAD               thread_7;
021 TX_QUEUE                queue_0;
022 TX_SEMAPHORE            semaphore_0;
023 TX_MUTEX                mutex_0;
024 TX_EVENT_FLAGS_GROUP    event_flags_0;
025 TX_BYTE_POOL            byte_pool_0;
026 TX_BLOCK_POOL           block_pool_0;
027
028 /* Define the counters used in the demo application...  */
029
030 ULONG                    thread_0_counter;
031 ULONG                    thread_1_counter;
032 ULONG                    thread_1_messages_sent;
033 ULONG                    thread_2_counter;
034 ULONG                    thread_2_messages_received;
035 ULONG                    thread_3_counter;
036 ULONG                    thread_4_counter;
037 ULONG                    thread_5_counter;
038 ULONG                    thread_6_counter;
039 ULONG                    thread_7_counter;
040
041 /* Define thread prototypes.  */
042
043 void    thread_0_entry(ULONG thread_input);
044 void    thread_1_entry(ULONG thread_input);
045 void    thread_2_entry(ULONG thread_input);
046 void    thread_3_and_4_entry(ULONG thread_input);
047 void    thread_5_entry(ULONG thread_input);
048 void    thread_6_and_7_entry(ULONG thread_input);
049
050
051 /* Define main entry point.  */
052
053 int main()
054 {
055
056     /* Enter the ThreadX SMP kernel. */
057     tx_kernel_enter();
058 }
059
060 /* Define what the initial system looks like. */
061 void    tx_application_define(void *first_unused_memory)
062 {
063
064 CHAR    *pointer;
065
066    /* Create a byte memory pool from which to allocate the thread stacks. */
067    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
068                               DEMO_BYTE_POOL_SIZE);
069
070    /* Put system definition stuff in here, e.g., thread creates and other assorted
071       create information. */
072
073    /* Allocate the stack for thread 0. */
074    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
075
076    /* Create the main thread. */
077    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
078                               pointer, DEMO_STACK_SIZE,
079                               1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
080
081    /* Allocate the stack for thread 1. */
082    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
083
084    /* Create threads 1 and 2. These threads pass information through a ThreadX SMP
085       message queue. It is also interesting to note that these threads have a time
086       slice. */
087    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
088                              pointer, DEMO_STACK_SIZE,
089                              16, 16, 4, TX_AUTO_START);
090
091    /* Allocate the stack for thread 2. */
092    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
093    tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
094                              pointer, DEMO_STACK_SIZE,
095                              16, 16, 4, TX_AUTO_START);
096
097    /* Allocate the stack for thread 3. */
098    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
099
100    /* Create threads 3 and 4. These threads compete for a ThreadX SMP counting semaphore.
101       An interesting thing here is that both threads share the same instruction area. */
102    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
103                              pointer, DEMO_STACK_SIZE,
104                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
105
106    /* Allocate the stack for thread 4. */
107    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
108
109    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
110                              pointer, DEMO_STACK_SIZE,
111                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
112
113    /* Allocate the stack for thread 5. */
114    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
115
116    /* Create thread 5. This thread simply pends on an event flag, which will be set
117       by thread_0. */
118    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
119                              pointer, DEMO_STACK_SIZE,
120                              4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
121
122    /* Allocate the stack for thread 6. */
123    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
124
125    /* Create threads 6 and 7. These threads compete for a ThreadX SMP mutex. */
126    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
127                              pointer, DEMO_STACK_SIZE,
128                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
129
130    /* Allocate the stack for thread 7. */
131    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
132
133    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
134                              pointer, DEMO_STACK_SIZE,
135                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
136
137    /* Allocate the message queue. */
138    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);
139
140    /* Create the message queue shared by threads 1 and 2. */
141    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));
142
143    /* Create the semaphore used by threads 3 and 4. */
144    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);
145
146    /* Create the event flags group used by threads 1 and 5. */
147    tx_event_flags_create(&event_flags_0, "event flags 0");
148
149    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
150    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);
151
152    /* Allocate the memory for a small block pool. */
153    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);
154
155    /* Create a block memory pool to allocate a message buffer from. */
156    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
157                 DEMO_BLOCK_POOL_SIZE);
158
159    /* Allocate a block and release the block memory. */
160    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);
161
162    /* Release the block back to the pool. */
163    tx_block_release(pointer);
164 }
165
166    /* Define the test threads. */
167    void thread_0_entry(ULONG thread_input)
168 {
169
170 UINT status;
171
172
173    /* This thread simply sits in while-forever-sleep loop. */
174     while(1)
175    {
176
177    /* Increment the thread counter. */
178    thread_0_counter++;
179
180    /* Sleep for 10 ticks. */
181    tx_thread_sleep(10);
182
183    /* Set event flag 0 to wakeup thread 5. */
184    status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);
185
186    /* Check status. */
187    if (status != TX_SUCCESS)
188       break;
189    }
190 }
191
192
193 void    thread_1_entry(ULONG thread_input)
194 {
195
196 UINT    status;
197
198
199    /* This thread simply sends messages to a queue shared by thread 2. */
200    while(1)
201    {
202
203         /* Increment the thread counter. */
204         thread_1_counter++;
205
206         /* Send message to queue 0. */
207         status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);
208
209         /* Check completion status. */
210         if (status != TX_SUCCESS)
211            break;
212
213         /* Increment the message sent. */
214         thread_1_messages_sent++;
215    }
216 }
217
218
219 void     thread_2_entry(ULONG thread_input)
220 {
221
222 ULONG     received_message;
223 UINT      status;
224
225     /* This thread retrieves messages placed on the queue by thread 1. */
226     while(1)
227     {
228
229         /* Increment the thread counter. */
230         thread_2_counter++;
231
232         /* Retrieve a message from the queue. */
233         status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);
234
235         /* Check completion status and make sure the message is what we
236            expected. */
237         if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
238            break;
239
240         /* Otherwise, all is okay. Increment the received message count. */
241         thread_2_messages_received++;
242      }
243 }
244
245
246 void     thread_3_and_4_entry(ULONG thread_input)
247 {
248
249 UINT     status;
250
251
252     /* This function is executed from thread 3 and thread 4. As the loop
253        below shows, these function compete for ownership of semaphore_0. */
254     while(1)
255     {
256
257         /* Increment the thread counter. */
258         if (thread_input == 3)
259            thread_3_counter++;
260         else
261            thread_4_counter++;
262
263         /* Get the semaphore with suspension. */
264         status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);
265
266         /* Check status. */
267         if (status != TX_SUCCESS)
268            break;
269
270         /* Sleep for 2 ticks to hold the semaphore. */
271         tx_thread_sleep(2);
272
273         /* Release the semaphore. */
274         status = tx_semaphore_put(&semaphore_0);
275
276         /* Check status. */
277         if (status != TX_SUCCESS)
278             break;
279     }
280 }
281
282
283 void     thread_5_entry(ULONG thread_input)
284 {
285
286 UINT     status;
287 ULONG    actual_flags;
288
289
290     /* This thread simply waits for an event in a forever loop. */
291     while(1)
292     {
293
294         /* Increment the thread counter. */
295         thread_5_counter++;
296
297         /* Wait for event flag 0. */
298         status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
299                                &actual_flags, TX_WAIT_FOREVER);
300
301         /* Check status. */
302         if ((status != TX_SUCCESS) || (actual_flags != 0x1))
303            break;
304     }
305 }
306
307 void     thread_6_and_7_entry(ULONG thread_input)
308 {
309
310 UINT     status;
311
312
313     /* This function is executed from thread 6 and thread 7. As the loop
314         below shows, these function compete for ownership of mutex_0. */
315     while(1)
316     {
317
318         /* Increment the thread counter. */
319         if (thread_input == 6)
320            thread_6_counter++;
321         else
322            thread_7_counter++;
323
324         /* Get the mutex with suspension. */
325         status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);
326
327         /* Check status. */
328         if (status != TX_SUCCESS)
329            break;
330
331         /* Get the mutex again with suspension. This shows
332            that an owning thread may retrieve the mutex it
333            owns multiple times. */
334         status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);
335
336         /* Check status. */
337         if (status != TX_SUCCESS)
338             break;
339
340         /* Sleep for 2 ticks to hold the mutex. */
341         tx_thread_sleep(2);
342
343         /* Release the mutex. */
344         status = tx_mutex_put(&mutex_0);
345
346         /* Check status. */
347         if (status != TX_SUCCESS)
348            break;
349
350         /* Release the mutex again. This will actually
351            release ownership since it was obtained twice. */
352         status = tx_mutex_put(&mutex_0);
353
354         /* Check status. */
355         if (status != TX_SUCCESS)
356            break;
357     }
358 }
```