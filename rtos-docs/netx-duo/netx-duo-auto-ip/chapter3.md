---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo AutoIP Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo AutoIP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826166"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="636f2-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo AutoIP Services</span><span class="sxs-lookup"><span data-stu-id="636f2-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="636f2-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo AutoIP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="636f2-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="636f2-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="636f2-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="636f2-106">**nx_auto_ip_create**: *skapa AutoIP-instans*</span><span class="sxs-lookup"><span data-stu-id="636f2-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="636f2-107">**nx_auto_ip_delete**: *ta bort AutoIP-instans*</span><span class="sxs-lookup"><span data-stu-id="636f2-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="636f2-108">**nx_auto_ip_get_address**: *Hämta aktuell AutoIP-adress*</span><span class="sxs-lookup"><span data-stu-id="636f2-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="636f2-109">**nx_auto_ip_set_interface**: *Ange IP-gränssnitt som behöver en AutoIP-adress*</span><span class="sxs-lookup"><span data-stu-id="636f2-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="636f2-110">**nx_auto_ip_start**: *Starta AutoIP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="636f2-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="636f2-111">**nx_auto_ip_stop**: *stoppa AutoIP-bearbetning*</span><span class="sxs-lookup"><span data-stu-id="636f2-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="636f2-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="636f2-112">nx_auto_ip_create</span></span>

<span data-ttu-id="636f2-113">Skapa AutoIP-instans</span><span class="sxs-lookup"><span data-stu-id="636f2-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="636f2-114">Prototyp</span><span class="sxs-lookup"><span data-stu-id="636f2-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="636f2-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="636f2-115">Description</span></span>

<span data-ttu-id="636f2-116">Den här tjänsten skapar en AutoIP-instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="636f2-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="636f2-117">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="636f2-117">Input Parameters</span></span>

- <span data-ttu-id="636f2-118">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="636f2-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="636f2-119">**namn**: namnet på AutoIP-instansen.</span><span class="sxs-lookup"><span data-stu-id="636f2-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="636f2-120">**ip_ptr**: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="636f2-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="636f2-121">**stack_ptr**: pekar på AutoIP tråds tack yta.</span><span class="sxs-lookup"><span data-stu-id="636f2-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="636f2-122">**stack_size**: storleken på AutoIP trådens stack Area.</span><span class="sxs-lookup"><span data-stu-id="636f2-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="636f2-123">**prioritet**: prioriteten för AutoIP-tråden.</span><span class="sxs-lookup"><span data-stu-id="636f2-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="636f2-124">Om DHCP används måste DHCP-tråden ha högre prioritet än IP-instansen och AutoIP-tråden.</span><span class="sxs-lookup"><span data-stu-id="636f2-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="636f2-125">Retur värden</span><span class="sxs-lookup"><span data-stu-id="636f2-125">Return Values</span></span>

- <span data-ttu-id="636f2-126">**NX_SUCCESS**: (0X00) lyckades skapa AutoIP.</span><span class="sxs-lookup"><span data-stu-id="636f2-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="636f2-127">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP skapa fel.</span><span class="sxs-lookup"><span data-stu-id="636f2-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="636f2-128">NX_PTR_ERROR: (0x16) ogiltig AutoIP, ip_ptr eller stack pekare.</span><span class="sxs-lookup"><span data-stu-id="636f2-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="636f2-129">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="636f2-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="636f2-130">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="636f2-130">Allowed From</span></span>

<span data-ttu-id="636f2-131">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="636f2-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="636f2-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="636f2-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="636f2-133">Se även</span><span class="sxs-lookup"><span data-stu-id="636f2-133">See Also</span></span>

<span data-ttu-id="636f2-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="636f2-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="636f2-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="636f2-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="636f2-136">Ta bort AutoIP-instans</span><span class="sxs-lookup"><span data-stu-id="636f2-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="636f2-137">Prototyp</span><span class="sxs-lookup"><span data-stu-id="636f2-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="636f2-138">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="636f2-138">Description</span></span>

<span data-ttu-id="636f2-139">Den här tjänsten tar bort en tidigare skapad AutoIP-instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="636f2-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="636f2-140">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="636f2-140">Input Parameters</span></span>

- <span data-ttu-id="636f2-141">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="636f2-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="636f2-142">Retur värden</span><span class="sxs-lookup"><span data-stu-id="636f2-142">Return Values</span></span>

