---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX AutoIP Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX AutoIP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826847"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a><span data-ttu-id="ebb5f-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX AutoIP Services</span><span class="sxs-lookup"><span data-stu-id="ebb5f-103">Chapter 3 - Description of Azure RTOS NetX AutoIP services</span></span>

<span data-ttu-id="ebb5f-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX AutoIP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-104">This chapter contains a description of all Azure RTOS NetX AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ebb5f-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ebb5f-106">**nx_auto_ip_create**: *skapa AutoIP-instans*</span><span class="sxs-lookup"><span data-stu-id="ebb5f-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="ebb5f-107">**nx_auto_ip_delete**: *ta bort AutoIP-instans*</span><span class="sxs-lookup"><span data-stu-id="ebb5f-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="ebb5f-108">**nx_auto_ip_get_address**: *Hämta aktuell AutoIP-adress*</span><span class="sxs-lookup"><span data-stu-id="ebb5f-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="ebb5f-109">**nx_auto_ip_set_interface**: *Ange IP-gränssnitt som behöver en AutoIP-adress*</span><span class="sxs-lookup"><span data-stu-id="ebb5f-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="ebb5f-110">**nx_auto_ip_start**: *Starta AutoIP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="ebb5f-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="ebb5f-111">**nx_auto_ip_stop**: *stoppa AutoIP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="ebb5f-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="ebb5f-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="ebb5f-112">nx_auto_ip_create</span></span>

<span data-ttu-id="ebb5f-113">Skapa AutoIP-instans</span><span class="sxs-lookup"><span data-stu-id="ebb5f-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ebb5f-114">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ebb5f-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a><span data-ttu-id="ebb5f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-115">Description</span></span>

<span data-ttu-id="ebb5f-116">Den här tjänsten skapar en AutoIP-instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

- <span data-ttu-id="ebb5f-117">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-117">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="ebb5f-118">**namn**: namnet på AutoIP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-118">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="ebb5f-119">**ip_ptr**: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-119">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="ebb5f-120">**stack_ptr**: pekar på AutoIP tråds tack yta.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-120">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="ebb5f-121">**stack_size**: storleken på AutoIP trådens stack Area.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-121">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="ebb5f-122">**prioritet**: prioriteten för AutoIP-tråden.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-122">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="ebb5f-123">Om DHCP används måste DHCP-tråden ha högre prioritet än IP-instansen och AutoIP-tråden.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-123">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ebb5f-124">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ebb5f-124">Return Values</span></span>

- <span data-ttu-id="ebb5f-125">**NX_SUCCESS**: (0X00) lyckades skapa AutoIP.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-125">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="ebb5f-126">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP skapa fel.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="ebb5f-127">NX_PTR_ERROR: (0x16) ogiltig AutoIP, ip_ptr eller stack pekare.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="ebb5f-128">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-128">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ebb5f-129">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ebb5f-129">Allowed From</span></span>

<span data-ttu-id="ebb5f-130">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-130">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ebb5f-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="ebb5f-131">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="ebb5f-132">Se även</span><span class="sxs-lookup"><span data-stu-id="ebb5f-132">See Also</span></span>

<span data-ttu-id="ebb5f-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="ebb5f-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="ebb5f-134">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="ebb5f-134">nx_auto_ip_delete</span></span>

<span data-ttu-id="ebb5f-135">Ta bort AutoIP-instans</span><span class="sxs-lookup"><span data-stu-id="ebb5f-135">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ebb5f-136">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ebb5f-136">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ebb5f-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-137">Description</span></span>

<span data-ttu-id="ebb5f-138">Den här tjänsten tar bort en tidigare skapad AutoIP-instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-138">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ebb5f-139">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-139">Input Parameters</span></span>

- <span data-ttu-id="ebb5f-140">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-140">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ebb5f-141">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ebb5f-141">Return Values</span></span>

- <span data-ttu-id="ebb5f-142">**NX_SUCCESS**: (0X00) lyckad AutoIP-borttagning.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-142">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="ebb5f-143">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP Delete-fel.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="ebb5f-144">NX_PTR_ERROR (0x16): ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-144">NX_PTR_ERROR (0x16): Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="ebb5f-145">NX_CALLER_ERROR (0x11): ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-145">NX_CALLER_ERROR (0x11): Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ebb5f-146">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ebb5f-146">Allowed From</span></span>

<span data-ttu-id="ebb5f-147">Konversation</span><span class="sxs-lookup"><span data-stu-id="ebb5f-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ebb5f-148">Exempel</span><span class="sxs-lookup"><span data-stu-id="ebb5f-148">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ebb5f-149">Se även</span><span class="sxs-lookup"><span data-stu-id="ebb5f-149">See Also</span></span>

<span data-ttu-id="ebb5f-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="ebb5f-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="ebb5f-151">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="ebb5f-151">nx_auto_ip_get_address</span></span>

<span data-ttu-id="ebb5f-152">Hämta aktuell AutoIP-adress</span><span class="sxs-lookup"><span data-stu-id="ebb5f-152">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ebb5f-153">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ebb5f-153">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="ebb5f-154">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-154">Description</span></span>

<span data-ttu-id="ebb5f-155">Den här tjänsten hämtar den aktuella AutoIP-adressen.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-155">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="ebb5f-156">Om det inte finns någon returneras en IP-adress 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-156">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ebb5f-157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-157">Input Parameters</span></span>

- <span data-ttu-id="ebb5f-158">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-158">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="ebb5f-159">**local_ip_address**: målet för retur-IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-159">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="ebb5f-160">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ebb5f-160">Return Values</span></span>

