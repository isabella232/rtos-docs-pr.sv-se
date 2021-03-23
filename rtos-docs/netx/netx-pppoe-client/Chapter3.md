---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825590"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="acd16-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Client Services</span><span class="sxs-lookup"><span data-stu-id="acd16-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="acd16-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE-klienttjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="acd16-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="acd16-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="acd16-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="acd16-106">**nx_pppoe_client_create** *skapa en PPPoE-klient instans*</span><span class="sxs-lookup"><span data-stu-id="acd16-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="acd16-107">**nx_pppoe_client_delete** *ta bort en PPPoE-klient instans*</span><span class="sxs-lookup"><span data-stu-id="acd16-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="acd16-108">**nx_pppoe_client_host_uniq_set** *Ange värden som unik för PPPoE-klienten*</span><span class="sxs-lookup"><span data-stu-id="acd16-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="acd16-109">**nx_pppoe_client_host_uniq_set_extended** *Ange värden som unik för PPPoE-klienten*</span><span class="sxs-lookup"><span data-stu-id="acd16-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="acd16-110">**nx_pppoe_client_service_name_set** *Ange tjänst namnet för PPPoE-klienten*</span><span class="sxs-lookup"><span data-stu-id="acd16-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="acd16-111">**nx_pppoe_client_service_name_set_extended** *Ange tjänst namnet för PPPoE-klienten*</span><span class="sxs-lookup"><span data-stu-id="acd16-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="acd16-112">**nx_pppoe_client_session_connect** *ansluta PPPoE-klientsessionen till PPPoE-servern*</span><span class="sxs-lookup"><span data-stu-id="acd16-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="acd16-113">**nx_pppoe_client_session_packet_send** *Skicka PPPoE-session paket*</span><span class="sxs-lookup"><span data-stu-id="acd16-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="acd16-114">**nx_pppoe_client_session_terminate** *Avsluta PPPoE-sessionen*</span><span class="sxs-lookup"><span data-stu-id="acd16-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="acd16-115">**nx_pppoe_client_session_get** *Hämta den angivna INF-filen för PPPoE-sessionen*</span><span class="sxs-lookup"><span data-stu-id="acd16-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="acd16-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="acd16-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="acd16-117">Skapa en PPPoE-klient instans</span><span class="sxs-lookup"><span data-stu-id="acd16-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-118">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="acd16-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-119">Description</span></span>

<span data-ttu-id="acd16-120">Den här tjänsten skapar en PPPoE-klient instans med den angivna länk driv rutinen för den angivna NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="acd16-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="acd16-121">Om länk driv rutinen inte har initierats, och Aktiver ATS, ansvarar PPPoE-klientprogrammet för att initiera länk driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="acd16-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="acd16-122">Dessutom måste programmet ange en tidigare skapad modempool för den PPPoE-klient instans som ska användas för intern paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="acd16-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-123">I allmänhet är det en bra idé att skapa en NetX IP-tråd med högre prioritet än PPPoE-klientens tråd prioritet.</span><span class="sxs-lookup"><span data-stu-id="acd16-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="acd16-124">Mer information om hur du anger prioritet för IP-tråd finns i *nx_ip_create* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="acd16-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-125">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-125">Input Parameters</span></span>

 - <span data-ttu-id="acd16-126">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-127">**namn** Namnet på den här PPPoE-klient instansen.</span><span class="sxs-lookup"><span data-stu-id="acd16-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="acd16-128">**ip_ptr** Pekare som styr blockering av IP-instans.</span><span class="sxs-lookup"><span data-stu-id="acd16-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="acd16-129">**interface_index** Gränssnitts index.</span><span class="sxs-lookup"><span data-stu-id="acd16-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="acd16-130">**pool_ptr** Pekare till Packet bassäng.</span><span class="sxs-lookup"><span data-stu-id="acd16-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="acd16-131">**stack_ptr** Pekare för start av PPPoE-klient trådens stack Area.</span><span class="sxs-lookup"><span data-stu-id="acd16-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="acd16-132">**stack_size** Storlek i byte i trådens stack.</span><span class="sxs-lookup"><span data-stu-id="acd16-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="acd16-133">**prioritet** Prioritet för interna PPPoE-klient trådar (1-31).</span><span class="sxs-lookup"><span data-stu-id="acd16-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="acd16-134">**pppoe_link_driver** Användarens angivna länk driv rutin.</span><span class="sxs-lookup"><span data-stu-id="acd16-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="acd16-135">**pppoe_packet_receive** Användare som har fått funktionen paket mottagning.</span><span class="sxs-lookup"><span data-stu-id="acd16-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-136">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-136">Return Values</span></span>

 - <span data-ttu-id="acd16-137">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klient skapa.</span><span class="sxs-lookup"><span data-stu-id="acd16-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="acd16-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient, IP, paket bassäng eller stack pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="acd16-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) ogiltigt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="acd16-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="acd16-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) ogiltig nytto Last storlek för Packet bassäng.</span><span class="sxs-lookup"><span data-stu-id="acd16-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="acd16-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) ogiltig minnes storlek.</span><span class="sxs-lookup"><span data-stu-id="acd16-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="acd16-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) ogiltig prioritet för PPPoE-klient tråd.</span><span class="sxs-lookup"><span data-stu-id="acd16-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-143">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-143">Allowed From</span></span>