- <span data-ttu-id="636f2-143">**NX_SUCCESS**: (0X00) lyckad AutoIP-borttagning.</span><span class="sxs-lookup"><span data-stu-id="636f2-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="636f2-144">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP Delete-fel.</span><span class="sxs-lookup"><span data-stu-id="636f2-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="636f2-145">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="636f2-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="636f2-146">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="636f2-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="636f2-147">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="636f2-147">Allowed From</span></span>

<span data-ttu-id="636f2-148">Konversation</span><span class="sxs-lookup"><span data-stu-id="636f2-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="636f2-149">Exempel</span><span class="sxs-lookup"><span data-stu-id="636f2-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="636f2-150">Se även</span><span class="sxs-lookup"><span data-stu-id="636f2-150">See Also</span></span>

<span data-ttu-id="636f2-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="636f2-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="636f2-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="636f2-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="636f2-153">Hämta aktuell AutoIP-adress</span><span class="sxs-lookup"><span data-stu-id="636f2-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="636f2-154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="636f2-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="636f2-155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="636f2-155">Description</span></span>

<span data-ttu-id="636f2-156">Den här tjänsten hämtar den aktuella AutoIP-adressen.</span><span class="sxs-lookup"><span data-stu-id="636f2-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="636f2-157">Om det inte finns någon returneras en IP-adress 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="636f2-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="636f2-158">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="636f2-158">Input Parameters</span></span>

- <span data-ttu-id="636f2-159">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="636f2-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="636f2-160">**local_ip_address**: målet för retur-IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="636f2-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="636f2-161">Retur värden</span><span class="sxs-lookup"><span data-stu-id="636f2-161">Return Values</span></span>

- <span data-ttu-id="636f2-162">**NX_SUCCESS**: (0X00) lyckad AutoIP-adress Hämta.</span><span class="sxs-lookup"><span data-stu-id="636f2-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="636f2-163">**NX_AUTO_IP_NO_LOCAL**: (0XA01) ingen giltig AutoIP-adress.</span><span class="sxs-lookup"><span data-stu-id="636f2-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="636f2-164">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="636f2-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="636f2-165">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="636f2-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="636f2-166">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="636f2-166">Allowed From</span></span>

<span data-ttu-id="636f2-167">Initiering, timers, trådar, ISR: er</span><span class="sxs-lookup"><span data-stu-id="636f2-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="636f2-168">Exempel</span><span class="sxs-lookup"><span data-stu-id="636f2-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="636f2-169">Se även</span><span class="sxs-lookup"><span data-stu-id="636f2-169">See Also</span></span>

<span data-ttu-id="636f2-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="636f2-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="636f2-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="636f2-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="636f2-172">Ange nätverks gränssnitt för AutoIP</span><span class="sxs-lookup"><span data-stu-id="636f2-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="636f2-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="636f2-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="636f2-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="636f2-174">Description</span></span>

<span data-ttu-id="636f2-175">Den här tjänsten anger index för nätverks gränssnittets AutoIP som avsöker en IP-adress för nätverket.</span><span class="sxs-lookup"><span data-stu-id="636f2-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="636f2-176">Standardvärdet är noll (det primära nätverks gränssnittet).</span><span class="sxs-lookup"><span data-stu-id="636f2-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="636f2-177">Gäller endast för multihomed-enheter.</span><span class="sxs-lookup"><span data-stu-id="636f2-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="636f2-178">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="636f2-178">Input Parameters</span></span>

- <span data-ttu-id="636f2-179">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="636f2-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="636f2-180">**interface_index**: gränssnitt till avsökning av IP-adress för</span><span class="sxs-lookup"><span data-stu-id="636f2-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="636f2-181">Retur värden</span><span class="sxs-lookup"><span data-stu-id="636f2-181">Return Values</span></span>

