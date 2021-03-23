---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNTP Client Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SNTP-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825746"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="2cf7c-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo SNTP Client Services</span><span class="sxs-lookup"><span data-stu-id="2cf7c-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="2cf7c-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo SNTP-klienttjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2cf7c-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2cf7c-106">**nx_sntp_client_create**: *skapa en SNTP-klient*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="2cf7c-107">**nx_sntp_client_delete**: *ta bort SNTP-klienten*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="2cf7c-108">**nx_sntp_client_get_local_time**: *Hämta lokal tid för SNTP-klient*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="2cf7c-109">**nx_sntp_client_get_local_time_extended**: *Hämta lokal tid för SNTP-klient*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="2cf7c-110">**nx_sntp_client_initialize_broadcast**: *initiera klienten för IPv4-sändnings åtgärd*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="2cf7c-111">**nxd_sntp_client_initialize_broadcast**: *initiera klienten för IPv6-eller IPv4-sändnings åtgärd*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="2cf7c-112">**nx_sntp_client_initialize_unicast**: *initiera klienten för IPv4 unicast-åtgärd*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="2cf7c-113">**nxd_sntp_client_initialize_unicast**: *initiera klienten för IPv4-eller IPv6 unicast-åtgärd*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="2cf7c-114">**nx_sntp_client_receiving_udpates**: *klienten får för närvarande giltiga SNTP-uppdateringar*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="2cf7c-115">**nx_sntp_client_request_unicast_time**: *skicka en unicast-begäran direkt till NTP-servern*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="2cf7c-116">**nx_sntp_client_run_broadcast**: *Kör klienten i sändnings läge*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="2cf7c-117">**nx_sntp_client_run_unicast**: *Kör klienten i unicast-läge*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="2cf7c-118">**nx_sntp_client_set_local_time**: *Ange första lokala tid för SNTP-klienten*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="2cf7c-119">**nx_sntp_client_set_time_update_notify**: *Ange uppdaterings ÅTERanrop för SNTP*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="2cf7c-120">**nx_sntp_client_stop**: *stoppa klient tråden för SNTP*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="2cf7c-121">**nx_sntp_client_utility_display_date_and_time**: *Visa NTP-tid i sekunder*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="2cf7c-122">**nx_sntp_client_utility_msecs_to_fraction**: *konvertera millisekunder till en NTP-fraktion*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="2cf7c-123">**nx_sntp_client_utility_usecs_to_fraction**: *konvertera mikrosekunder till en NTP-fraktion*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="2cf7c-124">**nx_sntp_client_utility_fraction_to_usecs**: *konvertera en NTP-fraktion till mikrosekunder*</span><span class="sxs-lookup"><span data-stu-id="2cf7c-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="2cf7c-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="2cf7c-125">nx_sntp_client_create</span></span>

<span data-ttu-id="2cf7c-126">Skapa en SNTP-klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-127">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="2cf7c-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-128">Description</span></span>

<span data-ttu-id="2cf7c-129">Den här tjänsten skapar en SNTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-130">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-130">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-131">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-132">**ip_ptr** Pekare till klientens IP-instans</span><span class="sxs-lookup"><span data-stu-id="2cf7c-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="2cf7c-133">**iface_index** Index till SNTP-nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="2cf7c-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="2cf7c-134">**packet_pool_ptr** Pekare till klient paketets pool</span><span class="sxs-lookup"><span data-stu-id="2cf7c-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="2cf7c-135">**leap_second_handler** Motringning för program svar till ett förestående skottår-sekund</span><span class="sxs-lookup"><span data-stu-id="2cf7c-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="2cf7c-136">**kiss_of_death_handler** Motringning för program svar för att ta emot kyss av döden-paket</span><span class="sxs-lookup"><span data-stu-id="2cf7c-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="2cf7c-137">**random_number_generator** Motringning till slumpmässig nummer generator tjänst</span><span class="sxs-lookup"><span data-stu-id="2cf7c-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-138">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-138">Return Values</span></span>

- <span data-ttu-id="2cf7c-139">**NX_SUCCESS** (0X00) lyckad klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="2cf7c-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0XD2A) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="2cf7c-141">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-142">NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="2cf7c-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-143">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-143">Allowed From</span></span>

<span data-ttu-id="2cf7c-144">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="2cf7c-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="2cf7c-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="2cf7c-147">Ta bort en SNTP-klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-148">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="2cf7c-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-149">Description</span></span>

