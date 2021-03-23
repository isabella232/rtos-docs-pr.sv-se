---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Server Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE Server-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826601"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="73af6-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX PPPoE Server Services</span><span class="sxs-lookup"><span data-stu-id="73af6-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="73af6-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX PPPoE Server-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="73af6-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="73af6-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="73af6-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="73af6-106">**nx_pppoe_server_create**: *skapa en PPPoE-serverinstans*</span><span class="sxs-lookup"><span data-stu-id="73af6-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="73af6-107">**nx_pppoe_server_ac_name_set**: *Ange namn på åtkomst kon centra Tor*</span><span class="sxs-lookup"><span data-stu-id="73af6-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="73af6-108">**nx_pppoe_server_delete**: *ta bort en PPPoE-serverinstans*</span><span class="sxs-lookup"><span data-stu-id="73af6-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="73af6-109">**nx_pppoe_server_enable**: *aktivera PPPoE Server-tjänster*</span><span class="sxs-lookup"><span data-stu-id="73af6-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="73af6-110">**nx_pppoe_server_disable**: *inaktivera PPPoE Server-tjänster*</span><span class="sxs-lookup"><span data-stu-id="73af6-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="73af6-111">**nx_pppoe_server_callback_notify_set**: *Ange återanrop för PPPoE-serverns aviserings funktioner*</span><span class="sxs-lookup"><span data-stu-id="73af6-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="73af6-112">**nx_pppoe_server_service_name_set**: *Ange ett tjänst namn för PPPoE-servern*</span><span class="sxs-lookup"><span data-stu-id="73af6-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="73af6-113">**nx_pppoe_server_session_send**: *Skicka PPPoE-serverns data till en angiven session*</span><span class="sxs-lookup"><span data-stu-id="73af6-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="73af6-114">**nx_pppoe_server_session_packet_send**: *Skicka PPPoE-serverns paket till en angiven session*</span><span class="sxs-lookup"><span data-stu-id="73af6-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="73af6-115">**nx_pppoe_server_session_terminate**: *avsluta den angivna PPPoE-sessionen*</span><span class="sxs-lookup"><span data-stu-id="73af6-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="73af6-116">**nx_pppoe_server_session_get**: *Hämta information om den angivna sessionen*</span><span class="sxs-lookup"><span data-stu-id="73af6-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="73af6-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="73af6-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="73af6-118">Skapa en PPPoE-serverinstans</span><span class="sxs-lookup"><span data-stu-id="73af6-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-119">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="73af6-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-120">Description</span></span>

<span data-ttu-id="73af6-121">Den här tjänsten skapar en PPPoE-serverinstans med den angivna länk driv rutinen för den angivna NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="73af6-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="73af6-122">Om länk driv rutinen inte har initierats och är aktive rad, är den ansvarig för PPPoE Sever-programvara som initierar länk driv rutinen.</span><span class="sxs-lookup"><span data-stu-id="73af6-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="73af6-123">Dessutom måste programmet ange en tidigare skapad modempool för att PPPoE-serverinstansen ska användas för intern paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="73af6-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="73af6-124">Observera att det vanligt vis är en bra idé att skapa NetX IP-tråd med högre prioritet än tråd prioriteten för PPPoE-servern.</span><span class="sxs-lookup"><span data-stu-id="73af6-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="73af6-125">Mer information om hur du anger prioritet för IP-tråd finns i *nx_ip_create* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="73af6-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-126">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-126">Input Parameters</span></span>

