---
title: Kapitel 5 – generera spårnings-buffertar
description: Det här kapitlet innehåller en beskrivning av hur du skapar en Azure återställnings tider TraceX-händelsehubben och beskriver även det underliggande formatet för bufferten.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827522"
---
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="1c245-103">Kapitel 5 – generera spårnings-buffertar</span><span class="sxs-lookup"><span data-stu-id="1c245-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="1c245-104">Det här kapitlet innehåller en beskrivning av hur du skapar en Azure återställnings tider TraceX-händelsehubben och beskriver även det underliggande formatet för bufferten.</span><span class="sxs-lookup"><span data-stu-id="1c245-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="1c245-105">Stöd för ThreadX Event trace</span><span class="sxs-lookup"><span data-stu-id="1c245-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="1c245-106">ThreadX tillhandahåller inbyggt stöd för spårning av händelser för alla ThreadX-tjänster, ändringar i tråd tillstånd och användardefinierade händelser.</span><span class="sxs-lookup"><span data-stu-id="1c245-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="1c245-107">ThreadX Event – trace-funktionen har främst utformats som ett efter slakt verktyg för att analysera de senaste "n"-aktiviteterna i programmet.</span><span class="sxs-lookup"><span data-stu-id="1c245-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="1c245-108">Med hjälp av den här informationen kan utvecklaren upptäcka problem och/eller potentiella optimerings mål.</span><span class="sxs-lookup"><span data-stu-id="1c245-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="1c245-109">TraceX visar den buffert för händelse spårning som skapats av ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1c245-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="1c245-110">Följande beskriver hur du skapar bufferten och beskriver buffertens underliggande format.</span><span class="sxs-lookup"><span data-stu-id="1c245-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="1c245-111">Aktivera händelse spårning</span><span class="sxs-lookup"><span data-stu-id="1c245-111">Enabling Event Trace</span></span>

<span data-ttu-id="1c245-112">Om du vill aktivera händelse spårning definierar du tids stämplings konstanterna, skapar ThreadX-biblioteket med **TX_ENABLE_EVENT_TRACE** definierat och aktiverar spårning genom att anropa funktionen **tx_trace_enable** .</span><span class="sxs-lookup"><span data-stu-id="1c245-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="1c245-113">Definiera Time-Stamp konstanter</span><span class="sxs-lookup"><span data-stu-id="1c245-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="1c245-114">Konstanterna för tidsstämpel är utformade för att ge utvecklare kontrollen över den tids stämpling som används i händelse spårnings posterna.</span><span class="sxs-lookup"><span data-stu-id="1c245-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="1c245-115">De två konstanterna för tidsstämpel och deras standardvärden är följande:</span><span class="sxs-lookup"><span data-stu-id="1c245-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="1c245-116">Ovanstående konstanter definieras i **tx_port. h** och skapar en "falsk" tidstämpel som bara ökar med en för varje händelse.</span><span class="sxs-lookup"><span data-stu-id="1c245-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="1c245-117">Följande är ett exempel på en faktisk tidsstämpel-definition:</span><span class="sxs-lookup"><span data-stu-id="1c245-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="1c245-118">Ovanstående konstanter anger en 32-bitars timer som hämtas genom att läsa adressen 0x13000004.</span><span class="sxs-lookup"><span data-stu-id="1c245-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="1c245-119">De flesta programspecifika tidsstämplar bör konfigureras på liknande sätt.</span><span class="sxs-lookup"><span data-stu-id="1c245-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="1c245-120">Exportera den sökta kommandobufferten</span><span class="sxs-lookup"><span data-stu-id="1c245-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="1c245-121">TraceX kräver en spårningssession i ett binärt, Intel HEX eller Motorola S-Record-filformat på värden.</span><span class="sxs-lookup"><span data-stu-id="1c245-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="1c245-122">Det enklaste sättet att göra detta är att stoppa målet och instruera fel söknings programmet att dumpa det minnes utrymme som du angav för att ***tx_trace_enable*** funktionen i en fil på värden.</span><span class="sxs-lookup"><span data-stu-id="1c245-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="1c245-123">***Var noga med att inte stoppa målet i själva spårnings insamlings koden. Om du gör det kan det orsaka ogiltig spårnings information. Om programmet har stoppats i ThreadX, är det bäst att stega över alla spårnings infognings makron innan du påsöker en spårnings-buffert.***</span><span class="sxs-lookup"><span data-stu-id="1c245-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-124">*Bilaga D visar hur du dumpar spårningssessionen från en rad olika utvecklingsverktyg.*</span><span class="sxs-lookup"><span data-stu-id="1c245-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="1c245-125">API för utökad händelse spårning</span><span class="sxs-lookup"><span data-stu-id="1c245-125">Extended Event Trace API</span></span>