<span data-ttu-id="2cf7c-150">Den här tjänsten tar bort en SNTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-151">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-151">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-152">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-153">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-153">Return Values</span></span>

- <span data-ttu-id="2cf7c-154">**NX_SUCCESS** (0X00) lyckad klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="2cf7c-155">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-156">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-157">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-157">Allowed From</span></span>

<span data-ttu-id="2cf7c-158">Konversation</span><span class="sxs-lookup"><span data-stu-id="2cf7c-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-159">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="2cf7c-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="2cf7c-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="2cf7c-161">Hämta lokal tid för SNTP-klienten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-162">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="2cf7c-163">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-163">Description</span></span>

<span data-ttu-id="2cf7c-164">Den här tjänsten hämtar SNTP-klientens lokala tid med en option buffer-indata för att ta emot data i sträng meddelande format.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="2cf7c-165">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-165">This service is deprecated.</span></span> <span data-ttu-id="2cf7c-166">Utvecklare uppmanas att migrera till *nx_sntp_client_get_local_time_extended*().</span><span class="sxs-lookup"><span data-stu-id="2cf7c-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-167">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-167">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-168">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-169">**sekunder** Pekare till lokal tid i sekunder</span><span class="sxs-lookup"><span data-stu-id="2cf7c-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="2cf7c-170">**bråk** Lokal tids fraktions komponent</span><span class="sxs-lookup"><span data-stu-id="2cf7c-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="2cf7c-171">**buffert** Pekare som buffrar för att skriva tids data</span><span class="sxs-lookup"><span data-stu-id="2cf7c-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-172">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-172">Return Values</span></span>

- <span data-ttu-id="2cf7c-173">**NX_SUCCESS** (0X00) lyckad klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="2cf7c-174">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-175">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-176">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-176">Allowed From</span></span>

<span data-ttu-id="2cf7c-177">Konversation</span><span class="sxs-lookup"><span data-stu-id="2cf7c-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-178">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="2cf7c-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="2cf7c-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="2cf7c-180">Hämta den utökade SNTP-klientens lokala tid</span><span class="sxs-lookup"><span data-stu-id="2cf7c-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-181">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="2cf7c-182">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-182">Description</span></span>

<span data-ttu-id="2cf7c-183">Den här tjänsten hämtar den utökade SNTP-klientens lokala tid med en option buffer-indata för att ta emot data i sträng meddelande format.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-184">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-184">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-185">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-186">**sekunder** Pekare till lokal tid i sekunder</span><span class="sxs-lookup"><span data-stu-id="2cf7c-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="2cf7c-187">**bråk** Pekare till bråk del</span><span class="sxs-lookup"><span data-stu-id="2cf7c-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="2cf7c-188">**buffert** Pekare som buffrar för att skriva tids data</span><span class="sxs-lookup"><span data-stu-id="2cf7c-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="2cf7c-189">**buffer_size** Buffertens längd</span><span class="sxs-lookup"><span data-stu-id="2cf7c-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-190">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-190">Return Values</span></span>

- <span data-ttu-id="2cf7c-191">**NX_SUCCESS** (0X00) lyckad klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="2cf7c-192">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-193">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="2cf7c-194">NX_SIZE_ERROR (0x09) kontrol lera buffer_size inte</span><span class="sxs-lookup"><span data-stu-id="2cf7c-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-195">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-195">Allowed From</span></span>

<span data-ttu-id="2cf7c-196">Konversation</span><span class="sxs-lookup"><span data-stu-id="2cf7c-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-197">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="2cf7c-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="2cf7c-199">Initiera klienten för sändnings åtgärd</span><span class="sxs-lookup"><span data-stu-id="2cf7c-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="2cf7c-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-201">Description</span></span>

<span data-ttu-id="2cf7c-202">Den här tjänsten initierar klienten för sändning genom att ange IP-adressen för SNTP-servern och initiera start parametrarna för SNTP och timeout.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="2cf7c-203">Om båda multicast-och broadcast-adresserna inte är null väljs multicast-adressen.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="2cf7c-204">Om båda adresserna är null returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="2cf7c-205">Observera att detta endast stöder IPv4-serveradresser.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-206">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-206">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-207">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-208">**multicast_server_address** Multicast-adress för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="2cf7c-209">**broadcast_time_server** Broadcast-adress för SNTP-server</span><span class="sxs-lookup"><span data-stu-id="2cf7c-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-210">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-210">Return Values</span></span>