- <span data-ttu-id="73af6-127">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-128">**namn**: namnet på den här PPPoE-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="73af6-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="73af6-129">**ip_ptr**: pekare till Control-Block för IP-instans.</span><span class="sxs-lookup"><span data-stu-id="73af6-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="73af6-130">**interface_index**: gränssnitts index.</span><span class="sxs-lookup"><span data-stu-id="73af6-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="73af6-131">**pppoe_link_driver**: användarens angivna länk driv rutin.</span><span class="sxs-lookup"><span data-stu-id="73af6-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="73af6-132">**pool_ptr**: pekar mot Packet bassäng.</span><span class="sxs-lookup"><span data-stu-id="73af6-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="73af6-133">**stack_ptr**: pekare för att starta PPPoE-Server trådens stack Area.</span><span class="sxs-lookup"><span data-stu-id="73af6-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="73af6-134">**stack_size**: storlek i byte i trådens stack.</span><span class="sxs-lookup"><span data-stu-id="73af6-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="73af6-135">**prioritet**: prioritet för interna PPPoE-Server trådar (1-31).</span><span class="sxs-lookup"><span data-stu-id="73af6-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-136">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-136">Return Values</span></span>

- <span data-ttu-id="73af6-137">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad PPPoE-Server skapa.</span><span class="sxs-lookup"><span data-stu-id="73af6-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="73af6-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server, IP, Packet bassäng eller stack pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="73af6-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) ogiltigt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="73af6-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="73af6-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) ogiltig nytto Last storlek för Packet bassäng.</span><span class="sxs-lookup"><span data-stu-id="73af6-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="73af6-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) ogiltig minnes storlek.</span><span class="sxs-lookup"><span data-stu-id="73af6-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="73af6-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) ogiltig prioritet för PPPoE-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="73af6-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-143">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-143">Allowed From</span></span>

<span data-ttu-id="73af6-144">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="73af6-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="73af6-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="73af6-147">Ta bort en PPPoE-serverinstans</span><span class="sxs-lookup"><span data-stu-id="73af6-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-148">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="73af6-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-149">Description</span></span>

<span data-ttu-id="73af6-150">Den här tjänsten tar bort den tidigare skapade PPPoE-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="73af6-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-151">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-151">Input Parameters</span></span>

- <span data-ttu-id="73af6-152">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-153">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-153">Return Values</span></span>

- <span data-ttu-id="73af6-154">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-156">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-156">Allowed From</span></span>

<span data-ttu-id="73af6-157">Konversation</span><span class="sxs-lookup"><span data-stu-id="73af6-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-158">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="73af6-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="73af6-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="73af6-160">Aktivera PPPoE-servertjänsten</span><span class="sxs-lookup"><span data-stu-id="73af6-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="73af6-162">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-162">Description</span></span>

<span data-ttu-id="73af6-163">Med den här tjänsten kan du använda PPPoE-Server tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="73af6-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="73af6-164">Den här funktionen måste anropas efter *nx_pppoe_server_create* och *nx_pppoe_server_callback_notify_set*.</span><span class="sxs-lookup"><span data-stu-id="73af6-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-165">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-165">Input Parameters</span></span>

- <span data-ttu-id="73af6-166">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-167">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-167">Return Values</span></span>

- <span data-ttu-id="73af6-168">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-170">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-170">Allowed From</span></span>

<span data-ttu-id="73af6-171">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-172">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="73af6-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="73af6-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="73af6-174">Inaktivera PPPoE-servertjänsten</span><span class="sxs-lookup"><span data-stu-id="73af6-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-175">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="73af6-176">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-176">Description</span></span>

<span data-ttu-id="73af6-177">Den här tjänsten inaktiverar PPPoE-Server tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="73af6-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-178">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-178">Input Parameters</span></span>

- <span data-ttu-id="73af6-179">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-180">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-180">Return Values</span></span>

- <span data-ttu-id="73af6-181">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-183">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-183">Allowed From</span></span>

<span data-ttu-id="73af6-184">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-185">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="73af6-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="73af6-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="73af6-187">Ange aviserings funktioner för motringning från PPPoE-Server</span><span class="sxs-lookup"><span data-stu-id="73af6-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="73af6-188">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="73af6-189">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-189">Description</span></span>

