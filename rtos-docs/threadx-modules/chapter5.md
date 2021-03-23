---
title: 'Kapitel 5 – modul Manager-API: er'
author: philmea
description: 'Den här artikeln är en sammanfattning av modul Manager-API: er som är tillgängliga för den inhemska delen av programmet.'
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825485"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="33e07-103">Kapitel 5 – modul Manager-API: er</span><span class="sxs-lookup"><span data-stu-id="33e07-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="33e07-104">Översikt över API: er för modul Manager</span><span class="sxs-lookup"><span data-stu-id="33e07-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="33e07-105">Det finns flera ytterligare API: er som är tillgängliga för den inhemska delen av programmet, enligt följande.</span><span class="sxs-lookup"><span data-stu-id="33e07-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="33e07-106">\***txm_module_manager_external_memory_enable** _-_Enable module-åtkomst till ett delat minnes utrymme \*</span><span class="sxs-lookup"><span data-stu-id="33e07-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="33e07-107">\***txm_module_manager_file_load** _-_Load modul från fil via FileX \*</span><span class="sxs-lookup"><span data-stu-id="33e07-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="33e07-108">\***txm_module_manager_in_place_load** _-_Load modul data, kör på plats \*</span><span class="sxs-lookup"><span data-stu-id="33e07-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="33e07-109">\***txm_module_manager_initialize** _-_Initialize modul Manager \*</span><span class="sxs-lookup"><span data-stu-id="33e07-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="33e07-110">\***txm_module_manager_mm_initialize** _-_Initialize minnes hanterings maskin varan \*</span><span class="sxs-lookup"><span data-stu-id="33e07-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="33e07-111">\***txm_module_manager_maximum_module_priority_set** _-_Set högsta tråd prioritet som tillåts i en modul \*</span><span class="sxs-lookup"><span data-stu-id="33e07-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="33e07-112">\***txm_module_manager_memory_fault_notify** _-_Register ett program motanrop vid minnes fel \*</span><span class="sxs-lookup"><span data-stu-id="33e07-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="33e07-113">\***txm_module_manager_memory_load** _-_Load modulen från minnet \*</span><span class="sxs-lookup"><span data-stu-id="33e07-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="33e07-114">\***txm_module_manager_object_pool_create** _-_Create en datapool för moduler \*</span><span class="sxs-lookup"><span data-stu-id="33e07-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="33e07-115">\***txm_module_manager_properties_get** _-_Get modul egenskaper \*</span><span class="sxs-lookup"><span data-stu-id="33e07-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="33e07-116">\***txm_module_manager_start** _-_Start körning av den angivna modulen \*</span><span class="sxs-lookup"><span data-stu-id="33e07-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="33e07-117">\***txm_module_manager_stop** _-_Stop körning av den angivna modulen \*</span><span class="sxs-lookup"><span data-stu-id="33e07-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="33e07-118">\***txm_module_manager_unload** _-_Unload modulen \*</span><span class="sxs-lookup"><span data-stu-id="33e07-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="33e07-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="33e07-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="33e07-120">Aktivera modul för att få åtkomst till ett delat minnes utrymme.</span><span class="sxs-lookup"><span data-stu-id="33e07-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-121">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="33e07-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-122">Description</span></span>

<span data-ttu-id="33e07-123">Den här tjänsten skapar en post i maskin varu tabellen för minnes hantering för en delad minnes region som modulen har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="33e07-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-124">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-124">Input parameters</span></span>

- <span data-ttu-id="33e07-125">**module_instance** Pekar till instansen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="33e07-126">**start_address** Start adress till den delade minnes regionen.</span><span class="sxs-lookup"><span data-stu-id="33e07-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="33e07-127">**längd** Längd på det delade minnets region.</span><span class="sxs-lookup"><span data-stu-id="33e07-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="33e07-128">**attribut** Attribut för minnes region (cache, läsa, skriva osv.).</span><span class="sxs-lookup"><span data-stu-id="33e07-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="33e07-129">Attribut är port-/regionsspecifika; Se [bilaga](appendix.md) för attribut format.</span><span class="sxs-lookup"><span data-stu-id="33e07-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-130">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-130">Return values</span></span>

