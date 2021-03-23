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
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="a4d56-103">Kapitel 3 – krav för modul Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="a4d56-104">ThreadX module Manager finns i den inhemska delen av programmet tillsammans med ThreadX-återställnings tider.</span><span class="sxs-lookup"><span data-stu-id="a4d56-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="a4d56-105">Den är ansvarig för att starta modulen samt för att ställa in och skicka alla begär Anden om ThreadX API-tjänster.</span><span class="sxs-lookup"><span data-stu-id="a4d56-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="a4d56-106">Källfilerna för ThreadX module **Manager** (C och Assembly) måste läggas till i biblioteks projektet "**TX**" för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="a4d56-107">Följande steg krävs för att skapa ThreadX module Manager (varje steg beskrivs mer detaljerat nedan).</span><span class="sxs-lookup"><span data-stu-id="a4d56-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="a4d56-108">**TX_THREAD** kontroll blocket måste utökas för att innehålla information om moduler.</span><span class="sxs-lookup"><span data-stu-id="a4d56-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="a4d56-109">Det enklaste sättet att åstadkomma detta är att ersätta definitionen av **TX_THREAD_EXTENSION_2** i **filen _tx_port. h_*_ med\* TX_THREAD_EXTENSION_2*\* som finns i **_txm_module_port. h_**.</span><span class="sxs-lookup"><span data-stu-id="a4d56-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="a4d56-110">Se [tillägg](appendix.md) för port-/regionsspecifika tillägg.</span><span class="sxs-lookup"><span data-stu-id="a4d56-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="a4d56-111">Exempel tillägg:</span><span class="sxs-lookup"><span data-stu-id="a4d56-111">Example extension:</span></span>

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

   <span data-ttu-id="a4d56-112">Följande tillägg måste definieras i ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="a4d56-112">The following extensions must be defined in ***tx_port.h***.</span></span>

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

2. <span data-ttu-id="a4d56-113">Lägg till alla ***txm_module_manager_ \**** C-och Assembly-filerna i ThreadX Library Project **_TX_**.</span><span class="sxs-lookup"><span data-stu-id="a4d56-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="a4d56-114">Återskapa alla bibliotek och körbara projekt.</span><span class="sxs-lookup"><span data-stu-id="a4d56-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="a4d56-115">Om NetX Duo krävs måste all modul-och modul Manager C-kod skapas med **TXM_MODULE_ENABLE_NETX_DUO** definierat.</span><span class="sxs-lookup"><span data-stu-id="a4d56-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="a4d56-116">Källor i modul Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-116">Module Manager sources</span></span>

