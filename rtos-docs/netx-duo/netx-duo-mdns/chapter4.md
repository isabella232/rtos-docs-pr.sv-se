---
title: Kapitel 4 – Beskrivning av mDNS-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX mDNS-tjänster
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825917"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="0df71-103">Kapitel 4 – Beskrivning av mDNS-tjänster</span><span class="sxs-lookup"><span data-stu-id="0df71-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="0df71-104">Det här kapitlet innehåller en beskrivning av alla NetX mDNS-tjänster (visas nedan).</span><span class="sxs-lookup"><span data-stu-id="0df71-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="0df71-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="0df71-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="0df71-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="0df71-106">nx_mdns_create</span></span>

<span data-ttu-id="0df71-107">Skapa en mDNS-instans</span><span class="sxs-lookup"><span data-stu-id="0df71-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="0df71-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-109">Description</span></span>

<span data-ttu-id="0df71-110">Den här tjänsten skapar en mDNS-instans på den angivna IP-instansen och associerade resurser.</span><span class="sxs-lookup"><span data-stu-id="0df71-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="0df71-111">En tråd skapas också för att hantera inkommande mDNS-meddelanden, för att svara på frågor och för att regelbundet överföra frågemeddelanden.</span><span class="sxs-lookup"><span data-stu-id="0df71-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-112">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-112">Input Parameters</span></span>

- <span data-ttu-id="0df71-113">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-114">**ip_ptr** Pekare till den associerade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="0df71-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="0df71-115">**packet_pool** Pekar mot en giltig adresspool.</span><span class="sxs-lookup"><span data-stu-id="0df71-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="0df71-116">**prioritet** Prioritet för mDNS-tråden.</span><span class="sxs-lookup"><span data-stu-id="0df71-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="0df71-117">**stack_ptr** Pekare till stackområdet för mDNS-tråden</span><span class="sxs-lookup"><span data-stu-id="0df71-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="0df71-118">**stack_size** Storlek på stackområdet.</span><span class="sxs-lookup"><span data-stu-id="0df71-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="0df71-119">**host_name** Värd namnet tilldelat till den här noden.</span><span class="sxs-lookup"><span data-stu-id="0df71-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="0df71-120">**local_service_cache** Lagrings utrymme för lokala registrerade tjänster.</span><span class="sxs-lookup"><span data-stu-id="0df71-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="0df71-121">**local_service_cache_size** Storlek på den lokala tjänstens cacheminne.</span><span class="sxs-lookup"><span data-stu-id="0df71-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="0df71-122">**peer_service_cache** Lagrings utrymme för mottagen tjänst information</span><span class="sxs-lookup"><span data-stu-id="0df71-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="0df71-123">**peer_service_cache_size** Storlek på peer-tjänstecache</span><span class="sxs-lookup"><span data-stu-id="0df71-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="0df71-124">**probing_notify** Valfri callback-funktion anropades i slutet av avsöknings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="0df71-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="0df71-125">Det meddelar programmet oavsett om värd namnet (när du aktiverar mDNS på ett lokalt gränssnitt), eller om tjänst namnet (efter registreringen av en tjänst) är unikt.</span><span class="sxs-lookup"><span data-stu-id="0df71-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-126">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-126">Return Values</span></span>

- <span data-ttu-id="0df71-127">**NX_SUCCESS** (0x00) skapade mdns-instansen.</span><span class="sxs-lookup"><span data-stu-id="0df71-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-128">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-128">Allowed From</span></span>

<span data-ttu-id="0df71-129">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="0df71-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="0df71-131">nx_mdns_delete</span></span>

<span data-ttu-id="0df71-132">Ta bort en mDNS-instans</span><span class="sxs-lookup"><span data-stu-id="0df71-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-133">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="0df71-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-134">Description</span></span>

<span data-ttu-id="0df71-135">Den här tjänsten tar bort mDNS-instansen och frigör dess resurser.</span><span class="sxs-lookup"><span data-stu-id="0df71-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-136">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-136">Input Parameters</span></span>

- <span data-ttu-id="0df71-137">**mdns_ptr** Pekare till kontroll blocket mDNS.</span><span class="sxs-lookup"><span data-stu-id="0df71-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-138">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-138">Return Values</span></span>

- <span data-ttu-id="0df71-139">**NX_SUCCESS** (0X00) har tagit bort mdns-instansen.</span><span class="sxs-lookup"><span data-stu-id="0df71-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-140">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-140">Allowed From</span></span>

