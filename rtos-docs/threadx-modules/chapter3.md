---
title: Kapitel 3 – Krav för modulhanteraren
description: Den här artikeln är en beskrivning av de steg som krävs för att skapa ThreadX-modulhanteraren.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6c4d0993284c8e0b8264020d721ac12bdfe8117df4480fb54ee4d5b20a1f677e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799191"
---
# <a name="chapter-3---module-manager-requirements"></a>Kapitel 3 – Krav för modulhanteraren

ThreadX-modulhanteraren finns i den invarande delen av programmet tillsammans med ThreadX RTOS. Den ansvarar för att starta modulen samt att sätta in och skicka alla modulbegäranden för ThreadX API-tjänster.

> [!NOTE]
> Källfilerna för **ThreadX-modulhanteraren** (C och sammansättning) ska läggas till i ThreadX-biblioteksprojektet "**tx**".

Följande steg krävs för att skapa ThreadX-modulhanteraren (varje steg beskrivs i detalj nedan).

1. Kontrollblocket **TX_THREAD** utökas till att omfatta modulinformation. Det enklaste sättet att åstadkomma detta är att ersätta **definitionen av TX_THREAD_EXTENSION_2** i filen **_tx_port.h_ _ med *_* TX_THREAD_EXTENSION_2** som finns i **_txm_module_port.h_**. Se [bilaga](appendix.md) för portspecifika tillägg.

Exempeltillägg:

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   Följande tillägg måste definieras i ***tx_port.h***.

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. Lägg till alla ***txm_module_manager_ \**** C och sammansättningsfiler i ThreadX-biblioteksprojektet **_tx_**.
3. Återskapa alla bibliotek och körbara projekt. Om NetX Duo krävs ska all C-kod för Module och Module Manager byggas **TXM_MODULE_ENABLE_NETX_DUO** definieras.

## <a name="module-manager-sources"></a>Module Manager-källor

ThreadX-modulhanteraren har en uppsättning källfiler som är utformade för att länkas och finns direkt med den lokala ThreadX-koden. Dessa filer ger möjlighet att starta en modul och sätta in efterföljande ThreadX API-begäranden från modulen. Modulhanterarens filer är följande.