<span data-ttu-id="a4d56-117">ThreadX module Manager har en uppsättning källfiler som är utformade för att länkas och placeras direkt med den inhemska ThreadX-koden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="a4d56-118">Dessa filer ger möjlighet att starta en modul och fält efter ThreadX API-begäranden från modulen.</span><span class="sxs-lookup"><span data-stu-id="a4d56-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="a4d56-119">Modul Manager-filerna är följande.</span><span class="sxs-lookup"><span data-stu-id="a4d56-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="a4d56-120">**Fil namn**</span><span class="sxs-lookup"><span data-stu-id="a4d56-120">**File Name**</span></span> |  <span data-ttu-id="a4d56-121">**Innehåll**</span><span class="sxs-lookup"><span data-stu-id="a4d56-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="a4d56-122">***txm_module. h***</span><span class="sxs-lookup"><span data-stu-id="a4d56-122">***txm_module.h***</span></span> | <span data-ttu-id="a4d56-123">Ta med en fil som definierar information om moduler (även i modulens käll kod).</span><span class="sxs-lookup"><span data-stu-id="a4d56-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="a4d56-124">***txm_module_manager_dispatch. h***</span><span class="sxs-lookup"><span data-stu-id="a4d56-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="a4d56-125">Inkludera en fil som definierar stöd för Dispatch-funktioner.</span><span class="sxs-lookup"><span data-stu-id="a4d56-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="a4d56-126">***txm_module_manager_util. h***</span><span class="sxs-lookup"><span data-stu-id="a4d56-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="a4d56-127">Inkludera en fil som definierar makron & funktioner för intern funktion.</span><span class="sxs-lookup"><span data-stu-id="a4d56-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="a4d56-128">***txm_module_port. h***</span><span class="sxs-lookup"><span data-stu-id="a4d56-128">***txm_module_port.h***</span></span> | <span data-ttu-id="a4d56-129">Inkludera en fil som definierar portbaserad information om moduler (som också ingår i modulens käll kod).</span><span class="sxs-lookup"><span data-stu-id="a4d56-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="a4d56-130">\***tx_initialize_low_level. \[ s, S, 68 \]** _</span><span class="sxs-lookup"><span data-stu-id="a4d56-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="a4d56-131">Ersätter befintlig biblioteks fil för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="a4d56-132">Uppdaterad vektor tabell och ytterligare vektor hanterare för modul Manager och minnes undantag.</span><span class="sxs-lookup"><span data-stu-id="a4d56-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="a4d56-133">_This-filen finns bara i cortex-A7/ARM, cortex-M7/ARM, cortex-R4/ARM, cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="a4d56-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="a4d56-134">\***tx_thread_context_restore. s** _</span><span class="sxs-lookup"><span data-stu-id="a4d56-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="a4d56-135">Ersätter befintlig biblioteks fil för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="a4d56-136">Återställ tråd kontext efter avbrott-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="a4d56-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="a4d56-137">_This-filen finns bara i cortex-A7/ARM, cortex-R4/ARM, cortex-R4/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="a4d56-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="a4d56-138">***tx_thread_schedule. \[ s, S, 68\]***</span><span class="sxs-lookup"><span data-stu-id="a4d56-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="a4d56-139">Ersätter befintlig biblioteks fil för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="a4d56-140">Utökad Scheduler Code, som i det här fallet används för att uppdatera minnes hanterings register.</span><span class="sxs-lookup"><span data-stu-id="a4d56-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="a4d56-141">\***tx_thread_stack_build. s** _</span><span class="sxs-lookup"><span data-stu-id="a4d56-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="a4d56-142">Ersätter befintlig biblioteks fil för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="a4d56-143">Skapar stack ramen för en tråd.</span><span class="sxs-lookup"><span data-stu-id="a4d56-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="a4d56-144">_This-filen finns bara i cortex-A7/ARM, cortex-R4/ARM, cortex-R4/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="a4d56-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="a4d56-145">***txm_module_manager_thread_stack_build. \[ s, S, 68\]***</span><span class="sxs-lookup"><span data-stu-id="a4d56-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="a4d56-146">Skapar alla inledande stackar för moduler, inklusive inställningar för positions oberoende data åtkomst.</span><span class="sxs-lookup"><span data-stu-id="a4d56-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="a4d56-147">\***txm_module_manager_user_mode_entry. \[ s, S \]** _</span><span class="sxs-lookup"><span data-stu-id="a4d56-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="a4d56-148">Tillåter att modulen går in i kernel-läge.</span><span class="sxs-lookup"><span data-stu-id="a4d56-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="a4d56-149">_This-filen finns bara i cortex-A7/ARM, cortex-R4/ARM, cortex-R4/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="a4d56-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="a4d56-150">***txm_module_manager_alignment_adjust. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="a4d56-151">Hanterar de portbaserade justerings kraven.</span><span class="sxs-lookup"><span data-stu-id="a4d56-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="a4d56-152">***txm_module_manager_application_request. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="a4d56-153">Hanterar programspecifika förfrågningar till den inhemska koden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="a4d56-154">***txm_module_manager_callback_request. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="a4d56-155">Skickar en callback-begäran till en modul.</span><span class="sxs-lookup"><span data-stu-id="a4d56-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="a4d56-156">***txm_module_manager_event_flags_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="a4d56-157">Bearbetar händelse flaggorna ange meddelande anrop från ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="a4d56-158">***txm_module_manager_external_memory_enable. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="a4d56-159">Skapar en post i minnes hanterings tabellen för ett delat minnes utrymme som modulen har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="a4d56-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="a4d56-160">***txm_module_manager_file_load. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="a4d56-161">Allokerar och läser in en fil för en binär modul i minnesmodulens minnes området och förbereder den för körning.</span><span class="sxs-lookup"><span data-stu-id="a4d56-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="a4d56-162">***txm_module_manager_in_place_load. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="a4d56-163">Allokerar modulens data områden och förbereder för att köra modulen från den angivna kod adressen.</span><span class="sxs-lookup"><span data-stu-id="a4d56-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="a4d56-164">***txm_module_manager_initialize. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="a4d56-165">Initierar modul hanteraren, inklusive specifikation av modulens minnes området som är tillgängligt för att läsa in och köra moduler.</span><span class="sxs-lookup"><span data-stu-id="a4d56-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="a4d56-166">\***txm_module_manager_initialize_mmu. c** _</span><span class="sxs-lookup"><span data-stu-id="a4d56-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="a4d56-167">Initiera MMU.</span><span class="sxs-lookup"><span data-stu-id="a4d56-167">Initialize MMU.</span></span> <span data-ttu-id="a4d56-168">Användare kan redigera den här filen enligt minnes kartan.</span><span class="sxs-lookup"><span data-stu-id="a4d56-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="a4d56-169">_This-filen finns bara i cortex-A7/ARM \*</span><span class="sxs-lookup"><span data-stu-id="a4d56-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="a4d56-170">\***txm_module_manager_mm_initialize. c** _</span><span class="sxs-lookup"><span data-stu-id="a4d56-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="a4d56-171">Initiera MPU/MMU.</span><span class="sxs-lookup"><span data-stu-id="a4d56-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="a4d56-172">Användare kan redigera den här filen enligt minnes kartan.</span><span class="sxs-lookup"><span data-stu-id="a4d56-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="a4d56-173">_This-filen finns bara i cortex-A7/ARM \*</span><span class="sxs-lookup"><span data-stu-id="a4d56-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="a4d56-174">***txm_module_manager_kernel_dispatch. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="a4d56-175">Hanterar API-begäranden baserat på ID för begäran.</span><span class="sxs-lookup"><span data-stu-id="a4d56-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="a4d56-176">***txm_module_manager_maximum_module_priority_set. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="a4d56-177">Anger högsta tillåtna tråd prioritet i en modul.</span><span class="sxs-lookup"><span data-stu-id="a4d56-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="a4d56-178">***txm_module_manager_memory_fault_handler. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="a4d56-179">Hanterar minnes fel som identifierats i en modul som körs.</span><span class="sxs-lookup"><span data-stu-id="a4d56-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="a4d56-180">***txm_module_manager_memory_fault_notify. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="a4d56-181">Registrerar ett återanrop för program meddelanden när ett minnes fel inträffar.</span><span class="sxs-lookup"><span data-stu-id="a4d56-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="a4d56-182">***txm_module_manager_memory_load. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="a4d56-183">Allokerar och läser in modulens kod och data och förbereder modulen för körning.</span><span class="sxs-lookup"><span data-stu-id="a4d56-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="a4d56-184">***txm_module_manager_mm_register_setup. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="a4d56-185">Ställer in MPU/MMU-register för modulen baserat på var koden och data läses in.</span><span class="sxs-lookup"><span data-stu-id="a4d56-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="a4d56-186">***txm_module_manager_object_allocate. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="a4d56-187">Allokerar minne för ett module-objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d56-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="a4d56-188">***txm_module_manager_object_deallocate. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="a4d56-189">Frigör minne för ett modul objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d56-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="a4d56-190">***txm_module_manager_object_pointer_get. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="a4d56-191">Söker efter angiven objekt typ och namn, och returnerar objekt pekaren om den hittas.</span><span class="sxs-lookup"><span data-stu-id="a4d56-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="a4d56-192">***txm_module_manager_object_pointer_get_extended. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="a4d56-193">Söker efter angiven objekt typ och namn, och returnerar objekt pekaren om den hittas.</span><span class="sxs-lookup"><span data-stu-id="a4d56-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="a4d56-194">Namn längd som angetts för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="a4d56-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="a4d56-195">***txm_module_manager_object_pool_create. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="a4d56-196">Skapar en pool av objekt utanför modulens data områden som module-program kan allokera från.</span><span class="sxs-lookup"><span data-stu-id="a4d56-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="a4d56-197">***txm_module_manager_properties_get. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="a4d56-198">Hämtar egenskaperna för den angivna modulen.</span><span class="sxs-lookup"><span data-stu-id="a4d56-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="a4d56-199">***txm_module_manager_queue_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="a4d56-200">Bearbetar köns meddelande anropet från ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="a4d56-201">***txm_module_manager_semaphore_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="a4d56-202">Bearbetar meddelandet om semafors meddelande anropet från ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="a4d56-203">***txm_module_manager_start. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="a4d56-204">Startar körning av en modul.</span><span class="sxs-lookup"><span data-stu-id="a4d56-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="a4d56-205">***txm_module_manager_stop. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="a4d56-206">Stoppar körningen av en modul.</span><span class="sxs-lookup"><span data-stu-id="a4d56-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="a4d56-207">***txm_module_manager_thread_create. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="a4d56-208">Skapar alla-modul-trådar.</span><span class="sxs-lookup"><span data-stu-id="a4d56-208">Creates all module threads.</span></span> |
| <span data-ttu-id="a4d56-209">***txm_module_manager_thread_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="a4d56-210">Bearbetar anropet för tråd-och avslutnings meddelande från ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="a4d56-211">***txm_module_manager_thread_reset. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="a4d56-212">Återställ en modul tråd.</span><span class="sxs-lookup"><span data-stu-id="a4d56-212">Reset a module thread.</span></span> |
| <span data-ttu-id="a4d56-213">***txm_module_manager_timer_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="a4d56-214">Förfaller av processer från ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a4d56-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="a4d56-215">***txm_module_manager_unload. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="a4d56-216">Laddar bort modulen från modulens minnes yta.</span><span class="sxs-lookup"><span data-stu-id="a4d56-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="a4d56-217">***txm_module_manager_util. c***</span><span class="sxs-lookup"><span data-stu-id="a4d56-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="a4d56-218">Interna hjälp funktioner för Manager.</span><span class="sxs-lookup"><span data-stu-id="a4d56-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="a4d56-219">Initiering av modul Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-219">Module Manager initialization</span></span>

