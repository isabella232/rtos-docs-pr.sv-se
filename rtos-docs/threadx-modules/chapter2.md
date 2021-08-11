---
title: Kapitel 2 – Modulkrav
description: Den här artikeln är en beskrivning av kraven för att skapa en ThreadX-modul.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b814e7c2b510093b809b70b02d9a11ed39996d114f2306e0993893799453cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791966"
---
# <a name="chapter-2---module-requirements"></a>Kapitel 2 – Modulkrav

En ThreadX-modul innehåller en ingress som definierar modulens grundläggande egenskaper. Ingressen följs av instruktionsområdet för modulen. Moduler kan köras på plats eller läsas in i modulminnesområdet av modulhanteraren innan de körs. Det enda kravet är att ingressen alltid finns på modulens första adress. Bild 2 visar en grundläggande modullayout.

| Modullayout |
|:---:|
| \[modulinamble\]         |
| \[modulinstruktionsområde\] |
| \[ram-området för modulen\]         |

**Bild 2** – Modullayout

> [!NOTE]
> Moduler måste byggas med lämplig positionsoberoende kod och alternativ för datakompilerare/länkare. Detta möjliggör körning av modulen i alla minnesutrymme.

När en modultråd skapas allokeras ett andra stackutrymme för användning när tråden finns i den minnesskyddade kerneln. Storleken på trådens kernelstackutrymme kan konfigureras av användaren med hjälp **av TXM_MODULE_KERNEL_STACK_SIZE** **_i txm_module_port.h_*_. Detta gör att* en mindre stackstorlek kan användas när du skapar en modultråd, eftersom stacken som anges av användaren _vid anrop av_ _ tx_thread_create** endast används i modulen.

> [!NOTE]
> Överst i en modultrådstack finns strukturen för trådinmatningsinformation (**TXM_MODULE_THREAD_ENTRY_INFO**), så den tillgängliga stackstorleken minskas med storleken på den här strukturen. När du skapar en tråd i en modul ska du öka stackstorleken med minst den storleken på den här strukturen.

Följande steg krävs för att skapa och skapa en ThreadX-modul (varje steg beskrivs i detalj nedan).

1. Alla C-filer i en modul måste #define **TXM_MODULE** innan du inkluderar **_txm_module.h_**. Detta kan åstadkommas i källfilen som kompileras eller som en del av projektinställningarna. När du gör det mappar du om ThreadX API-anropen till den modulspecifika versionen av API:et som anropar dispatch-funktionen i den invarande modulhanteraren för att utföra anropet till den faktiska API-funktionen.
2. Varje modul måste ha en ingress vid sin första instruktionsområdesadress som definierar modulens egenskaper och resursbehov.
3. Varje modul måste länka ingressen i början av modulens instruktionsområde.
4. Varje modul måste länka till ett modulbibliotek (***txm.a***), som innehåller modulspecifika funktioner som används för att interagera med ThreadX.

## <a name="module-sources"></a>Modulkällor

ThreadX-moduler har en egen uppsättning källfiler som är utformade för att länkas och placeras direkt med modulens källkod. De här filerna utgör bryggan mellan den separata modulen och den lokala modulhanteraren. Modulfilerna är följande.

| Filnamn | Innehåll |
|---|---|
| **txm_module.h** | Inkludera fil som definierar modulinformation. |
| **txm_module_port.h** | Inkludera fil som definierar portspecifik modulinformation. |
| **txm_module_user.h** | Definierar och värden som användaren kan anpassa. |
| **txm_module_initialize.s [1][3]** | Anropar inbyggda funktioner till startmodulen. |
| **txm_module_preamble. \{ s/S/68\}** | Modulindelabar sammansättningsfil. Den här filen definierar olika modulspecifika attribut och är länkad till modulens programkod. |
| **txm_module_application_request.c [1]** | Funktionen för modulprogrambegäran skickar en programspecifik begäran till den hemmavarande koden. |
| **txm_module_callback_request_thread_entry.c &nbsp; [1]** | Återanropstråd för modulen som ansvarar för bearbetning av återanrop som begärs av modulen, inklusive timers och återanrop av meddelanden. |
| **txm_*.c [1][2]** | ThreadX API-standardtjänsterna anropar kernel dispatcher.
| **txm_module_object_allocate.c [1]** | Modulfunktionen för att allokera minne för modulobjekt som finns i manager-minnespoolen. |
| **txm_module_object_deallocate.c [1]** | Modulfunktionen för att avallokera minne för modulobjekt som finns i manager-minnespoolen. |
| **txm_module_object_pointer_get.c [1]** | Modulfunktionen för att hämta en pekare till ett systemobjekt. |
| **txm_module_object_pointer_get_extended.c [1]** | Modulfunktionen för att hämta en pekare till ett systemobjekt, namnlängdens säkerhet. |
| **txm_module_thread_shell_entry.c [1]** | Modultrådens postfunktion. |
| **txm_module_thread_system_suspend.c [1]** | Modulfunktion för att pausa en tråd. |