<span data-ttu-id="0df71-141">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-142">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="0df71-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="0df71-143">nx_mdns_enable</span></span>

<span data-ttu-id="0df71-144">Starta mDNS-tjänsten</span><span class="sxs-lookup"><span data-stu-id="0df71-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-145">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0df71-146">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-146">Description</span></span>

<span data-ttu-id="0df71-147">Detta API aktiverar mDNS-tjänsten på ett angivet fysiskt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="0df71-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="0df71-148">När tjänsten är aktive rad avsöker mDNS-modulen först alla sina unika tjänst namn i nätverket innan de svarar på frågor som tagits emot i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="0df71-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-149">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-149">Input Parameters</span></span>

- <span data-ttu-id="0df71-150">**mdns_ptr** Pekar mot kontroll blocket för mDNS-instansen.</span><span class="sxs-lookup"><span data-stu-id="0df71-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="0df71-151">**interface_index** Indexera det gränssnitt där tjänsten ska aktive ras</span><span class="sxs-lookup"><span data-stu-id="0df71-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-152">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-152">Return Values</span></span>

- <span data-ttu-id="0df71-153">**NX_SUCCESS** (0x00) aktiverade tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-154">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-154">Allowed From</span></span>

<span data-ttu-id="0df71-155">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-156">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="0df71-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="0df71-157">nx_mdns_disable</span></span>

<span data-ttu-id="0df71-158">Inaktivera tjänsten mDNS</span><span class="sxs-lookup"><span data-stu-id="0df71-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-159">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0df71-160">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-160">Description</span></span>

<span data-ttu-id="0df71-161">Detta API inaktiverar mDNS-tjänsten för det angivna fysiska gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="0df71-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="0df71-162">När tjänsten är inaktive rad skickar mDNS meddelandet "Hej" för varje lokal tjänst till nätverket som är kopplat till gränssnittet, så att intilliggande noder meddelas.</span><span class="sxs-lookup"><span data-stu-id="0df71-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-163">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-163">Input Parameters</span></span>

- <span data-ttu-id="0df71-164">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-165">**interface_index** Indexera till gränssnittet där tjänsten ska inaktive ras</span><span class="sxs-lookup"><span data-stu-id="0df71-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-166">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-166">Return Values</span></span>

- <span data-ttu-id="0df71-167">**NX_SUCCESS** (0X00) har inaktiverat tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-168">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-168">Allowed From</span></span>

<span data-ttu-id="0df71-169">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="0df71-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="0df71-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="0df71-172">Installerar funktionen mDNS cache full notify</span><span class="sxs-lookup"><span data-stu-id="0df71-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="0df71-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-174">Description</span></span>

<span data-ttu-id="0df71-175">Den här tjänsten installerar en motringnings funktion som anges av användaren, som anropas när antingen den lokala tjänstecachen eller peer-tjänstecachen blir full.</span><span class="sxs-lookup"><span data-stu-id="0df71-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="0df71-176">När tjänstecachen är full kan ingen mer mDNS-resurspost läggas till.</span><span class="sxs-lookup"><span data-stu-id="0df71-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="0df71-177">Observera att tjänstecachen kan bli full till följd av intern fragmentering när tjänster med olika sträng längd läggs till och tas bort.</span><span class="sxs-lookup"><span data-stu-id="0df71-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="0df71-178">Vid mottagning av en cache fullständig avisering i peer service cache kan programmet använda tjänsten "*nx_mdns_service_cache_clear"* för att radera alla poster i peer-tjänstecachen.</span><span class="sxs-lookup"><span data-stu-id="0df71-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-179">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-179">Input Parameters</span></span>

- <span data-ttu-id="0df71-180">**mdns_ptr** Pekare till kontroll blocket mDNS.</span><span class="sxs-lookup"><span data-stu-id="0df71-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-181">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-181">Return Values</span></span>

- <span data-ttu-id="0df71-182">**NX_SUCCESS** (0X00) har installerat funktionen mdns cache notify motringning.</span><span class="sxs-lookup"><span data-stu-id="0df71-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-183">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-183">Allowed From</span></span>

<span data-ttu-id="0df71-184">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-185">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="0df71-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="0df71-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="0df71-187">Rensa funktionen mDNS service cache full notify</span><span class="sxs-lookup"><span data-stu-id="0df71-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-188">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="0df71-189">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-189">Description</span></span>

