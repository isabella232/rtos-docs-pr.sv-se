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
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a>Kapitel 6 – demonstrations system för Azure återställnings tider ThreadX

Det här kapitlet innehåller en beskrivning av demonstrations systemet som levereras med alla Azure återställnings tider ThreadX-processor support paket.

## <a name="overview"></a>Översikt

Varje ThreadX produkt distribution innehåller ett demonstrations system som körs på alla mikroprocessorer som stöds.

Det här exempel systemet definieras i distributions filen ***demo_threadx. c*** och är utformat för att illustrera hur ThreadX används i en inbäddad flertrådstestning-miljö. Demonstrationen består av initiering, åtta trådar, en byte-pool, en blockerande pool, en kö, en semafor, en mutex och en grupp med händelse flaggor.

> [!NOTE]
> *Med undantag för trådens stack storlek är demonstrations programmet identiskt på alla ThreadX-processorer som stöds.*

Den fullständiga listan över ***demo_threadx. c***, inklusive rad numren som refereras till i resten av det här kapitlet.

## <a name="application-define"></a>Tillämpnings definition

Funktionen ***tx_application_define*** körs när den grundläggande ThreadX har initierats. Den ansvarar för att konfigurera alla de första system resurserna, inklusive trådar, köer, semaforer, mutexer, händelse flaggor och lagringspooler.

Demonstrations systemet ***tx_application_define** _ (_line numren 60-164 *) skapar demonstrations objekt i följande ordning:

- byte_pool_0
- thread_0
- thread_1
- thread_2
- thread_3
- thread_4
- thread_5
- thread_6
- thread_7
- queue_0
- semaphore_0
- event_flags_0
- mutex_0
- block_pool_0

Demonstrations systemet skapar inga andra ytterligare ThreadX-objekt. Ett faktiskt program kan dock skapa system objekt under körningen i för att köra trådar.

### <a name="initial-execution"></a>Första körning

Alla trådar skapas med alternativet **TX_AUTO_START** . Detta gör att de ursprungligen kan köras. När ***tx_application_define*** har slutförts överförs kontrollen till thread Scheduler och därifrån till varje enskild tråd.

Den ordning som trådarna körs på bestäms av deras prioritet och i vilken ordning de skapades. I demonstrations systemet körs ***thread_0*** först eftersom det har högst prioritet (*det skapades med prioritet 1*). När ***thread_0*** har pausats körs ***thread_5*** följt av körningen av ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _* _thread_7_* *, ***thread_1**_ och slutligen _ *_thread_2_* *.

> [!NOTE]
> *Även om **thread_3** och **thread_4** har samma prioritet (båda har skapats med prioritet 8) börjar **thread_3** köras först. Detta beror på att **thread_3** skapats och blivit klart innan **thread_4**. Trådar med samma prioritet körs på en FIFO-miljö.*

## <a name="thread-0"></a>Tråd 0

Funktionen ***thread_0_entry*** markerar trådens start punkt *(rader 167-190*). ***Thread_0*** är den första tråden i demonstrations systemet som ska köras. Bearbetningen är enkel: den ökar räknaren, väntar på 10 timer-Tick, ställer in en händelse flagga för att väcka ***thread_5*** och upprepar sedan sekvensen.

***Thread_0*** är den högsta prioritets tråden i systemet. När den begärda vilo tiden går ut, kommer det att finnas någon annan körnings tråd i demonstrationen.

## <a name="thread-1"></a>Tråd 1

Funktionen ***thread_1_entry** _ anger start punkten för tråden _(rader 193-216 *). ***Thread_1*** är den andra-till-sista-tråden i demonstrations systemet som ska köras. Bearbetningen består i att öka räknarens räknare, skicka ett meddelande till ***thread_2*** (* till och med * ***queue_0***) och upprepa sekvensen. Observera att ***thread_1**_ pausas när _*_queue_0_*_ blir full (_line 207 *).

## <a name="thread-2"></a>Tråd 2

