---
title: Kapitel 3 – krav för modul Manager
description: Den här artikeln beskriver de steg som krävs för att skapa ThreadX module Manager.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826595"
---
# <a name="chapter-3---module-manager-requirements"></a>Kapitel 3 – krav för modul Manager

ThreadX module Manager finns i den inhemska delen av programmet tillsammans med ThreadX-återställnings tider. Den är ansvarig för att starta modulen samt för att ställa in och skicka alla begär Anden om ThreadX API-tjänster.

> [!NOTE]
> Källfilerna för ThreadX module **Manager** (C och Assembly) måste läggas till i biblioteks projektet "**TX**" för ThreadX.

Följande steg krävs för att skapa ThreadX module Manager (varje steg beskrivs mer detaljerat nedan).

1. **TX_THREAD** kontroll blocket måste utökas för att innehålla information om moduler. Det enklaste sättet att åstadkomma detta är att ersätta definitionen av **TX_THREAD_EXTENSION_2** i **filen _tx_port. h_*_ med* TX_THREAD_EXTENSION_2** som finns i **_txm_module_port. h_**. Se [tillägg](appendix.md) för port-/regionsspecifika tillägg.

Exempel tillägg:

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

   Följande tillägg måste definieras i ***tx_port. h***.

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

2. Lägg till alla ***txm_module_manager_ \**** C-och Assembly-filerna i ThreadX Library Project **_TX_**.
3. Återskapa alla bibliotek och körbara projekt. Om NetX Duo krävs måste all modul-och modul Manager C-kod skapas med **TXM_MODULE_ENABLE_NETX_DUO** definierat.

## <a name="module-manager-sources"></a>Källor i modul Manager

ThreadX module Manager har en uppsättning källfiler som är utformade för att länkas och placeras direkt med den inhemska ThreadX-koden. Dessa filer ger möjlighet att starta en modul och fält efter ThreadX API-begäranden från modulen. Modul Manager-filerna är följande.