<span data-ttu-id="1c245-126">När ThreadX har skapats med **TX_ENABLE_EVENT_TRACE** definierat, är följande nya API: er för Event trace tillgängliga för programmet:</span><span class="sxs-lookup"><span data-stu-id="1c245-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="1c245-127">tx_trace_enable: *Aktivera händelse spårning*</span><span class="sxs-lookup"><span data-stu-id="1c245-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="1c245-128">tx_trace_event_filter: *filtrera angivna händelse (er)*</span><span class="sxs-lookup"><span data-stu-id="1c245-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="1c245-129">tx_trace_event_unfilter: *avfiltrera angivna händelse (er)*</span><span class="sxs-lookup"><span data-stu-id="1c245-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="1c245-130">tx_trace_disable: *inaktivera händelse spårning*</span><span class="sxs-lookup"><span data-stu-id="1c245-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="1c245-131">tx_trace_isr_enter_insert: *Infoga ISR ange spårnings händelse*</span><span class="sxs-lookup"><span data-stu-id="1c245-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="1c245-132">tx_trace_isr_exit_insert: *Infoga ISR-avsluta spårnings händelse*</span><span class="sxs-lookup"><span data-stu-id="1c245-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="1c245-133">tx_trace_buffer_full_notify: *Registrera fullständig program återanrop i spårnings buffert*</span><span class="sxs-lookup"><span data-stu-id="1c245-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="1c245-134">tx_trace_user_event_insert: *Infoga användar händelse*</span><span class="sxs-lookup"><span data-stu-id="1c245-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="1c245-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="1c245-135">tx_trace_enable</span></span>

<span data-ttu-id="1c245-136">Aktivera händelse spårning</span><span class="sxs-lookup"><span data-stu-id="1c245-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-137">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="1c245-138">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-138">Description</span></span>
<span data-ttu-id="1c245-139">Den här tjänsten aktiverar händelse spårning i ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1c245-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="1c245-140">Den sökta bufferten och det maximala antalet ThreadX-objekt tillhandahålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="1c245-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-141">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-142">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-142">Input Parameters</span></span>

- <span data-ttu-id="1c245-143">**trace_buffer_start**: pekar mot början av den användarspecifika spårningssessionen.</span><span class="sxs-lookup"><span data-stu-id="1c245-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="1c245-144">**trace_buffer_size**: det totala antalet byte i minnet för den sökta kommandobufferten.</span><span class="sxs-lookup"><span data-stu-id="1c245-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="1c245-145">Ju större kommandobufferten, desto fler poster kan de lagra.</span><span class="sxs-lookup"><span data-stu-id="1c245-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="1c245-146">**registry_entries**: antalet program ThreadX objekt som ska behållas i spårnings registret.</span><span class="sxs-lookup"><span data-stu-id="1c245-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="1c245-147">Registret används för att korrelera objekt adresser med objekt namn.</span><span class="sxs-lookup"><span data-stu-id="1c245-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="1c245-148">Detta är mycket användbart för verktyg för spårnings analys av GUI.</span><span class="sxs-lookup"><span data-stu-id="1c245-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="1c245-149">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-149">Return Values</span></span>