- <span data-ttu-id="33e07-131">Minnes posten **TX_SUCCESS** (0x00) har skapats.</span><span class="sxs-lookup"><span data-stu-id="33e07-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="33e07-132">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats eller är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="33e07-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="33e07-133">**TX_PTR_ERROR** (0X03) ogiltig module-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="33e07-134">**TX_START_ERROR** -modulen (0x10) är inte i inläst läge.</span><span class="sxs-lookup"><span data-stu-id="33e07-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="33e07-135">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering av start adress.</span><span class="sxs-lookup"><span data-stu-id="33e07-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="33e07-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33e07-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-137">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-137">Allowed from</span></span>

<span data-ttu-id="33e07-138">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-139">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="33e07-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="33e07-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="33e07-141">Läs in modul från fil via FileX.</span><span class="sxs-lookup"><span data-stu-id="33e07-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-142">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="33e07-143">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-143">Description</span></span>

<span data-ttu-id="33e07-144">Den här tjänsten läser in den binära avbildningen av modulen som finns i den angivna filen i modulens minnes området och förbereder den för körning.</span><span class="sxs-lookup"><span data-stu-id="33e07-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="33e07-145">Det förutsätts att det angivna mediet redan är öppet.</span><span class="sxs-lookup"><span data-stu-id="33e07-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="33e07-146">FileX-systemet använder för att läsa in filen.</span><span class="sxs-lookup"><span data-stu-id="33e07-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="33e07-147">För att kunna aktivera FileX-åtkomst måste modulen, modulens bibliotek, modul Manager och ThreadX-biblioteket (med modul Manager-källor) skapas med **FX_FILEX_PRESENT** som definierats i projekten.</span><span class="sxs-lookup"><span data-stu-id="33e07-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-148">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-148">Input parameters</span></span>

- <span data-ttu-id="33e07-149">**module_instance** Pekar till instansen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="33e07-150">**module_name** Namn på modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="33e07-151">**media_ptr** Pekare till redan öppnade FileX-medier.</span><span class="sxs-lookup"><span data-stu-id="33e07-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="33e07-152">**file_name** Namnet på modulens binära fil.</span><span class="sxs-lookup"><span data-stu-id="33e07-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-153">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-153">Return values</span></span>

- <span data-ttu-id="33e07-154">**TX_SUCCESS** (0X00) lyckad inläsning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="33e07-155">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="33e07-156">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-157">**TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne för att läsa in modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="33e07-158">**TX_NOT_DONE** (0X20) mediet är inte öppet, filen hittades inte eller så är filen ogiltig.</span><span class="sxs-lookup"><span data-stu-id="33e07-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="33e07-159">**TX_PTR_ERROR** (0X03) ogiltig modul pekare.</span><span class="sxs-lookup"><span data-stu-id="33e07-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="33e07-160">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering.</span><span class="sxs-lookup"><span data-stu-id="33e07-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="33e07-161">Modulen **TXM_MODULE_ALREADY_LOADED** (0xF1) har redan lästs in.</span><span class="sxs-lookup"><span data-stu-id="33e07-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="33e07-162">**TXM_MODULE_INVALID** (0xF2) | Ogiltig inledning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="33e07-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33e07-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-164">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-164">Allowed from</span></span>

<span data-ttu-id="33e07-165">Konversation</span><span class="sxs-lookup"><span data-stu-id="33e07-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-166">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="33e07-167">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-167">See also</span></span>

- <span data-ttu-id="33e07-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="33e07-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="33e07-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="33e07-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="33e07-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="33e07-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="33e07-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="33e07-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="33e07-172">Läs endast in modul data, kör modul på en befintlig plats.</span><span class="sxs-lookup"><span data-stu-id="33e07-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="33e07-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-174">Description</span></span>