- <span data-ttu-id="2cf7c-211">**NX_SUCCESS** (0X00) lyckad klient</span><span class="sxs-lookup"><span data-stu-id="2cf7c-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="2cf7c-212">**NX_INVALID_PARAMETERS** (0X4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="2cf7c-213">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-214">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-215">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-215">Allowed From</span></span>

<span data-ttu-id="2cf7c-216">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-217">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="2cf7c-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="2cf7c-219">Initiera klienten för IPv4-eller IPv6-broadcast-åtgärd</span><span class="sxs-lookup"><span data-stu-id="2cf7c-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-220">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="2cf7c-221">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-221">Description</span></span>

<span data-ttu-id="2cf7c-222">Den här tjänsten initierar klienten för sändning genom att konfigurera IP-adressen för SNTP-servern och initiera start parametrarna för SNTP och timeout.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="2cf7c-223">Om både sändnings-och multicast-adress pekare är icke-null väljs multicast-adressen.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="2cf7c-224">Om båda adress pekarna är null returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="2cf7c-225">Detta stöder både IPv4-och IPv6-adress typer.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="2cf7c-226">Observera att IPv6 inte stöder sändning, så att sändnings adress pekaren är inställd på IPv6, ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-227">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-227">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-228">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-229">**multicast_server_address** Multicast-adress för SNTP-server</span><span class="sxs-lookup"><span data-stu-id="2cf7c-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="2cf7c-230">**broadcast_server_address** Broadcast-adress för SNTP-server</span><span class="sxs-lookup"><span data-stu-id="2cf7c-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-231">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-231">Return Values</span></span>