<span data-ttu-id="a4d56-220">Den inhemska delen av programmet ansvarar för att anropa modul hanterarens initierings funktion ***txm_module_manager_initialize***.</span><span class="sxs-lookup"><span data-stu-id="a4d56-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="a4d56-221">Den här funktionen konfigurerar de interna strukturerna för att läsa in och ta bort moduler, inklusive konfiguration av det minnes området som används för att allokera minnesmodulens minne.</span><span class="sxs-lookup"><span data-stu-id="a4d56-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="a4d56-222">Inläsning av modul Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-222">Module Manager loading</span></span>

<span data-ttu-id="a4d56-223">Module Manager kan läsa in moduler dynamiskt i modulens minne från binärfiler för binärfiler eller från ett modul kods avsnitt som redan finns i det inhemska kod området.</span><span class="sxs-lookup"><span data-stu-id="a4d56-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="a4d56-224">Dessutom kan module Manager köra kod på plats, det vill säga att endast modulens data allokeras i minnesmodulen och att kod körningen görs på plats.</span><span class="sxs-lookup"><span data-stu-id="a4d56-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="a4d56-225">Följande inläsnings-API-funktioner i module Manager är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="a4d56-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="a4d56-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="a4d56-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="a4d56-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="a4d56-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="a4d56-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="a4d56-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="a4d56-229">Den minnes säkra versionen av module Manager ser också till att modulen läses in med rätt justering och minnes hanterings registren konfigureras korrekt för varje modul.</span><span class="sxs-lookup"><span data-stu-id="a4d56-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="a4d56-230">När minnes skydd aktive ras via modulen inlednings alternativ, är minnesmodulens minnes åtkomst begränsad till modulens kod och data områden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="a4d56-231">Module Manager startar</span><span class="sxs-lookup"><span data-stu-id="a4d56-231">Module Manager starting</span></span>