<span data-ttu-id="0df71-190">Den här tjänsten rensar en funktion för att skicka ett tjänst-cache som tillhandahålls av användaren.</span><span class="sxs-lookup"><span data-stu-id="0df71-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-191">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-191">Input Parameters</span></span>

- <span data-ttu-id="0df71-192">**mdns_ptr** Pekare till kontroll blocket mDNS.</span><span class="sxs-lookup"><span data-stu-id="0df71-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-193">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-193">Return Values</span></span>

- <span data-ttu-id="0df71-194">**NX_SUCCESS** (0x00) rensade funktionen mdns service cache notify motringning.</span><span class="sxs-lookup"><span data-stu-id="0df71-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-195">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-195">Allowed From</span></span>

<span data-ttu-id="0df71-196">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-197">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="0df71-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="0df71-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="0df71-199">Anger domän namnet</span><span class="sxs-lookup"><span data-stu-id="0df71-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="0df71-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-201">Description</span></span>

<span data-ttu-id="0df71-202">Den här tjänsten konfigurerar det lokala standard domän namnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="0df71-203">När mDNS-instansen skapas anges standard namnet för den lokala domänen till ". local".</span><span class="sxs-lookup"><span data-stu-id="0df71-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="0df71-204">Detta API gör att ett program kan skriva över det lokala standard domän namnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-205">Input Parameters</span></span>

- <span data-ttu-id="0df71-206">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-207">**domain_name** Det domän namn som ska användas.</span><span class="sxs-lookup"><span data-stu-id="0df71-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-208">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-208">Return Values</span></span>

- <span data-ttu-id="0df71-209">**NX_SUCCESS** (0X00) har konfigurerat en lokal domän.</span><span class="sxs-lookup"><span data-stu-id="0df71-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-210">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-210">Allowed From</span></span>

<span data-ttu-id="0df71-211">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-212">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="0df71-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="0df71-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="0df71-214">Anger tids parametrar för service meddelande meddelanden</span><span class="sxs-lookup"><span data-stu-id="0df71-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-215">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="0df71-216">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-216">Description</span></span>

<span data-ttu-id="0df71-217">Den här tjänsten konfigurerar om de tids parametrar som används av mDNS när de skickar tjänst meddelanden.</span><span class="sxs-lookup"><span data-stu-id="0df71-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="0df71-218">Publicerings perioden börjar från *t* -Tick och kan utökas telescopically med 2 till kraften i *k* faktor.</span><span class="sxs-lookup"><span data-stu-id="0df71-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="0df71-219">Antalet upprepningar per annons är *p*, intervallet mellan varje upprepad annons är *intervall* Tick och antalet meddelande perioder är max_time.</span><span class="sxs-lookup"><span data-stu-id="0df71-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="0df71-220">Som standard anges den inledande perioden till 1 sekund, med k = 1 (perioden dubbleras varje gång), *p = 1* (ingen upprepning), retrans_interval = 0 (inget tidsintervall), Period_interval = 0xFFFFFFFF (max period intervall) och max_time = 3 (antal annonser).</span><span class="sxs-lookup"><span data-stu-id="0df71-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-221">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-221">Input Parameters</span></span>

- <span data-ttu-id="0df71-222">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-223">**t** antal Tick för den inledande perioden.</span><span class="sxs-lookup"><span data-stu-id="0df71-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="0df71-224">Standardvärdet är 100 för 1 sekund.</span><span class="sxs-lookup"><span data-stu-id="0df71-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="0df71-225">**p** antal upprepningar.</span><span class="sxs-lookup"><span data-stu-id="0df71-225">**p** Number of repetitions.</span></span> <span data-ttu-id="0df71-226">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="0df71-226">Default value is 1.</span></span>
- <span data-ttu-id="0df71-227">**k** Telescopic faktor.</span><span class="sxs-lookup"><span data-stu-id="0df71-227">**k** Telescopic factor.</span></span> <span data-ttu-id="0df71-228">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="0df71-228">Default value is 1.</span></span>
- <span data-ttu-id="0df71-229">**retrans_interval** Antal Tick som ska förflyta innan meddelanden skickas ut från upprepade meddelanden.</span><span class="sxs-lookup"><span data-stu-id="0df71-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="0df71-230">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="0df71-230">Default value is 0.</span></span>
- <span data-ttu-id="0df71-231">**period_interval** Antalet Tick mellan två meddelande perioder.</span><span class="sxs-lookup"><span data-stu-id="0df71-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="0df71-232">Standardvärdet är 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="0df71-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="0df71-233">**max_time** Antal meddelande perioder som ska användas för annonsen.</span><span class="sxs-lookup"><span data-stu-id="0df71-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="0df71-234">Efter *max_time* meddelande perioder skickas inga fler meddelande meddelanden.</span><span class="sxs-lookup"><span data-stu-id="0df71-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="0df71-235">Standardvärdet är 3.</span><span class="sxs-lookup"><span data-stu-id="0df71-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-236">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-236">Return Values</span></span>