- <span data-ttu-id="2cf7c-232">**NX_SUCCESS** (0X00) klienten har initierats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="2cf7c-233">NX_SNTP_PARAM_ERROR (0xD0D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="2cf7c-234">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-235">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="2cf7c-236">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-236">Allowed From</span></span>

<span data-ttu-id="2cf7c-237">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-238">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="2cf7c-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="2cf7c-240">Konfigurera SNTP-klienten så att den körs i unicast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-241">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="2cf7c-242">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-242">Description</span></span>

<span data-ttu-id="2cf7c-243">Den här tjänsten initierar klienten för unicast-åtgärd genom att ange IP-adressen för SNTP-servern och initiera start parametrar och tids gränser för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="2cf7c-244">Observera att detta endast stöder IPv4-serveradresser.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-245">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-245">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-246">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-247">**unicast_time_server** IP-adress för SNTP-server</span><span class="sxs-lookup"><span data-stu-id="2cf7c-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-248">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-248">Return Values</span></span>

- <span data-ttu-id="2cf7c-249">**NX_SUCCESS** (0X00) klienten har initierats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="2cf7c-250">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="2cf7c-251">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-252">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-253">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-253">Allowed From</span></span>

<span data-ttu-id="2cf7c-254">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-255">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="2cf7c-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="2cf7c-257">Konfigurera SNTP-klienten så att den körs i IPv4 eller IPv6 unicast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-258">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="2cf7c-259">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-259">Description</span></span>

<span data-ttu-id="2cf7c-260">Den här tjänsten initierar klienten för unicast-åtgärd genom att konfigurera IP-adressen för SNTP-servern och initiera start parametrarna för SNTP och timeout.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="2cf7c-261">Detta stöder både IPv4-och IPv6-adress typer.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-262">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-262">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-263">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-264">**unicast_time_server** IP-adress för SNTP-server</span><span class="sxs-lookup"><span data-stu-id="2cf7c-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-265">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-265">Return Values</span></span>

- <span data-ttu-id="2cf7c-266">**NX_SUCCESS** (0X00) klienten har initierats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="2cf7c-267">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="2cf7c-268">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-269">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-270">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-270">Allowed From</span></span>

<span data-ttu-id="2cf7c-271">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-272">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="2cf7c-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="2cf7c-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="2cf7c-274">Ange om klienten får giltiga uppdateringar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-275">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="2cf7c-276">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-276">Description</span></span>

<span data-ttu-id="2cf7c-277">Den här tjänsten anger om klienten tar emot giltiga SNTP-uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="2cf7c-278">Om den maximala tiden för fördröjning utan en giltig uppdatering eller gräns på efterföljande ogiltiga uppdateringar överskrids, returneras mottagar status som falskt.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="2cf7c-279">Observera att SNTP-klienten fortfarande körs och om programmet vill starta om SNTP-klienten med en annan unicast-eller broadcast/multicast-server måste den stoppa SNTP-klienten med hjälp av tjänsten *nx_sntp_client_stop* , initiera om klienten med hjälp av en av de initierande tjänsterna med en annan server.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-280">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-280">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-281">**client_ptr** Pekare till klient kontroll block för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="2cf7c-282">**receive_status** Pekare till indikator om klienten får giltiga uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-283">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-283">Return Values</span></span>

- <span data-ttu-id="2cf7c-284">**NX_SUCCESS** (0X00) klienten har tagit emot uppdaterings status</span><span class="sxs-lookup"><span data-stu-id="2cf7c-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="2cf7c-285">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-286">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-286">Allowed From</span></span>

<span data-ttu-id="2cf7c-287">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-288">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="2cf7c-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="2cf7c-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="2cf7c-290">Skicka en unicast-begäran direkt till NTP-servern</span><span class="sxs-lookup"><span data-stu-id="2cf7c-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="2cf7c-291">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="2cf7c-292">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-292">Description</span></span>

<span data-ttu-id="2cf7c-293">Med den här tjänsten kan programmet direkt skicka en unicast-begäran till NTP-servern asynkront från klient tråds aktiviteten för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="2cf7c-294">Alternativet wait anger hur lång tid det tar att vänta på ett svar.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="2cf7c-295">Om det lyckas kan programmet använda andra SNTP-klienttjänster för att hämta den senaste tiden.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="2cf7c-296">Se avsnittet **SNTP asynkrona unicast-begäranden** för mer information.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-297">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-297">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-298">**client_ptr** Pekare till klient kontroll block för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="2cf7c-299">**Wait_option** Vänte alternativ för NTP-svar i timer-Tick.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-300">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-300">Return Values</span></span>

- <span data-ttu-id="2cf7c-301">**NX_SUCCESS** (0X00) klienten skickar och tar emot unicast-uppdatering</span><span class="sxs-lookup"><span data-stu-id="2cf7c-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="2cf7c-302">**NX_SNTP_CLIENT_NOT_STARTED** (0XD0B) klient tråden har inte startats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="2cf7c-303">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-304">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-305">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-305">Allowed From</span></span>

<span data-ttu-id="2cf7c-306">Konversation</span><span class="sxs-lookup"><span data-stu-id="2cf7c-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-307">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="2cf7c-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="2cf7c-309">Kör klienten i sändnings läge</span><span class="sxs-lookup"><span data-stu-id="2cf7c-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-310">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="2cf7c-311">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-311">Description</span></span>

<span data-ttu-id="2cf7c-312">Den här tjänsten startar klienten i sändnings läge där den väntar på att få broadcasts från SNTP-servern.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="2cf7c-313">Om ett giltigt meddelande för broadcast-SNTP tas emot återställs klientens timeout-värde för SNTP-klienten för maximal fördröjning utan en uppdatering och antalet ogiltiga mottagna meddelanden som tagits emot återställs.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="2cf7c-314">Om någon av dessa gränser överskrids sätter SNTP-klienten Server statusen till ogiltig trots att den fortfarande väntar på att ta emot uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="2cf7c-315">Programmet kan avsöka SNTP-klientens aktivitet för Server status och om ogiltigt stoppa SNTP-klienten och initiera om den med en annan SNTP-sändnings adress.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="2cf7c-316">Den kan också växla till en unicast SNTP-server.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-317">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-317">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-318">**client_ptr** Pekare till klient kontroll block för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-319">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-319">Return Values</span></span>

- <span data-ttu-id="2cf7c-320">**status** --------faktisk slut för ande status</span><span class="sxs-lookup"><span data-stu-id="2cf7c-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="2cf7c-321">**NX_SNTP_CLIENT_ALREADY_STARTED** -klienten (0xD0C) har redan startats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="2cf7c-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** -klienten (0xD01) har inte initierats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="2cf7c-323">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-324">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-325">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-325">Allowed From</span></span>

<span data-ttu-id="2cf7c-326">Konversation</span><span class="sxs-lookup"><span data-stu-id="2cf7c-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-327">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="2cf7c-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="2cf7c-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="2cf7c-329">Kör klienten i unicast-läge</span><span class="sxs-lookup"><span data-stu-id="2cf7c-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-330">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="2cf7c-331">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-331">Description</span></span>

<span data-ttu-id="2cf7c-332">Den här tjänsten startar klienten i unicast-läge där den regelbundet skickar en unicast-begäran till dess SNTP-server för en tids uppdatering.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="2cf7c-333">Om ett giltigt SNTP-meddelande tas emot återställs värdet för SNTP-klienten för maximal fördröjning utan en uppdatering, det inledande avsöknings intervallet och antalet felaktiga mottagna meddelanden som tas emot återställs.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="2cf7c-334">Om någon av dessa gränser överskrids sätter SNTP-klienten Server statusen till ogiltig trots att den fortfarande kommer att söka efter och vänta på att ta emot uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="2cf7c-335">Programmet kan avsöka SNTP-klientens aktivitet för Server status och om ogiltigt stoppa SNTP-klienten och initiera om den med en annan SNTP unicast-adress.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="2cf7c-336">Den kan också växla till en broadcast-SNTP-server.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="2cf7c-337">.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-338">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-338">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-339">**client_ptr** Pekare till klient kontroll block för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-340">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-340">Return Values</span></span>

- <span data-ttu-id="2cf7c-341">**NX_SUCCESS** (0x00) startade klienten i unicast-läge</span><span class="sxs-lookup"><span data-stu-id="2cf7c-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="2cf7c-342">**NX_SNTP_CLIENT_ALREADY_STARTED** -klienten (0xD0C) har redan startats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="2cf7c-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** -klienten (0xD01) har inte initierats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="2cf7c-344">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="2cf7c-345">NX_CALLER_ERROR (0x11) ogiltig anropare av tjänsten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="2cf7c-346">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-346">Allowed From</span></span>

<span data-ttu-id="2cf7c-347">Konversation</span><span class="sxs-lookup"><span data-stu-id="2cf7c-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-348">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="2cf7c-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="2cf7c-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="2cf7c-350">Ange lokal tid för SNTP-klienten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-351">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="2cf7c-352">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-352">Description</span></span>

<span data-ttu-id="2cf7c-353">Den här tjänsten ställer in lokal tid för SNTP-klienten med ingångs tiden i SNTP-format, t. ex. sekunder och "bråk", vilket är formatet för att lägga bråk delar av en sekund i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="2cf7c-354">Den är avsedd för att uppdatera SNTP-klientens lokala tid från en oberoende tids hållare, t. ex. en real tids klocka.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="2cf7c-355">SNTP-protokollet är avsett för uppdatering av SNTP-tid för att hålla lokal instämplingstid från "drivgarn".</span><span class="sxs-lookup"><span data-stu-id="2cf7c-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="2cf7c-356">Uppdatering av SNTP-serverns tid kan vara, men är inte avsedd att vara den enda ingången till SNTP-klientens lokala tid om det inte finns någon oberoende tids behållare på program enheten.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="2cf7c-357">Det här API: et kan också användas för att ge SNTP-klienten en grund tid innan du startar klient tråden för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="2cf7c-358">Den lokala tiden för SNTP-klienten jämförs med mottagna uppdateringar för giltiga tids data.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="2cf7c-359">Den första gången mottagna uppdateringen kan ha stor avvikelse.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="2cf7c-360">Det finns därför ett alternativ för SNTP-klienten som ignorerar avvikelsen vid den första uppdateringen.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="2cf7c-361">På så sätt kan SNTP-klienten starta utan en bas tid.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="2cf7c-362">Indata-tid kan hämtas från kända epok tider (vanligt vis på Internet) och beräknas som antalet sekunder sedan 1 januari 1900 (tills 2036 när en ny "epok" kommer att startas.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-363">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-363">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-364">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-365">**sekunder** Sekunders komponent för tids indatamängden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="2cf7c-366">**bråk** Subseconds-komponent i SNTP-bråk formatet</span><span class="sxs-lookup"><span data-stu-id="2cf7c-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-367">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-367">Return Values</span></span>

- <span data-ttu-id="2cf7c-368">**NX_SUCCESS** (0X00) har angett lokal tid</span><span class="sxs-lookup"><span data-stu-id="2cf7c-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="2cf7c-369">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-370">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-370">Allowed From</span></span>

<span data-ttu-id="2cf7c-371">Initiering</span><span class="sxs-lookup"><span data-stu-id="2cf7c-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-372">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="2cf7c-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="2cf7c-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="2cf7c-374">Ange uppdaterings återanrop för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-375">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="2cf7c-376">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-376">Description</span></span>

<span data-ttu-id="2cf7c-377">Den här tjänsten anger motringning för att meddela programmet när SNTP-klienten får en giltig tid uppdatering.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="2cf7c-378">Den tillhandahåller det faktiska SNTP-meddelandet och SNTP-klientens lokala tid (vanligt vis samma) i NTP-format.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="2cf7c-379">Programmet kan använda NTP-data direkt eller anropa *tjänsten nx_sntp_client_utility_display_date_time* för att konvertera tiden till läsligt format.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-380">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-380">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-381">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="2cf7c-382">**time_update_cb** Pekare till motringnings funktion</span><span class="sxs-lookup"><span data-stu-id="2cf7c-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-383">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-383">Return Values</span></span>

- <span data-ttu-id="2cf7c-384">**NX_SUCCESS** (0X00) har angett återanrop</span><span class="sxs-lookup"><span data-stu-id="2cf7c-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="2cf7c-385">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-386">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-386">Allowed From</span></span>

<span data-ttu-id="2cf7c-387">Initiering</span><span class="sxs-lookup"><span data-stu-id="2cf7c-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-388">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="2cf7c-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="2cf7c-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="2cf7c-390">Stoppa klient tråden för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-391">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="2cf7c-392">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-392">Description</span></span>

<span data-ttu-id="2cf7c-393">Den här tjänsten stoppar klient tråden för SNTP.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="2cf7c-394">Klient tråds aktiviteterna i SNTP, som körs i en oändlig slinga, pausas vid varje iteration för att släppa kontrollen över SNTP-klientens tillstånd och tillåta att program gör API-anrop på SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-395">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-395">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-396">**client_ptr** Pekare till klient kontroll block för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-397">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-397">Return Values</span></span>

- <span data-ttu-id="2cf7c-398">**NX_SUCCESS** (0X00) slutförde sluten klient tråd</span><span class="sxs-lookup"><span data-stu-id="2cf7c-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="2cf7c-399">**NX_SNTP_CLIENT_NOT_STARTED** (0XDB) SNTP-klient tråd inte Startad</span><span class="sxs-lookup"><span data-stu-id="2cf7c-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="2cf7c-400">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="2cf7c-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-401">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-401">Allowed From</span></span>

<span data-ttu-id="2cf7c-402">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-403">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="2cf7c-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="2cf7c-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="2cf7c-405">Konvertera en NTP-tid till datum-och tids sträng</span><span class="sxs-lookup"><span data-stu-id="2cf7c-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-406">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="2cf7c-407">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-407">Description</span></span>

<span data-ttu-id="2cf7c-408">Tjänsten konverterar lokal tid för SNTP-klienten till ett datum format för en månad och returnerar datumet i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="2cf7c-409">NX_SNTP_CURRENT_YEAR behöver inte vara samma år som den aktuella klient tiden, men det måste definieras.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-410">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-410">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-411">**client_ptr pekare till SNTP-klient**</span><span class="sxs-lookup"><span data-stu-id="2cf7c-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="2cf7c-412">**buffert** Pekare till data lagrets datum</span><span class="sxs-lookup"><span data-stu-id="2cf7c-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="2cf7c-413">**längd** Storlek på indatabufferten</span><span class="sxs-lookup"><span data-stu-id="2cf7c-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-414">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-414">Return Values</span></span>

- <span data-ttu-id="2cf7c-415">**NX_SUCCESS** (0x00) konverteringen lyckades</span><span class="sxs-lookup"><span data-stu-id="2cf7c-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="2cf7c-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR inte definierat eller så har ingen lokal klient tid etablerats</span><span class="sxs-lookup"><span data-stu-id="2cf7c-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="2cf7c-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0XD07) otillräcklig buffert längd</span><span class="sxs-lookup"><span data-stu-id="2cf7c-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="2cf7c-418">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-418">Allowed From</span></span>