<span data-ttu-id="a4d56-232">Modul hanteraren initierar körning av en tidigare inläst modul via ***txm_module_manager_start*** API-funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4d56-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="a4d56-233">Den här funktionen skapar en tråd som går in i modulen på den Start plats som anges i modulen inledning för att initiera modul körning.</span><span class="sxs-lookup"><span data-stu-id="a4d56-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="a4d56-234">Trådens prioritet och stack storlek anges också i modulen inledning.</span><span class="sxs-lookup"><span data-stu-id="a4d56-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="a4d56-235">Stänger av module Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-235">Module Manager stopping</span></span>

<span data-ttu-id="a4d56-236">Module Manager avslutar körningen av en modul som har lästs in och körs via funktionen ***txm_module_manager_stop*** .</span><span class="sxs-lookup"><span data-stu-id="a4d56-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="a4d56-237">Den här API-funktionen avslutar först och tar bort den första start tråden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="a4d56-238">Om modulen inledning anger en stopp tråd skapas och körs den här tråden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="a4d56-239">Module Manager väntar under en bestämd tids period då stopp tråden ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="a4d56-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="a4d56-240">När du är klar tas alla system resurser som skapats av modulen bort och modulen placeras i ett inaktivt tillstånd, från vilken den kan startas om eller tas bort från minnet.</span><span class="sxs-lookup"><span data-stu-id="a4d56-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="a4d56-241">Borttagning av modul Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-241">Module Manager unloading</span></span>