- <span data-ttu-id="0df71-237">**NX_SUCCESS** (0X00) har angett tids värden.</span><span class="sxs-lookup"><span data-stu-id="0df71-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-238">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-238">Allowed From</span></span>

<span data-ttu-id="0df71-239">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-240">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="0df71-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="0df71-241">nx_mdns_service_add</span></span>

<span data-ttu-id="0df71-242">Lägg till en lokal tjänst</span><span class="sxs-lookup"><span data-stu-id="0df71-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-243">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0df71-244">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-244">Description</span></span>

<span data-ttu-id="0df71-245">Detta API registrerar en tjänst som erbjuds av programmet.</span><span class="sxs-lookup"><span data-stu-id="0df71-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="0df71-246">Om flaggan *is_unique* har angetts avsöker mdns tjänst namnet för att kontrol lera att det är unikt i det lokala nätverket innan du börjar meddela tjänsten i nätverket.</span><span class="sxs-lookup"><span data-stu-id="0df71-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="0df71-247">*Instans* är instans delen av tjänst namnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="0df71-248">*Tjänsten* är tjänst delen av tjänst namnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="0df71-249">Till exempel "_http. _ TCP" är en tjänst.</span><span class="sxs-lookup"><span data-stu-id="0df71-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="0df71-250">För att beskriva en tjänst med undertyp måste anroparen använda under *typ* parametern.</span><span class="sxs-lookup"><span data-stu-id="0df71-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="0df71-251">Om den önskade tjänsten t. ex. är "_printer. _sub. _http. _ TCP", är tjänst fältet "_http. _ TCP:, och under Typ fältet är" _printer ".</span><span class="sxs-lookup"><span data-stu-id="0df71-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-252">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-252">Input Parameters</span></span>

- <span data-ttu-id="0df71-253">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-254">**instans** Pekar mot instans namnet för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="0df71-255">**tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp.</span><span class="sxs-lookup"><span data-stu-id="0df71-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="0df71-256">**undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="0df71-257">**prioritet** Tjänst prioritet</span><span class="sxs-lookup"><span data-stu-id="0df71-257">**priority** Service priority</span></span>
- <span data-ttu-id="0df71-258">**vikt** Tjänst vikt</span><span class="sxs-lookup"><span data-stu-id="0df71-258">**weight** Service weight</span></span>
- <span data-ttu-id="0df71-259">**port** TCP-eller UDP-portnummer som tjänsten använder</span><span class="sxs-lookup"><span data-stu-id="0df71-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="0df71-260">**text** Ytterligare text information</span><span class="sxs-lookup"><span data-stu-id="0df71-260">**text** Additional text information</span></span>
- <span data-ttu-id="0df71-261">**is_unique** Boolesk flagga som anger om tjänsten är delad eller unik.</span><span class="sxs-lookup"><span data-stu-id="0df71-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="0df71-262">För tjänster som är registrerade som unika måste mDNS avsöka tjänsten i nätverket innan de påbörjar erbjudandet.</span><span class="sxs-lookup"><span data-stu-id="0df71-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="0df71-263">**Interface_index** Det fysiska gränssnitt som tjänsten erbjuds via.</span><span class="sxs-lookup"><span data-stu-id="0df71-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="0df71-264">För en tjänst som erbjuds via någon av de anslutna tjänsterna används värdet *NX_MDNS_ALL_INTERFACES* .</span><span class="sxs-lookup"><span data-stu-id="0df71-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-265">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-265">Return Values</span></span>

- <span data-ttu-id="0df71-266">**NX_SUCCESS** (0X00) har registrerat tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-267">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-267">Allowed From</span></span>

<span data-ttu-id="0df71-268">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-269">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="0df71-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="0df71-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="0df71-271">Ta bort en tidigare registrerad tjänst</span><span class="sxs-lookup"><span data-stu-id="0df71-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-272">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="0df71-273">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-273">Description</span></span>

