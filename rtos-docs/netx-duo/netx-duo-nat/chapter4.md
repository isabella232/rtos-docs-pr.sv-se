---
title: Kapitel 4 – Beskrivning av NAT-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo NAT API-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825851"
---
# <a name="chapter-4---description-of-nat-services"></a><span data-ttu-id="7eee2-103">Kapitel 4 – Beskrivning av NAT-tjänster</span><span class="sxs-lookup"><span data-stu-id="7eee2-103">Chapter 4 - Description of NAT services</span></span>

<span data-ttu-id="7eee2-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo NAT API-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="7eee2-104">This chapter contains a description of all NetX Duo NAT API services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="7eee2-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="7eee2-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_nat_create"></a><span data-ttu-id="7eee2-106">nx_nat_create</span><span class="sxs-lookup"><span data-stu-id="7eee2-106">nx_nat_create</span></span>

<span data-ttu-id="7eee2-107">Skapa en NAT-server</span><span class="sxs-lookup"><span data-stu-id="7eee2-107">Create a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-108">Prototype</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a><span data-ttu-id="7eee2-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-109">Description</span></span>

<span data-ttu-id="7eee2-110">Den här tjänsten skapar en instans av NAT-servern.</span><span class="sxs-lookup"><span data-stu-id="7eee2-110">This service creates an instance of the NAT server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-111">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-111">Input Parameters</span></span>

- <span data-ttu-id="7eee2-112">**nat_ptr** Pekare till NAT-instans som ska skapas</span><span class="sxs-lookup"><span data-stu-id="7eee2-112">**nat_ptr** Pointer to NAT instance to create</span></span>
- <span data-ttu-id="7eee2-113">**Ip_ptr pekare** till IP-instans</span><span class="sxs-lookup"><span data-stu-id="7eee2-113">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="7eee2-114">**global_interface_index** Index till det globala nätverks gränssnittet</span><span class="sxs-lookup"><span data-stu-id="7eee2-114">**global_interface_index** Index to the global network interface</span></span>
- <span data-ttu-id="7eee2-115">**dynamic_cache_memory** Pekarens minnes yta i NAT-tabellen</span><span class="sxs-lookup"><span data-stu-id="7eee2-115">**dynamic_cache_memory** Pointer memory area to NAT table</span></span>
- <span data-ttu-id="7eee2-116">**dynamic_cache_size** Storlek på minnes området för NAT-tabell</span><span class="sxs-lookup"><span data-stu-id="7eee2-116">**dynamic_cache_size** Size of memory area for NAT table</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-117">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-117">Return Values</span></span>

- <span data-ttu-id="7eee2-118">**NX_SUCCESS** (0X00) NAT-servern har skapats</span><span class="sxs-lookup"><span data-stu-id="7eee2-118">**NX_SUCCESS** (0x00) NAT server successfully created</span></span>
- <span data-ttu-id="7eee2-119">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-119">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="7eee2-120">NX_NAT_PARAM_ERROR (0xD01) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-120">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>
- <span data-ttu-id="7eee2-121">NX_NAT_CACHE_ERROR (0xD02) ogiltig Indatatyp för cache pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-121">NX_NAT_CACHE_ERROR (0xD02) Invalid cache pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-122">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-122">Allowed From</span></span>

<span data-ttu-id="7eee2-123">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-123">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-124">Example</span></span>

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a><span data-ttu-id="7eee2-125">nx_nat_delete</span><span class="sxs-lookup"><span data-stu-id="7eee2-125">nx_nat_delete</span></span>

<span data-ttu-id="7eee2-126">Ta bort en NAT-server</span><span class="sxs-lookup"><span data-stu-id="7eee2-126">Delete a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-127">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-127">Prototype</span></span>

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="7eee2-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-128">Description</span></span>

<span data-ttu-id="7eee2-129">Den här tjänsten tar bort en tidigare skapad NAT-server.</span><span class="sxs-lookup"><span data-stu-id="7eee2-129">This service deletes a previously created NAT Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-130">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-130">Input Parameters</span></span>