<span data-ttu-id="73af6-190">Den här tjänsten anger att återanrop i PPPoE-servern ska meddela funktioner.</span><span class="sxs-lookup"><span data-stu-id="73af6-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="73af6-191">Den här funktionen måste anropas före *nx_pppoe_server_enabl och* pppoe_data_receive_notify-funktions pekare måste anges, om inte, *nx_pppoe_server_enable* kommer att Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="73af6-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-192">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-192">Input Parameters</span></span>

- <span data-ttu-id="73af6-193">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-194">**pppoe_discover_initiation_notify**: program funktion som anropas när ett meddelande om att initiering av PPPoE-identifiering tas emot.</span><span class="sxs-lookup"><span data-stu-id="73af6-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="73af6-195">Om det här värdet är NULL inaktive ras funktionen motringning.</span><span class="sxs-lookup"><span data-stu-id="73af6-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="73af6-196">**pppoe_discover_request_notify**: program funktion som anropas när ett meddelande om PPPoE-Discover tas emot.</span><span class="sxs-lookup"><span data-stu-id="73af6-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="73af6-197">Om det här värdet är NULL är funktionen motringning för begäran inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="73af6-198">**pppoe_discover_terminate_notify**: program funktion som anropas när ett meddelande om att avsluta PPPoE-identifiering tas emot.</span><span class="sxs-lookup"><span data-stu-id="73af6-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="73af6-199">Om det här värdet är NULL är funktionen avsluta motringning inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="73af6-200">**pppoe_discover_terminate_confirm**: program funktion som anropas när ett meddelande om att avsluta PPPoE-identifiering skickas.</span><span class="sxs-lookup"><span data-stu-id="73af6-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="73af6-201">Om det här värdet är NULL är funktionen avsluta motringning inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="73af6-202">**pppoe_data_receive_notify**: program funktion som anropas när ett data meddelande för PPPoE tas emot.</span><span class="sxs-lookup"><span data-stu-id="73af6-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="73af6-203">Värdet får inte vara noll.</span><span class="sxs-lookup"><span data-stu-id="73af6-203">This value must not be zero.</span></span>
- <span data-ttu-id="73af6-204">**pppoe_data_send_notify**: program funktion som anropas när ett data meddelande för PPPoE skickas.</span><span class="sxs-lookup"><span data-stu-id="73af6-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="73af6-205">Om det här värdet är NULL är funktionen för att skicka motringning inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-206">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-206">Return Values</span></span>

- <span data-ttu-id="73af6-207">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare eller funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-209">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-209">Allowed From</span></span>

<span data-ttu-id="73af6-210">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-211">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="73af6-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="73af6-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="73af6-213">Ange namn på åtkomst kon centra Tor</span><span class="sxs-lookup"><span data-stu-id="73af6-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-214">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="73af6-215">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-215">Description</span></span>

<span data-ttu-id="73af6-216">Den här funktionen ställer in åtkomst till koncentrator Name funktion anrop.</span><span class="sxs-lookup"><span data-stu-id="73af6-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="73af6-217">Strängen för ac_name måste vara NULL-terminerad och längden på ac_name matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="73af6-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-218">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-218">Input Parameters</span></span>

- <span data-ttu-id="73af6-219">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-220">**ac_name**: åtkomst till koncentrator namn.</span><span class="sxs-lookup"><span data-stu-id="73af6-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="73af6-221">**ac_name_length**: längden på ac_ame.</span><span class="sxs-lookup"><span data-stu-id="73af6-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-222">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-222">Return Values</span></span>

- <span data-ttu-id="73af6-223">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad PPPoE-Server uppsättning.</span><span class="sxs-lookup"><span data-stu-id="73af6-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="73af6-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0XC1) ogiltig PPPoE-Server, IP, Packet bassäng eller stack pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="73af6-225">**NX_SIZE_ERROR**: (0X09) kontrol lera name_length inte.</span><span class="sxs-lookup"><span data-stu-id="73af6-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-226">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-226">Allowed From</span></span>

