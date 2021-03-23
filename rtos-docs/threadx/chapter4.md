---
title: Kapitel 4 – Beskrivning av Azure återställnings tider ThreadX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider ThreadX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825458"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="298ca-103">Kapitel 4 – Beskrivning av Azure återställnings tider ThreadX-tjänster</span><span class="sxs-lookup"><span data-stu-id="298ca-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="298ca-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider ThreadX-tjänster i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="298ca-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="298ca-105">Deras namn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="298ca-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="298ca-106">I avsnittet "retur värden" i följande beskrivningar påverkas inte värden i **fetstil** av **TX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-kontrollen. värden som visas i fet stil är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="298ca-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="298ca-107">Dessutom visar rubriken "**Ja**" som visas under rubriken "**avstängningen möjlig**" att anrop till tjänsten kan återuppta en tråd med högre prioritet, vilket innebär att den anropande tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="298ca-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-108">tx_block_allocate</span></span>

<span data-ttu-id="298ca-109">Allokera minnes block med fast storlek</span><span class="sxs-lookup"><span data-stu-id="298ca-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-110">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-111">Description</span></span>

<span data-ttu-id="298ca-112">Den här tjänsten allokerar ett minnes block med fast storlek från den angivna lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="298ca-113">Minnes blockets faktiska storlek bestäms när minnesbufferten skapas.</span><span class="sxs-lookup"><span data-stu-id="298ca-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-114">*Det är viktigt att se till att program koden inte skriver utanför det allokerade minnes blocket. Om detta inträffar inträffar skada i ett intilliggande (vanligt vis) minnes block. Resultatet är oförutsägbart och ofta allvarligt!*</span><span class="sxs-lookup"><span data-stu-id="298ca-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-115">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-115">Parameters</span></span>