- <span data-ttu-id="7eee2-131">**nat_ptr** Pekare till NAT-instans som ska tas bort</span><span class="sxs-lookup"><span data-stu-id="7eee2-131">**nat_ptr** Pointer to NAT instance to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-132">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-132">Return Values</span></span>

- <span data-ttu-id="7eee2-133">**NX_SUCCESS** (0X00) NAT har tagits bort</span><span class="sxs-lookup"><span data-stu-id="7eee2-133">**NX_SUCCESS** (0x00) NAT successfully deleted</span></span>
- <span data-ttu-id="7eee2-134">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-134">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-135">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-135">Allowed From</span></span>

<span data-ttu-id="7eee2-136">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-136">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-137">Example</span></span>

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a><span data-ttu-id="7eee2-138">nx_nat_enable</span><span class="sxs-lookup"><span data-stu-id="7eee2-138">nx_nat_enable</span></span>

<span data-ttu-id="7eee2-139">Aktivera IP-instansen för NAT</span><span class="sxs-lookup"><span data-stu-id="7eee2-139">Enable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-140">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-140">Prototype</span></span>

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="7eee2-141">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-141">Description</span></span>

<span data-ttu-id="7eee2-142">Den här tjänsten aktiverar IP-instansen för NAT (t. ex. vidarebefordrade paket till NAT-servern).</span><span class="sxs-lookup"><span data-stu-id="7eee2-142">This service enables the IP instance for NAT (e.g. forward received packets to the NAT server).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-143">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-143">Input Parameters</span></span>

- <span data-ttu-id="7eee2-144">**nat_ptr** Pekare till NAT-instans</span><span class="sxs-lookup"><span data-stu-id="7eee2-144">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-145">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-145">Return Values</span></span>

- <span data-ttu-id="7eee2-146">**NX_SUCCESS** (0X00) NAT har Aktiver ATS</span><span class="sxs-lookup"><span data-stu-id="7eee2-146">**NX_SUCCESS** (0x00) NAT successfully enabled</span></span>
- <span data-ttu-id="7eee2-147">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-147">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-148">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-148">Allowed From</span></span>

<span data-ttu-id="7eee2-149">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-149">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-150">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-150">Example</span></span>

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a><span data-ttu-id="7eee2-151">nx_nat_disable</span><span class="sxs-lookup"><span data-stu-id="7eee2-151">nx_nat_disable</span></span>

<span data-ttu-id="7eee2-152">Inaktivera IP-instansen för NAT</span><span class="sxs-lookup"><span data-stu-id="7eee2-152">Disable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-153">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-153">Prototype</span></span>

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="7eee2-154">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-154">Description</span></span>

<span data-ttu-id="7eee2-155">Den här tjänsten inaktiverar NAT på IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="7eee2-155">This service disables NAT on the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-156">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-156">Input Parameters</span></span>

- <span data-ttu-id="7eee2-157">**nat_ptr** Pekare till NAT-instans</span><span class="sxs-lookup"><span data-stu-id="7eee2-157">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-158">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-158">Return Values</span></span>

- <span data-ttu-id="7eee2-159">**NX_SUCCESS** (0X00) NAT har inaktiverats</span><span class="sxs-lookup"><span data-stu-id="7eee2-159">**NX_SUCCESS** (0x00) NAT successfully disabled</span></span>
- <span data-ttu-id="7eee2-160">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-160">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-161">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-161">Allowed From</span></span>

<span data-ttu-id="7eee2-162">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-162">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-163">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-163">Example</span></span>

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a><span data-ttu-id="7eee2-164">nx_nat_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="7eee2-164">nx_nat_cache_notify_set</span></span>

<span data-ttu-id="7eee2-165">Ange en cache fullständig notify motringnings funktion</span><span class="sxs-lookup"><span data-stu-id="7eee2-165">Set a cache full notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-166">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-166">Prototype</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a><span data-ttu-id="7eee2-167">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-167">Description</span></span>