| **Fil namn** |  **Innehåll** |
|-------------- | ------------- |
| ***txm_module. h*** | Ta med en fil som definierar information om moduler (även i modulens käll kod). |
| ***txm_module_manager_dispatch. h*** | Inkludera en fil som definierar stöd för Dispatch-funktioner.|
| ***txm_module_manager_util. h*** | Inkludera en fil som definierar makron & funktioner för intern funktion. |
| ***txm_module_port. h*** | Inkludera en fil som definierar portbaserad information om moduler (som också ingår i modulens käll kod). |
| ***tx_initialize_low_level. \[ s, S, 68 \]** _ | Ersätter befintlig biblioteks fil för ThreadX. Uppdaterad vektor tabell och ytterligare vektor hanterare för modul Manager och minnes undantag. _This-filen finns bara i cortex-A7/ARM, cortex-M7/ARM, cortex-R4/ARM, cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR. *|
| ***tx_thread_context_restore. s** _ | Ersätter befintlig biblioteks fil för ThreadX. Återställ tråd kontext efter avbrott-bearbetning. _This-filen finns bara i cortex-A7/ARM, cortex-R4/ARM, cortex-R4/IAR. *|
| ***tx_thread_schedule. \[ s, S, 68\]*** | Ersätter befintlig biblioteks fil för ThreadX. Utökad Scheduler Code, som i det här fallet används för att uppdatera minnes hanterings register. |
| ***tx_thread_stack_build. s** _ | Ersätter befintlig biblioteks fil för ThreadX. Skapar stack ramen för en tråd. _This-filen finns bara i cortex-A7/ARM, cortex-R4/ARM, cortex-R4/IAR. *|
| ***txm_module_manager_thread_stack_build. \[ s, S, 68\]*** | Skapar alla inledande stackar för moduler, inklusive inställningar för positions oberoende data åtkomst. |
| ***txm_module_manager_user_mode_entry. \[ s, S \]** _ | Tillåter att modulen går in i kernel-läge. _This-filen finns bara i cortex-A7/ARM, cortex-R4/ARM, cortex-R4/IAR. *|
| ***txm_module_manager_alignment_adjust. c*** | Hanterar de portbaserade justerings kraven.|
| ***txm_module_manager_application_request. c*** | Hanterar programspecifika förfrågningar till den inhemska koden. |
| ***txm_module_manager_callback_request. c*** | Skickar en callback-begäran till en modul. |
| ***txm_module_manager_event_flags_notify_trampoline. c*** | Bearbetar händelse flaggorna ange meddelande anrop från ThreadX. |
| ***txm_module_manager_external_memory_enable. c*** | Skapar en post i minnes hanterings tabellen för ett delat minnes utrymme som modulen har åtkomst till. |
| ***txm_module_manager_file_load. c*** | Allokerar och läser in en fil för en binär modul i minnesmodulens minnes området och förbereder den för körning. |
| ***txm_module_manager_in_place_load. c*** | Allokerar modulens data områden och förbereder för att köra modulen från den angivna kod adressen. |
| ***txm_module_manager_initialize. c*** | Initierar modul hanteraren, inklusive specifikation av modulens minnes området som är tillgängligt för att läsa in och köra moduler. |
| ***txm_module_manager_initialize_mmu. c** _ | Initiera MMU. Användare kan redigera den här filen enligt minnes kartan. _This-filen finns bara i cortex-A7/ARM * |
| ***txm_module_manager_mm_initialize. c** _ | Initiera MPU/MMU. Användare kan redigera den här filen enligt minnes kartan. _This-filen finns bara i cortex-A7/ARM * |
| ***txm_module_manager_kernel_dispatch. c*** | Hanterar API-begäranden baserat på ID för begäran. |
| ***txm_module_manager_maximum_module_priority_set. c*** | Anger högsta tillåtna tråd prioritet i en modul. |
| ***txm_module_manager_memory_fault_handler. c*** | Hanterar minnes fel som identifierats i en modul som körs. |
| ***txm_module_manager_memory_fault_notify. c*** | Registrerar ett återanrop för program meddelanden när ett minnes fel inträffar. |
| ***txm_module_manager_memory_load. c*** | Allokerar och läser in modulens kod och data och förbereder modulen för körning. |
| ***txm_module_manager_mm_register_setup. c*** | Ställer in MPU/MMU-register för modulen baserat på var koden och data läses in. |
| ***txm_module_manager_object_allocate. c*** | Allokerar minne för ett module-objekt. |
| ***txm_module_manager_object_deallocate. c*** | Frigör minne för ett modul objekt. |
| ***txm_module_manager_object_pointer_get. c*** | Söker efter angiven objekt typ och namn, och returnerar objekt pekaren om den hittas. |
| ***txm_module_manager_object_pointer_get_extended. c*** | Söker efter angiven objekt typ och namn, och returnerar objekt pekaren om den hittas. Namn längd som angetts för säkerhet. |
| ***txm_module_manager_object_pool_create. c***  | Skapar en pool av objekt utanför modulens data områden som module-program kan allokera från. |
| ***txm_module_manager_properties_get. c*** | Hämtar egenskaperna för den angivna modulen. |
| ***txm_module_manager_queue_notify_trampoline. c*** | Bearbetar köns meddelande anropet från ThreadX. |
| ***txm_module_manager_semaphore_notify_trampoline. c*** | Bearbetar meddelandet om semafors meddelande anropet från ThreadX.|
| ***txm_module_manager_start. c*** | Startar körning av en modul. |
| ***txm_module_manager_stop. c*** | Stoppar körningen av en modul. |
| ***txm_module_manager_thread_create. c*** | Skapar alla-modul-trådar. |
| ***txm_module_manager_thread_notify_trampoline. c*** | Bearbetar anropet för tråd-och avslutnings meddelande från ThreadX. |
| ***txm_module_manager_thread_reset. c*** | Återställ en modul tråd. |
| ***txm_module_manager_timer_notify_trampoline. c*** | Förfaller av processer från ThreadX. |
| ***txm_module_manager_unload. c*** | Laddar bort modulen från modulens minnes yta. |
| ***txm_module_manager_util. c*** | Interna hjälp funktioner för Manager. |