<span data-ttu-id="acd16-144">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="acd16-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="acd16-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="acd16-147">Ta bort en PPPoE-klient instans</span><span class="sxs-lookup"><span data-stu-id="acd16-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-148">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="acd16-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-149">Description</span></span>

<span data-ttu-id="acd16-150">Den här tjänsten tar bort den tidigare skapade PPPoE-klienten.</span><span class="sxs-lookup"><span data-stu-id="acd16-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-151">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-151">Input Parameters</span></span>

 - <span data-ttu-id="acd16-152">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block</span><span class="sxs-lookup"><span data-stu-id="acd16-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-153">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-153">Return Values</span></span>

 - <span data-ttu-id="acd16-154">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad borttagning av PPPoE-klienten.</span><span class="sxs-lookup"><span data-stu-id="acd16-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="acd16-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-156">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-156">Allowed From</span></span>

<span data-ttu-id="acd16-157">Konversation</span><span class="sxs-lookup"><span data-stu-id="acd16-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-158">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="acd16-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="acd16-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="acd16-160">Ange unik värd för PPPoE-klienten</span><span class="sxs-lookup"><span data-stu-id="acd16-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="acd16-162">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-162">Description</span></span>

<span data-ttu-id="acd16-163">Den här tjänsten anger en unik PPPoE-klient värd.</span><span class="sxs-lookup"><span data-stu-id="acd16-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="acd16-164">Host-Uniq används av en värd för att unikt koppla en åtkomst-koncentrator till en viss värd förfrågan.</span><span class="sxs-lookup"><span data-stu-id="acd16-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="acd16-165">Det kan vara binära data för alla värden och längden som värden väljer.</span><span class="sxs-lookup"><span data-stu-id="acd16-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-166">värdens unika måste vara null-terminerad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-167">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="acd16-167">This service is deprecated.</span></span> <span data-ttu-id="acd16-168">Utvecklare uppmanas att migrera till *nx_pppoe_client_host_uniq_set_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="acd16-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-169">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-169">Input Parameters</span></span>

 - <span data-ttu-id="acd16-170">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-171">**host_uniq** Pekar till en värd unik.</span><span class="sxs-lookup"><span data-stu-id="acd16-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="acd16-172">Värdens unika måste vara null-terminerad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-173">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-173">Return Values</span></span>

 - <span data-ttu-id="acd16-174">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad konfiguration av en unik PPPoE-klient värd.</span><span class="sxs-lookup"><span data-stu-id="acd16-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="acd16-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-176">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-176">Allowed From</span></span>

<span data-ttu-id="acd16-177">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-178">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="acd16-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="acd16-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="acd16-180">Ange unik värd för PPPoE-klienten</span><span class="sxs-lookup"><span data-stu-id="acd16-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-181">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="acd16-182">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-182">Description</span></span>

<span data-ttu-id="acd16-183">Den här tjänsten anger en unik PPPoE-klient värd.</span><span class="sxs-lookup"><span data-stu-id="acd16-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="acd16-184">Host-Uniq används av en värd för att unikt koppla en åtkomst-koncentrator till en viss värd förfrågan.</span><span class="sxs-lookup"><span data-stu-id="acd16-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="acd16-185">Det kan vara binära data för alla värden och längden som värden väljer.</span><span class="sxs-lookup"><span data-stu-id="acd16-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-186">värdens unika måste vara null-terminerad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-187">Den här tjänsten ersätter *nx_pppoe_client_host_uniq_set ()*.</span><span class="sxs-lookup"><span data-stu-id="acd16-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="acd16-188">Den här versionen tillhandahåller ytterligare längd information till tjänsten.</span><span class="sxs-lookup"><span data-stu-id="acd16-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-189">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-189">Input Parameters</span></span>

 - <span data-ttu-id="acd16-190">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-191">**host_uniq** Pekar till en värd unik.</span><span class="sxs-lookup"><span data-stu-id="acd16-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="acd16-192">Värdens unika måste vara null-terminerad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="acd16-193">**host_uniq_length** Host_uniq längd</span><span class="sxs-lookup"><span data-stu-id="acd16-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-194">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-194">Return Values</span></span>

 - <span data-ttu-id="acd16-195">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad konfiguration av en unik PPPoE-klient värd.</span><span class="sxs-lookup"><span data-stu-id="acd16-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="acd16-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="acd16-197">**NX_SIZE_ERROR** (0X09) kontrol lera host_uniq_length inte</span><span class="sxs-lookup"><span data-stu-id="acd16-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-198">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-198">Allowed From</span></span>