<span data-ttu-id="2cf7c-419">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-420">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="2cf7c-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="2cf7c-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="2cf7c-422">Konvertera millisekunder till en NTP-fraktion</span><span class="sxs-lookup"><span data-stu-id="2cf7c-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-423">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="2cf7c-424">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-424">Description</span></span>

<span data-ttu-id="2cf7c-425">Den här tjänsten konverterar indataportar i millisekunder till komponenten NTP-fraktion.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="2cf7c-426">Den är avsedd för användning med program som har en start bas tid för SNTP-klienten men inte i formatet NTP-sekunder/bråk.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="2cf7c-427">Antalet millisekunder måste vara mindre än 1000 för att ett giltigt bråk ska vara giltigt.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-428">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-428">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-429">**millisekunder i millisekunder som ska konverteras**</span><span class="sxs-lookup"><span data-stu-id="2cf7c-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="2cf7c-430">**bråk** Pekare till millisekunder som omvandlats till bråk</span><span class="sxs-lookup"><span data-stu-id="2cf7c-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-431">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-431">Return Values</span></span>

- <span data-ttu-id="2cf7c-432">**NX_SUCCESS** (0x00) konverteringen lyckades</span><span class="sxs-lookup"><span data-stu-id="2cf7c-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="2cf7c-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Det gick inte att konvertera tiden till ett datum</span><span class="sxs-lookup"><span data-stu-id="2cf7c-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="2cf7c-434">NX_SNTP_INVALID_TIME (0xD30) ogiltig data inmatning för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-435">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-435">Allowed From</span></span>

