---
title: 'Kapitel 3 – ThreadX-API: er för ARMv8-M'
description: Det här kapitlet beskriver en beskrivning av ARMv8-M-Specific ThreadX-tjänsterna.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377630"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="fa795-103">Kapitel 3 ThreadX-API: er för ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="fa795-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="fa795-104">Det här kapitlet innehåller en beskrivning av ARMv8-M-Specific ThreadX-tjänsterna i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="fa795-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="fa795-105">Deras namn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="fa795-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="fa795-106">I avsnittet "retur värden" i följande beskrivningar påverkas inte värden i **fetstil** av **TX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-kontrollen. värden som visas i icke-fetstil är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="fa795-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="fa795-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allokera en tråds tack i säkert minne.</span><span class="sxs-lookup"><span data-stu-id="fa795-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="fa795-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Fri tråds tack i säkert minne</span><span class="sxs-lookup"><span data-stu-id="fa795-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="fa795-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="fa795-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="fa795-110">Allokera en tråds tack i säkert minne.</span><span class="sxs-lookup"><span data-stu-id="fa795-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa795-111">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fa795-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="fa795-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fa795-112">Description</span></span>

<span data-ttu-id="fa795-113">Den här tjänsten allokerar en stack med storlek stack_size byte i säkert minne.</span><span class="sxs-lookup"><span data-stu-id="fa795-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="fa795-114">Den här funktionen ska anropas för varje tråd som anropar säkra funktioner.</span><span class="sxs-lookup"><span data-stu-id="fa795-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fa795-115">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fa795-115">Input Parameters</span></span>

- <span data-ttu-id="fa795-116">**thread_ptr** Pekare till den tidigare skapade tråden.</span><span class="sxs-lookup"><span data-stu-id="fa795-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="fa795-117">**stack_size** Storlek på säker stack.</span><span class="sxs-lookup"><span data-stu-id="fa795-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa795-118">Retur värden</span><span class="sxs-lookup"><span data-stu-id="fa795-118">Return Values</span></span>

- <span data-ttu-id="fa795-119">**TX_SUCCESS** (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="fa795-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="fa795-120">**TX_SIZE_ERRORs** stackens storlek (0x05) är utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="fa795-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="fa795-121">**TX_THREAD_ERROR** (0X0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="fa795-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="fa795-122">**TX_NO_MEMORY** (0X10) Det gick inte att allokera minne.</span><span class="sxs-lookup"><span data-stu-id="fa795-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="fa795-123">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fa795-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="fa795-124">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades för att köras i säkert läge.</span><span class="sxs-lookup"><span data-stu-id="fa795-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fa795-125">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="fa795-125">Allowed From</span></span>

<span data-ttu-id="fa795-126">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="fa795-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="fa795-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="fa795-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="fa795-128">Se även</span><span class="sxs-lookup"><span data-stu-id="fa795-128">See Also</span></span>

<span data-ttu-id="fa795-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="fa795-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="fa795-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="fa795-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="fa795-131">Frigör en tråds tack i säkert minne.</span><span class="sxs-lookup"><span data-stu-id="fa795-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="fa795-132">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fa795-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="fa795-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fa795-133">Description</span></span>

<span data-ttu-id="fa795-134">Den här tjänsten frigör en tråds säkra stack i säkert minne.</span><span class="sxs-lookup"><span data-stu-id="fa795-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="fa795-135">Den här funktionen ska anropas om en tråd har en säker stack och när tråden inte längre behöver anropa säkra funktioner eller om tråden tas bort.</span><span class="sxs-lookup"><span data-stu-id="fa795-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fa795-136">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fa795-136">Input Parameters</span></span>

- <span data-ttu-id="fa795-137">**thread_ptr** Pekare till den tidigare skapade tråden.</span><span class="sxs-lookup"><span data-stu-id="fa795-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa795-138">Retur värden</span><span class="sxs-lookup"><span data-stu-id="fa795-138">Return Values</span></span>

- <span data-ttu-id="fa795-139">**TX_SUCCESS** (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="fa795-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="fa795-140">**TX_THREAD_ERROR** (0X0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="fa795-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="fa795-141">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fa795-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="fa795-142">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades för att köras i säkert läge.</span><span class="sxs-lookup"><span data-stu-id="fa795-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fa795-143">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="fa795-143">Allowed From</span></span>

<span data-ttu-id="fa795-144">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="fa795-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="fa795-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="fa795-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="fa795-146">Se även</span><span class="sxs-lookup"><span data-stu-id="fa795-146">See Also</span></span>

<span data-ttu-id="fa795-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="fa795-147">tx_thread_secure_stack_allocate</span></span>
