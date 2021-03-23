---
title: Kapitel 11 – format för Event trace-buffert
description: ThreadX tillhandahåller inbyggt stöd för händelse spårning för alla Azure återställnings tider ThreadX-tjänster, ändringar i tråd tillstånd och användardefinierade händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827576"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="29697-103">Kapitel 11 – format för Event trace-buffert</span><span class="sxs-lookup"><span data-stu-id="29697-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="29697-104">Azure återställnings tider ThreadX innehåller inbyggt stöd för händelse spårning för alla ThreadX-tjänster, ändringar i tråd tillstånd och användardefinierade händelser.</span><span class="sxs-lookup"><span data-stu-id="29697-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="29697-105">Om du vill använda händelse spårning skapar du bara ThreadX-, NetX-och FileX-biblioteken med **TX_ENABLE_EVENT_TRACE** definierat och aktiverar spårning genom att anropa funktionen **_tx_trace_enable_** .</span><span class="sxs-lookup"><span data-stu-id="29697-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="29697-106">I det här kapitlet beskrivs processen.</span><span class="sxs-lookup"><span data-stu-id="29697-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="29697-107">Händelse spårnings format</span><span class="sxs-lookup"><span data-stu-id="29697-107">Event Trace Format</span></span>

<span data-ttu-id="29697-108">Formatet på ThreadX är uppdelat i tre delar, nämligen kontroll rubriken, objekt registret och spårnings posterna.</span><span class="sxs-lookup"><span data-stu-id="29697-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="29697-109">I följande avsnitt beskrivs den allmänna layouten för ThreadX Event trace buffer:</span><span class="sxs-lookup"><span data-stu-id="29697-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="29697-110">**Kontroll rubrik**</span><span class="sxs-lookup"><span data-stu-id="29697-110">**Control Header**</span></span>

<span data-ttu-id="29697-111">**Objekt register post 0**</span><span class="sxs-lookup"><span data-stu-id="29697-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="29697-112">**…**</span><span class="sxs-lookup"><span data-stu-id="29697-112">**…**</span></span>

<span data-ttu-id="29697-113">**Objekt register post "n"**</span><span class="sxs-lookup"><span data-stu-id="29697-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="29697-114">**Händelse spårnings post 0**</span><span class="sxs-lookup"><span data-stu-id="29697-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="29697-115">**…**</span><span class="sxs-lookup"><span data-stu-id="29697-115">**…**</span></span>

<span data-ttu-id="29697-116">**Händelse spårnings post "n"**</span><span class="sxs-lookup"><span data-stu-id="29697-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="29697-117">Kontroll rubrik för händelse spårning</span><span class="sxs-lookup"><span data-stu-id="29697-117">Event Trace Control Header</span></span>

<span data-ttu-id="29697-118">Kontroll rubriken definierar den exakta layouten för Event trace-bufferten.</span><span class="sxs-lookup"><span data-stu-id="29697-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="29697-119">Detta inkluderar hur många ThreadX-objekt som kan registreras och hur många händelser som kan registreras.</span><span class="sxs-lookup"><span data-stu-id="29697-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="29697-120">Dessutom definierar kontroll rubriken var var och en av elementen i kommandobufferten finns.</span><span class="sxs-lookup"><span data-stu-id="29697-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="29697-121">Följande data struktur definierar kontroll rubriken:</span><span class="sxs-lookup"><span data-stu-id="29697-121">The following data structure defines the control header:</span></span>

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a><span data-ttu-id="29697-122">ID för kontroll huvud</span><span class="sxs-lookup"><span data-stu-id="29697-122">Control Header ID</span></span>

<span data-ttu-id="29697-123">Kontroll huvudets ID består av 32-bitars HEX-värdet för 0x54585442, som motsvarar ASCII-tecknen ***TXTB***.</span><span class="sxs-lookup"><span data-stu-id="29697-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="29697-124">Eftersom det här värdet skrivs som en 32-bitars osignerad variabel, kan den också användas för att identifiera den här buffertens endian-värde.</span><span class="sxs-lookup"><span data-stu-id="29697-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="29697-125">Om värdet i de första fyra byes i minnet till exempel är 0x54, 0x58, 0x54, 0x42 skrevs Event trace-bufferten i big endian format.</span><span class="sxs-lookup"><span data-stu-id="29697-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="29697-126">Annars skrevs händelsespårningssessionen i little endian format.</span><span class="sxs-lookup"><span data-stu-id="29697-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="29697-127">Giltig timer-mask</span><span class="sxs-lookup"><span data-stu-id="29697-127">Timer Valid Mask</span></span>

