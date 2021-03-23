---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825641"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="7d023-103">Kapitel 4 – Beskrivning av Azure återställnings tider NetX-tjänster</span><span class="sxs-lookup"><span data-stu-id="7d023-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="7d023-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-tjänster i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="7d023-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="7d023-105">Tjänst namn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="7d023-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="7d023-106">Till exempel finns alla ARP-tjänster i början av det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="7d023-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="7d023-107">*Observera att det finns en BSD-Compatible socket-API för äldre program kod som inte kan dra full nytta av NetX-API: et med höga prestanda. Se bilaga D för mer information om API: et för BSD-Compatible socket.*</span><span class="sxs-lookup"><span data-stu-id="7d023-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="7d023-108">I avsnittet "returnera värden" i varje beskrivning påverkas inte värden i **fetstil** av NX_DISABLE_ERROR_CHECKING alternativ som används för att inaktivera API-felkontrollen, medan värden i icke-fetstil är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="7d023-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="7d023-109">I avsnitten "tillåten från" anges från vilka varje NetX-tjänst kan anropas.</span><span class="sxs-lookup"><span data-stu-id="7d023-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="7d023-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="7d023-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="7d023-111">Ogiltig förklara alla dynamiska poster i ARP-cachen</span><span class="sxs-lookup"><span data-stu-id="7d023-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-112">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-113">Description</span></span>

<span data-ttu-id="7d023-114">I den här tjänsten inaktive ras alla dynamiska ARP-poster i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-115">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-115">Parameters</span></span>

- <span data-ttu-id="7d023-116">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-117">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-117">Return Values</span></span>

- <span data-ttu-id="7d023-118">**NX_SUCCESS** (0X00) slutförde ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="7d023-119">**NX_NOT_ENABLED** (0X14) ARP har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="7d023-120">**NX_PTR_ERROR** (0X07) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-121">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="7d023-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-122">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-122">Allowed From</span></span>

<span data-ttu-id="7d023-123">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-124">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-124">Preemption Possible</span></span>

<span data-ttu-id="7d023-125">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-125">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-127">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-127">See Also</span></span>

- <span data-ttu-id="7d023-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="7d023-129">nx_arp_hardware_address_find nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-130">nx_arp_ip_address_find nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-131">nx_arp_static_entry_create nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="7d023-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="7d023-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="7d023-133">Ange dynamisk ARP-post</span><span class="sxs-lookup"><span data-stu-id="7d023-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-134">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="7d023-135">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-135">Description</span></span>

<span data-ttu-id="7d023-136">Den här tjänsten allokerar en dynamisk post från ARP-cachen och ställer in den angivna IP-adressen till fysisk adress mappning.</span><span class="sxs-lookup"><span data-stu-id="7d023-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="7d023-137">Om en fysisk adress på noll anges skickas en faktisk ARP-begäran till nätverket för att den fysiska adressen ska kunna matchas.</span><span class="sxs-lookup"><span data-stu-id="7d023-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="7d023-138">Observera också att den här posten tas bort om ARP-åldrande är aktiv eller om ARP-cachen är slut och det här är den minst nyligen använda ARP-posten.</span><span class="sxs-lookup"><span data-stu-id="7d023-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-139">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-139">Parameters</span></span>

- <span data-ttu-id="7d023-140">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-141">**ip_address** IP-adress att mappa.</span><span class="sxs-lookup"><span data-stu-id="7d023-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="7d023-142">**physical_msw** De 16 främsta bitarna (47-32) av den fysiska adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="7d023-143">**physical_lsw** Lägre 32 bitar (31-0) av den fysiska adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-144">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-144">Return Values</span></span>

- <span data-ttu-id="7d023-145">**NX_SUCCESS** (0x00) en dynamisk ARP-post uppsättning.</span><span class="sxs-lookup"><span data-stu-id="7d023-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="7d023-146">**NX_NO_MORE_ENTRIES** (0X17) inga fler ARP-poster är tillgängliga i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="7d023-147">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-148">**NX_PTR_ERROR** (0X07) ogiltig IP-instans pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="7d023-149">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-150">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-151">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-151">Allowed From</span></span>

<span data-ttu-id="7d023-152">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-153">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-153">Preemption Possible</span></span>

<span data-ttu-id="7d023-154">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-154">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-155">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-156">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-156">See Also</span></span>

- <span data-ttu-id="7d023-157">nx_arp_dynamic_entries_invalidate nx_arp_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="7d023-158">nx_arp_gratuitous_send nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="7d023-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-160">nx_arp_static_entry_create nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="7d023-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-161">nx_arp_enable</span></span>

<span data-ttu-id="7d023-162">Aktiverar adress matchnings protokoll (ARP).</span><span class="sxs-lookup"><span data-stu-id="7d023-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-163">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="7d023-164">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-164">Description</span></span>

<span data-ttu-id="7d023-165">Den här tjänsten initierar ARP-komponenten i NetX för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="7d023-166">ARP-initieringen innefattar konfiguration av ARP-cachen och olika ARP-bearbetnings rutiner som krävs för att skicka och ta emot ARP-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="7d023-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-167">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-167">Parameters</span></span>

- <span data-ttu-id="7d023-168">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-169">**arp_cache_memory** Pekare till minnes området för att placera ARP-cache.</span><span class="sxs-lookup"><span data-stu-id="7d023-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="7d023-170">**arp_cache_size** Varje ARP-post är 52 byte, det totala antalet ARP-poster är därför att storleken dividerat med 52.</span><span class="sxs-lookup"><span data-stu-id="7d023-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-171">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-171">Return Values</span></span>

- <span data-ttu-id="7d023-172">**NX_SUCCESS** (0X00) slutförde ARP-aktivering.</span><span class="sxs-lookup"><span data-stu-id="7d023-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="7d023-173">**NX_PTR_ERROR** (0X07) ogiltig IP eller minnes pekare för cache.</span><span class="sxs-lookup"><span data-stu-id="7d023-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="7d023-174">**NX_SIZE_ERROR** (0x09) den TILLHANDAHÅLLna ARP-cache-minnet är för litet.</span><span class="sxs-lookup"><span data-stu-id="7d023-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="7d023-175">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-176">**NX_ALREADY_ENABLED** (0X15) den här komponenten har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-177">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-177">Allowed From</span></span>

<span data-ttu-id="7d023-178">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-179">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-179">Preemption Possible</span></span>

<span data-ttu-id="7d023-180">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-180">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-181">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-182">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-182">See Also</span></span>

- <span data-ttu-id="7d023-183">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-184">nx_arp_gratuitous_send nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="7d023-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-186">nx_arp_static_entry_create nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="7d023-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="7d023-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="7d023-188">Skicka en kostnads fria ARP-begäran</span><span class="sxs-lookup"><span data-stu-id="7d023-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-189">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-190">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-190">Description</span></span>

<span data-ttu-id="7d023-191">Den här tjänsten går igenom alla fysiska gränssnitt för att överföra AntiArp-begäranden så länge som gränssnittets IP-adress är giltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="7d023-192">Om ett ARP-svar sedan tas emot, anropas den tillhandahållna svars hanteraren för att bearbeta svaret till den kostnads fria ARP-filen.</span><span class="sxs-lookup"><span data-stu-id="7d023-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-193">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-193">Parameters</span></span>

- <span data-ttu-id="7d023-194">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-195">**response_handler** Pekare till funktionen för svars hantering.</span><span class="sxs-lookup"><span data-stu-id="7d023-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="7d023-196">Om NX_NULL anges ignoreras svaren.</span><span class="sxs-lookup"><span data-stu-id="7d023-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-197">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-197">Return Values</span></span>

- <span data-ttu-id="7d023-198">**NX_SUCCESS** (0X00) lyckad överföring av kostnads fria ARP.</span><span class="sxs-lookup"><span data-stu-id="7d023-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="7d023-199">**NX_NO_PACKET** (0X01) inget paket tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="7d023-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="7d023-200">**NX_NOT_ENABLED** (0X14) ARP har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="7d023-201">Den aktuella IP-adressen för **NX_IP_ADDRESS_ERROR** (0x21) är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="7d023-202">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-203">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="7d023-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-204">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-204">Allowed From</span></span>

<span data-ttu-id="7d023-205">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-206">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-206">Preemption Possible</span></span>

<span data-ttu-id="7d023-207">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-207">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-208">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-209">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-209">See Also</span></span>

- <span data-ttu-id="7d023-210">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-212">nx_arp_ip_address_find nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-213">nx_arp_static_entry_create nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="7d023-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="7d023-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="7d023-215">Hitta en fysisk maskin varu adress med en IP-adress</span><span class="sxs-lookup"><span data-stu-id="7d023-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-216">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="7d023-217">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-217">Description</span></span>

<span data-ttu-id="7d023-218">Den här tjänsten försöker hitta en fysisk maskin varu adress i ARP-cachen som är associerad med den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-219">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-219">Parameters</span></span>

- <span data-ttu-id="7d023-220">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-221">**ip_address** IP-adress att söka efter.</span><span class="sxs-lookup"><span data-stu-id="7d023-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="7d023-222">**physical_msw** Pekare till variabeln för att returnera de översta 16 bitarna (47-32) av den fysiska adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="7d023-223">**physical_lsw** Pekare till variabeln för att returnera de lägre 32 bitarna (31-0) för den fysiska adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-224">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-224">Return Values</span></span>

- <span data-ttu-id="7d023-225">**NX_SUCCESS** (0X00) lyckad ARP-maskinvara Sök.</span><span class="sxs-lookup"><span data-stu-id="7d023-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="7d023-226">Det gick inte att hitta **NX_ENTRY_NOT_FOUND** -mappningen (0x16) i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="7d023-227">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-228">**NX_PTR_ERROR** (0X07) ogiltig IP-eller minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="7d023-229">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-230">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-231">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-231">Allowed From</span></span>

<span data-ttu-id="7d023-232">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-233">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-233">Preemption Possible</span></span>

<span data-ttu-id="7d023-234">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-234">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-235">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-236">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-236">See Also</span></span>

- <span data-ttu-id="7d023-237">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-239">nx_arp_ip_address_find nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-240">nx_arp_static_entry_create nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="7d023-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-241">nx_arp_info_get</span></span>

<span data-ttu-id="7d023-242">Hämta information om ARP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-243">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="7d023-244">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-244">Description</span></span>

<span data-ttu-id="7d023-245">Den här tjänsten hämtar information om ARP-aktiviteter för den associerade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="7d023-246">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-247">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-247">Parameters</span></span>

- <span data-ttu-id="7d023-248">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-249">**arp_requests_sent** Pekare till målet för de totala ARP-begäranden som skickats från den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="7d023-250">**arp_requests_received** Pekare till målet för de totala ARP-begäranden som tagits emot från nätverket.</span><span class="sxs-lookup"><span data-stu-id="7d023-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="7d023-251">**arp_responses_sent** Pekare till målet för det totala antalet ARP-svar som skickas från den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="7d023-252">**arp_responses_received** Pekar till målet för det totala antalet ARP-svar som tagits emot från nätverket.</span><span class="sxs-lookup"><span data-stu-id="7d023-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="7d023-253">**arp_dynamic_entries** Pekar mot målet för det aktuella antalet dynamiska ARP-poster.</span><span class="sxs-lookup"><span data-stu-id="7d023-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="7d023-254">**arp_static_entries** Pekar mot målet för det aktuella antalet statiska ARP-poster.</span><span class="sxs-lookup"><span data-stu-id="7d023-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="7d023-255">**arp_aged_entries** Pekar till målet för det totala antalet ARP-poster som har föråldrats och blivit ogiltiga.</span><span class="sxs-lookup"><span data-stu-id="7d023-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="7d023-256">**arp_invalid_messages** Pekar till målet för de totala ogiltiga ARP-meddelanden som tagits emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-257">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-257">Return Values</span></span>

- <span data-ttu-id="7d023-258">**NX_SUCCESS** (0X00) lyckades Hämta ARP-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="7d023-259">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-260">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-261">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-262">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-262">Allowed From</span></span>

<span data-ttu-id="7d023-263">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-264">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-264">Preemption Possible</span></span>

<span data-ttu-id="7d023-265">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-265">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-266">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-267">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-267">See Also</span></span>

- <span data-ttu-id="7d023-268">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-269">nx_arp_enable nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="7d023-270">nx_arp_hardware_address_find nx_arp_ip_address_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="7d023-271">nx_arp_static_entries_delete nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="7d023-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="7d023-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="7d023-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="7d023-274">Hitta IP-adress till en fysisk adress</span><span class="sxs-lookup"><span data-stu-id="7d023-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-275">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="7d023-276">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-276">Description</span></span>

<span data-ttu-id="7d023-277">Den här tjänsten försöker hitta en IP-adress i ARP-cachen som är associerad med den angivna fysiska adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-278">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-278">Parameters</span></span>

- <span data-ttu-id="7d023-279">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-280">**ip_address** Pekare för att returnera IP-adress, om en sådan finns, som har mappats.</span><span class="sxs-lookup"><span data-stu-id="7d023-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="7d023-281">**physical_msw** De 16 främsta bitarna (47-32) i den fysiska adressen som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="7d023-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="7d023-282">**physical_lsw** Lägre 32 bitar (31-0) för den fysiska adressen att söka efter.</span><span class="sxs-lookup"><span data-stu-id="7d023-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-283">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-283">Return Values</span></span>

- <span data-ttu-id="7d023-284">**NX_SUCCESS** (0X00) lyckade ARP IP-adress Sök</span><span class="sxs-lookup"><span data-stu-id="7d023-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="7d023-285">Det gick inte att hitta **NX_ENTRY_NOT_FOUND** -mappningen (0x16) i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="7d023-286">**NX_PTR_ERROR** (0X07) ogiltig IP-eller minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="7d023-287">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-288">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw är båda 0.</span><span class="sxs-lookup"><span data-stu-id="7d023-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-290">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-290">Allowed From</span></span>

<span data-ttu-id="7d023-291">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-292">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-292">Preemption Possible</span></span>

<span data-ttu-id="7d023-293">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-293">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-294">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-295">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-295">See Also</span></span>

- <span data-ttu-id="7d023-296">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-297">nx_arp_enable nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="7d023-298">nx_arp_hardware_address_find nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-299">nx_arp_static_entries_delete nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="7d023-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="7d023-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="7d023-302">Ta bort alla statiska ARP-poster</span><span class="sxs-lookup"><span data-stu-id="7d023-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-303">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-304">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-304">Description</span></span>

<span data-ttu-id="7d023-305">Den här tjänsten tar bort alla statiska poster i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-306">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-306">Parameters</span></span>

- <span data-ttu-id="7d023-307">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-308">Return Values</span></span>

- <span data-ttu-id="7d023-309">**NX_SUCCESS** (0X00) statiska poster tas bort.</span><span class="sxs-lookup"><span data-stu-id="7d023-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="7d023-310">**NX_PTR_ERROR** (0X07) ogiltig ip_ptr pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="7d023-311">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-312">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-313">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-313">Allowed From</span></span>

<span data-ttu-id="7d023-314">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-315">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-315">Preemption Possible</span></span>

<span data-ttu-id="7d023-316">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-316">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-317">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-318">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-318">See Also</span></span>

- <span data-ttu-id="7d023-319">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-320">nx_arp_enable nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="7d023-321">nx_arp_hardware_address_find nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-322">nx_arp_ip_address_find nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="7d023-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="7d023-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="7d023-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="7d023-325">Skapa statisk IP-adress för maskin varu mappning i ARP-cache</span><span class="sxs-lookup"><span data-stu-id="7d023-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-326">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="7d023-327">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-327">Description</span></span>

<span data-ttu-id="7d023-328">Den här tjänsten skapar en statisk IP-till-fysisk-adress mappning i ARP-cachen för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="7d023-329">Statiska ARP-poster omfattas inte av regelbundna ARP-uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="7d023-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-330">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-330">Parameters</span></span>

- <span data-ttu-id="7d023-331">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-332">**ip_address** IP-adress att mappa.</span><span class="sxs-lookup"><span data-stu-id="7d023-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="7d023-333">**physical_msw** De 16 främsta bitarna (47-32) av den fysiska adressen som ska mappas.</span><span class="sxs-lookup"><span data-stu-id="7d023-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="7d023-334">**physical_lsw** Nedre 32 bitar (31-0) av den fysiska adressen som ska mappas.</span><span class="sxs-lookup"><span data-stu-id="7d023-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-335">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-335">Return Values</span></span>

- <span data-ttu-id="7d023-336">**NX_SUCCESS** (0x00)-statisk post har skapats.</span><span class="sxs-lookup"><span data-stu-id="7d023-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="7d023-337">**NX_NO_MORE_ENTRIES** (0X17) inga fler ARP-poster är tillgängliga i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="7d023-338">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-339">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-340">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-341">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw är båda 0.</span><span class="sxs-lookup"><span data-stu-id="7d023-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-343">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-343">Allowed From</span></span>

<span data-ttu-id="7d023-344">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-345">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-345">Preemption Possible</span></span>

<span data-ttu-id="7d023-346">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-346">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-347">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-348">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-348">See Also</span></span>

- <span data-ttu-id="7d023-349">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-350">nx_arp_enable nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="7d023-351">nx_arp_hardware_address_find nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-352">nx_arp_ip_address_find nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="7d023-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="7d023-355">Ta bort statisk IP-adress till maskin varu mappning i ARP-cache</span><span class="sxs-lookup"><span data-stu-id="7d023-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-356">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="7d023-357">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-357">Description</span></span>

<span data-ttu-id="7d023-358">Den här tjänsten hittar och tar bort en tidigare skapad statisk IP-till-fysisk-adress mappning i ARP-cachen för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-359">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-359">Parameters</span></span>

- <span data-ttu-id="7d023-360">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-361">**ip_address** IP-adress som har mappats statiskt.</span><span class="sxs-lookup"><span data-stu-id="7d023-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="7d023-362">**physical_msw** De 16 16 bitarna (47-32) för den fysiska adress som har mappats statiskt.</span><span class="sxs-lookup"><span data-stu-id="7d023-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="7d023-363">**physical_lsw** Lägre 32 bitar (31-0) för den fysiska adress som har mappats statiskt.</span><span class="sxs-lookup"><span data-stu-id="7d023-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-364">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-364">Return Values</span></span>

- <span data-ttu-id="7d023-365">**NX_SUCCESS** (0X00) lyckade ARP-post borttagning.</span><span class="sxs-lookup"><span data-stu-id="7d023-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="7d023-366">Det gick inte att hitta den statiska ARP-posten **NX_ENTRY_NOT_FOUND** (0x16) i ARP-cachen.</span><span class="sxs-lookup"><span data-stu-id="7d023-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="7d023-367">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-368">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-369">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-370">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw och physical_lsw är båda 0.</span><span class="sxs-lookup"><span data-stu-id="7d023-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-372">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-372">Allowed From</span></span>

<span data-ttu-id="7d023-373">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-374">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-374">Preemption Possible</span></span>

<span data-ttu-id="7d023-375">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-375">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-376">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-377">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-377">See Also</span></span>

- <span data-ttu-id="7d023-378">nx_arp_dynamic_entries_invalidate nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="7d023-379">nx_arp_enable nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="7d023-380">nx_arp_hardware_address_find nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="7d023-381">nx_arp_ip_address_find nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="7d023-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="7d023-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="7d023-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-383">nx_icmp_enable</span></span>

<span data-ttu-id="7d023-384">Aktivera Internet Control Message Protocol (ICMP)</span><span class="sxs-lookup"><span data-stu-id="7d023-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-385">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-386">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-386">Description</span></span>

<span data-ttu-id="7d023-387">Den här tjänsten aktiverar ICMP-komponenten för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="7d023-388">ICMP-komponenten ansvarar för hantering av Internet fel meddelanden och ping-förfrågningar och svar.</span><span class="sxs-lookup"><span data-stu-id="7d023-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-389">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-389">Parameters</span></span>

- <span data-ttu-id="7d023-390">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-391">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-391">Return Values</span></span>

- <span data-ttu-id="7d023-392">**NX_SUCCESS** (0X00) slutförde ICMP-aktivering.</span><span class="sxs-lookup"><span data-stu-id="7d023-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="7d023-393">**NX_ALREADY_ENABLED** (0X15) ICMP har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="7d023-394">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-395">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-396">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-396">Allowed From</span></span>

<span data-ttu-id="7d023-397">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-398">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-398">Preemption Possible</span></span>

<span data-ttu-id="7d023-399">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-399">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-400">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-401">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-401">See Also</span></span>

- <span data-ttu-id="7d023-402">nx_icmp_info_get nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="7d023-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="7d023-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-403">nx_icmp_info_get</span></span>

<span data-ttu-id="7d023-404">Hämta information om ICMP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-405">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="7d023-406">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-406">Description</span></span>

<span data-ttu-id="7d023-407">Den här tjänsten hämtar information om ICMP-aktiviteter för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="7d023-408">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-409">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-409">Parameters</span></span>

- <span data-ttu-id="7d023-410">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-411">**pings_sent** Pekare till målet för det totala antalet pingar som skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="7d023-412">**ping_timeouts** Pekare till målet för det totala antalet ping-tidsgräns.</span><span class="sxs-lookup"><span data-stu-id="7d023-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="7d023-413">**ping_threads_suspended** Pekare till målet för det totala antalet trådar som har inaktiverats för ping-begäranden.</span><span class="sxs-lookup"><span data-stu-id="7d023-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="7d023-414">**ping_responses_received** Pekare till åltabell av det totala antalet ping-svar som tagits emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="7d023-415">**icmp_checksum_errors** Pekare till målet för det totala antalet fel i ICMP-kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="7d023-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="7d023-416">**icmp_unhandled_messages** Pekare till åltabell av det totala antalet ohanterade ICMP-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="7d023-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-417">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-417">Return Values</span></span>

- <span data-ttu-id="7d023-418">**NX_SUCCESS** (0X00) lyckades Hämta ICMP-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="7d023-419">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-420">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-421">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-422">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-422">Allowed From</span></span>

<span data-ttu-id="7d023-423">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-424">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-424">Preemption Possible</span></span>

<span data-ttu-id="7d023-425">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-425">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-426">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-427">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-427">See Also</span></span>

- <span data-ttu-id="7d023-428">nx_icmp_enable nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="7d023-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="7d023-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="7d023-429">nx_icmp_ping</span></span>

<span data-ttu-id="7d023-430">Skicka ping-begäran till angiven IP-adress</span><span class="sxs-lookup"><span data-stu-id="7d023-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-431">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-432">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-432">Description</span></span>

<span data-ttu-id="7d023-433">Den här tjänsten skickar en ping-begäran till den angivna IP-adressen och väntar på den angivna tiden för ett ping-svarsmeddelande.</span><span class="sxs-lookup"><span data-stu-id="7d023-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="7d023-434">Om inget svar tas emot returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="7d023-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="7d023-435">Annars returneras hela svarsmeddelandet i variabeln som pekas av response_ptr.</span><span class="sxs-lookup"><span data-stu-id="7d023-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="7d023-436">*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*</span><span class="sxs-lookup"><span data-stu-id="7d023-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-437">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-437">Parameters</span></span>

- <span data-ttu-id="7d023-438">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-439">**ip_address** IP-adress i byte ordning för värden till ping.</span><span class="sxs-lookup"><span data-stu-id="7d023-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="7d023-440">data pekare till data arean för ping-meddelande.</span><span class="sxs-lookup"><span data-stu-id="7d023-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="7d023-441">**data_size** Antal byte i ping-data</span><span class="sxs-lookup"><span data-stu-id="7d023-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="7d023-442">**response_ptr** Pekare till paket pekare för att returnera meddelandet ping-svar i.</span><span class="sxs-lookup"><span data-stu-id="7d023-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="7d023-443">**wait_option** Anger hur lång tid det tar att vänta på ping-svar.</span><span class="sxs-lookup"><span data-stu-id="7d023-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="7d023-444">vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="7d023-445">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="7d023-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="7d023-447">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-448">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-448">Return Values</span></span>

- <span data-ttu-id="7d023-449">**NX_SUCCESS** (0X00) lyckades ping.</span><span class="sxs-lookup"><span data-stu-id="7d023-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="7d023-450">Svars meddelandets pekare placerades i variabeln som pekades på av response_ptr.</span><span class="sxs-lookup"><span data-stu-id="7d023-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="7d023-451">**NX_NO_PACKET** (0X01) Det gick inte att allokera ett ping Request-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="7d023-452">**NX_OVERFLOW** (0x03) det angivna data utrymmet överskrider standard paket storleken för den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="7d023-453">**NX_NO_RESPONSE** (0X29) begärda IP-adressen svarade inte.</span><span class="sxs-lookup"><span data-stu-id="7d023-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="7d023-454">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-455">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-456">**NX_PTR_ERROR** (0X07) ogiltig IP-eller svars pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="7d023-457">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-458">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-459">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-459">Allowed From</span></span>

<span data-ttu-id="7d023-460">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-461">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-461">Preemption Possible</span></span>

<span data-ttu-id="7d023-462">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-462">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-463">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-464">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-464">See Also</span></span>

- <span data-ttu-id="7d023-465">nx_icmp_enable nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="7d023-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-466">nx_igmp_enable</span></span>