- <span data-ttu-id="298ca-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-116">**pool_ptr**</span></span> <br><span data-ttu-id="298ca-117">Pekare till en tidigare skapad pool för minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="298ca-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-118">**block_ptr**</span></span> <br><span data-ttu-id="298ca-119">Pekare till en mål Blocks pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="298ca-120">Vid lyckad allokering placeras adressen till det allokerade minnes blocket där den här parametern pekar.</span><span class="sxs-lookup"><span data-stu-id="298ca-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="298ca-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-121">**wait_option**</span></span> <br><span data-ttu-id="298ca-122">Definierar hur tjänsten fungerar om det inte finns några tillgängliga minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="298ca-123">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-124">**TX_NO_WAIT** (0x00000000) – om du väljer **TX_NO_WAIT** resultaten i en omedelbar återgång från den här tjänsten, oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="298ca-125">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd, t. ex., initiering, timer eller ISR*.</span><span class="sxs-lookup"><span data-stu-id="298ca-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="298ca-126">**TX_WAIT_FOREVER** (0xFFFFFFF) – genom att välja **TX_WAIT_FOREVER** kan anrops tråden Pausa tills ett minnes block är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="298ca-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="298ca-127">*timeout-värde* (0X00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på ett minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-128">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-128">Return Values</span></span>

- <span data-ttu-id="298ca-129">**TX_SUCCESS**    (0X00) slutförde minnes Blocks tilldelning.</span><span class="sxs-lookup"><span data-stu-id="298ca-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="298ca-130">**TX_DELETED**    (0X01) minnes Blocks gruppen togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-131">Tjänsten **TX_NO_MEMORY** (0x10) kunde inte allokera ett minnes block inom den angivna tiden till väntan.</span><span class="sxs-lookup"><span data-stu-id="298ca-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="298ca-132">**TX_WAIT_ABORTED**   SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="298ca-133">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="298ca-134">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="298ca-135">**TX_PTR_ERROR**  (0X03) ogiltig pekare till mål pekaren.</span><span class="sxs-lookup"><span data-stu-id="298ca-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-136">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-136">Allowed From</span></span>

<span data-ttu-id="298ca-137">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-138">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-138">Preemption Possible</span></span>

<span data-ttu-id="298ca-139">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-140">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-140">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-141">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-141">See Also</span></span>

- <span data-ttu-id="298ca-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-142">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="298ca-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="298ca-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="298ca-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-149">tx_block_pool_create</span></span>

<span data-ttu-id="298ca-150">Skapa pool med minnes block med fast storlek</span><span class="sxs-lookup"><span data-stu-id="298ca-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="298ca-152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-152">Description</span></span>

<span data-ttu-id="298ca-153">Den här tjänsten skapar en pool med minnes block med fast storlek.</span><span class="sxs-lookup"><span data-stu-id="298ca-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="298ca-154">Det angivna minnes området är indelat i så många minnes block med fast storlek som möjligt med hjälp av formeln:</span><span class="sxs-lookup"><span data-stu-id="298ca-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="298ca-155">**Totalt antal block** = (**Totalt antal byte**)/(**block storlek** + sizeof (void \*))</span><span class="sxs-lookup"><span data-stu-id="298ca-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="298ca-156">\* Varje minnes block innehåller en pekare som är dold för användaren och representeras av "sizeof (void *)" i föregående formel.*</span><span class="sxs-lookup"><span data-stu-id="298ca-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-157">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-157">Parameters</span></span>

- <span data-ttu-id="298ca-158">**pool_ptr**  Pekar mot ett kontroll block för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="298ca-159">**name_ptr**  Pekar till namnet på minnes Blocks-poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="298ca-160">**block_size**    Antal byte i varje minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="298ca-161">**pool_start**    Start adress för minnes Blocks gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="298ca-162">Start adressen måste vara justerad till storleken på data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="298ca-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="298ca-163">**pool_size** Totalt antal byte som är tillgängliga för minnes block poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-164">Return Values</span></span>

- <span data-ttu-id="298ca-165">**TX_SUCCESS**    (0x00) Det gick inte att skapa en minnes Blocks samling.</span><span class="sxs-lookup"><span data-stu-id="298ca-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="298ca-166">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="298ca-167">Antingen är pekaren NULL eller också har poolen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="298ca-168">**TX_PTR_ERROR**  (0X03) ogiltig start adress för poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="298ca-169">**TX_CALLER_ERROR**   (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="298ca-170">**TX_SIZE_ERROR** (0X05) storleken på poolen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="298ca-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-171">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-171">Allowed From</span></span>

<span data-ttu-id="298ca-172">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-173">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-173">Preemption Possible</span></span>

<span data-ttu-id="298ca-174">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-174">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-175">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-175">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-176">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-176">See Also</span></span>

- <span data-ttu-id="298ca-177">tx_block_allocate tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-178">tx_block_pool_info_get tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-180">tx_block_pool_prioritize tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="298ca-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-181">tx_block_pool_delete</span></span>

<span data-ttu-id="298ca-182">Ta bort pool för minnes block</span><span class="sxs-lookup"><span data-stu-id="298ca-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-183">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-184">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-184">Description</span></span>

<span data-ttu-id="298ca-185">Den här tjänsten tar bort den angivna block minnes poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="298ca-186">Alla trådar som pausas i väntan på ett minnes block från den här poolen återupptas och får en **TX_DELETED** retur status.</span><span class="sxs-lookup"><span data-stu-id="298ca-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-187">*Det är programmets ansvar att hantera det minnes område som är associerat med poolen, vilket är tillgängligt när tjänsten har slutförts. Dessutom måste programmet förhindra att en borttagen pool eller de tidigare minnes blocken används.*</span><span class="sxs-lookup"><span data-stu-id="298ca-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-188">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-188">Parameters</span></span>

- <span data-ttu-id="298ca-189">**pool_ptr** Pekare till en tidigare skapad pool för minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-190">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-190">Return Values</span></span>

- <span data-ttu-id="298ca-191">**TX_SUCCESS** (0x00) en lyckad borttagning av minnes Blocks pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="298ca-192">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="298ca-193">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-194">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-194">Allowed From</span></span>

<span data-ttu-id="298ca-195">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-196">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-196">Preemption Possible</span></span>

<span data-ttu-id="298ca-197">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-198">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="298ca-199">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-199">See Also</span></span>

- <span data-ttu-id="298ca-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-200">tx_block_allocate</span></span>
- <span data-ttu-id="298ca-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-201">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-202">tx_block_pool_info_get tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-204">tx_block_pool_prioritize tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="298ca-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="298ca-206">Hämta information om blockera pool</span><span class="sxs-lookup"><span data-stu-id="298ca-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-207">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-207">Prototype</span></span>

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="298ca-208">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-208">Description</span></span>

<span data-ttu-id="298ca-209">Den här tjänsten hämtar information om den angivna block minnes poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-210">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-210">Parameters</span></span>

- <span data-ttu-id="298ca-211">**pool_ptr**  Pekare till tidigare skapat minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="298ca-212">**namn**  Pekare till målet för visaren i block poolens namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="298ca-213">**tillgänglig** Pekare till målet för antalet tillgängliga block i block poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="298ca-214">**total_blocks**  Pekare till målet för det totala antalet block i block poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="298ca-215">**first_suspended**   Pekare till målet för visaren i den tråd som är överst i listan över avbrytande av den här block poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="298ca-216">**suspended_count**   Pekare till målet för antalet trådar som för närvarande har pausats på den här block poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="298ca-217">**next_pool** Pekare till målet för pekaren över nästa skapade block-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-218">*Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.*</span><span class="sxs-lookup"><span data-stu-id="298ca-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-219">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-219">Return Values</span></span>

- <span data-ttu-id="298ca-220">**TX_SUCCESS** (0x00) information om block pool har hämtats.</span><span class="sxs-lookup"><span data-stu-id="298ca-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="298ca-221">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-222">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-222">Allowed From</span></span>

<span data-ttu-id="298ca-223">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-224">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-224">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-225">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-225">See Also</span></span>

- <span data-ttu-id="298ca-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-226">tx_block_allocate</span></span>
- <span data-ttu-id="298ca-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-227">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-229">tx_block_pool_info_get tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-231">tx_block_pool_prioritize tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="298ca-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="298ca-233">Hämta prestanda information för block pool</span><span class="sxs-lookup"><span data-stu-id="298ca-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-234">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="298ca-235">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-235">Description</span></span>

<span data-ttu-id="298ca-236">Den här tjänsten hämtar prestanda information om den angivna Memory block-poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-237">*ThreadX-biblioteket och programmet måste skapas med* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-238">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-238">Parameters</span></span>

- <span data-ttu-id="298ca-239">**pool_ptr**  Pekare till tidigare skapat minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="298ca-240">**allokerar** Pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="298ca-241">**versioner**  Pekare till målet för antalet versions begär Anden som har utförts i poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="298ca-242">**SUS pensioner**   Pekare till målet för antalet avbrott i tråd tilldelningen för den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="298ca-243">**tids gränser**  Pekare till målet för antalet tids gräns värden för att allokera uppehåll i poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="298ca-244">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-245">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-245">Return Values</span></span>

- <span data-ttu-id="298ca-246">**TX_SUCCESS**    (0x00) prestanda för att blockera poolen lyckades.</span><span class="sxs-lookup"><span data-stu-id="298ca-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="298ca-247">**TX_PTR_ERROR**  (0X03) ogiltig pekare för att blockera poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="298ca-248">**TX_FEATURE_NOT_ENABLED**    (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-249">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-249">Allowed From</span></span>

<span data-ttu-id="298ca-250">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-251">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-251">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-252">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-252">See Also</span></span>

- <span data-ttu-id="298ca-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-253">tx_block_allocate</span></span>
- <span data-ttu-id="298ca-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-254">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="298ca-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="298ca-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="298ca-261">Hämta information om system prestanda för block pool</span><span class="sxs-lookup"><span data-stu-id="298ca-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-262">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-263">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-263">Description</span></span>

<span data-ttu-id="298ca-264">Den här tjänsten hämtar prestanda information om alla minnes Blocks pooler i programmet.</span><span class="sxs-lookup"><span data-stu-id="298ca-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-265">*ThreadX-biblioteket och programmet måste skapas med* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-266">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-266">Parameters</span></span>

- <span data-ttu-id="298ca-267">**allokerar** Pekare till målet för det totala antalet allokerade begär Anden som utförts på alla blockerade pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="298ca-268">**versioner**  Pekare till målet för det totala antalet versions begär Anden som utförts på alla blockerade pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="298ca-269">**SUS pensioner**   Pekare till målet för det totala antalet SUS pensioner i alla block-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="298ca-270">**tids gränser**  Pekare till målet för det totala antalet tids gränser för att allokera uppehåll i alla block-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-271">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-272">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-272">Return Values</span></span>

- <span data-ttu-id="298ca-273">**TX_SUCCESS** (0x00) system prestanda för att blockera poolen lyckades.</span><span class="sxs-lookup"><span data-stu-id="298ca-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="298ca-274">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-275">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-275">Allowed From</span></span>

<span data-ttu-id="298ca-276">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-277">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-277">Example</span></span>

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-278">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-278">See Also</span></span>

- <span data-ttu-id="298ca-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-279">tx_block_allocate</span></span>
- <span data-ttu-id="298ca-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-280">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="298ca-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="298ca-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="298ca-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="298ca-287">Prioritera spärr lista för block-pool</span><span class="sxs-lookup"><span data-stu-id="298ca-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-288">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-289">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-289">Description</span></span>

<span data-ttu-id="298ca-290">Den här tjänsten placerar tråden med högsta prioritet inaktive rad för ett minnes block på den här poolen längst fram i listan över SUS pensioner.</span><span class="sxs-lookup"><span data-stu-id="298ca-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="298ca-291">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="298ca-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-292">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-292">Parameters</span></span>

- <span data-ttu-id="298ca-293">**pool_ptr** Pekar mot ett kontroll block för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-294">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-294">Return Values</span></span>

- <span data-ttu-id="298ca-295">**TX_SUCCESS** (0x00) prioritet för att blockera poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="298ca-296">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för minnes Blocks-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-297">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-297">Allowed From</span></span>

<span data-ttu-id="298ca-298">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-299">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-299">Preemption Possible</span></span>

<span data-ttu-id="298ca-300">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-300">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-301">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-301">Example</span></span>
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-302">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-302">See Also</span></span>

- <span data-ttu-id="298ca-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-303">tx_block_allocate</span></span>
- <span data-ttu-id="298ca-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-304">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="298ca-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="298ca-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="298ca-310">tx_block_release</span></span>

<span data-ttu-id="298ca-311">Frigör block med fast storlek i minnet</span><span class="sxs-lookup"><span data-stu-id="298ca-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-312">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="298ca-313">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-313">Description</span></span>

<span data-ttu-id="298ca-314">Den här tjänsten släpper ett tidigare allokerat block tillbaka till den kopplade poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="298ca-315">Om det finns en eller flera trådar som pausas i väntan på minnes block från den här poolen, är den första tråden inaktive rad det här minnes blocket och återupptas.</span><span class="sxs-lookup"><span data-stu-id="298ca-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="298ca-316">*Programmet måste förhindra att ett minnes Blocks utrymme används när det har släppts tillbaka till poolen.*</span><span class="sxs-lookup"><span data-stu-id="298ca-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-317">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-317">Parameters</span></span>

- <span data-ttu-id="298ca-318">**block_ptr** Pekar till det tidigare allokerade minnes blocket.</span><span class="sxs-lookup"><span data-stu-id="298ca-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-319">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-319">Return Values</span></span>

- <span data-ttu-id="298ca-320">**TX_SUCCESS** (0X00) klar minnes Blocks version.</span><span class="sxs-lookup"><span data-stu-id="298ca-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="298ca-321">**TX_PTR_ERROR** (0X03) ogiltig pekare till minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-322">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-322">Allowed From</span></span>

<span data-ttu-id="298ca-323">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-324">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-324">Preemption Possible</span></span>

<span data-ttu-id="298ca-325">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-326">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-326">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-327">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-327">See Also</span></span>

- <span data-ttu-id="298ca-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-328">tx_block_allocate</span></span>
- <span data-ttu-id="298ca-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-329">tx_block_pool_create</span></span>
- <span data-ttu-id="298ca-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="298ca-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="298ca-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="298ca-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-335">tx_byte_allocate</span></span>

<span data-ttu-id="298ca-336">Allokera byte minne</span><span class="sxs-lookup"><span data-stu-id="298ca-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-337">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-338">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-338">Description</span></span>

<span data-ttu-id="298ca-339">Den här tjänsten allokerar det angivna antalet byte från den angivna Memory byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-340">*Det är viktigt att se till att program koden inte skriver utanför det allokerade minnes blocket. Om detta inträffar inträffar skada i ett intilliggande (vanligt vis) minnes block. Resultatet är oförutsägbart och ofta allvarligt!*</span><span class="sxs-lookup"><span data-stu-id="298ca-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-341">*Prestanda för den här tjänsten är en funktion i block storlek och fragmenteringen i poolen. Därför bör den här tjänsten inte användas under tids kritiska körnings trådar.*</span><span class="sxs-lookup"><span data-stu-id="298ca-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-342">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-342">Parameters</span></span>

- <span data-ttu-id="298ca-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-343">**pool_ptr**</span></span> <br><span data-ttu-id="298ca-344">Pekare till en tidigare skapad pool för minnes block.</span><span class="sxs-lookup"><span data-stu-id="298ca-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="298ca-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-345">**memory_ptr**</span></span> <br><span data-ttu-id="298ca-346">Pekar mot en mål minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="298ca-347">Vid lyckad allokering placeras adressen till det allokerade minnes området där parametern pekar på.</span><span class="sxs-lookup"><span data-stu-id="298ca-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="298ca-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="298ca-348">**memory_size**</span></span> <br><span data-ttu-id="298ca-349">Antal byte som begärts.</span><span class="sxs-lookup"><span data-stu-id="298ca-349">Number of bytes requested.</span></span>
- <span data-ttu-id="298ca-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-350">**wait_option**</span></span> <br><span data-ttu-id="298ca-351">Definierar hur tjänsten fungerar om det inte finns tillräckligt med minne tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="298ca-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="298ca-352">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-353">**TX_NO_WAIT** (0x00000000) – om du väljer **TX_NO_WAIT** resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-354">*Detta är det enda giltiga alternativet om tjänsten anropas från initiering.*</span><span class="sxs-lookup"><span data-stu-id="298ca-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="298ca-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) – om du väljer **TX_WAIT_FOREVER** kan anrops tråden Pausa tills tillräckligt med minne är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="298ca-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="298ca-356">*timeout-värde* (0X00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska vara pausat under väntan på minnet.</span><span class="sxs-lookup"><span data-stu-id="298ca-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-357">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-357">Return Values</span></span>

- <span data-ttu-id="298ca-358">**TX_SUCCESS** (0x00) minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="298ca-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="298ca-359">**TX_DELETED** (0x01)-mediepoolen togs bort medan tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-360">Tjänsten **TX_NO_MEMORY** (0x10) kunde inte allokera minnet inom den angivna tiden till väntan.</span><span class="sxs-lookup"><span data-stu-id="298ca-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="298ca-361">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-362">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="298ca-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="298ca-363">**TX_PTR_ERROR** (0X03) ogiltig pekare till mål pekaren.</span><span class="sxs-lookup"><span data-stu-id="298ca-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="298ca-364">**TX_SIZE_ERROR** (0X05) begärd storlek är noll eller större än poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="298ca-365">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="298ca-366">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-367">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-367">Allowed From</span></span>

<span data-ttu-id="298ca-368">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-369">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-369">Preemption Possible</span></span>

<span data-ttu-id="298ca-370">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-371">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-371">Example</span></span>
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-372">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-372">See Also</span></span>

- <span data-ttu-id="298ca-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="298ca-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="298ca-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-380">tx_byte_pool_create</span></span>

<span data-ttu-id="298ca-381">Skapa minnes-pool med byte</span><span class="sxs-lookup"><span data-stu-id="298ca-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-382">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="298ca-383">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-383">Description</span></span>

<span data-ttu-id="298ca-384">Den här tjänsten skapar en pool för minnes byte i det angivna området.</span><span class="sxs-lookup"><span data-stu-id="298ca-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="298ca-385">Från början består poolen av i princip ett mycket stort ledigt block.</span><span class="sxs-lookup"><span data-stu-id="298ca-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="298ca-386">Poolen är dock bruten i mindre block som tilldelningar görs.</span><span class="sxs-lookup"><span data-stu-id="298ca-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-387">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-387">Parameters</span></span>

- <span data-ttu-id="298ca-388">**pool_ptr** Pekar mot ett kontroll block för minnes-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="298ca-389">**name_ptr** Pekar till namnet på mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="298ca-390">**pool_start** Start adress för mediepoolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="298ca-391">Start adressen måste vara justerad till storleken på data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="298ca-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="298ca-392">**pool_size** Totalt antal byte som är tillgängliga för lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-393">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-393">Return Values</span></span>

- <span data-ttu-id="298ca-394">**TX_SUCCESS** (0x00) skapade minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="298ca-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="298ca-395">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="298ca-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="298ca-396">Antingen är pekaren NULL eller också har poolen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="298ca-397">**TX_PTR_ERROR** (0X03) ogiltig start adress för poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="298ca-398">**TX_SIZE_ERROR** (0X05) storleken på poolen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="298ca-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="298ca-399">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-400">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-400">Allowed From</span></span>

<span data-ttu-id="298ca-401">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-402">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-402">Preemption Possible</span></span>

<span data-ttu-id="298ca-403">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-403">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-404">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-404">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-405">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-405">See Also</span></span>

- <span data-ttu-id="298ca-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-406">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="298ca-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="298ca-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="298ca-414">Ta bort minnes byte pool</span><span class="sxs-lookup"><span data-stu-id="298ca-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-415">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-416">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-416">Description</span></span>

<span data-ttu-id="298ca-417">Den här tjänsten tar bort den angivna minnes bytes poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="298ca-418">Alla trådar som pausas i väntan på minne från den här poolen återupptas och har en **TX_DELETED** retur status.</span><span class="sxs-lookup"><span data-stu-id="298ca-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-419">*Det är programmets ansvar att hantera det minnes område som är associerat med poolen, vilket är tillgängligt när tjänsten har slutförts. Dessutom måste programmet förhindra användning av en borttagen pool eller minne som tidigare har allokerats från den.*</span><span class="sxs-lookup"><span data-stu-id="298ca-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-420">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-420">Parameters</span></span>

- <span data-ttu-id="298ca-421">**pool_ptr** Pekar till en tidigare skapad lagringspool.</span><span class="sxs-lookup"><span data-stu-id="298ca-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-422">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-422">Return Values</span></span>

- <span data-ttu-id="298ca-423">**TX_SUCCESS** (0x00) borttagning av minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="298ca-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="298ca-424">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="298ca-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="298ca-425">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-426">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-426">Allowed From</span></span>

<span data-ttu-id="298ca-427">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-428">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-428">Preemption Possible</span></span>

<span data-ttu-id="298ca-429">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-430">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-431">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-431">See Also</span></span>

- <span data-ttu-id="298ca-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-432">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="298ca-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="298ca-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="298ca-440">Hämta information om byte-poolen</span><span class="sxs-lookup"><span data-stu-id="298ca-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-441">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-441">Prototype</span></span>

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="298ca-442">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-442">Description</span></span>

<span data-ttu-id="298ca-443">Den här tjänsten hämtar information om den angivna minnes bytes poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-444">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-444">Parameters</span></span>

- <span data-ttu-id="298ca-445">**pool_ptr** Pekare till den tidigare skapade lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="298ca-446">**namn** Pekare till målet för pekaren till byte-poolens namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="298ca-447">**tillgänglig** Pekare till målet för antalet tillgängliga byte i poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="298ca-448">**fragment** Pekare till målet för det totala antalet minnesbuffertar i byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="298ca-449">**first_suspended** Pekare till målet för visaren i den tråd som är överst i listan över återkallade byte för denna byte-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="298ca-450">**suspended_count** Pekare till målet för antalet trådar som för närvarande har pausats i den här byte-poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="298ca-451">**next_pool** Pekare till målet för pekaren över nästa skapade byte-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-452">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-453">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-453">Return Values</span></span>

- <span data-ttu-id="298ca-454">**TX_SUCCESS** (0x00) information om lyckade pooler hämtades.</span><span class="sxs-lookup"><span data-stu-id="298ca-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="298ca-455">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="298ca-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-456">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-456">Allowed From</span></span>

<span data-ttu-id="298ca-457">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-458">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-458">Preemption Possible</span></span>

<span data-ttu-id="298ca-459">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-459">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-460">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-460">Example</span></span>

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-461">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-461">See Also</span></span>

- <span data-ttu-id="298ca-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-462">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="298ca-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="298ca-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="298ca-470">Hämta prestanda information för byte-pool</span><span class="sxs-lookup"><span data-stu-id="298ca-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-471">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-471">Prototype</span></span>

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-472">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-472">Description</span></span>

<span data-ttu-id="298ca-473">Den här tjänsten hämtar prestanda information om den angivna minnes bytes poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-474">*ThreadX-biblioteket och programmet måste skapas med* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-475">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-475">Parameters</span></span>

- <span data-ttu-id="298ca-476">**pool_ptr** Pekare till tidigare skapad pool för minnes byte.</span><span class="sxs-lookup"><span data-stu-id="298ca-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="298ca-477">**allokerar** Pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="298ca-478">**versioner** Pekare till målet för antalet versions begär Anden som har utförts i poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="298ca-479">**fragments_searched** Pekare till målet för antalet interna minnes fragment som genomsöks under tilldelnings begär anden i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="298ca-480">**sammanslagningar** Pekare till målet för antalet interna minnes block som sammanfogas under tilldelnings begär anden i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="298ca-481">**delningar** Pekare till målet för antalet interna minnes block delningar (fragment) som skapas vid tilldelnings begär Anden för den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="298ca-482">**SUS pensioner** Pekare till målet för antalet avbrott i tråd tilldelningen för den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="298ca-483">**tids gränser** Pekare till målet för antalet tids gräns värden för att allokera uppehåll i poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-484">*Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.*</span><span class="sxs-lookup"><span data-stu-id="298ca-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-485">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-485">Return Values</span></span>

- <span data-ttu-id="298ca-486">**TX_SUCCESS** (0x00) prestanda för slutförd byte-pool har hämtats.</span><span class="sxs-lookup"><span data-stu-id="298ca-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="298ca-487">**TX_PTR_ERROR** (0X03) ogiltig pekare för en byte-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="298ca-488">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-489">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-489">Allowed From</span></span>

<span data-ttu-id="298ca-490">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-491">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-491">Example</span></span>

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="298ca-492">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-492">See Also</span></span>

- <span data-ttu-id="298ca-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-493">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="298ca-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="298ca-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="298ca-501">Hämta information om prestanda för byte pool system</span><span class="sxs-lookup"><span data-stu-id="298ca-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-502">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-502">Prototype</span></span>

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="298ca-503">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-503">Description</span></span>

<span data-ttu-id="298ca-504">Den här tjänsten hämtar prestanda information om alla minnes byte pooler i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-505">*ThreadX-biblioteket och programmet måste skapas med* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-506">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-506">Parameters</span></span>

- <span data-ttu-id="298ca-507">**allokerar** Pekare till målet för antalet allokerade begär Anden som utförts i den här poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="298ca-508">**versioner** Pekare till målet för antalet versions begär Anden som har utförts i poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="298ca-509">**fragments_searched** Pekare till målet för det totala antalet interna minnes fragment som genomsöks under tilldelnings begär Anden för alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="298ca-510">**sammanslagningar** Pekare till målet för det totala antalet interna minnes block som sammanfogas under tilldelnings begär Anden för alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="298ca-511">**delningar** Pekare till målet för det totala antalet interna minnes block delningar (fragment) som skapas vid tilldelnings begär Anden för alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="298ca-512">**SUS pensioner** Pekare till målet för det totala antalet SUS pensioner i alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="298ca-513">**tids gränser** Pekare till målet för det totala antalet tids gränser för att allokera uppehåll i alla byte-pooler.</span><span class="sxs-lookup"><span data-stu-id="298ca-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-514">*Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.*</span><span class="sxs-lookup"><span data-stu-id="298ca-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-515">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-515">Return Values</span></span>

- <span data-ttu-id="298ca-516">**TX_SUCCESS** (0x00) prestanda för slutförd byte-pool har hämtats.</span><span class="sxs-lookup"><span data-stu-id="298ca-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="298ca-517">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-518">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-518">Allowed From</span></span>

 <span data-ttu-id="298ca-519">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-520">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-520">Example</span></span>

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-521">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-521">See Also</span></span>

- <span data-ttu-id="298ca-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-522">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="298ca-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="298ca-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="298ca-530">Prioritera överskjutande lista för byte-pool</span><span class="sxs-lookup"><span data-stu-id="298ca-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-531">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="298ca-532">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-532">Description</span></span>

<span data-ttu-id="298ca-533">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för minne på den här poolen överst i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="298ca-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="298ca-534">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="298ca-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-535">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-535">Parameters</span></span>

- <span data-ttu-id="298ca-536">**pool_ptr** Pekar mot ett kontroll block för minnes-pool.</span><span class="sxs-lookup"><span data-stu-id="298ca-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-537">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-537">Return Values</span></span>

- <span data-ttu-id="298ca-538">**TX_SUCCESS** (0x00) prioritet för minnesallokering.</span><span class="sxs-lookup"><span data-stu-id="298ca-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="298ca-539">**TX_POOL_ERROR** (protokollnumret 0x02) ogiltig pekare för skrivarpool.</span><span class="sxs-lookup"><span data-stu-id="298ca-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-540">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-540">Allowed From</span></span>

<span data-ttu-id="298ca-541">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-542">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-542">Preemption Possible</span></span>

<span data-ttu-id="298ca-543">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-543">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-544">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-544">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-545">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-545">See Also</span></span>

- <span data-ttu-id="298ca-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-546">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="298ca-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="298ca-553">tx_byte_release</span></span>

<span data-ttu-id="298ca-554">Frisläpp byte tillbaka till minnesbuffert</span><span class="sxs-lookup"><span data-stu-id="298ca-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-555">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-556">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-556">Description</span></span>

<span data-ttu-id="298ca-557">Den här tjänsten frigör ett tidigare allokerat minnes utrymme tillbaka till den associerade poolen.</span><span class="sxs-lookup"><span data-stu-id="298ca-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="298ca-558">Om en eller flera trådar pausas i väntan på minne från den här poolen, tilldelas varje pausad tråd minne och återupptas tills minnet är slut eller tills det inte finns några fler pausade trådar.</span><span class="sxs-lookup"><span data-stu-id="298ca-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="298ca-559">Den här processen för att allokera minne till pausade trådar börjar alltid med den första tråden inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-560">*Programmet måste förhindra att minnes området används när det har släppts.*</span><span class="sxs-lookup"><span data-stu-id="298ca-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-561">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-561">Parameters</span></span>

- <span data-ttu-id="298ca-562">**memory_ptr** Pekar till det tidigare allokerade minnes området.</span><span class="sxs-lookup"><span data-stu-id="298ca-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-563">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-563">Return Values</span></span>

- <span data-ttu-id="298ca-564">**TX_SUCCESS** (0x00) minnes versionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="298ca-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="298ca-565">**TX_PTR_ERROR** (0X03) ogiltig minnes områdets pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="298ca-566">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-567">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-567">Allowed From</span></span>

<span data-ttu-id="298ca-568">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-569">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-569">Preemption Possible</span></span>

<span data-ttu-id="298ca-570">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-571">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-572">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-572">See Also</span></span>

- <span data-ttu-id="298ca-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="298ca-573">tx_byte_allocate</span></span>
- <span data-ttu-id="298ca-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="298ca-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="298ca-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="298ca-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="298ca-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="298ca-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="298ca-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-580">tx_event_flags_create</span></span>

<span data-ttu-id="298ca-581">Skapa händelse flaggor grupp</span><span class="sxs-lookup"><span data-stu-id="298ca-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-582">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-583">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-583">Description</span></span>

<span data-ttu-id="298ca-584">Den här tjänsten skapar en grupp med 32 händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="298ca-585">Alla händelse flaggor i 32 i gruppen initieras till noll.</span><span class="sxs-lookup"><span data-stu-id="298ca-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="298ca-586">Varje händelse flagga representeras av en enskild bit.</span><span class="sxs-lookup"><span data-stu-id="298ca-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-587">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-587">Parameters</span></span>

- <span data-ttu-id="298ca-588">**group_ptr** Pekar på en grupp kontroll block för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="298ca-589">**name_ptr** Pekar till namnet på gruppen med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-590">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-590">Return Values</span></span>

- <span data-ttu-id="298ca-591">**TX_SUCCESS** (0x00) skapade händelse gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="298ca-592">**TX_GROUP_ERROR** (0X06) ogiltig händelse grupp pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="298ca-593">Antingen är pekaren **Null** eller också har händelse gruppen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="298ca-594">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-595">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-595">Allowed From</span></span>

<span data-ttu-id="298ca-596">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-597">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-597">Preemption Possible</span></span>

<span data-ttu-id="298ca-598">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-598">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-599">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-600">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-600">See Also</span></span>

- <span data-ttu-id="298ca-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-602">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-606">tx_event_flags_set</span></span>
- <span data-ttu-id="298ca-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="298ca-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-608">tx_event_flags_delete</span></span>

<span data-ttu-id="298ca-609">Ta bort händelse flaggor grupp</span><span class="sxs-lookup"><span data-stu-id="298ca-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-610">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-611">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-611">Description</span></span>

<span data-ttu-id="298ca-612">Den här tjänsten tar bort den angivna händelse flaggas gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="298ca-613">Alla trådar som pausas i väntan på att händelser från den här gruppen återupptas och får en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="298ca-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="298ca-614">*Programmet måste se till att en Set notify motringning för den här händelse flaggor gruppen är slutförd (eller inaktive rad) innan du tar bort händelse flaggor gruppen. Dessutom måste programmet förhindra all framtida användning av en borttagen händelse flaggor grupp.*</span><span class="sxs-lookup"><span data-stu-id="298ca-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-615">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-615">Parameters</span></span>

- <span data-ttu-id="298ca-616">**group_ptr** Pekar till en tidigare skapad grupp med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-617">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-617">Return Values</span></span>

- <span data-ttu-id="298ca-618">**TX_SUCCESS** (0x00) händelse flaggor gruppen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="298ca-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="298ca-619">**TX_GROUP_ERROR** (0X06) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="298ca-620">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-621">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-621">Allowed From</span></span>

<span data-ttu-id="298ca-622">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-623">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-623">Preemption Possible</span></span>

<span data-ttu-id="298ca-624">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-625">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-625">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-626">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-626">See Also</span></span>

- <span data-ttu-id="298ca-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-627">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-628">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-632">tx_event_flags_set</span></span>
- <span data-ttu-id="298ca-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="298ca-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-634">tx_event_flags_get</span></span>

<span data-ttu-id="298ca-635">Hämta händelse flaggor från gruppen med händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="298ca-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-636">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-637">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-637">Description</span></span>

<span data-ttu-id="298ca-638">Den här tjänsten hämtar händelse flaggor från den angivna händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="298ca-639">Varje händelse flaggor grupp innehåller 32 händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="298ca-640">Varje flagga representeras av en enskild bit.</span><span class="sxs-lookup"><span data-stu-id="298ca-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="298ca-641">Den här tjänsten kan hämta en rad olika kombinationer av händelse flaggor som valts av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="298ca-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-642">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-642">Parameters</span></span>

- <span data-ttu-id="298ca-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-643">**group_ptr**</span></span> <br><span data-ttu-id="298ca-644">Pekar till en tidigare skapad grupp med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="298ca-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="298ca-645">**requested_flags**</span></span> <br><span data-ttu-id="298ca-646">32-bit osignerad variabel som representerar de begärda händelse flaggorna.</span><span class="sxs-lookup"><span data-stu-id="298ca-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="298ca-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-647">**get_option**</span></span> <br><span data-ttu-id="298ca-648">Anger om alla eller någon av de begärda händelse flaggorna krävs.</span><span class="sxs-lookup"><span data-stu-id="298ca-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="298ca-649">Följande är giltiga val:</span><span class="sxs-lookup"><span data-stu-id="298ca-649">The following are valid selections:</span></span>

  - <span data-ttu-id="298ca-650">**TX_AND** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="298ca-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="298ca-651">**TX_AND_CLEAR** (0x03)</span><span class="sxs-lookup"><span data-stu-id="298ca-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="298ca-652">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="298ca-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="298ca-653">**TX_OR_CLEAR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="298ca-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="298ca-654">Om du väljer TX_AND eller TX_AND_CLEAR anger det att alla händelse flaggor måste finnas i gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="298ca-655">Om du väljer TX_OR eller TX_OR_CLEAR anges att en händelse flagga är tillfredsställande.</span><span class="sxs-lookup"><span data-stu-id="298ca-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="298ca-656">Händelse flaggor som uppfyller begäran rensas (anges till noll) om TX_AND_CLEAR eller TX_OR_CLEAR har angetts.</span><span class="sxs-lookup"><span data-stu-id="298ca-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="298ca-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="298ca-658">Pekare till målet där de hämtade händelse flaggorna placeras.</span><span class="sxs-lookup"><span data-stu-id="298ca-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="298ca-659">Observera att de faktiska flaggor som erhålls kan innehålla flaggor som inte har begärts.</span><span class="sxs-lookup"><span data-stu-id="298ca-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="298ca-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-660">**wait_option**</span></span>  <br><span data-ttu-id="298ca-661">Definierar hur tjänsten beter sig om de valda händelse flaggorna inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="298ca-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="298ca-662">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-663">**TX_NO_WAIT** (0x00000000) – om du väljer TX_NO_WAIT resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-664">Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="298ca-665">**TX_WAIT_FOREVER** timeout-värde (0xFFFFFFFF) – om du väljer TX_WAIT_FOREVER blir anrops tråden inaktiv under obestämd tid tills händelse flaggorna är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="298ca-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="298ca-666">timeout-värde (0x00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-667">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-667">Return Values</span></span>

- <span data-ttu-id="298ca-668">**TX_SUCCESS** (0x00) händelse flaggorna get.</span><span class="sxs-lookup"><span data-stu-id="298ca-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="298ca-669">**TX_DELETED** (0X01) händelse flaggor gruppen togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-670">Tjänsten **TX_NO_EVENTS** (0x07) kunde inte hämta de angivna händelserna inom den angivna tiden till wait.</span><span class="sxs-lookup"><span data-stu-id="298ca-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="298ca-671">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-672">**TX_GROUP_ERROR** (0X06) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="298ca-673">**TX_PTR_ERROR** (0X03) ogiltig pekare för faktiska händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="298ca-674">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="298ca-675">**TX_OPTION_ERROR** (0X08) ogiltigt get-option angavs.</span><span class="sxs-lookup"><span data-stu-id="298ca-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-676">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-676">Allowed From</span></span>

<span data-ttu-id="298ca-677">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-678">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-678">Preemption Possible</span></span>

<span data-ttu-id="298ca-679">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-680">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-680">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

<span data-ttu-id="298ca-681">**Se även**</span><span class="sxs-lookup"><span data-stu-id="298ca-681">**See Also**</span></span>

- <span data-ttu-id="298ca-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-682">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-687">tx_event_flags_set</span></span>
- <span data-ttu-id="298ca-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="298ca-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="298ca-690">Hämta information om händelse flaggor gruppen</span><span class="sxs-lookup"><span data-stu-id="298ca-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="298ca-691">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="298ca-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="298ca-692">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="298ca-692">**Description**</span></span>

<span data-ttu-id="298ca-693">Den här tjänsten hämtar information om den angivna händelse flagg gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="298ca-694">**Parametrar**</span><span class="sxs-lookup"><span data-stu-id="298ca-694">**Parameters**</span></span>

- <span data-ttu-id="298ca-695">**group_ptr** Pekar på en grupp kontroll block för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="298ca-696">**namn** Pekare till målet för visaren för händelse flaggor gruppens namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="298ca-697">**current_flags** Pekare till målet för de aktuella uppsättnings flaggorna i gruppen med händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="298ca-698">**first_suspended** Pekare till målet för visaren i den tråd som är överst i listan över uppskjutnings listor för den här händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="298ca-699">**suspended_count** Pekare till målet för antalet trådar som för närvarande har pausats på den här händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="298ca-700">**next_group** Pekare till målet för pekaren över nästa skapade händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="298ca-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-701">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-702">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-702">Return Values</span></span>

- <span data-ttu-id="298ca-703">**TX_SUCCESS** (0X00) lyckades hämta information om händelse grupps information.</span><span class="sxs-lookup"><span data-stu-id="298ca-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="298ca-704">**TX_GROUP_ERROR** (0X06) ogiltig händelse grupp pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-705">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-705">Allowed From</span></span>

<span data-ttu-id="298ca-706">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-707">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-707">Preemption Possible</span></span>

<span data-ttu-id="298ca-708">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-708">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-709">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-709">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
<span data-ttu-id="298ca-710">**Se även**</span><span class="sxs-lookup"><span data-stu-id="298ca-710">**See Also**</span></span>

- <span data-ttu-id="298ca-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-711">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-713">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-716">tx_event_flags_set</span></span>
- <span data-ttu-id="298ca-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="298ca-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="298ca-719">Hämta information om händelse flaggor grupp prestanda information</span><span class="sxs-lookup"><span data-stu-id="298ca-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-720">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-721">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-721">Description</span></span>

<span data-ttu-id="298ca-722">Den här tjänsten hämtar prestanda information om den angivna händelse flagg gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-723">*ThreadX-bibliotek och program måste skapas med* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-724">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-724">Parameters</span></span>

- <span data-ttu-id="298ca-725">**group_ptr** Pekare till tidigare skapade händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="298ca-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="298ca-726">**uppsättningar** Pekare till målet för antalet händelse flaggor ange begär Anden som utförs i den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="298ca-727">**hämtar** Pekare till målet för antalet händelse flaggor Hämta begär Anden som utförs i den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="298ca-728">**SUS pensioner** Pekare till målet för antalet tråd händelse flaggor för att få uppehåll i den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="298ca-729">**tids gränser** Pekare till målet för antalet händelse flaggor få uppehålls tids gränser för den här gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-730">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-731">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-731">Return Values</span></span>

- <span data-ttu-id="298ca-732">**TX_SUCCESS** (0x00) händelse flaggor grupp prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="298ca-733">**TX_PTR_ERROR** (0X03) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="298ca-734">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-735">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-735">Allowed From</span></span>

<span data-ttu-id="298ca-736">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-737">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-737">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-738">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-738">See Also</span></span>

- <span data-ttu-id="298ca-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-739">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-741">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-744">tx_event_flags_set</span></span>
- <span data-ttu-id="298ca-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="298ca-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="298ca-747">Hämta information om prestanda systemet</span><span class="sxs-lookup"><span data-stu-id="298ca-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-748">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-749">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-749">Description</span></span>

<span data-ttu-id="298ca-750">Den här tjänsten hämtar prestanda information om alla händelse flaggor grupper i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-751">*ThreadX-bibliotek och program måste skapas med* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-752">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-752">Parameters</span></span>

- <span data-ttu-id="298ca-753">**uppsättningar** Pekare till mål för det totala antalet händelse flaggor som har utförts i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="298ca-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="298ca-754">**hämtar** Pekare till mål för det totala antalet händelse flaggor som utförs i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="298ca-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="298ca-755">**SUS pensioner** Pekare till mål för det totala antalet tråd händelse flaggor som får uppehåll i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="298ca-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="298ca-756">**tids gränser** Pekare till målet för det totala antalet händelse flaggor få timeout för inaktive ring i alla grupper.</span><span class="sxs-lookup"><span data-stu-id="298ca-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-757">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-758">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-758">Return Values</span></span>

- <span data-ttu-id="298ca-759">**TX_SUCCESS** (0x00) händelse flaggor system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="298ca-760">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="298ca-761">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-761">Example</span></span>

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-762">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-762">See Also</span></span>

- <span data-ttu-id="298ca-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-763">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-765">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-768">tx_event_flags_set</span></span>
- <span data-ttu-id="298ca-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="298ca-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-770">tx_event_flags_set</span></span>

<span data-ttu-id="298ca-771">Ange händelse flaggor i en grupp med händelse flaggor</span><span class="sxs-lookup"><span data-stu-id="298ca-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-772">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="298ca-773">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-773">Description</span></span>

<span data-ttu-id="298ca-774">Den här tjänsten anger eller rensar händelse flaggor i en grupp med händelse flaggor, beroende på det angivna set-alternativet.</span><span class="sxs-lookup"><span data-stu-id="298ca-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="298ca-775">Alla pausade trådar vars begär Anden om Event Flags nu är uppfyllda återupptas.</span><span class="sxs-lookup"><span data-stu-id="298ca-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-776">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-776">Parameters</span></span>

- <span data-ttu-id="298ca-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-777">**group_ptr**</span></span> <br><span data-ttu-id="298ca-778">Pekar till de tidigare skapade händelse flaggorna grupp kontroll block.</span><span class="sxs-lookup"><span data-stu-id="298ca-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="298ca-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="298ca-779">**flags_to_set**</span></span> <br><span data-ttu-id="298ca-780">Anger vilka händelse flaggor som ska ställas in eller avmarkeras baserat på set-alternativet.</span><span class="sxs-lookup"><span data-stu-id="298ca-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="298ca-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-781">**set_option**</span></span> <br><span data-ttu-id="298ca-782">Anger om de angivna händelse flaggorna är ANDed eller ORed i gruppens aktuella händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="298ca-783">Följande är giltiga val:</span><span class="sxs-lookup"><span data-stu-id="298ca-783">The following are valid selections:</span></span>
  - <span data-ttu-id="298ca-784">**TX_AND** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="298ca-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="298ca-785">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="298ca-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="298ca-786">Om du väljer TX_AND anges att de angivna händelse flaggorna är **och** Erik i de aktuella händelse flaggorna i gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="298ca-787">Det här alternativet används ofta för att rensa händelse flaggor i en grupp.</span><span class="sxs-lookup"><span data-stu-id="298ca-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="298ca-788">Annars, om TX_OR anges, är de angivna händelse flaggorna **eller** Erik med den aktuella händelsen i gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-789">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-789">Return Values</span></span>
- <span data-ttu-id="298ca-790">Angivna händelse flaggor angavs för **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="298ca-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="298ca-791">**TX_GROUP_ERROR** (0X06) ogiltig pekare till händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="298ca-792">**TX_OPTION_ERROR** (0X08) ogiltigt set-alternativ angavs.</span><span class="sxs-lookup"><span data-stu-id="298ca-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-793">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-793">Preemption Possible</span></span>

<span data-ttu-id="298ca-794">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-795">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-795">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-796">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-796">See Also</span></span>

- <span data-ttu-id="298ca-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-797">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-799">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="298ca-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="298ca-805">Meddela program när händelse flaggor anges</span><span class="sxs-lookup"><span data-stu-id="298ca-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-806">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="298ca-807">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-807">Description</span></span>

<span data-ttu-id="298ca-808">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när en eller flera händelse flaggor anges i den angivna händelse flaggor gruppen.</span><span class="sxs-lookup"><span data-stu-id="298ca-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="298ca-809">Bearbetningen av meddelande återanropet definieras av</span><span class="sxs-lookup"><span data-stu-id="298ca-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-810">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-810">Parameters</span></span>
- <span data-ttu-id="298ca-811">**group_ptr** Pekare till tidigare skapade händelse flaggor grupp.</span><span class="sxs-lookup"><span data-stu-id="298ca-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="298ca-812">**events_set_notify** Pekar på programmets händelse flaggor ange meddelande funktion.</span><span class="sxs-lookup"><span data-stu-id="298ca-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="298ca-813">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-814">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-814">Return Values</span></span>

- <span data-ttu-id="298ca-815">**TX_SUCCESS** (0x00) registreringen av event Flags set-meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="298ca-816">**TX_GROUP_ERROR** (0X06) ogiltig grupp pekare för händelse flaggor.</span><span class="sxs-lookup"><span data-stu-id="298ca-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="298ca-817">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades med meddelande funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="298ca-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="298ca-818">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-818">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a><span data-ttu-id="298ca-819">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-819">See Also</span></span>

- <span data-ttu-id="298ca-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="298ca-820">tx_event_flags_create</span></span>
- <span data-ttu-id="298ca-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="298ca-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="298ca-822">tx_event_flags_get</span></span>
- <span data-ttu-id="298ca-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="298ca-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="298ca-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="298ca-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="298ca-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="298ca-827">tx_interrupt_control</span></span>

<span data-ttu-id="298ca-828">Aktivera och inaktivera avbrott</span><span class="sxs-lookup"><span data-stu-id="298ca-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-829">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="298ca-830">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-830">Description</span></span>

<span data-ttu-id="298ca-831">Den här tjänsten aktiverar eller inaktiverar avbrott som anges i indataparametern *new_posture*.</span><span class="sxs-lookup"><span data-stu-id="298ca-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-832">*Om den här tjänsten anropas från en program tråd förblir avbrotts position en del av trådens kontext. Om tråden till exempel anropar den här rutinen för att inaktivera avbrott och sedan pausar, så inaktive ras avbrott på nytt när de återupptas.*</span><span class="sxs-lookup"><span data-stu-id="298ca-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="298ca-833">*Den här tjänsten bör inte användas för att aktivera avbrott under initiering! Om du gör det kan det orsaka oförutsägbara resultat.*</span><span class="sxs-lookup"><span data-stu-id="298ca-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-834">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-834">Parameters</span></span>

- <span data-ttu-id="298ca-835">**new_posture** Den här parametern anger om avbrott är inaktiverade eller aktiverade.</span><span class="sxs-lookup"><span data-stu-id="298ca-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="298ca-836">Giltiga värden är **TX_INT_DISABLE** och **TX_INT_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="298ca-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="298ca-837">De faktiska värdena för dessa parametrar är specifika för porten.</span><span class="sxs-lookup"><span data-stu-id="298ca-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="298ca-838">Dessutom kan vissa bearbetnings arkitekturer stödja ytterligare avbrott inaktivera postures.</span><span class="sxs-lookup"><span data-stu-id="298ca-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-839">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-839">Return Values</span></span>
- <span data-ttu-id="298ca-840">**föregående position** Den här tjänsten returnerar den tidigare avbrotts position till anroparen.</span><span class="sxs-lookup"><span data-stu-id="298ca-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="298ca-841">Detta gör att användare av tjänsten kan återställa de tidigare position när avbrott har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="298ca-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-842">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-842">Allowed From</span></span>

<span data-ttu-id="298ca-843">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-844">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-844">Preemption Possible</span></span>

<span data-ttu-id="298ca-845">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-845">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-846">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="298ca-847">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-847">See Also</span></span>

<span data-ttu-id="298ca-848">Inget</span><span class="sxs-lookup"><span data-stu-id="298ca-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="298ca-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-849">tx_mutex_create</span></span>

<span data-ttu-id="298ca-850">Skapa ömsesidigt uteslutande mutex</span><span class="sxs-lookup"><span data-stu-id="298ca-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-851">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="298ca-852">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-852">Description</span></span>

<span data-ttu-id="298ca-853">Den här tjänsten skapar ett mutex för ömsesidigt undantag mellan trådar för resurs skydd.</span><span class="sxs-lookup"><span data-stu-id="298ca-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-854">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-854">Parameters</span></span>

- <span data-ttu-id="298ca-855">**mutex_ptr** Pekar på ett mutex-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="298ca-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="298ca-856">**name_ptr** Pekar till namnet på mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="298ca-857">**priority_inherit** Anger om denna mutex stöder arv av prioriteter.</span><span class="sxs-lookup"><span data-stu-id="298ca-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="298ca-858">Om det här värdet är TX_INHERIT stöds prioriterat arv.</span><span class="sxs-lookup"><span data-stu-id="298ca-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="298ca-859">Men om TX_NO_INHERIT anges stöds inte prioriterat arv av denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-860">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-860">Return Values</span></span>

- <span data-ttu-id="298ca-861">**TX_SUCCESS** (0x00) skapandet av mutex har slutförts.</span><span class="sxs-lookup"><span data-stu-id="298ca-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="298ca-862">**TX_MUTEX_ERROR** (0X1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="298ca-863">Antingen är pekaren NULL eller så har mutex redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="298ca-864">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="298ca-865">**TX_INHERIT_ERROR** (0X1F) ogiltig prioritet Ärv parameter.</span><span class="sxs-lookup"><span data-stu-id="298ca-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-866">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-866">Allowed From</span></span>

<span data-ttu-id="298ca-867">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-868">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-868">Preemption Possible</span></span>

<span data-ttu-id="298ca-869">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-869">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-870">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-870">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-871">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-871">See Also</span></span>

- <span data-ttu-id="298ca-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-872">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-873">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="298ca-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="298ca-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-879">tx_mutex_delete</span></span>

<span data-ttu-id="298ca-880">Ta bort ömsesidigt uteslutande mutex</span><span class="sxs-lookup"><span data-stu-id="298ca-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-881">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-882">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-882">Description</span></span>

<span data-ttu-id="298ca-883">Den här tjänsten tar bort angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="298ca-884">Alla trådar som pausas i väntan på att mutexen återupptas och har fått en **TX_DELETED** retur status.</span><span class="sxs-lookup"><span data-stu-id="298ca-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-885">*Det är programmets ansvar att förhindra användning av en borttagen mutex.*</span><span class="sxs-lookup"><span data-stu-id="298ca-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-886">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-886">Parameters</span></span>

- <span data-ttu-id="298ca-887">**mutex_ptr** Pekare till en tidigare skapad mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-888">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-888">Return Values</span></span>

- <span data-ttu-id="298ca-889">**TX_SUCCESS** (0x00) en borttagning av mutex har slutförts.</span><span class="sxs-lookup"><span data-stu-id="298ca-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="298ca-890">**TX_MUTEX_ERROR** (0X1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="298ca-891">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-892">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-892">Allowed From</span></span>

<span data-ttu-id="298ca-893">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-894">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-894">Preemption Possible</span></span>

<span data-ttu-id="298ca-895">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-896">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-897">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-897">See Also</span></span>

- <span data-ttu-id="298ca-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-898">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-899">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="298ca-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="298ca-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-905">tx_mutex_get</span></span>

<span data-ttu-id="298ca-906">Få ägarskap för mutex</span><span class="sxs-lookup"><span data-stu-id="298ca-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-907">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-908">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-908">Description</span></span>

<span data-ttu-id="298ca-909">Den här tjänsten försöker få exklusiv ägande rätt till angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="298ca-910">Om den anropande tråden redan äger mutex, ökar en intern räknare och en lyckad status returneras.</span><span class="sxs-lookup"><span data-stu-id="298ca-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="298ca-911">Om mutex ägs av en annan tråd och den här tråden är högre prioritet och arv av prioritet har angetts vid mutex Create, kommer den lägre prioritets Trådens prioritet att tillfälligt höjas till den för anrops tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-912">*Prioriteten för tråden med lägre prioritet som äger en mutex med priorityinheritance bör aldrig ändras av en extern tråd under mutex-ägarskapet.*</span><span class="sxs-lookup"><span data-stu-id="298ca-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-913">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-913">Parameters</span></span>

- <span data-ttu-id="298ca-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="298ca-915">Pekare till en tidigare skapad mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="298ca-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-916">**wait_option**</span></span> <br><span data-ttu-id="298ca-917">Definierar hur tjänsten fungerar om mutex redan ägs av en annan tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="298ca-918">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-919">**TX_NO_WAIT** (0x00000000) – om du väljer TX_NO_WAIT resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-920">*Detta är det enda giltiga alternativet om tjänsten anropas från initiering.*</span><span class="sxs-lookup"><span data-stu-id="298ca-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="298ca-921">**TX_WAIT_FOREVER** timeout-värde (0xFFFFFFFF) – om du väljer **TX_WAIT_FOREVER** kan anrops tråden Pausa tills mutexen är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="298ca-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="298ca-922">timeout-värde (0x00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska vara pausat under väntan på mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-923">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-923">Return Values</span></span>

- <span data-ttu-id="298ca-924">Åtgärd för hämtning av **TX_SUCCESS** (0X00) slutförde mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="298ca-925">**TX_DELETED** (0X01) mutex togs bort medan tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-926">Tjänsten **TX_NOT_AVAILABLE** (0x1D) kunde inte erhålla ägarskapet för mutex inom den angivna tiden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="298ca-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="298ca-927">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-928">**TX_MUTEX_ERROR** (0X1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="298ca-929">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="298ca-930">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-931">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-931">Allowed From</span></span>

<span data-ttu-id="298ca-932">Initiering och trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-933">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-933">Preemption Possible</span></span>

<span data-ttu-id="298ca-934">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-935">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="298ca-936">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-936">See Also</span></span>

- <span data-ttu-id="298ca-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-937">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-938">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="298ca-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="298ca-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-944">tx_mutex_info_get</span></span>

<span data-ttu-id="298ca-945">Hämta information om mutex</span><span class="sxs-lookup"><span data-stu-id="298ca-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-946">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-946">Prototype</span></span>

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a><span data-ttu-id="298ca-947">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-947">Description</span></span>

<span data-ttu-id="298ca-948">Den här tjänsten hämtar information från angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-949">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-949">Parameters</span></span>

- <span data-ttu-id="298ca-950">**mutex_ptr** Pekare till mutex Control Block.</span><span class="sxs-lookup"><span data-stu-id="298ca-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="298ca-951">**namn** Pekare till målet som pekar på mutexens namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="298ca-952">**antal** Pekare till målets antal ägarskap för mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="298ca-953">**ägare** Pekare till målet för den ägande trådens pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="298ca-954">**first_suspended** Pekare till målet för visaren i den tråd som är överst i listan över återkallade med denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="298ca-955">**suspended_count** Pekare till målet för antalet trådar som för närvarande har pausats på den här mutexen.</span><span class="sxs-lookup"><span data-stu-id="298ca-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="298ca-956">**next_mutex** Pekare till målet för pekaren över nästa skapade mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-957">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-958">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-958">Return Values</span></span>

- <span data-ttu-id="298ca-959">**TX_SUCCESS** (0x00) information om hämtning av mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="298ca-960">**TX_MUTEX_ERROR** (0X1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-961">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-961">Allowed From</span></span>

<span data-ttu-id="298ca-962">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-963">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-963">Preemption Possible</span></span>

<span data-ttu-id="298ca-964">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-964">No</span></span>

<span data-ttu-id="298ca-965">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="298ca-965">**Example**</span></span>

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-966">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-966">See Also</span></span>

- <span data-ttu-id="298ca-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-967">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-968">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-969">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="298ca-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="298ca-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="298ca-975">Hämta information om mutex-prestanda</span><span class="sxs-lookup"><span data-stu-id="298ca-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-976">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-976">Prototype</span></span>

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="298ca-977">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-977">Description</span></span>

<span data-ttu-id="298ca-978">Den här tjänsten hämtar prestanda information om angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-979">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-980">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-980">Parameters</span></span>

- <span data-ttu-id="298ca-981">**mutex_ptr** Pekare till tidigare skapad mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="298ca-982">**placerar** Pekare till målet för antalet placerings begär Anden som har utförts på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="298ca-983">**hämtar** Pekare till målet för antalet get-begäranden som utförts på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="298ca-984">**SUS pensioner** Pekare till målet för antalet tråd-mutex-inaktive ring av denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="298ca-985">**tids gränser** Pekare till målet för antalet mutex för att få tids fördröjningar på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="298ca-986">**inversioner** Pekare till målet för antalet tråd prioritets versioner på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="298ca-987">**arv** Pekare till målet för antalet arvs åtgärder för tråd prioritet på denna mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-988">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-989">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-989">Return Values</span></span>

- <span data-ttu-id="298ca-990">**TX_SUCCESS** (0X00) korrekt mutex-prestanda får.</span><span class="sxs-lookup"><span data-stu-id="298ca-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="298ca-991">**TX_PTR_ERROR** (0X03) ogiltig mutex-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="298ca-992">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-993">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-993">Allowed From</span></span>

<span data-ttu-id="298ca-994">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-995">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-995">Example</span></span>

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-996">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-996">See Also</span></span>

- <span data-ttu-id="298ca-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-997">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-998">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-999">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="298ca-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="298ca-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="298ca-1005">Hämta information om prestanda för mutex-system</span><span class="sxs-lookup"><span data-stu-id="298ca-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1006">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="298ca-1007">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1007">Description</span></span>

<span data-ttu-id="298ca-1008">Den här tjänsten hämtar prestanda information om alla mutexer i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1009">*ThreadX-biblioteket och programmet måste skapas med* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1010">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1010">Parameters</span></span>

- <span data-ttu-id="298ca-1011">**placerar** Pekare till målet för det totala antalet placerings begär Anden som utförts på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="298ca-1012">**hämtar** Pekare till målet för det totala antalet get-begäranden som utförts på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="298ca-1013">**SUS pensioner** Pekare till målet för det totala antalet tråd-mutex-inskjutningar i alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="298ca-1014">**tids gränser** Pekare till målet för det totala antalet mutexs-timeoutar för alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="298ca-1015">**inversioner** Pekare till målet för det totala antalet tråd prioritets versioner i alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="298ca-1016">**arv** Pekare till målet för det totala antalet arvs åtgärder för tråd prioritet på alla mutexer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1017">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1018">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1018">Return Values</span></span>

- <span data-ttu-id="298ca-1019">**TX_SUCCESS** (0X00) korrekt mutex system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="298ca-1020">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1021">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1021">Allowed From</span></span>

<span data-ttu-id="298ca-1022">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1023">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1023">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1024">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1024">See Also</span></span>

- <span data-ttu-id="298ca-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1025">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1027">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="298ca-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="298ca-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="298ca-1033">Prioritera mutex SUS pensioner List</span><span class="sxs-lookup"><span data-stu-id="298ca-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1034">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1035">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1035">Description</span></span>

<span data-ttu-id="298ca-1036">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för ägarskapet av mutexen längst fram i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="298ca-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="298ca-1037">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1038">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1038">Parameters</span></span>

- <span data-ttu-id="298ca-1039">**mutex_ptr** Pekare till den tidigare skapade mutexen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1040">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1040">Return Values</span></span>

- <span data-ttu-id="298ca-1041">**TX_SUCCESS** (0X00) korrekt mutex-prioritering.</span><span class="sxs-lookup"><span data-stu-id="298ca-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="298ca-1042">**TX_MUTEX_ERROR** (0X1C) ogiltig MUTEX-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1043">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1043">Allowed From</span></span>

<span data-ttu-id="298ca-1044">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1045">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1045">Preemption Possible</span></span>

<span data-ttu-id="298ca-1046">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1047">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1047">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1048">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1048">See Also</span></span>

- <span data-ttu-id="298ca-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1049">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1051">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="298ca-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1056">tx_mutex_put</span></span>

<span data-ttu-id="298ca-1057">Frigör ägarskap för mutex</span><span class="sxs-lookup"><span data-stu-id="298ca-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1058">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1059">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1059">Description</span></span>

<span data-ttu-id="298ca-1060">Den här tjänsten minskar ägarskaps antalet för angiven mutex.</span><span class="sxs-lookup"><span data-stu-id="298ca-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="298ca-1061">Om antalet ägarskap är noll görs mutex tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="298ca-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1062">*Om prioritets arv valdes när en mutex skapades återställs prioriteten för den frisläppta tråden till den prioritet den hade när den ursprungligen fick ägandet av mutex. Alla andra prioritets ändringar som görs i den sammanställda tråden under ägarskapet av mutex kan återställas.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1063">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1063">Parameters</span></span>
- <span data-ttu-id="298ca-1064">mutex_ptr pekare till den tidigare skapade mutexen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1065">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1065">Return Values</span></span>
- <span data-ttu-id="298ca-1066">**TX_SUCCESS** (0x00) en klar mutex-version.</span><span class="sxs-lookup"><span data-stu-id="298ca-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="298ca-1067">**TX_NOT_OWNED** (0X1E) mutex ägs inte av anroparen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="298ca-1068">**TX_MUTEX_ERROR** (0X1C) ogiltig pekare till MUTEX.</span><span class="sxs-lookup"><span data-stu-id="298ca-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="298ca-1069">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1070">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1070">Allowed From</span></span>

<span data-ttu-id="298ca-1071">Initiering och trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1072">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1072">Preemption Possible</span></span>

<span data-ttu-id="298ca-1073">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1074">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1075">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1075">See Also</span></span>

- <span data-ttu-id="298ca-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1076">tx_mutex_create</span></span>
- <span data-ttu-id="298ca-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="298ca-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1078">tx_mutex_get</span></span>
- <span data-ttu-id="298ca-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="298ca-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="298ca-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="298ca-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1083">tx_queue_create</span></span>

<span data-ttu-id="298ca-1084">Skapa meddelandekö</span><span class="sxs-lookup"><span data-stu-id="298ca-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1085">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="298ca-1086">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1086">Description</span></span>

<span data-ttu-id="298ca-1087">Tjänsten skapar en meddelandekö som vanligt vis används för kommunikation mellan trådar.</span><span class="sxs-lookup"><span data-stu-id="298ca-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="298ca-1088">Det totala antalet meddelanden beräknas från angiven meddelande storlek och det totala antalet byte i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1089">*Om det totala antalet byte som anges i köns minnes området inte är jämnt delbar med den angivna meddelande storleken, används inte återstående byte i minnes området.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1090">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1090">Parameters</span></span>

- <span data-ttu-id="298ca-1091">**queue_ptr** Pekar på ett kontroll block för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="298ca-1092">**name_ptr** Pekar till namnet på meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="298ca-1093">**message_size** Anger storleken på varje meddelande i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="298ca-1094">Meddelande storlekar sträcker sig från 1 32-bitars ord till 16 32-bitars ord.</span><span class="sxs-lookup"><span data-stu-id="298ca-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="298ca-1095">Giltiga alternativ för meddelande storlek är numeriska värden från 1 till 16.</span><span class="sxs-lookup"><span data-stu-id="298ca-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="298ca-1096">**queue_start** Start adress för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="298ca-1097">Start adressen måste vara justerad till storleken på data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="298ca-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="298ca-1098">**queue_size** Totalt antal byte som är tillgängliga för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1099">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1099">Return Values</span></span>

- <span data-ttu-id="298ca-1100">**TX_SUCCESS** (0X00) lyckades skapa meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="298ca-1101">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="298ca-1102">Antingen är pekaren NULL eller också har kön redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="298ca-1103">**TX_PTR_ERROR** (0X03) ogiltig start adress för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="298ca-1104">**TX_SIZE_ERROR** (0X05) storleken på meddelande kön är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="298ca-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="298ca-1105">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1106">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1106">Allowed From</span></span>

<span data-ttu-id="298ca-1107">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1108">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1108">Preemption Possible</span></span>

<span data-ttu-id="298ca-1109">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1110">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1110">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1111">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1111">See Also</span></span>

- <span data-ttu-id="298ca-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1112">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1113">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1119">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1120">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="298ca-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1122">tx_queue_delete</span></span>

<span data-ttu-id="298ca-1123">Ta bort meddelande kön</span><span class="sxs-lookup"><span data-stu-id="298ca-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1124">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1125">Description</span></span>

<span data-ttu-id="298ca-1126">Den här tjänsten tar bort den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="298ca-1127">Alla trådar som pausas i väntan på ett meddelande från den här kön återupptas och ger en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="298ca-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="298ca-1128">*Programmet måste se till att alla skicka aviserings återanrop för den här kön har slutförts (eller inaktiverats) innan kön tas bort. Dessutom måste programmet förhindra framtida användning av en borttagen kö.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="298ca-1129">*Det är också programmets ansvar att hantera det minnes område som är associerat med kön, vilket är tillgängligt när tjänsten har slutförts.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1130">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1130">Parameters</span></span>

- <span data-ttu-id="298ca-1131">**queue_ptr** Pekare till en tidigare skapad meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1132">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1132">Return Values</span></span>

- <span data-ttu-id="298ca-1133">**TX_SUCCESS** (0x00) meddelande kön har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="298ca-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="298ca-1134">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="298ca-1135">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1136">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1136">Allowed From</span></span>

<span data-ttu-id="298ca-1137">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1138">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1138">Preemption Possible</span></span>

<span data-ttu-id="298ca-1139">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1140">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1140">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1141">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1141">See Also</span></span>

- <span data-ttu-id="298ca-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1142">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1143">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1149">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1150">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="298ca-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1152">tx_queue_flush</span></span>

<span data-ttu-id="298ca-1153">Tomma meddelanden i meddelande kön</span><span class="sxs-lookup"><span data-stu-id="298ca-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1155">Description</span></span>

<span data-ttu-id="298ca-1156">Den här tjänsten tar bort alla meddelanden som lagras i den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="298ca-1157">Om kön är full ignoreras meddelanden från alla pausade trådar.</span><span class="sxs-lookup"><span data-stu-id="298ca-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="298ca-1158">Varje pausad tråd återupptas sedan med en retur status som anger att meddelandet skickades lyckades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="298ca-1159">Om kön är tom gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="298ca-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1160">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1160">Parameters</span></span>

- <span data-ttu-id="298ca-1161">**queue_ptr** Pekare till en tidigare skapad meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1162">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1162">Return Values</span></span>

- <span data-ttu-id="298ca-1163">**TX_SUCCESS** (0x00) meddelande kön har rensats.</span><span class="sxs-lookup"><span data-stu-id="298ca-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="298ca-1164">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1165">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1165">Allowed From</span></span>

<span data-ttu-id="298ca-1166">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1167">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1167">Preemption Possible</span></span>

<span data-ttu-id="298ca-1168">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1169">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1169">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1170">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1170">See Also</span></span>

- <span data-ttu-id="298ca-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1171">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1172">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1178">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1179">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="298ca-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1181">tx_queue_front_send</span></span>

<span data-ttu-id="298ca-1182">Skicka meddelande till kön längst fram</span><span class="sxs-lookup"><span data-stu-id="298ca-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1183">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-1184">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1184">Description</span></span>

<span data-ttu-id="298ca-1185">Den här tjänsten skickar ett meddelande till den första platsen i den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="298ca-1186">Meddelandet **kopieras** till platsen längst fram i kön från det minnes området som anges av käll pekaren.</span><span class="sxs-lookup"><span data-stu-id="298ca-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1187">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1187">Parameters</span></span>

- <span data-ttu-id="298ca-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1188">**queue_ptr**</span></span> <br><span data-ttu-id="298ca-1189">Pekar på ett kontroll block för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="298ca-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1190">**source_ptr**</span></span> <br><span data-ttu-id="298ca-1191">Pekare till meddelandet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1191">Pointer to the message.</span></span>
- <span data-ttu-id="298ca-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-1192">**wait_option**</span></span>  <br><span data-ttu-id="298ca-1193">Definierar hur tjänsten fungerar om meddelande kön är full.</span><span class="sxs-lookup"><span data-stu-id="298ca-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="298ca-1194">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-1195">**TX_NO_WAIT** (0x00000000) – om du väljer TX_NO_WAIT resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-1196">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="298ca-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) – om du väljer TX_WAIT_FOREVER kan anrops tråden Pausa tills det finns utrymme i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="298ca-1198">timeout-värde (0x00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på rum i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1199">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1199">Return Values</span></span>

- <span data-ttu-id="298ca-1200">**TX_SUCCESS** (0x00) meddelandet skickades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="298ca-1201">**TX_DELETED** (0X01) meddelande kön togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-1202">**TX_QUEUE_FULL** (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna tids perioden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="298ca-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="298ca-1203">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-1204">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="298ca-1205">**TX_PTR_ERROR** (0X03) ogiltig käll pekare för meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="298ca-1206">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1207">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1207">Allowed From</span></span>

<span data-ttu-id="298ca-1208">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1209">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1209">Preemption Possible</span></span>

<span data-ttu-id="298ca-1210">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1211">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1211">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1212">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1212">See Also</span></span>

- <span data-ttu-id="298ca-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1213">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1214">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1215">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1220">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1221">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="298ca-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1223">tx_queue_info_get</span></span>

<span data-ttu-id="298ca-1224">Hämta information om kö</span><span class="sxs-lookup"><span data-stu-id="298ca-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1225">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1225">Prototype</span></span>

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a><span data-ttu-id="298ca-1226">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1226">Description</span></span>

<span data-ttu-id="298ca-1227">Den här tjänsten hämtar information om den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1228">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1228">Parameters</span></span>

- <span data-ttu-id="298ca-1229">**queue_ptr** Pekare till en tidigare skapad meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="298ca-1230">**namn** Pekare till målet för visaren i köns namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="298ca-1231">**i kö** Pekare till målet för antalet meddelanden som för närvarande finns i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="298ca-1232">**available_storage** Pekare till målet för det antal meddelanden som kön för närvarande har utrymme för.</span><span class="sxs-lookup"><span data-stu-id="298ca-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="298ca-1233">**first_suspended** Pekare till målet för visaren i den tråd som är överst på listan över återkallade i den här kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="298ca-1234">**suspended_count** Pekare till målet för antalet trådar som för närvarande har pausats i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="298ca-1235">**next_queue** Pekare till målet för pekaren över nästa skapade kö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1236">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1237">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1237">Return Values</span></span>

- <span data-ttu-id="298ca-1238">**TX_SUCCESS** (0x00) information om lyckade köer hämtades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="298ca-1239">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1240">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1240">Allowed From</span></span>

<span data-ttu-id="298ca-1241">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1242">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1242">Preemption Possible</span></span>

<span data-ttu-id="298ca-1243">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1244">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1244">Example</span></span>

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1245">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1245">See Also</span></span>

- <span data-ttu-id="298ca-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1246">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1247">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1248">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1253">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1254">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="298ca-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="298ca-1257">Hämta prestanda information för kö</span><span class="sxs-lookup"><span data-stu-id="298ca-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1258">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1258">Prototype</span></span>

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-1259">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1259">Description</span></span>

<span data-ttu-id="298ca-1260">Den här tjänsten hämtar prestanda information om den angivna kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1261">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1262">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1262">Parameters</span></span>

- <span data-ttu-id="298ca-1263">**queue_ptr** Pekare till kön som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="298ca-1264">**messages_sent** Pekare till målet för antalet sändnings begär Anden som utförts i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="298ca-1265">**messages_received** Pekare till målet för antalet mottagnings begär Anden som har utförts i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="298ca-1266">**empty_suspensions** Pekare till målet för antalet tomma köer i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="298ca-1267">**full_suspensions** Pekare till målet för antalet fulla uppehåll i kön i den här kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="298ca-1268">**full_errors** Pekare till målet för antalet fullständiga fel i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="298ca-1269">**tids gränser** Pekare till målet för antalet tids gränser för tråd SUS Pension i den här kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1270">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1271">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1271">Return Values</span></span>

- <span data-ttu-id="298ca-1272">**TX_SUCCESS** (0x00) prestanda för slutförd kö hämtas.</span><span class="sxs-lookup"><span data-stu-id="298ca-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="298ca-1273">**TX_PTR_ERROR** (0X03) ogiltig Queue pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="298ca-1274">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1275">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1275">Allowed From</span></span>

<span data-ttu-id="298ca-1276">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1277">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1277">Example</span></span>

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1278">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1278">See Also</span></span>

- <span data-ttu-id="298ca-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1279">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1280">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1281">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1286">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1287">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="298ca-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="298ca-1290">Hämta prestanda information för Queue system</span><span class="sxs-lookup"><span data-stu-id="298ca-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1291">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-1292">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1292">Description</span></span>

<span data-ttu-id="298ca-1293">Den här tjänsten hämtar prestanda information om alla köer i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1294">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1295">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1295">Parameters</span></span>

- <span data-ttu-id="298ca-1296">**messages_sent** Pekare till målet för det totala antalet sändnings begär Anden som utförts på alla köer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="298ca-1297">**messages_received** Pekare till målet för det totala antalet mottagnings begär Anden som utförts på alla köer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="298ca-1298">**empty_suspensions** Pekare till målet för det totala antalet avstängningar i kö i alla köer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="298ca-1299">**full_suspensions** Pekare till målet för det totala antalet fulla uppehåll i kön på alla köer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="298ca-1300">**full_errors** Pekare till målet för det totala antalet fullständiga fel i kön i alla köer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="298ca-1301">**tids gränser** Pekare till målet för det totala antalet tids gränser för tråd SUS pensioner i alla köer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1302">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="298ca-1303">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="298ca-1303">**Return Values**</span></span>

- <span data-ttu-id="298ca-1304">**TX_SUCCESS** (0X00) lyckat system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="298ca-1305">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1306">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1306">Allowed From</span></span>

<span data-ttu-id="298ca-1307">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1308">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1308">Example</span></span>

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1309">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1309">See Also</span></span>

- <span data-ttu-id="298ca-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1310">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1311">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1312">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1317">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1318">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="298ca-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="298ca-1321">Prioritera lista över återkallade köer</span><span class="sxs-lookup"><span data-stu-id="298ca-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1322">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1323">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1323">Description</span></span>

<span data-ttu-id="298ca-1324">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för ett meddelande (eller för att placera ett meddelande) i den här kön överst i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="298ca-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="298ca-1325">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1326">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1326">Parameters</span></span>

- <span data-ttu-id="298ca-1327">**queue_ptr** Pekare till en tidigare skapad meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1328">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1328">Return Values</span></span>

- <span data-ttu-id="298ca-1329">**TX_SUCCESS** (0x00) prioriterad Queue.</span><span class="sxs-lookup"><span data-stu-id="298ca-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="298ca-1330">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1331">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1331">Allowed From</span></span>

<span data-ttu-id="298ca-1332">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1333">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1333">Preemption Possible</span></span>

<span data-ttu-id="298ca-1334">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1335">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1335">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1336">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1336">See Also</span></span>

- <span data-ttu-id="298ca-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1337">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1338">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1339">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1344">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1345">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="298ca-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1347">tx_queue_receive</span></span>

<span data-ttu-id="298ca-1348">Hämta meddelande från meddelandekö</span><span class="sxs-lookup"><span data-stu-id="298ca-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1349">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-1350">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1350">Description</span></span>

<span data-ttu-id="298ca-1351">Den här tjänsten hämtar ett meddelande från den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="298ca-1352">Det hämtade meddelandet **kopieras** från kön till det minnes utrymme som anges av mål pekaren.</span><span class="sxs-lookup"><span data-stu-id="298ca-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="298ca-1353">Meddelandet tas sedan bort från kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1354">*Det angivna mål minnes området måste vara tillräckligt stort för att rymma meddelandet, d.v.s. meddelande målet som pekas av*  \* **destination_ptr** _ _must vara minst lika stor som meddelande storleken för den här kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="298ca-1355">Annars, om målet inte är tillräckligt stort, sker minnes skada i följande minnes områden. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1356">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1356">Parameters</span></span>

- <span data-ttu-id="298ca-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1357">**queue_ptr**</span></span> <br><span data-ttu-id="298ca-1358">Pekare till en tidigare skapad meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="298ca-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1359">**destination_ptr**</span></span> <br><span data-ttu-id="298ca-1360">Plats där meddelandet ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="298ca-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="298ca-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-1361">**wait_option**</span></span> <br><span data-ttu-id="298ca-1362">Definierar hur tjänsten fungerar om meddelande kön är tom.</span><span class="sxs-lookup"><span data-stu-id="298ca-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="298ca-1363">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-1364">**TX_NO_WAIT** (0x00000000) – om du väljer TX_NO_WAIT resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-1365">Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="298ca-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) – om du väljer TX_WAIT_FOREVER kommer anrops tråden att skjuta upp oändligt tills ett meddelande är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="298ca-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="298ca-1367">timeout-värde (0x00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska vara pausat under väntan på ett meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1368">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1368">Return Values</span></span>

- <span data-ttu-id="298ca-1369">**TX_SUCCESS** (0x00) hämtning av meddelande har slutförts.</span><span class="sxs-lookup"><span data-stu-id="298ca-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="298ca-1370">**TX_DELETED** (0X01) meddelande kön togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-1371">**TX_QUEUE_EMPTY** (0x0A) kunde inte hämta ett meddelande eftersom kön var tom under den angivna tiden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="298ca-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="298ca-1372">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-1373">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="298ca-1374">**TX_PTR_ERROR** (0X03) ogiltig destinations pekare för meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="298ca-1375">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1376">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1376">Allowed From</span></span>

<span data-ttu-id="298ca-1377">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1378">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1378">Preemption Possible</span></span>

<span data-ttu-id="298ca-1379">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1380">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1380">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1381">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1381">See Also</span></span>

- <span data-ttu-id="298ca-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1382">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1383">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1384">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1390">tx_queue_send</span></span>
- <span data-ttu-id="298ca-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="298ca-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1392">tx_queue_send</span></span>

<span data-ttu-id="298ca-1393">Skicka meddelande till meddelandekö</span><span class="sxs-lookup"><span data-stu-id="298ca-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1394">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-1395">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1395">Description</span></span>

<span data-ttu-id="298ca-1396">Den här tjänsten skickar ett meddelande till den angivna meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="298ca-1397">Det skickade meddelandet **kopieras** till kön från det minnes utrymme som anges av käll pekaren.</span><span class="sxs-lookup"><span data-stu-id="298ca-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1398">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1398">Parameters</span></span>
- <span data-ttu-id="298ca-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1399">**queue_ptr**</span></span> <br><span data-ttu-id="298ca-1400">Pekare till en tidigare skapad meddelandekö.</span><span class="sxs-lookup"><span data-stu-id="298ca-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="298ca-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1401">**source_ptr**</span></span> <br><span data-ttu-id="298ca-1402">Pekare till meddelandet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1402">Pointer to the message.</span></span>
- <span data-ttu-id="298ca-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-1403">**wait_option**</span></span> <br><span data-ttu-id="298ca-1404">Definierar hur tjänsten fungerar om meddelande kön är full.</span><span class="sxs-lookup"><span data-stu-id="298ca-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="298ca-1405">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-1406">**TX_NO_WAIT** (0x00000000) – om du väljer TX_NO_WAIT resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-1407">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd, t. ex., initiering, timer eller ISR*.</span><span class="sxs-lookup"><span data-stu-id="298ca-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="298ca-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) – om du väljer TX_WAIT_FOREVER kan anrops tråden Pausa tills det finns utrymme i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="298ca-1409">timeout-värde (0x00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på rum i kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1410">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1410">Return Values</span></span>

- <span data-ttu-id="298ca-1411">**TX_SUCCESS** (0x00) meddelandet skickades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="298ca-1412">**TX_DELETED** (0X01) meddelande kön togs bort när tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-1413">**TX_QUEUE_FULL** (0x0B) Det gick inte att skicka meddelandet eftersom kön var full under den angivna tids perioden för att vänta.</span><span class="sxs-lookup"><span data-stu-id="298ca-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="298ca-1414">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-1415">**TX_QUEUE_ERROR** (0X09) ogiltig pekare för meddelande kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="298ca-1416">**TX_PTR_ERROR** (0X03) ogiltig käll pekare för meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="298ca-1417">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1418">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1418">Allowed From</span></span>

<span data-ttu-id="298ca-1419">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1420">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1420">Preemption Possible</span></span>

<span data-ttu-id="298ca-1421">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1422">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1422">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

<span data-ttu-id="298ca-1423">**Se även**</span><span class="sxs-lookup"><span data-stu-id="298ca-1423">**See Also**</span></span>

- <span data-ttu-id="298ca-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1424">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1425">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1426">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1432">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="298ca-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="298ca-1435">Meddela program när ett meddelande skickas till kön</span><span class="sxs-lookup"><span data-stu-id="298ca-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1436">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="298ca-1437">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1437">Description</span></span>

<span data-ttu-id="298ca-1438">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när ett meddelande skickas till den angivna kön.</span><span class="sxs-lookup"><span data-stu-id="298ca-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="298ca-1439">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="298ca-1440">*Det går inte att anropa något ThreadX-API med ett uppehålls alternativ i programmets kö för att skicka meddelanden.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1441">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1441">Parameters</span></span>

- <span data-ttu-id="298ca-1442">**queue_ptr** Pekare till kön som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="298ca-1443">**queue_send_notify** Pekare till programmets kö skicka aviserings funktion.</span><span class="sxs-lookup"><span data-stu-id="298ca-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="298ca-1444">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1445">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1445">Return Values</span></span>

- <span data-ttu-id="298ca-1446">**TX_SUCCESS** (0x00) registreringen av kön skickar meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="298ca-1447">**TX_QUEUE_ERROR** (0X09) ogiltig Queue pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="298ca-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades med meddelande funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="298ca-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1449">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1449">Allowed From</span></span>

<span data-ttu-id="298ca-1450">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1451">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1451">Example</span></span>

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a><span data-ttu-id="298ca-1452">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1452">See Also</span></span>

- <span data-ttu-id="298ca-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1453">tx_queue_create</span></span>
- <span data-ttu-id="298ca-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1454">tx_queue_delete</span></span>
- <span data-ttu-id="298ca-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="298ca-1455">tx_queue_flush</span></span>
- <span data-ttu-id="298ca-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="298ca-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="298ca-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="298ca-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="298ca-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="298ca-1461">tx_queue_receive</span></span>
- <span data-ttu-id="298ca-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="298ca-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="298ca-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="298ca-1464">Placera en instans vid räkning av semafor med tak</span><span class="sxs-lookup"><span data-stu-id="298ca-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="298ca-1466">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1466">Description</span></span>

<span data-ttu-id="298ca-1467">Den här tjänsten placerar en instans i den angivna räknaren semafor, som i verkligheten ökar inventerings semaforen med en.</span><span class="sxs-lookup"><span data-stu-id="298ca-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="298ca-1468">Om det aktuella värdet för Count-semaforen är större än eller lika med det angivna taket, kommer instansen inte att placeras och ett TX_CEILING_EXCEEDED fel kommer att returneras.</span><span class="sxs-lookup"><span data-stu-id="298ca-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1469">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1469">Parameters</span></span>

- <span data-ttu-id="298ca-1470">**semaphore_ptr** Pekare till en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="298ca-1471">**tak** Högsta tillåtna gräns för semaforen (giltiga värden är mellan 1 och 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="298ca-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1472">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1472">Return Values</span></span>

- <span data-ttu-id="298ca-1473">**TX_SUCCESS (0x00)** Avklarande av semafor tak.</span><span class="sxs-lookup"><span data-stu-id="298ca-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="298ca-1474">**TX_CEILING_EXCEEDED** (0x21)-begäran överskrider tak.</span><span class="sxs-lookup"><span data-stu-id="298ca-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="298ca-1475">**TX_INVALID_CEILING** (0X22) ett ogiltigt nollvärde angavs för tak.</span><span class="sxs-lookup"><span data-stu-id="298ca-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="298ca-1476">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1477">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1477">Allowed From</span></span>

<span data-ttu-id="298ca-1478">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1479">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1480">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1480">See Also</span></span>

- <span data-ttu-id="298ca-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="298ca-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1490">tx_semaphore_create</span></span>

<span data-ttu-id="298ca-1491">Skapa inventering av semafor</span><span class="sxs-lookup"><span data-stu-id="298ca-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1492">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="298ca-1493">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1493">Description</span></span>

<span data-ttu-id="298ca-1494">Den här tjänsten skapar en inventerings semafor för synkronisering mellan trådar.</span><span class="sxs-lookup"><span data-stu-id="298ca-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="298ca-1495">Det inledande antalet semaforer anges som en indataparameter.</span><span class="sxs-lookup"><span data-stu-id="298ca-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1496">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1496">Parameters</span></span>

- <span data-ttu-id="298ca-1497">**semaphore_ptr** Pekar mot ett semafors kontroll block.</span><span class="sxs-lookup"><span data-stu-id="298ca-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="298ca-1498">**name_ptr** Pekar till namnet på semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="298ca-1499">**initial_count** Anger det inledande antalet för denna semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="298ca-1500">Juridiska värden sträcker sig från 0x00000000 till 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1501">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1501">Return Values</span></span>

- <span data-ttu-id="298ca-1502">**TX_SUCCESS** (0x00) skapade semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="298ca-1503">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="298ca-1504">Antingen är pekaren NULL eller så har semaforen redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="298ca-1505">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1506">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1506">Allowed From</span></span>

<span data-ttu-id="298ca-1507">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1508">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1508">Preemption Possible</span></span>

<span data-ttu-id="298ca-1509">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1510">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1510">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1511">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1511">See Also</span></span>

- <span data-ttu-id="298ca-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="298ca-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="298ca-1522">Ta bort inventering av semafor</span><span class="sxs-lookup"><span data-stu-id="298ca-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1523">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1524">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1524">Description</span></span>

<span data-ttu-id="298ca-1525">Den här tjänsten tar bort den angivna uppräknings semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="298ca-1526">Alla trådar som pausats i väntan på en semafors instans återupptas och har fått en TX_DELETED retur status.</span><span class="sxs-lookup"><span data-stu-id="298ca-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1527">*Programmet måste se till att en skicka avisering om återanrop för den här semaforen har slutförts (eller inaktiverats) innan du tar bort semaforen. Dessutom måste programmet förhindra all framtida användning av en borttagen semafor.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1528">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1528">Parameters</span></span>

- <span data-ttu-id="298ca-1529">**semaphore_ptr** Pekare till en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1530">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1530">Return Values</span></span>

- <span data-ttu-id="298ca-1531">**TX_SUCCESS** (0x00) vid beräkning av semafor-borttagning.</span><span class="sxs-lookup"><span data-stu-id="298ca-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="298ca-1532">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="298ca-1533">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1534">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1534">Allowed From</span></span>

<span data-ttu-id="298ca-1535">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1536">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1536">Preemption Possible</span></span>

<span data-ttu-id="298ca-1537">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1538">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="298ca-1539">**Se även**</span><span class="sxs-lookup"><span data-stu-id="298ca-1539">**See Also**</span></span>

- <span data-ttu-id="298ca-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="298ca-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1549">tx_semaphore_get</span></span>

<span data-ttu-id="298ca-1550">Hämta instans från semafor</span><span class="sxs-lookup"><span data-stu-id="298ca-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1551">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="298ca-1552">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1552">Description</span></span>

<span data-ttu-id="298ca-1553">Den här tjänsten hämtar en instans (ett enda antal) från den angivna semaforen i beräkningen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="298ca-1554">Därför minskar antalet angivna semaforer med ett.</span><span class="sxs-lookup"><span data-stu-id="298ca-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1555">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1555">Parameters</span></span>

- <span data-ttu-id="298ca-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="298ca-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="298ca-1557">Pekar mot en tidigare skapad inventerings semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="298ca-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="298ca-1558">**wait_option**</span></span> <br><span data-ttu-id="298ca-1559">Definierar hur tjänsten fungerar om det inte finns några instanser av semaforen. det vill säga antalet semaforer är noll.</span><span class="sxs-lookup"><span data-stu-id="298ca-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="298ca-1560">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="298ca-1561">**TX_NO_WAIT** (0x00000000) – om du väljer TX_NO_WAIT resultaten i en omedelbar återgång från den här tjänsten oavsett om det lyckades eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="298ca-1562">*Detta är det enda giltiga alternativet om tjänsten anropas från en icke-tråd. t. ex., initiering, timer eller ISR.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="298ca-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) – om du väljer TX_WAIT_FOREVER kommer anrops tråden att inaktive ras under obestämd tid tills det finns en instans av semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="298ca-1564">timeout-värde (0x00000001 till 0xFFFFFFFE) – om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på en semafors instans.</span><span class="sxs-lookup"><span data-stu-id="298ca-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1565">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1565">Return Values</span></span>

- <span data-ttu-id="298ca-1566">**TX_SUCCESS** (0X00) lyckades hämta en semafors instans.</span><span class="sxs-lookup"><span data-stu-id="298ca-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="298ca-1567">**TX_DELETED** (0x01) som räknar semaforen togs bort medan tråden pausades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="298ca-1568">**TX_NO_INSTANCE** (0x0D) kunde inte hämta en instans av inventerings semaforen (antalet semaforer är noll inom den angivna tiden för att vänta).</span><span class="sxs-lookup"><span data-stu-id="298ca-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="298ca-1569">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-1570">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="298ca-1571">**TX_WAIT_ERROR** (0X04) ett annat wait-alternativ än TX_NO_WAIT angavs i ett anrop från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1572">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1572">Allowed From</span></span>

<span data-ttu-id="298ca-1573">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1574">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1574">Preemption Possible</span></span>

<span data-ttu-id="298ca-1575">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1576">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1576">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1577">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1577">See Also</span></span>

- <span data-ttu-id="298ca-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="298ca-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="298ca-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="298ca-1587">Hämta information om semafor</span><span class="sxs-lookup"><span data-stu-id="298ca-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1588">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="298ca-1589">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1589">Description</span></span>

<span data-ttu-id="298ca-1590">Den här tjänsten hämtar information om den angivna semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1591">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1591">Parameters</span></span>

- <span data-ttu-id="298ca-1592">**semaphore_ptr** Pekare mot semafors kontroll block.</span><span class="sxs-lookup"><span data-stu-id="298ca-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="298ca-1593">**namn** Pekare till målet som pekar på Semaforens namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="298ca-1594">**Current_value** Pekare till målet för det aktuella semafor antalet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="298ca-1595">**first_suspended** Pekare till målet för visaren i den tråd som är överst i listan över återkallade semaforer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="298ca-1596">**suspended_count** Pekare till målet för antalet trådar som för närvarande har pausats på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="298ca-1597">**next_semaphore** Pekare till målet för pekaren över nästa skapade semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1598">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1599">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1599">Return Values</span></span>

- <span data-ttu-id="298ca-1600">Informations hämtning för **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="298ca-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="298ca-1601">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1602">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1602">Allowed From</span></span>

<span data-ttu-id="298ca-1603">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1604">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1604">Preemption Possible</span></span>

<span data-ttu-id="298ca-1605">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1606">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1606">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1607">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1607">See Also</span></span>

- <span data-ttu-id="298ca-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="298ca-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="298ca-1618">Hämta information om semafor-prestanda</span><span class="sxs-lookup"><span data-stu-id="298ca-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1619">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-1620">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1620">Description</span></span>

<span data-ttu-id="298ca-1621">Den här tjänsten hämtar prestanda information om den angivna semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1622">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="298ca-1623">**Parametrar**</span><span class="sxs-lookup"><span data-stu-id="298ca-1623">**Parameters**</span></span>

-  <span data-ttu-id="298ca-1624">**semaphore_ptr** Pekare till en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="298ca-1625">**placerar** Pekare till målet för antalet beställnings begär Anden som utförts på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="298ca-1626">**hämtar** Pekare till målet för antalet get-begäranden som utförts på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="298ca-1627">**SUS pensioner** Pekare till målet för antalet tråd avbrott i denna semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="298ca-1628">**tids gränser** Pekare till målet för antalet tids gränser för trådarnas fjädring på denna semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1629">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1630">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1630">Return Values</span></span>

- <span data-ttu-id="298ca-1631">**TX_SUCCESS** (0x00) prestanda för semaforen har hämtats.</span><span class="sxs-lookup"><span data-stu-id="298ca-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="298ca-1632">**TX_PTR_ERROR** (0X03) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="298ca-1633">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1634">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1634">Allowed From</span></span>

<span data-ttu-id="298ca-1635">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1636">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1636">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1637">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1637">See Also</span></span>

- <span data-ttu-id="298ca-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="298ca-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="298ca-1648">Hämta information om prestanda för semafor-systemet</span><span class="sxs-lookup"><span data-stu-id="298ca-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1649">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="298ca-1650">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1650">Description</span></span>

<span data-ttu-id="298ca-1651">Den här tjänsten hämtar prestanda information om alla semaforer i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1652">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestanda information \*</span><span class="sxs-lookup"><span data-stu-id="298ca-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1653">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1653">Parameters</span></span>

- <span data-ttu-id="298ca-1654">**placerar** Pekare till målet för det totala antalet placerings begär Anden som utförts på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="298ca-1655">**hämtar** Pekare till målet för det totala antalet get-begäranden som utförts på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="298ca-1656">**SUS pensioner** Pekare till målet för det totala antalet tråd avbrott i alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="298ca-1657">**tids gränser** Pekare till målet för det totala antalet tids gränser för tråd SUS Pension på alla semaforer.</span><span class="sxs-lookup"><span data-stu-id="298ca-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1658">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1659">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1659">Return Values</span></span>

- <span data-ttu-id="298ca-1660">**TX_SUCCESS** (0x00) system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="298ca-1661">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1662">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1662">Allowed From</span></span>

<span data-ttu-id="298ca-1663">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1664">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1664">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1665">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1665">See Also</span></span>

- <span data-ttu-id="298ca-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="298ca-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="298ca-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="298ca-1676">Prioritera lista över återkallade semaforer</span><span class="sxs-lookup"><span data-stu-id="298ca-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1677">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1678">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1678">Description</span></span>

<span data-ttu-id="298ca-1679">Den här tjänsten placerar den högsta prioritets tråden inaktive rad för en instans av semaforen överst i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="298ca-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="298ca-1680">Alla andra trådar förblir i samma FIFO-ordning som de inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1681">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1681">Parameters</span></span>

- <span data-ttu-id="298ca-1682">**semaphore_ptr** Pekare till en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1683">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1683">Return Values</span></span>

- <span data-ttu-id="298ca-1684">**TX_SUCCESS** (0x00) semafors prioritet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="298ca-1685">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig inventering av semafors pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1686">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1686">Allowed From</span></span>

<span data-ttu-id="298ca-1687">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1688">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1688">Preemption Possible</span></span>

<span data-ttu-id="298ca-1689">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1690">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1690">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1691">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1691">See Also</span></span>

- <span data-ttu-id="298ca-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="298ca-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1697">tx_semaphore_put</span></span>

<span data-ttu-id="298ca-1698">Placera en instans i inventering av semafor</span><span class="sxs-lookup"><span data-stu-id="298ca-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1699">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1700">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1700">Description</span></span>

<span data-ttu-id="298ca-1701">Den här tjänsten placerar en instans i den angivna räknaren semafor, som i verkligheten ökar inventerings semaforen med en.</span><span class="sxs-lookup"><span data-stu-id="298ca-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1702">*Om den här tjänsten anropas när semaforen är alla (OxFFFFFFFF) gör den nya åtgärden att semaforen återställs till noll.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1703">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1703">Parameters</span></span>

- <span data-ttu-id="298ca-1704">**semaphore_ptr** Pekar mot det tidigare skapade semafors kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="298ca-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1705">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1705">Return Values</span></span>

- <span data-ttu-id="298ca-1706">**TX_SUCCESS** (0x00) en semafor-placering.</span><span class="sxs-lookup"><span data-stu-id="298ca-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="298ca-1707">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig pekare för att räkna semaforen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1708">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1708">Allowed From</span></span>

<span data-ttu-id="298ca-1709">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1710">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1710">Preemption Possible</span></span>

<span data-ttu-id="298ca-1711">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1712">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1713">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1713">See Also</span></span>

- <span data-ttu-id="298ca-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="298ca-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="298ca-1724">Meddela program när semaforen placeras</span><span class="sxs-lookup"><span data-stu-id="298ca-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1725">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="298ca-1726">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1726">Description</span></span>

<span data-ttu-id="298ca-1727">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när den angivna semaforen placeras.</span><span class="sxs-lookup"><span data-stu-id="298ca-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="298ca-1728">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1729">*Programmets återanrop för semafors meddelanden tillåts inte anropa något ThreadX-API med ett uppehålls alternativ.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1730">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1730">Parameters</span></span>

- <span data-ttu-id="298ca-1731">**semaphore_ptr** Pekare till en tidigare skapad semafor.</span><span class="sxs-lookup"><span data-stu-id="298ca-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="298ca-1732">**semaphore_put_notify** Pekare till programmets varnings funktion för semafors placering.</span><span class="sxs-lookup"><span data-stu-id="298ca-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="298ca-1733">Om det här värdet är TX_NULL inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1734">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1734">Return Values</span></span>

- <span data-ttu-id="298ca-1735">**TX_SUCCESS** (0x00) registreringen av ett meddelande om semafors placering.</span><span class="sxs-lookup"><span data-stu-id="298ca-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="298ca-1736">**TX_SEMAPHORE_ERROR** (0X0C) ogiltig semafor-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="298ca-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades med meddelande funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="298ca-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1738">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1738">Allowed From</span></span>

<span data-ttu-id="298ca-1739">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1740">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1740">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a><span data-ttu-id="298ca-1741">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1741">See Also</span></span>

- <span data-ttu-id="298ca-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="298ca-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="298ca-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="298ca-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="298ca-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="298ca-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="298ca-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="298ca-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="298ca-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="298ca-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="298ca-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1751">tx_thread_create</span></span>

<span data-ttu-id="298ca-1752">Skapa program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1753">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1753">Prototype</span></span>

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a><span data-ttu-id="298ca-1754">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1754">Description</span></span>

<span data-ttu-id="298ca-1755">Den här tjänsten skapar en program tråd som startar körningen vid den angivna aktivitets inmatnings funktionen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="298ca-1756">Stack, Priority, avstängningen-Threshold och Time-slice är bland de attribut som anges av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="298ca-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="298ca-1757">Dessutom anges även det första körnings läget för tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="298ca-1758">**Parametrar**</span><span class="sxs-lookup"><span data-stu-id="298ca-1758">**Parameters**</span></span>

- <span data-ttu-id="298ca-1759">**thread_ptr** Pekar på ett tråd kontroll block.</span><span class="sxs-lookup"><span data-stu-id="298ca-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="298ca-1760">**name_ptr** Pekar till namnet på tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="298ca-1761">**entry_function** Anger den inledande C-funktionen för tråd körning.</span><span class="sxs-lookup"><span data-stu-id="298ca-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="298ca-1762">När en tråd returnerar från den här post funktionen placeras den i ett *slutfört* tillstånd och inaktive ras på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="298ca-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="298ca-1763">**entry_input** Ett 32-bitars värde som skickas till trådens post funktion första gången den körs.</span><span class="sxs-lookup"><span data-stu-id="298ca-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="298ca-1764">Användningen av den här indatamängden fastställs exklusivt av programmet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="298ca-1765">**stack_start** Start adress för stackens minnes områden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="298ca-1766">**stack_size** Antal byte i stack minnes området.</span><span class="sxs-lookup"><span data-stu-id="298ca-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="298ca-1767">Trådens stack område måste vara tillräckligt stort för att hantera dess värsta fall funktions anrop till kapsling och lokal variabel användning.</span><span class="sxs-lookup"><span data-stu-id="298ca-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="298ca-1768">**prioritet** Numerisk prioritet för tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="298ca-1769">Giltiga värden är mellan 0 och (TX_MAX_PRIORITES-1), där värdet 0 representerar den högsta prioriteten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="298ca-1770">**preempt_threshold** Högsta prioritets nivå (0 till (TX_MAX_PRIORITIES-1)) av inaktiverade avstängningen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="298ca-1771">Endast prioriteter som är större än den här nivån tillåts för den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="298ca-1772">Värdet måste vara mindre än eller lika med den angivna prioriteten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="298ca-1773">Ett värde som är lika med tråd prioriteten inaktiverar avstängningen-Threshold.</span><span class="sxs-lookup"><span data-stu-id="298ca-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="298ca-1774">**time_slice** Antal timer-Tick som den här tråden tillåts köra innan andra redo trådar med samma prioritet ges möjlighet att köra.</span><span class="sxs-lookup"><span data-stu-id="298ca-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="298ca-1775">Observera att med avstängningen-tröskelvärdet inaktive ras tids segmentering.</span><span class="sxs-lookup"><span data-stu-id="298ca-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="298ca-1776">Legal Time-slice-värden sträcker sig från 1 till 0xFFFFFFFF (inklusive).</span><span class="sxs-lookup"><span data-stu-id="298ca-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="298ca-1777">Värdet **TX_NO_TIME_SLICE** (värdet 0) inaktiverar tids segmentering av tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="298ca-1778">*Om du använder tids segmentering blir det en liten del av systemets kostnader.   Eftersom tids segmentering bara är användbart i fall där flera trådar delar samma prioritet, ska trådar som har en unik prioritet inte tilldelas en tid-sektor.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="298ca-1779">**auto_start** Anger om tråden startar omedelbart eller om den placeras i ett uppehålls tillstånd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="298ca-1780">Juridiska alternativ är **TX_AUTO_START** (0x01) och **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="298ca-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="298ca-1781">Om TX_DONT_START anges måste programmet senare anropa tx_thread_resume för att tråden ska kunna köras.</span><span class="sxs-lookup"><span data-stu-id="298ca-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1782">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1782">Return Values</span></span>

- <span data-ttu-id="298ca-1783">**TX_SUCCESS** (0X00) lyckad tråd skapande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="298ca-1784">**TX_THREAD_ERROR** (0X0E) ogiltig tråd kontroll pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="298ca-1785">Antingen är pekaren NULL eller också har tråden redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="298ca-1786">**TX_PTR_ERROR** (0X03) ogiltig start adress för start punkten eller stackområdet är ogiltigt, vanligt vis null.</span><span class="sxs-lookup"><span data-stu-id="298ca-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="298ca-1787">**TX_SIZE_ERROR** storlek (0x05) för stackområdet är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="298ca-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="298ca-1788">Trådar måste ha minst **TX_MINIMUM_STACK** byte för att kunna köras.</span><span class="sxs-lookup"><span data-stu-id="298ca-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="298ca-1789">**TX_PRIORITY_ERROR** (0X0F) ogiltig tråd prioritet, vilket är ett värde utanför intervallet (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="298ca-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="298ca-1790">**TX_THRESH_ERROR** (0X18) ogiltig preemptionthreshold har angetts.</span><span class="sxs-lookup"><span data-stu-id="298ca-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="298ca-1791">Värdet måste vara en giltig prioritet som är mindre än eller lika med trådens inledande prioritet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="298ca-1792">**TX_START_ERROR** (0X10) ogiltig markering för automatisk start.</span><span class="sxs-lookup"><span data-stu-id="298ca-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="298ca-1793">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1794">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1794">Allowed From</span></span>

<span data-ttu-id="298ca-1795">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1796">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1796">Preemption Possible</span></span>

<span data-ttu-id="298ca-1797">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1798">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1798">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a><span data-ttu-id="298ca-1799">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1799">See Also</span></span>

- <span data-ttu-id="298ca-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1800">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-1802">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-1809">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-1810">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="298ca-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1817">tx_thread_delete</span></span>

<span data-ttu-id="298ca-1818">Ta bort program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1819">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-1820">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1820">Description</span></span>

<span data-ttu-id="298ca-1821">Den här tjänsten tar bort den angivna program tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="298ca-1822">Eftersom den angivna tråden måste vara i ett avslutat eller slutfört tillstånd, kan den här tjänsten inte anropas från en tråd som försöker ta bort sig själv.</span><span class="sxs-lookup"><span data-stu-id="298ca-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1823">*Det är programmets ansvar att hantera det minnes område som är associerat med trådens stack, vilket är tillgängligt när tjänsten har slutförts. Dessutom måste programmet förhindra att en borttagen tråd används.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1824">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1824">Parameters</span></span>

- <span data-ttu-id="298ca-1825">**thread_ptr** Pekare till en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1826">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1826">Return Values</span></span>

- <span data-ttu-id="298ca-1827">**TX_SUCCESS** (0X00) lyckad tråd borttagning.</span><span class="sxs-lookup"><span data-stu-id="298ca-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="298ca-1828">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-1829">**TX_DELETE_ERROR** (0x11) den angivna tråden är inte i ett tillstånd som är avbrutet eller slutfört.</span><span class="sxs-lookup"><span data-stu-id="298ca-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="298ca-1830">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1831">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1831">Allowed From</span></span>

<span data-ttu-id="298ca-1832">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1833">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1833">Preemption Possible</span></span>

<span data-ttu-id="298ca-1834">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1835">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1835">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1836">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1836">See Also</span></span>

- <span data-ttu-id="298ca-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1837">tx_thread_create</span></span>
- <span data-ttu-id="298ca-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-1839">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-1846">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-1847">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="298ca-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="298ca-1855">Meddela programmet vid tråd inmatning och avsluta</span><span class="sxs-lookup"><span data-stu-id="298ca-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1856">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="298ca-1857">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1857">Description</span></span>

<span data-ttu-id="298ca-1858">Den här tjänsten registrerar en funktion för motringning av meddelanden som anropas när den angivna tråden anges eller avslutas.</span><span class="sxs-lookup"><span data-stu-id="298ca-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="298ca-1859">Bearbetningen av aviserings återanropet definieras av programmet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1860">Det går inte att anropa något ThreadX-API med ett uppehålls alternativ i programmets tråd post-eller avslutnings meddelande återanrop.</span><span class="sxs-lookup"><span data-stu-id="298ca-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1861">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1861">Parameters</span></span>

- <span data-ttu-id="298ca-1862">**thread_ptr** Pekare till den tidigare skapade tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="298ca-1863">**entry_exit_notify** Pekare till programmets tråd post/avsluts meddelande funktion.</span><span class="sxs-lookup"><span data-stu-id="298ca-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="298ca-1864">Den andra parametern för funktionen post-/avslutnings meddelande anger om en post eller Exit finns.</span><span class="sxs-lookup"><span data-stu-id="298ca-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="298ca-1865">Värdet **TX_THREAD_ENTRY** (0x00) anger att tråden angavs, medan värdet **TX_THREAD_EXIT** (0x01) anger att tråden avslutades.</span><span class="sxs-lookup"><span data-stu-id="298ca-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="298ca-1866">Om det här värdet är **TX_NULL** inaktive ras meddelande.</span><span class="sxs-lookup"><span data-stu-id="298ca-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1867">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1867">Return Values</span></span>

- <span data-ttu-id="298ca-1868">**TX_SUCCESS** (0x00) registreringen av aviserings funktionen för tråd post/avslutning.</span><span class="sxs-lookup"><span data-stu-id="298ca-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="298ca-1869">**TX_THREAD_ERROR** (0X0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="298ca-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades med meddelande funktioner inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="298ca-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1871">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1871">Allowed From</span></span>

<span data-ttu-id="298ca-1872">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1873">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1873">Example</span></span>

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="298ca-1874">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1874">See Also</span></span>

- <span data-ttu-id="298ca-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1875">tx_thread_create</span></span>
- <span data-ttu-id="298ca-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1876">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-1878">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-1885">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-1886">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="298ca-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-1893">tx_thread_identify</span></span>

<span data-ttu-id="298ca-1894">Hämtar pekare till tråd som körs för tillfället</span><span class="sxs-lookup"><span data-stu-id="298ca-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="298ca-1896">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1896">Description</span></span>

<span data-ttu-id="298ca-1897">Den här tjänsten returnerar en pekare till den aktuella tråden som körs.</span><span class="sxs-lookup"><span data-stu-id="298ca-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="298ca-1898">Om ingen tråd körs returnerar den här tjänsten en null-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1899">*Om den här tjänsten anropas från en ISR representerar returvärdet den tråd som körs innan avbrotts hanteraren körs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1900">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1900">Parameters</span></span>

<span data-ttu-id="298ca-1901">Ingen</span><span class="sxs-lookup"><span data-stu-id="298ca-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="298ca-1902">Retuen-värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1902">Retuen Values</span></span>

- <span data-ttu-id="298ca-1903">**tråd pekare** Pekare till den tråd som körs för tillfället.</span><span class="sxs-lookup"><span data-stu-id="298ca-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="298ca-1904">Om ingen tråd körs **TX_NULL** det returnerade värdet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1905">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1905">Allowed From</span></span>

<span data-ttu-id="298ca-1906">Trådar och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1907">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1907">Preemption Possible</span></span>

<span data-ttu-id="298ca-1908">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1909">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1909">Example</span></span>

<span data-ttu-id="298ca-1910">TX_THREAD \* my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="298ca-1910">TX_THREAD \*my_thread_ptr;</span></span>

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1911">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1911">See Also</span></span>

- <span data-ttu-id="298ca-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1912">tx_thread_create</span></span>
- <span data-ttu-id="298ca-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1913">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-1921">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-1922">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="298ca-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1929">tx_thread_info_get</span></span>

<span data-ttu-id="298ca-1930">Hämta information om tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1931">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1931">Prototype</span></span>

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a><span data-ttu-id="298ca-1932">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1932">Description</span></span>

<span data-ttu-id="298ca-1933">Den här tjänsten hämtar information om den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1934">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1934">Parameters</span></span>
- <span data-ttu-id="298ca-1935">**thread_ptr** Pekare till tråd kontroll block.</span><span class="sxs-lookup"><span data-stu-id="298ca-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="298ca-1936">**namn** Pekare till målet som pekar på trådens namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="298ca-1937">**tillstånd** Pekare till målet för trådens aktuella körnings tillstånd.</span><span class="sxs-lookup"><span data-stu-id="298ca-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="298ca-1938">Möjliga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="298ca-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="298ca-1939">**TX_READY** (0x00)</span><span class="sxs-lookup"><span data-stu-id="298ca-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="298ca-1940">**TX_COMPLETED** (0x01)</span><span class="sxs-lookup"><span data-stu-id="298ca-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="298ca-1941">**TX_TERMINATED** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="298ca-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="298ca-1942">**TX_SUSPENDED** (0x03)</span><span class="sxs-lookup"><span data-stu-id="298ca-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="298ca-1943">**TX_SLEEP** (0x04)</span><span class="sxs-lookup"><span data-stu-id="298ca-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="298ca-1944">**TX_QUEUE_SUSP** (0x05)</span><span class="sxs-lookup"><span data-stu-id="298ca-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="298ca-1945">**TX_SEMAPHORE_SUSP** (0x06)</span><span class="sxs-lookup"><span data-stu-id="298ca-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="298ca-1946">**TX_EVENT_FLAG** (0x07)</span><span class="sxs-lookup"><span data-stu-id="298ca-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="298ca-1947">**TX_BLOCK_MEMORY** (0x08)</span><span class="sxs-lookup"><span data-stu-id="298ca-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="298ca-1948">**TX_BYTE_MEMORY** (0x09)</span><span class="sxs-lookup"><span data-stu-id="298ca-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="298ca-1949">**TX_MUTEX_SUSP** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="298ca-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="298ca-1950">**run_count** Pekare till målet för trådens antal körningar.</span><span class="sxs-lookup"><span data-stu-id="298ca-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="298ca-1951">**prioritet** Pekare till målet för Trådens prioritet.</span><span class="sxs-lookup"><span data-stu-id="298ca-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="298ca-1952">**preemption_threshold** Pekare till målet för trådens avstängningen-tröskelvärde.</span><span class="sxs-lookup"><span data-stu-id="298ca-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="298ca-1953">**time_slice** Pekare till målet för trådens tids segment.</span><span class="sxs-lookup"><span data-stu-id="298ca-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="298ca-1954">**next_thread** Pekare till målet för nästa skapade tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="298ca-1955">**suspended_thread** Pekar till mål för pekare till nästa tråd i SUS pensions listan.</span><span class="sxs-lookup"><span data-stu-id="298ca-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-1956">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-1957">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-1957">Return Values</span></span>

- <span data-ttu-id="298ca-1958">**TX_SUCCESS** (0X00) lyckad tråd informations hämtning.</span><span class="sxs-lookup"><span data-stu-id="298ca-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="298ca-1959">**TX_THREAD_ERROR** (0X0E) ogiltig tråd kontroll pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-1960">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-1960">Allowed From</span></span>

<span data-ttu-id="298ca-1961">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-1962">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-1962">Preemption Possible</span></span>

<span data-ttu-id="298ca-1963">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-1964">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-1964">Example</span></span>

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-1965">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-1965">See Also</span></span>

- <span data-ttu-id="298ca-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-1966">tx_thread_create</span></span>
- <span data-ttu-id="298ca-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-1967">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-1969">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-1975">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-1976">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="298ca-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="298ca-1984">Hämta information om tråd prestanda</span><span class="sxs-lookup"><span data-stu-id="298ca-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-1985">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-1985">Prototype</span></span>

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a><span data-ttu-id="298ca-1986">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-1986">Description</span></span>

<span data-ttu-id="298ca-1987">Den här tjänsten hämtar prestanda information om den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-1988">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-1989">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-1989">Parameters</span></span>
- <span data-ttu-id="298ca-1990">**thread_ptr** Pekare till den tidigare skapade tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="298ca-1991">**återupptar** Pekare till målet för antalet återupptagningar av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="298ca-1992">**SUS pensioner** Pekare till målet för antalet SUS pensioner av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="298ca-1993">**solicited_preemptions** Pekare till målet för antalet preemptions till följd av ett ThreadX API-tjänst anrop som gjorts av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="298ca-1994">**interrupt_preemptions** Pekare till målet för antalet preemptions för den här tråden som ett resultat av avbrotts bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="298ca-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="298ca-1995">**priority_inversions** Pekare till målet för antalet prioritets versioner av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="298ca-1996">**time_slices** Pekare till målet för antalet Time-Slices för den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="298ca-1997">**låser** sig Pekare till målet för antalet trådar som utförs av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="298ca-1998">**tids gränser** Pekare till målet för antalet timeout-tids gränser för den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="298ca-1999">**wait_aborts** Pekare till målet för antalet väntande avbrott som utförs på den här tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="298ca-2000">**last_preempted_by** Pekare till målet för tråd pekaren som senast blockerade tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2001">*Om du anger en TX_NULL för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2002">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2002">Return Values</span></span>

- <span data-ttu-id="298ca-2003">**TX_SUCCESS** (0X00) lyckad tråd prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="298ca-2004">**TX_PTR_ERROR** (0X03) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="298ca-2005">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2006">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2006">Allowed From</span></span>

<span data-ttu-id="298ca-2007">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2008">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2008">Example</span></span>

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2009">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2009">See Also</span></span>

- <span data-ttu-id="298ca-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2010">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2011">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2013">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2019">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2020">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="298ca-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="298ca-2028">Hämta information om tråd system prestanda</span><span class="sxs-lookup"><span data-stu-id="298ca-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2029">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2029">Prototype</span></span>

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a><span data-ttu-id="298ca-2030">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2030">Description</span></span>

<span data-ttu-id="298ca-2031">Den här tjänsten hämtar prestanda information om alla trådar i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="298ca-2032">*ThreadX-biblioteket och programmet måste vara byggt med*</span><span class="sxs-lookup"><span data-stu-id="298ca-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="298ca-2033">\***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined för att den här tjänsten ska returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2034">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2034">Parameters</span></span>

- <span data-ttu-id="298ca-2035">**återupptar** Pekare till målet för det totala antalet trådar som återupptas.</span><span class="sxs-lookup"><span data-stu-id="298ca-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="298ca-2036">**SUS pensioner** Pekare till målet för det totala antalet tråd SUS pensioner.</span><span class="sxs-lookup"><span data-stu-id="298ca-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="298ca-2037">**solicited_preemptions** Pekare till målet för det totala antalet tråd-preemptions som ett resultat av en tråd som anropar en ThreadX-API-tjänst.</span><span class="sxs-lookup"><span data-stu-id="298ca-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="298ca-2038">**interrupt_preemptions** Pekare till målet för det totala antalet tråd-preemptions som ett resultat av avbrotts bearbetning.</span><span class="sxs-lookup"><span data-stu-id="298ca-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="298ca-2039">**priority_inversions** Pekare till målet för det totala antalet tråd prioritets versioner.</span><span class="sxs-lookup"><span data-stu-id="298ca-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="298ca-2040">**time_slices** Pekare till målet för det totala antalet tråd-Time-Slices.</span><span class="sxs-lookup"><span data-stu-id="298ca-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="298ca-2041">**låser** sig Pekare till målet för det totala antalet trådar.</span><span class="sxs-lookup"><span data-stu-id="298ca-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="298ca-2042">**tids gränser** Pekare till målet för det totala antalet tids gränser för tråd upphängning.</span><span class="sxs-lookup"><span data-stu-id="298ca-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="298ca-2043">**wait_aborts** Pekare till målet för det totala antalet avbrott i tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="298ca-2044">**non_idle_returns** Pekare till målet för antalet gånger som en tråd återgår till systemet när en annan tråd är redo att köras.</span><span class="sxs-lookup"><span data-stu-id="298ca-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="298ca-2045">**idle_returns** Pekare till målet för antalet gånger som en tråd återgår till systemet när ingen annan tråd är redo att köras (inaktivt system).</span><span class="sxs-lookup"><span data-stu-id="298ca-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2046">*Om du anger en **TX_NULL** för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2047">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2047">Return Values</span></span>

- <span data-ttu-id="298ca-2048">**TX_SUCCESS** (0X00) lyckad tråd system prestanda Hämta.</span><span class="sxs-lookup"><span data-stu-id="298ca-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="298ca-2049">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2050">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2050">Allowed From</span></span>

<span data-ttu-id="298ca-2051">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2052">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2052">Example</span></span>

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2053">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2053">See Also</span></span>

- <span data-ttu-id="298ca-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2054">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2055">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2057">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2063">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2064">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="298ca-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="298ca-2072">Ändra avstängningen-tröskel för program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2073">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="298ca-2074">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2074">Description</span></span>

<span data-ttu-id="298ca-2075">Den här tjänsten ändrar avstängningen-tröskeln för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="298ca-2076">Avstängningen-Threshold förhindrar avstängningen av den angivna tråden efter trådar som är lika med eller lägre än värdet för avstängningen-tröskelvärdet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="298ca-2077">*Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2078">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2078">Parameters</span></span>
- <span data-ttu-id="298ca-2079">**thread_ptr** Pekare till en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="298ca-2080">**new_threshold** Ny avstängningen prioritets nivå (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="298ca-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="298ca-2081">**old_threshold** Pekar på en plats för att returnera föregående avstängningen-tröskelvärde.</span><span class="sxs-lookup"><span data-stu-id="298ca-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2082">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2082">Return Values</span></span>

- <span data-ttu-id="298ca-2083">**TX_SUCCESS** (0X00) lyckades avstängningen-tröskel ändring.</span><span class="sxs-lookup"><span data-stu-id="298ca-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="298ca-2084">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2085">**TX_THRESH_ERROR** (0X18) angiven ny avstängningen-tröskel är inte en giltig tråd prioritet (ett annat värde än (0 till (**TX_MAX_PRIORITIES**-1)) eller är större än (lägre prioritet) än den aktuella tråd prioriteten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="298ca-2086">**TX_PTR_ERROR** (0X03) ogiltig pekare till den tidigare preemptionthreshold lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="298ca-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="298ca-2087">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2088">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2088">Allowed From</span></span>

<span data-ttu-id="298ca-2089">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2090">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2090">Preemption Possible</span></span>

<span data-ttu-id="298ca-2091">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2092">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2092">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2093">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2093">See Also</span></span>

- <span data-ttu-id="298ca-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2094">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2095">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2097">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2103">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2104">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="298ca-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="298ca-2112">Ändra prioritet för program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2113">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="298ca-2114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2114">Description</span></span>

<span data-ttu-id="298ca-2115">Den här tjänsten ändrar prioriteten för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="298ca-2116">Giltiga prioriteter är mellan 0 och (TX_MAX_PRIORITES-1), där 0 representerar den högsta prioritets nivån.</span><span class="sxs-lookup"><span data-stu-id="298ca-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-2117">\* Avstängningen-tröskelvärdet för den angivna tråden anges automatiskt till den nya prioriteten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="298ca-2118">Om ett nytt tröskelvärde önskas måste du använda \***tx_thread_preemption_change** _-tjänsten efter den här Call._</span><span class="sxs-lookup"><span data-stu-id="298ca-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2119">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2119">Parameters</span></span>

- <span data-ttu-id="298ca-2120">**thread_ptr** Pekare till en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="298ca-2121">**new_priority** Ny tråd prioritets nivå (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="298ca-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="298ca-2122">**old_priority** Pekar på en plats för att returnera trådens föregående prioritet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2123">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2123">Return Values</span></span>

- <span data-ttu-id="298ca-2124">**TX_SUCCESS** (0x00) prioritets ändring har genomförts.</span><span class="sxs-lookup"><span data-stu-id="298ca-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="298ca-2125">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2126">Den angivna nya prioriteten för **TX_PRIORITY_ERROR** (0x0F) är ogiltig (ett värde annat än (0 till (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="298ca-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="298ca-2127">**TX_PTR_ERROR** (0X03) ogiltig pekare till den tidigare prioritets lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="298ca-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="298ca-2128">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2129">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2129">Allowed From</span></span>

<span data-ttu-id="298ca-2130">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2131">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2131">Preemption Possible</span></span>

<span data-ttu-id="298ca-2132">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2133">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2133">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="298ca-2134">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2134">See Also</span></span>

- <span data-ttu-id="298ca-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2135">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2136">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2138">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2144">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2145">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="298ca-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="298ca-2153">Lämna kontroll till andra program trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="298ca-2155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2155">Description</span></span>

<span data-ttu-id="298ca-2156">Den här tjänsten övervärderar processor kontroll till andra trådar som är redo att köra med samma eller högre prioritet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2157">*Förutom att förhindra kontroll till trådar med samma prioritet, förhindrar den här tjänsten också kontroll till att tråden med högsta prioritet förhindras från att köras på grund av den aktuella trådens avstängningen-inställning.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2158">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2158">Parameters</span></span>

<span data-ttu-id="298ca-2159">Ingen</span><span class="sxs-lookup"><span data-stu-id="298ca-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2160">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2160">Return Values</span></span>

<span data-ttu-id="298ca-2161">Inget</span><span class="sxs-lookup"><span data-stu-id="298ca-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2162">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2162">Allowed From</span></span>

<span data-ttu-id="298ca-2163">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2164">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2164">Preemption Possible</span></span>

<span data-ttu-id="298ca-2165">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="298ca-2166">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2166">Examples</span></span>

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a><span data-ttu-id="298ca-2167">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2167">See Also</span></span>

- <span data-ttu-id="298ca-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2168">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2169">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2171">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2177">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2178">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="298ca-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2185">tx_thread_reset</span></span>

<span data-ttu-id="298ca-2186">Återställ tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2187">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2188">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2188">Description</span></span>

<span data-ttu-id="298ca-2189">Den här tjänsten återställer den angivna tråden så att den körs vid den Start punkt som definieras vid skapandet av tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="298ca-2190">Tråden måste vara antingen i ett **TX_COMPLETED** eller **TX_TERMINATED** tillstånd för att den ska kunna återställas</span><span class="sxs-lookup"><span data-stu-id="298ca-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-2191">*Tråden måste återupptas för att den ska kunna köras igen.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2192">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2192">Parameters</span></span>

- <span data-ttu-id="298ca-2193">**thread_ptr** Pekare till en tidigare skapad tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2194">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2194">Return Values</span></span>

- <span data-ttu-id="298ca-2195">**TX_SUCCESS** (0X00) lyckad tråd återställning.</span><span class="sxs-lookup"><span data-stu-id="298ca-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="298ca-2196">**TX_NOT_DONE** (0x20) den angivna tråden är inte i ett **TX_COMPLETED** eller **TX_TERMINATED** tillstånd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="298ca-2197">**TX_THREAD_ERROR** (0X0E) ogiltig tråd pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="298ca-2198">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2199">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2199">Allowed From</span></span>

<span data-ttu-id="298ca-2200">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2201">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2201">Example</span></span>

<span data-ttu-id="298ca-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="298ca-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2203">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2203">See Also</span></span>

- <span data-ttu-id="298ca-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2204">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2205">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2207">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="298ca-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2214">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="298ca-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2221">tx_thread_resume</span></span>

<span data-ttu-id="298ca-2222">Återuppta inaktive rad program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2223">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2224">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2224">Description</span></span>

<span data-ttu-id="298ca-2225">Den här tjänsten återupptar eller förbereder körning av en tråd som tidigare har avbrutits av ett ***tx_thread_suspend*** -anrop.</span><span class="sxs-lookup"><span data-stu-id="298ca-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="298ca-2226">Dessutom återupptar den här tjänsten trådar som skapats utan automatisk start.</span><span class="sxs-lookup"><span data-stu-id="298ca-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2227">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2227">Parameters</span></span>

- <span data-ttu-id="298ca-2228">**thread_ptr** Pekar till en inaktive rad program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2229">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2229">Return Values</span></span>

- <span data-ttu-id="298ca-2230">**TX_SUCCESS** (0X00) lyckad tråd återgång.</span><span class="sxs-lookup"><span data-stu-id="298ca-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="298ca-2231">**TX_SUSPEND_LIFTED** (0x19) fastställde tidigare fördröjd SUS pension.</span><span class="sxs-lookup"><span data-stu-id="298ca-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="298ca-2232">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2233">**TX_RESUME_ERROR** (0x12) den angivna tråden har inte pausats eller har tidigare avbrutits av en annan tjänst än **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="298ca-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2234">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2234">Allowed From</span></span>

<span data-ttu-id="298ca-2235">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2236">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2236">Preemption Possible</span></span>

<span data-ttu-id="298ca-2237">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2237">Yes</span></span>

<span data-ttu-id="298ca-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="298ca-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2239">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2240">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2240">See Also</span></span>

- <span data-ttu-id="298ca-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2241">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2242">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2244">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2251">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="298ca-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2258">tx_thread_sleep</span></span>

<span data-ttu-id="298ca-2259">Pausa den aktuella tråden för angiven tid</span><span class="sxs-lookup"><span data-stu-id="298ca-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2260">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="298ca-2261">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2261">Description</span></span>

<span data-ttu-id="298ca-2262">Den här tjänsten gör att den anropande tråden pausas för det angivna antalet timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="298ca-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="298ca-2263">Mängden fysiskt klock slag som är associerad med ett timer-Tick är programspecifik.</span><span class="sxs-lookup"><span data-stu-id="298ca-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="298ca-2264">Den här tjänsten kan endast anropas från en program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2265">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2265">Parameters</span></span>

- <span data-ttu-id="298ca-2266">**timer_ticks** Antalet timer-Tick för att pausa den anropande program tråden, mellan 0 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="298ca-2267">Om 0 anges returnerar tjänsten omedelbart.</span><span class="sxs-lookup"><span data-stu-id="298ca-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2268">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2268">Return Values</span></span>

- <span data-ttu-id="298ca-2269">**TX_SUCCESS** (0X00) lyckad tråd ström.</span><span class="sxs-lookup"><span data-stu-id="298ca-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="298ca-2270">**TX_WAIT_ABORTED** SUS pensionen (0x1a) avbröts av en annan tråd, timer eller ISR.</span><span class="sxs-lookup"><span data-stu-id="298ca-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="298ca-2271">**TX_CALLER_ERROR** -tjänsten (0x13) anropades från en icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2272">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2272">Allowed From</span></span>

<span data-ttu-id="298ca-2273">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2274">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2274">Preemption Possible</span></span>

<span data-ttu-id="298ca-2275">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2276">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2277">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2277">See Also</span></span>

- <span data-ttu-id="298ca-2278">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2280">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2287">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2288">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="298ca-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="298ca-2295">Registrera återanrop för tråds tack rings meddelande</span><span class="sxs-lookup"><span data-stu-id="298ca-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2296">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="298ca-2297">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2297">Description</span></span>

<span data-ttu-id="298ca-2298">Den här tjänsten registrerar en funktion för motringning av meddelanden för hantering av tråds tack fel.</span><span class="sxs-lookup"><span data-stu-id="298ca-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="298ca-2299">När ThreadX identifierar ett tråds tack-fel under körningen, anropar den denna aviserings funktion för att bearbeta felet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="298ca-2300">Bearbetningen av felet har definierats fullständigt av programmet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="298ca-2301">Allt från att pausa den överträdande tråden för att återställa hela systemet kan göras.</span><span class="sxs-lookup"><span data-stu-id="298ca-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-2302">*ThreadX-biblioteket måste ha skapats med* **TX_ENABLE_STACK_CHECKING** *definierat för att den här tjänsten ska returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2303">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2303">Parameters</span></span>
- <span data-ttu-id="298ca-2304">**error_handler** Pekare till programmets stack fel hanterings funktion.</span><span class="sxs-lookup"><span data-stu-id="298ca-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="298ca-2305">Om det här värdet är TX_NULL inaktive ras meddelandet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2306">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2306">Return Values</span></span>

- <span data-ttu-id="298ca-2307">**TX_SUCCESS** (0X00) lyckad tråd återställning.</span><span class="sxs-lookup"><span data-stu-id="298ca-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="298ca-2308">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2309">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2309">Allowed From</span></span>

<span data-ttu-id="298ca-2310">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2311">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="298ca-2312">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2312">See Also</span></span>

- <span data-ttu-id="298ca-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2313">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2314">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2316">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="298ca-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2323">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2324">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="298ca-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2330">tx_thread_suspend</span></span>

<span data-ttu-id="298ca-2331">Pausa program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2332">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2333">Description</span></span>

<span data-ttu-id="298ca-2334">Den här tjänsten pausar den angivna program tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="298ca-2335">En tråd kan anropa den här tjänsten för att inaktivera den.</span><span class="sxs-lookup"><span data-stu-id="298ca-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2336">*Om den angivna tråden redan har pausats av en annan anledning hålls denna SUS Pension internt tills den föregående uppskjutningen har lyfts upp. När detta sker utförs denna avbrytande avstängning av den angivna tråden. Ytterligare avstängnings begär Anden utan tillstånd har ingen påverkan.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="298ca-2337">Efter inaktive rad måste tråden återupptas genom att ***tx_thread_resume*** köras igen.</span><span class="sxs-lookup"><span data-stu-id="298ca-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2338">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2338">Parameters</span></span>

- <span data-ttu-id="298ca-2339">**thread_ptr** Pekare till en program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2340">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2340">Return Values</span></span>

- <span data-ttu-id="298ca-2341">**TX_SUCCESS** (0x00) en lyckad tråd har pausats.</span><span class="sxs-lookup"><span data-stu-id="298ca-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="298ca-2342">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2343">**TX_SUSPEND_ERROR** (0x14) den angivna tråden är i ett avslutat eller slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="298ca-2344">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2345">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2345">Allowed From</span></span>

<span data-ttu-id="298ca-2346">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2347">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2347">Preemption Possible</span></span>

<span data-ttu-id="298ca-2348">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2349">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2350">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2350">See Also</span></span>

- <span data-ttu-id="298ca-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2351">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2352">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2354">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2361">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2362">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="298ca-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2368">tx_thread_terminate</span></span>

<span data-ttu-id="298ca-2369">Avslutar program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2370">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="298ca-2371">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2371">Description</span></span>

<span data-ttu-id="298ca-2372">Den här tjänsten avslutar den angivna program tråden oavsett om tråden är inaktive rad eller inte.</span><span class="sxs-lookup"><span data-stu-id="298ca-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="298ca-2373">En tråd kan anropa den här tjänsten för att avsluta sig själv.</span><span class="sxs-lookup"><span data-stu-id="298ca-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2374">*Det är programmets ansvar att se till att tråden är i ett tillstånd som är lämpligt för uppsägning. En tråd bör till exempel inte avslutas under kritisk program bearbetning eller i andra komponenter för mellanprogram där den kan lämna sådan bearbetning i ett okänt tillstånd.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-2375">*Efter att ha avslut ATS måste tråden återställas för att den ska kunna köras igen.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2376">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2376">Parameters</span></span>

- <span data-ttu-id="298ca-2377">**thread_ptr** Pekare till program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2378">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2378">Return Values</span></span>
- <span data-ttu-id="298ca-2379">**TX_SUCCESS** (0X00) lyckad tråd avslutas.</span><span class="sxs-lookup"><span data-stu-id="298ca-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="298ca-2380">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2381">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2382">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2382">Allowed From</span></span>

<span data-ttu-id="298ca-2383">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2384">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2384">Preemption Possible</span></span>

<span data-ttu-id="298ca-2385">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2386">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2387">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2387">See Also</span></span>

- <span data-ttu-id="298ca-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2390">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2397">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2398">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="298ca-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="298ca-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="298ca-2405">Ändra tid – sektor för program tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2406">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="298ca-2407">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2407">Description</span></span>

<span data-ttu-id="298ca-2408">Den här tjänsten ändrar tids segmentet för den angivna program tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="298ca-2409">Om du väljer en tids gräns för en tråd är det inte säkert att det kör fler än det angivna antalet timer-Tick innan andra trådar av samma eller högre prioritet har möjlighet att köra.</span><span class="sxs-lookup"><span data-stu-id="298ca-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2410">*Om du använder avstängningen-tröskelvärdet inaktive ras tids segmentering för den angivna tråden.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2411">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2411">Parameters</span></span>

- <span data-ttu-id="298ca-2412">**thread_ptr** Pekare till program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="298ca-2413">**new_time_slice** Nytt tids sektor värde.</span><span class="sxs-lookup"><span data-stu-id="298ca-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="298ca-2414">Giltiga värden är TX_NO_TIME_SLICE och numeriska värden från 1 till 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="298ca-2415">**old_time_slice** Pekare till platsen för lagring av föregående timeslice-värde för den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2416">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2416">Return Values</span></span>

- <span data-ttu-id="298ca-2417">**TX_SUCCESS** (0X00) slutförd Time-slice-risk.</span><span class="sxs-lookup"><span data-stu-id="298ca-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="298ca-2418">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2419">**TX_PTR_ERROR** (0X03) ogiltig pekare till föregående tid – sektor lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="298ca-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="298ca-2420">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2421">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2421">Allowed From</span></span>

<span data-ttu-id="298ca-2422">Trådar och timers</span><span class="sxs-lookup"><span data-stu-id="298ca-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2423">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2423">Preemption Possible</span></span>

<span data-ttu-id="298ca-2424">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2425">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2425">Example</span></span>

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2426">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2426">See Also</span></span>

- <span data-ttu-id="298ca-2427">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2427">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2428">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2430">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2437">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2438">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="298ca-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="298ca-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="298ca-2445">Avbryt avstängning av angiven tråd</span><span class="sxs-lookup"><span data-stu-id="298ca-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2446">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2447">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2447">Description</span></span>

<span data-ttu-id="298ca-2448">Den här tjänsten avbryter vilo läge eller andra objekt avbrott i den angivna tråden.</span><span class="sxs-lookup"><span data-stu-id="298ca-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="298ca-2449">Om vänte tiden avbryts returneras ett **TX_WAIT_ABORTED** -värde från den tjänst som tråden väntade på.</span><span class="sxs-lookup"><span data-stu-id="298ca-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2450">*Den här tjänsten frigör inte explicit avstängning som görs av tjänsten tx_thread_suspend.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2451">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2451">Parameters</span></span>

- <span data-ttu-id="298ca-2452">**thread_ptr** Pekare till en tidigare skapad program tråd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2453">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2453">Return Values</span></span>

- <span data-ttu-id="298ca-2454">**TX_SUCCESS** (0X00) slutfört tråds wait-avbrott.</span><span class="sxs-lookup"><span data-stu-id="298ca-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="298ca-2455">**TX_THREAD_ERROR** (0X0E) ogiltig Application Thread-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="298ca-2456">**TX_WAIT_ABORT_ERROR** (0x1B) den angivna tråden är inte i ett väntande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2457">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2457">Allowed From</span></span>

<span data-ttu-id="298ca-2458">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2459">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2459">Preemption Possible</span></span>
<span data-ttu-id="298ca-2460">Ja</span><span class="sxs-lookup"><span data-stu-id="298ca-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2461">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2462">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2462">See Also</span></span>

- <span data-ttu-id="298ca-2463">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2463">tx_thread_create</span></span>
- <span data-ttu-id="298ca-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2464">tx_thread_delete</span></span>
- <span data-ttu-id="298ca-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="298ca-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="298ca-2466">tx_thread_identify</span></span>
- <span data-ttu-id="298ca-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="298ca-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="298ca-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="298ca-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="298ca-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="298ca-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="298ca-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="298ca-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="298ca-2473">tx_thread_reset</span></span>
- <span data-ttu-id="298ca-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="298ca-2474">tx_thread_resume</span></span>
- <span data-ttu-id="298ca-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="298ca-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="298ca-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="298ca-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="298ca-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="298ca-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="298ca-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="298ca-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="298ca-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="298ca-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2480">tx_time_get</span></span>

<span data-ttu-id="298ca-2481">Hämtar aktuell tid</span><span class="sxs-lookup"><span data-stu-id="298ca-2481">Retrieves the current time</span></span>

<span data-ttu-id="298ca-2482">Program timers</span><span class="sxs-lookup"><span data-stu-id="298ca-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2483">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="298ca-2484">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2484">Description</span></span>

<span data-ttu-id="298ca-2485">Den här tjänsten returnerar innehållet i den interna system klockan.</span><span class="sxs-lookup"><span data-stu-id="298ca-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="298ca-2486">Varje timertick ökar den interna system klockan med ett.</span><span class="sxs-lookup"><span data-stu-id="298ca-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="298ca-2487">System klockan är inställd på noll under initieringen och kan ändras till ett särskilt värde av tjänsten ***tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="298ca-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2488">*Den faktiska tiden som varje timer-Tick representerar är programspecifik.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="298ca-2489">**Parametrar**</span><span class="sxs-lookup"><span data-stu-id="298ca-2489">**Parameters**</span></span>

<span data-ttu-id="298ca-2490">Inget</span><span class="sxs-lookup"><span data-stu-id="298ca-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2491">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2491">Return Values</span></span>

- <span data-ttu-id="298ca-2492">**system klock streck** Värdet för intern, kostnads fri körning, system klocka.</span><span class="sxs-lookup"><span data-stu-id="298ca-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2493">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2493">Allowed From</span></span>

<span data-ttu-id="298ca-2494">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2495">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2495">Preemption Possible</span></span>
<span data-ttu-id="298ca-2496">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2497">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2498">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2498">See Also</span></span>

- <span data-ttu-id="298ca-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="298ca-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="298ca-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="298ca-2500">tx_time_set</span></span>

<span data-ttu-id="298ca-2501">Anger aktuell tid</span><span class="sxs-lookup"><span data-stu-id="298ca-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2502">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="298ca-2503">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2503">Description</span></span>

<span data-ttu-id="298ca-2504">Den här tjänsten anger den interna system klockan för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="298ca-2505">Varje timer-Ticket ökar den interna system klockan med ett.</span><span class="sxs-lookup"><span data-stu-id="298ca-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2506">*Den faktiska tiden som varje timer-Tick representerar är programspecifik.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2507">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2507">Parameters</span></span>

- <span data-ttu-id="298ca-2508">**new_time** Ny tid för system klockan, giltiga värden är mellan 0 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2509">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2509">Return Values</span></span>

<span data-ttu-id="298ca-2510">Inget</span><span class="sxs-lookup"><span data-stu-id="298ca-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2511">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2511">Allowed From</span></span>

<span data-ttu-id="298ca-2512">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2513">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2513">Preemption Possible</span></span>

<span data-ttu-id="298ca-2514">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2515">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2516">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2516">See Also</span></span>

- <span data-ttu-id="298ca-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="298ca-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2518">tx_timer_activate</span></span>

<span data-ttu-id="298ca-2519">Aktivera program-timer</span><span class="sxs-lookup"><span data-stu-id="298ca-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2520">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2521">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2521">Description</span></span>

<span data-ttu-id="298ca-2522">Den här tjänsten aktiverar den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="298ca-2523">Utgångs rutinerna för timers som går ut samtidigt körs i den ordning som de aktiverades.</span><span class="sxs-lookup"><span data-stu-id="298ca-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2524">*En förfallen timer med en bild måste återställas via*  \* **tx_timer_change** _ _before den kan aktive ras igen. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2525">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2525">Parameters</span></span>

- <span data-ttu-id="298ca-2526">**timer_ptr** Pekar till en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="298ca-2527">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="298ca-2527">**Return Values**</span></span>

- <span data-ttu-id="298ca-2528">**TX_SUCCESS** (0x00) aktiveringen av programtimern lyckades.</span><span class="sxs-lookup"><span data-stu-id="298ca-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="298ca-2529">**TX_TIMER_ERROR** (0X15) ogiltig pekare för program timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="298ca-2530">0x17-timern var redan aktiv eller är en timer för en bild som redan har upphört att gälla. **TX_ACTIVATE_ERROR**</span><span class="sxs-lookup"><span data-stu-id="298ca-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2531">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2531">Allowed From</span></span>

<span data-ttu-id="298ca-2532">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2533">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2533">Preemption Possible</span></span>

<span data-ttu-id="298ca-2534">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2535">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2536">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2536">See Also</span></span>

- <span data-ttu-id="298ca-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2537">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2538">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2540">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="298ca-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="298ca-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2544">tx_timer_change</span></span>

<span data-ttu-id="298ca-2545">Ändra programmets timer</span><span class="sxs-lookup"><span data-stu-id="298ca-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2546">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="298ca-2547">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2547">Description</span></span>

<span data-ttu-id="298ca-2548">Den här tjänsten ändrar utgångs egenskaperna för den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="298ca-2549">Timern måste inaktive ras innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="298ca-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2550">*Ett anrop till*  \* **tx_timer_activate** _ _service krävs efter den här tjänsten för att starta timern igen. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2551">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2551">Parameters</span></span>

- <span data-ttu-id="298ca-2552">**timer_ptr** Pekar mot ett timer Control-Block.</span><span class="sxs-lookup"><span data-stu-id="298ca-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="298ca-2553">**initial_ticks** Anger det ursprungliga antalet Tick för förfallo datum för timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="298ca-2554">Giltiga värden är mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="298ca-2555">**reschedule_ticks** Anger antalet Tick för alla timer-förfaller efter den första.</span><span class="sxs-lookup"><span data-stu-id="298ca-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="298ca-2556">En noll för den här parametern gör timern till en timer med en *bild* .</span><span class="sxs-lookup"><span data-stu-id="298ca-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="298ca-2557">Annars, för periodiska timers, är de juridiska värdena mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2558">*En förfallen timer med en bild måste återställas via* 
\* **tx_timer_change** _ _before den kan aktive ras igen. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2559">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2559">Return Values</span></span>

- <span data-ttu-id="298ca-2560">**TX_SUCCESS** (0x00) ändring av programtimern har slutförts.</span><span class="sxs-lookup"><span data-stu-id="298ca-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="298ca-2561">**TX_TIMER_ERROR** (0X15) ogiltig pekare för program timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="298ca-2562">**TX_TICK_ERROR** (0X16) ogiltigt värde (noll) angavs för inledande Tick.</span><span class="sxs-lookup"><span data-stu-id="298ca-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="298ca-2563">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2564">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2564">Allowed From</span></span>

<span data-ttu-id="298ca-2565">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2566">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2566">Preemption Possible</span></span>

<span data-ttu-id="298ca-2567">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2568">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2568">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a><span data-ttu-id="298ca-2569">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2569">See Also</span></span>

- <span data-ttu-id="298ca-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2570">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2571">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2573">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="298ca-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="298ca-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2577">tx_timer_create</span></span>

<span data-ttu-id="298ca-2578">Skapa programtimer</span><span class="sxs-lookup"><span data-stu-id="298ca-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2579">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2579">Prototype</span></span>

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a><span data-ttu-id="298ca-2580">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2580">Description</span></span>

<span data-ttu-id="298ca-2581">Den här tjänsten skapar en programtimer med angiven förfallo funktion och periodisk.</span><span class="sxs-lookup"><span data-stu-id="298ca-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2582">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2582">Parameters</span></span>

- <span data-ttu-id="298ca-2583">**timer_ptr** Pekare till ett timer Control-Block</span><span class="sxs-lookup"><span data-stu-id="298ca-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="298ca-2584">**name_ptr** Pekar till namnet på timern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="298ca-2585">**expiration_function** Program funktion som anropas när timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="298ca-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="298ca-2586">**expiration_input** Inmatat för att skicka till Expires-funktionen när timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="298ca-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="298ca-2587">**initial_ticks** Anger det ursprungliga antalet Tick för förfallo datum för timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="298ca-2588">Giltiga värden är mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="298ca-2589">**reschedule_ticks** Anger antalet Tick för alla timer-förfaller efter den första.</span><span class="sxs-lookup"><span data-stu-id="298ca-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="298ca-2590">En noll för den här parametern gör timern till en timer med en *bild* .</span><span class="sxs-lookup"><span data-stu-id="298ca-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="298ca-2591">Annars, för periodiska timers, är de juridiska värdena mellan 1 och 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="298ca-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="298ca-2592">*När en timer för en bild har gått ut måste den återställas via tx_timer_change innan den kan aktive ras igen.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="298ca-2593">**auto_activate** Anger om timern aktive ras automatiskt när den skapas.</span><span class="sxs-lookup"><span data-stu-id="298ca-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="298ca-2594">Om det här värdet är **TX_AUTO_ACTIVATE** (0x01) blir timern aktiv.</span><span class="sxs-lookup"><span data-stu-id="298ca-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="298ca-2595">Annars, om värdet **TX_NO_ACTIVATE** (0x00) är markerat, skapas timern i ett icke-aktivt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="298ca-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="298ca-2596">I det här fallet är ett efterföljande **_tx_timer_activate_** tjänst anrop nödvändigt för att hämta den timer som faktiskt startades.</span><span class="sxs-lookup"><span data-stu-id="298ca-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2597">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2597">Return Values</span></span>

- <span data-ttu-id="298ca-2598">**TX_SUCCESS** (0x00) körning av programskapade program.</span><span class="sxs-lookup"><span data-stu-id="298ca-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="298ca-2599">**TX_TIMER_ERROR** (0X15) ogiltig pekare för program timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="298ca-2600">Antingen är pekaren NULL eller också har timern redan skapats.</span><span class="sxs-lookup"><span data-stu-id="298ca-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="298ca-2601">**TX_TICK_ERROR** (0X16) ogiltigt värde (noll) angavs för inledande Tick.</span><span class="sxs-lookup"><span data-stu-id="298ca-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="298ca-2602">En ogiltig aktivering har valts för **TX_ACTIVATE_ERROR** (0x17).</span><span class="sxs-lookup"><span data-stu-id="298ca-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="298ca-2603">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2604">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2604">Allowed From</span></span>

<span data-ttu-id="298ca-2605">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="298ca-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2606">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2606">Preemption Possible</span></span>

<span data-ttu-id="298ca-2607">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2608">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2608">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2609">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2609">See Also</span></span>

- <span data-ttu-id="298ca-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2610">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2611">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2613">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="298ca-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="298ca-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="298ca-2618">Inaktivera Application timer</span><span class="sxs-lookup"><span data-stu-id="298ca-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2619">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2620">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2620">Description</span></span>

<span data-ttu-id="298ca-2621">Den här tjänsten inaktiverar den angivna programtimern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="298ca-2622">Om timern redan är inaktive rad har den här tjänsten ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="298ca-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2623">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2623">Parameters</span></span>

- <span data-ttu-id="298ca-2624">**timer_ptr** Pekar till en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2625">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2625">Return Values</span></span>

- <span data-ttu-id="298ca-2626">**TX_SUCCESS** (0X00) slutförde inaktive ring av program.</span><span class="sxs-lookup"><span data-stu-id="298ca-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="298ca-2627">**TX_TIMER_ERROR** (0X15) ogiltig pekare för program timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2628">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2628">Allowed From</span></span>

<span data-ttu-id="298ca-2629">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2630">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2630">Preemption Possible</span></span>

<span data-ttu-id="298ca-2631">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2632">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2633">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2633">See Also</span></span>

- <span data-ttu-id="298ca-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2634">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2635">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2636">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2637">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="298ca-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="298ca-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2641">tx_timer_delete</span></span>

<span data-ttu-id="298ca-2642">Ta bort program timer</span><span class="sxs-lookup"><span data-stu-id="298ca-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2643">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="298ca-2644">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2644">Description</span></span>

<span data-ttu-id="298ca-2645">Den här tjänsten tar bort den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2646">*Det är programmets ansvar att förhindra användning av en borttagen timer.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2647">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2647">Parameters</span></span>

- <span data-ttu-id="298ca-2648">**timer_ptr** Pekar till en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2649">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2649">Return Values</span></span>

- <span data-ttu-id="298ca-2650">**TX_SUCCESS** (0x00)-slutförd borttagning av program tids gräns.</span><span class="sxs-lookup"><span data-stu-id="298ca-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="298ca-2651">**TX_TIMER_ERROR** (0X15) ogiltig pekare för program timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="298ca-2652">**TX_CALLER_ERROR** (0X13) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="298ca-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2653">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2653">Allowed From</span></span>

<span data-ttu-id="298ca-2654">Konversation</span><span class="sxs-lookup"><span data-stu-id="298ca-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2655">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2655">Preemption Possible</span></span>

<span data-ttu-id="298ca-2656">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2657">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2658">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2658">See Also</span></span>

- <span data-ttu-id="298ca-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2659">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2660">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2661">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="298ca-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="298ca-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2666">tx_timer_info_get</span></span>

<span data-ttu-id="298ca-2667">Hämta information om en programtimer</span><span class="sxs-lookup"><span data-stu-id="298ca-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2668">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="298ca-2669">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2669">Description</span></span>

<span data-ttu-id="298ca-2670">Den här tjänsten hämtar information om den angivna program-timern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2671">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2671">Parameters</span></span>

- <span data-ttu-id="298ca-2672">**timer_ptr** Pekar till en tidigare skapad program-timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="298ca-2673">**namn** Pekare till målet för visaren till timerns namn.</span><span class="sxs-lookup"><span data-stu-id="298ca-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="298ca-2674">**aktiv** Pekare till målet för den timer-aktiva indikeringen.</span><span class="sxs-lookup"><span data-stu-id="298ca-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="298ca-2675">Om timern är inaktiv eller om den här tjänsten anropas från själva timern returneras ett **TX_FALSE** -värde.</span><span class="sxs-lookup"><span data-stu-id="298ca-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="298ca-2676">Annars returneras ett **TX_TRUE** -värde om timern är aktiv.</span><span class="sxs-lookup"><span data-stu-id="298ca-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="298ca-2677">**remaining_ticks** Pekare till målet för antalet timer-Tick kvar innan timern upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="298ca-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="298ca-2678">**reschedule_ticks** Pekare till målet för antalet timer-Tick som ska användas för att automatiskt schemalägga denna timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="298ca-2679">Om värdet är noll är timern en One-bild och kommer inte att omplaneras.</span><span class="sxs-lookup"><span data-stu-id="298ca-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="298ca-2680">**next_timer** Pekare till målet för pekaren över nästa skapade program-timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2681">*Om du anger en **TX_NULL** för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2682">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2682">Return Values</span></span>

- <span data-ttu-id="298ca-2683">**TX_SUCCESS** (0x00) information om slutförd timer-information.</span><span class="sxs-lookup"><span data-stu-id="298ca-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="298ca-2684">**TX_TIMER_ERROR** (0X15) ogiltig pekare för program timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2685">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2685">Allowed From</span></span>

<span data-ttu-id="298ca-2686">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="298ca-2687">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="298ca-2687">Preemption Possible</span></span>

<span data-ttu-id="298ca-2688">Inga</span><span class="sxs-lookup"><span data-stu-id="298ca-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2689">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2689">Example</span></span>

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2690">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2690">See Also</span></span>

- <span data-ttu-id="298ca-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2691">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2692">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2693">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2695">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="298ca-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="298ca-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="298ca-2700">Hämta information om timer-prestanda</span><span class="sxs-lookup"><span data-stu-id="298ca-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2701">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="298ca-2702">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2702">Description</span></span>

<span data-ttu-id="298ca-2703">Den här tjänsten hämtar prestanda information om den angivna program tids gränsen.</span><span class="sxs-lookup"><span data-stu-id="298ca-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-2704">*ThreadX-biblioteket och programmet måste vara byggt med*  \* **TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined för den här tjänsten för att returnera prestanda information. \*</span><span class="sxs-lookup"><span data-stu-id="298ca-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="298ca-2705">Parametrar</span><span class="sxs-lookup"><span data-stu-id="298ca-2705">Parameters</span></span>
- <span data-ttu-id="298ca-2706">**timer_ptr** Pekare till tidigare skapad timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="298ca-2707">**aktiverar** Pekare till målet för antalet aktiverings begär Anden som utförts i denna timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="298ca-2708">**återaktiverar** Pekare till målet för antalet automatiska återaktiveringar som utförts på denna periodiska timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="298ca-2709">**inaktiverar** Pekare till målet för antalet förfrågningar om inaktivitet som utförts på denna timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="298ca-2710">**förfallo datum** Pekare till målet för antalet förfallo datum för den här timern.</span><span class="sxs-lookup"><span data-stu-id="298ca-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="298ca-2711">**expiration_adjusts** Pekare till målet för antalet interna utgångs justeringar som utförts i denna timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="298ca-2712">De här justeringarna görs i den tids lösa bearbetningen för timers som är större än standard storleken för timer-listan (som standard timers med förfallo datum som är större än 32 Tick).</span><span class="sxs-lookup"><span data-stu-id="298ca-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="298ca-2713">Lägg *Om du anger en TX_NULL för vilken parameter som helst är parametern inte obligatorisk.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2714">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2714">Return Values</span></span>

- <span data-ttu-id="298ca-2715">**TX_SUCCESS** (0x00) prestanda för slutförd timer.</span><span class="sxs-lookup"><span data-stu-id="298ca-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="298ca-2716">**TX_PTR_ERROR** (0X03) ogiltig timer-pekare.</span><span class="sxs-lookup"><span data-stu-id="298ca-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="298ca-2717">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2718">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2718">Allowed From</span></span>

<span data-ttu-id="298ca-2719">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2720">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2720">Example</span></span>

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2721">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2721">See Also</span></span>

- <span data-ttu-id="298ca-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2722">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2723">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2724">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2726">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="298ca-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="298ca-2730">Hämta information om system prestanda för timer</span><span class="sxs-lookup"><span data-stu-id="298ca-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="298ca-2731">Prototyp</span><span class="sxs-lookup"><span data-stu-id="298ca-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="298ca-2732">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="298ca-2732">Description</span></span>

<span data-ttu-id="298ca-2733">Den här tjänsten hämtar prestanda information om alla program timers i systemet.</span><span class="sxs-lookup"><span data-stu-id="298ca-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="298ca-2734">*ThreadX-biblioteket och programmet måste skapas med* **TX_TIMER_ENABLE_PERFORMANCE_INFO** som *definierats för den här tjänsten för att returnera prestanda information.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="298ca-2735">**Parametrar**</span><span class="sxs-lookup"><span data-stu-id="298ca-2735">**Parameters**</span></span>

- <span data-ttu-id="298ca-2736">**aktiverar** Pekare till målet för det totala antalet aktiverings begär Anden som utförts för alla timers.</span><span class="sxs-lookup"><span data-stu-id="298ca-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="298ca-2737">**återaktiverar** Pekare till målet för det totala antalet automatisk återaktivering som gjorts för alla periodiska timers.</span><span class="sxs-lookup"><span data-stu-id="298ca-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="298ca-2738">**inaktiverar** Pekare till målet för det totala antalet begär Anden om inaktive ring som utförts för alla timers.</span><span class="sxs-lookup"><span data-stu-id="298ca-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="298ca-2739">**förfallo datum** Pekare till målet för det totala antalet förfallo datum för alla timers.</span><span class="sxs-lookup"><span data-stu-id="298ca-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="298ca-2740">**expiration_adjusts** Pekare till målet för det totala antalet interna utgångs justeringar som utförts för alla timers.</span><span class="sxs-lookup"><span data-stu-id="298ca-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="298ca-2741">De här justeringarna görs i den tids lösa bearbetningen för timers som är större än standard storleken för timer-listan (som standard timers med förfallo datum som är större än 32 Tick).</span><span class="sxs-lookup"><span data-stu-id="298ca-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="298ca-2742">*Om du anger en **TX_NULL** för någon parameter anges att parametern inte krävs.*</span><span class="sxs-lookup"><span data-stu-id="298ca-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="298ca-2743">Retur värden</span><span class="sxs-lookup"><span data-stu-id="298ca-2743">Return Values</span></span>

- <span data-ttu-id="298ca-2744">**TX_SUCCESS** (0x00) system prestanda har hämtats.</span><span class="sxs-lookup"><span data-stu-id="298ca-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="298ca-2745">**TX_FEATURE_NOT_ENABLED** (0Xff) Det gick inte att kompilera systemet med prestanda information aktive rad.</span><span class="sxs-lookup"><span data-stu-id="298ca-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="298ca-2746">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="298ca-2746">Allowed From</span></span>

<span data-ttu-id="298ca-2747">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="298ca-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="298ca-2748">Exempel</span><span class="sxs-lookup"><span data-stu-id="298ca-2748">Example</span></span>

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="298ca-2749">Se även</span><span class="sxs-lookup"><span data-stu-id="298ca-2749">See Also</span></span>

- <span data-ttu-id="298ca-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="298ca-2750">tx_timer_activate</span></span>
- <span data-ttu-id="298ca-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="298ca-2751">tx_timer_change</span></span>
- <span data-ttu-id="298ca-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="298ca-2752">tx_timer_create</span></span>
- <span data-ttu-id="298ca-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="298ca-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="298ca-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="298ca-2754">tx_timer_delete</span></span>
- <span data-ttu-id="298ca-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="298ca-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="298ca-2756">tx_timer_performance_info_get</span></span>
