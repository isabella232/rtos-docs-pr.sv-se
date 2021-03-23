---
title: Kapitel 4 – API för modul
author: philmea
ms.author: philmea
description: 'Den här artikeln är en sammanfattning av de ytterligare API: er som är tillgängliga för en modul.'
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825488"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="74152-103">Kapitel 4 – API för modul</span><span class="sxs-lookup"><span data-stu-id="74152-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="74152-104">Översikt över API: er för modul</span><span class="sxs-lookup"><span data-stu-id="74152-104">Summary of Module APIs</span></span>

<span data-ttu-id="74152-105">Det finns flera ytterligare API-funktioner som är tillgängliga för en modul enligt följande:</span><span class="sxs-lookup"><span data-stu-id="74152-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="74152-106">\***txm_module_application_request** _-_Application-speciell begäran till Resident kod \*</span><span class="sxs-lookup"><span data-stu-id="74152-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="74152-107">\***txm_module_object_allocate** _-_Allocate minne utanför modulen för objekt \*</span><span class="sxs-lookup"><span data-stu-id="74152-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="74152-108">\***txm_module_object_deallocate** _-_Deallocate tidigare allokerat objekt minne \*</span><span class="sxs-lookup"><span data-stu-id="74152-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="74152-109">\***txm_module_object_pointer_get** _-_Find system objekt och hämta objekt pekare \*</span><span class="sxs-lookup"><span data-stu-id="74152-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="74152-110">\***txm_module_object_pointer_get_extended** _-_Find system objekt och hämta objekt pekare, namn längd säkerhet \*</span><span class="sxs-lookup"><span data-stu-id="74152-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="74152-111">Returvärden</span><span class="sxs-lookup"><span data-stu-id="74152-111">Return values</span></span>

<span data-ttu-id="74152-112">Ytterligare fel koder returneras för vissa Azure återställnings tider-API: er.</span><span class="sxs-lookup"><span data-stu-id="74152-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="74152-113">Dessa ytterligare fel koder definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="74152-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="74152-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): visar att modulen inte har rätt egenskaper för att göra ett API-anrop.</span><span class="sxs-lookup"><span data-stu-id="74152-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="74152-115">Du kan till exempel anropa trace-API: er i användarläge.</span><span class="sxs-lookup"><span data-stu-id="74152-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="74152-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): anger att det minne som angavs av modulen är ogiltigt eller på en ogiltig plats.</span><span class="sxs-lookup"><span data-stu-id="74152-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="74152-117">Till exempel, i minnesmoduler som är skyddade, kan objekt kontroll block inte finnas i minnet som modulen har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="74152-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="74152-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): motringning som anges i API: t ligger utanför intervallet för modulens kod och är därför ogiltig.</span><span class="sxs-lookup"><span data-stu-id="74152-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="74152-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="74152-119">txm_module_application_request</span></span>

<span data-ttu-id="74152-120">Programspecifik begäran till Resident kod.</span><span class="sxs-lookup"><span data-stu-id="74152-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="74152-121">Prototyp</span><span class="sxs-lookup"><span data-stu-id="74152-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="74152-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74152-122">Description</span></span>

<span data-ttu-id="74152-123">Den här tjänsten gör den angivna begäran till den inhemska delen av programmet.</span><span class="sxs-lookup"><span data-stu-id="74152-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="74152-124">Det förutsätts att begär ande strukturen har förberetts före anropet.</span><span class="sxs-lookup"><span data-stu-id="74152-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="74152-125">Den faktiska bearbetningen av begäran sker i den inhemska koden i funktionen ***_txm_module_manager_application_request***.</span><span class="sxs-lookup"><span data-stu-id="74152-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="74152-126">Den här funktionen lämnas som standard Tom och är utformad för den inhemska programutvecklaren att ändra.</span><span class="sxs-lookup"><span data-stu-id="74152-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74152-127">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="74152-127">Input parameters</span></span>

- <span data-ttu-id="74152-128">**begäran** ID för begäran (program definierat)</span><span class="sxs-lookup"><span data-stu-id="74152-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="74152-129">**param_1** Första parametern</span><span class="sxs-lookup"><span data-stu-id="74152-129">**param_1** First parameter</span></span>
- <span data-ttu-id="74152-130">**param_2** Andra parameter</span><span class="sxs-lookup"><span data-stu-id="74152-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="74152-131">**param_3** Tredje parametern</span><span class="sxs-lookup"><span data-stu-id="74152-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="74152-132">Returvärden</span><span class="sxs-lookup"><span data-stu-id="74152-132">Return values</span></span>