**[1]** Finns i biblioteket **_txm.a_**.

**[2] De** här filerna har samma namn som ThreadX API-filerna, **med txm_** prefix i stället för **tx_** prefix.

**[3]** Filen **txm_module_initialize.s är** endast för portar som använder ARM-verktyg.

## <a name="module-preamble"></a>Modulens ingress

Modulinledningen definierar egenskaper och resurser för modulen. Information som den första trådinmatningsfunktionen och det inledande minnesområdet som är associerat med tråden definieras i ingressen. Portspecifika ingressexempel finns i [bilagan](appendix.md). Bild 3 visar ett exempel på en ThreadX-modul preamble för ett allmänt mål (raderna som börjar med * ändras vanligtvis av programmet):

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

**Bild 3**

I de flesta fall behöver utvecklaren bara definiera modulens starttråd (offset 0x1C), modul-ID (offset 0x10), start/stopp-trådprioritet (förskjuten 0x24) och starta/stoppa trådstackstorlek (förskjuten 0x28). Demonstrationen ovan är konfigurerad så att modulens starttråd är ***demo_module_start** _, modul-ID:t _*_är 0x12345678_*_ och starttråden har _*_prioriteten 1_*_ och stackstorleken _ *_2 048_** byte.

Vissa program kan eventuellt definiera en stopptråd som körs när Modulhanteraren stoppar modulen. Dessutom kan vissa program använda fältet Modulegenskaper, som definieras på följande sätt.

## <a name="module-properties-bit-map"></a>Bitmappning för modulegenskaper

Tabellen nedan visar ett exempel på bitkartan för egenskaper. Portspecifika egenskapsmappar finns i [bilagan](appendix.md).

| Bitars | Värde | Innebörd |
|---|---|---|
| 0 | 0<br />1 | Körning av privilegierat läge<br />Körning av användarläge |
| 1 | 0<br />1 | Inget MPU-skydd<br />MPU-skydd (måste ha användarläge valt) |
| 2 | 0<br />1 | Inaktivera åtkomst till delat/externt minne<br />Aktivera åtkomst till delat/externt minne |
| [23-3] | 0 | Reserverat
| [31-24] | <br />0x01<br />0x02<br />0x03 | **Kompilator-ID**<br />Iar<br />ARM<br />Gnu |


## <a name="module-linker-control-file"></a>Modullänkerkontrollfil

När du skapar en modul måste modulinledningen placeras före andra kodavsnitt. En modul måste byggas med positionsoberoende kod och dataavsnitt. Portspecifika exempellänkningsfiler finns i [bilagan](appendix.md).

## <a name="module-threadx-library"></a>Module ThreadX-bibliotek

Varje modul måste länkas till ett särskilt modulcentrerat ThreadX-bibliotek. Det här biblioteket ger åtkomst till ThreadX-tjänster i den hemmavarande koden. Merparten av åtkomsten sker via de txm_ ***\* .c-filerna.*** Följande är ett exempel på modulåtkomstanropet för ThreadX API-funktionen **_tx_thread_relinquish_* _ _*_ \_ (i txm_thread_relinquish.c \* ).).

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

I det här exemplet används funktionspekaren som tillhandahålls av ***Modulhanteraren*** för att anropa dispatch-funktionen module manager med det ID som är associerat med tx_thread_relinquish tjänsten. Den här tjänsten tar inga parametrar.

## <a name="module-example"></a>Modulexempel

Följande är ett exempel på ThreadX-standarddemonstrationen i form av en modul. De största skillnaderna mellan ThreadX-standarddemonstrationen och moduldemonstrationen är.

1. Ersättning av ***tx_api.h** _ med _ *_txm_module.h_**
2. Tillägg av **#define TXM_MODULE** före **_txm_module.h_**
3. Ersättning av ***main** _ och _ *tx_application_define** med **_demo_module_start_**
4. Deklarera *pekare* till ThreadX-objekt i stället för själva objekten.

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

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

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

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
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
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
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

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
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
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
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a>Skapa moduler

Att skapa en modul beror på vilken verktygskedja som används. Se [bilaga](appendix.md) för portspecifika exempel. Vanliga aktiviteter för alla portar är följande.

- Skapa ett modulbibliotek
- Skapa modulprogrammet

Varje modul måste ha en **txm_module_preamble** (särskilt konfiguration för modulen) och modulbiblioteket (till exempel **_txm.a_**).