<span data-ttu-id="a4d56-242">Module Manager inaktiverar en tidigare inläst men inte exekverande modul via funktionen ***txm_module_manager_unload*** .</span><span class="sxs-lookup"><span data-stu-id="a4d56-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="a4d56-243">Detta API frigör allt minne som är associerat med modulen och frigör det för användning med en annan modul i framtiden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="a4d56-244">Module Manager-begäranden</span><span class="sxs-lookup"><span data-stu-id="a4d56-244">Module Manager requests</span></span>

<span data-ttu-id="a4d56-245">Begär Anden som görs av moduler till modul Manager utförs via makron i ***txm_module. h*** som mappar alla ThreadX-anrop för att anropa modul hanterarens sändnings funktion via en funktions pekare som tillhandahålls till modulen av modul Manager.</span><span class="sxs-lookup"><span data-stu-id="a4d56-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="a4d56-246">Ytterligare programspecifika tjänster som görs via modulen anropar ***txm_module_application_request*** hanteras av samma makro mekanism som används för ThreadX-API: et.</span><span class="sxs-lookup"><span data-stu-id="a4d56-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="a4d56-247">Som standard är den här hanterings funktionen i modul Manager Tom och utformad så att programmet lägger till den nödvändiga koden för att bearbeta programspecifika begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="a4d56-248">Om begäran inte implementeras av module Manager returneras ett värde för **TX_NOT_AVAILABLE** fel status av modul Manager.</span><span class="sxs-lookup"><span data-stu-id="a4d56-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="a4d56-249">Den här felkoden returneras även om modulen begär en åtgärd som ligger utanför omfånget för modulens åtkomst.</span><span class="sxs-lookup"><span data-stu-id="a4d56-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="a4d56-250">En modul kan till exempel inte skapa en timer med timer-kontrollens block eller återanrops adress utanför modulens kod områden.</span><span class="sxs-lookup"><span data-stu-id="a4d56-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="a4d56-251">Exempel på modul hanteraren</span><span class="sxs-lookup"><span data-stu-id="a4d56-251">Module Manager example</span></span>

<span data-ttu-id="a4d56-252">Följande är ett exempel på en modul Manager-kod som startar exempel-modulen som definierades tidigare i kapitel 2.</span><span class="sxs-lookup"><span data-stu-id="a4d56-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="a4d56-253">Det förutsätts att modulen redan har lästs in, antagen av fel söknings programmet, i ROM-0x00800000.</span><span class="sxs-lookup"><span data-stu-id="a4d56-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

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

## <a name="module-manager-building"></a><span data-ttu-id="a4d56-254">Skapa modul Manager</span><span class="sxs-lookup"><span data-stu-id="a4d56-254">Module Manager building</span></span>

<span data-ttu-id="a4d56-255">***Txm_module_manager_ \**** källfiler måste läggas till i ThreadX-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="a4d56-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="a4d56-256">Ett ThreadX module Manager-program är i praktiken detsamma som ett standard program för ThreadX, vilket är en eller flera programfiler som är länkade tillsammans med ThreadX-biblioteket ***TX. a***.</span><span class="sxs-lookup"><span data-stu-id="a4d56-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="a4d56-257">Att skapa en modul Manager-applikation är beroende av den verktygs kedja som används.</span><span class="sxs-lookup"><span data-stu-id="a4d56-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="a4d56-258">Se [tillägg](appendix.md) för port-/regionsspecifika exempel.</span><span class="sxs-lookup"><span data-stu-id="a4d56-258">See [appendix](appendix.md) for port-specific examples.</span></span>
