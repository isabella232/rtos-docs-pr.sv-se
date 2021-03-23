---
title: Kapitel 2 – modulens krav
description: Den här artikeln beskriver kraven för att bygga en ThreadX-modul.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32288d78ceffb74ab088a1d720dbac657f6d3ed4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825494"
---
# <a name="chapter-2---module-requirements"></a><span data-ttu-id="87e83-103">Kapitel 2 – modulens krav</span><span class="sxs-lookup"><span data-stu-id="87e83-103">Chapter 2 - Module requirements</span></span>

<span data-ttu-id="87e83-104">En ThreadX-modul innehåller en inledning som definierar modulens grundläggande egenskaper.</span><span class="sxs-lookup"><span data-stu-id="87e83-104">A ThreadX Module contains a preamble, which defines the basic characteristics of the module.</span></span> <span data-ttu-id="87e83-105">Inledningen följs av instruktions avsnittet i modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-105">The preamble is followed by the instruction area of the module.</span></span> <span data-ttu-id="87e83-106">Moduler kan köras på plats eller kan läsas in i modulens minnes området av modul hanteraren innan körningen.</span><span class="sxs-lookup"><span data-stu-id="87e83-106">Modules may be executed in place or they may be loaded into the module memory area by the Module Manager prior to execution.</span></span> <span data-ttu-id="87e83-107">Det enda kravet är att inledningen alltid finns i den första adressen i modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-107">The only requirement is that the preamble is always located at the first address of the module.</span></span> <span data-ttu-id="87e83-108">Bild 2 visar en grundläggande modulens layout.</span><span class="sxs-lookup"><span data-stu-id="87e83-108">Figure 2 illustrates a basic module layout.</span></span>

| <span data-ttu-id="87e83-109">Modulens layout</span><span class="sxs-lookup"><span data-stu-id="87e83-109">Module Layout</span></span> |
|:---:|
| <span data-ttu-id="87e83-110">\[modul, inledning\]</span><span class="sxs-lookup"><span data-stu-id="87e83-110">\[module preamble\]</span></span>         |
| <span data-ttu-id="87e83-111">\[modulens instruktions områden\]</span><span class="sxs-lookup"><span data-stu-id="87e83-111">\[module instruction area\]</span></span> |
| <span data-ttu-id="87e83-112">\[modul RAM-yta\]</span><span class="sxs-lookup"><span data-stu-id="87e83-112">\[module RAM area\]</span></span>         |

<span data-ttu-id="87e83-113">**Bild 2** – modulens layout</span><span class="sxs-lookup"><span data-stu-id="87e83-113">**Figure 2** - Module Layout</span></span>

> [!NOTE]
> <span data-ttu-id="87e83-114">Modulerna måste vara skapade med lämpliga placerings oberoende kod-och data kompilator/länknings alternativ.</span><span class="sxs-lookup"><span data-stu-id="87e83-114">Modules must be built with the appropriate position independent code and data compiler/linker options.</span></span> <span data-ttu-id="87e83-115">Detta aktiverar körning av modulen i alla minnes områden.</span><span class="sxs-lookup"><span data-stu-id="87e83-115">This enables execution of the module in any memory area.</span></span>

<span data-ttu-id="87e83-116">När en modulreferens skapas allokeras ett andra stack utrymme för användning när tråden är i den minnesbaserade kerneln.</span><span class="sxs-lookup"><span data-stu-id="87e83-116">When a Module thread is created, a second stack space is allocated for use when the thread is in the memory-protected kernel.</span></span> <span data-ttu-id="87e83-117">Storleken på trådens kernel stack-utrymme kan konfigureras av användaren med hjälp av **TXM_MODULE_KERNEL_STACK_SIZE** i **_txm_module_port. h_*_. På så sätt kan du använda en mindre stack storlek när du skapar en modulreferens, eftersom stacken som anges av användaren när du anropar _*_tx_thread_create_** endast används i modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-117">The size of the thread's kernel stack space is user-configurable using **TXM_MODULE_KERNEL_STACK_SIZE** in **_txm_module_port.h_*_. This allows a smaller stack size to be used when creating a Module thread, as the stack specified by the user when calling _*_tx_thread_create_** is only used in the module.</span></span>