<span data-ttu-id="0df71-274">Detta API tar bort en tidigare registrerad tjänst.</span><span class="sxs-lookup"><span data-stu-id="0df71-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="0df71-275">När tjänsten tas bort skickas "" rader "meddelanden till det lokala nätverket så att intilliggande noder meddelas.</span><span class="sxs-lookup"><span data-stu-id="0df71-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-276">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-276">Input Parameters</span></span>

- <span data-ttu-id="0df71-277">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-278">**instans** Pekar mot instans namnet för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="0df71-279">**tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp.</span><span class="sxs-lookup"><span data-stu-id="0df71-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="0df71-280">**undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-281">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-281">Return Values</span></span>

- <span data-ttu-id="0df71-282">**NX_SUCCESS** (0X00) har tagit bort tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-283">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-283">Allowed From</span></span>

<span data-ttu-id="0df71-284">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-285">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="0df71-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="0df71-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="0df71-287">Starta tjänst identifiering för en bild</span><span class="sxs-lookup"><span data-stu-id="0df71-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-288">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0df71-289">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-289">Description</span></span>

<span data-ttu-id="0df71-290">Den här tjänsten utför en mDNS-fråga med en bild.</span><span class="sxs-lookup"><span data-stu-id="0df71-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="0df71-291">Om den angivna tjänsten finns i peer-tjänstecachen returneras den första instansen.</span><span class="sxs-lookup"><span data-stu-id="0df71-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="0df71-292">Om inga tjänster hittas i den lokala peer-tjänstecachen, utfärdar mDNS-modulen ett Query-kommando och väntar på svar.</span><span class="sxs-lookup"><span data-stu-id="0df71-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="0df71-293">Tjänsten är blockerad till antingen det första svaret eller tids gränsen för frågan.</span><span class="sxs-lookup"><span data-stu-id="0df71-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-294">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-294">Input Parameters</span></span>

- <span data-ttu-id="0df71-295">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-296">**instans** Pekar mot instans namnet för tjänsten, om det är tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="0df71-297">**tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp.</span><span class="sxs-lookup"><span data-stu-id="0df71-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="0df71-298">programmet måste ange tjänst typen.</span><span class="sxs-lookup"><span data-stu-id="0df71-298">the application must specify the service type.</span></span>
- <span data-ttu-id="0df71-299">**undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="0df71-300">**service_ptr** Användaren tillhandahöll NX_MDNS_SERVICE struktur som lagrar frågeresultaten.</span><span class="sxs-lookup"><span data-stu-id="0df71-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="0df71-301">**wait_option** Tiden, i Tick, för att vänta på ett svar.</span><span class="sxs-lookup"><span data-stu-id="0df71-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-302">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-302">Return Values</span></span>

- <span data-ttu-id="0df71-303">Information om tjänsten **NX_SUCCESS** (0X00) har hämtats.</span><span class="sxs-lookup"><span data-stu-id="0df71-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-304">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-304">Allowed From</span></span>

<span data-ttu-id="0df71-305">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-306">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="0df71-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="0df71-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="0df71-308">Initiera kontinuerlig identifiering av tjänst</span><span class="sxs-lookup"><span data-stu-id="0df71-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-309">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="0df71-310">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-310">Description</span></span>

<span data-ttu-id="0df71-311">Den här tjänsten startar en kontinuerlig fråga.</span><span class="sxs-lookup"><span data-stu-id="0df71-311">This service starts a continuous query.</span></span> <span data-ttu-id="0df71-312">Observera att tjänsten returnerar omedelbart.</span><span class="sxs-lookup"><span data-stu-id="0df71-312">Note that the service returns immediately.</span></span> <span data-ttu-id="0df71-313">När du har utfärdat en kontinuerlig fråga kan programmet Hämta tjänst poster med hjälp av API- *nx_mdns_service_lookup*.</span><span class="sxs-lookup"><span data-stu-id="0df71-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="0df71-314">För att stoppa den kontinuerliga frågan kan programmet använda API- *nx_mdns_service_query_stop*</span><span class="sxs-lookup"><span data-stu-id="0df71-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-315">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-315">Input Parameters</span></span>

- <span data-ttu-id="0df71-316">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-317">**instans** Pekar mot instans namnet för tjänsten, om det är tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="0df71-318">**tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="0df71-319">**undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-320">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-320">Return Values</span></span>

- <span data-ttu-id="0df71-321">**NX_SUCCESS** (0X00) har börjat fortsätta fråga.</span><span class="sxs-lookup"><span data-stu-id="0df71-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-322">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-322">Allowed From</span></span>