<span data-ttu-id="73af6-227">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-228">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="73af6-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="73af6-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="73af6-230">Ange namn på tjänsten PPPoE-Server</span><span class="sxs-lookup"><span data-stu-id="73af6-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-231">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="73af6-232">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-232">Description</span></span>

<span data-ttu-id="73af6-233">Den här tjänsten anger tjänst namnet för en PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-234">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-234">Input Parameters</span></span>

- <span data-ttu-id="73af6-235">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-236">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-236">Return Values</span></span>

- <span data-ttu-id="73af6-237">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-239">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-239">Allowed From</span></span>

<span data-ttu-id="73af6-240">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-241">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="73af6-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="73af6-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="73af6-243">Skicka PPPoE-serverns data till en angiven session</span><span class="sxs-lookup"><span data-stu-id="73af6-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-244">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="73af6-245">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-245">Description</span></span>

<span data-ttu-id="73af6-246">Den här tjänsten skickar PPPoE-ramen med angivet sessions-ID.</span><span class="sxs-lookup"><span data-stu-id="73af6-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-247">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-247">Input Parameters</span></span>

- <span data-ttu-id="73af6-248">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-249">**session_index**: sessionens index.</span><span class="sxs-lookup"><span data-stu-id="73af6-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="73af6-250">**data_ptr**: pekare för att starta data rutan för PPPoE-servern.</span><span class="sxs-lookup"><span data-stu-id="73af6-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="73af6-251">**data_length**: längden på data fältet för PPPoE-servern.</span><span class="sxs-lookup"><span data-stu-id="73af6-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-252">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-252">Return Values</span></span>

- <span data-ttu-id="73af6-253">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="73af6-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="73af6-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.</span><span class="sxs-lookup"><span data-stu-id="73af6-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="73af6-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="73af6-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-258">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-258">Allowed From</span></span>

<span data-ttu-id="73af6-259">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-260">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="73af6-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="73af6-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="73af6-262">Skicka PPPoE-serverns paket till en angiven session</span><span class="sxs-lookup"><span data-stu-id="73af6-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-263">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="73af6-264">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-264">Description</span></span>

<span data-ttu-id="73af6-265">Den här tjänsten skickar PPPoE-paket med angivet sessions-ID.</span><span class="sxs-lookup"><span data-stu-id="73af6-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-266">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-266">Input Parameters</span></span>

- <span data-ttu-id="73af6-267">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-268">**session_index**: sessionens index.</span><span class="sxs-lookup"><span data-stu-id="73af6-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="73af6-269">**packet_ptr**: pekare till PPPoE-paket.</span><span class="sxs-lookup"><span data-stu-id="73af6-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-270">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-270">Return Values</span></span>

- <span data-ttu-id="73af6-271">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="73af6-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) ogiltigt PPPoE-Server paket.</span><span class="sxs-lookup"><span data-stu-id="73af6-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="73af6-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="73af6-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.</span><span class="sxs-lookup"><span data-stu-id="73af6-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="73af6-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="73af6-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-277">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-277">Allowed From</span></span>

<span data-ttu-id="73af6-278">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-279">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="73af6-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="73af6-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="73af6-281">Avsluta den angivna PPPoE-sessionen</span><span class="sxs-lookup"><span data-stu-id="73af6-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-282">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="73af6-283">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-283">Description</span></span>

<span data-ttu-id="73af6-284">Den här tjänsten avslutar den angivna PPPoE-sessionen.</span><span class="sxs-lookup"><span data-stu-id="73af6-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-285">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-285">Input Parameters</span></span>

- <span data-ttu-id="73af6-286">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-287">**session_index**: sessionens index.</span><span class="sxs-lookup"><span data-stu-id="73af6-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-288">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-288">Return Values</span></span>

- <span data-ttu-id="73af6-289">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="73af6-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE-servertjänsten är inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="73af6-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="73af6-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.</span><span class="sxs-lookup"><span data-stu-id="73af6-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="73af6-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="73af6-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-294">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-294">Allowed From</span></span>