<span data-ttu-id="2cf7c-436">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-437">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="2cf7c-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="2cf7c-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="2cf7c-439">Omvandla mikrosekunder till en NTP-fraktion</span><span class="sxs-lookup"><span data-stu-id="2cf7c-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-440">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="2cf7c-441">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-441">Description</span></span>

<span data-ttu-id="2cf7c-442">Den här tjänsten konverterar de inmatade mikrosekunderna till NTP-fraktions komponenten.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="2cf7c-443">Den är avsedd för användning med program som har en start bas tid för SNTP-klienten men inte i formatet NTP-sekunder/bråk.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="2cf7c-444">Antalet mikrosekunder måste vara mindre än 1000000 för att ett giltigt bråk ska vara giltigt.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-445">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-445">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-446">**mikrosekunder** Mikrosekunder att konvertera</span><span class="sxs-lookup"><span data-stu-id="2cf7c-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="2cf7c-447">**bråk** Pekare till mikrosekunder omvandlas till bråk</span><span class="sxs-lookup"><span data-stu-id="2cf7c-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-448">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-448">Return Values</span></span>

- <span data-ttu-id="2cf7c-449">**NX_SUCCESS** (0x00) konverteringen lyckades</span><span class="sxs-lookup"><span data-stu-id="2cf7c-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="2cf7c-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Det gick inte att konvertera tiden till ett datum</span><span class="sxs-lookup"><span data-stu-id="2cf7c-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="2cf7c-451">NX_SNTP_INVALID_TIME (0xD30) ogiltig data inmatning för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-452">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-452">Allowed From</span></span>