<span data-ttu-id="0df71-323">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-324">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="0df71-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="0df71-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="0df71-326">Upphöra med en tidigare utfärdad kontinuerlig tjänst identifiering</span><span class="sxs-lookup"><span data-stu-id="0df71-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-327">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="0df71-328">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-328">Description</span></span>

<span data-ttu-id="0df71-329">Detta API avslutar en tidigare utfärdad kontinuerlig tjänst identifiering.</span><span class="sxs-lookup"><span data-stu-id="0df71-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-330">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-330">Input Parameters</span></span>

- <span data-ttu-id="0df71-331">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-332">**instans** Pekar mot instans namnet för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="0df71-333">**tjänsten** Pekare till mDNS Service Type, undertyp information.</span><span class="sxs-lookup"><span data-stu-id="0df71-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="0df71-334">**undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-335">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-335">Return Values</span></span>

- <span data-ttu-id="0df71-336">**NX_SUCCESS** (0X00) har stoppats Fortsätt frågan.</span><span class="sxs-lookup"><span data-stu-id="0df71-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-337">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-337">Allowed From</span></span>

<span data-ttu-id="0df71-338">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-339">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="0df71-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="0df71-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="0df71-341">Hämtar tjänsten från den lokala peer-tjänstecachen</span><span class="sxs-lookup"><span data-stu-id="0df71-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-342">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="0df71-343">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-343">Description</span></span>

<span data-ttu-id="0df71-344">Den här tjänsten söker efter tjänster som matchar instans namnet (om det finns) och typen av tjänst i den lokala peer-tjänstecachen.</span><span class="sxs-lookup"><span data-stu-id="0df71-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="0df71-345">Programmet ska starta tjänstens sökning med *instance_index* har värdet noll för den första tjänsten i cachen som matchar beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="0df71-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="0df71-346">Programmet måste fortsätta använda den här tjänsten med ökande *instance_index* värde för ytterligare tjänster som finns i cacheminnet, till tjänsten returnerar *NX_NO_MORE_ENTRIES*, vilket indikerar cacheminnets slut.</span><span class="sxs-lookup"><span data-stu-id="0df71-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-347">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-347">Input Parameters</span></span>

- <span data-ttu-id="0df71-348">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-349">**instans** Pekar mot instans namnet för tjänsten, om det är tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="0df71-350">**tjänsten** Pekare till tjänst typen mDNS, exklusive information om undertyp, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="0df71-351">**undertyp** Pekar på under typs delen av mDNS-tjänsten, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="0df71-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="0df71-352">**Instance_index** Index numret till den instans som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="0df71-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="0df71-353">**service_ptr** Användaren tillhandahöll en NX_MDNS_SERVICE struktur som lagrar Sök resultaten.</span><span class="sxs-lookup"><span data-stu-id="0df71-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-354">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-354">Return Values</span></span>

- <span data-ttu-id="0df71-355">**NX_SUCCESS** (0X00) har hämtat tjänsten</span><span class="sxs-lookup"><span data-stu-id="0df71-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="0df71-356">**NX_NO_MORE_ENTRIES** (0x17) Det gick inte att hitta någon tjänst post på det angivna index numret.</span><span class="sxs-lookup"><span data-stu-id="0df71-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="0df71-357">Den här fel koden anger slutet på sökningen.</span><span class="sxs-lookup"><span data-stu-id="0df71-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-358">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-358">Allowed From</span></span>

<span data-ttu-id="0df71-359">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-360">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="0df71-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="0df71-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="0df71-362">Konfigurerar en tjänst som ignorerar</span><span class="sxs-lookup"><span data-stu-id="0df71-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-363">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="0df71-364">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-364">Description</span></span>

<span data-ttu-id="0df71-365">Detta API konfigurerar en mask för att ignorera tjänster som anges av *service_mask* bitmask.</span><span class="sxs-lookup"><span data-stu-id="0df71-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="0df71-366">Användaren kan eventuellt använda service_mask för att välja tjänst typer som inte vill cachelagras.</span><span class="sxs-lookup"><span data-stu-id="0df71-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="0df71-367">En lista över tjänster definieras i tabellen *nx_mdns_service_types* i *nxd_mdns. c.*</span><span class="sxs-lookup"><span data-stu-id="0df71-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="0df71-368">Motsvarande mask för den första tjänst typen i nx_mdns_service_types [] är 0x00000001, masken för den andra tjänst typen är 0x00000002 och så vidare.</span><span class="sxs-lookup"><span data-stu-id="0df71-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-369">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-369">Input Parameters</span></span>