<span data-ttu-id="7eee2-168">Den här tjänsten registrerar cachen med fullständig motringning med indata-funktionen pekare cache_full_notify_cb som pekar på en användardefinierad cache fullständig meddelande funktion.</span><span class="sxs-lookup"><span data-stu-id="7eee2-168">This service registers the cache full callback with the input function pointer cache_full_notify_cb which points to a user defined cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-169">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-169">Input Parameters</span></span>

- <span data-ttu-id="7eee2-170">**nat_ptr** Pekare till NAT-instans</span><span class="sxs-lookup"><span data-stu-id="7eee2-170">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="7eee2-171">**cache_full_notify_cb** Pekare för att cachelagra fullständig Avisera-funktion</span><span class="sxs-lookup"><span data-stu-id="7eee2-171">**cache_full_notify_cb** Pointer to cache full notify function</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-172">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-172">Return Values</span></span>

- <span data-ttu-id="7eee2-173">**NX_SUCCESS** (0X00) cache fullständig aviserings funktion har angetts</span><span class="sxs-lookup"><span data-stu-id="7eee2-173">**NX_SUCCESS** (0x00) Cache full notify function successfully set</span></span>
- <span data-ttu-id="7eee2-174">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-174">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="7eee2-175">NX_NAT_PARAM_ERROR (0xD01) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-175">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-176">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-176">Allowed From</span></span>

<span data-ttu-id="7eee2-177">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-177">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-178">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-178">Example</span></span>

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a><span data-ttu-id="7eee2-179">nx_nat_inbound_entry_create</span><span class="sxs-lookup"><span data-stu-id="7eee2-179">nx_nat_inbound_entry_create</span></span>

<span data-ttu-id="7eee2-180">Skapa en inkommande post i översättnings tabellen för NAT</span><span class="sxs-lookup"><span data-stu-id="7eee2-180">Create an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-181">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-181">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a><span data-ttu-id="7eee2-182">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-182">Description</span></span>

<span data-ttu-id="7eee2-183">Den här tjänsten skapar en inkommande post som statisk (permanent post, upphör aldrig att gälla) och lägger till den i översättnings tabellen NAT.</span><span class="sxs-lookup"><span data-stu-id="7eee2-183">This service creates an inbound entry as static (permanent entry, never expires) and adds it to the NAT translation table.</span></span> <span data-ttu-id="7eee2-184">Dessa poster skapas vanligt vis för lokala värd servrar där en anslutning initieras från en värd i nätverket utanför nätverket.</span><span class="sxs-lookup"><span data-stu-id="7eee2-184">These entries are usually created for local host servers where a connection is initiated from a host on the outside network.</span></span> <span data-ttu-id="7eee2-185">NAT-servern kontrollerar att den externa porten inte redan används i översättnings tabellen eller bundits av en tidigare befintlig NetX Duo-socket av samma protokoll.</span><span class="sxs-lookup"><span data-stu-id="7eee2-185">The NAT server checks that the external port is not already in use in the translation table or bound by a previously existing NetX Duo socket of the same protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-186">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-186">Input Parameters</span></span>

- <span data-ttu-id="7eee2-187">**nat_ptr** Pekare till NAT-instans</span><span class="sxs-lookup"><span data-stu-id="7eee2-187">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="7eee2-188">**entry_ptr** Pekare till översättnings post</span><span class="sxs-lookup"><span data-stu-id="7eee2-188">**entry_ptr** Pointer to translation entry</span></span>
- <span data-ttu-id="7eee2-189">**local_ip_address** IP-adress för lokal värd</span><span class="sxs-lookup"><span data-stu-id="7eee2-189">**local_ip_address** Local host IP address</span></span>
- <span data-ttu-id="7eee2-190">**external_port** Mål port på det externa nätverket</span><span class="sxs-lookup"><span data-stu-id="7eee2-190">**external_port** Destination port on the external network</span></span>
- <span data-ttu-id="7eee2-191">**local_port** Käll port (lokal värd)</span><span class="sxs-lookup"><span data-stu-id="7eee2-191">**local_port** Source (local host) port</span></span>
- <span data-ttu-id="7eee2-192">**protokoll** Paket protokoll (t. ex. TCP)</span><span class="sxs-lookup"><span data-stu-id="7eee2-192">**protocol** Packet protocol (e.g TCP)</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-193">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-193">Return Values</span></span>