<span data-ttu-id="7d023-467">Aktivera IGMP (Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="7d023-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-468">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-469">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-469">Description</span></span>

<span data-ttu-id="7d023-470">Den här tjänsten aktiverar IGMP-komponenten på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="7d023-471">IGMP-komponenten ansvarar för att ge stöd för hanterings åtgärder för IP-multicast-grupper.</span><span class="sxs-lookup"><span data-stu-id="7d023-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-472">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-472">Parameters</span></span>

- <span data-ttu-id="7d023-473">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-474">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-474">Return Values</span></span>

- <span data-ttu-id="7d023-475">**NX_SUCCESS** (0X00) lyckad IGMP-aktivering.</span><span class="sxs-lookup"><span data-stu-id="7d023-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="7d023-476">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-477">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-478">**NX_ALREADY_ENABLED** (0X15) den här komponenten har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-479">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-479">Allowed From</span></span>

<span data-ttu-id="7d023-480">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-481">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-481">Preemption Possible</span></span>

<span data-ttu-id="7d023-482">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-482">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-483">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-484">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-484">See Also</span></span>

- <span data-ttu-id="7d023-485">nx_igmp_info_get nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="7d023-486">nx_igmp_loopback_enable nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="7d023-487">nx_igmp_multicast_join nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="7d023-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-488">nx_igmp_info_get</span></span>

<span data-ttu-id="7d023-489">Hämta information om IGMP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-490">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="7d023-491">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-491">Description</span></span>

<span data-ttu-id="7d023-492">Den här tjänsten hämtar information om IGMP-aktiviteter för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="7d023-493">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-494">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-494">Parameters</span></span>

- <span data-ttu-id="7d023-495">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-496">**igmp_reports_sent** Pekare till målet för det totala antalet ICMP-rapporter som skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="7d023-497">**igmp_queries_received** Pekare till målet för det totala antalet frågor som tagits emot av multicast-router.</span><span class="sxs-lookup"><span data-stu-id="7d023-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="7d023-498">**igmp_checksum_errors** Pekare till målet för det totala antalet fel i IGMP-kontrollsumma för mottagna paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="7d023-499">**current_groups_joined** Pekare till målet för det aktuella antalet grupper som anslöts via den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-500">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-500">Return Values</span></span>

- <span data-ttu-id="7d023-501">**NX_SUCCESS** (0X00) lyckad IGMP-informations hämtning.</span><span class="sxs-lookup"><span data-stu-id="7d023-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="7d023-502">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-503">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-504">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-505">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-505">Allowed From</span></span>

<span data-ttu-id="7d023-506">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-507">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-507">Preemption Possible</span></span>

<span data-ttu-id="7d023-508">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-508">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-509">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-510">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-510">See Also</span></span>

- <span data-ttu-id="7d023-511">nx_igmp_enable nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="7d023-512">nx_igmp_loopback_enable nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="7d023-513">nx_igmp_multicast_join nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="7d023-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="7d023-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="7d023-515">Inaktivera IGMP loopback</span><span class="sxs-lookup"><span data-stu-id="7d023-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-516">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-517">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-517">Description</span></span>

<span data-ttu-id="7d023-518">Den här tjänsten inaktiverar IGMP loopback för alla efterföljande multicast-grupper som anslutits.</span><span class="sxs-lookup"><span data-stu-id="7d023-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-519">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-519">Parameters</span></span>

- <span data-ttu-id="7d023-520">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-521">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-521">Return Values</span></span>
- <span data-ttu-id="7d023-522">**NX_SUCCESS** (0X00) lyckades IGMP loopback-inaktive ring.</span><span class="sxs-lookup"><span data-stu-id="7d023-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="7d023-523">**NX_NOT_ENABLED** (0X14) IGMP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="7d023-524">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-525">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.</span><span class="sxs-lookup"><span data-stu-id="7d023-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-526">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-526">Allowed From</span></span>

<span data-ttu-id="7d023-527">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-528">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-528">Preemption Possible</span></span>

<span data-ttu-id="7d023-529">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-529">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-530">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-531">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-531">See Also</span></span>

- <span data-ttu-id="7d023-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="7d023-533">nx_igmp_multicast_interface_join nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="7d023-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="7d023-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="7d023-536">Aktivera IGMP loopback</span><span class="sxs-lookup"><span data-stu-id="7d023-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-537">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-538">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-538">Description</span></span>

<span data-ttu-id="7d023-539">Den här tjänsten aktiverar IGMP loopback för alla efterföljande multicast-grupper som är anslutna.</span><span class="sxs-lookup"><span data-stu-id="7d023-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-540">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-540">Parameters</span></span>

- <span data-ttu-id="7d023-541">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-542">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-542">Return Values</span></span>
- <span data-ttu-id="7d023-543">**NX_SUCCESS** (0X00) lyckades IGMP loopback-inaktive ring.</span><span class="sxs-lookup"><span data-stu-id="7d023-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="7d023-544">**NX_NOT_ENABLED** (0X14) IGMP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="7d023-545">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-546">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.</span><span class="sxs-lookup"><span data-stu-id="7d023-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-547">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-547">Allowed From</span></span>

<span data-ttu-id="7d023-548">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-549">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-549">Preemption Possible</span></span>

<span data-ttu-id="7d023-550">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-550">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-551">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-552">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-552">See Also</span></span>

- <span data-ttu-id="7d023-553">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="7d023-554">nx_igmp_multicast_interface_join nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="7d023-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="7d023-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="7d023-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="7d023-557">Ansluta IP-instans till angiven multicast-grupp via ett gränssnitt</span><span class="sxs-lookup"><span data-stu-id="7d023-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-558">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="7d023-559">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-559">Description</span></span>

<span data-ttu-id="7d023-560">Den här tjänsten ansluter en IP-instans till den angivna multicast-gruppen via ett angivet nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="7d023-561">En intern räknare upprätthålls för att hålla reda på hur många gånger samma grupp har anslutits.</span><span class="sxs-lookup"><span data-stu-id="7d023-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="7d023-562">När du har anslutit till multicast-gruppen tillåter IGMP-komponenten mottagning av IP-paket med den här grupp adressen via det angivna nätverks gränssnittet och rapporterar till routrar som den här IP-adressen är medlem i den här multicast-gruppen.</span><span class="sxs-lookup"><span data-stu-id="7d023-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="7d023-563">IGMP-medlemskapet Anslut, rapportera och lämna meddelanden skickas också via det angivna nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-564">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-564">Parameters</span></span>

- <span data-ttu-id="7d023-565">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-566">**group_address** Klass D IP multicast-gruppadress att ansluta till i värdens byte ordning.</span><span class="sxs-lookup"><span data-stu-id="7d023-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="7d023-567">**interface_index** Index för det gränssnitt som är kopplat till NetX-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-568">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-568">Return Values</span></span>

- <span data-ttu-id="7d023-569">**NX_SUCCESS** (0x00) multicast-gruppanslutningen är klar.</span><span class="sxs-lookup"><span data-stu-id="7d023-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="7d023-570">**NX_NO_MORE_ENTRIES** (0x17) Det går inte att ansluta fler multicast-grupper, maximalt antal har överskridits.</span><span class="sxs-lookup"><span data-stu-id="7d023-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="7d023-571">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-572">**NX_INVALID_INTERFACE** (0X4C) enhets index pekar på ett ogiltigt nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="7d023-573">Den tillhandahållna **NX_IP_ADDRESS_ERROR** (0X21) multicast-gruppadressen är inte en giltig klass D-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="7d023-574">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-575">**NX_NOT_ENABLED** (0x14) stöd för IP-multicast är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-576">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-576">Allowed From</span></span>

<span data-ttu-id="7d023-577">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-578">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-578">Preemption Possible</span></span>

<span data-ttu-id="7d023-579">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-579">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-580">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-581">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-581">See Also</span></span>

- <span data-ttu-id="7d023-582">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="7d023-583">nx_igmp_loopback_enable nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="7d023-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="7d023-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="7d023-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="7d023-586">Anslut IP-instans till angiven multicast-grupp</span><span class="sxs-lookup"><span data-stu-id="7d023-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-587">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="7d023-588">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-588">Description</span></span>

<span data-ttu-id="7d023-589">Den här tjänsten ansluter en IP-instans till den angivna multicast-gruppen.</span><span class="sxs-lookup"><span data-stu-id="7d023-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="7d023-590">En intern räknare upprätthålls för att hålla reda på hur många gånger samma grupp har anslutits.</span><span class="sxs-lookup"><span data-stu-id="7d023-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="7d023-591">Driv rutinen anropas för att skicka en IGMP-rapport om detta är den första anslutnings förfrågan som finns i nätverket och som anger värden för att ansluta till gruppen.</span><span class="sxs-lookup"><span data-stu-id="7d023-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="7d023-592">När du har anslutit till IGMP-komponenten kan IGMP-komponenten ta emot IP-paket med den här grupp adressen och rapportera till routrar som den här IP-adressen är medlem i den här multicast-gruppen.</span><span class="sxs-lookup"><span data-stu-id="7d023-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="7d023-593">*Använd tjänsten nx_igmp_multicast_interface_join om du vill ansluta en multicast-grupp på en icke-primär enhet **.***</span><span class="sxs-lookup"><span data-stu-id="7d023-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="7d023-594">**Parametrar**</span><span class="sxs-lookup"><span data-stu-id="7d023-594">**Parameters**</span></span>

- <span data-ttu-id="7d023-595">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-596">**group_address** Klass D IP multicast-grupp adress att ansluta till.</span><span class="sxs-lookup"><span data-stu-id="7d023-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-597">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-597">Return Values</span></span>

- <span data-ttu-id="7d023-598">**NX_SUCCESS** (0x00) multicast-gruppanslutningen är klar.</span><span class="sxs-lookup"><span data-stu-id="7d023-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="7d023-599">**NX_NO_MORE_ENTRIES** (0x17) Det går inte att ansluta fler multicast-grupper, maximalt antal har överskridits.</span><span class="sxs-lookup"><span data-stu-id="7d023-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="7d023-600">**NX_INVALID_INTERFACE** (0X4C) enhets index pekar på ett ogiltigt nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="7d023-601">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-gruppadress.</span><span class="sxs-lookup"><span data-stu-id="7d023-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="7d023-602">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-603">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-604">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-605">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-605">Allowed From</span></span>

<span data-ttu-id="7d023-606">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-607">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-607">Preemption Possible</span></span>

<span data-ttu-id="7d023-608">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-608">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-609">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-610">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-610">See Also</span></span>

- <span data-ttu-id="7d023-611">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="7d023-612">nx_igmp_loopback_enable nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="7d023-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="7d023-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="7d023-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="7d023-615">Orsak till att IP-instansen lämnar angiven multicast-grupp</span><span class="sxs-lookup"><span data-stu-id="7d023-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-616">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="7d023-617">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-617">Description</span></span>

<span data-ttu-id="7d023-618">Den här tjänsten gör att en IP-instans lämnar den angivna multicast-gruppen, om antalet tjänstledighets begär Anden matchar antalet anslutnings begär Anden.</span><span class="sxs-lookup"><span data-stu-id="7d023-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="7d023-619">Annars minskas antalet interna anslutningar helt enkelt.</span><span class="sxs-lookup"><span data-stu-id="7d023-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-620">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-620">Parameters</span></span>

- <span data-ttu-id="7d023-621">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-622">**group_address** Multicast-grupp att lämna.</span><span class="sxs-lookup"><span data-stu-id="7d023-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-623">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-623">Return Values</span></span>

- <span data-ttu-id="7d023-624">**NX_SUCCESS** (0x00) multicast-gruppanslutningen är klar.</span><span class="sxs-lookup"><span data-stu-id="7d023-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="7d023-625">Det gick inte att hitta den tidigare kopplings förfrågan för **NX_ENTRY_NOT_FOUND** (0x16).</span><span class="sxs-lookup"><span data-stu-id="7d023-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="7d023-626">**NX_INVALID_INTERFACE** (0X4C) enhets index pekar på ett ogiltigt nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="7d023-627">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-gruppadress.</span><span class="sxs-lookup"><span data-stu-id="7d023-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="7d023-628">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-629">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-630">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-631">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-631">Allowed From</span></span>

<span data-ttu-id="7d023-632">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-633">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-633">Preemption Possible</span></span>

<span data-ttu-id="7d023-634">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-634">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-635">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="7d023-636">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-636">See Also</span></span>

- <span data-ttu-id="7d023-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="7d023-638">nx_igmp_loopback_enable nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="7d023-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="7d023-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="7d023-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="7d023-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="7d023-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="7d023-641">Meddela program om IP-adressen ändras</span><span class="sxs-lookup"><span data-stu-id="7d023-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-642">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="7d023-643">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-643">Description</span></span>

<span data-ttu-id="7d023-644">Den här tjänsten registrerar en program meddelande funktion som anropas när IP-adressen ändras.</span><span class="sxs-lookup"><span data-stu-id="7d023-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-645">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-645">Parameters</span></span>

- <span data-ttu-id="7d023-646">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-647">**change_notify** Pekare till funktionen IP-ändrings meddelande.</span><span class="sxs-lookup"><span data-stu-id="7d023-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="7d023-648">Om den här parametern är NX_NULL inaktive ras meddelandet om ändring av IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="7d023-649">**additional_info** Pekare till valfri ytterligare information som också tillhandahålls till meddelande funktionen när IP-adressen ändras.</span><span class="sxs-lookup"><span data-stu-id="7d023-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-650">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-650">Return Values</span></span>

- <span data-ttu-id="7d023-651">**NX_SUCCESS** (0x00) avisering om ändring av IP-adress har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="7d023-652">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-653">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-654">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-654">Allowed From</span></span>

<span data-ttu-id="7d023-655">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-656">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-656">Preemption Possible</span></span>

<span data-ttu-id="7d023-657">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-657">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-658">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-659">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-659">See Also</span></span>

- <span data-ttu-id="7d023-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="7d023-661">nx_ip_driver_direct_command nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="7d023-662">nx_ip_forwarding_disable nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="7d023-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-664">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="7d023-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="7d023-665">nx_ip_address_get</span></span>

<span data-ttu-id="7d023-666">Hämta IP-adress och nätverks mask</span><span class="sxs-lookup"><span data-stu-id="7d023-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-667">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="7d023-668">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-668">Description</span></span>

<span data-ttu-id="7d023-669">Den här tjänsten hämtar IP-adressen och dess nätmask för det primära nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="7d023-670">\* Om du vill hämta information om den sekundära enheten använder du tjänsten</span><span class="sxs-lookup"><span data-stu-id="7d023-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="7d023-671">**nx_ip_interface_address_get**. \*</span><span class="sxs-lookup"><span data-stu-id="7d023-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-672">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-672">Parameters</span></span>

- <span data-ttu-id="7d023-673">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-674">**ip_address** Pekare till mål för IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="7d023-675">**network_mask** Pekare till målet för nätverks masken.</span><span class="sxs-lookup"><span data-stu-id="7d023-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-676">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-676">Return Values</span></span>

- <span data-ttu-id="7d023-677">**NX_SUCCESS** (0X00) IP-adress hämtades.</span><span class="sxs-lookup"><span data-stu-id="7d023-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="7d023-678">**NX_PTR_ERROR** (0X07) ogiltig IP-eller RETUR variabel pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="7d023-679">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-680">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-680">Allowed From</span></span>

<span data-ttu-id="7d023-681">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-682">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-682">Preemption Possible</span></span>

<span data-ttu-id="7d023-683">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-683">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-684">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-685">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-685">See Also</span></span>

- <span data-ttu-id="7d023-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="7d023-687">nx_ip_delete nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-688">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-689">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="7d023-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="7d023-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="7d023-692">nx_ip_address_set</span></span>

<span data-ttu-id="7d023-693">Ange IP-adress och nätverks mask</span><span class="sxs-lookup"><span data-stu-id="7d023-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-694">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="7d023-695">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-695">Description</span></span>

<span data-ttu-id="7d023-696">Den här tjänsten anger IP-adress och nätverks mask för det primära nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="7d023-697">*Om du vill ange IP-adress och nätverks mask för den sekundära enheten använder du tjänsten **nx_ip_interface_address_set**.*</span><span class="sxs-lookup"><span data-stu-id="7d023-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-698">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-698">Parameters</span></span>

- <span data-ttu-id="7d023-699">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-700">**ip_address** Ny IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="7d023-701">**network_mask** Ny nätverks mask.</span><span class="sxs-lookup"><span data-stu-id="7d023-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-702">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-702">Return Values</span></span>

- <span data-ttu-id="7d023-703">Den angivna IP-adressen för **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="7d023-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="7d023-704">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-705">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-706">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-707">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-707">Allowed From</span></span>

<span data-ttu-id="7d023-708">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-709">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-709">Preemption Possible</span></span>

<span data-ttu-id="7d023-710">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-710">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-711">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-712">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-712">See Also</span></span>

- <span data-ttu-id="7d023-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="7d023-714">nx_ip_delete nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-715">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-716">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="7d023-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="7d023-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="7d023-719">nx_ip_create</span></span>

<span data-ttu-id="7d023-720">Skapa en IP-instans</span><span class="sxs-lookup"><span data-stu-id="7d023-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-721">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="7d023-722">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-722">Description</span></span>

<span data-ttu-id="7d023-723">Den här tjänsten skapar en IP-instans med användaren angiven IP-adress och nätverks driv rutin.</span><span class="sxs-lookup"><span data-stu-id="7d023-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="7d023-724">Dessutom måste programmet ange en tidigare skapad modempool för IP-instansen som ska användas för intern paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="7d023-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="7d023-725">Observera att den angivna program nätverks driv rutinen inte anropas förrän den här IP-tråden körts.</span><span class="sxs-lookup"><span data-stu-id="7d023-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-726">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-726">Parameters</span></span>

- <span data-ttu-id="7d023-727">**ip_ptr** Pekare för att kontrol lera block för att skapa en ny IP-instans.</span><span class="sxs-lookup"><span data-stu-id="7d023-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="7d023-728">**namn** Namnet på den nya IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="7d023-729">**ip_address** IP-adress för den här nya IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="7d023-730">**network_mask** Mask för att avgränsa nätverks delen av IP-adressen för under näts tycken och Super-nett användning.</span><span class="sxs-lookup"><span data-stu-id="7d023-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="7d023-731">**default_pool** Pekare för att kontrol lera blockeringen av tidigare skapade NetX-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="7d023-732">**ip_network_driver** Nätverks driv rutin som anges av användaren som används för att skicka och ta emot IP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="7d023-733">**memory_ptr** Pekare till minnes området för IP Helper-trådens stack Area.</span><span class="sxs-lookup"><span data-stu-id="7d023-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="7d023-734">**memory_size** Antal byte i minnes området för IP Helper-trådens stack.</span><span class="sxs-lookup"><span data-stu-id="7d023-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="7d023-735">**prioritet** Prioritet för IP Helper-tråd.</span><span class="sxs-lookup"><span data-stu-id="7d023-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-736">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-736">Return Values</span></span>
- <span data-ttu-id="7d023-737">**NX_SUCCESS** (0x00) en lyckad IP-instans skapas.</span><span class="sxs-lookup"><span data-stu-id="7d023-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="7d023-738">**NX_NOT_IMPLEMENTED** (0X4A) netx-biblioteket är felaktigt konfigurerat.</span><span class="sxs-lookup"><span data-stu-id="7d023-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="7d023-739">**NX_PTR_ERROR** (0X07) ogiltig IP, nätverks driv rutin funktion pekare, adresspool eller minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="7d023-740">**NX_SIZE_ERROR** (0X09) den angivna stack storleken är för liten.</span><span class="sxs-lookup"><span data-stu-id="7d023-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="7d023-741">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-742">**NX_IP_ADDRESS_ERROR** (0X21) den angivna IP-adressen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="7d023-743">**NX_OPTION_ERROR** (0X21) den angivna prioriteten för IP-tråd är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-744">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-744">Allowed From</span></span>

<span data-ttu-id="7d023-745">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-746">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-746">Preemption Possible</span></span>

<span data-ttu-id="7d023-747">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-747">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-748">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-749">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-749">See Also</span></span>

- <span data-ttu-id="7d023-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-751">nx_ip_delete nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-752">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-753">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="7d023-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="7d023-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-756">nx_ip_delete</span></span>

<span data-ttu-id="7d023-757">Ta bort den tidigare skapade IP-instansen</span><span class="sxs-lookup"><span data-stu-id="7d023-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-758">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-759">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-759">Description</span></span>

<span data-ttu-id="7d023-760">Den här tjänsten tar bort en tidigare skapad IP-instans och släpper alla system resurser som ägs av IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-761">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-761">Parameters</span></span>
- <span data-ttu-id="7d023-762">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-763">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-763">Return Values</span></span>

- <span data-ttu-id="7d023-764">**NX_SUCCESS** (0x00) IP-borttagning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="7d023-765">**NX_SOCKETS_BOUND** (0X28) den här IP-instansen har fortfarande UDP-eller TCP-Sockets kopplade till sig.</span><span class="sxs-lookup"><span data-stu-id="7d023-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="7d023-766">Alla Sockets måste vara obundna och tas bort innan IP-instansen tas bort.</span><span class="sxs-lookup"><span data-stu-id="7d023-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="7d023-767">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-768">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-769">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-769">Allowed From</span></span>

<span data-ttu-id="7d023-770">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-771">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-771">Preemption Possible</span></span>

<span data-ttu-id="7d023-772">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-773">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-774">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-774">See Also</span></span>

- <span data-ttu-id="7d023-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-776">nx_ip_create nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-777">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-778">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="7d023-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="7d023-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="7d023-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="7d023-782">Issue-kommando för nätverks driv rutin</span><span class="sxs-lookup"><span data-stu-id="7d023-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-783">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-784">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-784">Description</span></span>

<span data-ttu-id="7d023-785">Den här tjänsten tillhandahåller ett direkt gränssnitt till programmets primära nätverks gränssnitts driv rutin som anges under ***nx_ip_create*** -anropet.</span><span class="sxs-lookup"><span data-stu-id="7d023-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="7d023-786">Programspecifika kommandon kan användas för att tillhandahålla ett numeriskt värde som är större än eller lika med NX_LINK_USER_COMMAND.</span><span class="sxs-lookup"><span data-stu-id="7d023-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="7d023-787">*Om du vill utfärda kommando för den sekundära enheten använder du tjänsten **nx_ip_driver_interface_direct_command** .*</span><span class="sxs-lookup"><span data-stu-id="7d023-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-788">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-788">Parameters</span></span>

- <span data-ttu-id="7d023-789">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-790">**kommando** Numerisk kommando kod.</span><span class="sxs-lookup"><span data-stu-id="7d023-790">**command** Numeric command code.</span></span> <span data-ttu-id="7d023-791">Standard kommandon definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="7d023-792">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="7d023-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="7d023-793">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="7d023-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="7d023-794">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="7d023-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="7d023-795">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="7d023-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="7d023-796">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="7d023-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="7d023-797">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="7d023-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="7d023-798">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="7d023-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="7d023-799">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="7d023-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="7d023-800">**return_value_ptr** Pekare som returnerar variabeln i anroparen.</span><span class="sxs-lookup"><span data-stu-id="7d023-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-801">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-801">Return Values</span></span>

- <span data-ttu-id="7d023-802">**NX_SUCCESS** (0x00) enhets direkt kommando för nätverks driv rutin.</span><span class="sxs-lookup"><span data-stu-id="7d023-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="7d023-803">**NX_UNHANDLED_COMMAND** (0x44) ohanterad eller ej implementerad nätverks driv rutin kommando.</span><span class="sxs-lookup"><span data-stu-id="7d023-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="7d023-804">**NX_PTR_ERROR** (0X07) ogiltig IP-eller RETUR värdes pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="7d023-805">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-806">**NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitts index.</span><span class="sxs-lookup"><span data-stu-id="7d023-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-807">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-807">Allowed From</span></span>

<span data-ttu-id="7d023-808">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-808">Threads</span></span>

- <span data-ttu-id="7d023-809">**Avstängningen möjlig**</span><span class="sxs-lookup"><span data-stu-id="7d023-809">**Preemption Possible**</span></span>

<span data-ttu-id="7d023-810">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-810">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-811">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-812">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-812">See Also</span></span>

- <span data-ttu-id="7d023-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="7d023-815">nx_ip_forwarding_disable nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="7d023-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-817">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="7d023-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="7d023-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="7d023-819">Issue-kommando för nätverks driv rutin</span><span class="sxs-lookup"><span data-stu-id="7d023-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-820">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-821">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-821">Description</span></span>

<span data-ttu-id="7d023-822">Den här tjänsten tillhandahåller ett direkt kommando för programmets nätverks enhets driv rutin i IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="7d023-823">Programspecifika kommandon kan användas för att tillhandahålla ett numeriskt värde som är större än eller lika med *NX_LINK_USER_COMMAND*.</span><span class="sxs-lookup"><span data-stu-id="7d023-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-824">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-824">Parameters</span></span>

- <span data-ttu-id="7d023-825">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-826">**kommando** Numerisk kommando kod.</span><span class="sxs-lookup"><span data-stu-id="7d023-826">**command** Numeric command code.</span></span> <span data-ttu-id="7d023-827">Standard kommandon definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="7d023-828">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="7d023-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="7d023-829">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="7d023-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="7d023-830">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="7d023-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="7d023-831">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="7d023-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="7d023-832">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="7d023-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="7d023-833">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="7d023-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="7d023-834">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="7d023-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="7d023-835">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="7d023-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="7d023-836">**interface_index** Index för det nätverks gränssnitt som kommandot ska skickas till.</span><span class="sxs-lookup"><span data-stu-id="7d023-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="7d023-837">**return_value_ptr** Pekare som returnerar variabeln i anroparen.</span><span class="sxs-lookup"><span data-stu-id="7d023-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-838">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-838">Return Values</span></span>
- <span data-ttu-id="7d023-839">**NX_SUCCESS** (0x00) enhets direkt kommando för nätverks driv rutin.</span><span class="sxs-lookup"><span data-stu-id="7d023-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="7d023-840">**NX_UNHANDLED_COMMAND** (0x44) ohanterad eller ej implementerad nätverks driv rutin kommando.</span><span class="sxs-lookup"><span data-stu-id="7d023-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="7d023-841">**NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="7d023-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="7d023-842">**NX_PTR_ERROR** (0X07) ogiltig IP-eller RETUR värdes pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="7d023-843">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-844">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-844">Allowed From</span></span>

<span data-ttu-id="7d023-845">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-846">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-846">Preemption Possible</span></span>

<span data-ttu-id="7d023-847">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-847">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-848">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-849">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-849">See Also</span></span>

- <span data-ttu-id="7d023-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-852">nx_ip_forwarding_disable nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="7d023-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-854">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="7d023-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="7d023-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="7d023-856">Inaktivera vidarebefordran av IP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-857">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-858">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-858">Description</span></span>

<span data-ttu-id="7d023-859">Den här tjänsten inaktiverar vidarebefordring av IP-paket i IP-komponenten NetX.</span><span class="sxs-lookup"><span data-stu-id="7d023-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="7d023-860">Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.</span><span class="sxs-lookup"><span data-stu-id="7d023-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-861">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-861">Parameters</span></span>

- <span data-ttu-id="7d023-862">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-863">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-863">Return Values</span></span>

- <span data-ttu-id="7d023-864">**NX_SUCCESS** (0x00)-slutförd IP-vidarebefordring inaktivera.</span><span class="sxs-lookup"><span data-stu-id="7d023-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="7d023-865">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-866">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-867">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-867">Allowed From</span></span>

<span data-ttu-id="7d023-868">Initiering, trådar, timers</span><span class="sxs-lookup"><span data-stu-id="7d023-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-869">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-869">Preemption Possible</span></span>

<span data-ttu-id="7d023-870">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-870">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-871">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-872">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-872">See Also</span></span>

- <span data-ttu-id="7d023-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-875">nx_ip_driver_interface_direct_command nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="7d023-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-877">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="7d023-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="7d023-879">Aktivera vidarebefordran av IP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-880">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-881">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-881">Description</span></span>

<span data-ttu-id="7d023-882">Den här tjänsten aktiverar vidarebefordring av IP-paket i NetX-IP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="7d023-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="7d023-883">Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.</span><span class="sxs-lookup"><span data-stu-id="7d023-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-884">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-884">Parameters</span></span>

- <span data-ttu-id="7d023-885">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-886">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-886">Return Values</span></span>
- <span data-ttu-id="7d023-887">**NX_SUCCESS** (0X00) lyckad IP-vidarebefordring aktivera.</span><span class="sxs-lookup"><span data-stu-id="7d023-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="7d023-888">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-889">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-890">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-890">Allowed From</span></span>

<span data-ttu-id="7d023-891">Initiering, trådar, timers</span><span class="sxs-lookup"><span data-stu-id="7d023-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-892">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-892">Preemption Possible</span></span>

<span data-ttu-id="7d023-893">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-893">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-894">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-895">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-895">See Also</span></span>

- <span data-ttu-id="7d023-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-898">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-900">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="7d023-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="7d023-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="7d023-902">Inaktivera fragmentering av IP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-903">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-904">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-904">Description</span></span>

<span data-ttu-id="7d023-905">Den här tjänsten inaktiverar funktionen för fragmentering och sammansättning av IP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="7d023-906">För paket som väntar på att ommonteras, frigör tjänsten dessa paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="7d023-907">Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.</span><span class="sxs-lookup"><span data-stu-id="7d023-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-908">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-908">Parameters</span></span>

- <span data-ttu-id="7d023-909">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-910">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-910">Return Values</span></span>
- <span data-ttu-id="7d023-911">**NX_SUCCESS** (0x00) IP-fragment har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="7d023-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="7d023-912">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-913">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-914">**NX_NOT_ENABLED** (0x14) IP-fragmentering är inte aktive rad på IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-915">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-915">Allowed From</span></span>

<span data-ttu-id="7d023-916">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-917">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-917">Preemption Possible</span></span>

<span data-ttu-id="7d023-918">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-918">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-919">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-920">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-920">See Also</span></span>

- <span data-ttu-id="7d023-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-923">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-925">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="7d023-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="7d023-927">Aktivera fragmentering av IP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-928">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-929">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-929">Description</span></span>

<span data-ttu-id="7d023-930">Den här tjänsten aktiverar funktioner för att fragmentera och ommontera IP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="7d023-931">Den här tjänsten inaktive ras automatiskt när du skapar IP-uppgiften.</span><span class="sxs-lookup"><span data-stu-id="7d023-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-932">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-932">Parameters</span></span>

- <span data-ttu-id="7d023-933">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-934">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-934">Return Values</span></span>

- <span data-ttu-id="7d023-935">**NX_SUCCESS** (0X00) lyckades aktivera IP-fragment.</span><span class="sxs-lookup"><span data-stu-id="7d023-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="7d023-936">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-937">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-938">**NX_NOT_ENABLED** (0x14) funktioner för IP-fragmentering har inte kompilerats i netx.</span><span class="sxs-lookup"><span data-stu-id="7d023-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-939">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-939">Allowed From</span></span>

<span data-ttu-id="7d023-940">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-941">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-941">Preemption Possible</span></span>

<span data-ttu-id="7d023-942">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-942">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-943">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-944">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-944">See Also</span></span>

- <span data-ttu-id="7d023-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-947">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="7d023-949">nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="7d023-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="7d023-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="7d023-951">Ange IP-adress för gateway</span><span class="sxs-lookup"><span data-stu-id="7d023-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-952">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="7d023-953">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-953">Description</span></span>

<span data-ttu-id="7d023-954">Den här tjänsten anger IP-gatewayens IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="7d023-955">All trafik utanför nätverket dirigeras till den här gatewayen för överföring.</span><span class="sxs-lookup"><span data-stu-id="7d023-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="7d023-956">Gatewayen måste vara direkt tillgänglig via ett av nätverks gränssnitten.</span><span class="sxs-lookup"><span data-stu-id="7d023-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-957">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-957">Parameters</span></span>

- <span data-ttu-id="7d023-958">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-959">**ip_address** IP-adressen för gatewayen.</span><span class="sxs-lookup"><span data-stu-id="7d023-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-960">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-960">Return Values</span></span>

- <span data-ttu-id="7d023-961">**NX_SUCCESS** (0X00) GATEWAYens IP-adress har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="7d023-962">**NX_PTR_ERROR** (0X07) ogiltig IP-instans pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="7d023-963">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-964">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-965">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-965">Allowed From</span></span>

<span data-ttu-id="7d023-966">Initiering, tråd</span><span class="sxs-lookup"><span data-stu-id="7d023-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-967">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-967">Preemption Possible</span></span>

<span data-ttu-id="7d023-968">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-968">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-969">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="7d023-970">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-970">See Also</span></span>

- <span data-ttu-id="7d023-971">nx_ip_info_get nx_ip_static_route_add nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="7d023-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-972">nx_ip_info_get</span></span>

<span data-ttu-id="7d023-973">Hämta information om IP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-974">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="7d023-975">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-975">Description</span></span>

<span data-ttu-id="7d023-976">Den här tjänsten hämtar information om IP-aktiviteter för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="7d023-977">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-978">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-978">Parameters</span></span>

- <span data-ttu-id="7d023-979">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-980">**ip_total_packets_sent** Pekare till målet för det totala antalet skickade IP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="7d023-981">**ip_total_bytes_sent** Pekare till målet för det totala antalet byte som har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="7d023-982">**ip_total_packets_received** Pekare till målet för det totala antalet IP-mottagna paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="7d023-983">**ip_total_bytes_received** Pekare till målet för det totala antalet mottagna IP-byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="7d023-984">**ip_invalid_packets** Pekare till målet för det totala antalet ogiltiga IP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="7d023-985">**ip_receive_packets_dropped** Pekare till målet för det totala antalet mottagna paket som har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="7d023-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="7d023-986">**ip_receive_checksum_errors** Pekare till målet för det totala antalet fel i kontroll summor i mottagna paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="7d023-987">**ip_send_packets_dropped** Pekare till målet för det totala antalet skickade paket som släppts.</span><span class="sxs-lookup"><span data-stu-id="7d023-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="7d023-988">**ip_total_fragments_sent** Pekare till målet för det totala antalet fragment som skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="7d023-989">**ip_total_fragments_received** Pekare till målet för det totala antalet fragment som tagits emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-990">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-990">Return Values</span></span>

- <span data-ttu-id="7d023-991">**NX_SUCCESS** (0x00) hämtning av IP-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="7d023-992">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-993">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-994">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-994">Allowed From</span></span>

<span data-ttu-id="7d023-995">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-996">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-996">Preemption Possible</span></span>

<span data-ttu-id="7d023-997">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-997">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-998">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-999">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-999">See Also</span></span>

- <span data-ttu-id="7d023-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-1002">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-1003">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-1004">nx_ip_fragment_enable nx_ip_status_check nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="7d023-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="7d023-1006">Hämta gränssnittets IP-adress</span><span class="sxs-lookup"><span data-stu-id="7d023-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1007">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="7d023-1008">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1008">Description</span></span>

<span data-ttu-id="7d023-1009">Den här tjänsten hämtar IP-adressen för ett angivet nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="7d023-1010">*Den angivna enheten måste, om den inte är den primära enheten, vara tidigare ansluten till IP-instansen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1011">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1011">Parameters</span></span>

- <span data-ttu-id="7d023-1012">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1013">**interface_index** Gränssnitts index, samma värde som indexet till nätverks gränssnittet som är kopplat till IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="7d023-1014">**ip_address** Pekare till målet för enhets gränssnittets IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="7d023-1015">**network_mask** Pekare till målet för enhets gränssnittets nätverks mask.</span><span class="sxs-lookup"><span data-stu-id="7d023-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1016">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1016">Return Values</span></span>

- <span data-ttu-id="7d023-1017">**NX_SUCCESS** (0X00) IP-adress hämtades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="7d023-1018">**NX_INVALID_INTERFACE** (0x4C) det angivna nätverks gränssnittet är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="7d023-1019">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1020">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1021">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1021">Allowed From</span></span>

<span data-ttu-id="7d023-1022">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1023">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1023">Preemption Possible</span></span>

<span data-ttu-id="7d023-1024">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1025">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1026">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1026">See Also</span></span>

- <span data-ttu-id="7d023-1027">nx_ip_interface_address_set nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="7d023-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="7d023-1028">nx_ip_interface_info_get nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="7d023-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="7d023-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="7d023-1031">Ange gränssnittets IP-adress och nätverks mask</span><span class="sxs-lookup"><span data-stu-id="7d023-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1032">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="7d023-1033">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1033">Description</span></span>

<span data-ttu-id="7d023-1034">Den här tjänsten anger IP-adressen och nätverks masken för det angivna IP-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="7d023-1035">*Det angivna gränssnittet måste vara kopplat till IP-instansen tidigare.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1036">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1036">Parameters</span></span>

- <span data-ttu-id="7d023-1037">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1038">**interface_index** Index för det gränssnitt som är kopplat till NetX-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="7d023-1039">**ip_address** Nytt IP-adress för nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="7d023-1040">**network_mask** Nätverks mask för nytt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1041">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1041">Return Values</span></span>

- <span data-ttu-id="7d023-1042">Den angivna IP-adressen för **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="7d023-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="7d023-1043">**NX_INVALID_INTERFACE** (0x4C) det angivna nätverks gränssnittet är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="7d023-1044">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1045">**NX_PTR_ERROR** (0X07) ogiltiga pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="7d023-1046">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress</span><span class="sxs-lookup"><span data-stu-id="7d023-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1047">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1047">Allowed From</span></span>

<span data-ttu-id="7d023-1048">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1049">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1049">Preemption Possible</span></span>

<span data-ttu-id="7d023-1050">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1051">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1052">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1052">See Also</span></span>

- <span data-ttu-id="7d023-1053">nx_ip_interface_address_get nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="7d023-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="7d023-1054">nx_ip_interface_info_get nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="7d023-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="7d023-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="7d023-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="7d023-1057">Koppla nätverks gränssnitt till IP-instans</span><span class="sxs-lookup"><span data-stu-id="7d023-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1058">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="7d023-1059">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1059">Description</span></span>

<span data-ttu-id="7d023-1060">Den här tjänsten lägger till ett fysiskt nätverks gränssnitt i IP-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="7d023-1061">Observera att IP-instansen skapas med det primära gränssnittet så att varje ytterligare gränssnitt är sekundärt till det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="7d023-1062">Det totala antalet nätverks gränssnitt som är kopplade till IP-instansen (inklusive det primära gränssnittet) får inte överskrida **NX_MAX_PHYSICAL_INTERFACES**.</span><span class="sxs-lookup"><span data-stu-id="7d023-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="7d023-1063">Om IP-tråden inte har körts än kommer de sekundära gränssnitten att initieras som en del av start processen för IP-tråd som initierar alla fysiska gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="7d023-1064">Om IP-tråden inte körs ännu initieras det sekundära gränssnittet som en del av ***nx_ip_interface_attachs*** tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="7d023-1065">*ip_ptr måste peka på en giltig IP-struktur för NetX.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="7d023-1066">***NX_MAX_PHYSICAL_INTERFACES** måste konfigureras för antalet nätverks gränssnitt för IP-instansen. Standardvärdet är ett.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1067">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1067">Parameters</span></span>

- <span data-ttu-id="7d023-1068">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1069">**INTERFACE_NAME** Pekare till gränssnittets namn sträng.</span><span class="sxs-lookup"><span data-stu-id="7d023-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="7d023-1070">**ip_address** Enhetens IP-adress i byte ordningen för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="7d023-1071">**network_mask** Enhetens nätverks mask i byte ordningen för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="7d023-1072">**ip_link_driver** Ethernet-drivrutin för gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1073">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1073">Return Values</span></span>

- <span data-ttu-id="7d023-1074">**NX_SUCCESS** -posten (0x00) läggs till i den statiska routningstabellen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="7d023-1075">**NX_NO_MORE_ENTRIES** (0X17) Max antal gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="7d023-1076">**NX_MAX_PHYSICAL_INTERFACES** har överskridits.</span><span class="sxs-lookup"><span data-stu-id="7d023-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="7d023-1077">**NX_DUPLICATED_ENTRY** (0X52) den angivna IP-adressen används redan på den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="7d023-1078">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1079">**NX_PTR_ERROR** (0X07) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="7d023-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="7d023-1080">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress för indata.</span><span class="sxs-lookup"><span data-stu-id="7d023-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1081">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1081">Allowed From</span></span>

<span data-ttu-id="7d023-1082">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1083">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1083">Preemption Possible</span></span>

<span data-ttu-id="7d023-1084">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1085">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1086">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1086">See Also</span></span>

- <span data-ttu-id="7d023-1087">nx_ip_interface_address_get nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="7d023-1088">nx_ip_interface_info_get nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="7d023-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="7d023-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="7d023-1091">Hämta nätverks gränssnitts parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-1092">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="7d023-1093">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1093">Description</span></span>

<span data-ttu-id="7d023-1094">Den här tjänsten hämtar information om nätverks parametrar för det angivna nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="7d023-1095">Alla data hämtas i byte ordning för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="7d023-1096">*ip_ptr måste peka på en giltig IP-struktur för NetX. Det angivna gränssnittet, om inte det primära gränssnittet, måste vara tidigare kopplat till IP-instansen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1097">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1097">Parameters</span></span>

- <span data-ttu-id="7d023-1098">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1099">**interface_index** Index som anger nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="7d023-1100">**INTERFACE_NAME** Pekar på den buffert som innehåller namnet på nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="7d023-1101">**ip_address** Pekar till målet för gränssnittets IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="7d023-1102">**network_mask** Pekare till målet för nätverks masken.</span><span class="sxs-lookup"><span data-stu-id="7d023-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="7d023-1103">**mtu_size** Pekare till målet för den maximala överförings enheten för det här gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="7d023-1104">**physical_address_msw** Pekare till målet för de 16 främsta bitarna i enhetens MAC-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="7d023-1105">**physical_address_lsw** Pekare till målet för nedre 32 bitar av enhetens MAC-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-1106">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1106">Return Values</span></span>
- <span data-ttu-id="7d023-1107">**NX_SUCCESS** (0X00) gränssnitts information har hämtats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="7d023-1108">**NX_PTR_ERROR** (0X07) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="7d023-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="7d023-1109">**NX_INVALID_INTERFACE** (0X4C) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1110">Tjänsten **NX_CALLER_ERROR** (0x11) anropas inte från system initiering eller tråd kontext.</span><span class="sxs-lookup"><span data-stu-id="7d023-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1111">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1111">Allowed From</span></span>

<span data-ttu-id="7d023-1112">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1113">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1113">Preemption Possible</span></span>

<span data-ttu-id="7d023-1114">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1115">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1116">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1116">See Also</span></span>

- <span data-ttu-id="7d023-1117">nx_ip_interface_address_get nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="7d023-1118">nx_ip_interface_attach nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="7d023-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="7d023-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="7d023-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="7d023-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="7d023-1121">Kontrol lera status för en IP-instans</span><span class="sxs-lookup"><span data-stu-id="7d023-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-1122">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1123">Description</span></span>

<span data-ttu-id="7d023-1124">Den här tjänsten kontrollerar och väntar på den angivna statusen för nätverks gränssnittet för en tidigare skapad IP-instans.</span><span class="sxs-lookup"><span data-stu-id="7d023-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1125">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1125">Parameters</span></span>

- <span data-ttu-id="7d023-1126">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1127">**interface_index** Gränssnitts index nummer</span><span class="sxs-lookup"><span data-stu-id="7d023-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="7d023-1128">**needed_status** IP-status begärd, definierad i bit-Map-formulär enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="7d023-1129">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="7d023-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="7d023-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="7d023-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="7d023-1131">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="7d023-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="7d023-1132">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="7d023-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="7d023-1133">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="7d023-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="7d023-1134">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="7d023-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="7d023-1135">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="7d023-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="7d023-1136">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="7d023-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="7d023-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="7d023-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="7d023-1138">**actual_status** Pekare till målet för faktisk BITS-uppsättning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="7d023-1139">**wait_option** Definierar hur tjänsten fungerar om de begärda status bitarna inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="7d023-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="7d023-1140">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="7d023-1141">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="7d023-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="7d023-1143">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1144">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1144">Return Values</span></span>

- <span data-ttu-id="7d023-1145">**NX_SUCCESS** (0x00) kontroll av IP-status har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="7d023-1146">**NX_NOT_SUCCESSFUL** (0X43) status förfrågan uppfylldes inte inom den angivna tids gränsen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="7d023-1147">**NX_PTR_ERROR** (0x07) IP-pekaren är eller har blivit ogiltig eller så är den faktiska status pekaren ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="7d023-1148">**NX_OPTION_ERROR** (0X0a) ogiltigt status alternativ.</span><span class="sxs-lookup"><span data-stu-id="7d023-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="7d023-1149">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index är utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="7d023-1151">eller så är gränssnittet ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1152">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1152">Allowed From</span></span>

<span data-ttu-id="7d023-1153">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1154">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1154">Preemption Possible</span></span>

<span data-ttu-id="7d023-1155">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1156">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1157">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1157">See Also</span></span>

- <span data-ttu-id="7d023-1158">nx_ip_interface_address_get nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="7d023-1159">nx_ip_interface_attach nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="7d023-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="7d023-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="7d023-1162">Ange funktionen länk status ändring meddela motringning</span><span class="sxs-lookup"><span data-stu-id="7d023-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1163">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="7d023-1164">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1164">Description</span></span>

<span data-ttu-id="7d023-1165">Den här tjänsten konfigurerar funktionen länk status ändring meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="7d023-1166">Den användardefinierade *link_status_change_notify* rutinen anropas när antingen den primära eller sekundära gränssnitts statusen ändras (till exempel om IP-adressen har ändrats). Om *link_status_change_notify* är null, är länk status ändring meddela motringning funktion inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1167">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1167">Parameters</span></span>

- <span data-ttu-id="7d023-1168">**ip_ptr** Pekare för IP Control Block</span><span class="sxs-lookup"><span data-stu-id="7d023-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="7d023-1169">**link_status_change_notify** Återanrops funktion som användaren har angett för att anropas vid en ändring i det fysiska gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-1170">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1170">Return Values</span></span>

- <span data-ttu-id="7d023-1171">**NX_SUCCESS** (0x00) har angetts</span><span class="sxs-lookup"><span data-stu-id="7d023-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="7d023-1172">**NX_PTR_ERROR** (0X07) ogiltig kontroll block pekare eller ny fysisk adress pekare</span><span class="sxs-lookup"><span data-stu-id="7d023-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="7d023-1173">Tjänsten **NX_CALLER_ERROR** (0x11) anropas inte från system initiering eller tråd kontext.</span><span class="sxs-lookup"><span data-stu-id="7d023-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="7d023-1174">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1174">Allowed From</span></span>

<span data-ttu-id="7d023-1175">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1176">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1176">Preemption Possible</span></span>

<span data-ttu-id="7d023-1177">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1178">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1179">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1179">See Also</span></span>

- <span data-ttu-id="7d023-1180">nx_ip_interface_address_get nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="7d023-1181">nx_ip_interface_attach nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="7d023-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="7d023-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="7d023-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="7d023-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="7d023-1184">Inaktivera sändning/mottagning av RAW-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-1185">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1186">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1186">Description</span></span>

<span data-ttu-id="7d023-1187">Den här tjänsten inaktiverar överföring och mottagning av obehandlade IP-paket för den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="7d023-1188">Om RAW Packet service tidigare har Aktiver ATS och det finns RAW-paket i Receive-kön, kommer den här tjänsten att släppa eventuella mottagna rå paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1189">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1189">Parameters</span></span>

- <span data-ttu-id="7d023-1190">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1191">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1191">Return Values</span></span>

- <span data-ttu-id="7d023-1192">**NX_SUCCESS** (0X00) genomförde IP RAW-paket inaktivera.</span><span class="sxs-lookup"><span data-stu-id="7d023-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="7d023-1193">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1194">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1195">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1195">Allowed From</span></span>

<span data-ttu-id="7d023-1196">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1197">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1197">Preemption Possible</span></span>

<span data-ttu-id="7d023-1198">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1199">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1200">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1200">See Also</span></span>

- <span data-ttu-id="7d023-1201">nx_ip_raw_packet_enable nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="7d023-1202">nx_ip_raw_packet_send nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="7d023-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="7d023-1204">Aktivera rå paket bearbetning</span><span class="sxs-lookup"><span data-stu-id="7d023-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-1205">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1206">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1206">Description</span></span>

<span data-ttu-id="7d023-1207">Den här tjänsten möjliggör överföring och mottagning av RAW IP-paket för den här IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="7d023-1208">Inkommande TCP-, UDP-, ICMP-och IGMP-paket bearbetas fortfarande av NetX.</span><span class="sxs-lookup"><span data-stu-id="7d023-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="7d023-1209">Paket med okända protokoll typer för övre skikt bearbetas av rutinen för mottagning av rå paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1210">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1210">Parameters</span></span>

- <span data-ttu-id="7d023-1211">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1212">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1212">Return Values</span></span>

- <span data-ttu-id="7d023-1213">**NX_SUCCESS** (0X00) lyckade IP RAW-paket aktivera.</span><span class="sxs-lookup"><span data-stu-id="7d023-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="7d023-1214">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1215">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1216">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1216">Allowed From</span></span>

<span data-ttu-id="7d023-1217">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1218">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1218">Preemption Possible</span></span>

<span data-ttu-id="7d023-1219">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1220">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1221">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1221">See Also</span></span>

- <span data-ttu-id="7d023-1222">nx_ip_raw_packet_disable nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="7d023-1223">nx_ip_raw_packet_send nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="7d023-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="7d023-1225">Skicka RAW IP-paket via angivet nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="7d023-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1226">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="7d023-1227">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1227">Description</span></span>

<span data-ttu-id="7d023-1228">Den här tjänsten skickar ett RAW IP-paket till målets IP-adress med den angivna lokala IP-adressen som käll adress och via det associerade nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="7d023-1229">Observera att den här rutinen returnerar omedelbart och är därför inte känd om IP-paketet faktiskt har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="7d023-1230">Nätverks driv rutinen kommer att ansvara för att släppa paketet när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="7d023-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="7d023-1231">Den här tjänsten skiljer sig från andra tjänster eftersom det inte finns något sätt att veta om paketet faktiskt har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="7d023-1232">Det kan gå förlorat på Internet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="7d023-1233">*Observera att RAW IP-bearbetning måste vara aktiverat.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="7d023-1234">*Den här tjänsten liknar **nx_ip_raw_packet_send**, förutom att den här tjänsten tillåter att ett program skickar RAW IP-paket från ett angivet fysiskt gränssnitt.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1235">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1235">Parameters</span></span>

- <span data-ttu-id="7d023-1236">**ip_ptr** Pekare till en tidigare skapad IP-aktivitet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="7d023-1237">**packet_ptr** Pekare till paket att överföra.</span><span class="sxs-lookup"><span data-stu-id="7d023-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="7d023-1238">**destination_ip** IP-adress för att skicka paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="7d023-1239">**address_index** Index för den gränssnitts adress som paketet ska skickas till.</span><span class="sxs-lookup"><span data-stu-id="7d023-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="7d023-1240">**type_of_service** Typ av tjänst för paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1241">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1241">Return Values</span></span>

- <span data-ttu-id="7d023-1242">**NX_SUCCESS** (0X00) paket har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="7d023-1243">**NX_IP_ADDRESS_ERROR** (0X21) inget lämpligt utgående gränssnitt är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="7d023-1244">**NX_NOT_ENABLED** (0X14) RAW IP-paketfiltrering är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="7d023-1245">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1246">**NX_PTR_ERROR** (0X07) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="7d023-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="7d023-1247">**NX_OPTION_ERROR** (0X0a) ogiltig tjänst typ har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="7d023-1248">**NX_OVERFLOW** (0X03) ogiltig lägga pekare för paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="7d023-1249">**NX_UNDERFLOW** (protokollnumret 0x02) ogiltig lägga pekare för paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="7d023-1250">**NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitts index angavs.</span><span class="sxs-lookup"><span data-stu-id="7d023-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1251">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1251">Allowed From</span></span>

<span data-ttu-id="7d023-1252">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1253">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1253">Preemption Possible</span></span>

<span data-ttu-id="7d023-1254">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1255">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1256">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1256">See Also</span></span>

- <span data-ttu-id="7d023-1257">nx_ip_raw_packet_disable nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="7d023-1258">nx_ip_raw_packet_receive nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="7d023-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="7d023-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="7d023-1260">Ta emot RAW IP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1261">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1262">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1262">Description</span></span>

<span data-ttu-id="7d023-1263">Den här tjänsten tar emot ett RAW IP-paket från den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="7d023-1264">Om det finns IP-paket i kön för mottagna obearbetade paket returneras det första (äldsta) paketet till anroparen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="7d023-1265">Annars, om inga paket är tillgängliga, kan anroparen pausa så som anges av alternativet vänta.</span><span class="sxs-lookup"><span data-stu-id="7d023-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="7d023-1266">*Om NX_SUCCESS returneras, ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1267">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1267">Parameters</span></span>

- <span data-ttu-id="7d023-1268">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1269">**packet_ptr** Pekare till pekaren för att placera det mottagna RAW IP-paketet i.</span><span class="sxs-lookup"><span data-stu-id="7d023-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="7d023-1270">**wait_option** Definierar hur tjänsten fungerar om det inte finns några tillgängliga obehandlade IP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="7d023-1271">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1272">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1274">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1275">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1275">Return Values</span></span>

- <span data-ttu-id="7d023-1276">**NX_SUCCESS** (0x00) Det gick inte att ta emot IP RAW-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="7d023-1277">**NX_NO_PACKET** (0X01) inget paket var tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="7d023-1278">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-1279">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-1280">**NX_PTR_ERROR** (0X07) ogiltig IP eller RETUR paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="7d023-1281">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="7d023-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1282">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1282">Allowed From</span></span>

<span data-ttu-id="7d023-1283">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1284">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1284">Preemption Possible</span></span>

<span data-ttu-id="7d023-1285">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1286">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1287">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1287">See Also</span></span>

- <span data-ttu-id="7d023-1288">nx_ip_raw_packet_disable nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="7d023-1289">nx_ip_raw_packet_send nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="7d023-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="7d023-1291">Skicka RAW IP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1292">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="7d023-1293">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1293">Description</span></span>

<span data-ttu-id="7d023-1294">Den här tjänsten skickar ett RAW IP-paket till målets IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="7d023-1295">Observera att den här rutinen returnerar omedelbart och är därför inte känd om IP-paketet faktiskt har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="7d023-1296">Nätverks driv rutinen kommer att ansvara för att släppa paketet när överföringen är klar.</span><span class="sxs-lookup"><span data-stu-id="7d023-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="7d023-1297">För ett multihome-system använder NetX målets IP-adress för att hitta ett lämpligt nätverks gränssnitt och använder gränssnittets IP-adress som käll adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="7d023-1298">Om mål-IP-adressen är broadcast eller multicast används det första giltiga gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="7d023-1299">Programmen använder ***nx_ip_raw_packet_interface_send*** i det här fallet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="7d023-1300">*Om ett fel returneras ska programmet inte släppa paketet efter det här anropet. På så sätt kan oväntade resultat uppstå, eftersom nätverks driv rutinen kommer att släppa paketet efter överföringen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1301">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1301">Parameters</span></span>

- <span data-ttu-id="7d023-1302">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1303">**packet_ptr** Pekare till det RAW IP-paket som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="7d023-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="7d023-1304">**destination_ip** Målets IP-adress, som kan vara en speciell värd-IP-adress, en nätverks sändning, en intern loop eller en multicast-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="7d023-1305">**type_of_service** Definierar typ av tjänst för överföringen, de juridiska värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="7d023-1306">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="7d023-1307">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="7d023-1308">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="7d023-1309">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="7d023-1310">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-1311">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1311">Return Values</span></span>

- <span data-ttu-id="7d023-1312">**NX_SUCCESS** (0X00) lyckade IP RAW-paket sändning initierad.</span><span class="sxs-lookup"><span data-stu-id="7d023-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="7d023-1313">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-1314">**NX_NOT_ENABLED** (0X14) RAW IP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="7d023-1315">**NX_OPTION_ERROR** (0X0a) ogiltig typ av tjänst.</span><span class="sxs-lookup"><span data-stu-id="7d023-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="7d023-1316">**NX_UNDERFLOW** (protokollnumret 0x02) inte tillräckligt med utrymme för att lägga ett IP-huvud i paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="7d023-1317">**NX_OVERFLOW** (0X03) paket tilläggs pekare är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="7d023-1318">**NX_PTR_ERROR** (0X07) ogiltig IP-eller paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="7d023-1319">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1320">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1320">Allowed From</span></span>

<span data-ttu-id="7d023-1321">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1322">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1322">Preemption Possible</span></span>

<span data-ttu-id="7d023-1323">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1324">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1325">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1325">See Also</span></span>

- <span data-ttu-id="7d023-1326">nx_ip_raw_packet_disable nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="7d023-1327">nx_ip_raw_packet_receive nx_ip_raw_packet_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="7d023-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="7d023-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="7d023-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="7d023-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="7d023-1330">Lägg till statisk väg i routningstabellen</span><span class="sxs-lookup"><span data-stu-id="7d023-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1331">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="7d023-1332">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1332">Description</span></span>

<span data-ttu-id="7d023-1333">Den här tjänsten lägger till en post i tabellen för statisk routning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="7d023-1334">Observera att den *next_hop* adressen måste vara direkt åtkomlig från en av de lokala nätverks enheterna.</span><span class="sxs-lookup"><span data-stu-id="7d023-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="7d023-1335">*Observera att ip_ptr måste peka på en giltig IP-struktur för NetX och NetX-biblioteket måste skapas med NX_ENABLE_IP_STATIC_ROUTING som har definierats för att använda den här tjänsten. Som standard skapas NetX utan att NX_ENABLE_IP_STATIC_ROUTING definieras.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1336">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1336">Parameters</span></span>

- <span data-ttu-id="7d023-1337">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1338">**network_address** Mål nätverks adress, i byte ordning för värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="7d023-1339">**net_mask** Mål nätverks mask, i byte ordning för värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="7d023-1340">**next_hop** Nästa hopp adress för mål nätverket, i byte ordning för värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1341">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1341">Return Values</span></span>

- <span data-ttu-id="7d023-1342">**NX_SUCCESSs** posten (0x00) läggs till i tabellen med statiska vägar.</span><span class="sxs-lookup"><span data-stu-id="7d023-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="7d023-1343">**NX_OVERFLOW** (0X03) statisk routningstabell är full.</span><span class="sxs-lookup"><span data-stu-id="7d023-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="7d023-1344">**NX_NOT_SUPPORTED** (0X4B) den här funktionen är inte kompilerad i.</span><span class="sxs-lookup"><span data-stu-id="7d023-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="7d023-1345">**NX_IP_ADDRESS_ERROR** (0X21) nästa hopp är inte direkt tillgängligt via lokala gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="7d023-1346">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1347">**NX_PTR_ERROR** (0X07) ogiltig ip_ptr pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1348">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1348">Allowed From</span></span>

<span data-ttu-id="7d023-1349">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1350">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1350">Preemption Possible</span></span>

<span data-ttu-id="7d023-1351">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1352">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1353">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1353">See Also</span></span>

- <span data-ttu-id="7d023-1354">nx_ip_gateway_address_set nx_ip_info_get nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="7d023-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="7d023-1356">Ta bort statisk väg från routningstabell</span><span class="sxs-lookup"><span data-stu-id="7d023-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1357">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="7d023-1358">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1358">Description</span></span>

<span data-ttu-id="7d023-1359">Den här tjänsten tar bort en post från tabellen för statisk routning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="7d023-1360">*Observera att ip_ptr måste peka på en giltig IP-struktur för NetX och NetX-biblioteket måste skapas med NX_ENABLE_IP_STATIC_ROUTING som har definierats för att använda den här tjänsten. Som standard skapas NetX utan att NX_ENABLE_IP_STATIC_ROUTING definieras.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1361">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1361">Parameters</span></span>

- <span data-ttu-id="7d023-1362">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1363">**network_address** Mål nätverks adress i byte ordning för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="7d023-1364">**net_mask** Mål nätverks mask i byte ordning för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1365">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1365">Allowed From</span></span>

<span data-ttu-id="7d023-1366">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1367">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1367">Preemption Possible</span></span>

<span data-ttu-id="7d023-1368">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1369">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1370">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1370">See Also</span></span>

- <span data-ttu-id="7d023-1371">nx_ip_gateway_address_set nx_ip_info_get nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="7d023-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="7d023-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="7d023-1372">nx_ip_status_check</span></span>

<span data-ttu-id="7d023-1373">Kontrol lera status för en IP-instans</span><span class="sxs-lookup"><span data-stu-id="7d023-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1374">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1375">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1375">Description</span></span>

<span data-ttu-id="7d023-1376">Den här tjänsten kontrollerar och väntar på den angivna statusen för det primära nätverks gränssnittet för en tidigare skapad IP-instans.</span><span class="sxs-lookup"><span data-stu-id="7d023-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="7d023-1377">För att få status för sekundära gränssnitt, ska program använda tjänsten ***nx_ip_interface_status_check.***</span><span class="sxs-lookup"><span data-stu-id="7d023-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1378">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1378">Parameters</span></span>

- <span data-ttu-id="7d023-1379">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1380">**needed_status** IP-status begärd, definierad i bit-Map-formulär enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="7d023-1381">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="7d023-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="7d023-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="7d023-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="7d023-1383">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="7d023-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="7d023-1384">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="7d023-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="7d023-1385">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="7d023-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="7d023-1386">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="7d023-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="7d023-1387">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="7d023-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="7d023-1388">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="7d023-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="7d023-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="7d023-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="7d023-1390">**actual_status** Pekare till målet för faktisk BITS-uppsättning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="7d023-1391">**wait_option** Definierar hur tjänsten fungerar om de begärda status bitarna inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="7d023-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="7d023-1392">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1393">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1395">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1396">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1396">Return Values</span></span>

- <span data-ttu-id="7d023-1397">**NX_SUCCESS** (0x00) kontroll av IP-status har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="7d023-1398">**NX_NOT_SUCCESSFUL** (0X43) status förfrågan uppfylldes inte inom den angivna tids gränsen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="7d023-1399">**NX_PTR_ERROR** (0x07) IP-pekaren är eller har blivit ogiltig eller så är den faktiska status pekaren ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="7d023-1400">**NX_OPTION_ERROR** (0X0a) ogiltigt status alternativ.</span><span class="sxs-lookup"><span data-stu-id="7d023-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="7d023-1401">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1402">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1402">Allowed From</span></span>

<span data-ttu-id="7d023-1403">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1404">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1404">Preemption Possible</span></span>

<span data-ttu-id="7d023-1405">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1406">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1407">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1407">See Also</span></span>

- <span data-ttu-id="7d023-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-1410">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-1411">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-1412">nx_ip_fragment_enable nx_ip_info_get nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="7d023-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7d023-1413">nx_packet_allocate</span></span>

<span data-ttu-id="7d023-1414">Allokera paket från angiven pool</span><span class="sxs-lookup"><span data-stu-id="7d023-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1415">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1416">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1416">Description</span></span>

<span data-ttu-id="7d023-1417">Den här tjänsten allokerar ett paket från den angivna poolen och justerar lägga-pekaren i paketet enligt den typ av paket som angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="7d023-1418">Om inget paket är tillgängligt pausas tjänsten enligt det angivna vänte alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1419">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1419">Parameters</span></span>

- <span data-ttu-id="7d023-1420">**pool_ptr** Pekare till den tidigare skapade lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="7d023-1421">**packet_ptr** Pekare till pekaren över den allokerade paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="7d023-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="7d023-1422">**packet_type** Definierar den typ av paket som begärs.</span><span class="sxs-lookup"><span data-stu-id="7d023-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="7d023-1423">Se "paket pooler" på sidan 49 i kapitel 3 för en lista över paket typer som stöds.</span><span class="sxs-lookup"><span data-stu-id="7d023-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="7d023-1424">**wait_option** Definierar vänte tiden i Tick om det inte finns några tillgängliga paket i modempoolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="7d023-1425">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1426">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1428">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1429">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1429">Return Values</span></span>

- <span data-ttu-id="7d023-1430">**NX_SUCCESS** (0x00) paket tilldelningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="7d023-1431">**NX_NO_PACKET** (0X01) inget paket tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="7d023-1432">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-1433">**NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="7d023-1434">**NX_OPTION_ERROR** (0X0a) ogiltig pakettyp.</span><span class="sxs-lookup"><span data-stu-id="7d023-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="7d023-1435">**NX_PTR_ERROR** (0X07) ogiltig pool eller paket retur pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="7d023-1436">**NX_CALLER_ERROR** (0X11) ogiltigt wait-alternativ från icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="7d023-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1437">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1437">Allowed From</span></span>

<span data-ttu-id="7d023-1438">Initiering, trådar, timers och ISR: er (program nätverks driv rutiner).</span><span class="sxs-lookup"><span data-stu-id="7d023-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="7d023-1439">Alternativet wait måste vara NX_NO_WAIT när det används i ISR eller i timer-kontext.</span><span class="sxs-lookup"><span data-stu-id="7d023-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1440">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1440">Preemption Possible</span></span>

<span data-ttu-id="7d023-1441">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1442">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1443">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1443">See Also</span></span>

- <span data-ttu-id="7d023-1444">nx_packet_copy nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1445">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="7d023-1447">nx_packet_pool_info_get nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="7d023-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="7d023-1449">nx_packet_copy</span></span>

<span data-ttu-id="7d023-1450">Kopiera paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1451">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1452">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1452">Description</span></span>

<span data-ttu-id="7d023-1453">Den här tjänsten kopierar informationen i det angivna paketet till ett eller flera nya paket som tilldelas från den angivna poolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="7d023-1454">Om det lyckas returneras pekaren till det nya paketet i destinationen som **new_packet_ptr**.</span><span class="sxs-lookup"><span data-stu-id="7d023-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1455">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1455">Parameters</span></span>

- <span data-ttu-id="7d023-1456">**packet_ptr** Pekare till käll paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="7d023-1457">**new_packet_ptr** Pekar till målet där pekaren återgår till den nya kopian av paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="7d023-1458">**pool_ptr** Visar en pekare till den tidigare skapade Packet-poolen som används för att allokera ett eller flera paket för kopian.</span><span class="sxs-lookup"><span data-stu-id="7d023-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="7d023-1459">**wait_option** Definierar hur tjänsten väntar om det inte finns några tillgängliga paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="7d023-1460">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1461">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1463">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1464">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1464">Return Values</span></span>
- <span data-ttu-id="7d023-1465">**NX_SUCCESS** (0x00) paket kopiering har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="7d023-1466">**NX_NO_PACKET** -paket (0x01) är inte tillgängligt för kopiering.</span><span class="sxs-lookup"><span data-stu-id="7d023-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="7d023-1467">**NX_INVALID_PACKET** (0X12) tomt käll paket eller kopia misslyckades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="7d023-1468">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-1469">**NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="7d023-1470">**NX_PTR_ERROR** (0X07) ogiltig pool, paket eller destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="7d023-1471">**NX_UNDERFLOW** (protokollnumret 0x02) ogiltig lägga pekare för paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="7d023-1472">**NX_OVERFLOW** (0X03) ogiltig paket tilläggs pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="7d023-1473">**NX_CALLER_ERROR** (0X11) ett wait-alternativ angavs i initiering eller i en ISR.</span><span class="sxs-lookup"><span data-stu-id="7d023-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1474">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1474">Allowed From</span></span>

<span data-ttu-id="7d023-1475">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="7d023-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1476">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1476">Preemption Possible</span></span>

<span data-ttu-id="7d023-1477">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1478">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1479">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1479">See Also</span></span>

- <span data-ttu-id="7d023-1480">nx_packet_allocate nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1481">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="7d023-1483">nx_packet_pool_info_get nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="7d023-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="7d023-1485">nx_packet_data_append</span></span>

<span data-ttu-id="7d023-1486">Lägg till data i slutet av paketet</span><span class="sxs-lookup"><span data-stu-id="7d023-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1487">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1488">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1488">Description</span></span>

<span data-ttu-id="7d023-1489">Den här tjänsten lägger till data i slutet av det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="7d023-1490">Det angivna data utrymmet kopieras till paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="7d023-1491">Om det inte finns tillräckligt med minne tillgängligt och funktionen länkat paket är aktive rad allokeras ett eller flera paket för att uppfylla begäran.</span><span class="sxs-lookup"><span data-stu-id="7d023-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="7d023-1492">Om funktionen för länkat paket inte är aktive rad returneras *NX_SIZE_ERROR* .</span><span class="sxs-lookup"><span data-stu-id="7d023-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1493">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1493">Parameters</span></span>

- <span data-ttu-id="7d023-1494">**packet_ptr** Paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="7d023-1495">**data_start** Pekar till början av användarens data områden som ska läggas till i paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="7d023-1496">**data_size** Storlek på användarens data områden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="7d023-1497">**pool_ptr** Pekare till Packet bassäng från vilken du vill allokera ett annat paket om det inte finns tillräckligt med utrymme i det aktuella paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="7d023-1498">**wait_option** Definierar hur tjänsten fungerar om det inte finns några tillgängliga paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="7d023-1499">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1500">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1502">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1503">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1503">Return Values</span></span>

- <span data-ttu-id="7d023-1504">**NX_SUCCESS** (0X00) slutfört paket tillägg.</span><span class="sxs-lookup"><span data-stu-id="7d023-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="7d023-1505">**NX_NO_PACKET** (0X01) inget paket tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="7d023-1506">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="7d023-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="7d023-1507">**NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="7d023-1508">**NX_UNDERFLOW** (protokollnumret 0x02) lägga-pekaren är mindre än start av nytto Last.</span><span class="sxs-lookup"><span data-stu-id="7d023-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="7d023-1509">**NX_OVERFLOW** (0X03) Lägg till-pekare är större än nytto Last slutet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="7d023-1510">**NX_PTR_ERROR** (0X07) ogiltig pool, paket eller data pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="7d023-1511">**NX_SIZE_ERROR** (0X09) ogiltig data storlek.</span><span class="sxs-lookup"><span data-stu-id="7d023-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="7d023-1512">**NX_CALLER_ERROR** (0X11) ogiltigt wait-alternativ från icke-tråd.</span><span class="sxs-lookup"><span data-stu-id="7d023-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1513">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1513">Allowed From</span></span>

<span data-ttu-id="7d023-1514">Initiering, trådar, timers och ISR: er (program nätverks driv rutiner)</span><span class="sxs-lookup"><span data-stu-id="7d023-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1515">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1515">Preemption Possible</span></span>

<span data-ttu-id="7d023-1516">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1517">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="7d023-1518">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1518">See Also</span></span>

- <span data-ttu-id="7d023-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span><span class="sxs-lookup"><span data-stu-id="7d023-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="7d023-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="7d023-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="7d023-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="7d023-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="7d023-1524">Extrahera data från paket via en förskjutning</span><span class="sxs-lookup"><span data-stu-id="7d023-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1525">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="7d023-1526">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1526">Description</span></span>

<span data-ttu-id="7d023-1527">Den här tjänsten kopierar data från ett NetX-paket (eller paket kedja) som börjar vid den angivna förskjutningen från paketets lägga-pekare i byte till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="7d023-1528">Antalet byte som faktiskt kopieras returneras i *bytes_copied.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="7d023-1529">Den här tjänsten tar inte bort data från paketet eller justerar inte lägga-pekaren eller annan information om internt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1530">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1530">Parameters</span></span>

- <span data-ttu-id="7d023-1531">**packet_ptr** Pekare till paket att extrahera</span><span class="sxs-lookup"><span data-stu-id="7d023-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="7d023-1532">**förskjutning** Offset från den aktuella lägga-pekaren.</span><span class="sxs-lookup"><span data-stu-id="7d023-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="7d023-1533">**buffer_start** Pekare till början av Spara buffert</span><span class="sxs-lookup"><span data-stu-id="7d023-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="7d023-1534">**buffer_length** Antal byte som ska kopieras</span><span class="sxs-lookup"><span data-stu-id="7d023-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="7d023-1535">**bytes_copied** Antal byte som faktiskt har kopierats</span><span class="sxs-lookup"><span data-stu-id="7d023-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1536">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1536">Return Values</span></span>

- <span data-ttu-id="7d023-1537">**NX_SUCCESS** (0x00) paket kopiering har slutförts</span><span class="sxs-lookup"><span data-stu-id="7d023-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="7d023-1538">**NX_PACKET_OFFSET_ERROR** (0X53) ogiltigt offset-värde angavs</span><span class="sxs-lookup"><span data-stu-id="7d023-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="7d023-1539">**NX_PTR_ERROR** (0X07) ogiltig paket pekare eller buffert pekare</span><span class="sxs-lookup"><span data-stu-id="7d023-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1540">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1540">Allowed From</span></span>

<span data-ttu-id="7d023-1541">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="7d023-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1542">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1542">Preemption Possible</span></span>

<span data-ttu-id="7d023-1543">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1544">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1545">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1545">See Also</span></span>

- <span data-ttu-id="7d023-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="7d023-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="7d023-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="7d023-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="7d023-1551">Hämta data från paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1552">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="7d023-1553">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1553">Description</span></span>

<span data-ttu-id="7d023-1554">Den här tjänsten kopierar data från det angivna paketet till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="7d023-1555">Det faktiska antalet kopierade byte returneras i målet som pekas av **bytes_copied**.</span><span class="sxs-lookup"><span data-stu-id="7d023-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="7d023-1556">Observera att den här tjänsten inte ändrar paketets interna tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="7d023-1557">De data som hämtas är fortfarande tillgängliga i paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="7d023-1558">*Måldomänkontrollanten måste vara tillräckligt stor för att rymma paketets innehåll. Om inte, kommer minnet att skadas orsaka oförutsägbara resultat.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1559">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1559">Parameters</span></span>

- <span data-ttu-id="7d023-1560">**packet_ptr** Pekare till käll paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="7d023-1561">**buffer_start** Pekar till början av mellanlagringsområdet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="7d023-1562">**bytes_copied** Pekar mot målet för antalet kopierade byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1563">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1563">Return Values</span></span>

- <span data-ttu-id="7d023-1564">**NX_SUCCESS** (0x00) paket data hämtades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="7d023-1565">**NX_INVALID_PACKET** (0X12) ogiltigt paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="7d023-1566">**NX_PTR_ERROR** (0X07) ogiltig paket, StartStart eller kopierade byte-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1567">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1567">Allowed From</span></span>

<span data-ttu-id="7d023-1568">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="7d023-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1569">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1569">Preemption Possible</span></span>

<span data-ttu-id="7d023-1570">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1571">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1572">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1572">See Also</span></span>

- <span data-ttu-id="7d023-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1574">nx_packet_data_extract_offset nx_packet_length_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="7d023-1575">nx_packet_pool_create nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="7d023-1576">nx_packet_pool_info_get nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="7d023-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1578">nx_packet_length_get</span></span>

<span data-ttu-id="7d023-1579">Hämta längd på paket data</span><span class="sxs-lookup"><span data-stu-id="7d023-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1580">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="7d023-1581">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1581">Description</span></span>

<span data-ttu-id="7d023-1582">Den här tjänsten hämtar längden på data i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1583">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1583">Parameters</span></span>

- <span data-ttu-id="7d023-1584">**packet_ptr** Pekare till paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="7d023-1585">**längd** Mål för paketets längd.</span><span class="sxs-lookup"><span data-stu-id="7d023-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1586">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1586">Allowed From</span></span>

<span data-ttu-id="7d023-1587">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="7d023-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1588">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1588">Preemption Possible</span></span>

<span data-ttu-id="7d023-1589">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1590">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1591">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1591">See Also</span></span>

- <span data-ttu-id="7d023-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1593">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1594">nx_packet_pool_create nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="7d023-1595">nx_packet_pool_info_get nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="7d023-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="7d023-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="7d023-1598">Skapa en modempool i angivet minnes området</span><span class="sxs-lookup"><span data-stu-id="7d023-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1599">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="7d023-1600">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1600">Description</span></span>

<span data-ttu-id="7d023-1601">Den här tjänsten skapar en adresspool av den angivna paket storleken i det minnes utrymme som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="7d023-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1602">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1602">Parameters</span></span>

- <span data-ttu-id="7d023-1603">**pool_ptr** Pekare till kontroll block för Packet-pool.</span><span class="sxs-lookup"><span data-stu-id="7d023-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="7d023-1604">**namn** Pekar till programmets namn för poolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="7d023-1605">**payload_size** Antal byte i varje paket i poolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="7d023-1606">Värdet måste vara minst 40 byte och måste också vara jämnt delbar med 4.</span><span class="sxs-lookup"><span data-stu-id="7d023-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="7d023-1607">**memory_ptr** Pekar på minnes området för att placera mediepoolen i.</span><span class="sxs-lookup"><span data-stu-id="7d023-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="7d023-1608">Pekaren ska vara justerad mot en ULONG-gränser.</span><span class="sxs-lookup"><span data-stu-id="7d023-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="7d023-1609">**memory_size** Storlek på poolens minnes området.</span><span class="sxs-lookup"><span data-stu-id="7d023-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1610">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1610">Return Values</span></span>

- <span data-ttu-id="7d023-1611">**NX_SUCCESS** (0x00) en paket bassäng har skapats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="7d023-1612">**NX_PTR_ERROR** (0X07) ogiltig pool eller minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="7d023-1613">**NX_SIZE_ERROR** (0X09) ogiltigt block eller minnes storlek.</span><span class="sxs-lookup"><span data-stu-id="7d023-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="7d023-1614">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1615">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1615">Allowed From</span></span>

<span data-ttu-id="7d023-1616">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1617">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1617">Preemption Possible</span></span>

<span data-ttu-id="7d023-1618">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1619">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1620">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1620">See Also</span></span>

- <span data-ttu-id="7d023-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1622">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="7d023-1624">nx_packet_release nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="7d023-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="7d023-1626">Ta bort tidigare skapade paket pool</span><span class="sxs-lookup"><span data-stu-id="7d023-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1627">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1628">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1628">Description</span></span>

<span data-ttu-id="7d023-1629">Den här tjänsten tar bort en tidigare skapad paket pool.</span><span class="sxs-lookup"><span data-stu-id="7d023-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="7d023-1630">NetX söker efter trådar som för närvarande är inaktiverade på paket i modempoolen och rensar uppskjutningen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1631">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1631">Parameters</span></span>

- <span data-ttu-id="7d023-1632">**pool_ptr** Pekare för kontroll block för Packet-pool.</span><span class="sxs-lookup"><span data-stu-id="7d023-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1633">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1633">Return Values</span></span>

- <span data-ttu-id="7d023-1634">**NX_SUCCESS** (0X00) lyckades ta bort paketets pool.</span><span class="sxs-lookup"><span data-stu-id="7d023-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="7d023-1635">**NX_PTR_ERROR** (0X07) ogiltig pool pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="7d023-1636">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1637">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1637">Allowed From</span></span>

<span data-ttu-id="7d023-1638">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1639">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1639">Preemption Possible</span></span>

<span data-ttu-id="7d023-1640">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1641">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1642">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1642">See Also</span></span>

- <span data-ttu-id="7d023-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1644">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1645">nx_packet_length_get nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="7d023-1646">nx_packet_pool_info_get nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="7d023-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="7d023-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="7d023-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="7d023-1649">Hämta information om en modempool</span><span class="sxs-lookup"><span data-stu-id="7d023-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1650">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="7d023-1651">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1651">Description</span></span>

<span data-ttu-id="7d023-1652">Den här tjänsten hämtar information om den angivna poolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="7d023-1653">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1654">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1654">Parameters</span></span>

- <span data-ttu-id="7d023-1655">**pool_ptr** Pekare till den tidigare skapade lagringspoolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="7d023-1656">**total_packets** Pekare till målet för det totala antalet paket i poolen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="7d023-1657">**free_packets** Pekare till målet för det totala antalet paket som för närvarande är kostnads fria.</span><span class="sxs-lookup"><span data-stu-id="7d023-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="7d023-1658">**empty_pool_requests** Pekare till målet för det totala antalet tilldelnings begär anden när poolen var tom.</span><span class="sxs-lookup"><span data-stu-id="7d023-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="7d023-1659">**empty_pool_suspensions** Pekare till målet för det totala antalet avstängningar av tomma pooler.</span><span class="sxs-lookup"><span data-stu-id="7d023-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="7d023-1660">**invalid_packet_releases** Pekare till målet för det totala antalet ogiltiga paket utgåvor.</span><span class="sxs-lookup"><span data-stu-id="7d023-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1661">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1661">Return Values</span></span>

- <span data-ttu-id="7d023-1662">**NX_SUCCESS** (0x00) information om hämtning av paket bassäng lyckades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="7d023-1663">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1664">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1665">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1665">Allowed From</span></span>

<span data-ttu-id="7d023-1666">Initiering, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="7d023-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1667">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1667">Preemption Possible</span></span>

<span data-ttu-id="7d023-1668">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1669">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1670">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1670">See Also</span></span>

- <span data-ttu-id="7d023-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1672">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1673">nx_packet_length_get nx_packet_pool_create nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="7d023-1674">nx_packet_release nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="7d023-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1675">nx_packet_release</span></span>

<span data-ttu-id="7d023-1676">Frigör tidigare allokerat paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1677">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1678">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1678">Description</span></span>

<span data-ttu-id="7d023-1679">Den här tjänsten frigör ett paket, inklusive eventuella ytterligare paket som är länkade till det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="7d023-1680">Om en annan tråd blockeras vid paket tilldelningen får den paketet och återupptas.</span><span class="sxs-lookup"><span data-stu-id="7d023-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="7d023-1681">*Programmet måste förhindra att ett paket släpps mer än en gång, eftersom detta kan orsaka oförutsägbara resultat.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1682">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1682">Parameters</span></span>

- <span data-ttu-id="7d023-1683">**packet_ptr** Paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-1684">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1684">Return Values</span></span>
- <span data-ttu-id="7d023-1685">**NX_SUCCESS** (0x00) paket versionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="7d023-1686">**NX_PTR_ERROR** (0X07) ogiltig paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="7d023-1687">**NX_UNDERFLOW** (protokollnumret 0x02) lägga-pekaren är mindre än start av nytto Last.</span><span class="sxs-lookup"><span data-stu-id="7d023-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="7d023-1688">**NX_OVERFLOW** (0X03) Lägg till-pekare är större än nytto Last slutet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1689">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1689">Allowed From</span></span>

<span data-ttu-id="7d023-1690">Initiering, trådar, timers och ISR: er (program nätverks driv rutiner)</span><span class="sxs-lookup"><span data-stu-id="7d023-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1691">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1691">Preemption Possible</span></span>

<span data-ttu-id="7d023-1692">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1693">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1694">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1694">See Also</span></span>

- <span data-ttu-id="7d023-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1696">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="7d023-1698">nx_packet_pool_info_get nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="7d023-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="7d023-1700">Frisläpp ett överfört paket</span><span class="sxs-lookup"><span data-stu-id="7d023-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1701">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1702">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1702">Description</span></span>

<span data-ttu-id="7d023-1703">För icke-TCP-paket släpper den här tjänsten ett överfört paket, inklusive eventuella ytterligare paket som är länkade till det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="7d023-1704">Om en annan tråd blockeras vid paket tilldelningen får den paketet och återupptas.</span><span class="sxs-lookup"><span data-stu-id="7d023-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="7d023-1705">För ett överfört TCP-paket markeras paketet som överfört, men släpps inte till paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="7d023-1706">Den här tjänsten kallas vanligt vis för programmets nätverks driv rutin när ett paket har överförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="7d023-1707">*Nätverks driv rutinen bör ta bort det fysiska medie huvudet och justera Paketets längd innan du anropar den här tjänsten.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1708">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1708">Parameters</span></span>

- <span data-ttu-id="7d023-1709">**packet_ptr** Paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1710">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1710">Return Values</span></span>

- <span data-ttu-id="7d023-1711">**NX_SUCCESS** (0x00) utgåva av överförings paket lyckades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="7d023-1712">**NX_PTR_ERROR** (0X07) ogiltig paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="7d023-1713">**NX_UNDERFLOW** (protokollnumret 0x02) lägga-pekaren är mindre än start av nytto Last.</span><span class="sxs-lookup"><span data-stu-id="7d023-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="7d023-1714">**NX_OVERFLOW** (0X03) Lägg till-pekare är större än nytto Last slutet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1715">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1715">Allowed From</span></span>

<span data-ttu-id="7d023-1716">Initiering, trådar, timers, program nätverks driv rutiner (inklusive ISR: er)</span><span class="sxs-lookup"><span data-stu-id="7d023-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1717">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1717">Preemption Possible</span></span>

<span data-ttu-id="7d023-1718">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1719">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1720">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1720">See Also</span></span>

- <span data-ttu-id="7d023-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="7d023-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="7d023-1722">nx_packet_data_extract_offset nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="7d023-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="7d023-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="7d023-1724">nx_packet_pool_info_get nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="7d023-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="7d023-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="7d023-1725">nx_rarp_disable</span></span>

<span data-ttu-id="7d023-1726">Inaktivera RARP (reverse Address Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="7d023-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1727">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1728">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1728">Description</span></span>

<span data-ttu-id="7d023-1729">Den här tjänsten inaktiverar RARP-komponenten för NetX för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="7d023-1730">För ett multihome-system inaktiverar den här tjänsten RARP på alla gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1731">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1731">Parameters</span></span>

- <span data-ttu-id="7d023-1732">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1733">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1733">Return Values</span></span>

- <span data-ttu-id="7d023-1734">**NX_SUCCESS** (0X00) RARP-inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="7d023-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="7d023-1735">**NX_NOT_ENABLED** (0X14) RARP har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="7d023-1736">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1737">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1738">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1738">Allowed From</span></span>

<span data-ttu-id="7d023-1739">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1740">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1740">Preemption Possible</span></span>

<span data-ttu-id="7d023-1741">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1742">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1743">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1743">See Also</span></span>

- <span data-ttu-id="7d023-1744">nx_rarp_enable nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="7d023-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-1745">nx_rarp_enable</span></span>

<span data-ttu-id="7d023-1746">Aktivera omvänt adress matchnings protokoll (RARP)</span><span class="sxs-lookup"><span data-stu-id="7d023-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1747">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1748">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1748">Description</span></span>

<span data-ttu-id="7d023-1749">Den här tjänsten aktiverar RARP-komponenten för NetX för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="7d023-1750">RARP-komponenterna söker igenom alla anslutna nätverks gränssnitt för noll IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="7d023-1751">En noll-IP-adress anger att gränssnittet inte har IP-adresstilldelning ännu.</span><span class="sxs-lookup"><span data-stu-id="7d023-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="7d023-1752">RARP försöker matcha IP-adressen genom att aktivera RARP-processen på det gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1753">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1753">Parameters</span></span>

- <span data-ttu-id="7d023-1754">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1755">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1755">Return Values</span></span>

- <span data-ttu-id="7d023-1756">**NX_SUCCESS** (0X00) RARP aktivera har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="7d023-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP-adressen är redan giltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="7d023-1758">**NX_ALREADY_ENABLED** (0X15) RARP har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="7d023-1759">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1760">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1761">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1761">Allowed From</span></span>

<span data-ttu-id="7d023-1762">Initiering, trådar, timers</span><span class="sxs-lookup"><span data-stu-id="7d023-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1763">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1763">Preemption Possible</span></span>

<span data-ttu-id="7d023-1764">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1765">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1766">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1766">See Also</span></span>

- <span data-ttu-id="7d023-1767">nx_rarp_disable nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="7d023-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="7d023-1769">Hämta information om RARP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1770">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="7d023-1771">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1771">Description</span></span>

<span data-ttu-id="7d023-1772">Den här tjänsten hämtar information om RARP-aktiviteter för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="7d023-1773">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1774">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1774">Parameters</span></span>

- <span data-ttu-id="7d023-1775">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1776">**rarp_requests_sent** Pekare till målet för det totala antalet RARP-begäranden som skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="7d023-1777">**rarp_responses_received** Pekare till målet för det totala antalet RARP-svar som tagits emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="7d023-1778">**rarp_invalid_messages** Pekare till målet för det totala antalet ogiltiga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="7d023-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-1779">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1779">Return Values</span></span>
- <span data-ttu-id="7d023-1780">**NX_SUCCESS** (0X00) lyckad RARP information hämtning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="7d023-1781">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1782">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-1783">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1784">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1784">Allowed From</span></span>

<span data-ttu-id="7d023-1785">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1786">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1786">Preemption Possible</span></span>

<span data-ttu-id="7d023-1787">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1788">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1789">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1789">See Also</span></span>

- <span data-ttu-id="7d023-1790">nx_rarp_disable nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="7d023-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="7d023-1791">nx_system_initialize</span></span>

<span data-ttu-id="7d023-1792">Initiera NetX-system</span><span class="sxs-lookup"><span data-stu-id="7d023-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1793">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="7d023-1794">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1794">Description</span></span>

<span data-ttu-id="7d023-1795">Den här tjänsten initierar de grundläggande NetX system resurserna som förberedelse för användning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="7d023-1796">Den ska anropas av programmet under initieringen och innan något annat NetX-anrop görs.</span><span class="sxs-lookup"><span data-stu-id="7d023-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1797">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1797">Parameters</span></span>

<span data-ttu-id="7d023-1798">Ingen</span><span class="sxs-lookup"><span data-stu-id="7d023-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1799">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1799">Return Values</span></span>

<span data-ttu-id="7d023-1800">Inget</span><span class="sxs-lookup"><span data-stu-id="7d023-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1801">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1801">Allowed From</span></span>

<span data-ttu-id="7d023-1802">Initiering, trådar, timers, ISR: er</span><span class="sxs-lookup"><span data-stu-id="7d023-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1803">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1803">Preemption Possible</span></span>

<span data-ttu-id="7d023-1804">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1805">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1806">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1806">See Also</span></span>

- <span data-ttu-id="7d023-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="7d023-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="7d023-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="7d023-1809">nx_ip_driver_interface_direct_command nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="7d023-1810">nx_ip_forwarding_enable nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="7d023-1811">nx_ip_fragment_enable nx_ip_info_get nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="7d023-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="7d023-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="7d023-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="7d023-1813">Bind klient TCP-socket till TCP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1814">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1815">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1815">Description</span></span>

<span data-ttu-id="7d023-1816">Den här tjänsten binder den tidigare skapade TCP-klientcachen till den angivna TCP-porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="7d023-1817">Giltiga TCP-Sockets sträcker sig från 0 till 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="7d023-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="7d023-1818">Om den angivna TCP-porten inte är tillgänglig pausas tjänsten enligt det angivna vänte alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1819">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1819">Parameters</span></span>

- <span data-ttu-id="7d023-1820">**socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="7d023-1821">**port** Port nummer att binda (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="7d023-1822">Om Port numret är NX_ANY_PORT (0x0000) kommer IP-instansen att söka efter nästa lediga port och använda den för bindningen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="7d023-1823">**wait_option** Definierar hur tjänsten beter sig om porten redan är kopplad till en annan socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="7d023-1824">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1825">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1827">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1828">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1828">Return Values</span></span>

- <span data-ttu-id="7d023-1829">**NX_SUCCESS** (0x00) socket-bindning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="7d023-1830">**NX_ALREADY_BOUND** (0X22) den här socketen är redan kopplad till en annan TCP-port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="7d023-1831">**NX_PORT_UNAVAILABLE** -porten (0x23) är redan kopplad till en annan socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="7d023-1832">**NX_NO_FREE_PORTS** (0X45) ingen kostnads fri port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="7d023-1833">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="7d023-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="7d023-1834">**NX_INVALID_PORT** (0X46) ogiltig port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="7d023-1835">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-1836">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1837">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1838">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1838">Allowed From</span></span>

<span data-ttu-id="7d023-1839">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1840">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1840">Preemption Possible</span></span>

<span data-ttu-id="7d023-1841">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1842">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1843">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1843">See Also</span></span>

- <span data-ttu-id="7d023-1844">nx_tcp_client_socket_connect nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="7d023-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="7d023-1846">nx_tcp_info_get nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-1847">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-1848">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-1849">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-1850">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-1851">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-1852">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="7d023-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="7d023-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="7d023-1855">Anslut klientens TCP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1856">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-1857">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1857">Description</span></span>

<span data-ttu-id="7d023-1858">Den här tjänsten ansluter den tidigare skapade och kopplade TCP-klientens socket till den angivna serverns port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="7d023-1859">Giltiga TCP server-portar är mellan 0 och 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="7d023-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="7d023-1860">Om anslutningen inte slutförs omedelbart pausas tjänsten enligt det angivna vänte alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1861">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1861">Parameters</span></span>

- <span data-ttu-id="7d023-1862">**socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="7d023-1863">**server_ip** Serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="7d023-1864">**SERVER_PORT** Server port nummer att ansluta till (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="7d023-1865">**wait_option** Definierar hur tjänsten fungerar när anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="7d023-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="7d023-1866">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-1867">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-1869">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1870">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1870">Return Values</span></span>

- <span data-ttu-id="7d023-1871">**NX_SUCCESS** (0x00) anslutningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="7d023-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="7d023-1872">**NX_NOT_BOUND** -socketen (0x24) är inte kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="7d023-1873">**NX_NOT_CLOSED** -socketen (0x35) är inte i ett stängt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="7d023-1874">**NX_IN_PROGRESS** (0X37) ingen väntan angavs, anslutnings försöket pågår.</span><span class="sxs-lookup"><span data-stu-id="7d023-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="7d023-1875">**NX_INVALID_INTERFACE** (0X4C) ogiltigt gränssnitt har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="7d023-1876">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-1877">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig Server-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="7d023-1878">**NX_INVALID_PORT** (0X46) ogiltig port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="7d023-1879">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-1880">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1881">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1882">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1882">Allowed From</span></span>

<span data-ttu-id="7d023-1883">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1884">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1884">Preemption Possible</span></span>

<span data-ttu-id="7d023-1885">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1886">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1887">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1887">See Also</span></span>

- <span data-ttu-id="7d023-1888">nx_tcp_client_socket_bind nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="7d023-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="7d023-1890">nx_tcp_info_get nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-1891">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-1892">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-1893">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-1894">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-1895">nx_tcp_socket_info_get nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d023-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7d023-1896">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="7d023-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="7d023-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="7d023-1899">Hämta port nummer kopplat till klienten TCP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1900">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1901">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1901">Description</span></span>

<span data-ttu-id="7d023-1902">Den här tjänsten hämtar det port nummer som är associerat med socketen, vilket är användbart för att hitta den port som allokerats av NetX i situationer där NX_ANY_PORT angavs vid den tidpunkt då socketen var kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1903">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1903">Parameters</span></span>

- <span data-ttu-id="7d023-1904">**socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="7d023-1905">**port_ptr** Pekare till målet för retur port numret.</span><span class="sxs-lookup"><span data-stu-id="7d023-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="7d023-1906">Giltiga port nummer är (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1907">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1907">Return Values</span></span>

- <span data-ttu-id="7d023-1908">**NX_SUCCESS** (0x00) socket-bindning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="7d023-1909">**NX_NOT_BOUND** (0X24) den här socketen är inte kopplad till någon port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="7d023-1910">**NX_PTR_ERROR** (0X07) ogiltig socket pekare eller port retur pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="7d023-1911">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1912">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1913">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1913">Allowed From</span></span>

<span data-ttu-id="7d023-1914">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1915">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1915">Preemption Possible</span></span>

<span data-ttu-id="7d023-1916">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1917">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1918">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1918">See Also</span></span>

- <span data-ttu-id="7d023-1919">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="7d023-1921">nx_tcp_info_get nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-1922">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-1923">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-1924">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-1925">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-1926">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-1927">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="7d023-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="7d023-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="7d023-1930">Bind TCP-klientens socket från TCP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1931">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1932">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1932">Description</span></span>

<span data-ttu-id="7d023-1933">Den här tjänsten frigör bindningen mellan TCP-klientens socket och en TCP-port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="7d023-1934">Om det finns andra trådar som väntar på att binda en annan socket till samma port nummer, binds den första pausade tråden till den här porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1935">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1935">Parameters</span></span>

- <span data-ttu-id="7d023-1936">**socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1937">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1937">Return Values</span></span>

- <span data-ttu-id="7d023-1938">**NX_SUCCESS** (0x00) uppkopplad socket-bindning.</span><span class="sxs-lookup"><span data-stu-id="7d023-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="7d023-1939">**NX_NOT_BOUND** -socketen var inte kopplad till någon port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="7d023-1940">**NX_NOT_CLOSED** -socketen (0x35) har inte kopplats från.</span><span class="sxs-lookup"><span data-stu-id="7d023-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="7d023-1941">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-1942">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-1943">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1944">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1944">Allowed From</span></span>

<span data-ttu-id="7d023-1945">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1946">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1946">Preemption Possible</span></span>

<span data-ttu-id="7d023-1947">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1948">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1949">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1949">See Also</span></span>

- <span data-ttu-id="7d023-1950">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="7d023-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="7d023-1952">nx_tcp_info_get nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-1953">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-1954">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-1955">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-1956">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-1957">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-1958">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="7d023-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-1960">nx_tcp_enable</span></span>

<span data-ttu-id="7d023-1961">Aktivera TCP-komponenten NetX</span><span class="sxs-lookup"><span data-stu-id="7d023-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1962">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1963">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1963">Description</span></span>

<span data-ttu-id="7d023-1964">Den här tjänsten aktiverar Transmission Control Protocol-komponenten (TCP) i NetX.</span><span class="sxs-lookup"><span data-stu-id="7d023-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="7d023-1965">När den har Aktiver ATS kan TCP-anslutningar upprättas av programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1966">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1966">Parameters</span></span>

- <span data-ttu-id="7d023-1967">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-1968">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-1968">Return Values</span></span>

- <span data-ttu-id="7d023-1969">**NX_SUCCESS** (0X00) TCP-aktivering har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="7d023-1970">**NX_ALREADY_ENABLED** (0X15) TCP har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="7d023-1971">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-1972">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-1973">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-1973">Allowed From</span></span>

<span data-ttu-id="7d023-1974">Initiering, trådar, timers</span><span class="sxs-lookup"><span data-stu-id="7d023-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-1975">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-1975">Preemption Possible</span></span>

<span data-ttu-id="7d023-1976">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-1977">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-1978">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-1978">See Also</span></span>

- <span data-ttu-id="7d023-1979">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-1980">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-1982">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-1983">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-1984">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-1985">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-1986">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-1987">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="7d023-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="7d023-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="7d023-1990">Hitta nästa tillgängliga TCP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-1991">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-1992">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-1992">Description</span></span>

<span data-ttu-id="7d023-1993">Den här tjänsten försöker hitta en kostnads fri TCP-port (obunden) med början från appens angivna port.</span><span class="sxs-lookup"><span data-stu-id="7d023-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="7d023-1994">Sök logiken kommer att figursättas runt om sökningen sker för att uppnå det högsta port svärdet för 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="7d023-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="7d023-1995">Om sökningen lyckas returneras den kostnads fria porten i variabeln som pekar på *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="7d023-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="7d023-1996">*Den här tjänsten kan anropas från en annan tråd och har samma port returnerad. För att förhindra det här konkurrens tillståndet kanske programmet vill placera den här tjänsten och det faktiska klient-socket-bindningen under skyddet av en mutex.*</span><span class="sxs-lookup"><span data-stu-id="7d023-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-1997">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-1997">Parameters</span></span>

- <span data-ttu-id="7d023-1998">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-1999">**port** Port nummer för att starta sökningen vid (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="7d023-2000">**free_port_ptr** Pekar till målets lediga port retur värde.</span><span class="sxs-lookup"><span data-stu-id="7d023-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2001">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2001">Return Values</span></span>

- <span data-ttu-id="7d023-2002">**NX_SUCCESS** (0x00) den kostnads fria porten hittades.</span><span class="sxs-lookup"><span data-stu-id="7d023-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="7d023-2003">**NX_NO_FREE_PORTS** (0X45) inga lediga portar hittades.</span><span class="sxs-lookup"><span data-stu-id="7d023-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="7d023-2004">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-2005">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2006">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-2007">**NX_INVALID_PORT** (0X46) det angivna port numret är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2008">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2008">Allowed From</span></span>

<span data-ttu-id="7d023-2009">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2010">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2010">Preemption Possible</span></span>

<span data-ttu-id="7d023-2011">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2012">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2013">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2013">See Also</span></span>

- <span data-ttu-id="7d023-2014">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2015">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-2017">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-2018">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-2019">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2020">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2021">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2022">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="7d023-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="7d023-2025">Hämta information om TCP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2026">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="7d023-2027">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2027">Description</span></span>

<span data-ttu-id="7d023-2028">Den här tjänsten hämtar information om TCP-aktiviteter för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="7d023-2029">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2030">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2030">Parameters</span></span>

- <span data-ttu-id="7d023-2031">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2032">**tcp_packets_sent** Pekare till målet för det totala antalet skickade TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="7d023-2033">**tcp_bytes_sent** Pekare till målet för det totala antalet TCP-byte som har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="7d023-2034">**tcp_packets_received** Pekare till målet för det totala antalet mottagna TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="7d023-2035">**tcp_bytes_received** Pekare till målet för det totala antalet mottagna TCP-byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="7d023-2036">**tcp_invalid_packets** Pekare till målet för det totala antalet ogiltiga TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="7d023-2037">**tcp_receive_packets_dropped** Pekare till målet för det totala antalet TCP-mottagna paket som har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="7d023-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="7d023-2038">**tcp_checksum_errors** Pekare till målet för det totala antalet TCP-paket med fel kontroll summor.</span><span class="sxs-lookup"><span data-stu-id="7d023-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="7d023-2039">**tcp_connections** Pekare till målet för det totala antalet TCP-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="7d023-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="7d023-2040">**tcp_disconnections** Pekare till målet för det totala antalet TCP-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="7d023-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="7d023-2041">**tcp_connections_dropped** Pekare till målet för det totala antalet avbrutna TCP-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="7d023-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="7d023-2042">**tcp_retransmit_packets** Pekare till målet för det totala antalet återsända TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2043">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2043">Return Values</span></span>

- <span data-ttu-id="7d023-2044">**NX_SUCCESS** (0X00) lyckad hämtning av TCP-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="7d023-2045">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-2046">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2047">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2048">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2048">Allowed From</span></span>

<span data-ttu-id="7d023-2049">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2050">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2050">Preemption Possible</span></span>

<span data-ttu-id="7d023-2051">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2052">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2053">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2053">See Also</span></span>

- <span data-ttu-id="7d023-2054">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2055">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-2057">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-2058">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-2059">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2060">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2061">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2062">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="7d023-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="7d023-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="7d023-2065">Acceptera TCP-anslutning</span><span class="sxs-lookup"><span data-stu-id="7d023-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2066">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-2067">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2067">Description</span></span>

<span data-ttu-id="7d023-2068">Den här tjänsten accepterar (eller förbereder att godkänna) en begäran om TCP-anslutning till Socket för en port som tidigare har kon figurer ATS för lyssning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="7d023-2069">Den här tjänsten kan anropas omedelbart när programmet anropar lyssnings-eller återlyssnar-tjänsten, eller efter att lyssnings rutinen för lyssning anropas när klient anslutningen faktiskt finns.</span><span class="sxs-lookup"><span data-stu-id="7d023-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="7d023-2070">Om en anslutning inte kan upprättas direkt, pausas tjänsten enligt det angivna vänte alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="7d023-2071">*Programmet måste anropa **nx_tcp_server_socket_unaccept** när anslutningen inte längre behövs för att ta bort Server socketens bindning till Server porten.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="7d023-2072">*Rutinen för återanrop av program anropas inifrån IP: s hjälp tråd.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2073">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2073">Parameters</span></span>

- <span data-ttu-id="7d023-2074">**socket_ptr** Pekar mot TCP-serverns socket Control-Block.</span><span class="sxs-lookup"><span data-stu-id="7d023-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="7d023-2075">**wait_option** Definierar hur tjänsten fungerar när anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="7d023-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="7d023-2076">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-2077">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-2079">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-2080">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2080">Return Values</span></span>
- <span data-ttu-id="7d023-2081">**NX_SUCCESS** (0X00) lyckad TCP-server-socket acceptera (passiv anslutning).</span><span class="sxs-lookup"><span data-stu-id="7d023-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="7d023-2082">**NX_NOT_LISTEN_STATE** (0X36) den angivna Server-socketen är inte i ett lyssnings tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="7d023-2083">**NX_IN_PROGRESS** (0X37) ingen väntan angavs, anslutnings försöket pågår.</span><span class="sxs-lookup"><span data-stu-id="7d023-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="7d023-2084">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="7d023-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="7d023-2085">**NX_PTR_ERROR** (0X07) socket Point-fel.</span><span class="sxs-lookup"><span data-stu-id="7d023-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="7d023-2086">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2087">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2088">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2088">Allowed From</span></span>

<span data-ttu-id="7d023-2089">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2090">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2090">Preemption Possible</span></span>

<span data-ttu-id="7d023-2091">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2092">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="7d023-2093">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2093">See Also</span></span>

- <span data-ttu-id="7d023-2094">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2095">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2097">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-2098">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-2099">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2100">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2101">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2102">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="7d023-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="7d023-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="7d023-2105">Aktivera lyssning för klient anslutning på TCP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="7d023-2107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2107">Description</span></span>

<span data-ttu-id="7d023-2108">Med den här tjänsten kan du lyssna efter en klient anslutnings förfrågan på den angivna TCP-porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="7d023-2109">När en begäran om klient anslutning tas emot binds den angivna Server sockeln till den angivna porten och den angivna funktionen för lyssnings motringning anropas.</span><span class="sxs-lookup"><span data-stu-id="7d023-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="7d023-2110">Bearbetningen av lyssnings rutinen för lyssning är helt upp i programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="7d023-2111">Den kan innehålla logik för att väcka en program tråd som sedan utför en acceptera-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="7d023-2112">Om programmet redan har en tråd inaktive rad för accepterad bearbetning för den här socketen kanske inte rutinen för lyssnings anrop behövs.</span><span class="sxs-lookup"><span data-stu-id="7d023-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="7d023-2113">Om programmet vill hantera ytterligare klient anslutningar på samma port måste ***nx_tcp_server_socket_relisten*** anropas med en tillgänglig socket (en socket i stängt tillstånd) för nästa anslutning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="7d023-2114">Ytterligare klient anslutningar köas tills tjänsten relistener anropas.</span><span class="sxs-lookup"><span data-stu-id="7d023-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="7d023-2115">När det maximala ködjup överskrids, släpps den äldsta anslutningsbegäran i stället för att köa den nya anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="7d023-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="7d023-2116">Det maximala ködjup anges av den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="7d023-2117">*Rutinen för återanrop av program anropas från den interna IP-hjälpen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2118">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2118">Parameters</span></span>

- <span data-ttu-id="7d023-2119">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2120">**port** Port nummer att lyssna på (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="7d023-2121">**socket_ptr** Pekare till Socket som ska användas för anslutningen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="7d023-2122">**listen_queue_size** Antal klient anslutnings begär Anden som kan köas.</span><span class="sxs-lookup"><span data-stu-id="7d023-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="7d023-2123">**listen_callback** Program funktion som anropas när anslutningen tas emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="7d023-2124">Om du anger ett NULL-värde är funktionen lyssnande motringning inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2125">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2125">Return Values</span></span>

- <span data-ttu-id="7d023-2126">**NX_SUCCESS** (0X00) lyckade TCP-ports lyssning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="7d023-2127">**NX_MAX_LISTEN** (0X33) inga fler lyssnar begär ande strukturer är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="7d023-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="7d023-2128">Konstanten NX_MAX_LISTEN_REQUESTS i nx_api. h definierar hur många aktiva lyssnings begär Anden som är möjliga.</span><span class="sxs-lookup"><span data-stu-id="7d023-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="7d023-2129">**NX_NOT_CLOSED** (0X35) den angivna Server socketen är inte i ett stängt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="7d023-2130">**NX_ALREADY_BOUND** (0X22) den angivna Server socketen är redan kopplad till en port.</span><span class="sxs-lookup"><span data-stu-id="7d023-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="7d023-2131">**NX_DUPLICATE_LISTEN** (0X34) det finns redan en aktiv avlyssnings förfrågan för den här porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="7d023-2132">**NX_INVALID_PORT** (0X46) ogiltig Port har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="7d023-2133">**NX_PTR_ERROR** (0X07) ogiltig IP-eller socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="7d023-2134">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2135">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2136">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2136">Allowed From</span></span>

<span data-ttu-id="7d023-2137">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2138">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2138">Preemption Possible</span></span>

<span data-ttu-id="7d023-2139">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2140">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="7d023-2141">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2141">See Also</span></span>

- <span data-ttu-id="7d023-2142">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2143">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2145">nx_tcp_server_socket_accept nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-2146">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-2147">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2148">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2149">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2150">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="7d023-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="7d023-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="7d023-2153">Lyssna efter klient anslutning på TCP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-2155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2155">Description</span></span>

<span data-ttu-id="7d023-2156">Den här tjänsten anropas efter att en anslutning har tagits emot på en port som tidigare har kon figurer ATS för lyssning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="7d023-2157">Huvud syftet med den här tjänsten är att tillhandahålla en ny server-socket för nästa klient anslutning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="7d023-2158">Om en anslutningsbegäran är i kö kommer anslutningen att bearbetas omedelbart under det här tjänst anropet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="7d023-2159">*Samma återanrops rutin som anges av den ursprungliga lyssnar förfrågan kallas även när det finns en anslutning för denna nya server-socket.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2160">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2160">Parameters</span></span>

- <span data-ttu-id="7d023-2161">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2162">**port** Port nummer att lyssna på igen (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="7d023-2163">**socket_ptr** Socket som ska användas för nästa klient anslutning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2164">Return Values</span></span>
- <span data-ttu-id="7d023-2165">**NX_SUCCESS** (0X00) lyckade TCP-port-lyssna igen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="7d023-2166">**NX_NOT_CLOSED** (0X35) den angivna Server socketen är inte i ett stängt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="7d023-2167">**NX_ALREADY_BOUND** (0X22) den angivna Server socketen är redan kopplad till en port.</span><span class="sxs-lookup"><span data-stu-id="7d023-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="7d023-2168">**NX_INVALID_RELISTEN** (0X47) det finns redan en giltig socket-pekare för den här porten, eller så har den angivna porten ingen avlyssnings förfrågan aktiv.</span><span class="sxs-lookup"><span data-stu-id="7d023-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="7d023-2169">**NX_CONNECTION_PENDING** (0X48) samma som NX_SUCCESS, förutom att det fanns en köade anslutningsbegäran och bearbetades under det här anropet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="7d023-2170">**NX_INVALID_PORT** (0X46) ogiltig Port har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="7d023-2171">**NX_PTR_ERROR** (0X07) ogiltig IP-eller lyssnande återanrops pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="7d023-2172">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2173">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2174">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2174">Allowed From</span></span>

<span data-ttu-id="7d023-2175">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2176">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2176">Preemption Possible</span></span>

<span data-ttu-id="7d023-2177">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2178">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="7d023-2179">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2179">See Also</span></span>

- <span data-ttu-id="7d023-2180">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2181">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2183">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2184">nx_tcp_server_socket_unaccept nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="7d023-2185">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2186">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2187">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2188">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="7d023-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="7d023-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="7d023-2191">Ta bort socket-associationen med lyssnings porten</span><span class="sxs-lookup"><span data-stu-id="7d023-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-2193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2193">Description</span></span>

<span data-ttu-id="7d023-2194">Den här tjänsten tar bort associationen mellan denna server-socket och den angivna Server porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="7d023-2195">Programmet måste anropa tjänsten efter en från koppling eller efter ett misslyckat accept-anrop.</span><span class="sxs-lookup"><span data-stu-id="7d023-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2196">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2196">Parameters</span></span>

- <span data-ttu-id="7d023-2197">**socket_ptr** Pekare till tidigare konfigurerad server-socket-instans.</span><span class="sxs-lookup"><span data-stu-id="7d023-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2198">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2198">Return Values</span></span>

- <span data-ttu-id="7d023-2199">**NX_SUCCESS** (0X00) lyckad Server-socket accepterades inte.</span><span class="sxs-lookup"><span data-stu-id="7d023-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="7d023-2200">**NX_NOT_LISTEN_STATE** (0x36)-serverns socket är i ett felaktigt tillstånd och är förmodligen inte frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="7d023-2201">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2202">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2203">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2204">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2204">Allowed From</span></span>

<span data-ttu-id="7d023-2205">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2206">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2206">Preemption Possible</span></span>

<span data-ttu-id="7d023-2207">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2208">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="7d023-2209">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2209">See Also</span></span>

- <span data-ttu-id="7d023-2210">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="7d023-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="7d023-2213">nx_tcp_server_socket_listen nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="7d023-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="7d023-2214">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2216">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2217">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="7d023-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="7d023-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="7d023-2220">Inaktivera lyssning för klient anslutning på TCP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2221">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="7d023-2222">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2222">Description</span></span>

<span data-ttu-id="7d023-2223">Den här tjänsten inaktiverar avlyssningen av en klient anslutnings förfrågan på den angivna TCP-porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2224">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2224">Parameters</span></span>

- <span data-ttu-id="7d023-2225">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2226">**port** Antal portar för att inaktivera lyssning (0 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2227">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2227">Return Values</span></span>

- <span data-ttu-id="7d023-2228">**NX_SUCCESS** (0X00) TCP-lyssning har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="7d023-2229">Lyssning för **NX_ENTRY_NOT_FOUND** (0x16) har inte Aktiver ATS för den angivna porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="7d023-2230">**NX_INVALID_PORT** (0X46) ogiltig Port har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="7d023-2231">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-2232">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2233">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2234">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2234">Allowed From</span></span>

<span data-ttu-id="7d023-2235">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2236">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2236">Preemption Possible</span></span>

<span data-ttu-id="7d023-2237">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2238">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="7d023-2239">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2239">See Also</span></span>

- <span data-ttu-id="7d023-2240">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2241">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2243">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2244">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2245">nx_tcp_socket_bytes_available nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2246">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2247">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2248">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="7d023-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="7d023-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="7d023-2251">Hämtar antalet byte som är tillgängliga för hämtning</span><span class="sxs-lookup"><span data-stu-id="7d023-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2252">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="7d023-2253">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2253">Description</span></span>

<span data-ttu-id="7d023-2254">Den här tjänsten hämtar antalet byte som är tillgängliga för hämtning i den angivna TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="7d023-2255">Observera att TCP-socketen måste vara ansluten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2256">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2256">Parameters</span></span>

- <span data-ttu-id="7d023-2257">**socket_ptr** Pekare till tidigare skapad och ansluten TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="7d023-2258">**bytes_available** Pekare till målet för tillgängliga byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2259">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2259">Return Values</span></span>

- <span data-ttu-id="7d023-2260">Tjänsten **NX_SUCCESS** (0x00) har körts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="7d023-2261">Antalet byte som är tillgängliga för läsning returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="7d023-2262">**NX_NOT_CONNECTED** -socketen (0x38) är inte i ett anslutet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="7d023-2263">**NX_PTR_ERROR** (0X07) ogiltiga pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="7d023-2264">**NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="7d023-2265">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2266">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2266">Allowed From</span></span>

<span data-ttu-id="7d023-2267">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2268">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2268">Preemption Possible</span></span>

<span data-ttu-id="7d023-2269">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2270">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2271">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2271">See Also</span></span>

- <span data-ttu-id="7d023-2272">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2273">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2275">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2276">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2277">nx_tcp_server_socket_unlisten nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2278">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2279">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2280">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="7d023-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="7d023-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="7d023-2283">Skapa TCP-klient eller Server-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2284">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-2285">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2285">Description</span></span>

<span data-ttu-id="7d023-2286">Den här tjänsten skapar en TCP-klient eller Server-socket för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="7d023-2287">*Rutinen för återanrop av program anropas från tråden som är kopplad till den här IP-instansen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2288">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2288">Parameters</span></span>

- <span data-ttu-id="7d023-2289">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2290">**socket_ptr** Pekare till nytt TCP socket Control-Block.</span><span class="sxs-lookup"><span data-stu-id="7d023-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="7d023-2291">**namn** Programmets namn för denna TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="7d023-2292">**type_of_service** Definierar typ av tjänst för överföringen, de juridiska värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="7d023-2293">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="7d023-2294">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="7d023-2295">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="7d023-2296">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="7d023-2297">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="7d023-2298">**fragment**  Anger om IP-fragmentering tillåts eller inte.</span><span class="sxs-lookup"><span data-stu-id="7d023-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="7d023-2299">Om NX_FRAGMENT_OKAY (0x0) anges tillåts IP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="7d023-2300">Om NX_DONT_FRAGMENT (0x4000) anges inaktive ras IP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="7d023-2301">**time_to_live** Anger det 8-bitars värde som definierar hur många routrar det här paketet kan passera innan det utlöses.</span><span class="sxs-lookup"><span data-stu-id="7d023-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="7d023-2302">Standardvärdet anges av NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="7d023-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="7d023-2303">**window_size** Definierar det maximala antalet byte som tillåts i mottagnings kön för denna socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="7d023-2304">**urgent_data_callback** Programfunktion som anropas när brådskande data identifieras i Receive-dataströmmen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="7d023-2305">Om det här värdet är NX_NULL ignoreras brådskande data.</span><span class="sxs-lookup"><span data-stu-id="7d023-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="7d023-2306">**disconnect_callback** Program funktion som anropas när en från koppling utfärdas av socketen i den andra änden av anslutningen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="7d023-2307">Om det här värdet är NX_NULL inaktive ras funktionen för motringning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2308">Return Values</span></span>
- <span data-ttu-id="7d023-2309">**NX_SUCCESS** (0X00) TCP-klient-socket har skapats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="7d023-2310">**NX_OPTION_ERROR** (0X0a) ogiltigt alternativ för typ av tjänst, fragment, ogiltig fönster storlek eller tid tolive.</span><span class="sxs-lookup"><span data-stu-id="7d023-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="7d023-2311">**NX_PTR_ERROR** (0X07) ogiltig IP-eller socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="7d023-2312">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2313">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2314">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2314">Allowed From</span></span>

<span data-ttu-id="7d023-2315">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2316">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2316">Preemption Possible</span></span>

<span data-ttu-id="7d023-2317">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2318">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2319">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2319">See Also</span></span>

- <span data-ttu-id="7d023-2320">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2321">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2323">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2324">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2325">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2326">nx_tcp_socket_delete nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2327">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2328">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="7d023-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="7d023-2331">Ta bort TCP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2332">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-2333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2333">Description</span></span>

<span data-ttu-id="7d023-2334">Den här tjänsten tar bort en tidigare skapad TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="7d023-2335">Om socketen fortfarande är bunden eller ansluten, returnerar tjänsten en felkod.</span><span class="sxs-lookup"><span data-stu-id="7d023-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2336">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2336">Parameters</span></span>

- <span data-ttu-id="7d023-2337">**socket_ptr** TCP-socket har skapats tidigare</span><span class="sxs-lookup"><span data-stu-id="7d023-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2338">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2338">Return Values</span></span>

- <span data-ttu-id="7d023-2339">**NX_SUCCESS** (0x00) ta bort socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="7d023-2340">Det gick inte att skapa **NX_NOT_CREATED** (0X27) socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="7d023-2341">**NX_STILL_BOUND** (0X42) socket är fortfarande kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="7d023-2342">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2343">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2344">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2345">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2345">Allowed From</span></span>

<span data-ttu-id="7d023-2346">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2347">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2347">Preemption Possible</span></span>

<span data-ttu-id="7d023-2348">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2349">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2350">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2350">See Also</span></span>

- <span data-ttu-id="7d023-2351">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2352">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2354">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2355">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2356">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2357">nx_tcp_socket_create nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2358">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2359">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="7d023-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="7d023-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="7d023-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="7d023-2362">Koppla från klient-och Server anslutningar</span><span class="sxs-lookup"><span data-stu-id="7d023-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2363">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-2364">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2364">Description</span></span>

<span data-ttu-id="7d023-2365">Den här tjänsten kopplar från en upprättad klient eller Server-socket-anslutning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="7d023-2366">En från koppling av en server-socket bör följas av en begäran om att ta emot begäran, medan en klient-socket som är frånkopplad är kvar i ett tillstånd som är redo för en annan anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="7d023-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="7d023-2367">Om från kopplings processen inte kan slutföras omedelbart pausas tjänsten enligt det angivna vänte alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2368">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2368">Parameters</span></span>

- <span data-ttu-id="7d023-2369">**socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="7d023-2370">**wait_option** Definierar hur tjänsten fungerar när från koppling pågår.</span><span class="sxs-lookup"><span data-stu-id="7d023-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="7d023-2371">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-2372">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-2374">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2375">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2375">Return Values</span></span>

- <span data-ttu-id="7d023-2376">**NX_SUCCESS** (0X00) lyckades socket från kopplingen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="7d023-2377">**NX_NOT_CONNECTED** (0x38) den angivna socketen är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="7d023-2378">**NX_IN_PROGRESS** (0x37) från koppling pågår, ingen väntan har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="7d023-2379">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-2380">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2381">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2382">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2383">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2383">Allowed From</span></span>

<span data-ttu-id="7d023-2384">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2385">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2385">Preemption Possible</span></span>

<span data-ttu-id="7d023-2386">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2387">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2388">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2388">See Also</span></span>

- <span data-ttu-id="7d023-2389">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2390">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2392">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2393">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2394">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-2396">nx_tcp_socket_receive nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="7d023-2397">nx_tcp_socket_send nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="7d023-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="7d023-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="7d023-2399">Installera TCP från koppling Slutför meddela motringning</span><span class="sxs-lookup"><span data-stu-id="7d023-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2400">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-2401">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2401">Description</span></span>

<span data-ttu-id="7d023-2402">Den här tjänsten registrerar en callback-funktion som anropas när en socket-från koppling har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="7d023-2403">Callback-funktionen för att koppla från TCP socket är tillgänglig om NetX har skapats med alternativet</span><span class="sxs-lookup"><span data-stu-id="7d023-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="7d023-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definierats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2405">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2405">Parameters</span></span>

- <span data-ttu-id="7d023-2406">**socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="7d023-2407">**tcp_disconnect_complete_notify** Motringningsfunktionen som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="7d023-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2408">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2408">Return Values</span></span>
- <span data-ttu-id="7d023-2409">**NX_SUCCESS** (0x00) registrerade återanrops funktionen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="7d023-2410">**NX_NOT_SUPPORTED** (0x4B) funktionen för utökad avisering är inte inbyggd i netx-biblioteket</span><span class="sxs-lookup"><span data-stu-id="7d023-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="7d023-2411">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2412">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2413">**NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2414">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2414">Allowed From</span></span>

<span data-ttu-id="7d023-2415">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2416">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2416">Preemption Possible</span></span>

<span data-ttu-id="7d023-2417">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2418">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="7d023-2419">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2419">See Also</span></span>

- <span data-ttu-id="7d023-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="7d023-2421">nx_tcp_socket_mss_get nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="7d023-2422">nx_tcp_socket_mss_set nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="7d023-2423">nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2424">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="7d023-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="7d023-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="7d023-2427">Ange TCP-upprättning av funktionen meddela motringning</span><span class="sxs-lookup"><span data-stu-id="7d023-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2428">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-2429">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2429">Description</span></span>

<span data-ttu-id="7d023-2430">Den här tjänsten registrerar en callback-funktion som anropas när en TCP-socket upprättar en anslutning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="7d023-2431">TCP-socketen för att skapa en motringning är tillgänglig om NetX har skapats med alternativet ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definierat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2432">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2432">Parameters</span></span>

- <span data-ttu-id="7d023-2433">**socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="7d023-2434">**tcp_establish_notify** Callback-funktionen anropas efter att en TCP-anslutning har upprättats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2435">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2435">Return Values</span></span>

- <span data-ttu-id="7d023-2436">**NX_SUCCESS** (0X00) har angett funktionen notify.</span><span class="sxs-lookup"><span data-stu-id="7d023-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="7d023-2437">**NX_NOT_SUPPORTED** (0x4B) funktionen för utökad avisering är inte inbyggd i netx-biblioteket</span><span class="sxs-lookup"><span data-stu-id="7d023-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="7d023-2438">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2439">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2440">**NX_NOT_ENABLED** (0X14) TCP har inte Aktiver ATS av programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2441">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2441">Allowed From</span></span>

<span data-ttu-id="7d023-2442">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2443">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2443">Preemption Possible</span></span>

<span data-ttu-id="7d023-2444">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2445">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="7d023-2446">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2446">See Also</span></span>

- <span data-ttu-id="7d023-2447">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2448">nx_tcp_socket_disconnect_complete_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2449">nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="7d023-2450">nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-2451">nx_tcp_socket_timed_wait_callback nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="7d023-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="7d023-2454">Hämta information om TCP-socket-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2455">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="7d023-2456">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2456">Description</span></span>

<span data-ttu-id="7d023-2457">Den här tjänsten hämtar information om TCP-socket-aktiviteter för den angivna TCP socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="7d023-2458">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2459">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2459">Parameters</span></span>

- <span data-ttu-id="7d023-2460">**socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="7d023-2461">**tcp_packets_sent** Pekare till målet för det totala antalet TCP-paket som skickats på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="7d023-2462">**tcp_bytes_sent** Pekare till målet för det totala antalet TCP-byte som skickats på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="7d023-2463">**tcp_packets_received** Pekare till målet för det totala antalet TCP-paket som tagits emot på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="7d023-2464">**tcp_bytes_received** Pekare till målet för det totala antalet TCP-byte som tagits emot vid socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="7d023-2465">**tcp_retransmit_packets** Pekare till målet för det totala antalet återöverföringar av TCP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="7d023-2466">**tcp_packets_queued** Pekare till målet för det totala antalet köade TCP-paket på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="7d023-2467">**tcp_checksum_errors** Pekare till målet för det totala antalet TCP-paket med fel kontroll summor på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="7d023-2468">**tcp_socket_state** Pekare till målet för socketens aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="7d023-2469">**tcp_transmit_queue_depth** Pekare till målet för det totala antalet överförings paket som fortfarande står i kö i väntan på bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="7d023-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="7d023-2470">**tcp_transmit_window** Pekare till målet för den aktuella överförings fönster storleken.</span><span class="sxs-lookup"><span data-stu-id="7d023-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="7d023-2471">**tcp_receive_window** Pekare till målet för den aktuella storleken för mottagnings fönster.</span><span class="sxs-lookup"><span data-stu-id="7d023-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2472">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2472">Return Values</span></span>

- <span data-ttu-id="7d023-2473">**NX_SUCCESS** (0X00) lyckades Hämta TCP-socket-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="7d023-2474">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2475">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2476">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2477">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="7d023-2478">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2478">Allowed From</span></span>

<span data-ttu-id="7d023-2479">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2480">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2480">Preemption Possible</span></span>

<span data-ttu-id="7d023-2481">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2482">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2483">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2483">See Also</span></span>

- <span data-ttu-id="7d023-2484">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2485">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2487">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2488">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2489">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2491">nx_tcp_socket_receive nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="7d023-2492">nx_tcp_socket_send nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="7d023-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="7d023-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="7d023-2494">Hämta MSS för socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2495">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="7d023-2496">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2496">Description</span></span>

<span data-ttu-id="7d023-2497">Den här tjänsten hämtar den angivna socketens lokala maximala segment storlek (MSS).</span><span class="sxs-lookup"><span data-stu-id="7d023-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2498">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2498">Parameters</span></span>

- <span data-ttu-id="7d023-2499">**socket_ptr** Pekare till den tidigare skapade socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="7d023-2500">**MSS** Mål för returnerad MSS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2501">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2501">Return Values</span></span>

- <span data-ttu-id="7d023-2502">**NX_SUCCESS** (0X00) godkänd MSS Hämta.</span><span class="sxs-lookup"><span data-stu-id="7d023-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="7d023-2503">**NX_PTR_ERROR** (0X07) ogiltig mål pekare för socket eller MSS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="7d023-2504">**NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="7d023-2505">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2506">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2506">Allowed From</span></span>

<span data-ttu-id="7d023-2507">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2508">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2508">Preemption Possible</span></span>

<span data-ttu-id="7d023-2509">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2510">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2511">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2511">See Also</span></span>

- <span data-ttu-id="7d023-2512">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2513">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2514">nx_tcp_socket_establish_notify nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="7d023-2515">nx_tcp_socket_mss_set nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="7d023-2516">nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2517">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="7d023-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="7d023-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="7d023-2520">Hämta MSS för peer TCP-socketen</span><span class="sxs-lookup"><span data-stu-id="7d023-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2521">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="7d023-2522">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2522">Description</span></span>

<span data-ttu-id="7d023-2523">Den här tjänsten hämtar den maximala segment storleken (MSS) som annonseras av peer-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2524">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2524">Parameters</span></span>

- <span data-ttu-id="7d023-2525">**socket_ptr** Pekare till tidigare skapad och ansluten socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="7d023-2526">**MSS** Mål för att returnera MSS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-2527">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2527">Return Values</span></span>

- <span data-ttu-id="7d023-2528">**NX_SUCCESS** (0X00) lyckad peer-MSS Hämta.</span><span class="sxs-lookup"><span data-stu-id="7d023-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="7d023-2529">**NX_PTR_ERROR** (0X07) ogiltig mål pekare för socket eller MSS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="7d023-2530">**NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="7d023-2531">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2532">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2532">Allowed From</span></span>

<span data-ttu-id="7d023-2533">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2534">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2534">Preemption Possible</span></span>

<span data-ttu-id="7d023-2535">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2536">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2537">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2537">See Also</span></span>

- <span data-ttu-id="7d023-2538">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2539">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2540">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2541">nx_tcp_socket_mss_set nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="7d023-2542">nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2543">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="7d023-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="7d023-2546">Ange MSS för socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2547">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="7d023-2548">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2548">Description</span></span>

<span data-ttu-id="7d023-2549">Den här tjänsten anger den angivna socketens största segment storlek (MSS).</span><span class="sxs-lookup"><span data-stu-id="7d023-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="7d023-2550">Observera att MSS-värdet måste ligga inom nätverks gränssnittets IP-MTU, vilket ger utrymme för IP-och TCP-huvuden.</span><span class="sxs-lookup"><span data-stu-id="7d023-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="7d023-2551">Den här tjänsten ska användas innan en TCP-socket startar anslutnings processen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="7d023-2552">Om tjänsten används när en TCP-anslutning har upprättats har det nya värdet ingen påverkan på anslutningen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2553">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2553">Parameters</span></span>

- <span data-ttu-id="7d023-2554">**socket_ptr** Pekare till den tidigare skapade socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="7d023-2555">**MSS** Värdet för MSS som ska anges.</span><span class="sxs-lookup"><span data-stu-id="7d023-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2556">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2556">Return Values</span></span>

- <span data-ttu-id="7d023-2557">**NX_SUCCESS** (0X00) godkänd MSS-uppsättning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="7d023-2558">Det angivna MSS-värdet för **NX_SIZE_ERROR** (0x09) är för stort.</span><span class="sxs-lookup"><span data-stu-id="7d023-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="7d023-2559">**NX_NOT_CONNECTED** (0X38) TCP-anslutning har inte upprättats</span><span class="sxs-lookup"><span data-stu-id="7d023-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="7d023-2560">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2561">**NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="7d023-2562">**NX_CALLER_ERROR** (0X11) anroparen är inte en tråd eller initiering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2563">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2563">Allowed From</span></span>

<span data-ttu-id="7d023-2564">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2565">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2565">Preemption Possible</span></span>

<span data-ttu-id="7d023-2566">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2567">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2568">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2568">See Also</span></span>

- <span data-ttu-id="7d023-2569">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2570">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2571">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2572">nx_tcp_socket_mss_peer_get nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="7d023-2573">nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2574">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="7d023-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="7d023-2577">Hämta information om peer TCP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2578">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="7d023-2579">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2579">Description</span></span>

<span data-ttu-id="7d023-2580">Den här tjänsten hämtar information om peer-IP-adress och port för den anslutna TCP-socketen över IP-nätverket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2581">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2581">Parameters</span></span>

- <span data-ttu-id="7d023-2582">**socket_ptr** Pekare till den tidigare skapade TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="7d023-2583">**peer_ip_address** Pekare till mål för peer-IP-adress i byte ordning för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="7d023-2584">**peer_port** Pekar till mål för peer-portnummer i byte ordning för värden.</span><span class="sxs-lookup"><span data-stu-id="7d023-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2585">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2585">Return Values</span></span>

- <span data-ttu-id="7d023-2586">Tjänsten **NX_SUCCESS** (0x00) har körts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="7d023-2587">Peer-IP-adress och port nummer returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="7d023-2588">**NX_NOT_CONNECTED** -socketen (0x38) är inte i ett anslutet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="7d023-2589">**NX_PTR_ERROR** (0X07) ogiltiga pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="7d023-2590">**NX_NOT_ENABLED** (0X14) TCP är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="7d023-2591">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2592">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2592">Allowed From</span></span>

<span data-ttu-id="7d023-2593">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2594">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2594">Preemption Possible</span></span>

<span data-ttu-id="7d023-2595">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2596">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2597">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2597">See Also</span></span>

- <span data-ttu-id="7d023-2598">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2599">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2600">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2601">nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="7d023-2602">nx_tcp_socket_receive_notify nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2603">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="7d023-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d023-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="7d023-2606">Ta emot data från TCP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2607">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-2608">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2608">Description</span></span>

<span data-ttu-id="7d023-2609">Den här tjänsten tar emot TCP-data från den angivna socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="7d023-2610">Om inga data har placerats i kö på den angivna socketen, pausas anroparen utifrån det angivna wait-alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="7d023-2611">*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2612">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2612">Parameters</span></span>

- <span data-ttu-id="7d023-2613">**socket_ptr** Pekare till den tidigare skapade TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="7d023-2614">**packet_ptr** Pekare till TCP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="7d023-2615">**wait_option** Definierar hur tjänsten beter sig om inga data är köade på denna socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="7d023-2616">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-2617">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-2619">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2620">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2620">Return Values</span></span>
- <span data-ttu-id="7d023-2621">**NX_SUCCESS** (0X00) lyckades ta emot socket-data.</span><span class="sxs-lookup"><span data-stu-id="7d023-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="7d023-2622">**NX_NOT_BOUND** (0x24)-socketen är inte kopplad än.</span><span class="sxs-lookup"><span data-stu-id="7d023-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="7d023-2623">**NX_NO_PACKET** (0X01) inga data togs emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7d023-2624">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-2625">**NX_NOT_CONNECTED** (0x38) socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="7d023-2626">**NX_PTR_ERROR** (0X07) ogiltig socket eller RETUR paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="7d023-2627">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2628">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2629">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2629">Allowed From</span></span>

<span data-ttu-id="7d023-2630">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2631">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2631">Preemption Possible</span></span>

<span data-ttu-id="7d023-2632">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2633">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2633">Example</span></span>

<span data-ttu-id="7d023-2634">/\* Ta emot ett paket från den tidigare skapade och anslutna TCP-klientens socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="7d023-2635">Om det inte finns något paket tillgängligt väntar du tills 200 timer-Tick innan du får upp.</span><span class="sxs-lookup"><span data-stu-id="7d023-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="7d023-2636">\*/status = nx_tcp_socket_receive (&client_socket &packet_ptr 200);</span><span class="sxs-lookup"><span data-stu-id="7d023-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="7d023-2637">/\* Om status är NX_SUCCESS kommer det mottagna paketet att pekas av "packet_ptr".</span><span class="sxs-lookup"><span data-stu-id="7d023-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="7d023-2638">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2638">See Also</span></span>

- <span data-ttu-id="7d023-2639">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2640">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2642">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2643">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2644">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2646">nx_tcp_socket_info_get nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="7d023-2647">nx_tcp_socket_send nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="7d023-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="7d023-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="7d023-2649">Meddela program om mottagna paket</span><span class="sxs-lookup"><span data-stu-id="7d023-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="7d023-2650">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-2651">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2651">Description</span></span>

<span data-ttu-id="7d023-2652">Den här tjänsten konfigurerar funktionen ta emot aviserings funktion med återanrops funktionen som anges av programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="7d023-2653">Den här återanrops funktionen anropas sedan när ett eller flera paket tas emot på socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="7d023-2654">Om en NX_NULL-pekare har angetts inaktive ras funktionen notify.</span><span class="sxs-lookup"><span data-stu-id="7d023-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2655">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2655">Parameters</span></span>

- <span data-ttu-id="7d023-2656">**socket_ptr** Pekare till TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="7d023-2657">**tcp_receive_notify** Funktionen motringning till program som anropas när ett eller flera paket tas emot på socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2658">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2658">Return Values</span></span>

- <span data-ttu-id="7d023-2659">**NX_SUCCESS** (0X00) lyckad socket Receive-avisering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="7d023-2660">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2661">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2662">**NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2663">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2663">Allowed From</span></span>

<span data-ttu-id="7d023-2664">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2665">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2665">Preemption Possible</span></span>

<span data-ttu-id="7d023-2666">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2667">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2668">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2668">See Also</span></span>

- <span data-ttu-id="7d023-2669">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2670">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2671">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2672">nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="7d023-2673">nx_tcp_socket_peer_info_get nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2674">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="7d023-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="7d023-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="7d023-2677">Skicka data via en TCP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2678">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-2679">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2679">Description</span></span>

<span data-ttu-id="7d023-2680">Den här tjänsten skickar TCP-data via en tidigare ansluten TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="7d023-2681">Om mottagarens senaste annonserade fönster storlek är mindre än den här begäran, så pausas tjänsten om den inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="7d023-2682">Den här tjänsten garanterar att inga paket data som är större än MSS skickas till IP-skiktet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="7d023-2683">*Om ett fel returneras ska programmet inte släppa paketet efter det här anropet. Om du gör det kan det orsaka oförutsägbara resultat, eftersom nätverks driv rutinen även försöker frigöra paketet efter överföringen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2684">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2684">Parameters</span></span>

- <span data-ttu-id="7d023-2685">**socket_ptr** Pekare till den tidigare anslutna TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="7d023-2686">**packet_ptr** TCP data paket pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="7d023-2687">**wait_option** Definierar hur tjänsten fungerar om begäran är större än mottagarens fönster storlek.</span><span class="sxs-lookup"><span data-stu-id="7d023-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="7d023-2688">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-2689">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-2691">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2692">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2692">Return Values</span></span>

- <span data-ttu-id="7d023-2693">**NX_SUCCESS** (0x00) skickade socket-sändning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="7d023-2694">**NX_NOT_BOUND** -socketen var inte kopplad till någon port.</span><span class="sxs-lookup"><span data-stu-id="7d023-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="7d023-2695">**NX_NO_INTERFACE_ADDRESS** (0X50) inget lämpligt utgående gränssnitt hittades.</span><span class="sxs-lookup"><span data-stu-id="7d023-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="7d023-2696">**NX_NOT_CONNECTED** -socketen (0x38) är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="7d023-2697">**NX_WINDOW_OVERFLOW** -begäran (0x39) är större än mottagarens annonserade fönster storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="7d023-2698">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-2699">**NX_INVALID_PACKET** -paketet (0x12) har inte allokerats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="7d023-2700">**NX_TX_QUEUE_DEPTH** (0X49) högsta tillåtna djup för överförings kön har uppnåtts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="7d023-2701">**NX_OVERFLOW** (0X03) paket tilläggs pekare är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="7d023-2702">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2703">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2704">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-2705">**NX_UNDERFLOW** (protokollnumret 0x02) paket lägga pekare är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="7d023-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2706">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2706">Allowed From</span></span>

<span data-ttu-id="7d023-2707">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2708">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2708">Preemption Possible</span></span>

<span data-ttu-id="7d023-2709">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2710">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2711">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2711">See Also</span></span>

- <span data-ttu-id="7d023-2712">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2713">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2715">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2716">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2717">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2719">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2720">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="7d023-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="7d023-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="7d023-2722">Vänta tills TCP-socketen har angett ett angivet tillstånd</span><span class="sxs-lookup"><span data-stu-id="7d023-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2723">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="7d023-2724">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2724">Description</span></span>

<span data-ttu-id="7d023-2725">Den här tjänsten väntar på att socketen ska ange önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="7d023-2726">Om socketen inte har önskat tillstånd pausas tjänsten enligt det angivna wait-alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2727">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2727">Parameters</span></span>

- <span data-ttu-id="7d023-2728">**socket_ptr** Pekare till den tidigare anslutna TCP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="7d023-2729">**desired_state** Önskat TCP-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7d023-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="7d023-2730">Giltiga TCP-socket-tillstånd definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="7d023-2731">NX_TCP_CLOSED (0x01)</span><span class="sxs-lookup"><span data-stu-id="7d023-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="7d023-2732">NX_TCP_LISTEN_STATE (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="7d023-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="7d023-2733">NX_TCP_SYN_SENT (0x03)</span><span class="sxs-lookup"><span data-stu-id="7d023-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="7d023-2734">NX_TCP_SYN_RECEIVED (0x04)</span><span class="sxs-lookup"><span data-stu-id="7d023-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="7d023-2735">NX_TCP_ESTABLISHED (0x05)</span><span class="sxs-lookup"><span data-stu-id="7d023-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="7d023-2736">NX_TCP_CLOSE_WAIT (0x06)</span><span class="sxs-lookup"><span data-stu-id="7d023-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="7d023-2737">NX_TCP_FIN_WAIT_1 (0x07)</span><span class="sxs-lookup"><span data-stu-id="7d023-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="7d023-2738">NX_TCP_FIN_WAIT_2 (0x08)</span><span class="sxs-lookup"><span data-stu-id="7d023-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="7d023-2739">NX_TCP_CLOSING (0x09)</span><span class="sxs-lookup"><span data-stu-id="7d023-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="7d023-2740">NX_TCP_TIMED_WAIT (0x0A)</span><span class="sxs-lookup"><span data-stu-id="7d023-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="7d023-2741">NX_TCP_LAST_ACK (0x0B)</span><span class="sxs-lookup"><span data-stu-id="7d023-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="7d023-2742">**wait_option** Definierar hur tjänsten fungerar om det begärda läget inte finns.</span><span class="sxs-lookup"><span data-stu-id="7d023-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="7d023-2743">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-2744">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-2746">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2747">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2747">Return Values</span></span>
- <span data-ttu-id="7d023-2748">**NX_SUCCESS** (0x00) tillstånd väntar.</span><span class="sxs-lookup"><span data-stu-id="7d023-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="7d023-2749">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2750">**NX_NOT_SUCCESSFUL** (0X43) status finns inte inom angiven vänte tid.</span><span class="sxs-lookup"><span data-stu-id="7d023-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="7d023-2751">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-2752">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2753">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-2754">**NX_OPTION_ERROR** (0X0a) det önskade socket-läget är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2755">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2755">Allowed From</span></span>

<span data-ttu-id="7d023-2756">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2757">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2757">Preemption Possible</span></span>

<span data-ttu-id="7d023-2758">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2759">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2760">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2760">See Also</span></span>

- <span data-ttu-id="7d023-2761">nx_tcp_client_socket_bind nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="7d023-2762">nx_tcp_client_socket_port_get nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="7d023-2764">nx_tcp_server_socket_accept nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="7d023-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="7d023-2765">nx_tcp_server_socket_relisten nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="7d023-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="7d023-2766">nx_tcp_server_socket_unlisten nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="7d023-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="7d023-2768">nx_tcp_socket_info_get nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2769">nx_tcp_socket_receive_queue_max_set nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="7d023-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="7d023-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="7d023-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="7d023-2771">Installera motringning för vänte läge med vänte tid</span><span class="sxs-lookup"><span data-stu-id="7d023-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2772">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-2773">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2773">Description</span></span>

<span data-ttu-id="7d023-2774">Den här tjänsten registrerar en callback-funktion som anropas när TCP-socketen är i vänte läge.</span><span class="sxs-lookup"><span data-stu-id="7d023-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="7d023-2775">Om du vill använda den här tjänsten måste NetX-biblioteket skapas med alternativet ***NX_ENABLE_EXTENDED_NOTIFY*** definierat.</span><span class="sxs-lookup"><span data-stu-id="7d023-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2776">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2776">Parameters</span></span>

- <span data-ttu-id="7d023-2777">**socket_ptr** Pekare till den tidigare anslutna klienten eller Server-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="7d023-2778">**tcp_timed_wait_callback** Funktionen vänte tid för motringning</span><span class="sxs-lookup"><span data-stu-id="7d023-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2779">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2779">Return Values</span></span>

- <span data-ttu-id="7d023-2780">**NX_SUCCESS** (0x00) registrerar återanrops funktionens socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="7d023-2781">**NX_NOT_SUPPORTED** (0X4B) netx-biblioteket har skapats utan den utökade meddelande funktionen aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="7d023-2782">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2783">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2784">**NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2785">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2785">Allowed From</span></span>

<span data-ttu-id="7d023-2786">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2787">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2787">Preemption Possible</span></span>

<span data-ttu-id="7d023-2788">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2789">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="7d023-2790">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2790">See Also</span></span>

- <span data-ttu-id="7d023-2791">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2792">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2793">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2794">nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="7d023-2795">nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-2796">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="7d023-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="7d023-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="7d023-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="7d023-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="7d023-2799">Konfigurera överförings parametrar för socket</span><span class="sxs-lookup"><span data-stu-id="7d023-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2800">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="7d023-2801">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2801">Description</span></span>

<span data-ttu-id="7d023-2802">Den här tjänsten konfigurerar olika överförings parametrar för den angivna TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2803">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2803">Parameters</span></span>

- <span data-ttu-id="7d023-2804">**socket_ptr** Pekare till TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="7d023-2805">**max_queue_depth** Högsta antal paket som får placeras i kö för överföring.</span><span class="sxs-lookup"><span data-stu-id="7d023-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="7d023-2806">**tids gräns** Antal ThreadX timer-Tick som en ACK väntar innan paketet skickas igen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="7d023-2807">**max_retries** Maximalt antal tillåtna försök.</span><span class="sxs-lookup"><span data-stu-id="7d023-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="7d023-2808">**timeout_shift** Värde för att skifta tids gränsen för varje efterföljande försök.</span><span class="sxs-lookup"><span data-stu-id="7d023-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="7d023-2809">Värdet 0, resulterar i samma tids gräns mellan efterföljande försök.</span><span class="sxs-lookup"><span data-stu-id="7d023-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="7d023-2810">Värdet 1, dubblar tids gränsen mellan återförsök.</span><span class="sxs-lookup"><span data-stu-id="7d023-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2811">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2811">Return Values</span></span>
- <span data-ttu-id="7d023-2812">**NX_SUCCESS** (0x00) konfiguration av överförings-socket har slutförts.</span><span class="sxs-lookup"><span data-stu-id="7d023-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="7d023-2813">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-2814">**NX_OPTION_ERROR** (0X0a) ogiltigt ködjup-alternativ.</span><span class="sxs-lookup"><span data-stu-id="7d023-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="7d023-2815">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2816">**NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2817">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2817">Allowed From</span></span>

<span data-ttu-id="7d023-2818">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2819">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2819">Preemption Possible</span></span>

<span data-ttu-id="7d023-2820">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2821">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2822">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2822">See Also</span></span>

- <span data-ttu-id="7d023-2823">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2824">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2825">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2826">nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="7d023-2827">nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-2828">nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="7d023-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="7d023-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="7d023-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="7d023-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="7d023-2831">Meddela programmet om uppdateringar av fönster storlek</span><span class="sxs-lookup"><span data-stu-id="7d023-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2832">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-2833">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2833">Description</span></span>

<span data-ttu-id="7d023-2834">Den här tjänsten installerar ett socket-fönster uppdatera motringning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="7d023-2835">Den här rutinen anropas automatiskt när den angivna socketen tar emot ett paket som anger en ökning av fönster storleken för fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="7d023-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2836">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2836">Parameters</span></span>

- <span data-ttu-id="7d023-2837">**socket_ptr** Pekare till den tidigare skapade TCP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="7d023-2838">**tcp_window_update_notify** Callback-rutin som anropas när fönstrets storlek ändras.</span><span class="sxs-lookup"><span data-stu-id="7d023-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="7d023-2839">Värdet NULL inaktiverar uppdatering av fönster ändringar.</span><span class="sxs-lookup"><span data-stu-id="7d023-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2840">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2840">Return Values</span></span>
- <span data-ttu-id="7d023-2841">**NX_SUCCESS** (0x00) återanrops rutinen är installerad på socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="7d023-2842">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2843">**NX_PTR_ERROR** (0X07) ogiltiga pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="7d023-2844">**NX_NOT_ENABLED** (0X14) TCP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="7d023-2845">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2845">Allowed From</span></span>

<span data-ttu-id="7d023-2846">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2847">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2847">Preemption Possible</span></span>

<span data-ttu-id="7d023-2848">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2849">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="7d023-2850">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2850">See Also</span></span>

- <span data-ttu-id="7d023-2851">nx_tcp_enable nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="7d023-2852">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="7d023-2853">nx_tcp_socket_establish_notify nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="7d023-2854">nx_tcp_socket_mss_peer_get nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="7d023-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="7d023-2855">nx_tcp_socket_peer_info_get nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-2856">nx_tcp_socket_timed_wait_callback nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="7d023-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="7d023-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-2857">nx_udp_enable</span></span>

<span data-ttu-id="7d023-2858">Aktivera UDP-komponenten för NetX</span><span class="sxs-lookup"><span data-stu-id="7d023-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2859">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-2860">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2860">Description</span></span>

<span data-ttu-id="7d023-2861">Den här tjänsten aktiverar UDP-komponenten (User Datagram Protocol) i NetX.</span><span class="sxs-lookup"><span data-stu-id="7d023-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="7d023-2862">När den har Aktiver ATS kan UDP-datagram skickas och tas emot av programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2863">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2863">Parameters</span></span>

- <span data-ttu-id="7d023-2864">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2865">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2865">Return Values</span></span>

- <span data-ttu-id="7d023-2866">**NX_SUCCESS** (0X00) lyckad UDP-aktivering.</span><span class="sxs-lookup"><span data-stu-id="7d023-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="7d023-2867">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-2868">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2869">**NX_ALREADY_ENABLED** (0X15) den här komponenten har redan Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2870">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2870">Allowed From</span></span>

<span data-ttu-id="7d023-2871">Initiering, trådar, timers</span><span class="sxs-lookup"><span data-stu-id="7d023-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2872">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2872">Preemption Possible</span></span>

<span data-ttu-id="7d023-2873">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2874">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2875">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2875">See Also</span></span>

- <span data-ttu-id="7d023-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="7d023-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="7d023-2877">nx_udp_socket_bind nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2878">nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="7d023-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-2880">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2881">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-2882">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="7d023-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="7d023-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="7d023-2885">Hitta nästa tillgängliga UDP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2886">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-2887">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2887">Description</span></span>

<span data-ttu-id="7d023-2888">Den här tjänsten söker efter en kostnads fri UDP-port (obunden) med början från det angivna port numret för programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="7d023-2889">Sök logiken kommer att figursättas runt om sökningen når det högsta port svärdet för 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="7d023-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="7d023-2890">Om sökningen lyckas returneras den kostnads fria porten i variabeln som pekar på *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="7d023-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="7d023-2891">*Den här tjänsten kan anropas från en annan tråd och kan ha samma port som returneras. För att förhindra det här konkurrens tillståndet kanske programmet vill placera den här tjänsten och faktiskt socket-bindning under skyddet av en mutex.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2892">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2892">Parameters</span></span>

- <span data-ttu-id="7d023-2893">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2894">**port** Port nummer för att starta sökning (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="7d023-2895">**free_port_ptr** Pekar på den lediga portens retur variabel.</span><span class="sxs-lookup"><span data-stu-id="7d023-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="7d023-2896">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2896">Return Values</span></span>

- <span data-ttu-id="7d023-2897">**NX_SUCCESS** (0x00) den kostnads fria porten hittades.</span><span class="sxs-lookup"><span data-stu-id="7d023-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="7d023-2898">**NX_NO_FREE_PORTS** (0X45) inga lediga portar hittades.</span><span class="sxs-lookup"><span data-stu-id="7d023-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="7d023-2899">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-2900">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2901">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="7d023-2902">**NX_INVALID_PORT** (0x46) det angivna port numret är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2903">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2903">Allowed From</span></span>

<span data-ttu-id="7d023-2904">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2905">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2905">Preemption Possible</span></span>

<span data-ttu-id="7d023-2906">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2907">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2908">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2908">See Also</span></span>

- <span data-ttu-id="7d023-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="7d023-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="7d023-2910">nx_udp_socket_bind nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2911">nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="7d023-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-2913">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2914">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-2915">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="7d023-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-2917">nx_udp_info_get</span></span>

<span data-ttu-id="7d023-2918">Hämta information om UDP-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2919">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="7d023-2920">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2920">Description</span></span>

<span data-ttu-id="7d023-2921">Den här tjänsten hämtar information om UDP-aktiviteter för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="7d023-2922">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2923">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2923">Parameters</span></span>

- <span data-ttu-id="7d023-2924">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-2925">**udp_packets_sent** Pekare till målet för det totala antalet skickade UDP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="7d023-2926">**udp_bytes_sent** Pekare till målet för det totala antalet UDP-byte som har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="7d023-2927">**udp_packets_received** Pekare till målet för det totala antalet mottagna UDP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="7d023-2928">**udp_bytes_received** Pekare till målet för det totala antalet mottagna UDP-byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="7d023-2929">**udp_invalid_packets** Pekare till målet för det totala antalet ogiltiga UDP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="7d023-2930">**udp_receive_packets_dropped** Pekare till målet för det totala antalet mottagna UDP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="7d023-2931">**udp_checksum_errors** Pekare till målet för det totala antalet UDP-paket med fel kontroll summor.</span><span class="sxs-lookup"><span data-stu-id="7d023-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2932">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2932">Return Values</span></span>

- <span data-ttu-id="7d023-2933">**NX_SUCCESS** (0X00) lyckades hämtning av UDP-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="7d023-2934">**NX_PTR_ERROR** (0X07) ogiltig IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="7d023-2935">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-2936">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="7d023-2937">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2937">Allowed From</span></span>

<span data-ttu-id="7d023-2938">Initiering, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="7d023-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2939">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2939">Preemption Possible</span></span>

<span data-ttu-id="7d023-2940">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2941">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2942">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2942">See Also</span></span>

- <span data-ttu-id="7d023-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="7d023-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="7d023-2944">nx_udp_socket_bind nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2945">nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="7d023-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-2947">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2948">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-2949">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="7d023-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="7d023-2952">Extrahera nätverks parametrar från UDP-paket</span><span class="sxs-lookup"><span data-stu-id="7d023-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2953">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="7d023-2954">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2954">Description</span></span>

<span data-ttu-id="7d023-2955">Den här tjänsten extraherar nätverks parametrar, till exempel IP-adress, peer-portnummer, protokoll typ (den här tjänsten returnerar alltid UDP-typ) från ett paket som tas emot i ett inkommande gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2956">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2956">Parameters</span></span>

- <span data-ttu-id="7d023-2957">**packet_ptr** Pekar mot paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="7d023-2958">**ip_address** Pekare till avsändar-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="7d023-2959">**protokoll** Pekare till protokoll (UDP).</span><span class="sxs-lookup"><span data-stu-id="7d023-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="7d023-2960">**port** Pekare till avsändarens port nummer.</span><span class="sxs-lookup"><span data-stu-id="7d023-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="7d023-2961">**interface_index** Pekare för att ta emot gränssnitts index.</span><span class="sxs-lookup"><span data-stu-id="7d023-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2962">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2962">Return Values</span></span>

- <span data-ttu-id="7d023-2963">**NX_SUCCESS** (0X00) paket gränssnitts data har extraherats.</span><span class="sxs-lookup"><span data-stu-id="7d023-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="7d023-2964">**NX_INVALID_PACKET** -paketet (0x12) innehåller inte någon IP-ram.</span><span class="sxs-lookup"><span data-stu-id="7d023-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="7d023-2965">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="7d023-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="7d023-2966">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-2967">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-2967">Allowed From</span></span>

<span data-ttu-id="7d023-2968">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-2969">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-2969">Preemption Possible</span></span>

<span data-ttu-id="7d023-2970">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-2971">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-2972">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-2972">See Also</span></span>

- <span data-ttu-id="7d023-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-2974">nx_udp_socket_bind nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-2975">nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="7d023-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-2977">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-2978">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-2979">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="7d023-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="7d023-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="7d023-2982">Bind UDP-socket till UDP-port</span><span class="sxs-lookup"><span data-stu-id="7d023-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-2983">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-2984">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-2984">Description</span></span>

<span data-ttu-id="7d023-2985">Den här tjänsten binder den tidigare skapade UDP-socketen till den angivna UDP-porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="7d023-2986">Giltiga UDP-socketar sträcker sig från 0 till 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="7d023-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="7d023-2987">Om det begärda port numret är kopplat till en annan socket, väntar den här tjänsten på den angivna tids perioden för att socketen ska kunna bindas från Port numret.</span><span class="sxs-lookup"><span data-stu-id="7d023-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-2988">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-2988">Parameters</span></span>

- <span data-ttu-id="7d023-2989">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="7d023-2990">**port** Port nummer att binda till (1 till 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="7d023-2991">Om Port numret är NX_ANY_PORT (0x0000) kommer IP-instansen att söka efter nästa lediga port och använda den för bindningen.</span><span class="sxs-lookup"><span data-stu-id="7d023-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="7d023-2992">**wait_option** Definierar hur tjänsten beter sig om porten redan är kopplad till en annan socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="7d023-2993">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-2994">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-2996">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-2997">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-2997">Return Values</span></span>

- <span data-ttu-id="7d023-2998">**NX_SUCCESS** (0x00) socket-bindning.</span><span class="sxs-lookup"><span data-stu-id="7d023-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="7d023-2999">**NX_ALREADY_BOUND** (0X22) den här socketen är redan kopplad till en annan port.</span><span class="sxs-lookup"><span data-stu-id="7d023-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="7d023-3000">**NX_PORT_UNAVAILABLE** -porten (0x23) är redan kopplad till en annan socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="7d023-3001">**NX_NO_FREE_PORTS** (0X45) ingen kostnads fri port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="7d023-3002">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="7d023-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="7d023-3003">**NX_INVALID_PORT** (0X46) ogiltig Port har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d023-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="7d023-3004">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-3005">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3006">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3007">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3007">Allowed From</span></span>

<span data-ttu-id="7d023-3008">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3009">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3009">Preemption Possible</span></span>

<span data-ttu-id="7d023-3010">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3011">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-3012">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3012">See Also</span></span>

- <span data-ttu-id="7d023-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3014">nx_udp_packet_info_extract nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="7d023-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="7d023-3015">nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="7d023-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3017">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3018">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3019">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="7d023-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="7d023-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="7d023-3022">Hämtar antalet byte som är tillgängliga för hämtning</span><span class="sxs-lookup"><span data-stu-id="7d023-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3023">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="7d023-3024">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3024">Description</span></span>

<span data-ttu-id="7d023-3025">Den här tjänsten hämtar antalet byte som är tillgängliga för mottagning i den angivna UDP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3026">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3026">Parameters</span></span>

- <span data-ttu-id="7d023-3027">**socket_ptr** Pekare till den tidigare skapade UDP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="7d023-3028">**bytes_available** Pekare till målet för tillgängliga byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3029">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3029">Return Values</span></span>

- <span data-ttu-id="7d023-3030">**NX_SUCCESS** (0x00) hämtade bytes tillgängliga byte.</span><span class="sxs-lookup"><span data-stu-id="7d023-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="7d023-3031">**NX_NOT_SUCCESSFUL** -socketen (0x43) är inte kopplad till en port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="7d023-3032">**NX_PTR_ERROR** (0X07) ogiltiga pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="7d023-3033">**NX_NOT_ENABLED** (0X14) UDP-funktionen är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="7d023-3034">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3035">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3035">Allowed From</span></span>

<span data-ttu-id="7d023-3036">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3037">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3037">Preemption Possible</span></span>

<span data-ttu-id="7d023-3038">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3039">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-3040">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3040">See Also</span></span>

- <span data-ttu-id="7d023-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3042">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3043">nx_udp_socket_checksum_disable nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="7d023-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3045">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3046">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3047">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="7d023-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="7d023-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="7d023-3050">Inaktivera kontroll summa för UDP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3051">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-3052">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3052">Description</span></span>

<span data-ttu-id="7d023-3053">Den här tjänsten inaktiverar kontroll summan för att skicka och ta emot paket på den angivna UDP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="7d023-3054">När logiken för kontroll summa är inaktive rad läses värdet noll in i UDP-huvudets fält för kontroll summa för alla paket som skickas via denna socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="7d023-3055">Ett värde för en kontroll summa med noll värde i UDP-huvudet signalerar mottagaren om att kontroll summan inte har beräknats för det här paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="7d023-3056">Observera också att detta inte har någon inverkan om ***NX_DISABLE_UDP_RX_CHECKSUM** _ och _ *_NX_DISABLE_UDP_TX_CHECKSUM_** definieras när du tar emot och skickar UDP-paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3057">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3057">Parameters</span></span>

- <span data-ttu-id="7d023-3058">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3059">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3059">Return Values</span></span>

- <span data-ttu-id="7d023-3060">**NX_SUCCESS** (0x00) inaktive ring av kontroll summa.</span><span class="sxs-lookup"><span data-stu-id="7d023-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="7d023-3061">**NX_NOT_BOUND** -socketen (0x24) är inte kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="7d023-3062">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-3063">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3064">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3065">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3065">Allowed From</span></span>

<span data-ttu-id="7d023-3066">Initiering, trådar, timer</span><span class="sxs-lookup"><span data-stu-id="7d023-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3067">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3067">Preemption Possible</span></span>

<span data-ttu-id="7d023-3068">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3069">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3070">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3070">See Also</span></span>

- <span data-ttu-id="7d023-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3072">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3073">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3075">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3076">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3077">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="7d023-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="7d023-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="7d023-3080">Aktivera kontroll summa för UDP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3081">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-3082">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3082">Description</span></span>

<span data-ttu-id="7d023-3083">Den här tjänsten aktiverar den logiska kontroll summan för att skicka och ta emot paket på den angivna UDP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="7d023-3084">Kontroll summan täcker hela UDP-dataområdet samt ett IP-huvud för pseudo.</span><span class="sxs-lookup"><span data-stu-id="7d023-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="7d023-3085">Observera också att detta inte har någon påverkan om **NX_DISABLE_UDP_RX_CHECKSUM** och **NX_DISABLE_UDP_TX_CHECKSUM** definieras när UDP-paket tas emot och skickas.</span><span class="sxs-lookup"><span data-stu-id="7d023-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3086">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3086">Parameters</span></span>

- <span data-ttu-id="7d023-3087">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3088">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3088">Return Values</span></span>

- <span data-ttu-id="7d023-3089">**NX_SUCCESS** (0x00) Enabled-kontroll Summa aktivera.</span><span class="sxs-lookup"><span data-stu-id="7d023-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="7d023-3090">**NX_NOT_BOUND** -socketen (0x24) är inte kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="7d023-3091">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-3092">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3093">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3094">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3094">Allowed From</span></span>

<span data-ttu-id="7d023-3095">Initiering, trådar, timer</span><span class="sxs-lookup"><span data-stu-id="7d023-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3096">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3096">Preemption Possible</span></span>

<span data-ttu-id="7d023-3097">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3098">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3099">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3099">See Also</span></span>

- <span data-ttu-id="7d023-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3101">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3102">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3104">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3105">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3106">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="7d023-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="7d023-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="7d023-3109">Skapa UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3110">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="7d023-3111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3111">Description</span></span>

<span data-ttu-id="7d023-3112">Den här tjänsten skapar en UDP-socket för den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3113">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3113">Parameters</span></span>

- <span data-ttu-id="7d023-3114">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7d023-3115">**socket_ptr** Pekar på ny Bloc för UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="7d023-3116">**namn** Program namn för denna UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="7d023-3117">**type_of_service** Definierar typ av tjänst för överföringen, de juridiska värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="7d023-3118">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="7d023-3119">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="7d023-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="7d023-3120">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="7d023-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="7d023-3121">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="7d023-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="7d023-3122">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="7d023-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="7d023-3123">**fragment** Anger om IP-fragmentering tillåts eller inte.</span><span class="sxs-lookup"><span data-stu-id="7d023-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="7d023-3124">Om NX_FRAGMENT_OKAY (0x0) anges tillåts IP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="7d023-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="7d023-3125">Om NX_DONT_FRAGMENT (0x4000) anges inaktive ras IP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="7d023-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="7d023-3126">**time_to_live** Anger det 8-bitars värde som definierar hur många routrar det här paketet kan passera innan det utlöses.</span><span class="sxs-lookup"><span data-stu-id="7d023-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="7d023-3127">Standardvärdet anges av NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="7d023-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="7d023-3128">**queue_maximum** Definierar det maximala antalet UDP-datagram som kan köas för denna socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="7d023-3129">När gränsen för kön har uppnåtts frigörs det äldsta UDP-paketet för varje nytt paket som togs emot.</span><span class="sxs-lookup"><span data-stu-id="7d023-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3130">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3130">Return Values</span></span>

- <span data-ttu-id="7d023-3131">**NX_SUCCESS** (0x00) Det gick inte att skapa UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="7d023-3132">**NX_OPTION_ERROR** (0X0a) ogiltigt alternativ typ-of-service, fragment eller Time-to-Live.</span><span class="sxs-lookup"><span data-stu-id="7d023-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="7d023-3133">**NX_PTR_ERROR** (0X07) ogiltig IP-eller socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="7d023-3134">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3135">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3136">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3136">Allowed From</span></span>

<span data-ttu-id="7d023-3137">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="7d023-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3138">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3138">Preemption Possible</span></span>

<span data-ttu-id="7d023-3139">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3140">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3141">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3141">See Also</span></span>

- <span data-ttu-id="7d023-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3143">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3144">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3145">nx_udp_socket_checksum_enable nx_udp_socket_delete,</span><span class="sxs-lookup"><span data-stu-id="7d023-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="7d023-3146">nx_udp_socket_info_get nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="7d023-3147">nx_udp_socket_receive nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-3148">nx_udp_socket_send nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="7d023-3149">nx_udp_socket_unbind nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="7d023-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="7d023-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="7d023-3151">Ta bort UDP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3152">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-3153">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3153">Description</span></span>

<span data-ttu-id="7d023-3154">Den här tjänsten tar bort en UDP-socket som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="7d023-3155">Om socketen var kopplad till en port måste socketen vara obunden först.</span><span class="sxs-lookup"><span data-stu-id="7d023-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3156">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3156">Parameters</span></span>

- <span data-ttu-id="7d023-3157">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3158">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3158">Return Values</span></span>

- <span data-ttu-id="7d023-3159">**NX_SUCCESS** (0x00) ta bort socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="7d023-3160">**NX_STILL_BOUND** (0X42) socket är fortfarande kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="7d023-3161">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-3162">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3163">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3164">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3164">Allowed From</span></span>

<span data-ttu-id="7d023-3165">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3166">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3166">Preemption Possible</span></span>

<span data-ttu-id="7d023-3167">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3168">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3169">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3169">See Also</span></span>

- <span data-ttu-id="7d023-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3171">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3172">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3173">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3174">nx_udp_socket_info_get nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="7d023-3175">nx_udp_socket_receive nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-3176">nx_udp_socket_send nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="7d023-3177">nx_udp_socket_unbind nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="7d023-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="7d023-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="7d023-3179">Hämta information om UDP-socket-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="7d023-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3180">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="7d023-3181">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3181">Description</span></span>

<span data-ttu-id="7d023-3182">Den här tjänsten hämtar information om UDP-socket-aktiviteter för den angivna UDP-socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="7d023-3183">*Om en mål pekare är NX_NULL returneras inte den informationen till anroparen.*</span><span class="sxs-lookup"><span data-stu-id="7d023-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3184">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3184">Parameters</span></span>

- <span data-ttu-id="7d023-3185">**socket_ptr** Pekare till den tidigare skapade UDP socket-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="7d023-3186">**udp_packets_sent** Pekare till målet för det totala antalet UDP-paket som skickats på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="7d023-3187">**udp_bytes_sent** Pekare till målet för det totala antalet UDP-byte som skickats på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="7d023-3188">**udp_packets_received** Pekare till målet för det totala antalet UDP-paket som tagits emot på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="7d023-3189">**udp_bytes_received** Pekare till målet för det totala antalet UDP-byte som tagits emot vid socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="7d023-3190">**udp_packets_queued** Pekare till målet för det totala antalet köade UDP-paket på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="7d023-3191">**udp_receive_packets_dropped** Pekare till målet för det totala antalet UDP-mottagna paket som har tagits bort för socket på grund av att köns storlek överskrids.</span><span class="sxs-lookup"><span data-stu-id="7d023-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="7d023-3192">**udp_checksum_errors** Pekare till målet för det totala antalet UDP-paket med fel kontroll summor på socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3193">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3193">Return Values</span></span>

- <span data-ttu-id="7d023-3194">**NX_SUCCESS** (0X00) lyckades hämtning av UDP-socket-information.</span><span class="sxs-lookup"><span data-stu-id="7d023-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="7d023-3195">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-3196">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3197">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3198">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3198">Allowed From</span></span>

<span data-ttu-id="7d023-3199">Initiering, trådar och timers</span><span class="sxs-lookup"><span data-stu-id="7d023-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3200">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3200">Preemption Possible</span></span>

<span data-ttu-id="7d023-3201">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3202">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-3203">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3203">See Also</span></span>

- <span data-ttu-id="7d023-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3205">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3206">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3207">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3208">nx_udp_socket_delete nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="7d023-3209">nx_udp_socket_receive nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-3210">nx_udp_socket_send nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="7d023-3211">nx_udp_socket_unbind nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="7d023-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="7d023-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="7d023-3213">Hämta port nummer som är kopplat till UDP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3214">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-3215">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3215">Description</span></span>

<span data-ttu-id="7d023-3216">Den här tjänsten hämtar det port nummer som är associerat med socketen, vilket är användbart för att hitta den port som allokerats av NetX i situationer där NX_ANY_PORT angavs vid den tidpunkt då socketen var kopplad.</span><span class="sxs-lookup"><span data-stu-id="7d023-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3217">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3217">Parameters</span></span>

- <span data-ttu-id="7d023-3218">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="7d023-3219">**port_ptr** Pekare till målet för retur port numret.</span><span class="sxs-lookup"><span data-stu-id="7d023-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="7d023-3220">Giltiga port nummer är (1 – 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="7d023-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3221">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3221">Return Values</span></span>

- <span data-ttu-id="7d023-3222">**NX_SUCCESS** (0x00) socket-bindning.</span><span class="sxs-lookup"><span data-stu-id="7d023-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="7d023-3223">**NX_NOT_BOUND** (0X24) den här socketen är inte kopplad till någon port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="7d023-3224">**NX_PTR_ERROR** (0X07) ogiltig socket pekare eller port retur pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="7d023-3225">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3226">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3227">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3227">Allowed From</span></span>

<span data-ttu-id="7d023-3228">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3229">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3229">Preemption Possible</span></span>

<span data-ttu-id="7d023-3230">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3231">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3232">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3232">See Also</span></span>

- <span data-ttu-id="7d023-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3234">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3235">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3236">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3237">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3238">nx_udp_socket_receive nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-3239">nx_udp_socket_send nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="7d023-3240">nx_udp_socket_unbind nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="7d023-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d023-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="7d023-3242">Ta emot datagram från UDP-socket</span><span class="sxs-lookup"><span data-stu-id="7d023-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3243">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d023-3244">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3244">Description</span></span>

<span data-ttu-id="7d023-3245">Den här tjänsten tar emot ett UDP-datagram från den angivna socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="7d023-3246">Om inget datagram har placerats i kö på den angivna socketen, pausas anroparen utifrån det angivna wait-alternativet.</span><span class="sxs-lookup"><span data-stu-id="7d023-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="7d023-3247">*Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*</span><span class="sxs-lookup"><span data-stu-id="7d023-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3248">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3248">Parameters</span></span>

- <span data-ttu-id="7d023-3249">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="7d023-3250">**packet_ptr** Pekare till paket pekare för UDP-datagram.</span><span class="sxs-lookup"><span data-stu-id="7d023-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="7d023-3251">**wait_option** Definierar hur tjänsten fungerar om ett datagram inte är i kö för närvarande i kö.</span><span class="sxs-lookup"><span data-stu-id="7d023-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="7d023-3252">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d023-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="7d023-3253">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="7d023-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="7d023-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="7d023-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="7d023-3255">timeout-värde i Tick (0x00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="7d023-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3256">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3256">Allowed From</span></span>

<span data-ttu-id="7d023-3257">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3258">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3258">Preemption Possible</span></span>

<span data-ttu-id="7d023-3259">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3260">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3261">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3261">See Also</span></span>

- <span data-ttu-id="7d023-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3263">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3264">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3265">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3266">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3267">nx_udp_socket_port_get nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="7d023-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="7d023-3268">nx_udp_socket_send nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="7d023-3269">nx_udp_socket_unbind nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="7d023-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="7d023-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="7d023-3271">Meddela program om varje mottaget paket</span><span class="sxs-lookup"><span data-stu-id="7d023-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3272">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="7d023-3273">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3273">Description</span></span>

<span data-ttu-id="7d023-3274">Den här tjänsten ställer in en aviserings funktions pekare för funktionen motringning till funktionen motringning som anges av programmet.</span><span class="sxs-lookup"><span data-stu-id="7d023-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="7d023-3275">Den här återanrops funktionen anropas sedan när ett paket tas emot på socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="7d023-3276">Om det finns en NX_NULL-pekare är funktionen Receive notify inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="7d023-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3277">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3277">Parameters</span></span>

- <span data-ttu-id="7d023-3278">**socket_ptr** Pekare till UDP-socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="7d023-3279">**udp_receive_notify** Funktionen motringning till program som anropas när ett paket tas emot på socketen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3280">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3280">Allowed From</span></span>

<span data-ttu-id="7d023-3281">Initiering, trådar, timers och ISR: er</span><span class="sxs-lookup"><span data-stu-id="7d023-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3282">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3282">Preemption Possible</span></span>

<span data-ttu-id="7d023-3283">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3284">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3285">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3285">See Also</span></span>

- <span data-ttu-id="7d023-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3287">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3288">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3289">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3290">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3292">nx_udp_socket_interface_send nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="7d023-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="7d023-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="7d023-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="7d023-3295">Skicka ett UDP-datagram</span><span class="sxs-lookup"><span data-stu-id="7d023-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3296">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="7d023-3297">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3297">Description</span></span>

<span data-ttu-id="7d023-3298">Den här tjänsten skickar ett UDP-datagram via en tidigare skapad och kopplad UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="7d023-3299">NetX hittar en lämplig lokal IP-adress som käll adress baserat på mål-IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="7d023-3300">Om du vill ange ett särskilt gränssnitt och en käll-IP-adress ska programmet använda tjänsten **nx_udp_socket_interface_send** .</span><span class="sxs-lookup"><span data-stu-id="7d023-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="7d023-3301">Observera att den här tjänsten returnerar omedelbart oavsett om UDP-datagramet har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="7d023-3302">Socketen måste vara kopplad till en lokal port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3303">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3303">Parameters</span></span>

- <span data-ttu-id="7d023-3304">**socket_ptr** Pekare till den tidigare skapade UDP-instansen</span><span class="sxs-lookup"><span data-stu-id="7d023-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="7d023-3305">**packet_ptr** Paket pekare för UDP-datagram</span><span class="sxs-lookup"><span data-stu-id="7d023-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="7d023-3306">**ip_address** Mål-IP-adress</span><span class="sxs-lookup"><span data-stu-id="7d023-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="7d023-3307">**port** Giltigt mål port nummer mellan 1 och 0Xffffffff) i värdens byte ordning</span><span class="sxs-lookup"><span data-stu-id="7d023-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3308">Return Values</span></span>

- <span data-ttu-id="7d023-3309">**NX_SUCCESS** (0X00) lyckades UDP socket Send</span><span class="sxs-lookup"><span data-stu-id="7d023-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="7d023-3310">**NX_NOT_BOUND** -sockel (0x24) är inte kopplad till någon port</span><span class="sxs-lookup"><span data-stu-id="7d023-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="7d023-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) Det går inte att hitta något lämpligt utgående gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7d023-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="7d023-3312">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig Server-IP-adress</span><span class="sxs-lookup"><span data-stu-id="7d023-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="7d023-3313">**NX_UNDERFLOW** (protokollnumret 0x02) inte tillräckligt med utrymme för UDP-huvudet i paketet</span><span class="sxs-lookup"><span data-stu-id="7d023-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="7d023-3314">**NX_OVERFLOW** (0X03) paket tilläggs pekare är ogiltig</span><span class="sxs-lookup"><span data-stu-id="7d023-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="7d023-3315">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare</span><span class="sxs-lookup"><span data-stu-id="7d023-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="7d023-3316">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="7d023-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="7d023-3317">**NX_NOT_ENABLED** (0X14) UDP har inte Aktiver ATS</span><span class="sxs-lookup"><span data-stu-id="7d023-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="7d023-3318">**NX_INVALID_PORT** (0X46) port numret är inte inom ett giltigt intervall</span><span class="sxs-lookup"><span data-stu-id="7d023-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3319">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3319">Allowed From</span></span>

<span data-ttu-id="7d023-3320">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3321">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3321">Preemption Possible</span></span>

<span data-ttu-id="7d023-3322">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3323">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3324">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3324">See Also</span></span>

- <span data-ttu-id="7d023-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3326">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3327">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3328">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3329">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3330">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3331">nx_udp_socket_receive_notify nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="7d023-3332">nx_udp_socket_unbind nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="7d023-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="7d023-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="7d023-3334">Skicka datagram via UDP-socket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3335">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="7d023-3336">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3336">Description</span></span>

<span data-ttu-id="7d023-3337">Den här tjänsten skickar ett UDP-datagram via en tidigare skapad och kopplad UDP-socket via nätverks gränssnittet med den angivna IP-adressen som käll adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="7d023-3338">Observera att tjänsten returnerar omedelbart, oavsett om UDP-datagramet har skickats eller inte.</span><span class="sxs-lookup"><span data-stu-id="7d023-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3339">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3339">Parameters</span></span>

- <span data-ttu-id="7d023-3340">**socket_ptr** Socket för att överföra paketet.</span><span class="sxs-lookup"><span data-stu-id="7d023-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="7d023-3341">**packet_ptr** Pekare till paket att överföra.</span><span class="sxs-lookup"><span data-stu-id="7d023-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="7d023-3342">**ip_address** Mål-IP-adress att skicka paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="7d023-3343">**port** Målport.</span><span class="sxs-lookup"><span data-stu-id="7d023-3343">**port** Destination port.</span></span>
- <span data-ttu-id="7d023-3344">**address_index** Index för den adress som är associerad med det gränssnitt som ska användas för att skicka paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3345">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3345">Return Values</span></span>

- <span data-ttu-id="7d023-3346">**NX_SUCCESSs** paket (0x00) har skickats.</span><span class="sxs-lookup"><span data-stu-id="7d023-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="7d023-3347">**NX_NOT_BOUND** -socketen (0x24) är inte kopplad till en port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="7d023-3348">**NX_IP_ADDRESS_ERROR** (0X21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="7d023-3349">**NX_NOT_ENABLED** (0X14) UDP-bearbetning är inte aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7d023-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="7d023-3350">**NX_PTR_ERROR** (0X07) ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="7d023-3351">**NX_OVERFLOW** (0X03) ogiltig paket tilläggs pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="7d023-3352">**NX_UNDERFLOW** (protokollnumret 0x02) ogiltig lägga pekare för paket.</span><span class="sxs-lookup"><span data-stu-id="7d023-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="7d023-3353">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3354">**NX_INVALID_INTERFACE** (0X4C) ogiltigt adress index.</span><span class="sxs-lookup"><span data-stu-id="7d023-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="7d023-3355">**NX_INVALID_PORT** (0X46) port numret överskrider det högsta port numret.</span><span class="sxs-lookup"><span data-stu-id="7d023-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3356">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3356">Allowed From</span></span>

<span data-ttu-id="7d023-3357">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3358">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3358">Preemption Possible</span></span>

<span data-ttu-id="7d023-3359">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3360">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3361">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3361">See Also</span></span>

- <span data-ttu-id="7d023-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3363">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3364">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3365">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3366">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3367">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3368">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="7d023-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="7d023-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="7d023-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="7d023-3371">Bind UDP-socketen från UDP-porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3372">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="7d023-3373">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3373">Description</span></span>

<span data-ttu-id="7d023-3374">Den här tjänsten frigör bindningen mellan UDP-socketen och en UDP-port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="7d023-3375">Alla mottagna paket som lagras i mottagnings kön frigörs som en del av Unbind-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7d023-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="7d023-3376">Om det finns andra trådar som väntar på att binda en annan socket till den obundna porten, binds den första pausade tråden till den nyligen obundna porten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3377">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3377">Parameters</span></span>

- <span data-ttu-id="7d023-3378">**socket_ptr** Pekare till den tidigare skapade UDP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7d023-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3379">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3379">Return Values</span></span>

- <span data-ttu-id="7d023-3380">**NX_SUCCESS** (0x00) uppkopplad socket-bindning.</span><span class="sxs-lookup"><span data-stu-id="7d023-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="7d023-3381">**NX_NOT_BOUND** -socketen var inte kopplad till någon port.</span><span class="sxs-lookup"><span data-stu-id="7d023-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="7d023-3382">**NX_PTR_ERROR** (0X07) ogiltig socket-pekare.</span><span class="sxs-lookup"><span data-stu-id="7d023-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="7d023-3383">**NX_CALLER_ERROR** (0X11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="7d023-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="7d023-3384">**NX_NOT_ENABLED** (0X14) den här komponenten har inte Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="7d023-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3385">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3385">Allowed From</span></span>

<span data-ttu-id="7d023-3386">Konversation</span><span class="sxs-lookup"><span data-stu-id="7d023-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3387">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3387">Preemption Possible</span></span>

<span data-ttu-id="7d023-3388">Ja</span><span class="sxs-lookup"><span data-stu-id="7d023-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3389">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="7d023-3390">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3390">See Also</span></span>

- <span data-ttu-id="7d023-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3392">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3393">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3394">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3395">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3396">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3397">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3398">nx_udp_socket_interface_send nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="7d023-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="7d023-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="7d023-3400">Extrahera IP och skicka port från UDP-datagram</span><span class="sxs-lookup"><span data-stu-id="7d023-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="7d023-3401">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7d023-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="7d023-3402">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d023-3402">Description</span></span>

<span data-ttu-id="7d023-3403">Den här tjänsten extraherar avsändarens IP-adress och port nummer från IP-och UDP-huvudena för det angivna UDP-datagrammet.</span><span class="sxs-lookup"><span data-stu-id="7d023-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d023-3404">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d023-3404">Parameters</span></span>

- <span data-ttu-id="7d023-3405">**packet_ptr** Paket pekare för UDP-datagram.</span><span class="sxs-lookup"><span data-stu-id="7d023-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="7d023-3406">**ip_address** Giltig pekare till variabeln returnera IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7d023-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="7d023-3407">**port** Giltig pekare till retur port-variabeln.</span><span class="sxs-lookup"><span data-stu-id="7d023-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d023-3408">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7d023-3408">Return Values</span></span>

- <span data-ttu-id="7d023-3409">**NX_SUCCESS** (0X00) lyckad käll-IP/port-extrahering.</span><span class="sxs-lookup"><span data-stu-id="7d023-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="7d023-3410">**NX_INVALID_PACKET** (0X12) det angivna paketet är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="7d023-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="7d023-3411">**NX_PTR_ERROR** (0X07) ogiltigt paket eller IP-eller port mål.</span><span class="sxs-lookup"><span data-stu-id="7d023-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d023-3412">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7d023-3412">Allowed From</span></span>

<span data-ttu-id="7d023-3413">Initiering, trådar, timers, ISR</span><span class="sxs-lookup"><span data-stu-id="7d023-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="7d023-3414">Avstängningen möjlig</span><span class="sxs-lookup"><span data-stu-id="7d023-3414">Preemption Possible</span></span>

<span data-ttu-id="7d023-3415">Inga</span><span class="sxs-lookup"><span data-stu-id="7d023-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="7d023-3416">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d023-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="7d023-3417">Se även</span><span class="sxs-lookup"><span data-stu-id="7d023-3417">See Also</span></span>

- <span data-ttu-id="7d023-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="7d023-3419">nx_udp_packet_info_extract nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="7d023-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="7d023-3420">nx_udp_socket_bytes_available nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="7d023-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="7d023-3421">nx_udp_socket_checksum_enable nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="7d023-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="7d023-3422">nx_udp_socket_delete nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="7d023-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="7d023-3423">nx_udp_socket_port_get nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="7d023-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="7d023-3424">nx_udp_socket_receive_notify nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="7d023-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="7d023-3425">nx_udp_socket_interface_send nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="7d023-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>