## <a name="module-manager-initialization"></a>Initiering av modul Manager

Den inhemska delen av programmet ansvarar för att anropa modul hanterarens initierings funktion ***txm_module_manager_initialize***. Den här funktionen konfigurerar de interna strukturerna för att läsa in och ta bort moduler, inklusive konfiguration av det minnes området som används för att allokera minnesmodulens minne.

## <a name="module-manager-loading"></a>Inläsning av modul Manager

Module Manager kan läsa in moduler dynamiskt i modulens minne från binärfiler för binärfiler eller från ett modul kods avsnitt som redan finns i det inhemska kod området. Dessutom kan module Manager köra kod på plats, det vill säga att endast modulens data allokeras i minnesmodulen och att kod körningen görs på plats. Följande inläsnings-API-funktioner i module Manager är tillgängliga.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

Den minnes säkra versionen av module Manager ser också till att modulen läses in med rätt justering och minnes hanterings registren konfigureras korrekt för varje modul. När minnes skydd aktive ras via modulen inlednings alternativ, är minnesmodulens minnes åtkomst begränsad till modulens kod och data områden.

## <a name="module-manager-starting"></a>Module Manager startar

Modul hanteraren initierar körning av en tidigare inläst modul via ***txm_module_manager_start*** API-funktionen. Den här funktionen skapar en tråd som går in i modulen på den Start plats som anges i modulen inledning för att initiera modul körning. Trådens prioritet och stack storlek anges också i modulen inledning.

## <a name="module-manager-stopping"></a>Stänger av module Manager

Module Manager avslutar körningen av en modul som har lästs in och körs via funktionen ***txm_module_manager_stop*** . Den här API-funktionen avslutar först och tar bort den första start tråden. Om modulen inledning anger en stopp tråd skapas och körs den här tråden. Module Manager väntar under en bestämd tids period då stopp tråden ska slutföras. När du är klar tas alla system resurser som skapats av modulen bort och modulen placeras i ett inaktivt tillstånd, från vilken den kan startas om eller tas bort från minnet.

## <a name="module-manager-unloading"></a>Borttagning av modul Manager

Module Manager inaktiverar en tidigare inläst men inte exekverande modul via funktionen ***txm_module_manager_unload*** . Detta API frigör allt minne som är associerat med modulen och frigör det för användning med en annan modul i framtiden.

## <a name="module-manager-requests"></a>Module Manager-begäranden

Begär Anden som görs av moduler till modul Manager utförs via makron i ***txm_module. h*** som mappar alla ThreadX-anrop för att anropa modul hanterarens sändnings funktion via en funktions pekare som tillhandahålls till modulen av modul Manager.

Ytterligare programspecifika tjänster som görs via modulen anropar ***txm_module_application_request*** hanteras av samma makro mekanism som används för ThreadX-API: et. Som standard är den här hanterings funktionen i modul Manager Tom och utformad så att programmet lägger till den nödvändiga koden för att bearbeta programspecifika begär Anden.

Om begäran inte implementeras av module Manager returneras ett värde för **TX_NOT_AVAILABLE** fel status av modul Manager. Den här felkoden returneras även om modulen begär en åtgärd som ligger utanför omfånget för modulens åtkomst. En modul kan till exempel inte skapa en timer med timer-kontrollens block eller återanrops adress utanför modulens kod områden.

## <a name="module-manager-example"></a>Exempel på modul hanteraren

Följande är ett exempel på en modul Manager-kod som startar exempel-modulen som definierades tidigare i kapitel 2. Det förutsätts att modulen redan har lästs in, antagen av fel söknings programmet, i ROM-0x00800000.

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

## <a name="module-manager-building"></a>Skapa modul Manager

***Txm_module_manager_ \**** källfiler måste läggas till i ThreadX-biblioteket.

Ett ThreadX module Manager-program är i praktiken detsamma som ett standard program för ThreadX, vilket är en eller flera programfiler som är länkade tillsammans med ThreadX-biblioteket ***TX. a***. Att skapa en modul Manager-applikation är beroende av den verktygs kedja som används. Se [tillägg](appendix.md) för port-/regionsspecifika exempel.