- <span data-ttu-id="0df71-370">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-371">**service_mask** Användardefinierade tjänst typer att ignorera.</span><span class="sxs-lookup"><span data-stu-id="0df71-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="0df71-372">Masken är en 32-bitars ULONG-typ.</span><span class="sxs-lookup"><span data-stu-id="0df71-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="0df71-373">Varje bit representerar en post i den användardefinierade *nx_mdns_service_types* matrisen.</span><span class="sxs-lookup"><span data-stu-id="0df71-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="0df71-374">Om en bit anges kommer motsvarande tjänst typ som anges i *nx_mdns_service_type* matrisen inte att lagras i peer-tjänstecacheminnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-375">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-375">Return Values</span></span>

- <span data-ttu-id="0df71-376">**NX_SUCCESS** (0X00) har angett en mask för att ignorera tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0df71-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-377">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-377">Allowed From</span></span>

<span data-ttu-id="0df71-378">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-379">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="0df71-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="0df71-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="0df71-381">Konfigurerar en tjänst ändring Avisera motringning funktion</span><span class="sxs-lookup"><span data-stu-id="0df71-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-382">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="0df71-383">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-383">Description</span></span>

<span data-ttu-id="0df71-384">Detta API konfigurerar en tjänst ändrings avisering om motringning.</span><span class="sxs-lookup"><span data-stu-id="0df71-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="0df71-385">Den här callback-funktionen anropas när en tjänst som erbjuds av andra noder i nätverket läggs till, ändras eller inte längre är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="0df71-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="0df71-386">Användaren kan eventuellt använda service_mask för att välja tjänst typer som det vill övervaka.</span><span class="sxs-lookup"><span data-stu-id="0df71-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="0df71-387">En lista över tjänster som övervakas är hårdkodade i tabellen *nx_mdns_service_types* i *nxd_mdns. c.*</span><span class="sxs-lookup"><span data-stu-id="0df71-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="0df71-388">Motsvarande mask för den första tjänst typen i nx_mdns_service_types [] är 0x00000001, masken för den andra tjänst typen är 0x00000002 och så vidare.</span><span class="sxs-lookup"><span data-stu-id="0df71-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-389">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-389">Input Parameters</span></span>

- <span data-ttu-id="0df71-390">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-391">**service_mask** Användardefinierade tjänst typer som ska övervakas.</span><span class="sxs-lookup"><span data-stu-id="0df71-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="0df71-392">Masken är en 32-bitars ULONG-typ.</span><span class="sxs-lookup"><span data-stu-id="0df71-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="0df71-393">Varje bit representerar en post i *nx_mdns_service_types* matrisen.</span><span class="sxs-lookup"><span data-stu-id="0df71-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="0df71-394">**service_change_notify** Motringningsfunktionen som anropas när den angivna tjänsten ändras.</span><span class="sxs-lookup"><span data-stu-id="0df71-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="0df71-395">Detaljerad tjänst information returneras i minnet som pekas på *service_ptr.*</span><span class="sxs-lookup"><span data-stu-id="0df71-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="0df71-396">Observera att innehållet i minnet är ogiltigt när du har returnerat från funktionen meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="0df71-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-397">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-397">Return Values</span></span>

- <span data-ttu-id="0df71-398">**NX_SUCCESS** (0X00) har installerat motringningsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="0df71-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-399">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-399">Allowed From</span></span>

<span data-ttu-id="0df71-400">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-401">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="0df71-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="0df71-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="0df71-403">Rensa aviserings funktionen för tjänst ändringar</span><span class="sxs-lookup"><span data-stu-id="0df71-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-404">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="0df71-405">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-405">Description</span></span>

<span data-ttu-id="0df71-406">Detta API rensar tjänst ändringen meddela motringning och.</span><span class="sxs-lookup"><span data-stu-id="0df71-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-407">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-407">Input Parameters</span></span>

- <span data-ttu-id="0df71-408">**mdns_ptr** Pekare till mDNS kontroll block..</span><span class="sxs-lookup"><span data-stu-id="0df71-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-409">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-409">Return Values</span></span>

- <span data-ttu-id="0df71-410">**NX_SUCCESS** (0x00) rensade återanrops funktionen.</span><span class="sxs-lookup"><span data-stu-id="0df71-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-411">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-411">Allowed From</span></span>

<span data-ttu-id="0df71-412">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-413">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="0df71-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="0df71-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="0df71-415">Hämta värd adressen</span><span class="sxs-lookup"><span data-stu-id="0df71-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-416">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0df71-417">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-417">Description</span></span>