<span data-ttu-id="73af6-295">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-296">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="73af6-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="73af6-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="73af6-298">Hämta den angivna informationen om PPPoE-sessionen</span><span class="sxs-lookup"><span data-stu-id="73af6-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-299">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="73af6-300">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-300">Description</span></span>

<span data-ttu-id="73af6-301">Den här tjänsten hämtar den angivna PPPoE-sessionsinformation, klientens fysiska adress och sessions-ID.</span><span class="sxs-lookup"><span data-stu-id="73af6-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-302">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-302">Input Parameters</span></span>

- <span data-ttu-id="73af6-303">**pppoe_server_ptr**: pekar på kontroll block för PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="73af6-304">**session_index**: sessionens index.</span><span class="sxs-lookup"><span data-stu-id="73af6-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="73af6-305">**client_mac_msw**: MSW-pekare för klientens fysiska adress.</span><span class="sxs-lookup"><span data-stu-id="73af6-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="73af6-306">**client_mac_lsw**: MSW-pekare för klientens fysiska adress.</span><span class="sxs-lookup"><span data-stu-id="73af6-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="73af6-307">**session_id**: sessions-ID-pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-308">Return Values</span></span>

- <span data-ttu-id="73af6-309">**NX_PPPOE_SERVER_SUCCESS**: (0X00) lyckad borttagning av PPPoE-Server.</span><span class="sxs-lookup"><span data-stu-id="73af6-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="73af6-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) ogiltig PPPoE-Server pekare.</span><span class="sxs-lookup"><span data-stu-id="73af6-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="73af6-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) ogiltigt PPPoE-sessions index.</span><span class="sxs-lookup"><span data-stu-id="73af6-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="73af6-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE-sessionen har inte upprättats.</span><span class="sxs-lookup"><span data-stu-id="73af6-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-313">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-313">Allowed From</span></span>

<span data-ttu-id="73af6-314">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-315">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="73af6-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="73af6-316">PppInitInd</span></span>

<span data-ttu-id="73af6-317">Konfigurera standard tjänst namnet</span><span class="sxs-lookup"><span data-stu-id="73af6-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-318">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="73af6-319">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-319">Description</span></span>

<span data-ttu-id="73af6-320">PPPoE-programmet kommer att visa den här funktionen för att tillåta att TTP-programvaran konfigurerar standard tjänst namnet som PPPoE ska använda för att filtrera inkommande PADI-begäranden.</span><span class="sxs-lookup"><span data-stu-id="73af6-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="73af6-321">PPPoE-programvaran bör komma ihåg den här informationen och om ett PADI-paket tas emot som innehåller ett tjänst namn som matchar, ska det anropa PppDiscoverReq.</span><span class="sxs-lookup"><span data-stu-id="73af6-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-322">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-322">Input Parameters</span></span>

- <span data-ttu-id="73af6-323">**längd**: längden på standard tjänst namnet.</span><span class="sxs-lookup"><span data-stu-id="73af6-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="73af6-324">**aData**: standard tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="73af6-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-325">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-325">Return Values</span></span>

<span data-ttu-id="73af6-326">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-327">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-327">Allowed From</span></span>

<span data-ttu-id="73af6-328">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-329">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="73af6-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="73af6-330">PppDiscoverCnf</span></span>

<span data-ttu-id="73af6-331">Definiera tjänst namns fältet för PADO-paketet</span><span class="sxs-lookup"><span data-stu-id="73af6-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-332">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="73af6-333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-333">Description</span></span>