<span data-ttu-id="2cf7c-453">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-454">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="2cf7c-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="2cf7c-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="2cf7c-456">Omvandla en NTP-fraktion till mikrosekunder</span><span class="sxs-lookup"><span data-stu-id="2cf7c-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="2cf7c-457">Prototyp</span><span class="sxs-lookup"><span data-stu-id="2cf7c-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="2cf7c-458">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cf7c-458">Description</span></span>

<span data-ttu-id="2cf7c-459">Den här tjänsten konverterar den inmatade NTP-delen till mikrosekunder.</span><span class="sxs-lookup"><span data-stu-id="2cf7c-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2cf7c-460">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-460">Input Parameters</span></span>

- <span data-ttu-id="2cf7c-461">**bråk bråk att konvertera**</span><span class="sxs-lookup"><span data-stu-id="2cf7c-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="2cf7c-462">**mikrosekunder** Pekare till bråk som omvandlats till mikrosekunder</span><span class="sxs-lookup"><span data-stu-id="2cf7c-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="2cf7c-463">Retur värden</span><span class="sxs-lookup"><span data-stu-id="2cf7c-463">Return Values</span></span>

- <span data-ttu-id="2cf7c-464">**NX_SUCCESS** (0x00) konverteringen lyckades</span><span class="sxs-lookup"><span data-stu-id="2cf7c-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="2cf7c-465">NX_SNTP_INVALID_TIME (0xD30) ogiltig data inmatning för SNTP</span><span class="sxs-lookup"><span data-stu-id="2cf7c-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2cf7c-466">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="2cf7c-466">Allowed From</span></span>

<span data-ttu-id="2cf7c-467">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="2cf7c-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2cf7c-468">Exempel</span><span class="sxs-lookup"><span data-stu-id="2cf7c-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```