- <span data-ttu-id="ebb5f-161">**NX_SUCCESS**: (0X00) lyckad AutoIP-adress Hämta.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-161">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="ebb5f-162">**NX_AUTO_IP_NO_LOCAL**: (0XA01) ingen giltig AutoIP-adress.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="ebb5f-163">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-163">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="ebb5f-164">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-164">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ebb5f-165">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ebb5f-165">Allowed From</span></span>

<span data-ttu-id="ebb5f-166">Initiering, timers, trådar, ISR: er</span><span class="sxs-lookup"><span data-stu-id="ebb5f-166">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ebb5f-167">Exempel</span><span class="sxs-lookup"><span data-stu-id="ebb5f-167">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="ebb5f-168">Se även</span><span class="sxs-lookup"><span data-stu-id="ebb5f-168">See Also</span></span>

<span data-ttu-id="ebb5f-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="ebb5f-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="ebb5f-170">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="ebb5f-170">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="ebb5f-171">Ange nätverks gränssnitt för AutoIP</span><span class="sxs-lookup"><span data-stu-id="ebb5f-171">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="ebb5f-172">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ebb5f-172">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ebb5f-173">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-173">Description</span></span>

<span data-ttu-id="ebb5f-174">Den här tjänsten anger index för nätverks gränssnittets AutoIP som avsöker en IP-adress för nätverket.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-174">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="ebb5f-175">Standardvärdet är noll (det primära nätverks gränssnittet).</span><span class="sxs-lookup"><span data-stu-id="ebb5f-175">The default is zero (the primary network interface).</span></span> <span data-ttu-id="ebb5f-176">Gäller endast för multihomed-enheter.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-176">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ebb5f-177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-177">Input Parameters</span></span>

- <span data-ttu-id="ebb5f-178">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-178">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="ebb5f-179">**interface_index**: gränssnitt till avsökning av IP-adress för</span><span class="sxs-lookup"><span data-stu-id="ebb5f-179">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="ebb5f-180">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ebb5f-180">Return Values</span></span>

- <span data-ttu-id="ebb5f-181">**NX_SUCCESS**: (0X00) lyckad AutoIP-gränssnitts uppsättning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-181">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="ebb5f-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0XA02) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="ebb5f-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface</span></span> 
- <span data-ttu-id="ebb5f-183">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-183">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="ebb5f-184">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ebb5f-185">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ebb5f-185">Allowed From</span></span>

<span data-ttu-id="ebb5f-186">Initiering, timers, trådar, ISR: er</span><span class="sxs-lookup"><span data-stu-id="ebb5f-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ebb5f-187">Exempel</span><span class="sxs-lookup"><span data-stu-id="ebb5f-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a><span data-ttu-id="ebb5f-188">Se även</span><span class="sxs-lookup"><span data-stu-id="ebb5f-188">See Also</span></span>

<span data-ttu-id="ebb5f-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="ebb5f-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="ebb5f-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="ebb5f-190">nx_auto_ip_start</span></span>

<span data-ttu-id="ebb5f-191">Starta AutoIP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ebb5f-192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ebb5f-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="ebb5f-193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-193">Description</span></span>

<span data-ttu-id="ebb5f-194">Den här tjänsten startar AutoIP-protokollet på en tidigare skapad AutoIP-instans.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ebb5f-195">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-195">Input Parameters</span></span>

- <span data-ttu-id="ebb5f-196">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="ebb5f-197">**starting_local_address**: valfri start adress för AutoIP.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="ebb5f-198">Värdet IP_ADDRESS (0, 0, 0) anger att en slumpmässig AutoIP-adress ska härledas.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="ebb5f-199">Annars, om en giltig AutoIP-adress har angetts försöker NetX AutoIP tilldela adressen.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="ebb5f-200">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ebb5f-200">Return Values</span></span>

- <span data-ttu-id="ebb5f-201">**NX_SUCCESS**: (0X00) lyckades AutoIP-start.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="ebb5f-202">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP start fel.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="ebb5f-203">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="ebb5f-204">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ebb5f-205">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ebb5f-205">Allowed From</span></span>

<span data-ttu-id="ebb5f-206">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ebb5f-207">Exempel</span><span class="sxs-lookup"><span data-stu-id="ebb5f-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="ebb5f-208">Se även</span><span class="sxs-lookup"><span data-stu-id="ebb5f-208">See Also</span></span>

<span data-ttu-id="ebb5f-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="ebb5f-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="ebb5f-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="ebb5f-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="ebb5f-211">Stoppa AutoIP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ebb5f-212">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ebb5f-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ebb5f-213">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ebb5f-213">Description</span></span>

<span data-ttu-id="ebb5f-214">Den här tjänsten stoppar AutoIP-protokollet på en tidigare skapad och startad AutoIP-instans.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="ebb5f-215">Den här tjänsten används vanligt vis när IP-adressen ändras via DHCP eller manuellt till en icke-AutoIP adress.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ebb5f-216">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ebb5f-216">Input Parameters</span></span>

- <span data-ttu-id="ebb5f-217">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ebb5f-218">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ebb5f-218">Return Values</span></span>

- <span data-ttu-id="ebb5f-219">**NX_SUCCESS**: (0X00) lyckades AutoIP-stopp.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="ebb5f-220">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP Stop-fel.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="ebb5f-221">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="ebb5f-222">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ebb5f-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ebb5f-223">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ebb5f-223">Allowed From</span></span>

<span data-ttu-id="ebb5f-224">Konversation</span><span class="sxs-lookup"><span data-stu-id="ebb5f-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ebb5f-225">Exempel</span><span class="sxs-lookup"><span data-stu-id="ebb5f-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="ebb5f-226">Se även</span><span class="sxs-lookup"><span data-stu-id="ebb5f-226">See Also</span></span>

<span data-ttu-id="ebb5f-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="ebb5f-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>