<span data-ttu-id="73af6-334">PPPoE-programmet kommer att visa den här funktionen för att tillåta att TTP-programvaran definierar fältet för tjänst namn i PADO-paketet.</span><span class="sxs-lookup"><span data-stu-id="73af6-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="73af6-335">PPPoE-programvaran bör inte skicka PADO förrän PppDiscoverCnf anropas.</span><span class="sxs-lookup"><span data-stu-id="73af6-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="73af6-336">PADO-paketet måste innehålla ett namn för åtkomst koncentrator (med taggen ID 0x0102 som definieras i RFC2516), definierat i initieringen av PPPoE-programvaran.</span><span class="sxs-lookup"><span data-stu-id="73af6-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="73af6-337">Flera tjänst namn kan skickas i aData, där varje namn ska vara null.</span><span class="sxs-lookup"><span data-stu-id="73af6-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="73af6-338">NULL-tecken används som avgränsare för att ge maximal flexibilitet om andra kommandon måste skickas in som en del av tjänstens namn.</span><span class="sxs-lookup"><span data-stu-id="73af6-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-339">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-339">Input Parameters</span></span>

- <span data-ttu-id="73af6-340">**längd**: längden på standard tjänst namnet.</span><span class="sxs-lookup"><span data-stu-id="73af6-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="73af6-341">**aData**: standard tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="73af6-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="73af6-342">**interfaceHandle**: gränssnitts referens.</span><span class="sxs-lookup"><span data-stu-id="73af6-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-343">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-343">Return Values</span></span>

<span data-ttu-id="73af6-344">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-345">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-345">Allowed From</span></span>

<span data-ttu-id="73af6-346">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-347">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="73af6-348">PppOpenCnf</span><span class="sxs-lookup"><span data-stu-id="73af6-348">PppOpenCnf</span></span>

<span data-ttu-id="73af6-349">Acceptera eller avvisa PPPoE-sessionen</span><span class="sxs-lookup"><span data-stu-id="73af6-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-350">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="73af6-351">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-351">Description</span></span>

<span data-ttu-id="73af6-352">PPPoE-programmet kommer att exponera den här funktionen så att TTP-programvaran kan godkänna eller avvisa PPPoE-sessionen.</span><span class="sxs-lookup"><span data-stu-id="73af6-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="73af6-353">Som svar på det här är PPPoE-stacken att godkänna anslutningen och tilldela ett unikt PPPoE-Session_ID kopplat till interfaceHandle.</span><span class="sxs-lookup"><span data-stu-id="73af6-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-354">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-354">Input Parameters</span></span>

- <span data-ttu-id="73af6-355">**acceptera**: NX_TRUE om anslutningen ska godkännas.</span><span class="sxs-lookup"><span data-stu-id="73af6-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="73af6-356">**interfaceHandle**: gränssnitts referens.</span><span class="sxs-lookup"><span data-stu-id="73af6-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-357">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-357">Return Values</span></span>

<span data-ttu-id="73af6-358">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-359">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-359">Allowed From</span></span>

<span data-ttu-id="73af6-360">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-361">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="73af6-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="73af6-362">PppCloseInd</span></span>

<span data-ttu-id="73af6-363">Stänga en PPPoE-session</span><span class="sxs-lookup"><span data-stu-id="73af6-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-364">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="73af6-365">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-365">Description</span></span>

<span data-ttu-id="73af6-366">PPPoE-programvaran kommer att exponera den här funktionen för att låta TTP-programvaran stänga en PPPoE-session.</span><span class="sxs-lookup"><span data-stu-id="73af6-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="73af6-367">PPPoE-programvaran anger orsaks kod strängen i Generic-Error-taggen (0x0203) i PADT-meddelandet</span><span class="sxs-lookup"><span data-stu-id="73af6-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-368">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-368">Input Parameters</span></span>

- <span data-ttu-id="73af6-369">**interfaceHandle**: gränssnitts referens.</span><span class="sxs-lookup"><span data-stu-id="73af6-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="73af6-370">**causeCode**: null-avslutad sträng för sändning av information om orsaken till att anslutningen stängdes från PPPoE-servern.</span><span class="sxs-lookup"><span data-stu-id="73af6-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-371">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-371">Return Values</span></span>