- <span data-ttu-id="74152-133">**TX_SUCCESS** (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="74152-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="74152-134">**TX_NOT_AVAILABLE** -begäran (0x1D) stöds inte av den inhemska koden.</span><span class="sxs-lookup"><span data-stu-id="74152-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74152-135">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="74152-135">Allowed from</span></span>

<span data-ttu-id="74152-136">Modul-trådar</span><span class="sxs-lookup"><span data-stu-id="74152-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="74152-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="74152-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="74152-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="74152-138">txm_module_object_allocate</span></span>

<span data-ttu-id="74152-139">Allokera minne i objektcachen (som skapats av det inhemska programmet) för ett objekt kontroll block i modulen.</span><span class="sxs-lookup"><span data-stu-id="74152-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="74152-140">Prototyp</span><span class="sxs-lookup"><span data-stu-id="74152-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="74152-141">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74152-141">Description</span></span>

<span data-ttu-id="74152-142">Den här tjänsten allokerar minne för ett modul-objekt från minnet utanför modulen, vilket förhindrar att objekt kontroll blocket skadas av modulens kod.</span><span class="sxs-lookup"><span data-stu-id="74152-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="74152-143">I minnes skyddade system måste alla objekt kontroll block tilldelas med detta API innan de kan skapas.</span><span class="sxs-lookup"><span data-stu-id="74152-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74152-144">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="74152-144">Input parameters</span></span>

- <span data-ttu-id="74152-145">**object_ptr** Objekt pekarens mål för lyckad allokering.</span><span class="sxs-lookup"><span data-stu-id="74152-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="74152-146">**object_size** Storlek i byte på det objekt som ska allokeras.</span><span class="sxs-lookup"><span data-stu-id="74152-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="74152-147">Returvärden</span><span class="sxs-lookup"><span data-stu-id="74152-147">Return values</span></span>

- <span data-ttu-id="74152-148">**TX_SUCCESS** (0x00) objekt tilldelning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="74152-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="74152-149">**TX_NO_MEMORY** (0x10) det finns inte tillräckligt med minne.</span><span class="sxs-lookup"><span data-stu-id="74152-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="74152-150">**TX_NOT_AVAILABLE** (0X1D) module Manager har inte skapat en objektmall att allokera från</span><span class="sxs-lookup"><span data-stu-id="74152-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74152-151">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="74152-151">Allowed from</span></span>

<span data-ttu-id="74152-152">Modul-trådar</span><span class="sxs-lookup"><span data-stu-id="74152-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="74152-153">Exempel</span><span class="sxs-lookup"><span data-stu-id="74152-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="74152-154">Se även</span><span class="sxs-lookup"><span data-stu-id="74152-154">See also</span></span>

- <span data-ttu-id="74152-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="74152-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="74152-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="74152-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="74152-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="74152-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="74152-158">Frigör tidigare allokerat objekt minne</span><span class="sxs-lookup"><span data-stu-id="74152-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="74152-159">Prototyp</span><span class="sxs-lookup"><span data-stu-id="74152-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="74152-160">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74152-160">Description</span></span>

<span data-ttu-id="74152-161">***Den här tjänsten är inaktuell eftersom den inte längre behövs***.</span><span class="sxs-lookup"><span data-stu-id="74152-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="74152-162">Minnet som tidigare har allokerats via \*\*\*txm_module_object_allocate \**_ har* frigjorts i tjänsten _ _TX_ \_ _delete\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="74152-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74152-163">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="74152-163">Input parameters</span></span>

- <span data-ttu-id="74152-164">**object_ptr** Objekt pekare för att frigöra.</span><span class="sxs-lookup"><span data-stu-id="74152-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="74152-165">Returvärden</span><span class="sxs-lookup"><span data-stu-id="74152-165">Return values</span></span>

- <span data-ttu-id="74152-166">**TX_SUCCESS** (0x00) objekt tilldelning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="74152-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74152-167">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="74152-167">Allowed from</span></span>

<span data-ttu-id="74152-168">Modul-trådar</span><span class="sxs-lookup"><span data-stu-id="74152-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="74152-169">Exempel</span><span class="sxs-lookup"><span data-stu-id="74152-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="74152-170">Se även</span><span class="sxs-lookup"><span data-stu-id="74152-170">See also</span></span>

- <span data-ttu-id="74152-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="74152-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="74152-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="74152-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="74152-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="74152-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="74152-174">Hitta system objekt och hämta objekt pekare</span><span class="sxs-lookup"><span data-stu-id="74152-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="74152-175">Prototyp</span><span class="sxs-lookup"><span data-stu-id="74152-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="74152-176">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74152-176">Description</span></span>

<span data-ttu-id="74152-177">Den här tjänsten hämtar objekt pekaren för en viss typ med ett visst namn.</span><span class="sxs-lookup"><span data-stu-id="74152-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="74152-178">Om objektet inte hittas returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="74152-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="74152-179">Annars placeras adressen för objektet i "object_ptr", om objektet hittas.</span><span class="sxs-lookup"><span data-stu-id="74152-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="74152-180">Den här pekaren kan sedan användas för att göra system tjänst anrop, för att interagera med den inhemska koden och/eller andra inlästa moduler i systemet.</span><span class="sxs-lookup"><span data-stu-id="74152-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74152-181">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="74152-181">Input parameters</span></span>

- <span data-ttu-id="74152-182">**object_type** Typ av ThreadX-objekt som begärdes.</span><span class="sxs-lookup"><span data-stu-id="74152-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="74152-183">Giltiga typer är följande:</span><span class="sxs-lookup"><span data-stu-id="74152-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="74152-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="74152-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="74152-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="74152-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="74152-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="74152-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="74152-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="74152-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="74152-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="74152-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="74152-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="74152-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="74152-196">**namn** Programspecifikt objekt namn som definieras när objektet skapades.</span><span class="sxs-lookup"><span data-stu-id="74152-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="74152-197">**object_ptr** Mål för objekt pekare.</span><span class="sxs-lookup"><span data-stu-id="74152-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="74152-198">Returvärden</span><span class="sxs-lookup"><span data-stu-id="74152-198">Return values</span></span>

- <span data-ttu-id="74152-199">**TX_SUCCESS** (0x00) objekt hämtades.</span><span class="sxs-lookup"><span data-stu-id="74152-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="74152-200">**TX_OPTION_ERROR** (0X08) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="74152-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="74152-201">**TX_PTR_ERROR** (0X03) ogiltigt mål.</span><span class="sxs-lookup"><span data-stu-id="74152-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="74152-202">**TX_SIZE_ERROR** (0X05) ogiltig storlek.</span><span class="sxs-lookup"><span data-stu-id="74152-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="74152-203">Det gick inte att hitta **TX_NO_INSTANCE** -objektet (0x0D).</span><span class="sxs-lookup"><span data-stu-id="74152-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74152-204">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="74152-204">Allowed from</span></span>

<span data-ttu-id="74152-205">Modul-trådar</span><span class="sxs-lookup"><span data-stu-id="74152-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="74152-206">Exempel</span><span class="sxs-lookup"><span data-stu-id="74152-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="74152-207">Se även</span><span class="sxs-lookup"><span data-stu-id="74152-207">See also</span></span>

- <span data-ttu-id="74152-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="74152-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="74152-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="74152-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="74152-210">Hitta system objekt och hämta objekt pekare</span><span class="sxs-lookup"><span data-stu-id="74152-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="74152-211">Prototyp</span><span class="sxs-lookup"><span data-stu-id="74152-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="74152-212">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74152-212">Description</span></span>

<span data-ttu-id="74152-213">Den här tjänsten hämtar objekt pekaren för en viss typ med ett visst namn.</span><span class="sxs-lookup"><span data-stu-id="74152-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="74152-214">Om objektet inte hittas returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="74152-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="74152-215">Annars placeras adressen för objektet i "object_ptr", om objektet hittas.</span><span class="sxs-lookup"><span data-stu-id="74152-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="74152-216">Den här pekaren kan sedan användas för att göra system tjänst anrop, för att interagera med den inhemska koden och/eller andra inlästa moduler i systemet.</span><span class="sxs-lookup"><span data-stu-id="74152-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74152-217">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="74152-217">Input parameters</span></span>

- <span data-ttu-id="74152-218">**object_type** Typ av ThreadX-objekt som begärdes.</span><span class="sxs-lookup"><span data-stu-id="74152-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="74152-219">Giltiga typer är följande:</span><span class="sxs-lookup"><span data-stu-id="74152-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="74152-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="74152-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="74152-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="74152-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="74152-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="74152-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="74152-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="74152-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="74152-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="74152-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="74152-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="74152-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="74152-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="74152-232">**namn** Programspecifikt objekt namn som definieras när objektet skapades.</span><span class="sxs-lookup"><span data-stu-id="74152-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="74152-233">**name_length** Namnets längd.</span><span class="sxs-lookup"><span data-stu-id="74152-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="74152-234">**object_ptr** Mål för objekt pekare.</span><span class="sxs-lookup"><span data-stu-id="74152-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="74152-235">Returvärden</span><span class="sxs-lookup"><span data-stu-id="74152-235">Return values</span></span>

- <span data-ttu-id="74152-236">**TX_SUCCESS** (0x00) objekt hämtades.</span><span class="sxs-lookup"><span data-stu-id="74152-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="74152-237">**TX_OPTION_ERROR** (0X08) ogiltig objekt typ.</span><span class="sxs-lookup"><span data-stu-id="74152-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="74152-238">**TX_PTR_ERROR** (0X03) ogiltigt mål.</span><span class="sxs-lookup"><span data-stu-id="74152-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="74152-239">**TX_SIZE_ERROR** (0X05) ogiltig storlek.</span><span class="sxs-lookup"><span data-stu-id="74152-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="74152-240">Det gick inte att hitta **TX_NO_INSTANCE** -objektet (0x0D).</span><span class="sxs-lookup"><span data-stu-id="74152-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74152-241">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="74152-241">Allowed from</span></span>

<span data-ttu-id="74152-242">Modul-trådar</span><span class="sxs-lookup"><span data-stu-id="74152-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="74152-243">Exempel</span><span class="sxs-lookup"><span data-stu-id="74152-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="74152-244">Se även</span><span class="sxs-lookup"><span data-stu-id="74152-244">See also</span></span>

- <span data-ttu-id="74152-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="74152-245">txm_module_manager_object_pointer_get</span></span>