- <span data-ttu-id="1c245-150">**TX_SUCCESS** (0x00) aktive ras spårning av händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="1c245-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="1c245-151">Den angivna storleken för 0x05 () är för liten. **TX_SIZE_ERROR**</span><span class="sxs-lookup"><span data-stu-id="1c245-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="1c245-152">Det måste vara tillräckligt stort för spårnings huvudet, objekt registret och minst en spårnings post.</span><span class="sxs-lookup"><span data-stu-id="1c245-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="1c245-153">**TX_NOT_DONE** (0X20) händelse spårning har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="1c245-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="1c245-154">**TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="1c245-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-155">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-155">Allowed From</span></span>

<span data-ttu-id="1c245-156">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="1c245-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-157">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-158">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-158">See Also</span></span>

<span data-ttu-id="1c245-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="1c245-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="1c245-160">tx_trace_event_filter</span></span>

<span data-ttu-id="1c245-161">Filtrera angivna händelser</span><span class="sxs-lookup"><span data-stu-id="1c245-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-162">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="1c245-163">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-163">Description</span></span>

<span data-ttu-id="1c245-164">Den här tjänsten filtrerar den eller de angivna händelserna från att infogas i den aktiva spårningssessionen.</span><span class="sxs-lookup"><span data-stu-id="1c245-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="1c245-165">Observera att standardinställningen inga händelser filtreras efter att *tx_trace_enable* anropas.</span><span class="sxs-lookup"><span data-stu-id="1c245-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-166">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-167">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-167">Input Parameters</span></span>

- <span data-ttu-id="1c245-168">**event_filter_bits**: bitar som motsvarar händelser att filtrera.</span><span class="sxs-lookup"><span data-stu-id="1c245-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="1c245-169">Flera händelser kan filtreras genom att helt enkelt Oring lämpliga konstanter.</span><span class="sxs-lookup"><span data-stu-id="1c245-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="1c245-170">Giltiga konstanter för den här variabeln definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1c245-170">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="1c245-171">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-171">Return Values</span></span>

- <span data-ttu-id="1c245-172">**TX_SUCCESS** (0x00) händelse filter har slutförts.</span><span class="sxs-lookup"><span data-stu-id="1c245-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="1c245-173">**TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="1c245-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-174">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-174">Allowed From</span></span>

<span data-ttu-id="1c245-175">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="1c245-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-176">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-177">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-177">See Also</span></span>

<span data-ttu-id="1c245-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="1c245-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="1c245-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="1c245-180">Filtrera angivna händelser</span><span class="sxs-lookup"><span data-stu-id="1c245-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-181">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="1c245-182">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-182">Description</span></span>

<span data-ttu-id="1c245-183">Den här tjänsten avfiltrerar den eller de angivna händelse (er) som de ska infogas i den aktiva spårningssessionen.</span><span class="sxs-lookup"><span data-stu-id="1c245-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-184">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-185">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-185">Input Parameters</span></span>

- <span data-ttu-id="1c245-186">**event_unfilter_bits**: bitar som motsvarar händelser som ska avfiltreras.</span><span class="sxs-lookup"><span data-stu-id="1c245-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="1c245-187">Flera händelser kan avfiltreras genom att enkelt eller genom att kombinera lämpliga konstanter.</span><span class="sxs-lookup"><span data-stu-id="1c245-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="1c245-188">Giltiga konstanter för den här variabeln definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1c245-188">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="1c245-189">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-189">Return Values</span></span>

- <span data-ttu-id="1c245-190">**TX_SUCCESS** (0x00) händelse Avfiltrering slutfördes.</span><span class="sxs-lookup"><span data-stu-id="1c245-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="1c245-191">**TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="1c245-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-192">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-192">Allowed From</span></span>

<span data-ttu-id="1c245-193">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="1c245-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-194">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-195">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-195">See Also</span></span>

<span data-ttu-id="1c245-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="1c245-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="1c245-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="1c245-198">Inaktivera händelse spårning</span><span class="sxs-lookup"><span data-stu-id="1c245-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-199">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="1c245-200">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-200">Description</span></span>

