---
title: Kapitel 2 – API-referenser för körnings profil paket
description: I det här kapitlet dokumenteras de API-funktioner som tillhandahålls av EPK.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a198e48bdacbc141fb3de4670cc7ea5ba079612d
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377633"
---
#  <a name="chapter-2--execution-profile-kit-api-references"></a><span data-ttu-id="4466d-103">Kapitel 2 API-referenser för körnings profil paket</span><span class="sxs-lookup"><span data-stu-id="4466d-103">Chapter 2  Execution Profile Kit API References</span></span>

<span data-ttu-id="4466d-104">ThreadX-EPK ger till gång till funktioner för att hämta körnings profil informationen, enligt följande.</span><span class="sxs-lookup"><span data-stu-id="4466d-104">The ThreadX EPK provides access functions to get the execution profile information, as follows.</span></span>

| <span data-ttu-id="4466d-105">Funktions &nbsp; namn</span><span class="sxs-lookup"><span data-stu-id="4466d-105">Function&nbsp;Name</span></span> | <span data-ttu-id="4466d-106">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-106">Description</span></span> |
| --- | --- |
| <span data-ttu-id="4466d-107">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-107">_tx_execution_thread_time_reset</span></span> | <span data-ttu-id="4466d-108">Återställ den ackumulerade tiden för en tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-108">Reset the accumulated time for a thread.</span></span> |
| <span data-ttu-id="4466d-109">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-109">_tx_execution_thread_total_time_reset</span></span> | <span data-ttu-id="4466d-110">Återställ den ackumulerade totala tråd tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-110">Reset the accumulated total thread time.</span></span> |
| <span data-ttu-id="4466d-111">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-111">_tx_execution_isr_time_reset</span></span> | <span data-ttu-id="4466d-112">Återställ den ackumulerade ISR-tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-112">Reset the accumulated ISR time.</span></span> |
| <span data-ttu-id="4466d-113">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-113">_tx_execution_idle_time_reset</span></span> | <span data-ttu-id="4466d-114">Återställ den ackumulerade inaktiva tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-114">Reset the accumulated idle time.</span></span> |
| <span data-ttu-id="4466d-115">_tx_execution_thread_time_get hämta den ackumulerade tiden för en tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-115">_tx_execution_thread_time_get Get the accumulated time for a thread.</span></span> |
| <span data-ttu-id="4466d-116">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-116">_tx_execution_thread_total_time_get</span></span> | <span data-ttu-id="4466d-117">Hämta den ackumulerade total tråd tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-117">Get the accumulated total thread time.</span></span> |
| <span data-ttu-id="4466d-118">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-118">_tx_execution_isr_time_get</span></span> | <span data-ttu-id="4466d-119">Hämta den ackumulerade ISR-tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-119">Get the accumulated ISR time.</span></span> |
| <span data-ttu-id="4466d-120">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-120">_tx_execution_idle_time_get</span></span> | <span data-ttu-id="4466d-121">Hämta den ackumulerade inaktiva tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-121">Get the accumulated idle time.</span></span> |

##  <a name="_tx_execution_thread_time_reset"></a><span data-ttu-id="4466d-122">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-122">_tx_execution_thread_time_reset</span></span>

<span data-ttu-id="4466d-123">Återställ den ackumulerade tiden för en tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-123">Reset the accumulated time for a thread.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-124">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-124">Prototype</span></span>

```C
UINT _tx_execution_thread_time_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="4466d-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-125">Description</span></span>

<span data-ttu-id="4466d-126">Den här tjänsten anger den ackumulerade tråd körnings tiden tillbaka till noll.</span><span class="sxs-lookup"><span data-stu-id="4466d-126">This service sets the accumulated thread execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-127">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-127">Input Parameters</span></span>

- <span data-ttu-id="4466d-128">**thread_ptr** Pekare till tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-128">**thread_ptr** Pointer to thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-129">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-129">Return Values</span></span>

- <span data-ttu-id="4466d-130">**TX_SUCCESS** (0X00) lyckades EPK-återställning.</span><span class="sxs-lookup"><span data-stu-id="4466d-130">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-131">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-131">Allowed From</span></span>

<span data-ttu-id="4466d-132">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-132">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-133">Example</span></span>

```c
/* Reset the execution time for thread_0.  */
status =  tx_execution_thread_time_reset(&thread_0);