Funktionen ***thread_2_entry*** markerar trådens start punkt *(rader 219-243*). ***Thread_2*** är den sista tråden i demonstrations systemet som ska köras. Bearbetningen består av att öka räknaren, hämta ett meddelande från ***thread_1*** (via ***queue_0***) och upprepa sekvensen. Observera att ***thread_2** _ pausas när _*_queue_0_*_ blir tomt (_line 233 *).

Även om ***thread_1** _ och _ *_thread_2_** delar den lägsta prioriteten i demonstrations systemet (* prioritet 16 *), *trådarna 3 och 4*

är också de enda trådar som är redo att köras i den här tiden. De är också de enda trådarna som skapas med tids segmentering (*raderna 87 och 93*). Varje tråd kan köras med högst 4 timer-Tick innan den andra tråden körs.

## <a name="threads-3-and-4"></a>Trådar 3 och 4

Funktionen ***thread_3_and_4_entry*** markerar start punkten för både ***thread_3** _ och _ *_thread_4_** (rader 246-280). Båda trådarna har prioriteten 8, vilket gör dem till de tredje och fjärde trådarna i demonstrations systemet som ska köras. Bearbetningen för varje tråd är detsamma: att öka räknarens räknare, Hämta ***semaphore_0***, vilande för 2 timer-Tick, släppa ***semaphore_0*** och upprepa sekvensen. Observera att varje tråd pausas när ***semaphore_0*** inte är tillgängligt (rad 264).

Båda trådarna använder också samma funktion för sin huvudsakliga bearbetning.
Detta ger inga problem eftersom de båda har sin egen unika stack, och C är naturlig reentrant. Varje tråd avgör vilken som är av genom att undersöka trådens indataparametrar (rad 258), som är en inställning när de skapas (rader 102 och 109).

> [!NOTE]
> *Det är också rimligt att du får den aktuella tråd punkten under tråd körning och jämför den med kontroll blockets adress för att fastställa tråd identitet.*

## <a name="thread-5"></a>Tråd 5

Funktionen ***thread_5_entry*** markerar trådens start punkt (rader 283-305). ***Thread_5*** är den andra tråden i demonstrations systemet som ska köras. Bearbetningen består av en stegvis ökning av räknaren, hämtar en händelse flagga från ***thread_0*** (via ***event_flags_0***) och upprepar sekvensen. Observera att ***thread_5*** pausas när händelse flaggan i ***event_flags_0*** inte är tillgänglig (rad 298).

## <a name="threads-6-and-7"></a>Trådar 6 och 7

Funktionen ***thread_6_and_7_entry*** markerar start punkten för både ***thread_6** _ och _ *_thread_7_** (rader 307-358). Båda trådarna har prioriteten 8, vilket gör dem till de femte och sjätte trådarna i demonstrations systemet som ska köras. Bearbetningen för varje tråd är detsamma: att öka räknaren, få ***mutex_0*** två gånger, i vilo läge för 2 timer-Tick, släppa ***mutex_0*** två gånger och upprepa sekvensen. Observera att varje tråd pausas när ***mutex_0*** inte är tillgängligt (rad 325).

Båda trådarna använder också samma funktion för sin huvudsakliga bearbetning. Detta ger inga problem eftersom de båda har sin egen unika stack, och C är naturlig reentrant.
Varje tråd avgör vilken som är av genom att undersöka trådens indataparametrar (rad 319), som är en inställning när de skapas (rader 126 och 133).

## <a name="observing-the-demonstration"></a>Att iaktta demonstrationen

Varje demonstrations tråd ökar sin egen unika räknare.
Följande räknare kan undersökas för att kontrol lera demoets åtgärd:

- thread_0_counter
- thread_1_counter
- thread_2_counter
- thread_3_counter
- thread_4_counter
- thread_5_counter
- thread_6_counter
- thread_7_counter

Var och en av dessa räknare bör fortsätta att öka när demonstrationen körs, med ***thread_1_counter** _ och _ *_thread_2_counter_** ökar med den snabbaste hastigheten.

## <a name="distribution-file-demo_threadxc"></a>Distributions fil: demo_threadx. c

I det här avsnittet visas en fullständig lista över ***demo_threadx. c***, inklusive de rad nummer som refereras till i det här kapitlet.

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