<span data-ttu-id="0df71-418">Den här tjänsten utför en mDNS-fråga på värd-IPv4-och IPv6-adresser.</span><span class="sxs-lookup"><span data-stu-id="0df71-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="0df71-419">Om adressen för det angivna värd namnet finns i peer-tjänstecachen returneras adressen.</span><span class="sxs-lookup"><span data-stu-id="0df71-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="0df71-420">Om ingen adress hittas i peer-tjänstecachen, utfärdar mDNS-modulen en och AAAA-typfrågor och väntar på svar.</span><span class="sxs-lookup"><span data-stu-id="0df71-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="0df71-421">Detta API-block tills antingen ett svar tas emot eller tids gränsen för frågan har uppnåtts.</span><span class="sxs-lookup"><span data-stu-id="0df71-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-422">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-422">Input Parameters</span></span>

- <span data-ttu-id="0df71-423">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="0df71-424">**host_name** Pekare till värd namnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="0df71-425">**ipv4_address** Pekar på en 4-bytes justerad adress för IPv4-adress lagrings utrymme.</span><span class="sxs-lookup"><span data-stu-id="0df71-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="0df71-426">Användaren ska allokera 4 byte av utrymme för IPv4-adressen.</span><span class="sxs-lookup"><span data-stu-id="0df71-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="0df71-427">NX_NULL adress kan skickas till det här API: et om programmet inte behöver hämta IPv4-adressen.</span><span class="sxs-lookup"><span data-stu-id="0df71-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="0df71-428">**ipv6_address** Pekar på 4-bytes justerad adress för IPv6-adress lagrings utrymme.</span><span class="sxs-lookup"><span data-stu-id="0df71-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="0df71-429">Användaren tilldelas 16 bytes utrymme för-IPv6-adressen.</span><span class="sxs-lookup"><span data-stu-id="0df71-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="0df71-430">NX_NULL adress kan skickas till det här API: et om programmet inte behöver hämta IPv6-adressen.</span><span class="sxs-lookup"><span data-stu-id="0df71-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="0df71-431">**wait_option** Tiden, i Tick, för att vänta på ett svar.</span><span class="sxs-lookup"><span data-stu-id="0df71-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-432">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-432">Return Values</span></span>

- <span data-ttu-id="0df71-433">**NX_SUCCESS** (0x00) hämtade värd adressen.</span><span class="sxs-lookup"><span data-stu-id="0df71-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-434">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-434">Allowed From</span></span>

<span data-ttu-id="0df71-435">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-436">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="0df71-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="0df71-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="0df71-438">Radera alla lokala tjänster</span><span class="sxs-lookup"><span data-stu-id="0df71-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-439">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="0df71-440">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-440">Description</span></span>

<span data-ttu-id="0df71-441">Den här tjänsten rensar alla poster i den lokala tjänstecachen när meddelandet har skickats.</span><span class="sxs-lookup"><span data-stu-id="0df71-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-442">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-442">Input Parameters</span></span>

- <span data-ttu-id="0df71-443">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-444">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-444">Return Values</span></span>

- <span data-ttu-id="0df71-445">**NX_SUCCESS** (0x00) raderade alla poster i cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-446">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-446">Allowed From</span></span>

<span data-ttu-id="0df71-447">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-448">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="0df71-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="0df71-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="0df71-450">Radera alla identifierade tjänster</span><span class="sxs-lookup"><span data-stu-id="0df71-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="0df71-451">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0df71-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="0df71-452">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0df71-452">Description</span></span>

<span data-ttu-id="0df71-453">Den här tjänsten rensar alla poster i peer-tjänstecachen.</span><span class="sxs-lookup"><span data-stu-id="0df71-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df71-454">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0df71-454">Input Parameters</span></span>

- <span data-ttu-id="0df71-455">**mdns_ptr** Pekare till mDNS Control Block.</span><span class="sxs-lookup"><span data-stu-id="0df71-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df71-456">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0df71-456">Return Values</span></span>

- <span data-ttu-id="0df71-457">**NX_SUCCESS** (0x00) raderade alla poster i cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="0df71-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df71-458">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0df71-458">Allowed From</span></span>

<span data-ttu-id="0df71-459">Konversation</span><span class="sxs-lookup"><span data-stu-id="0df71-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df71-460">Exempel</span><span class="sxs-lookup"><span data-stu-id="0df71-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