/* If status is TX_SUCCESS thread_0's execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-134">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-134">See Also</span></span>

- <span data-ttu-id="4466d-135">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-135">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-136">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-136">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-137">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-137">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-138">tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-138">tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-139">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-139">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-140">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-140">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="4466d-141">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-141">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_total_time_reset"></a><span data-ttu-id="4466d-142">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-142">_tx_execution_thread_total_time_reset</span></span>

<span data-ttu-id="4466d-143">Återställ den totala ackumulerade tråd tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-143">Reset the total accumulated thread time.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-144">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-144">Prototype</span></span>
```c
UINT _tx_execution_thread_total_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="4466d-145">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-145">Description</span></span>

<span data-ttu-id="4466d-146">Den här tjänsten anger den ackumulerade totala körnings tiden för trådar tillbaka till noll.</span><span class="sxs-lookup"><span data-stu-id="4466d-146">This service sets the accumulated total thread execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-147">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-147">Input Parameters</span></span>

<span data-ttu-id="4466d-148">Inga.</span><span class="sxs-lookup"><span data-stu-id="4466d-148">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-149">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-149">Return Values</span></span>

- <span data-ttu-id="4466d-150">**TX_SUCCESS** (0X00) lyckades EPK-återställning.</span><span class="sxs-lookup"><span data-stu-id="4466d-150">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-151">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-151">Allowed From</span></span>

- <span data-ttu-id="4466d-152">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-152">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-153">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-153">Example</span></span>

```c
/* Reset the total execution time for all threads.  */
status =  tx_execution_thread_total_time_reset();

/* If status is TX_SUCCESS the total thread execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-154">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-154">See Also</span></span>

- <span data-ttu-id="4466d-155">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-155">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-156">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-156">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-157">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-157">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-158">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-158">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-159">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-159">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-160">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-160">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="4466d-161">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-161">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_isr_time_reset"></a><span data-ttu-id="4466d-162">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-162">_tx_execution_isr_time_reset</span></span>

<span data-ttu-id="4466d-163">Återställ den ackumulerade ISR-tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-163">Reset the accumulated ISR time.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-164">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-164">Prototype</span></span>

```c
UINT _tx_execution_isr_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="4466d-165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-165">Description</span></span>

<span data-ttu-id="4466d-166">Den här tjänsten anger ackumulerad total ISR-körnings tid tillbaka till noll.</span><span class="sxs-lookup"><span data-stu-id="4466d-166">This service sets the accumulated total ISR execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-167">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-167">Input Parameters</span></span>

<span data-ttu-id="4466d-168">Inga.</span><span class="sxs-lookup"><span data-stu-id="4466d-168">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-169">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-169">Return Values</span></span>

- <span data-ttu-id="4466d-170">**TX_SUCCESS** (0X00) lyckades EPK-återställning.</span><span class="sxs-lookup"><span data-stu-id="4466d-170">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

<span data-ttu-id="4466d-171">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="4466d-171">**Allowed From**</span></span>

- <span data-ttu-id="4466d-172">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-172">Threads, timers, and ISRs</span></span>

<span data-ttu-id="4466d-173">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="4466d-173">**Example**</span></span>

```c
/* Reset the total ISR execution time.  */
status =  tx_execution_isr_time_reset();

/* If status is TX_SUCCESS the total ISR execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-174">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-174">See Also</span></span>

- <span data-ttu-id="4466d-175">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-175">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-176">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-176">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-177">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-177">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-178">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-178">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-179">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-179">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-180">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-180">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="4466d-181">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-181">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_idle_time_reset"></a><span data-ttu-id="4466d-182">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-182">_tx_execution_idle_time_reset</span></span>

<span data-ttu-id="4466d-183">Återställ den ackumulerade inaktiva tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-183">Reset the accumulated idle time.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-184">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-184">Prototype</span></span>

```c
UINT _tx_execution_idle_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="4466d-185">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-185">Description</span></span>

<span data-ttu-id="4466d-186">Den här tjänsten anger den ackumulerade totala inaktiva körnings tiden tillbaka till noll.</span><span class="sxs-lookup"><span data-stu-id="4466d-186">This service sets the accumulated total idle execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-187">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-187">Input Parameters</span></span>

<span data-ttu-id="4466d-188">Inga.</span><span class="sxs-lookup"><span data-stu-id="4466d-188">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-189">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-189">Return Values</span></span>

- <span data-ttu-id="4466d-190">**TX_SUCCESS** (0X00) lyckades EPK-återställning.</span><span class="sxs-lookup"><span data-stu-id="4466d-190">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-191">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-191">Allowed From</span></span>

- <span data-ttu-id="4466d-192">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-192">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-193">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-193">Example</span></span>

```c
/* Reset the total idle execution time.  */
status =  tx_execution_idle_time_reset();