<span data-ttu-id="1c245-201">Den här tjänsten inaktiverar händelse spårning i ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1c245-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="1c245-202">Detta kan vara användbart om programmet vill låsa den aktuella bufferten för händelse spårning och eventuellt transportera den externt under körnings tillfället.</span><span class="sxs-lookup"><span data-stu-id="1c245-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="1c245-203">När den är inaktive rad kan **tx_trace_enable** anropas för att börja spåra igen.</span><span class="sxs-lookup"><span data-stu-id="1c245-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-204">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-205">Input Parameters</span></span>

<span data-ttu-id="1c245-206">Inga.</span><span class="sxs-lookup"><span data-stu-id="1c245-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="1c245-207">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-207">Return Values</span></span>

- <span data-ttu-id="1c245-208">**TX_SUCCESS** (0x00) inaktive ring av händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="1c245-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="1c245-209">Händelse spårning för **TX_NOT_DONE** (0x20) har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="1c245-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="1c245-210">**TX_FEATURE_NOT_ENABLED** (0xFF)-systemet kompilerades inte med spårning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="1c245-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-211">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-211">Allowed From</span></span>

<span data-ttu-id="1c245-212">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="1c245-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-213">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-214">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-214">See Also</span></span>

<span data-ttu-id="1c245-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="1c245-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="1c245-217">Infoga händelse för ISR-retur</span><span class="sxs-lookup"><span data-stu-id="1c245-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-218">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="1c245-219">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-219">Description</span></span>

<span data-ttu-id="1c245-220">Den här tjänsten infogar ISR-händelsen retur i bufferten för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="1c245-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="1c245-221">Den bör anropas av programmet i början av ISR-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="1c245-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="1c245-222">Den angivna parametern ska identifiera den specifika ISR för programmet.</span><span class="sxs-lookup"><span data-stu-id="1c245-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-223">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-224">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-224">Input Parameters</span></span> 
- <span data-ttu-id="1c245-225">**isr_id**: Programspecifikt värde för att identifiera ISR.</span><span class="sxs-lookup"><span data-stu-id="1c245-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="1c245-226">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-226">Return Values</span></span>

<span data-ttu-id="1c245-227">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="1c245-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-228">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-228">Allowed From</span></span> 

<span data-ttu-id="1c245-229">ISR: er</span><span class="sxs-lookup"><span data-stu-id="1c245-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-230">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-231">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-231">See Also</span></span>

<span data-ttu-id="1c245-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="1c245-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="1c245-234">Infoga ISR-avsluts händelse</span><span class="sxs-lookup"><span data-stu-id="1c245-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-235">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="1c245-236">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-236">Description</span></span>

<span data-ttu-id="1c245-237">Den här tjänsten infogar händelsen ISR-post i kommandobufferten.</span><span class="sxs-lookup"><span data-stu-id="1c245-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="1c245-238">Den bör anropas av programmet i början av ISR-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="1c245-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="1c245-239">Den angivna parametern ska identifiera ISR till programmet.</span><span class="sxs-lookup"><span data-stu-id="1c245-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-240">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-241">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-241">Input Parameters</span></span> 

- <span data-ttu-id="1c245-242">**isr_id**: Programspecifikt värde för att identifiera ISR.</span><span class="sxs-lookup"><span data-stu-id="1c245-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="1c245-243">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-243">Return Values</span></span>

<span data-ttu-id="1c245-244">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="1c245-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-245">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-245">Allowed From</span></span>

<span data-ttu-id="1c245-246">ISR: er</span><span class="sxs-lookup"><span data-stu-id="1c245-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-247">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-248">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-248">See Also</span></span>

<span data-ttu-id="1c245-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="1c245-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="1c245-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="1c245-251">Registrera fullständig motringning för spårnings buffert</span><span class="sxs-lookup"><span data-stu-id="1c245-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-252">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="1c245-253">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-253">Description</span></span>

<span data-ttu-id="1c245-254">Den här tjänsten registrerar en återanrops funktion för program som anropas av ThreadX när spårnings-bufferten blir full.</span><span class="sxs-lookup"><span data-stu-id="1c245-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="1c245-255">Programmet kan sedan välja att inaktivera spårning och/eller eventuellt konfigurera en ny spårnings-buffert.</span><span class="sxs-lookup"><span data-stu-id="1c245-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-256">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-257">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-257">Input Parameters</span></span>