<span data-ttu-id="73af6-372">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-373">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-373">Allowed From</span></span>

<span data-ttu-id="73af6-374">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-375">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="73af6-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="73af6-376">PppCloseCnf</span></span>

<span data-ttu-id="73af6-377">Bekräfta att referensen har frigjorts</span><span class="sxs-lookup"><span data-stu-id="73af6-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-378">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="73af6-379">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-379">Description</span></span>

<span data-ttu-id="73af6-380">PPPoE-programmet kommer att exponera den här funktionen för att tillåta att TTP-programvaran bekräftar att referensen har frigjorts.</span><span class="sxs-lookup"><span data-stu-id="73af6-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-381">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-381">Input Parameters</span></span>

- <span data-ttu-id="73af6-382">**interfaceHandle**: gränssnitts referens.</span><span class="sxs-lookup"><span data-stu-id="73af6-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-383">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-383">Return Values</span></span>

<span data-ttu-id="73af6-384">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-385">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-385">Allowed From</span></span>

<span data-ttu-id="73af6-386">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-387">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="73af6-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="73af6-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="73af6-389">Tillåt att en tidigare PPP-data bekräftas</span><span class="sxs-lookup"><span data-stu-id="73af6-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-390">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="73af6-391">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-391">Description</span></span>

<span data-ttu-id="73af6-392">PPPoE-programmet kommer att exponera den här funktionen så att en föregående PppTransmitDataReq kan bekräftas.</span><span class="sxs-lookup"><span data-stu-id="73af6-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="73af6-393">Det innebär att TTP-programvaran är redo för en ny PPP-ram från PPPoE.</span><span class="sxs-lookup"><span data-stu-id="73af6-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-394">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-394">Input Parameters</span></span>

- <span data-ttu-id="73af6-395">**interfaceHandle**: gränssnitts referens.</span><span class="sxs-lookup"><span data-stu-id="73af6-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="73af6-396">**aData**: pekar på den PPP-databuffert som har godkänts.</span><span class="sxs-lookup"><span data-stu-id="73af6-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="73af6-397">**Packet_id**: paket-ID.</span><span class="sxs-lookup"><span data-stu-id="73af6-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-398">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-398">Return Values</span></span>

<span data-ttu-id="73af6-399">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-400">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-400">Allowed From</span></span>

<span data-ttu-id="73af6-401">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-402">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="73af6-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="73af6-403">PppReceiveDataInd</span></span>

<span data-ttu-id="73af6-404">Ta emot data från överföring över Ethernet</span><span class="sxs-lookup"><span data-stu-id="73af6-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="73af6-405">Prototyp</span><span class="sxs-lookup"><span data-stu-id="73af6-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="73af6-406">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73af6-406">Description</span></span>

<span data-ttu-id="73af6-407">PPPoE-programmet kommer att exponera den här funktionen för att ta emot data för överföring via Ethernet</span><span class="sxs-lookup"><span data-stu-id="73af6-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73af6-408">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="73af6-408">Input Parameters</span></span>

- <span data-ttu-id="73af6-409">**interfaceHandle**: gränssnitts referens.</span><span class="sxs-lookup"><span data-stu-id="73af6-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="73af6-410">**längd**: antalet byte i aData.</span><span class="sxs-lookup"><span data-stu-id="73af6-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="73af6-411">**aData**: databuffert som innehåller en ram med PPP-data.</span><span class="sxs-lookup"><span data-stu-id="73af6-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="73af6-412">Retur värden</span><span class="sxs-lookup"><span data-stu-id="73af6-412">Return Values</span></span>

<span data-ttu-id="73af6-413">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="73af6-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73af6-414">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="73af6-414">Allowed From</span></span>

<span data-ttu-id="73af6-415">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="73af6-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="73af6-416">Exempel</span><span class="sxs-lookup"><span data-stu-id="73af6-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```