| **Filnamn** |  **Innehåll** |
|-------------- | ------------- |
| ***txm_module.h*** | Inkludera fil som definierar modulinformation (ingår även i modulens källkod). |
| ***txm_module_manager_dispatch.h*** | Inkludera fil som definierar dispatch helper-funktioner.|
| ***txm_module_manager_util.h*** | Inkludera fil som definierar interna verktygshjälp makron & funktioner. |
| ***txm_module_port.h*** | Inkludera fil som definierar portspecifik modulinformation (ingår även i modulens källkod). |
| ***tx_initialize_low_level. \[ s,S,68 \]** _ | Ersätter befintlig ThreadX-biblioteksfil. Uppdaterad vektortabell och ytterligare vektorhanterare för modulhanterare och minnesundantag. _This filen finns bara i Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.*|
| ***tx_thread_context_restore.s** _ | Ersätter befintlig ThreadX-biblioteksfil. Återställ trådkontexten efter avbrottsbearbetning. _This filen finns bara i Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***tx_thread_schedule. \[ s,S,68\]*** | Ersätter befintlig ThreadX-biblioteksfil. Utökad scheduler-kod, som i det här fallet används för att uppdatera minneshanteringsregister. |
| ***tx_thread_stack_build.s** _ | Ersätter befintlig ThreadX-biblioteksfil. Skapar stackramen för en tråd. _This filen finns bara i Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_thread_stack_build. \[ s,S,68\]*** | Skapar alla modulens initiala stackar, inklusive konfiguration för positionsoberoende dataåtkomst. |
| ***txm_module_manager_user_mode_entry. \[ s,S \]** _ | Tillåter att modulen går in i kernelläge. _This filen finns bara i Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_alignment_adjust.c*** | Hanterar portspecifika justeringskrav.|
| ***txm_module_manager_application_request.c*** | Hanterar programspecifika begäranden till den hemmavarande koden. |
| ***txm_module_manager_callback_request.c*** | Skickar en återanropsbegäran till en modul. |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | Bearbetar händelseflaggorna med meddelandeanrop från ThreadX. |
| ***txm_module_manager_external_memory_enable.c*** | Skapar en post i minneshanteringstabellen för ett delat minnesutrymme som modulen kan komma åt. |
| ***txm_module_manager_file_load.c*** | Allokerar och läser in en binär modulfil i modulminnesområdet och förbereder den för körning. |
| ***txm_module_manager_in_place_load.c*** | Allokerar moduldataområdet och förbereder för modulkörning från den angivna kodadressen. |
| ***txm_module_manager_initialize.c*** | Initierar modulhanteraren, inklusive specifikation av modulminnesområdet som är tillgängligt för inläsning och körning av moduler. |
| ***txm_module_manager_initialize_mmu.c** _ | Initiera MMU. Användare kan redigera den här filen enligt sin minneskarta. _This filen finns bara i Cortex-A7/ARM* |
| ***txm_module_manager_mm_initialize.c** _ | Initiera MPU/MMU. Användare kan redigera den här filen enligt sin minneskarta. _This filen finns bara i Cortex-A7/ARM* |
| ***txm_module_manager_kernel_dispatch.c*** | Hanterar modul-API-begäranden baserat på begäran-ID. |
| ***txm_module_manager_maximum_module_priority_set.c*** | Anger den högsta trådprioritet som tillåts i en modul. |
| ***txm_module_manager_memory_fault_handler.c*** | Hanterar minnesfel som identifierats i en körningsmodul. |
| ***txm_module_manager_memory_fault_notify.c*** | Registrerar ett återanrop av programmeddelanden när ett minnesfel inträffar. |
| ***txm_module_manager_memory_load.c*** | Allokerar och läser in en moduls kod och data och förbereder modulen för körning. |
| ***txm_module_manager_mm_register_setup.c*** | Uppsättningar MPU/MMU-register för modulen baserat på var koden och data läses in. |
| ***txm_module_manager_object_allocate.c*** | Allokerar minne för ett modulobjekt. |
| ***txm_module_manager_object_deallocate.c*** | Avallokerar minne för ett modulobjekt. |
| ***txm_module_manager_object_pointer_get.c*** | Söker efter den angivna objekttypen och namnet, och returnerar objekt pekaren om den hittas. |
| ***txm_module_manager_object_pointer_get_extended.c*** | Söker efter den angivna objekttypen och namnet, och returnerar objekt pekaren om den hittas. Namnlängden har angetts för säkerhet. |
| ***txm_module_manager_object_pool_create.c***  | Skapar en pool med objekt utanför modulens dataområde som modulprogram kan allokera från. |
| ***txm_module_manager_properties_get.c*** | Hämtar egenskaperna för den angivna modulen. |
| ***txm_module_manager_queue_notify_trampoline.c*** | Bearbetar kömeddelandeanropet från ThreadX. |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | Bearbetar aviseringsanropet semaphore put från ThreadX.|
| ***txm_module_manager_start.c*** | Startar körningen av en modul. |
| ***txm_module_manager_stop.c*** | Stoppar körningen av en modul. |
| ***txm_module_manager_thread_create.c*** | Skapar alla modultrådar. |
| ***txm_module_manager_thread_notify_trampoline.c*** | Bearbetar trådmeddelandeanropet för inmatning/avslut från ThreadX. |
| ***txm_module_manager_thread_reset.c*** | Återställa en modultråd. |
| ***txm_module_manager_timer_notify_trampoline.c*** | Bearbetar förfallotid från ThreadX. |
| ***txm_module_manager_unload.c*** | Tar bort modulen från modulens minnesutrymme. |
| ***txm_module_manager_util.c*** | Interna hjälpfunktioner för chef. |

## <a name="module-manager-initialization"></a>Modulhanterarens initiering