<span data-ttu-id="33e07-175">Den här tjänsten läser bara in modulens data områden i modulens minnes området och förbereder den för körning.</span><span class="sxs-lookup"><span data-stu-id="33e07-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="33e07-176">Modulens kod körning är på plats, det vill säga från den adress förskjutning som anges av modulens inledning på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="33e07-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-177">Input parameters</span></span>

- <span data-ttu-id="33e07-178">**module_instance** Pekar till instansen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="33e07-179">**module_name** Namn på modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="33e07-180">**plats** Pekare till modulens kod områden, inledning först.</span><span class="sxs-lookup"><span data-stu-id="33e07-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-181">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-181">Return values</span></span>

- <span data-ttu-id="33e07-182">**TX_SUCCESS** (0X00) lyckad inläsning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="33e07-183">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="33e07-184">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-185">**TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne för att läsa in modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="33e07-186">**TX_PTR_ERROR** (0X03) ogiltig pekare, modul instans eller inledning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="33e07-187">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering.</span><span class="sxs-lookup"><span data-stu-id="33e07-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="33e07-188">Modulen **TXM_MODULE_ALREADY_LOADED** (0xF1) har redan lästs in.</span><span class="sxs-lookup"><span data-stu-id="33e07-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="33e07-189">**TXM_MODULE_INVALID** (0XF2) ogiltig inledning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="33e07-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33e07-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-191">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-191">Allowed from</span></span>

<span data-ttu-id="33e07-192">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-193">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="33e07-194">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-194">See also</span></span>

- <span data-ttu-id="33e07-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="33e07-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="33e07-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="33e07-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="33e07-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="33e07-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="33e07-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="33e07-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="33e07-199">Initiera modul Manager.</span><span class="sxs-lookup"><span data-stu-id="33e07-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="33e07-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-201">Description</span></span>

<span data-ttu-id="33e07-202">Den här tjänsten initierar modul hanterarens interna resurser, inklusive det minnes utrymme som används för att läsa in moduler.</span><span class="sxs-lookup"><span data-stu-id="33e07-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-203">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-203">Input parameters</span></span>

- <span data-ttu-id="33e07-204">**module_memory_start** Pekar till start av modulens minne.</span><span class="sxs-lookup"><span data-stu-id="33e07-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="33e07-205">**module_memory_size** Storlek i byte för modulens minne.</span><span class="sxs-lookup"><span data-stu-id="33e07-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-206">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-206">Return values</span></span>

- <span data-ttu-id="33e07-207">**TX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="33e07-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="33e07-208">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-209">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-209">Allowed from</span></span>

<span data-ttu-id="33e07-210">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-211">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="33e07-212">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-212">See also</span></span>

- <span data-ttu-id="33e07-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="33e07-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="33e07-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="33e07-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="33e07-215">Initiera maskin varan för minnes hantering.</span><span class="sxs-lookup"><span data-stu-id="33e07-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-216">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="33e07-217">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-217">Description</span></span>

<span data-ttu-id="33e07-218">Den här tjänsten initierar MMU.</span><span class="sxs-lookup"><span data-stu-id="33e07-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-219">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-219">Input parameters</span></span>

<span data-ttu-id="33e07-220">inget</span><span class="sxs-lookup"><span data-stu-id="33e07-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-221">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-221">Return values</span></span>

- <span data-ttu-id="33e07-222">**TX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="33e07-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="33e07-223">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-224">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-224">Allowed from</span></span>

<span data-ttu-id="33e07-225">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-226">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="33e07-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="33e07-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="33e07-228">Ange högsta tillåtna tråd prioritet i en modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-229">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="33e07-230">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-230">Description</span></span>

<span data-ttu-id="33e07-231">Den här tjänsten anger den maximala tråd prioriteten som tillåts i en modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-232">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-232">Input parameters</span></span>

- <span data-ttu-id="33e07-233">**module_instance** Pekar till instansen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="33e07-234">**prioritet** Högsta tråd prioritet.</span><span class="sxs-lookup"><span data-stu-id="33e07-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-235">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-235">Return values</span></span>