> [!NOTE]
> <span data-ttu-id="87e83-118">Den översta delen i en modul tråds tack innehåller information strukturen för tråd posten (**TXM_MODULE_THREAD_ENTRY_INFO**), så den tillgängliga stack storleken minskas med storleken på den här strukturen.</span><span class="sxs-lookup"><span data-stu-id="87e83-118">The top of a module thread stack contains the thread entry information structure (**TXM_MODULE_THREAD_ENTRY_INFO**), so the available stack size is decreased by the size of this structure.</span></span> <span data-ttu-id="87e83-119">När du skapar en tråd i en modul ökar du dess stack storlek genom att minst den här strukturen.</span><span class="sxs-lookup"><span data-stu-id="87e83-119">When creating a thread in a module, increase its stack size by at least this the size of this structure.</span></span>

<span data-ttu-id="87e83-120">Följande steg krävs för att skapa och skapa en ThreadX-modul (varje steg beskrivs mer detaljerat nedan).</span><span class="sxs-lookup"><span data-stu-id="87e83-120">The following steps are required for creating and building a ThreadX Module (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="87e83-121">Alla C-filer i en modul måste #define **TXM_MODULE** innan du kan ta med **_txm_module. h_**.</span><span class="sxs-lookup"><span data-stu-id="87e83-121">All C files in a module must #define **TXM_MODULE** prior to including **_txm_module.h_**.</span></span> <span data-ttu-id="87e83-122">Detta kan utföras i käll filen som kompileras eller som en del av projekt inställningarna.</span><span class="sxs-lookup"><span data-stu-id="87e83-122">This can be accomplished in the source file being compiled or as part of the project settings.</span></span> <span data-ttu-id="87e83-123">Om du gör det omavbildas ThreadX-API-anrop till den modul-specifika versionen av API: et som anropar funktionen Dispatch i den inhemska modulen Manager för att utföra anropet till den faktiska API-funktionen.</span><span class="sxs-lookup"><span data-stu-id="87e83-123">Doing so remaps the ThreadX API calls to the module-specific version of the API that invokes the dispatch function in the resident Module Manager to perform the call to the actual API function.</span></span>
2. <span data-ttu-id="87e83-124">Varje modul måste ha en inledning i den första instruktions delens adress som definierar egenskaperna och resurs behoven för modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-124">Each module must have a preamble at its first instruction area address which defines the characteristics and the resource needs of the module.</span></span>
3. <span data-ttu-id="87e83-125">Varje modul måste länka inledningen i början av modulens instruktions områden.</span><span class="sxs-lookup"><span data-stu-id="87e83-125">Each module must link the preamble at the beginning of the module instruction area.</span></span>
4. <span data-ttu-id="87e83-126">Varje modul måste länka till ett-modul bibliotek (***TXM. a***), som innehåller moduler-/regionsspecifika funktioner som används för att interagera med ThreadX.</span><span class="sxs-lookup"><span data-stu-id="87e83-126">Each module must link against a module library (***txm.a***), which contains module-specific functions used to interact with ThreadX.</span></span>

## <a name="module-sources"></a><span data-ttu-id="87e83-127">Modul källor</span><span class="sxs-lookup"><span data-stu-id="87e83-127">Module sources</span></span>

<span data-ttu-id="87e83-128">ThreadX-moduler har en egen uppsättning källfiler som är utformade för att länkas och placeras direkt med modulens käll kod.</span><span class="sxs-lookup"><span data-stu-id="87e83-128">ThreadX Modules have their own set of source files that are designed to be linked and located directly with the module source code.</span></span> <span data-ttu-id="87e83-129">Dessa filer tillhandahåller bryggan mellan den separata modulen och den inhemska modul hanteraren.</span><span class="sxs-lookup"><span data-stu-id="87e83-129">These files provide the bridge between the separate module and resident Module Manager.</span></span> <span data-ttu-id="87e83-130">Filerna är följande.</span><span class="sxs-lookup"><span data-stu-id="87e83-130">The Module files are as follows.</span></span>

| <span data-ttu-id="87e83-131">Filnamn</span><span class="sxs-lookup"><span data-stu-id="87e83-131">File Name</span></span> | <span data-ttu-id="87e83-132">Innehåll</span><span class="sxs-lookup"><span data-stu-id="87e83-132">Contents</span></span> |
|---|---|
| <span data-ttu-id="87e83-133">**txm_module. h**</span><span class="sxs-lookup"><span data-stu-id="87e83-133">**txm_module.h**</span></span> | <span data-ttu-id="87e83-134">Inkludera en fil som definierar information om moduler.</span><span class="sxs-lookup"><span data-stu-id="87e83-134">Include file that defines module information.</span></span> |
| <span data-ttu-id="87e83-135">**txm_module_port. h**</span><span class="sxs-lookup"><span data-stu-id="87e83-135">**txm_module_port.h**</span></span> | <span data-ttu-id="87e83-136">Inkludera en fil som definierar information om portbaserad moduler.</span><span class="sxs-lookup"><span data-stu-id="87e83-136">Include file that defines port-specific module information.</span></span> |
| <span data-ttu-id="87e83-137">**txm_module_user. h**</span><span class="sxs-lookup"><span data-stu-id="87e83-137">**txm_module_user.h**</span></span> | <span data-ttu-id="87e83-138">Definierar och värden som användaren kan anpassa.</span><span class="sxs-lookup"><span data-stu-id="87e83-138">Defines and values the user can customize.</span></span> |
| <span data-ttu-id="87e83-139">**txm_module_initialize. s [1] [3]**</span><span class="sxs-lookup"><span data-stu-id="87e83-139">**txm_module_initialize.s [1][3]**</span></span> | <span data-ttu-id="87e83-140">Anropar inbyggda funktioner i startup-modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-140">Calls intrinsic functions to startup module.</span></span> |
| <span data-ttu-id="87e83-141">**txm_module_preamble. \{ s/S/68\}**</span><span class="sxs-lookup"><span data-stu-id="87e83-141">**txm_module_preamble.\{s/S/68\}**</span></span> | <span data-ttu-id="87e83-142">Sammansättnings fil för modul inledning.</span><span class="sxs-lookup"><span data-stu-id="87e83-142">Module preamble assembly file.</span></span> <span data-ttu-id="87e83-143">Den här filen definierar olika platsspecifika attribut och är länkade till modulens program kod.</span><span class="sxs-lookup"><span data-stu-id="87e83-143">This file defines various module-specific attributes and is linked with the module application code.</span></span> |
| <span data-ttu-id="87e83-144">**txm_module_application_request. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-144">**txm_module_application_request.c [1]**</span></span> | <span data-ttu-id="87e83-145">Funktionen module Application Request skickar en programspecifik begäran till den inhemska koden.</span><span class="sxs-lookup"><span data-stu-id="87e83-145">Module application request function sends an application-specific request to the resident code.</span></span> |
| <span data-ttu-id="87e83-146">**txm_module_callback_request_thread_entry. c &nbsp; [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-146">**txm_module_callback_request_thread_entry.c&nbsp;[1]**</span></span> | <span data-ttu-id="87e83-147">Återanrops tråd för modul som ansvarar för bearbetning av återanrop som begärts av modulen, inklusive timers och timers och återanrop till meddelanden.</span><span class="sxs-lookup"><span data-stu-id="87e83-147">Module callback thread that is responsible for processing callbacks requested by the module, including timers and notification callbacks.</span></span> |
| <span data-ttu-id="87e83-148">\**txm_ *. c [1] [2]**</span><span class="sxs-lookup"><span data-stu-id="87e83-148">**txm_\*.c [1][2]**</span></span> | <span data-ttu-id="87e83-149">Standard-API-tjänsterna i ThreadX anropar kernel dispatcher.</span><span class="sxs-lookup"><span data-stu-id="87e83-149">The standard ThreadX API services, these call the kernel dispatcher.</span></span>
| <span data-ttu-id="87e83-150">**txm_module_object_allocate. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-150">**txm_module_object_allocate.c [1]**</span></span> | <span data-ttu-id="87e83-151">Module-funktion för att allokera minne för modul-objekt som finns i Manager-lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="87e83-151">Module function to allocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="87e83-152">**txm_module_object_deallocate. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-152">**txm_module_object_deallocate.c [1]**</span></span> | <span data-ttu-id="87e83-153">Modul funktion för att frigöra minne för modul objekt som finns i Manager-lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="87e83-153">Module function to deallocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="87e83-154">**txm_module_object_pointer_get. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-154">**txm_module_object_pointer_get.c [1]**</span></span> | <span data-ttu-id="87e83-155">Module funktion för att hämta en pekare till ett system objekt.</span><span class="sxs-lookup"><span data-stu-id="87e83-155">Module function to retrieve a pointer to a system object.</span></span> |
| <span data-ttu-id="87e83-156">**txm_module_object_pointer_get_extended. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-156">**txm_module_object_pointer_get_extended.c [1]**</span></span> | <span data-ttu-id="87e83-157">Module funktion för att hämta en pekare till ett system objekt, namn längds säkerhet.</span><span class="sxs-lookup"><span data-stu-id="87e83-157">Module function to retrieve a pointer to a system object, name length safety.</span></span> |
| <span data-ttu-id="87e83-158">**txm_module_thread_shell_entry. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-158">**txm_module_thread_shell_entry.c [1]**</span></span> | <span data-ttu-id="87e83-159">Funktionen för tråd inmatning i modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-159">Module thread entry function.</span></span> |
| <span data-ttu-id="87e83-160">**txm_module_thread_system_suspend. c [1]**</span><span class="sxs-lookup"><span data-stu-id="87e83-160">**txm_module_thread_system_suspend.c [1]**</span></span> | <span data-ttu-id="87e83-161">Module funktion för att pausa en tråd.</span><span class="sxs-lookup"><span data-stu-id="87e83-161">Module function to suspend a thread.</span></span> |

<span data-ttu-id="87e83-162">**[1]** finns i biblioteket **_TXM. a_**.</span><span class="sxs-lookup"><span data-stu-id="87e83-162">**[1]** Located in library **_txm.a_**.</span></span>

<span data-ttu-id="87e83-163">**[2]** de här filerna har samma namn som THREADX-API-filerna, med **txm_** prefix i stället för **TX_** prefix.</span><span class="sxs-lookup"><span data-stu-id="87e83-163">**[2]** These files have the same name as the ThreadX API files, with **txm_** prefix instead of **tx_** prefix.</span></span>

<span data-ttu-id="87e83-164">**[3]** filen **txm_module_initialize. s** är bara för portar som använder arm-verktyg.</span><span class="sxs-lookup"><span data-stu-id="87e83-164">**[3]** The **txm_module_initialize.s** file is only for ports using ARM tools.</span></span>

## <a name="module-preamble"></a><span data-ttu-id="87e83-165">Modul, inledning</span><span class="sxs-lookup"><span data-stu-id="87e83-165">Module preamble</span></span>

<span data-ttu-id="87e83-166">I modulen inledning definieras egenskaper och resurser för modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-166">The Module Preamble defines characteristics and resources of the module.</span></span> <span data-ttu-id="87e83-167">Information som den första tråd inmatnings funktionen och det första minnes området som är kopplat till tråden definieras i inledningen.</span><span class="sxs-lookup"><span data-stu-id="87e83-167">Information such as the initial thread entry function and the initial memory area associated with the thread are defined in the preamble.</span></span> <span data-ttu-id="87e83-168">Port-/regionsspecifika inlednings exempel finns i [bilagan](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="87e83-168">Port-specific preamble examples are in the [appendix](appendix.md).</span></span> <span data-ttu-id="87e83-169">Bild 3 visar ett exempel på ThreadX module för ett allmänt mål (raderna som börjar med \* är värden som vanligt vis ändras av programmet):</span><span class="sxs-lookup"><span data-stu-id="87e83-169">Figure 3 shows an example ThreadX module preamble for a generic target (the lines starting with \* are values typically modified by the application):</span></span>

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

<span data-ttu-id="87e83-170">**Bild 3**</span><span class="sxs-lookup"><span data-stu-id="87e83-170">**Figure 3**</span></span>

<span data-ttu-id="87e83-171">I de flesta fall behöver utvecklaren bara definiera modulens start tråd (offset 0x1C), modul-ID (offset-0x10), starta/stoppa tråd prioritet (förskjutning 0x24) och starta/stoppa trådens stack storlek (förskjutning 0x28).</span><span class="sxs-lookup"><span data-stu-id="87e83-171">In most cases, the developer only needs to define the module's starting thread (offset 0x1C), module ID (offset 0x10), start/stop thread priority (offset 0x24), and start/stop thread stack size (offset 0x28).</span></span> <span data-ttu-id="87e83-172">Demonstrationen ovan är inställd så att den första tråden i modulen är ***demo_module_start** _, modul-ID: t är _*_0x12345678_*_ och start tråden har prioritet _*_1_*_ och en stack storlek på _ *_2048_** byte.</span><span class="sxs-lookup"><span data-stu-id="87e83-172">The demonstration above is set up such that the starting thread of the module is ***demo_module_start** _, the module ID is _*_0x12345678_*_, and the starting thread has a priority of _*_1_*_, and a stack size of _ *_2048_** bytes.</span></span>

<span data-ttu-id="87e83-173">Vissa program kan eventuellt definiera en stoppad tråd, som körs när module Manager stoppar modulen.</span><span class="sxs-lookup"><span data-stu-id="87e83-173">Some applications may optionally define a stopping thread, which is executed as the Module Manager stops the module.</span></span> <span data-ttu-id="87e83-174">Dessutom kan vissa program använda fältet modul egenskaper, som definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="87e83-174">In addition, some applications might utilize the Module Properties field, defined as follows.</span></span>

## <a name="module-properties-bit-map"></a><span data-ttu-id="87e83-175">BITS-mappning för modul egenskaper</span><span class="sxs-lookup"><span data-stu-id="87e83-175">Module properties bit map</span></span>

<span data-ttu-id="87e83-176">I tabellen nedan visas ett exempel på en egenskaps-bitars karta.</span><span class="sxs-lookup"><span data-stu-id="87e83-176">The table below shows an example of the properties bit map.</span></span> <span data-ttu-id="87e83-177">Bitmappar för portbaserad egenskaper finns i [bilagan](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="87e83-177">Port-specific properties bitmaps are in the [appendix](appendix.md).</span></span>

| <span data-ttu-id="87e83-178">Bitmask</span><span class="sxs-lookup"><span data-stu-id="87e83-178">Bit</span></span> | <span data-ttu-id="87e83-179">Värde</span><span class="sxs-lookup"><span data-stu-id="87e83-179">Value</span></span> | <span data-ttu-id="87e83-180">Innebörd</span><span class="sxs-lookup"><span data-stu-id="87e83-180">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="87e83-181">0</span><span class="sxs-lookup"><span data-stu-id="87e83-181">0</span></span> | <span data-ttu-id="87e83-182">0</span><span class="sxs-lookup"><span data-stu-id="87e83-182">0</span></span><br /><span data-ttu-id="87e83-183">1</span><span class="sxs-lookup"><span data-stu-id="87e83-183">1</span></span> | <span data-ttu-id="87e83-184">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="87e83-184">Privileged mode execution</span></span><br /><span data-ttu-id="87e83-185">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="87e83-185">User mode execution</span></span> |
| <span data-ttu-id="87e83-186">1</span><span class="sxs-lookup"><span data-stu-id="87e83-186">1</span></span> | <span data-ttu-id="87e83-187">0</span><span class="sxs-lookup"><span data-stu-id="87e83-187">0</span></span><br /><span data-ttu-id="87e83-188">1</span><span class="sxs-lookup"><span data-stu-id="87e83-188">1</span></span> | <span data-ttu-id="87e83-189">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="87e83-189">No MPU protection</span></span><br /><span data-ttu-id="87e83-190">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="87e83-190">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="87e83-191">2</span><span class="sxs-lookup"><span data-stu-id="87e83-191">2</span></span> | <span data-ttu-id="87e83-192">0</span><span class="sxs-lookup"><span data-stu-id="87e83-192">0</span></span><br /><span data-ttu-id="87e83-193">1</span><span class="sxs-lookup"><span data-stu-id="87e83-193">1</span></span> | <span data-ttu-id="87e83-194">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="87e83-194">Disable shared/external memory access</span></span><br /><span data-ttu-id="87e83-195">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="87e83-195">Enable shared/external memory access</span></span> |
| <span data-ttu-id="87e83-196">[23-3]</span><span class="sxs-lookup"><span data-stu-id="87e83-196">[23-3]</span></span> | <span data-ttu-id="87e83-197">0</span><span class="sxs-lookup"><span data-stu-id="87e83-197">0</span></span> | <span data-ttu-id="87e83-198">Reserverat</span><span class="sxs-lookup"><span data-stu-id="87e83-198">Reserved</span></span>
| <span data-ttu-id="87e83-199">[31-24]</span><span class="sxs-lookup"><span data-stu-id="87e83-199">[31-24]</span></span> | <br /><span data-ttu-id="87e83-200">0x01</span><span class="sxs-lookup"><span data-stu-id="87e83-200">0x01</span></span><br /><span data-ttu-id="87e83-201">0x02</span><span class="sxs-lookup"><span data-stu-id="87e83-201">0x02</span></span><br /><span data-ttu-id="87e83-202">0x03</span><span class="sxs-lookup"><span data-stu-id="87e83-202">0x03</span></span> | <span data-ttu-id="87e83-203">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="87e83-203">**Compiler ID**</span></span><br /><span data-ttu-id="87e83-204">IAR</span><span class="sxs-lookup"><span data-stu-id="87e83-204">IAR</span></span><br /><span data-ttu-id="87e83-205">ARM</span><span class="sxs-lookup"><span data-stu-id="87e83-205">ARM</span></span><br /><span data-ttu-id="87e83-206">GNU</span><span class="sxs-lookup"><span data-stu-id="87e83-206">GNU</span></span> |


## <a name="module-linker-control-file"></a><span data-ttu-id="87e83-207">Kontroll fil för modul länkar</span><span class="sxs-lookup"><span data-stu-id="87e83-207">Module linker control file</span></span>

<span data-ttu-id="87e83-208">När du skapar en modul måste modulens inledning placeras före andra kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="87e83-208">When building a module, the module preamble must be placed before any other code section.</span></span> <span data-ttu-id="87e83-209">En modul måste ha skapats med positions oberoende kod och data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="87e83-209">A module must be built with position-independent code and data sections.</span></span> <span data-ttu-id="87e83-210">Port-/regionsspecifika exempel länkar filer finns i [bilagan](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="87e83-210">Port-specific example linker files are in the [appendix](appendix.md).</span></span>

## <a name="module-threadx-library"></a><span data-ttu-id="87e83-211">Modul ThreadX-bibliotek</span><span class="sxs-lookup"><span data-stu-id="87e83-211">Module ThreadX library</span></span>

<span data-ttu-id="87e83-212">Varje modul måste länka till ett särskilt, modulbaserade ThreadX-bibliotek.</span><span class="sxs-lookup"><span data-stu-id="87e83-212">Each module must link against a special, module-centric ThreadX library.</span></span> <span data-ttu-id="87e83-213">Det här biblioteket ger åtkomst till ThreadX-tjänster i den inhemska koden.</span><span class="sxs-lookup"><span data-stu-id="87e83-213">This library provides access to ThreadX services in the resident code.</span></span> <span data-ttu-id="87e83-214">Det mesta av åtkomsten görs via ***txm_ \* . c*** -filerna.</span><span class="sxs-lookup"><span data-stu-id="87e83-214">Most of the access is accomplished via the ***txm_\*.c*** files.</span></span> <span data-ttu-id="87e83-215">Följande är ett exempel på anropet till modulen för API-funktionen ThreadX **_tx_thread_relinquish_* _ (i _*_ \_ txm_thread_relinquish. c \* \* \* \* \*).</span><span class="sxs-lookup"><span data-stu-id="87e83-215">The following is an example of the module access call for the ThreadX API function **_tx_thread_relinquish_* _ (in _*_\_txm_thread_relinquish.c\*\*\*\*).</span></span>

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

<span data-ttu-id="87e83-216">I det här exemplet används funktions pekaren som tillhandahållits av module Manager för att anropa modulen för hantering av modul Manager med det ID som är kopplat till tjänsten ***tx_thread_relinquish*** .</span><span class="sxs-lookup"><span data-stu-id="87e83-216">In this example, the function pointer supplied by the Module Manager is used to call the Module Manager dispatch function with the ID associated with the ***tx_thread_relinquish*** service.</span></span> <span data-ttu-id="87e83-217">Den här tjänsten tar inga parametrar.</span><span class="sxs-lookup"><span data-stu-id="87e83-217">This service takes no parameters.</span></span>

## <a name="module-example"></a><span data-ttu-id="87e83-218">Modul-exempel</span><span class="sxs-lookup"><span data-stu-id="87e83-218">Module example</span></span>

<span data-ttu-id="87e83-219">Följande är ett exempel på standard demonstrationen av ThreadX i form av en modul.</span><span class="sxs-lookup"><span data-stu-id="87e83-219">The following is an example of the standard ThreadX demonstration in the form of a module.</span></span> <span data-ttu-id="87e83-220">De viktigaste skillnaderna mellan standard demonstrationen av ThreadX och demonstrationen av modulen är.</span><span class="sxs-lookup"><span data-stu-id="87e83-220">The main differences between the standard ThreadX demonstration and the module demonstration are.</span></span>

1. <span data-ttu-id="87e83-221">Ersätter ***tx_api. h** _ med _ *_txm_module. h_**</span><span class="sxs-lookup"><span data-stu-id="87e83-221">Replacement of ***tx_api.h** _ with _ *_txm_module.h_**</span></span>
2. <span data-ttu-id="87e83-222">Tillägg av **#define TXM_MODULE** innan **_txm_module. h_**</span><span class="sxs-lookup"><span data-stu-id="87e83-222">Addition of **#define TXM_MODULE** prior to **_txm_module.h_**</span></span>
3. <span data-ttu-id="87e83-223">Ersättning av ***main** _ och _ *tx_application_define** med **_demo_module_start_**</span><span class="sxs-lookup"><span data-stu-id="87e83-223">Replacement of ***main** _ and _ *tx_application_define** with **_demo_module_start_**</span></span>
4. <span data-ttu-id="87e83-224">Deklarera *pekare* till ThreadX-objekt i stället för själva objekten.</span><span class="sxs-lookup"><span data-stu-id="87e83-224">Declaring *pointers* to ThreadX objects rather than the objects themselves.</span></span>

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

## <a name="building-modules"></a><span data-ttu-id="87e83-225">Skapa moduler</span><span class="sxs-lookup"><span data-stu-id="87e83-225">Building Modules</span></span>

<span data-ttu-id="87e83-226">Att skapa en modul är beroende av den verktygs kedja som används.</span><span class="sxs-lookup"><span data-stu-id="87e83-226">Building a module is dependent on the tool chain being used.</span></span> <span data-ttu-id="87e83-227">Se [tillägg](appendix.md) för port-/regionsspecifika exempel.</span><span class="sxs-lookup"><span data-stu-id="87e83-227">See [appendix](appendix.md) for port-specific examples.</span></span> <span data-ttu-id="87e83-228">Vanliga aktiviteter för alla portar är följande.</span><span class="sxs-lookup"><span data-stu-id="87e83-228">Common activities to all ports include the following.</span></span>

- <span data-ttu-id="87e83-229">Skapa ett modul bibliotek</span><span class="sxs-lookup"><span data-stu-id="87e83-229">Building a module library</span></span>
- <span data-ttu-id="87e83-230">Skapa modulens program</span><span class="sxs-lookup"><span data-stu-id="87e83-230">Building the module application</span></span>

<span data-ttu-id="87e83-231">Varje modul måste ha en **txm_module_preamble** (installationen är särskilt för modulen) och modul biblioteket (till exempel **_TXM. a_**).</span><span class="sxs-lookup"><span data-stu-id="87e83-231">Each module is required to have a **txm_module_preamble** (setup specifically for the module) and the module library (for example, **_txm.a_**).</span></span>