- <span data-ttu-id="1c245-258">**full_buffer_callback**: program funktion som anropas när kommandobufferten är full.</span><span class="sxs-lookup"><span data-stu-id="1c245-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="1c245-259">Värdet NULL inaktiverar återanropet av meddelandet.</span><span class="sxs-lookup"><span data-stu-id="1c245-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="1c245-260">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-260">Return Values</span></span>

<span data-ttu-id="1c245-261">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="1c245-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-262">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-262">Allowed From</span></span>

<span data-ttu-id="1c245-263">ISR: er</span><span class="sxs-lookup"><span data-stu-id="1c245-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-264">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-265">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-265">See Also</span></span>

<span data-ttu-id="1c245-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="1c245-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="1c245-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="1c245-268">Infoga användar händelse</span><span class="sxs-lookup"><span data-stu-id="1c245-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="1c245-269">Prototyp</span><span class="sxs-lookup"><span data-stu-id="1c245-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="1c245-270">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c245-270">Description</span></span>

<span data-ttu-id="1c245-271">Den här tjänsten infogar användar händelsen i den sökta bufferten.</span><span class="sxs-lookup"><span data-stu-id="1c245-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="1c245-272">Användar händelse-ID: n måste vara större än konstanten **TX_TRACE_USER_EVENT_START**, som definieras som 4096.</span><span class="sxs-lookup"><span data-stu-id="1c245-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="1c245-273">Den maximala användar händelsen definieras av konstant **TX_TRACE_USER_EVENT_END**, som definieras som 65535.</span><span class="sxs-lookup"><span data-stu-id="1c245-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="1c245-274">Alla händelser inom det här intervallet är tillgängliga för programmet.</span><span class="sxs-lookup"><span data-stu-id="1c245-274">All events within this range are available to the application.</span></span> <span data-ttu-id="1c245-275">Informations fälten är programspecifika.</span><span class="sxs-lookup"><span data-stu-id="1c245-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c245-276">ThreadX-biblioteket och programmet måste ha skapats med **TX_ENABLE_EVENT_TRACE** definierat för att spårning av händelser ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1c245-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="1c245-277">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="1c245-277">Input Parameters</span></span>

- <span data-ttu-id="1c245-278">**event_id**: identifiering av programspecifik händelse och måste börja vara större än **TX_TRACE_USER_EVENT_START** och mindre än eller lika med **TX_TRACE_USER_EVENT_END**.</span><span class="sxs-lookup"><span data-stu-id="1c245-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="1c245-279">**info_field_1**: programspecifikt informations fält.</span><span class="sxs-lookup"><span data-stu-id="1c245-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="1c245-280">**info_field_2**: programspecifikt informations fält.</span><span class="sxs-lookup"><span data-stu-id="1c245-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="1c245-281">**info_field_3**: programspecifikt informations fält.</span><span class="sxs-lookup"><span data-stu-id="1c245-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="1c245-282">**info_field_4**: programspecifikt informations fält.</span><span class="sxs-lookup"><span data-stu-id="1c245-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="1c245-283">Retur värden</span><span class="sxs-lookup"><span data-stu-id="1c245-283">Return Values</span></span>
- <span data-ttu-id="1c245-284">**TX_SUCCESS** (0x00) användar händelsen infogades.</span><span class="sxs-lookup"><span data-stu-id="1c245-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="1c245-285">Händelse spårning för **TX_NOT_DONE** (0x20) har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="1c245-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="1c245-286">**TX_FEATURE_NOT_ENABLED** (0xFF) systemet kompilerades inte med spårning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="1c245-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="1c245-287">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="1c245-287">Allowed From</span></span>

<span data-ttu-id="1c245-288">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="1c245-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="1c245-289">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c245-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="1c245-290">Se även</span><span class="sxs-lookup"><span data-stu-id="1c245-290">See Also</span></span>

<span data-ttu-id="1c245-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="1c245-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>