- <span data-ttu-id="33e07-236">**TX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="33e07-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="33e07-237">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-238">**TX_PTR_ERROR** (0X03) ogiltig module-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="33e07-239">**TX_START_ERROR** -modulen (0x10) är inte i inläst läge.</span><span class="sxs-lookup"><span data-stu-id="33e07-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-240">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-240">Allowed from</span></span>

<span data-ttu-id="33e07-241">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-242">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="33e07-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="33e07-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="33e07-244">Registrera ett program återanrop vid minnes fel.</span><span class="sxs-lookup"><span data-stu-id="33e07-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-245">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="33e07-246">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-246">Description</span></span>

<span data-ttu-id="33e07-247">Den här tjänsten registrerar den angivna funktionen för motringning av program minnes fel med modul Manager.</span><span class="sxs-lookup"><span data-stu-id="33e07-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="33e07-248">Om ett minnes fel inträffar anropas funktionen med en pekare till den felaktiga tråden och den modul som motsvarar den felaktiga tråden.</span><span class="sxs-lookup"><span data-stu-id="33e07-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="33e07-249">Bearbetningen av den felaktiga tråden avbryts automatiskt av module Manager, men andra trådar i modulen lämnas orörda.</span><span class="sxs-lookup"><span data-stu-id="33e07-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="33e07-250">Det är upp till programmet att bestämma vad som ska göras med den modul som är kopplad till minnes felet.</span><span class="sxs-lookup"><span data-stu-id="33e07-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="33e07-251">Du hittar mer information om själva minnes felet i den interna **_txm_module_manager_memory_fault_info** strukturer.</span><span class="sxs-lookup"><span data-stu-id="33e07-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="33e07-252">Funktionen för motanrop för minnes fel körs direkt från minnes Fels undantaget, så endast ThreadX-API: er som tillåts från avbrott i tjänst rutinen kan anropas.</span><span class="sxs-lookup"><span data-stu-id="33e07-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="33e07-253">För att stoppa och ta bort den felaktiga modulen måste program meddelande återanropet skicka en signal till en program aktivitet så att modulen kan stoppas och tas bort från minnet.</span><span class="sxs-lookup"><span data-stu-id="33e07-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-254">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-254">Input parameters</span></span>

- <span data-ttu-id="33e07-255">**notify_function** Funktions pekare till programmets återanrop för minnes Fels meddelanden.</span><span class="sxs-lookup"><span data-stu-id="33e07-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="33e07-256">Om du anger ett NULL-värde inaktive ras minnes Fels aviseringen.</span><span class="sxs-lookup"><span data-stu-id="33e07-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-257">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-257">Return values</span></span>

- <span data-ttu-id="33e07-258">**TX_SUCCESS** (0x00) registreringen av aviserings funktionen lyckades.</span><span class="sxs-lookup"><span data-stu-id="33e07-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-259">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-259">Allowed from</span></span>

<span data-ttu-id="33e07-260">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-261">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="33e07-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="33e07-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="33e07-263">Läsa in modulen från minnet.</span><span class="sxs-lookup"><span data-stu-id="33e07-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-264">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="33e07-265">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-265">Description</span></span>

<span data-ttu-id="33e07-266">Den här tjänsten läser in modulens kod och data i modulens minnes området som har ställts in av ***txm_module_manager_initialize*** och förbereder den för körning.</span><span class="sxs-lookup"><span data-stu-id="33e07-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-267">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-267">Input parameters</span></span>

- <span data-ttu-id="33e07-268">**module_instance** Pekar till instansen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="33e07-269">**module_name** Namn på modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="33e07-270">**plats** Pekare till modulens kod områden, inledning först.</span><span class="sxs-lookup"><span data-stu-id="33e07-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-271">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-271">Return values</span></span>