<span data-ttu-id="29697-128">Den giltiga tids masken definierar hur många bitar av tidsstämpeln i de faktiska spårnings posterna för händelsen som är giltiga.</span><span class="sxs-lookup"><span data-stu-id="29697-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="29697-129">Om till exempel en Time-stämpel-källa har 16 bitar, ska värdet i det här fältet vara 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="29697-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="29697-130">En 32-bitars Time-tag-källa har värdet 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="29697-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="29697-131">Det här värdet definieras av \***TX_TRACE_TIME_MASK** _ konstanten i _ *_tx_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="29697-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="29697-132">Spårnings bas adress</span><span class="sxs-lookup"><span data-stu-id="29697-132">Trace Base Address</span></span>

<span data-ttu-id="29697-133">Den sökta bas adressen är den adress som programmet angav som början på spårningssessionen i ***tx_trace_enable*** -anropet.</span><span class="sxs-lookup"><span data-stu-id="29697-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="29697-134">Den här adressen upprätthålls för den enda användningen av analys verktyget för att härleda bufferrelative-förskjutningar för de olika elementen i bufferten.</span><span class="sxs-lookup"><span data-stu-id="29697-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="29697-135">Till exempel beräknas den relativa förskjutningen för den aktuella händelsen i kommandobufferten med enkel subtraktion av bas adressen från den aktuella händelse adressen.</span><span class="sxs-lookup"><span data-stu-id="29697-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="29697-136">Start-och slut punkter för registret</span><span class="sxs-lookup"><span data-stu-id="29697-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="29697-137">Start pekaren för registret pekar på adressen till den första objekt register posten, medan slut punkten för registret pekar på snabb adressen till adressen... /mediately följer den sista register posten.</span><span class="sxs-lookup"><span data-stu-id="29697-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="29697-138">Dessa värden konfigureras under den *tx_trace_enable* bearbetningen och ändras inte under spårnings tiden.</span><span class="sxs-lookup"><span data-stu-id="29697-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="29697-139">Register namn storlek</span><span class="sxs-lookup"><span data-stu-id="29697-139">Registry Name Size</span></span>