- <span data-ttu-id="7eee2-194">**NX_SUCCESS** (0x00) har skapats</span><span class="sxs-lookup"><span data-stu-id="7eee2-194">**NX_SUCCESS** (0x00) Entry successfully created</span></span>
- <span data-ttu-id="7eee2-195">**NX_NAT_PORT_UNAVAILABLE** (0XD0D) ogiltig extern port</span><span class="sxs-lookup"><span data-stu-id="7eee2-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) Invalid external port</span></span>
- <span data-ttu-id="7eee2-196">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-196">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="7eee2-197">NX_NAT_PARAM_ERROR (0xD01) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-197">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-198">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-198">Allowed From</span></span>

<span data-ttu-id="7eee2-199">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-199">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-200">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-200">Example</span></span>

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a><span data-ttu-id="7eee2-201">nx_nat_inbound_entry_delete</span><span class="sxs-lookup"><span data-stu-id="7eee2-201">nx_nat_inbound_entry_delete</span></span>

<span data-ttu-id="7eee2-202">Ta bort en inkommande post i översättnings tabellen för NAT</span><span class="sxs-lookup"><span data-stu-id="7eee2-202">Delete an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="7eee2-203">Prototyp</span><span class="sxs-lookup"><span data-stu-id="7eee2-203">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a><span data-ttu-id="7eee2-204">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7eee2-204">Description</span></span>

<span data-ttu-id="7eee2-205">Den här tjänsten tar bort den angivna inkommande posten från översättnings tabellen.</span><span class="sxs-lookup"><span data-stu-id="7eee2-205">This service deletes the specified inbound entry from the translation table.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7eee2-206">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="7eee2-206">Input Parameters</span></span>

- <span data-ttu-id="7eee2-207">**nat_ptr** Pekare till NAT-instans</span><span class="sxs-lookup"><span data-stu-id="7eee2-207">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="7eee2-208">**delete_entry_ptr** Pekare till översättnings posten NAT</span><span class="sxs-lookup"><span data-stu-id="7eee2-208">**delete_entry_ptr** Pointer to the NAT translation entry</span></span>

### <a name="return-values"></a><span data-ttu-id="7eee2-209">Retur värden</span><span class="sxs-lookup"><span data-stu-id="7eee2-209">Return Values</span></span>

- <span data-ttu-id="7eee2-210">**NX_SUCCESS** (0x00) har tagits bort</span><span class="sxs-lookup"><span data-stu-id="7eee2-210">**NX_SUCCESS** (0x00) Entry successfully deleted</span></span>
- <span data-ttu-id="7eee2-211">Det gick inte att hitta **NX_NAT_ENTRY_NOT_FOUND** (0xD04)-posten</span><span class="sxs-lookup"><span data-stu-id="7eee2-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entry does not found</span></span>
- <span data-ttu-id="7eee2-212">NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare</span><span class="sxs-lookup"><span data-stu-id="7eee2-212">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="7eee2-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) ogiltig översättnings typ</span><span class="sxs-lookup"><span data-stu-id="7eee2-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Invalid translation type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7eee2-214">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="7eee2-214">Allowed From</span></span>

<span data-ttu-id="7eee2-215">Program kod</span><span class="sxs-lookup"><span data-stu-id="7eee2-215">Application code</span></span>

### <a name="example"></a><span data-ttu-id="7eee2-216">Exempel</span><span class="sxs-lookup"><span data-stu-id="7eee2-216">Example</span></span>

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