- <span data-ttu-id="636f2-182">**NX_SUCCESS**: (0X00) lyckad AutoIP-gränssnitts uppsättning</span><span class="sxs-lookup"><span data-stu-id="636f2-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="636f2-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0XA02) ogiltigt nätverks gränssnitt NX_PTR_ERROR (0X16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="636f2-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="636f2-184">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="636f2-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="636f2-185">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="636f2-185">Allowed From</span></span>

<span data-ttu-id="636f2-186">Initiering, timers, trådar, ISR: er</span><span class="sxs-lookup"><span data-stu-id="636f2-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="636f2-187">Exempel</span><span class="sxs-lookup"><span data-stu-id="636f2-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="636f2-188">Se även</span><span class="sxs-lookup"><span data-stu-id="636f2-188">See Also</span></span>

<span data-ttu-id="636f2-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="636f2-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="636f2-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="636f2-190">nx_auto_ip_start</span></span>

<span data-ttu-id="636f2-191">Starta AutoIP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="636f2-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="636f2-192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="636f2-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="636f2-193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="636f2-193">Description</span></span>

<span data-ttu-id="636f2-194">Den här tjänsten startar AutoIP-protokollet på en tidigare skapad AutoIP-instans.</span><span class="sxs-lookup"><span data-stu-id="636f2-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="636f2-195">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="636f2-195">Input Parameters</span></span>

- <span data-ttu-id="636f2-196">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="636f2-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="636f2-197">**starting_local_address**: valfri start adress för AutoIP.</span><span class="sxs-lookup"><span data-stu-id="636f2-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="636f2-198">Värdet IP_ADDRESS (0, 0, 0) anger att en slumpmässig AutoIP-adress ska härledas.</span><span class="sxs-lookup"><span data-stu-id="636f2-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="636f2-199">Annars, om en giltig AutoIP-adress har angetts försöker NetX AutoIP tilldela adressen.</span><span class="sxs-lookup"><span data-stu-id="636f2-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="636f2-200">Retur värden</span><span class="sxs-lookup"><span data-stu-id="636f2-200">Return Values</span></span>

- <span data-ttu-id="636f2-201">**NX_SUCCESS**: (0X00) lyckades AutoIP-start.</span><span class="sxs-lookup"><span data-stu-id="636f2-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="636f2-202">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP start fel.</span><span class="sxs-lookup"><span data-stu-id="636f2-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="636f2-203">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="636f2-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="636f2-204">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="636f2-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="636f2-205">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="636f2-205">Allowed From</span></span>

<span data-ttu-id="636f2-206">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="636f2-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="636f2-207">Exempel</span><span class="sxs-lookup"><span data-stu-id="636f2-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="636f2-208">Se även</span><span class="sxs-lookup"><span data-stu-id="636f2-208">See Also</span></span>

<span data-ttu-id="636f2-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="636f2-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="636f2-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="636f2-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="636f2-211">Stoppa AutoIP-bearbetning</span><span class="sxs-lookup"><span data-stu-id="636f2-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="636f2-212">Prototyp</span><span class="sxs-lookup"><span data-stu-id="636f2-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="636f2-213">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="636f2-213">Description</span></span>

<span data-ttu-id="636f2-214">Den här tjänsten stoppar AutoIP-protokollet på en tidigare skapad och startad AutoIP-instans.</span><span class="sxs-lookup"><span data-stu-id="636f2-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="636f2-215">Den här tjänsten används vanligt vis när IP-adressen ändras via DHCP eller manuellt till en icke-AutoIP adress.</span><span class="sxs-lookup"><span data-stu-id="636f2-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="636f2-216">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="636f2-216">Input Parameters</span></span>

- <span data-ttu-id="636f2-217">**auto_ip_ptr**: pekare till AutoIP Control Block.</span><span class="sxs-lookup"><span data-stu-id="636f2-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="636f2-218">Retur värden</span><span class="sxs-lookup"><span data-stu-id="636f2-218">Return Values</span></span>

- <span data-ttu-id="636f2-219">**NX_SUCCESS**: (0X00) lyckades AutoIP-stopp.</span><span class="sxs-lookup"><span data-stu-id="636f2-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="636f2-220">**NX_AUTO_IP_ERROR**: (0XA00) AutoIP Stop-fel.</span><span class="sxs-lookup"><span data-stu-id="636f2-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="636f2-221">NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.</span><span class="sxs-lookup"><span data-stu-id="636f2-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="636f2-222">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="636f2-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="636f2-223">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="636f2-223">Allowed From</span></span>

<span data-ttu-id="636f2-224">Konversation</span><span class="sxs-lookup"><span data-stu-id="636f2-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="636f2-225">Exempel</span><span class="sxs-lookup"><span data-stu-id="636f2-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="636f2-226">Se även</span><span class="sxs-lookup"><span data-stu-id="636f2-226">See Also</span></span>

<span data-ttu-id="636f2-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="636f2-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>