/* If status is TX_SUCCESS the total idle execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-194">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-194">See Also</span></span>

- <span data-ttu-id="4466d-195">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-195">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-196">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-196">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-197">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-197">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-198">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-198">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-199">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-199">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-200">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-200">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="4466d-201">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-201">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_time_get"></a><span data-ttu-id="4466d-202">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-202">_tx_execution_thread_time_get</span></span>

<span data-ttu-id="4466d-203">Hämta den ackumulerade tiden för en tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-203">Get the accumulated time for a thread.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-204">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-204">Prototype</span></span>

```c
UINT _tx_execution_thread_time_get(
    TX_THREAD *thread_ptr,
    EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="4466d-205">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-205">Description</span></span>

<span data-ttu-id="4466d-206">Den här tjänsten hämtar den ackumulerade körnings tiden för en tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-206">This service gets the accumulated execution time for a thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-207">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-207">Input Parameters</span></span>

- <span data-ttu-id="4466d-208">**thread_ptr** Pekare till tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-208">**thread_ptr** Pointer to thread.</span></span>

- <span data-ttu-id="4466d-209">**total_time** Målet för trådens \' körnings tid.</span><span class="sxs-lookup"><span data-stu-id="4466d-209">**total_time** Destination for thread\'s execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-210">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-210">Return Values</span></span>

- <span data-ttu-id="4466d-211">**TX_SUCCESS** (0X00) lyckades EPK Time get.</span><span class="sxs-lookup"><span data-stu-id="4466d-211">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-212">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-212">Allowed From</span></span>

<span data-ttu-id="4466d-213">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-213">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-214">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-214">Example</span></span>

```c

/* Get the total thread execution time for thread_0.  */
status =  tx_execution_thread_time_get(&thread_0, &execution_time);

/* If status is TX_SUCCESS, execution_time contains the thread's
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-215">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-215">See Also</span></span>

- <span data-ttu-id="4466d-216">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-216">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-217">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-217">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-218">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-218">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-219">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-219">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-220">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-220">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-221">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-221">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="4466d-222">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-222">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_total_time_get"></a><span data-ttu-id="4466d-223">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-223">_tx_execution_thread_total_time_get</span></span>

<span data-ttu-id="4466d-224">Hämta den ackumulerade trådens sammanlagda tid.</span><span class="sxs-lookup"><span data-stu-id="4466d-224">Get the accumulated thread total time.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-225">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-225">Prototype</span></span>

```c
UINT _tx_execution_thread_total_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="4466d-226">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-226">Description</span></span>

<span data-ttu-id="4466d-227">Den här tjänsten hämtar den ackumulerade total körnings tiden för tråden.</span><span class="sxs-lookup"><span data-stu-id="4466d-227">This service gets the accumulated total thread execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-228">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-228">Input Parameters</span></span>

- <span data-ttu-id="4466d-229">**total_time** Mål för total körnings tid för tråd.</span><span class="sxs-lookup"><span data-stu-id="4466d-229">**total_time** Destination for total thread execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-230">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-230">Return Values</span></span>

- <span data-ttu-id="4466d-231">**TX_SUCCESS** (0X00) lyckades EPK Time get.</span><span class="sxs-lookup"><span data-stu-id="4466d-231">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-232">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-232">Allowed From</span></span>

- <span data-ttu-id="4466d-233">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-233">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-234">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-234">Example</span></span>

```c
EXECUTION_TIME *execution_time;

/* Get the total thread execution time.  */
status =  tx_execution_thread_total_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the thread
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-235">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-235">See Also</span></span>