Den ursprungliga delen av programmet ansvarar för att anropa modulhanterarens initieringsfunktion ***txm_module_manager_initialize***. Den här funktionen ställer in de interna strukturerna för inläsning och avlastning av moduler, inklusive att konfigurera det minnesområde som används för att allokera modulminne.

## <a name="module-manager-loading"></a>Module Manager-inläsning

Modulhanteraren kan läsa in moduler dynamiskt i modulminnet från binära modulfiler eller från ett modulkodavsnitt som redan finns i det lokala kodområdet. Modulhanteraren kan dessutom köra kod på plats, det vill säga att endast moduldata allokeras i modulminnet och kodkörningen utförs på plats. Följande api-funktioner för module manager-inläsning är tillgängliga.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

Den minnesskyddade versionen av Modulhanteraren ser också till att modulen har lästs in med rätt justering och att minneshanteringsregister har ställts in korrekt för varje modul. När minnesskydd har aktiverats via modulens ingressalternativ begränsas modulminnesåtkomsten till modulkoden och dataområdena.

## <a name="module-manager-starting"></a>Module Manager startar

Modulhanteraren initierar körningen av en tidigare  inläst modul via txm_module_manager_start API-funktionen. För att initiera modulkörningen skapar den här funktionen en tråd som går in i modulen på den startplats som anges i modulinledningen. Prioritet och stackstorlek för den här tråden anges också i modulens ingress.

## <a name="module-manager-stopping"></a>Modulhanteraren stoppas

Modulhanteraren avslutar körningen av en tidigare inläst  och körande modul via txm_module_manager_stop funktion. Den här API-funktionen avslutas först och tar bort den första starttråden. Om modulinledningen anger en stopptråd skapas och körs den här tråden. Modulhanteraren väntar en fast tidsperiod på att stopptråden ska slutföras. När du är klar tas alla systemresurser som skapats av modulen bort och modulen placeras i ett vilande tillstånd där den antingen kan startas om eller tas bort.

## <a name="module-manager-unloading"></a>Module Manager-avlastning

Modulhanteraren tar bort en tidigare inläst men  inte kör modulen via txm_module_manager_unload funktion. Det här API:et släpper allt minne som är associerat med modulen och frigör det för användning med en annan modul i framtiden.

## <a name="module-manager-requests"></a>Module Manager-begäranden

Begäranden som görs av moduler till modulhanteraren görs via makron i ***txm_module.h*** som mappar alla ThreadX-anrop för att anropa dispatchfunktionen i Module Manager via en funktionspekare som tillhandahålls till modulen av modulhanteraren.

Ytterligare programspecifika tjänster som görs via modulen som ***anropar txm_module_application_request*** hanteras av samma makromekanism som används för ThreadX-API:et. Som standard är den här hanteringsfunktionen i Modulhanteraren tom och utformad så att programmet lägger till nödvändig kod för att bearbeta programspecifika begäranden.

Om begäran inte implementeras av modulhanteraren returneras värdet **TX_NOT_AVAILABLE** felstatus av modulhanteraren. Den här felkoden returneras också om modulen begär en åtgärd som ligger utanför omfånget för modulens åtkomst. En modul kan till exempel inte skapa en timer med timerkontrollblocket eller återanropsadressen utanför modulens kodområde.

## <a name="module-manager-example"></a>Module Manager-exempel

Följande är ett exempel på modulhanterarens kod som startar exempelmodulen som tidigare definierades i kapitel 2. Det förutsätts att modulen redan har lästs in, förmodligen av felsökaren, på ROM-0x00800000.

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a>Modulhanterarens byggnad

Den ***txm_module_manager_ \**** måste läggas till i ThreadX-biblioteket.

Ett ThreadX Module Manager-program är i praktiken detsamma som ett ThreadX-standardprogram, som är en eller flera programfiler som är länkade tillsammans med ThreadX-biblioteket ***tx.a***. Att skapa ett modulhanteraresprogram beror på vilken verktygskedja som används. Se [bilaga](appendix.md) för portspecifika exempel.