<span data-ttu-id="acd16-199">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-200">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="acd16-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="acd16-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="acd16-202">Ange PPPoE-klientens tjänst namn</span><span class="sxs-lookup"><span data-stu-id="acd16-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-203">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="acd16-204">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-204">Description</span></span>

<span data-ttu-id="acd16-205">Den här tjänsten anger PPPoE-klientens tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="acd16-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="acd16-206">Service-Name som indikerar den tjänst som värden begär.</span><span class="sxs-lookup"><span data-stu-id="acd16-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="acd16-207">Om Service-Name inte är inställt, anger värden att antalet tjänster ska accepteras.</span><span class="sxs-lookup"><span data-stu-id="acd16-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-208">tjänst namnet måste vara null-avslutad sträng</span><span class="sxs-lookup"><span data-stu-id="acd16-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-209">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="acd16-209">This service is deprecated.</span></span> <span data-ttu-id="acd16-210">Utvecklare uppmanas att migrera till *nx_pppoe_client_service_name_set_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="acd16-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-211">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-211">Input Parameters</span></span>

 - <span data-ttu-id="acd16-212">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-213">**SERVICE_NAME** Pekar till ett tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="acd16-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="acd16-214">Tjänst namnet måste vara null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-215">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-215">Return Values</span></span>

 - <span data-ttu-id="acd16-216">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klient tjänst namn angavs.</span><span class="sxs-lookup"><span data-stu-id="acd16-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="acd16-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-218">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-218">Allowed From</span></span>

<span data-ttu-id="acd16-219">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-220">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="acd16-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="acd16-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="acd16-222">Ange PPPoE-klientens tjänst namn</span><span class="sxs-lookup"><span data-stu-id="acd16-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-223">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="acd16-224">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-224">Description</span></span>

<span data-ttu-id="acd16-225">Den här tjänsten anger PPPoE-klientens tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="acd16-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="acd16-226">Service-Name som indikerar den tjänst som värden begär.</span><span class="sxs-lookup"><span data-stu-id="acd16-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="acd16-227">Om Service-Name inte är inställt, anger värden att antalet tjänster ska accepteras.</span><span class="sxs-lookup"><span data-stu-id="acd16-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-228">tjänst namnet måste vara null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-229">Den här tjänsten ersätter *nx_pppoe_client_service_name_set ()*.</span><span class="sxs-lookup"><span data-stu-id="acd16-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="acd16-230">Den här versionen tillhandahåller ytterligare information om tjänst namnens längd till funktionen.</span><span class="sxs-lookup"><span data-stu-id="acd16-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-231">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-231">Input Parameters</span></span>

 - <span data-ttu-id="acd16-232">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-233">**SERVICE_NAME** Pekar till ett tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="acd16-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="acd16-234">Tjänst namnet måste vara null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="acd16-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="acd16-235">**service_name_length** Service_name längd</span><span class="sxs-lookup"><span data-stu-id="acd16-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-236">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-236">Return Values</span></span>

 - <span data-ttu-id="acd16-237">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klient tjänst namn angavs.</span><span class="sxs-lookup"><span data-stu-id="acd16-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="acd16-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0XD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="acd16-239">**NX_SIZE_ERROR** (0X09) kontrol lera service_name_length inte</span><span class="sxs-lookup"><span data-stu-id="acd16-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-240">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-240">Allowed From</span></span>

<span data-ttu-id="acd16-241">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-242">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="acd16-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="acd16-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="acd16-244">Ansluta PPPoE-klientsession</span><span class="sxs-lookup"><span data-stu-id="acd16-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-245">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="acd16-246">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-246">Description</span></span>