- <span data-ttu-id="4466d-236">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-236">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-237">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-237">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-238">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-238">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-239">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-239">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-240">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-240">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-241">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-241">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="4466d-242">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-242">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_isr_time_get"></a><span data-ttu-id="4466d-243">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-243">_tx_execution_isr_time_get</span></span>

<span data-ttu-id="4466d-244">Hämta den ackumulerade ISR-tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-244">Get the accumulated ISR time.</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-245">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-245">Prototype</span></span>

```c
UINT _tx_execution_isr_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="4466d-246">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-246">Description</span></span>

<span data-ttu-id="4466d-247">Den här tjänsten hämtar den ackumulerade ISR-körnings tiden.</span><span class="sxs-lookup"><span data-stu-id="4466d-247">This service gets the accumulated ISR execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-248">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-248">Input Parameters</span></span>

- <span data-ttu-id="4466d-249">**total_time** Mål för total ISR-körnings tid.</span><span class="sxs-lookup"><span data-stu-id="4466d-249">**total_time** Destination for total ISR execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-250">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-250">Return Values</span></span>

- <span data-ttu-id="4466d-251">**TX_SUCCESS** (0X00) lyckades EPK Time get.</span><span class="sxs-lookup"><span data-stu-id="4466d-251">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-252">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-252">Allowed From</span></span>

<span data-ttu-id="4466d-253">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-253">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-254">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-254">Example</span></span>

```c
EXECUTION_TIME  *execution_time;

/* Get the total ISR execution time.  */
status =  tx_execution_isr_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the ISR
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-255">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-255">See Also</span></span>

- <span data-ttu-id="4466d-256">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-256">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-257">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-257">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-258">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-258">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-259">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-259">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-260">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-260">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-261">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-261">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-262">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-262">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_idle_time_get"></a><span data-ttu-id="4466d-263">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-263">_tx_execution_idle_time_get</span></span>

### <a name="get-the-accumulated-idle-time"></a><span data-ttu-id="4466d-264">Hämta den ackumulerade inaktiva tiden</span><span class="sxs-lookup"><span data-stu-id="4466d-264">Get the accumulated idle time</span></span>

### <a name="prototype"></a><span data-ttu-id="4466d-265">Prototyp</span><span class="sxs-lookup"><span data-stu-id="4466d-265">Prototype</span></span>

```c
UINT _tx_execution_idle_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="4466d-266">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4466d-266">Description</span></span>

<span data-ttu-id="4466d-267">Den här tjänsten hämtar den ackumulerade körnings tiden för inaktivitet.</span><span class="sxs-lookup"><span data-stu-id="4466d-267">This service gets the accumulated idle execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4466d-268">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="4466d-268">Input Parameters</span></span>

- <span data-ttu-id="4466d-269">**total_time** Mål för total körnings tid för inaktivitet.</span><span class="sxs-lookup"><span data-stu-id="4466d-269">**total_time** Destination for total idle execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="4466d-270">Retur värden</span><span class="sxs-lookup"><span data-stu-id="4466d-270">Return Values</span></span>

- <span data-ttu-id="4466d-271">**TX_SUCCESS** (0X00) lyckades EPK Time get.</span><span class="sxs-lookup"><span data-stu-id="4466d-271">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4466d-272">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="4466d-272">Allowed From</span></span>

- <span data-ttu-id="4466d-273">Trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="4466d-273">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="4466d-274">Exempel</span><span class="sxs-lookup"><span data-stu-id="4466d-274">Example</span></span>

```c
EXECUTION_TIME  *execution_time;

/* Get the total idle execution time.  */
status =  tx_execution_idle_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the idle
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="4466d-275">Se även</span><span class="sxs-lookup"><span data-stu-id="4466d-275">See Also</span></span>

- <span data-ttu-id="4466d-276">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-276">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="4466d-277">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-277">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="4466d-278">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-278">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="4466d-279">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="4466d-279">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="4466d-280">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-280">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="4466d-281">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-281">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="4466d-282">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="4466d-282">_tx_execution_isr_time_get</span></span>