- <span data-ttu-id="33e07-272">**TX_SUCCESS** (0X00) lyckad inläsning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="33e07-273">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="33e07-274">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-275">**TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne för att läsa in modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="33e07-276">**TX_PTR_ERROR** (0X03) ogiltig pekare, modul instans eller inledning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="33e07-277">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) ogiltig justering.</span><span class="sxs-lookup"><span data-stu-id="33e07-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="33e07-278">Modulen **TXM_MODULE_ALREADY_LOADED** (0xF1) har redan lästs in.</span><span class="sxs-lookup"><span data-stu-id="33e07-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="33e07-279">**TXM_MODULE_INVALID** (0XF2) ogiltig inledning av modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="33e07-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) inkompatibla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33e07-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-281">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-281">Allowed from</span></span>

<span data-ttu-id="33e07-282">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-283">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="33e07-284">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-284">See also</span></span>

- <span data-ttu-id="33e07-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="33e07-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="33e07-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="33e07-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="33e07-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="33e07-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="33e07-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="33e07-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="33e07-289">Skapa en datapool för moduler.</span><span class="sxs-lookup"><span data-stu-id="33e07-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-290">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="33e07-291">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-291">Description</span></span>

<span data-ttu-id="33e07-292">Den här tjänsten skapar en pool för modul hanterarens objekt som modulerna kan använda för att allokera ThreadX/NetX-objekt från, och därmed behålla systemobjektet från modulens minnes yta.</span><span class="sxs-lookup"><span data-stu-id="33e07-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-293">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-293">Input parameters</span></span>

- <span data-ttu-id="33e07-294">**pool_memory_start** Pekar mot start av objekt minnet.</span><span class="sxs-lookup"><span data-stu-id="33e07-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="33e07-295">**pool_memory_size** Storlek i byte för objektets minnes uppsättning.</span><span class="sxs-lookup"><span data-stu-id="33e07-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-296">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-296">Return values</span></span>

- <span data-ttu-id="33e07-297">**TX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="33e07-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="33e07-298">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-299">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-299">Allowed from</span></span>

<span data-ttu-id="33e07-300">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-301">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="33e07-302">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-302">See also</span></span>

- <span data-ttu-id="33e07-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="33e07-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="33e07-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="33e07-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="33e07-305">Hämta egenskaper för modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-306">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="33e07-307">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-307">Description</span></span>

<span data-ttu-id="33e07-308">Den här tjänsten returnerar egenskaperna (anges i ingressen) för en modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-309">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-309">Input parameters</span></span>

- <span data-ttu-id="33e07-310">**module_instance** Pekare till module-instansen.</span><span class="sxs-lookup"><span data-stu-id="33e07-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="33e07-311">**module_properties_ptr** Pekare till målet för modulens egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33e07-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-312">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-312">Return values</span></span>

- <span data-ttu-id="33e07-313">**TX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="33e07-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="33e07-314">**TX_PTR_ERROR** (0X03) ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="33e07-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="33e07-315">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-316">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-316">Allowed from</span></span>

<span data-ttu-id="33e07-317">Konversation</span><span class="sxs-lookup"><span data-stu-id="33e07-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-318">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="33e07-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="33e07-319">txm_module_manager_start</span></span>

<span data-ttu-id="33e07-320">Starta körningen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-321">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="33e07-322">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-322">Description</span></span>

<span data-ttu-id="33e07-323">Den här tjänsten startar körningen av angiven, redan inläst modul.</span><span class="sxs-lookup"><span data-stu-id="33e07-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-324">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-324">Input parameters</span></span>

- <span data-ttu-id="33e07-325">**module_instance** Pekare till tidigare inläst modul-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-326">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-326">Return values</span></span>

- <span data-ttu-id="33e07-327">**TX_SUCCESS** (0X00) lyckad modul startades.</span><span class="sxs-lookup"><span data-stu-id="33e07-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="33e07-328">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="33e07-329">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-330">**TX_PTR_ERROR** (0X03) ogiltig pekar-eller module-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="33e07-331">Modulen **TX_START_ERROR** (0x10) har redan startats.</span><span class="sxs-lookup"><span data-stu-id="33e07-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-332">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-332">Allowed from</span></span>