<span data-ttu-id="acd16-247">Den här tjänsten gör PPPoE-sessionen ansluten med en tidigare skapad PPPoE-klient till den angivna PPPoE-servern.</span><span class="sxs-lookup"><span data-stu-id="acd16-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="acd16-248">Den här funktionen måste anropas efter nx_pppoe_client_create *nx_pppoe_client_host_uniq_set* och *nx_pppoe_client_service_name_set*.</span><span class="sxs-lookup"><span data-stu-id="acd16-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-249">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-249">Input Parameters</span></span>

 - <span data-ttu-id="acd16-250">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-251">**wait_option** Alternativet vänta medan anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="acd16-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-252">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-252">Return Values</span></span>

 - <span data-ttu-id="acd16-253">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klientsession Connect.</span><span class="sxs-lookup"><span data-stu-id="acd16-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="acd16-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-255">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-255">Allowed From</span></span>

<span data-ttu-id="acd16-256">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-257">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="acd16-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="acd16-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="acd16-259">Skicka PPPoE-klient paketet till en angiven session</span><span class="sxs-lookup"><span data-stu-id="acd16-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-260">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="acd16-261">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-261">Description</span></span>

<span data-ttu-id="acd16-262">Den här tjänsten skickar PPPoE-paket med angivet sessions-ID.</span><span class="sxs-lookup"><span data-stu-id="acd16-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-263">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-263">Input Parameters</span></span>

 - <span data-ttu-id="acd16-264">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-265">**packet_ptr** Pekare till PPPoE-paket.</span><span class="sxs-lookup"><span data-stu-id="acd16-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-266">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-266">Return Values</span></span>

 - <span data-ttu-id="acd16-267">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckades skicka PPPoE-klient paket.</span><span class="sxs-lookup"><span data-stu-id="acd16-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="acd16-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="acd16-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) ogiltigt PPPoE-klient paket.</span><span class="sxs-lookup"><span data-stu-id="acd16-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="acd16-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE-sessionen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="acd16-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-271">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-271">Allowed From</span></span>

<span data-ttu-id="acd16-272">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-273">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="acd16-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="acd16-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="acd16-275">Avsluta PPPoE-klientsession</span><span class="sxs-lookup"><span data-stu-id="acd16-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-276">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="acd16-277">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-277">Description</span></span>

<span data-ttu-id="acd16-278">Den här tjänsten avslutar den angivna PPPoE-sessionen.</span><span class="sxs-lookup"><span data-stu-id="acd16-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-279">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-279">Input Parameters</span></span>

 - <span data-ttu-id="acd16-280">**pppoe_client_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-281">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-281">Return Values</span></span>

 - <span data-ttu-id="acd16-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) en lyckad PPPoE-klientsession avslutades.</span><span class="sxs-lookup"><span data-stu-id="acd16-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="acd16-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-284">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-284">Allowed From</span></span>

<span data-ttu-id="acd16-285">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-286">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="acd16-287">nx_pppoe_client_session_get</span><span class="sxs-lookup"><span data-stu-id="acd16-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="acd16-288">Hämta den angivna informationen om PPPoE-sessionen</span><span class="sxs-lookup"><span data-stu-id="acd16-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="acd16-289">Prototyp</span><span class="sxs-lookup"><span data-stu-id="acd16-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="acd16-290">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="acd16-290">Description</span></span>

<span data-ttu-id="acd16-291">Den här tjänsten hämtar den angivna PPPoE-sessionsinformation, serverns fysiska adress och sessions-ID.</span><span class="sxs-lookup"><span data-stu-id="acd16-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="acd16-292">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="acd16-292">Input Parameters</span></span>

 - <span data-ttu-id="acd16-293">**pppoe_server_ptr** Pekare till PPPoE-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="acd16-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="acd16-294">**server_mac_msw** Serverns fysiska MSW-pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="acd16-295">**server_mac_lsw** Serverns fysiska MSW-pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="acd16-296">**session_id** Sessions-ID-pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="acd16-297">Retur värden</span><span class="sxs-lookup"><span data-stu-id="acd16-297">Return Values</span></span>

 - <span data-ttu-id="acd16-298">**NX_PPPOE_CLIENT_SUCCESS** (0X00) lyckad PPPoE-klientsession Hämta.</span><span class="sxs-lookup"><span data-stu-id="acd16-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="acd16-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) ogiltig PPPoE-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="acd16-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="acd16-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE-sessionen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="acd16-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="acd16-301">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="acd16-301">Allowed From</span></span>

<span data-ttu-id="acd16-302">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="acd16-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="acd16-303">Exempel</span><span class="sxs-lookup"><span data-stu-id="acd16-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