<span data-ttu-id="29697-140">Register namnets storlek definierar den maximala storleken i byte för varje objekt namn i register posten och definieras av symbolen \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span><span class="sxs-lookup"><span data-stu-id="29697-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="29697-141">Standardvärdet är 32 och definieras i _*_tx_trace. h_*_.</span><span class="sxs-lookup"><span data-stu-id="29697-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="29697-142">Objekt namnet motsvarar det namn som angavs av programmet när objektet skapades.</span><span class="sxs-lookup"><span data-stu-id="29697-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="29697-143">Objekt register namnet för en tråd är till exempel det namn som tillhandahålls av programmet till mappen _ *_tx_thread_create_* \*.</span><span class="sxs-lookup"><span data-stu-id="29697-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="29697-144">Buffertens start-och slut punkter</span><span class="sxs-lookup"><span data-stu-id="29697-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="29697-145">Start pekaren för Event trace buffer pekar mot adressen för den första spårnings posten, medan register slut punkten pekar på snabb meddelandet för adress. /mediately efter den sista spårnings posten.</span><span class="sxs-lookup"><span data-stu-id="29697-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="29697-146">Dessa värden konfigureras under ***tx_trace_enable</*** bearbetning och ändras inte under spårnings tiden.</span><span class="sxs-lookup"><span data-stu-id="29697-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="29697-147">Aktuell buffert pekare</span><span class="sxs-lookup"><span data-stu-id="29697-147">Current Buffer Pointer</span></span>

<span data-ttu-id="29697-148">Den aktuella pekaren för Event trace buffer pekar på den äldsta spårnings postens adress.</span><span class="sxs-lookup"><span data-stu-id="29697-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="29697-149">Eftersom spårnings posterna upprätthålls i en cirkulär lista, representerar den aktuella bufferten också nästa spårnings post som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="29697-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="29697-150">Objekt register för händelse spårning</span><span class="sxs-lookup"><span data-stu-id="29697-150">Event Trace Object Registry</span></span>

<span data-ttu-id="29697-151">Händelse spårnings objekt registret innehåller \***n** _ objekt register poster som motsvarar de objekt som skapats av programmet.</span><span class="sxs-lookup"><span data-stu-id="29697-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="29697-152">Huvud syftet med objekt registret är för externa analys verktyg för att korrelera faktiska objekt namn med objekt adresser för spårningens buffert poster.</span><span class="sxs-lookup"><span data-stu-id="29697-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="29697-153">Antalet register poster som anges av programmet i _ *_tx_trace_enable_*\* anropa.</span><span class="sxs-lookup"><span data-stu-id="29697-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="29697-154">Varje objekt register post innehåller information om ett specifik ThreadX-objekt som tidigare har skapats av programmet.</span><span class="sxs-lookup"><span data-stu-id="29697-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="29697-155">Följande data struktur definierar varje objekt register post:</span><span class="sxs-lookup"><span data-stu-id="29697-155">The following data structure defines each object registry entry:</span></span>

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a><span data-ttu-id="29697-156">Flagga för objekt tillgänglig</span><span class="sxs-lookup"><span data-stu-id="29697-156">Object Available Flag</span></span>

<span data-ttu-id="29697-157">Flaggan objekt available är inställd på 1 om objektets register post är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="29697-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="29697-158">Annars, om värdet inte är 1, är objekt register posten inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="29697-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="29697-159">Observera att posten fortfarande kan innehålla giltig information trots att den är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="29697-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="29697-160">Objekt post typ</span><span class="sxs-lookup"><span data-stu-id="29697-160">Object Entry Type</span></span>

<span data-ttu-id="29697-161">Objekt post typen identifierar objekt typen i den här posten.</span><span class="sxs-lookup"><span data-stu-id="29697-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="29697-162">Följande är en lista över giltiga objekt typer:</span><span class="sxs-lookup"><span data-stu-id="29697-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="29697-163">**Värde**</span><span class="sxs-lookup"><span data-stu-id="29697-163">**Value**</span></span> | <span data-ttu-id="29697-164">**Objekt typ**</span><span class="sxs-lookup"><span data-stu-id="29697-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="29697-165">0</span><span class="sxs-lookup"><span data-stu-id="29697-165">0</span></span>         | <span data-ttu-id="29697-166">Ogiltig</span><span class="sxs-lookup"><span data-stu-id="29697-166">Not Valid</span></span>       |
| <span data-ttu-id="29697-167">1</span><span class="sxs-lookup"><span data-stu-id="29697-167">1</span></span>         | <span data-ttu-id="29697-168">Trådtoken</span><span class="sxs-lookup"><span data-stu-id="29697-168">Thread</span></span>          |
| <span data-ttu-id="29697-169">2</span><span class="sxs-lookup"><span data-stu-id="29697-169">2</span></span>         | <span data-ttu-id="29697-170">Timer</span><span class="sxs-lookup"><span data-stu-id="29697-170">Timer</span></span> |
| <span data-ttu-id="29697-171">3</span><span class="sxs-lookup"><span data-stu-id="29697-171">3</span></span>         | <span data-ttu-id="29697-172">Kö</span><span class="sxs-lookup"><span data-stu-id="29697-172">Queue</span></span> |
| <span data-ttu-id="29697-173">4</span><span class="sxs-lookup"><span data-stu-id="29697-173">4</span></span>         | <span data-ttu-id="29697-174">Semafor</span><span class="sxs-lookup"><span data-stu-id="29697-174">Semaphore</span></span> |
| <span data-ttu-id="29697-175">5</span><span class="sxs-lookup"><span data-stu-id="29697-175">5</span></span>         | <span data-ttu-id="29697-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="29697-176">Mutex</span></span> |
| <span data-ttu-id="29697-177">6</span><span class="sxs-lookup"><span data-stu-id="29697-177">6</span></span>         | <span data-ttu-id="29697-178">Händelse flaggor grupp</span><span class="sxs-lookup"><span data-stu-id="29697-178">Event Flags Group</span></span> |
| <span data-ttu-id="29697-179">7</span><span class="sxs-lookup"><span data-stu-id="29697-179">7</span></span>         | <span data-ttu-id="29697-180">Blockera pool</span><span class="sxs-lookup"><span data-stu-id="29697-180">Block Pool</span></span> |
| <span data-ttu-id="29697-181">8</span><span class="sxs-lookup"><span data-stu-id="29697-181">8</span></span>         | <span data-ttu-id="29697-182">Byte-pool</span><span class="sxs-lookup"><span data-stu-id="29697-182">Byte Pool</span></span> |
| <span data-ttu-id="29697-183">9</span><span class="sxs-lookup"><span data-stu-id="29697-183">9</span></span>         | <span data-ttu-id="29697-184">.. /media</span><span class="sxs-lookup"><span data-stu-id="29697-184">../media</span></span> |
| <span data-ttu-id="29697-185">10</span><span class="sxs-lookup"><span data-stu-id="29697-185">10</span></span>        | <span data-ttu-id="29697-186">Fil</span><span class="sxs-lookup"><span data-stu-id="29697-186">File</span></span> |
| <span data-ttu-id="29697-187">11</span><span class="sxs-lookup"><span data-stu-id="29697-187">11</span></span>        | <span data-ttu-id="29697-188">IP-adress</span><span class="sxs-lookup"><span data-stu-id="29697-188">IP</span></span> |
| <span data-ttu-id="29697-189">12</span><span class="sxs-lookup"><span data-stu-id="29697-189">12</span></span>        | <span data-ttu-id="29697-190">Paketets pool</span><span class="sxs-lookup"><span data-stu-id="29697-190">Packet Pool</span></span> |
| <span data-ttu-id="29697-191">13</span><span class="sxs-lookup"><span data-stu-id="29697-191">13</span></span>        | <span data-ttu-id="29697-192">TCP-socket</span><span class="sxs-lookup"><span data-stu-id="29697-192">TCP Socket</span></span> |
| <span data-ttu-id="29697-193">14</span><span class="sxs-lookup"><span data-stu-id="29697-193">14</span></span>        | <span data-ttu-id="29697-194">UDP-socket</span><span class="sxs-lookup"><span data-stu-id="29697-194">UDP Socket</span></span> |
| <span data-ttu-id="29697-195">15-20</span><span class="sxs-lookup"><span data-stu-id="29697-195">15-20</span></span>     | <span data-ttu-id="29697-196">Reserverat</span><span class="sxs-lookup"><span data-stu-id="29697-196">Reserved</span></span> |  
| <span data-ttu-id="29697-197">21</span><span class="sxs-lookup"><span data-stu-id="29697-197">21</span></span>        | <span data-ttu-id="29697-198">USB-värd, stack enhet</span><span class="sxs-lookup"><span data-stu-id="29697-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="29697-199">22</span><span class="sxs-lookup"><span data-stu-id="29697-199">22</span></span>        | <span data-ttu-id="29697-200">Gränssnitt för stack för USB-värd</span><span class="sxs-lookup"><span data-stu-id="29697-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="29697-201">23</span><span class="sxs-lookup"><span data-stu-id="29697-201">23</span></span>        | <span data-ttu-id="29697-202">Slut punkt för USB-värd</span><span class="sxs-lookup"><span data-stu-id="29697-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="29697-203">24</span><span class="sxs-lookup"><span data-stu-id="29697-203">24</span></span>        | <span data-ttu-id="29697-204">USB-värd klass</span><span class="sxs-lookup"><span data-stu-id="29697-204">USB Host Class</span></span> |
| <span data-ttu-id="29697-205">25</span><span class="sxs-lookup"><span data-stu-id="29697-205">25</span></span>        | <span data-ttu-id="29697-206">USB-enhet</span><span class="sxs-lookup"><span data-stu-id="29697-206">USB Device</span></span> |
| <span data-ttu-id="29697-207">26</span><span class="sxs-lookup"><span data-stu-id="29697-207">26</span></span>        | <span data-ttu-id="29697-208">USB-enhets gränssnitt</span><span class="sxs-lookup"><span data-stu-id="29697-208">USB Device Interface</span></span> |
| <span data-ttu-id="29697-209">27</span><span class="sxs-lookup"><span data-stu-id="29697-209">27</span></span>        | <span data-ttu-id="29697-210">USB-enhetens slut punkt</span><span class="sxs-lookup"><span data-stu-id="29697-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="29697-211">28</span><span class="sxs-lookup"><span data-stu-id="29697-211">28</span></span>        | <span data-ttu-id="29697-212">USB-enhets klass</span><span class="sxs-lookup"><span data-stu-id="29697-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="29697-213">Objekt pekare</span><span class="sxs-lookup"><span data-stu-id="29697-213">Object Pointer</span></span>

<span data-ttu-id="29697-214">Objekt pekaren anger objekt adressen som används för att komma åt objektet med ThreadX-API: et.</span><span class="sxs-lookup"><span data-stu-id="29697-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="29697-215">Objekt reserverade fält</span><span class="sxs-lookup"><span data-stu-id="29697-215">Object Reserved Fields</span></span>

<span data-ttu-id="29697-216">För alla objekt utom trådar ska dessa reserverade fält vara 0.</span><span class="sxs-lookup"><span data-stu-id="29697-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="29697-217">För trådar placeras Trådens prioritet vid den tidpunkt som den anges i registret i dessa två reserverade fält.</span><span class="sxs-lookup"><span data-stu-id="29697-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="29697-218">Objekt parametrar</span><span class="sxs-lookup"><span data-stu-id="29697-218">Object Parameters</span></span>

<span data-ttu-id="29697-219">Objekt parametrarna innehåller kompletterande information om objektet.</span><span class="sxs-lookup"><span data-stu-id="29697-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="29697-220">Följande beskriver kompletterande information för varje ThreadX-objekt:</span><span class="sxs-lookup"><span data-stu-id="29697-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="29697-221">**Objekt typ**</span><span class="sxs-lookup"><span data-stu-id="29697-221">**Object Type**</span></span>        | <span data-ttu-id="29697-222">**Parameter 1**</span><span class="sxs-lookup"><span data-stu-id="29697-222">**Parameter 1**</span></span>  | <span data-ttu-id="29697-223">**Parameter 2**</span><span class="sxs-lookup"><span data-stu-id="29697-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="29697-224">Trådtoken</span><span class="sxs-lookup"><span data-stu-id="29697-224">Thread</span></span>                 | <span data-ttu-id="29697-225">Stack start</span><span class="sxs-lookup"><span data-stu-id="29697-225">Stack Start</span></span>      | <span data-ttu-id="29697-226">Stack storlek</span><span class="sxs-lookup"><span data-stu-id="29697-226">Stack Size</span></span> |
| <span data-ttu-id="29697-227">Timer</span><span class="sxs-lookup"><span data-stu-id="29697-227">Timer</span></span>                  | <span data-ttu-id="29697-228">Inledande Tick</span><span class="sxs-lookup"><span data-stu-id="29697-228">Initial Ticks</span></span> | <span data-ttu-id="29697-229">Ändra schema för Tick</span><span class="sxs-lookup"><span data-stu-id="29697-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="29697-230">Kö</span><span class="sxs-lookup"><span data-stu-id="29697-230">Queue</span></span>                  | <span data-ttu-id="29697-231">Kös Tor lek</span><span class="sxs-lookup"><span data-stu-id="29697-231">Queue Size</span></span> | <span data-ttu-id="29697-232">Meddelande storlek</span><span class="sxs-lookup"><span data-stu-id="29697-232">Message Size</span></span> |
| <span data-ttu-id="29697-233">Semafor</span><span class="sxs-lookup"><span data-stu-id="29697-233">Semaphore</span></span>              | <span data-ttu-id="29697-234">Ursprungliga instanser</span><span class="sxs-lookup"><span data-stu-id="29697-234">Initial Instances</span></span> | - |
| <span data-ttu-id="29697-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="29697-235">Mutex</span></span>                  | <span data-ttu-id="29697-236">Arvs flagga</span><span class="sxs-lookup"><span data-stu-id="29697-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="29697-237">Händelse flaggor grupp</span><span class="sxs-lookup"><span data-stu-id="29697-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="29697-238">Blockera pool</span><span class="sxs-lookup"><span data-stu-id="29697-238">Block Pool</span></span>             | <span data-ttu-id="29697-239">Totalt antal block</span><span class="sxs-lookup"><span data-stu-id="29697-239">Total Blocks</span></span> | <span data-ttu-id="29697-240">Blockstorlek</span><span class="sxs-lookup"><span data-stu-id="29697-240">Block Size</span></span> |
| <span data-ttu-id="29697-241">Byte-pool</span><span class="sxs-lookup"><span data-stu-id="29697-241">Byte Pool</span></span>              | <span data-ttu-id="29697-242">Totalt antal byte</span><span class="sxs-lookup"><span data-stu-id="29697-242">Total Bytes</span></span> | - |
| <span data-ttu-id="29697-243">.. /media</span><span class="sxs-lookup"><span data-stu-id="29697-243">../media</span></span>                  | <span data-ttu-id="29697-244">Storlek på fat-cache</span><span class="sxs-lookup"><span data-stu-id="29697-244">Fat Cache Size</span></span> | <span data-ttu-id="29697-245">Cachestorlek för sektor</span><span class="sxs-lookup"><span data-stu-id="29697-245">Sector Cache Size</span></span> |
| <span data-ttu-id="29697-246">Fil</span><span class="sxs-lookup"><span data-stu-id="29697-246">File</span></span>                   | - | - |
| <span data-ttu-id="29697-247">IP-adress</span><span class="sxs-lookup"><span data-stu-id="29697-247">IP</span></span>                     | <span data-ttu-id="29697-248">Stack start</span><span class="sxs-lookup"><span data-stu-id="29697-248">Stack Start</span></span> | <span data-ttu-id="29697-249">Stack storlek</span><span class="sxs-lookup"><span data-stu-id="29697-249">Stack Size</span></span> |
| <span data-ttu-id="29697-250">Paketets pool</span><span class="sxs-lookup"><span data-stu-id="29697-250">Packet Pool</span></span>            | <span data-ttu-id="29697-251">Paket storlek</span><span class="sxs-lookup"><span data-stu-id="29697-251">Packet Size</span></span> | <span data-ttu-id="29697-252">Antal paket</span><span class="sxs-lookup"><span data-stu-id="29697-252">Number of Packets</span></span> |
| <span data-ttu-id="29697-253">TCP-socket</span><span class="sxs-lookup"><span data-stu-id="29697-253">TCP Socket</span></span>             | <span data-ttu-id="29697-254">IP-adress</span><span class="sxs-lookup"><span data-stu-id="29697-254">IP address</span></span> | <span data-ttu-id="29697-255">Fönster storlek</span><span class="sxs-lookup"><span data-stu-id="29697-255">Window Size</span></span> |
| <span data-ttu-id="29697-256">UDP-socket</span><span class="sxs-lookup"><span data-stu-id="29697-256">UDP Socket</span></span>             | <span data-ttu-id="29697-257">IP-adress</span><span class="sxs-lookup"><span data-stu-id="29697-257">IP address</span></span> | <span data-ttu-id="29697-258">Max för RX-kö</span><span class="sxs-lookup"><span data-stu-id="29697-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="29697-259">Objekt namn</span><span class="sxs-lookup"><span data-stu-id="29697-259">Object Name</span></span>

<span data-ttu-id="29697-260">Objekt namnet innehåller namnet på ThreadX-objektet.</span><span class="sxs-lookup"><span data-stu-id="29697-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="29697-261">Namnet är det namn som angavs för ThreadX vid den tidpunkt då objektet skapades.</span><span class="sxs-lookup"><span data-stu-id="29697-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="29697-262">Som standard har objekt namnet högst 32 tecken.</span><span class="sxs-lookup"><span data-stu-id="29697-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="29697-263">Faktiska namn som är större än 32 tecken trunkeras.</span><span class="sxs-lookup"><span data-stu-id="29697-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="29697-264">Händelse spårnings poster</span><span class="sxs-lookup"><span data-stu-id="29697-264">Event Trace Entries</span></span>

<span data-ttu-id="29697-265">Händelse spårnings posterna finns i den nedre delen av bufferten för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="29697-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="29697-266">Posterna bevaras i en cirkulär lista, och den aktuella post markören pekar på den äldsta posten.</span><span class="sxs-lookup"><span data-stu-id="29697-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="29697-267">Antalet poster i listan beräknas av ***tx_trace_enable*** anropet.</span><span class="sxs-lookup"><span data-stu-id="29697-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="29697-268">Varje objekt register post innehåller information om en enskild spårnings händelse för ThreadX.</span><span class="sxs-lookup"><span data-stu-id="29697-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="29697-269">Följande data struktur definierar varje spårnings händelse post:</span><span class="sxs-lookup"><span data-stu-id="29697-269">The following data structure defines each trace event entry:</span></span>

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a><span data-ttu-id="29697-270">Tråd pekare</span><span class="sxs-lookup"><span data-stu-id="29697-270">Thread Pointer</span></span>

<span data-ttu-id="29697-271">Tråd pekaren innehåller adressen till tråden som körs vid tidpunkten för den här händelsen.</span><span class="sxs-lookup"><span data-stu-id="29697-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="29697-272">Om händelsen inträffade under initieringen (ingen tråd körs), är värdet för den här visaren 0xF0F0F0F0.</span><span class="sxs-lookup"><span data-stu-id="29697-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="29697-273">Om händelsen inträffade under en avbrotts tjänst rutin (ISR) är värdet för den här pekaren 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="29697-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="29697-274">Om posten inte har använts än, är värdet för den här pekaren 0.</span><span class="sxs-lookup"><span data-stu-id="29697-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="29697-275">Tråd prioritet</span><span class="sxs-lookup"><span data-stu-id="29697-275">Thread Priority</span></span>

<span data-ttu-id="29697-276">Fältet tråd prioritet innehåller tråd prioriteten och avstängningen för den tråd som kördes vid tidpunkten för den här händelsen.</span><span class="sxs-lookup"><span data-stu-id="29697-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="29697-277">Om det finns en avbrotts kontext (tråd pekare är 0xFFFFFFFF) är värdet för det här fältet inte prioritet utan i stället värdet för ***_tx_thread_current_ptr*** vid tidpunkten för händelsen.</span><span class="sxs-lookup"><span data-stu-id="29697-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="29697-278">Annars är värdet för det här fältet 0.</span><span class="sxs-lookup"><span data-stu-id="29697-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="29697-279">Händelse-ID</span><span class="sxs-lookup"><span data-stu-id="29697-279">Event ID</span></span>

<span data-ttu-id="29697-280">Händelse-ID: t anger händelsen som ägde rum.</span><span class="sxs-lookup"><span data-stu-id="29697-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="29697-281">Giltigt ID för spårnings händelse för ThreadX-spårning från 1 till 1024.</span><span class="sxs-lookup"><span data-stu-id="29697-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="29697-282">Värden som börjar på 1025 och senare är reserverade för användarspecifika händelser.</span><span class="sxs-lookup"><span data-stu-id="29697-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="29697-283">Den fullständiga definitionen av ThreadX-händelse-ID: n finns i filen ***tx_trace. h*** .</span><span class="sxs-lookup"><span data-stu-id="29697-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="29697-284">Informations fält (1-4)</span><span class="sxs-lookup"><span data-stu-id="29697-284">Information Fields (1-4)</span></span>

<span data-ttu-id="29697-285">Informations fälten innehåller ytterligare information om den aktuella händelsen.</span><span class="sxs-lookup"><span data-stu-id="29697-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="29697-286">En fullständig beskrivning av informations fälten för varje definierat ThreadX händelse-ID finns i filen ***tx_trace. h*** .</span><span class="sxs-lookup"><span data-stu-id="29697-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>