<span data-ttu-id="33e07-333">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-334">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="33e07-335">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-335">See also</span></span>

- <span data-ttu-id="33e07-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="33e07-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="33e07-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="33e07-337">txm_module_manager_stop</span></span>

<span data-ttu-id="33e07-338">Stoppa körningen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-339">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="33e07-340">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-340">Description</span></span>

<span data-ttu-id="33e07-341">Den här tjänsten stoppar en modul som tidigare har lästs in och startats.</span><span class="sxs-lookup"><span data-stu-id="33e07-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="33e07-342">Att stoppa en modul inkluderar att köra modulens valfria Stop-tråd, avsluta alla trådar och ta bort alla resurser som är kopplade till modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-343">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-343">Input parameters</span></span>

- <span data-ttu-id="33e07-344">**module_instance** Pekare till modul-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-345">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-345">Return values</span></span>

- <span data-ttu-id="33e07-346">**TX_SUCCESS** (0X00) lyckad modul stoppa.</span><span class="sxs-lookup"><span data-stu-id="33e07-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="33e07-347">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="33e07-348">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-349">**TX_PTR_ERROR** (0X03) ogiltig pekar-eller module-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="33e07-350">Modulen **TX_START_ERROR** (0x10) startades inte.</span><span class="sxs-lookup"><span data-stu-id="33e07-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-351">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-351">Allowed from</span></span>

<span data-ttu-id="33e07-352">Konversation</span><span class="sxs-lookup"><span data-stu-id="33e07-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-353">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="33e07-354">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-354">See also</span></span>

- <span data-ttu-id="33e07-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="33e07-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="33e07-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="33e07-356">txm_module_manager_unload</span></span>

<span data-ttu-id="33e07-357">Ta bort modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="33e07-358">Prototyp</span><span class="sxs-lookup"><span data-stu-id="33e07-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="33e07-359">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33e07-359">Description</span></span>

<span data-ttu-id="33e07-360">Den här tjänsten inaktiverar den tidigare inlästa och stoppade modulen, vilket frigör alla associerade minnes resurser för modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="33e07-361">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="33e07-361">Input parameters</span></span>

- <span data-ttu-id="33e07-362">**module_instance** Pekar till instansen av modulen.</span><span class="sxs-lookup"><span data-stu-id="33e07-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="33e07-363">Returvärden</span><span class="sxs-lookup"><span data-stu-id="33e07-363">Return values</span></span>

- <span data-ttu-id="33e07-364">**TX_SUCCESS** 0x00) modulen har tagits bort från minnet.</span><span class="sxs-lookup"><span data-stu-id="33e07-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="33e07-365">**TX_CALLER_ERROR** (0X13) ogiltig anropare.</span><span class="sxs-lookup"><span data-stu-id="33e07-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="33e07-366">**TX_NOT_AVAILABLE** (0X1D) hanteraren har inte initierats.</span><span class="sxs-lookup"><span data-stu-id="33e07-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="33e07-367">**TX_NOT_DONE** (0X20) ogiltig modul eller modul stoppades inte.</span><span class="sxs-lookup"><span data-stu-id="33e07-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="33e07-368">**TX_PTR_ERROR** (0X03) ogiltig pekar-eller module-instans.</span><span class="sxs-lookup"><span data-stu-id="33e07-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="33e07-369">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="33e07-369">Allowed from</span></span>

<span data-ttu-id="33e07-370">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="33e07-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="33e07-371">Exempel</span><span class="sxs-lookup"><span data-stu-id="33e07-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="33e07-372">Se även</span><span class="sxs-lookup"><span data-stu-id="33e07-372">See also</span></span>

- <span data-ttu-id="33e07-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="33e07-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="33e07-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="33e07-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="33e07-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="33e07-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="33e07-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="33e07-376">txm_module_manager_stop</span></span>
