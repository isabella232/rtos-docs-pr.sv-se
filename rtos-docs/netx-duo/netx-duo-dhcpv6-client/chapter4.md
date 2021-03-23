---
title: Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DHCPv6-klient tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826073"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="0827b-103">Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-klient tjänster</span><span class="sxs-lookup"><span data-stu-id="0827b-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="0827b-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DHCPv6-klient tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="0827b-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0827b-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="0827b-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0827b-106">**nx_dhcpv6_client_create:** *skapa en DHCPV6-klient instans*</span><span class="sxs-lookup"><span data-stu-id="0827b-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="0827b-107">**nx_dhcpv6_client_delete:** *ta bort en DHCPV6-klient instans*</span><span class="sxs-lookup"><span data-stu-id="0827b-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="0827b-108">**nx_dhcpv6_create_ client_duid:** *skapa ett DUID för DHCPv6-klienten*</span><span class="sxs-lookup"><span data-stu-id="0827b-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="0827b-109">**nx_dhcpv6 _add_client_ia:** *Lägg till en Dhcpv6-klient identitets adress (IA)*</span><span class="sxs-lookup"><span data-stu-id="0827b-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="0827b-110">**nx_dhcpv6 _create_client_ia:** (*äldre Lägg till en DHCPv6-klients identitets adress (IA))*</span><span class="sxs-lookup"><span data-stu-id="0827b-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="0827b-111">**nx_dhcpv6_create_client_iana:** *skapa en Dhcpv6-klient identitets Association för icke-temporära adresser (IANA)*</span><span class="sxs-lookup"><span data-stu-id="0827b-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="0827b-112">**nx_dhcpv6_get_client_duid_time_id:** *Hämta tid-ID: t från DHCPv6-klientens DUID*</span><span class="sxs-lookup"><span data-stu-id="0827b-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="0827b-113">**nx_dhcpv6_client_set_interface:** *Ange klient nätverks gränssnittet för kommunikation med DHCPv6-servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="0827b-114">**nx_dhcpv6_get_IP_address:** *Hämta den globala IPv6-adress som tilldelats till DHCPv6-klienten*</span><span class="sxs-lookup"><span data-stu-id="0827b-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="0827b-115">**nx_dhcpv6_get_lease_time_data:** *Hämta T1, T2, giltiga och önskade livs längder för den globala klientens globala IPv6-adress*</span><span class="sxs-lookup"><span data-stu-id="0827b-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="0827b-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Hämta T1, T2, giltiga och önskade livs längder för DHCPv6-klientens IPv6-adress med adress index*</span><span class="sxs-lookup"><span data-stu-id="0827b-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="0827b-117">**nx_dhcpv6_get_iana_lease_time:** *Hämta T1 och T2 i identitets associeringen (IANA) som är lånad till DHCPv6-klienten*</span><span class="sxs-lookup"><span data-stu-id="0827b-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="0827b-118">**nx_dhcpv6_get_other_option_data:** *Hämta de angivna alternativ data, t. ex. domän namn eller tids zons Server*</span><span class="sxs-lookup"><span data-stu-id="0827b-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="0827b-119">**nx_dhcpv6_get_DNS_server_address:** *Hämta DNS-serveradress vid angivet index till DHCPv6-klientens DNS-server lista*</span><span class="sxs-lookup"><span data-stu-id="0827b-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="0827b-120">**nx_dhcpv6_get_time_accrued:** *Hämta den uppskjutna tiden som det globala IPv6-adresslån har bundits till DHCPv6-klienten*</span><span class="sxs-lookup"><span data-stu-id="0827b-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="0827b-121">**nx_dhcpv6_get_time_server_address:** *Hämta tids server adress vid angivet index i DHCPv6-klientens tids server lista*</span><span class="sxs-lookup"><span data-stu-id="0827b-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="0827b-122">**nx_dhcpv6_get_valid_ip_address_count:** *Hämta antalet IPv6-adresser som har tilldelats DHCPv6-klienten*</span><span class="sxs-lookup"><span data-stu-id="0827b-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="0827b-123">**nx_dhcpv6_reinitialize:** *initiera om DHCPv6 för att starta om DHCPv6-klientens tillstånds dator och köra DHCPv6-protokollet igen*</span><span class="sxs-lookup"><span data-stu-id="0827b-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="0827b-124">**nx_dhcpv6_request_confirm:** *skicka en Confirm-begäran till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="0827b-125">**nx_dhcpv6_request_inform_request:** S *Avsluta ett meddelande om begäran till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="0827b-126">**nx_dhcpv6_request_release:** *skicka en release-begäran till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="0827b-127">**nx_dhcpv6_request_option_DNS_server:** *Lägg till alternativet DNS-server i klient alternativ begär ande data i begär ande meddelanden till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="0827b-128">**nx_dhcpv6_request_option_FQDN:** *Lägg till alternativet FQDN i klient alternativ begär ande data i begär ande meddelanden till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="0827b-129">**nx_dhcpv6_request_option_domain_name:** *Lägg till alternativet domän namn i klient alternativ begär ande data i begär ande meddelanden till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="0827b-130">**nx_dhcpv6_request_option_time_server:** *Lägg till alternativet för tids server i klient alternativ begär ande data i begär ande meddelanden till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="0827b-131">**nx_dhcpv6_request_option_timezone:** *Lägg till alternativet tidszon i begär ande data för klient alternativ i begär ande meddelanden till servern*</span><span class="sxs-lookup"><span data-stu-id="0827b-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="0827b-132">**nx_dhcpv6_request_solicit:** *skicka en begäran om DHCPv6-begäran till valfri server i klient nätverket (sändning)*</span><span class="sxs-lookup"><span data-stu-id="0827b-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="0827b-133">**nx_dhcpv6_request_solicit_rapid:** *skicka en begäran om DHCPv6-begäran till valfri server på klient nätverket (sändning) med alternativ uppsättningen för snabb incheckning*</span><span class="sxs-lookup"><span data-stu-id="0827b-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="0827b-134">**nx_dhcpv6_resume:** *återuppta DHCPV6-klient bearbetning*</span><span class="sxs-lookup"><span data-stu-id="0827b-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="0827b-135">**nx_dhcpv6_start:** *starta aktiviteten dhcpv6 client Thread. OBS! detta motsvarar inte start av DHCPv6-tillstånds datorn och skickar ingen begär ande förfrågan*</span><span class="sxs-lookup"><span data-stu-id="0827b-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="0827b-136">**nx_dhcpv6_stop:** *Stoppa aktiviteten DHCPV6 klient tråd*</span><span class="sxs-lookup"><span data-stu-id="0827b-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="0827b-137">**nx_dhcpv6_suspend:** *inaktivera aktiviteten för DHCPv6-klient tråd*</span><span class="sxs-lookup"><span data-stu-id="0827b-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="0827b-138">**nx_dhcpv6_set_time_accrued:** *Ange den tid som ska periodiseras på det globala klientens IPv6-adresslån i klient posten.*</span><span class="sxs-lookup"><span data-stu-id="0827b-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="0827b-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="0827b-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="0827b-140">Skapa en DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-141">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="0827b-142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-142">Description</span></span>

<span data-ttu-id="0827b-143">Den här tjänsten skapar en DHCPv6-klient instans inklusive återanrops funktioner.</span><span class="sxs-lookup"><span data-stu-id="0827b-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-144">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-144">Input Parameters</span></span>

- <span data-ttu-id="0827b-145">**dhcpv6_ptr** Pekare till DHCPv6-kontroll block</span><span class="sxs-lookup"><span data-stu-id="0827b-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="0827b-146">**ip_ptr** Pekare till klientens IP-instans</span><span class="sxs-lookup"><span data-stu-id="0827b-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="0827b-147">**name_ptr** Pekare till namn på DHCPv6-instans</span><span class="sxs-lookup"><span data-stu-id="0827b-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="0827b-148">**packet_pool_ptr** Pekare till klient paketets pool</span><span class="sxs-lookup"><span data-stu-id="0827b-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="0827b-149">**stack_ptr** Pekare till klientens stack minne</span><span class="sxs-lookup"><span data-stu-id="0827b-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="0827b-150">**stack_size** Storlek på klientens stack minne</span><span class="sxs-lookup"><span data-stu-id="0827b-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="0827b-151">**dhcpv6_state_change_notify** Pekare till callback-funktionen anropas när klienten initierar en ny DHCPv6-begäran till servern</span><span class="sxs-lookup"><span data-stu-id="0827b-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="0827b-152">**dhcpv6_server_error_handler** Pekare till callback-funktionen anropas när klienten får en fel status från servern</span><span class="sxs-lookup"><span data-stu-id="0827b-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-153">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-153">Return Values</span></span>

- <span data-ttu-id="0827b-154">**NX_SUCCESS** (0X00) lyckad klient skapande</span><span class="sxs-lookup"><span data-stu-id="0827b-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="0827b-155">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-156">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-157">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-157">Allowed From</span></span>

<span data-ttu-id="0827b-158">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-159">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-160">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-160">See Also</span></span>

- <span data-ttu-id="0827b-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="0827b-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="0827b-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="0827b-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="0827b-163">Ta bort en DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-164">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-165">Description</span></span>

<span data-ttu-id="0827b-166">Den här tjänsten tar bort en tidigare skapad DHCPv6-klient instans.</span><span class="sxs-lookup"><span data-stu-id="0827b-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-167">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-167">Input Parameters</span></span>

- <span data-ttu-id="0827b-168">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-169">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-169">Return Values</span></span>

- <span data-ttu-id="0827b-170">**NX_SUCCESS** (0X00) lyckade DHCPv6-borttagning</span><span class="sxs-lookup"><span data-stu-id="0827b-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="0827b-171">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-172">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-173">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-173">Allowed From</span></span>

<span data-ttu-id="0827b-174">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-175">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-176">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-176">See Also</span></span>

- <span data-ttu-id="0827b-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="0827b-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="0827b-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="0827b-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="0827b-179">Anger klientens nätverks gränssnitt för DHCPv6</span><span class="sxs-lookup"><span data-stu-id="0827b-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-180">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="0827b-181">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-181">Description</span></span>

<span data-ttu-id="0827b-182">Den här tjänsten anger klientens nätverks gränssnitt för att kommunicera med DHCPv6-servrarna till det angivna indexet för indataport.</span><span class="sxs-lookup"><span data-stu-id="0827b-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-183">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-183">Input Parameters</span></span>

- <span data-ttu-id="0827b-184">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-185">**interface_index** Index indikerar nätverks gränssnitt</span><span class="sxs-lookup"><span data-stu-id="0827b-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-186">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-186">Return Values</span></span>

- <span data-ttu-id="0827b-187">Gränssnittet för **NX_SUCCESS** (0x00) har angetts</span><span class="sxs-lookup"><span data-stu-id="0827b-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="0827b-188">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-189">NX_INVALID_INTERFACE (0x4C) ogiltigt inmatade gränssnitts index</span><span class="sxs-lookup"><span data-stu-id="0827b-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-190">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-190">Allowed From</span></span>

<span data-ttu-id="0827b-191">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-192">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-193">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-193">See Also</span></span>

- <span data-ttu-id="0827b-194">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="0827b-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="0827b-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="0827b-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="0827b-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="0827b-197">Anger mål adressen där DHCPv6-meddelande ska skickas till</span><span class="sxs-lookup"><span data-stu-id="0827b-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-198">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="0827b-199">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-199">Description</span></span>

<span data-ttu-id="0827b-200">Den här tjänsten anger mål adressen där DHCPv6-meddelandet ska skickas.</span><span class="sxs-lookup"><span data-stu-id="0827b-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="0827b-201">Som standard är ALL_DHCP_Relay_Agents_and_Servers (FF02:: 1:2).</span><span class="sxs-lookup"><span data-stu-id="0827b-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-202">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-202">Input Parameters</span></span>

- <span data-ttu-id="0827b-203">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-204">**destination_address** Mål adress</span><span class="sxs-lookup"><span data-stu-id="0827b-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-205">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-205">Return Values</span></span>

- <span data-ttu-id="0827b-206">Gränssnittet för **NX_SUCCESS** (0x00) har angetts</span><span class="sxs-lookup"><span data-stu-id="0827b-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="0827b-207">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-208">NX_DHCPV6_PARAM_ERROR (0xE93) stycke fel</span><span class="sxs-lookup"><span data-stu-id="0827b-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-209">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-209">Allowed From</span></span>

<span data-ttu-id="0827b-210">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-211">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-212">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-212">See Also</span></span>

- <span data-ttu-id="0827b-213">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="0827b-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="0827b-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="0827b-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="0827b-216">Skapa DUID-objekt för klient</span><span class="sxs-lookup"><span data-stu-id="0827b-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-217">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="0827b-218">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-218">Description</span></span>

<span data-ttu-id="0827b-219">Den här tjänsten skapar klienten DUID med indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="0827b-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="0827b-220">Om tiden inte anges och DUID-typen indikerar länk lager med tid, kommer den här funktionen att tillhandahålla en tid som innehåller en slumpmässig faktor för unikhet.</span><span class="sxs-lookup"><span data-stu-id="0827b-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="0827b-221">Leverantörs tilldelning (Enterprise) DUID-typer stöds inte.</span><span class="sxs-lookup"><span data-stu-id="0827b-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-222">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-222">Input Parameters</span></span>

- <span data-ttu-id="0827b-223">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-224">**duid_type** Typ av DUID (maskin vara, företag osv.)</span><span class="sxs-lookup"><span data-stu-id="0827b-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="0827b-225">**hardware_type** Nätverks maskin vara, t. ex. IEEE 802</span><span class="sxs-lookup"><span data-stu-id="0827b-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="0827b-226">**tid** Värde som används för att skapa unik identifierare</span><span class="sxs-lookup"><span data-stu-id="0827b-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-227">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-227">Return Values</span></span>

- <span data-ttu-id="0827b-228">**NX_SUCCESS** (0x00) ett lyckat klient-DUID skapades</span><span class="sxs-lookup"><span data-stu-id="0827b-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="0827b-229">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-230">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="0827b-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID-typen är okänd eller stöds inte</span><span class="sxs-lookup"><span data-stu-id="0827b-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="0827b-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID-maskin varu typen är okänd eller stöds inte</span><span class="sxs-lookup"><span data-stu-id="0827b-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-233">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-233">Allowed From</span></span>

<span data-ttu-id="0827b-234">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-235">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-236">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-236">See Also</span></span>

- <span data-ttu-id="0827b-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="0827b-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="0827b-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="0827b-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="0827b-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="0827b-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="0827b-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="0827b-241">Lägg till en identitets koppling till klienten</span><span class="sxs-lookup"><span data-stu-id="0827b-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-242">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="0827b-243">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-243">Description</span></span>

<span data-ttu-id="0827b-244">Den här tjänsten är identisk med *nx_dhcpv6_add_client_ia* -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="0827b-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="0827b-245">Den lägger till en klient identitets Association genom att fylla i klient posten med de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0827b-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="0827b-246">Ange de här parametrarna till oändlighet för att begära maximalt antal prioriterade och giltiga livstider.</span><span class="sxs-lookup"><span data-stu-id="0827b-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="0827b-247">Om du vill lägga till mer än ett IA i en DHCPv6-klient anger du NX_DHCPV6_MAX_IA_ADDRESS till ett värde som är högre än standardvärdet 1.</span><span class="sxs-lookup"><span data-stu-id="0827b-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-248">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-248">Input Parameters</span></span>

- <span data-ttu-id="0827b-249">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-250">**ipv6_address** Pekare till NetX Duo IP-adressblock</span><span class="sxs-lookup"><span data-stu-id="0827b-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="0827b-251">**preferred_lifetime** Tids längd innan IP-adressen är föråldrad</span><span class="sxs-lookup"><span data-stu-id="0827b-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="0827b-252">**valid_lifetime** Tids längd innan IP-adressen har gått ut</span><span class="sxs-lookup"><span data-stu-id="0827b-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-253">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-253">Return Values</span></span>

- <span data-ttu-id="0827b-254">**NX_SUCCESS** (0X00) lyckad klient-IA har lagts till</span><span class="sxs-lookup"><span data-stu-id="0827b-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="0827b-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) DUBBLETT av IA-adress</span><span class="sxs-lookup"><span data-stu-id="0827b-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="0827b-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA överskrider den högsta antalet IAS-klienter som kan lagra</span><span class="sxs-lookup"><span data-stu-id="0827b-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="0827b-257">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) ogiltig (t. ex. null) IA-adress i IA</span><span class="sxs-lookup"><span data-stu-id="0827b-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="0827b-259">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0827b-260">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-260">Allowed From</span></span>

<span data-ttu-id="0827b-261">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-262">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-263">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-263">See Also</span></span>

- <span data-ttu-id="0827b-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="0827b-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="0827b-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="0827b-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="0827b-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="0827b-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="0827b-268">Skapa en identitets Association (icke-tillfällig) för klienten</span><span class="sxs-lookup"><span data-stu-id="0827b-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-269">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="0827b-270">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-270">Description</span></span>

<span data-ttu-id="0827b-271">Den här tjänsten skapar en klient som inte har en tillfällig identitets Association (IANA) från de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0827b-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="0827b-272">Om du vill ställa in T1-och T2-tiderna till maximum (oändlighet) i DHCPv6-klient förfrågningarna ställer du in dessa parametrar på NX_DHCPV6_INFINITE_LEASE.</span><span class="sxs-lookup"><span data-stu-id="0827b-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="0827b-273">En klient har bara en IANA.</span><span class="sxs-lookup"><span data-stu-id="0827b-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-274">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-274">Input Parameters</span></span>

- <span data-ttu-id="0827b-275">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-276">**IA_ident** Unikt ID för identitets Association</span><span class="sxs-lookup"><span data-stu-id="0827b-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="0827b-277">**T1** När klienten måste starta förnyelsen av IPv6-adressen</span><span class="sxs-lookup"><span data-stu-id="0827b-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="0827b-278">**T2** När klienten måste starta theIPv6 Address binding</span><span class="sxs-lookup"><span data-stu-id="0827b-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-279">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-279">Return Values</span></span>

- <span data-ttu-id="0827b-280">**NX_SUCCESS** (0x00) skapade IANA</span><span class="sxs-lookup"><span data-stu-id="0827b-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="0827b-281">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-282">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-283">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-283">Allowed From</span></span>

<span data-ttu-id="0827b-284">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-285">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-286">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-286">See Also</span></span>

- <span data-ttu-id="0827b-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="0827b-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="0827b-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="0827b-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="0827b-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="0827b-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="0827b-291">Lägg till en identitets koppling till klienten</span><span class="sxs-lookup"><span data-stu-id="0827b-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-292">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="0827b-293">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-293">Description</span></span>

<span data-ttu-id="0827b-294">Den här tjänsten lägger till en klient identitets Association genom att fylla i klient posten med de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0827b-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="0827b-295">Ange de här parametrarna till oändlighet för att begära maximalt antal prioriterade och giltiga livstider.</span><span class="sxs-lookup"><span data-stu-id="0827b-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="0827b-296">Om du vill lägga till mer än ett IA i en DHCPv6-klient anger du NX_DHCPV6_MAX_IA_ADDRESS till ett värde som är högre än standardvärdet 1.</span><span class="sxs-lookup"><span data-stu-id="0827b-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-297">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-297">Input Parameters</span></span>

- <span data-ttu-id="0827b-298">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-299">**ipv6_address** Pekare till NetX Duo IP-adressblock</span><span class="sxs-lookup"><span data-stu-id="0827b-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="0827b-300">**preferred_lifetime** Tids längd innan IP-adressen är föråldrad</span><span class="sxs-lookup"><span data-stu-id="0827b-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="0827b-301">**valid_lifetime** Tids längd innan IP-adressen har gått ut</span><span class="sxs-lookup"><span data-stu-id="0827b-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="0827b-302">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-302">Return Values</span></span>

- <span data-ttu-id="0827b-303">**NX_SUCCESS** (0X00) lyckad klient-IA har lagts till</span><span class="sxs-lookup"><span data-stu-id="0827b-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="0827b-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) DUBBLETT av IA-adress</span><span class="sxs-lookup"><span data-stu-id="0827b-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="0827b-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA överskrider den högsta antalet IAS-klienter som kan lagra</span><span class="sxs-lookup"><span data-stu-id="0827b-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="0827b-306">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) ogiltig (t. ex. null) IA-adress i IA</span><span class="sxs-lookup"><span data-stu-id="0827b-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="0827b-308">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="0827b-309">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-309">Allowed From</span></span>

<span data-ttu-id="0827b-310">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-311">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-312">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-312">See Also</span></span>

- <span data-ttu-id="0827b-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="0827b-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="0827b-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="0827b-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="0827b-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="0827b-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="0827b-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="0827b-317">Hämtar tid-ID från klientens DUID</span><span class="sxs-lookup"><span data-stu-id="0827b-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-318">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="0827b-319">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-319">Description</span></span>

<span data-ttu-id="0827b-320">Den här tjänsten hämtar fältet tid-ID från klientens DUID.</span><span class="sxs-lookup"><span data-stu-id="0827b-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="0827b-321">Om programmet först måste anropa *nx_dhcpv6_create_client_duid*, för att fylla i klientens DUID i Dhcpv6-klient instansen, eller så har det ett null-värde för det här fältet.</span><span class="sxs-lookup"><span data-stu-id="0827b-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="0827b-322">Avsikten är att programmet ska kunna spara dessa data och presentera samma klient-DUID på servern, inklusive fältet Time, i omstarter.</span><span class="sxs-lookup"><span data-stu-id="0827b-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-323">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-323">Input Parameters</span></span>

- <span data-ttu-id="0827b-324">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-325">**TIME_ID** Pekare till datum fältet för klientens DUID</span><span class="sxs-lookup"><span data-stu-id="0827b-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-326">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-326">Return Values</span></span>

- <span data-ttu-id="0827b-327">**NX_SUCCESS** (0x00) IP-adresslån har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="0827b-328">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-329">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-330">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-330">Allowed From</span></span>

<span data-ttu-id="0827b-331">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-332">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-333">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-333">See Also</span></span>

- <span data-ttu-id="0827b-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="0827b-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="0827b-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="0827b-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="0827b-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="0827b-339">Hämtar klientens globala IPv6-adress</span><span class="sxs-lookup"><span data-stu-id="0827b-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-340">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="0827b-341">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-341">Description</span></span>

<span data-ttu-id="0827b-342">Den här tjänsten hämtar klientens globala IPv6-adress.</span><span class="sxs-lookup"><span data-stu-id="0827b-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="0827b-343">Om klienten inte har en giltig adress returneras en fel status.</span><span class="sxs-lookup"><span data-stu-id="0827b-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="0827b-344">Om en klient har fler än en global IPv6-adress returneras den primära IPv6-adressen.</span><span class="sxs-lookup"><span data-stu-id="0827b-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-345">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-345">Input Parameters</span></span>

- <span data-ttu-id="0827b-346">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-347">**ip_address** Pekare till IPv6-adress</span><span class="sxs-lookup"><span data-stu-id="0827b-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-348">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-348">Return Values</span></span>

- <span data-ttu-id="0827b-349">**NX_SUCCESS** (0X00) IPv6-adress har tilldelats</span><span class="sxs-lookup"><span data-stu-id="0827b-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="0827b-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0XEAD) IPv6-adressen är inte giltig</span><span class="sxs-lookup"><span data-stu-id="0827b-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="0827b-351">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-352">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-353">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-353">Allowed From</span></span>

<span data-ttu-id="0827b-354">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-355">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="0827b-356">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-356">See Also</span></span>

- <span data-ttu-id="0827b-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="0827b-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="0827b-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="0827b-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="0827b-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="0827b-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="0827b-362">Hämtar information om låne tid för klientens IA-adress</span><span class="sxs-lookup"><span data-stu-id="0827b-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-363">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="0827b-364">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-364">Description</span></span>

<span data-ttu-id="0827b-365">Den här tjänsten hämtar klientens globala data för IA-adress.</span><span class="sxs-lookup"><span data-stu-id="0827b-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="0827b-366">Om status för klientens IA-adress är ogiltig anges tids data till noll och statusen för lyckad slut för ande har returnerats.</span><span class="sxs-lookup"><span data-stu-id="0827b-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="0827b-367">Om en klient har fler än en global IPv6-adress returneras data för primär data källor.</span><span class="sxs-lookup"><span data-stu-id="0827b-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-368">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-368">Input Parameters</span></span>

- <span data-ttu-id="0827b-369">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-370">**T1** Pekare till IA-adress förnyelse tid</span><span class="sxs-lookup"><span data-stu-id="0827b-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="0827b-371">**T2** Pekare till tid i IA-adress OMBINDNING</span><span class="sxs-lookup"><span data-stu-id="0827b-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="0827b-372">**preferred_lifetime** Pekare till tid när IA-adressen är föråldrad</span><span class="sxs-lookup"><span data-stu-id="0827b-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="0827b-373">**valid_lifetime** Pekare till tid när IA-adressen har upphört att gälla</span><span class="sxs-lookup"><span data-stu-id="0827b-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-374">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-374">Return Values</span></span>

- <span data-ttu-id="0827b-375">**NX_SUCCESS** (0X00) IA låne data har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="0827b-376">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-377">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-378">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-378">Allowed From</span></span>

<span data-ttu-id="0827b-379">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-380">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-381">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-381">See Also</span></span>

- <span data-ttu-id="0827b-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="0827b-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="0827b-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="0827b-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="0827b-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="0827b-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="0827b-387">nx_dhcpv6_get_iana lease_time</span><span class="sxs-lookup"><span data-stu-id="0827b-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="0827b-388">Hämta klientens information om låne tid för IANA</span><span class="sxs-lookup"><span data-stu-id="0827b-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-389">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="0827b-390">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-390">Description</span></span>

<span data-ttu-id="0827b-391">Den här tjänsten hämtar klientens globala IA-NA-data (T1 och T2).</span><span class="sxs-lookup"><span data-stu-id="0827b-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="0827b-392">Om ingen av klientens IA-NA-adresser har en giltig adress status anges tids data till noll, och statusen för lyckad slut för ande har returnerats.</span><span class="sxs-lookup"><span data-stu-id="0827b-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="0827b-393">Om en klient har fler än en global IPv6-adress returneras data för primär data källor.</span><span class="sxs-lookup"><span data-stu-id="0827b-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-394">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-394">Input Parameters</span></span>

- <span data-ttu-id="0827b-395">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-396">**T1** Pekare till tid för att påbörja låne förnyelse</span><span class="sxs-lookup"><span data-stu-id="0827b-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="0827b-397">**T2** Pekare till tid för att starta låne OMBINDNING</span><span class="sxs-lookup"><span data-stu-id="0827b-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-398">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-398">Return Values</span></span>

- <span data-ttu-id="0827b-399">**NX_SUCCESS** (0X00) IANA-adresslån har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="0827b-400">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-401">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-402">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-402">Allowed From</span></span>

<span data-ttu-id="0827b-403">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-404">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-405">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-405">See Also</span></span>

- <span data-ttu-id="0827b-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="0827b-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="0827b-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="0827b-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="0827b-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="0827b-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="0827b-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="0827b-412">Hämta antalet klientens giltiga IA-adresser</span><span class="sxs-lookup"><span data-stu-id="0827b-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-413">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="0827b-414">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-414">Description</span></span>

<span data-ttu-id="0827b-415">Tjänsten hämtar antalet giltiga IPv6-adresser för klienten.</span><span class="sxs-lookup"><span data-stu-id="0827b-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="0827b-416">En giltig IPv6-adress är kopplad till klienten och är registrerad hos IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="0827b-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-417">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-417">Input Parameters</span></span>

- <span data-ttu-id="0827b-418">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-419">**address_count** Pekare till adress antal att returnera</span><span class="sxs-lookup"><span data-stu-id="0827b-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-420">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-420">Return Values</span></span>

- <span data-ttu-id="0827b-421">**NX_SUCCESS** (0X00) IANA-adresslån har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="0827b-422">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-423">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-424">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-424">Allowed From</span></span>

<span data-ttu-id="0827b-425">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-426">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="0827b-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="0827b-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="0827b-428">Hämta klientens IA-data med adress index</span><span class="sxs-lookup"><span data-stu-id="0827b-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-429">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="0827b-430">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-430">Description</span></span>

<span data-ttu-id="0827b-431">Den här tjänsten hämtar klientens IA-adress och låne data efter adress index.</span><span class="sxs-lookup"><span data-stu-id="0827b-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="0827b-432">Om ett ogiltigt index anges eller IPv6-adressen i det indexet inte är giltig, returnerar tjänsten en NX_DHCPV6_IA_ADDRESS_NOT_VALID fel status.</span><span class="sxs-lookup"><span data-stu-id="0827b-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-433">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-433">Input Parameters</span></span>

- <span data-ttu-id="0827b-434">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-435">**address_index** Index i DHCPv6 IA-tabell</span><span class="sxs-lookup"><span data-stu-id="0827b-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="0827b-436">**ip_address** Pekare till IPv6-adress att hämta</span><span class="sxs-lookup"><span data-stu-id="0827b-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="0827b-437">**preferred_lifetime** Pekare till tid när IA-adressen är föråldrad</span><span class="sxs-lookup"><span data-stu-id="0827b-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="0827b-438">**valid_lifetime** Pekare till tid när IA-adressen har upphört att gälla</span><span class="sxs-lookup"><span data-stu-id="0827b-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-439">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-439">Return Values</span></span>

- <span data-ttu-id="0827b-440">**NX_SUCCESS** (0X00) IANA-data har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="0827b-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0XEAD) ett ogiltigt index eller ingen giltig IPv6-adress med det angivna indexet</span><span class="sxs-lookup"><span data-stu-id="0827b-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="0827b-442">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-443">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-444">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-444">Allowed From</span></span>

<span data-ttu-id="0827b-445">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-446">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="0827b-447">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-447">See Also</span></span>

- <span data-ttu-id="0827b-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="0827b-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="0827b-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="0827b-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="0827b-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="0827b-452">Hämtar DNS-serveradress</span><span class="sxs-lookup"><span data-stu-id="0827b-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-453">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="0827b-454">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-454">Description</span></span>

<span data-ttu-id="0827b-455">Den här tjänsten hämtar DNS-serverns IPv6-Datadata med det angivna indexet i klient listan.</span><span class="sxs-lookup"><span data-stu-id="0827b-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="0827b-456">Om listan inte innehåller någon server adress vid indexet returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="0827b-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="0827b-457">Indexet får inte överskrida storleken på listan över DNS-servrar som anges av alternativet för att konfigurera användare NX_DHCPV6_NUM_DNS_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="0827b-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-458">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-458">Input Parameters</span></span>

- <span data-ttu-id="0827b-459">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-460">**index** Index i listan DNS-Server</span><span class="sxs-lookup"><span data-stu-id="0827b-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="0827b-461">**server_address** Pekare till server adress buffer</span><span class="sxs-lookup"><span data-stu-id="0827b-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-462">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-462">Return Values</span></span>

- <span data-ttu-id="0827b-463">**NX_SUCCESSs** adress (0x00) har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="0827b-464">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-465">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-466">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-466">Allowed From</span></span>

<span data-ttu-id="0827b-467">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-468">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-469">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-469">See Also</span></span>

- <span data-ttu-id="0827b-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="0827b-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="0827b-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="0827b-474">Hämtar DHCPv6-alternativ data</span><span class="sxs-lookup"><span data-stu-id="0827b-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-475">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="0827b-476">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-476">Description</span></span>

<span data-ttu-id="0827b-477">Den här tjänsten hämtar DHCPv6-alternativ data från ett DHCPv6-meddelande för den angivna alternativ koden.</span><span class="sxs-lookup"><span data-stu-id="0827b-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-478">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-478">Input Parameters</span></span>

- <span data-ttu-id="0827b-479">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-480">**alternativ** kod för alternativ kod för vilka data som ska hämtas</span><span class="sxs-lookup"><span data-stu-id="0827b-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="0827b-481">**buffert** Pekare till buffert för att kopiera data till</span><span class="sxs-lookup"><span data-stu-id="0827b-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="0827b-482">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-482">Return Values</span></span>

- <span data-ttu-id="0827b-483">**NX_SUCCESS** (0X00) alternativ data har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="0827b-484">**NX_DHCPV6_UNKNOWN_OPTION** (0XEAB) Okänd/alternativ kod som inte stöds</span><span class="sxs-lookup"><span data-stu-id="0827b-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="0827b-485">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-486">NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="0827b-487">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-488">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-488">Allowed From</span></span>

<span data-ttu-id="0827b-489">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-490">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-491">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-491">See Also</span></span>

- <span data-ttu-id="0827b-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="0827b-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="0827b-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="0827b-496">Hämtar den tid som periodiseras på klientens IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="0827b-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-497">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="0827b-498">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-498">Description</span></span>

<span data-ttu-id="0827b-499">Den här tjänsten hämtar den tid som periodiseras på klientens IPv6-adresslån.</span><span class="sxs-lookup"><span data-stu-id="0827b-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="0827b-500">Funktionen kontrollerar alla IPv6-adresser som tilldelats klienten för den första giltiga adressen.</span><span class="sxs-lookup"><span data-stu-id="0827b-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="0827b-501">Om inga giltiga adresser hittas returneras ett nollvärde för den uppskjutna tiden.</span><span class="sxs-lookup"><span data-stu-id="0827b-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-502">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-502">Input Parameters</span></span>

- <span data-ttu-id="0827b-503">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-504">**time_accrued** Pekare till tid som periodiseras i IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="0827b-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-505">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-505">Return Values</span></span>

- <span data-ttu-id="0827b-506">**NX_SUCCESS** (0X00) upplupen tid har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="0827b-507">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-508">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-509">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-509">Allowed From</span></span>

<span data-ttu-id="0827b-510">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-511">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-512">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-512">See Also</span></span>

- <span data-ttu-id="0827b-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="0827b-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="0827b-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="0827b-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="0827b-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="0827b-518">Hämtar tids server adress</span><span class="sxs-lookup"><span data-stu-id="0827b-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-519">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="0827b-520">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-520">Description</span></span>

<span data-ttu-id="0827b-521">Den här tjänsten hämtar Time servers IPv6-Datadata vid det angivna indexet i klient listan.</span><span class="sxs-lookup"><span data-stu-id="0827b-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="0827b-522">Om listan inte innehåller någon server adress vid indexet returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="0827b-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="0827b-523">Indexet får inte överskrida storleken på tids server listan som anges av alternativet för att konfigurera användare NX_DHCPV6_NUM_TIME_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="0827b-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-524">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-524">Input Parameters</span></span>

- <span data-ttu-id="0827b-525">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-526">**index** Index i tids server listan</span><span class="sxs-lookup"><span data-stu-id="0827b-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="0827b-527">**server_address** Pekare till server adress buffer</span><span class="sxs-lookup"><span data-stu-id="0827b-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-528">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-528">Return Values</span></span>

- <span data-ttu-id="0827b-529">**NX_SUCCESSs** adress (0x00) har hämtats</span><span class="sxs-lookup"><span data-stu-id="0827b-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="0827b-530">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-531">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-532">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-532">Allowed From</span></span>

<span data-ttu-id="0827b-533">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-534">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-535">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-535">See Also</span></span>

- <span data-ttu-id="0827b-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="0827b-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="0827b-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="0827b-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="0827b-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="0827b-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="0827b-541">Ta bort klientens IP-adress från IP-tabellen</span><span class="sxs-lookup"><span data-stu-id="0827b-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-542">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-543">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-543">Description</span></span>

<span data-ttu-id="0827b-544">Den här tjänsten initierar om klienten för att starta om DHCPv6-tillstånds datorn och köra DHCPv6-protokollet igen.</span><span class="sxs-lookup"><span data-stu-id="0827b-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="0827b-545">Detta är inte nödvändigt om klienten inte tidigare har startat DHPCv6-tillstånds datorn eller tilldelats några IPv6-adresser.</span><span class="sxs-lookup"><span data-stu-id="0827b-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="0827b-546">Adresserna som sparas i DHCPv6-klienten samt registrerade med IP-instansen är båda rensade.</span><span class="sxs-lookup"><span data-stu-id="0827b-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="0827b-547">Programmet måste fortfarande starta DHCPv6-klienten med hjälp av *nx_dhcpv6_start tjänsten* och påbörja begäran om IPv6-adress tilldelning genom att anropa *nx_dhcpv6_request_solicit*.</span><span class="sxs-lookup"><span data-stu-id="0827b-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-548">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-548">Input Parameters</span></span>

- <span data-ttu-id="0827b-549">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-550">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-550">Return Values</span></span>

- <span data-ttu-id="0827b-551">**NX_SUCCESSs** adress (0x00) har tagits bort</span><span class="sxs-lookup"><span data-stu-id="0827b-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="0827b-552">**NX_DHCPV6_ALREADY_STARTED** (0XE91) DHCPv6-klienten körs redan</span><span class="sxs-lookup"><span data-stu-id="0827b-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="0827b-553">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-554">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-555">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-555">Allowed From</span></span>

<span data-ttu-id="0827b-556">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-557">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-558">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-558">See Also</span></span>

- <span data-ttu-id="0827b-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="0827b-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="0827b-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="0827b-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="0827b-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="0827b-562">Bearbeta klientens bekräftelse tillstånd</span><span class="sxs-lookup"><span data-stu-id="0827b-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-563">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-564">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-564">Description</span></span>

<span data-ttu-id="0827b-565">Den här tjänsten skickar en bekräftelse förfrågan.</span><span class="sxs-lookup"><span data-stu-id="0827b-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="0827b-566">Om ett svar tas emot från servern uppdaterar DHCPv6-klienten dess låne parametrar med mottagna data.</span><span class="sxs-lookup"><span data-stu-id="0827b-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-567">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-567">Input Parameters</span></span>

- <span data-ttu-id="0827b-568">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-569">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-569">Return Values</span></span>

- <span data-ttu-id="0827b-570">**NX_SUCCESS** (0X00) bekräfta att meddelandet har skickats och bearbetats</span><span class="sxs-lookup"><span data-stu-id="0827b-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="0827b-571">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-572">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-573">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-573">Allowed From</span></span>

<span data-ttu-id="0827b-574">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-575">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-576">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-576">See Also</span></span>

- <span data-ttu-id="0827b-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="0827b-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="0827b-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="0827b-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="0827b-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="0827b-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="0827b-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="0827b-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="0827b-581">Behandla klientens tillstånd för att meddela begäran</span><span class="sxs-lookup"><span data-stu-id="0827b-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-582">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-583">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-583">Description</span></span>

<span data-ttu-id="0827b-584">Den här tjänsten skickar ett meddelande om meddelande om begäran.</span><span class="sxs-lookup"><span data-stu-id="0827b-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="0827b-585">Om ett svar tas emot bearbetas svaret för att fastställa att det är giltigt och servern beviljar begäran.</span><span class="sxs-lookup"><span data-stu-id="0827b-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="0827b-586">Klient instansen uppdateras sedan med Server informationen vid behov.</span><span class="sxs-lookup"><span data-stu-id="0827b-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-587">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-587">Input Parameters</span></span>

- <span data-ttu-id="0827b-588">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-589">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-589">Return Values</span></span>

- <span data-ttu-id="0827b-590">**NX_SUCCESS** (0X00) meddela att begär ande meddelandet har skapats och bearbetats</span><span class="sxs-lookup"><span data-stu-id="0827b-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="0827b-591">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-592">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-593">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-593">Allowed From</span></span>

<span data-ttu-id="0827b-594">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-595">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-596">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-596">See Also</span></span>

- <span data-ttu-id="0827b-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="0827b-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="0827b-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="0827b-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="0827b-599">Lägg till DNS-server i DHCPv6 option-begäran</span><span class="sxs-lookup"><span data-stu-id="0827b-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-600">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-601">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-601">Description</span></span>

<span data-ttu-id="0827b-602">Den här tjänsten lägger till alternativet för att begära DNS-Server information till DHCPv6-alternativ förfrågan.</span><span class="sxs-lookup"><span data-stu-id="0827b-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="0827b-603">Om servern svarar inkluderar DNS-Datadata kommer klienten att lagra DNS-servern om den har utrymme att göra det.</span><span class="sxs-lookup"><span data-stu-id="0827b-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="0827b-604">Antalet DNS-servrar som klienten kan lagra bestäms av det konfigurerbara alternativet NX_DHCPV6_NUM_DNS_SERVERS vars standardvärde är 2.</span><span class="sxs-lookup"><span data-stu-id="0827b-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-605">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-605">Input Parameters</span></span>

- <span data-ttu-id="0827b-606">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-607">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-607">Return Values</span></span>

- <span data-ttu-id="0827b-608">Alternativet DNS-server för **NX_SUCCESS** (0x00) ingår</span><span class="sxs-lookup"><span data-stu-id="0827b-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="0827b-609">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-610">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-611">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-611">Allowed From</span></span>

<span data-ttu-id="0827b-612">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-613">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="0827b-614">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-614">See Also</span></span>

- <span data-ttu-id="0827b-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="0827b-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="0827b-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="0827b-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="0827b-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="0827b-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="0827b-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="0827b-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="0827b-619">Lägg till fullständigt kvalificerat domän namns alternativ i option Request List</span><span class="sxs-lookup"><span data-stu-id="0827b-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-620">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="0827b-621">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-621">Description</span></span>

<span data-ttu-id="0827b-622">Den här tjänsten lägger till alternativet för att lägga till klientens fullständigt kvalificerade domän namn i DHCPv6 option-begäran.</span><span class="sxs-lookup"><span data-stu-id="0827b-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="0827b-623">Det finns tre alternativ för alternativet FQDN:</span><span class="sxs-lookup"><span data-stu-id="0827b-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="0827b-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 uppdatera FQDN-till-IPv6-adress mappningen för FQDN och adress (er) som används av klienten.</span><span class="sxs-lookup"><span data-stu-id="0827b-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="0827b-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 uppdatera adress mappningen för FQDN-till-IPv6 för FQDN och adress (er) som används av klienten till servern.</span><span class="sxs-lookup"><span data-stu-id="0827b-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="0827b-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 begär att servern inte utför DNS-uppdateringar på klientens vägnar.</span><span class="sxs-lookup"><span data-stu-id="0827b-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-627">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-627">Input Parameters</span></span>

- <span data-ttu-id="0827b-628">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-629">**domain_name** Sträng som innehåller domän namnet</span><span class="sxs-lookup"><span data-stu-id="0827b-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="0827b-630">**op** Typ av FQDN-alternativ som ska användas (se listan ovan)</span><span class="sxs-lookup"><span data-stu-id="0827b-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-631">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-631">Return Values</span></span>

- <span data-ttu-id="0827b-632">Alternativet för **NX_SUCCESS** (0X00) FQDN ingår</span><span class="sxs-lookup"><span data-stu-id="0827b-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="0827b-633">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-634">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-635">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-635">Allowed From</span></span>

<span data-ttu-id="0827b-636">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-637">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="0827b-638">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-638">See Also</span></span>

- <span data-ttu-id="0827b-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="0827b-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="0827b-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="0827b-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="0827b-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="0827b-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="0827b-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="0827b-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="0827b-643">Lägg till domän namns alternativ i DHCPv6 option-begäran</span><span class="sxs-lookup"><span data-stu-id="0827b-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-644">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-645">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-645">Description</span></span>

<span data-ttu-id="0827b-646">Den här tjänsten lägger till alternativet domän namn i option-begäran i klient begär ande meddelanden.</span><span class="sxs-lookup"><span data-stu-id="0827b-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="0827b-647">Om Server svaret inkluderar domän namns data kommer klienten att lagra domän namns informationen om domän namnets storlek ligger inom buffertstorleken för att hålla domän namnet.</span><span class="sxs-lookup"><span data-stu-id="0827b-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="0827b-648">Buffertstorleken är ett konfigurerbart alternativ (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) med ett standardvärde på 30 byte.</span><span class="sxs-lookup"><span data-stu-id="0827b-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-649">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-649">Input Parameters</span></span>

- <span data-ttu-id="0827b-650">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-651">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-651">Return Values</span></span>

- <span data-ttu-id="0827b-652">**NX_SUCCESS** (0x00) alternativ uppsättning för domän namn</span><span class="sxs-lookup"><span data-stu-id="0827b-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="0827b-653">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-654">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-655">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-655">Allowed From</span></span>

<span data-ttu-id="0827b-656">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-657">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="0827b-658">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-658">See Also</span></span>

- <span data-ttu-id="0827b-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="0827b-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="0827b-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="0827b-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="0827b-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="0827b-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="0827b-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="0827b-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="0827b-663">Ange tids Server data som valfri begäran</span><span class="sxs-lookup"><span data-stu-id="0827b-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-664">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-665">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-665">Description</span></span>

<span data-ttu-id="0827b-666">Den här tjänsten lägger till alternativet för Time Server-information i option-begäran om klient begär ande meddelanden.</span><span class="sxs-lookup"><span data-stu-id="0827b-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="0827b-667">Om Server svaret innehåller Tim Server data kommer klienten att lagra tids servern om den har utrymme att göra det.</span><span class="sxs-lookup"><span data-stu-id="0827b-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="0827b-668">Antalet tids servrar som klienten kan lagra bestäms av det konfigurerbara alternativet</span><span class="sxs-lookup"><span data-stu-id="0827b-668">The number of time servers the Client can store is determined by the configurable option</span></span>

<span data-ttu-id="0827b-669">NX_DHCPV6_NUM_TIME _SERVERS vars standardvärde är 1.</span><span class="sxs-lookup"><span data-stu-id="0827b-669">NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-670">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-670">Input Parameters</span></span>

- <span data-ttu-id="0827b-671">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-672">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-672">Return Values</span></span>

- <span data-ttu-id="0827b-673">**NX_SUCCESS** (0X00) tids Server alternativ har lagts till</span><span class="sxs-lookup"><span data-stu-id="0827b-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="0827b-674">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-675">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-676">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-676">Allowed From</span></span>

<span data-ttu-id="0827b-677">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-678">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="0827b-679">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-679">See Also</span></span>

- <span data-ttu-id="0827b-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="0827b-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="0827b-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="0827b-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="0827b-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="0827b-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="0827b-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="0827b-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="0827b-684">Ange tids zons data som valfri begäran</span><span class="sxs-lookup"><span data-stu-id="0827b-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-685">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-686">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-686">Description</span></span>

<span data-ttu-id="0827b-687">Den här tjänsten lägger till alternativet för att begära tids zons information till klient Options förfrågan.</span><span class="sxs-lookup"><span data-stu-id="0827b-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="0827b-688">Om Server svaret innehåller tids zons data, kommer klienten att lagra tids zons informationen om tids zonens storlek ligger inom buffertstorleken för att hålla tids zonen.</span><span class="sxs-lookup"><span data-stu-id="0827b-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="0827b-689">Buffertstorleken är ett konfigurerbart alternativ (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) med ett standardvärde på 10 byte.</span><span class="sxs-lookup"><span data-stu-id="0827b-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-690">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-690">Input Parameters</span></span>

- <span data-ttu-id="0827b-691">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-692">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-692">Return Values</span></span>

- <span data-ttu-id="0827b-693">**NX_SUCCESS** (0X00) tids zons alternativ har lagts till</span><span class="sxs-lookup"><span data-stu-id="0827b-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="0827b-694">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-695">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-696">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-696">Allowed From</span></span>

<span data-ttu-id="0827b-697">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-698">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="0827b-699">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-699">See Also</span></span>

- <span data-ttu-id="0827b-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="0827b-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="0827b-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="0827b-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="0827b-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="0827b-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="0827b-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="0827b-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="0827b-704">Skicka ett DHCPv6-RELEASE-meddelande</span><span class="sxs-lookup"><span data-stu-id="0827b-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-705">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-706">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-706">Description</span></span>

<span data-ttu-id="0827b-707">Den här tjänsten skickar ett RELEASE-meddelande i klient nätverket.</span><span class="sxs-lookup"><span data-stu-id="0827b-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="0827b-708">Om meddelandet har skickats returneras en lyckad status.</span><span class="sxs-lookup"><span data-stu-id="0827b-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="0827b-709">En lyckad slut för ande innebär inte att klienten tog emot ett svar eller har beviljats en IPv6-adress ännu.</span><span class="sxs-lookup"><span data-stu-id="0827b-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="0827b-710">Aktiviteten DHCPv6 klient tråd väntar på ett svar från en DHCPv6-server.</span><span class="sxs-lookup"><span data-stu-id="0827b-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="0827b-711">Om ett tas emot, kontrollerar det att svaret är giltigt och lagrar data till klient posten.</span><span class="sxs-lookup"><span data-stu-id="0827b-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-712">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-712">Input Parameters</span></span>

- <span data-ttu-id="0827b-713">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-714">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-714">Return Values</span></span>

- <span data-ttu-id="0827b-715">**NX_SUCCESS** (0X00) versions meddelandet har skickats</span><span class="sxs-lookup"><span data-stu-id="0827b-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="0827b-716">**NX_DHCPV6_NOT_STARTED** (0XE92) DHCPV6-klient aktiviteten har inte startats</span><span class="sxs-lookup"><span data-stu-id="0827b-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="0827b-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** -adressen (0xEAD) är inte kopplad till klienten</span><span class="sxs-lookup"><span data-stu-id="0827b-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="0827b-718">Det gick inte att hitta **NX_INVALID_INTERFACE** (0x4C) i IP-adress tabellen</span><span class="sxs-lookup"><span data-stu-id="0827b-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="0827b-719">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-720">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-721">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-721">Allowed From</span></span>

<span data-ttu-id="0827b-722">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-723">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-724">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-724">See Also</span></span>

- <span data-ttu-id="0827b-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="0827b-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="0827b-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="0827b-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="0827b-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="0827b-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="0827b-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="0827b-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="0827b-729">Skicka ett INBJUDNINGs meddelande</span><span class="sxs-lookup"><span data-stu-id="0827b-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-730">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-731">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-731">Description</span></span>

<span data-ttu-id="0827b-732">Den här tjänsten skickar ett INBJUDNINGs meddelande ut från nätverket.</span><span class="sxs-lookup"><span data-stu-id="0827b-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="0827b-733">Om meddelandet har skickats returneras en lyckad status.</span><span class="sxs-lookup"><span data-stu-id="0827b-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="0827b-734">En lyckad slut för ande innebär inte att klienten tog emot ett svar eller har beviljats en IPv6-adress ännu.</span><span class="sxs-lookup"><span data-stu-id="0827b-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="0827b-735">Aktiviteten DHCPv6 klient tråd väntar på ett svar (ett ANNONSERINGs meddelande) från en DHCPv6-server.</span><span class="sxs-lookup"><span data-stu-id="0827b-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="0827b-736">Om en tas emot, kontrol leras att svaret är giltigt, lagrar data i klient posten och befordrar klienten till status för begäran.</span><span class="sxs-lookup"><span data-stu-id="0827b-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="0827b-737">Om alternativet för snabb incheckning är inställt, går DHCPv6-klienten direkt till det begränsade tillstånd om den får ett giltigt meddelande om Server annonsering.</span><span class="sxs-lookup"><span data-stu-id="0827b-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="0827b-738">Mer information finns i tjänst beskrivningen för *nx_dhcpv6_request_solicit_rapid* .</span><span class="sxs-lookup"><span data-stu-id="0827b-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-739">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-739">Input Parameters</span></span>

- <span data-ttu-id="0827b-740">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-741">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-741">Return Values</span></span>

- <span data-ttu-id="0827b-742">**NX_SUCCESS** (0X00) SOLICIT-meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="0827b-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="0827b-743">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-744">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-745">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-745">Allowed From</span></span>

<span data-ttu-id="0827b-746">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-747">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="0827b-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="0827b-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="0827b-749">Skicka ett INBJUDNINGs meddelande med alternativet för snabb incheckning</span><span class="sxs-lookup"><span data-stu-id="0827b-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-750">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-751">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-751">Description</span></span>

<span data-ttu-id="0827b-752">Den här tjänsten skickar ett VÄRVNINGs meddelande i nätverket med alternativet för snabb incheckning.</span><span class="sxs-lookup"><span data-stu-id="0827b-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="0827b-753">Om meddelandet har skickats returneras en lyckad status.</span><span class="sxs-lookup"><span data-stu-id="0827b-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="0827b-754">En lyckad slut för ande innebär inte att klienten tog emot ett svar eller har beviljats en IPv6-adress ännu.</span><span class="sxs-lookup"><span data-stu-id="0827b-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="0827b-755">Aktiviteten DHCPv6 klient tråd väntar på ett svar (ett ANNONSERINGs meddelande) från en DHCPv6-server.</span><span class="sxs-lookup"><span data-stu-id="0827b-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="0827b-756">Om en tas emot, kontrollerar det att svaret är giltigt, lagrar data till klient posten och befordrar klienten till ett begränsat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="0827b-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-757">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-757">Input Parameters</span></span>

- <span data-ttu-id="0827b-758">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-759">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-759">Return Values</span></span>

- <span data-ttu-id="0827b-760">**NX_SUCCESS** (0X00) SOLICIT-meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="0827b-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="0827b-761">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-762">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-763">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-763">Allowed From</span></span>

<span data-ttu-id="0827b-764">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-765">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-766">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-766">See Also</span></span>

- <span data-ttu-id="0827b-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="0827b-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="0827b-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="0827b-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="0827b-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="0827b-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="0827b-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="0827b-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="0827b-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="0827b-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="0827b-772">Återuppta DHCPv6-klient aktivitet</span><span class="sxs-lookup"><span data-stu-id="0827b-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-773">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-774">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-774">Description</span></span>

<span data-ttu-id="0827b-775">Den här tjänsten återupptar aktiviteten för DHCPv6 client-tråden.</span><span class="sxs-lookup"><span data-stu-id="0827b-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="0827b-776">Aktuellt DHCPv6-klient tillstånd kommer att bearbetas (t. ex. bounds, solicit)</span><span class="sxs-lookup"><span data-stu-id="0827b-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-777">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-777">Input Parameters</span></span>

- <span data-ttu-id="0827b-778">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-779">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-779">Return Values</span></span>

- <span data-ttu-id="0827b-780">**NX_SUCCESS** (0X00) klienten har återupptagits</span><span class="sxs-lookup"><span data-stu-id="0827b-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="0827b-781">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-782">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-783">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-783">Allowed From</span></span>

<span data-ttu-id="0827b-784">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-785">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-786">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-786">See Also</span></span>

- <span data-ttu-id="0827b-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="0827b-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="0827b-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="0827b-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="0827b-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="0827b-790">nx_dhcpv6_set_ time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="0827b-791">Anger den tid som periodiseras på klientens IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="0827b-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="0827b-792">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="0827b-793">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-793">Description</span></span>

<span data-ttu-id="0827b-794">Den här tjänsten anger den tid som ska periodiseras på klientens globala IP-adress sedan den tilldelades av servern.</span><span class="sxs-lookup"><span data-stu-id="0827b-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="0827b-795">Detta bör endast användas om en klient för närvarande är kopplad till en tilldelad IPv6-adress.</span><span class="sxs-lookup"><span data-stu-id="0827b-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-796">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-796">Input Parameters</span></span>

- <span data-ttu-id="0827b-797">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="0827b-798">**time_accrued** Tid som periodiseras i IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="0827b-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-799">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-799">Return Values</span></span>

- <span data-ttu-id="0827b-800">**NX_SUCCESS** (0x00) som har angetts</span><span class="sxs-lookup"><span data-stu-id="0827b-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="0827b-801">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-802">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-802">Allowed From</span></span>

<span data-ttu-id="0827b-803">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-804">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-805">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-805">See Also</span></span>

- <span data-ttu-id="0827b-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="0827b-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="0827b-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="0827b-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="0827b-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="0827b-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="0827b-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="0827b-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="0827b-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="0827b-811">Starta aktiviteten DHCPv6-klient</span><span class="sxs-lookup"><span data-stu-id="0827b-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-812">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-813">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-813">Description</span></span>

<span data-ttu-id="0827b-814">Den här tjänsten startar DHCPv6-klient aktiviteten och förbereder klienten för att köra DHCPv6-protokollet.</span><span class="sxs-lookup"><span data-stu-id="0827b-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="0827b-815">Den verifierar att klient instansen har tillräckligt med information (till exempel en klient-DUID), skapar och binder UDP-socketen för att skicka och ta emot DHCPv6-meddelanden och aktiverar timers för att hålla reda på sessionens tid och när det aktuella IPv6-lånet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="0827b-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-816">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-816">Input Parameters</span></span>

- <span data-ttu-id="0827b-817">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-818">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-818">Return Values</span></span>

- <span data-ttu-id="0827b-819">**NX_SUCCESS** (0X00) klienten har startats</span><span class="sxs-lookup"><span data-stu-id="0827b-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="0827b-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** -klienten (0xEA9) saknar nödvändiga alternativ</span><span class="sxs-lookup"><span data-stu-id="0827b-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="0827b-821">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-822">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-823">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-823">Allowed From</span></span>

<span data-ttu-id="0827b-824">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-825">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-826">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-826">See Also</span></span>

- <span data-ttu-id="0827b-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="0827b-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="0827b-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="0827b-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="0827b-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="0827b-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="0827b-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="0827b-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="0827b-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="0827b-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="0827b-832">Stoppa aktiviteten DHCPv6-klient</span><span class="sxs-lookup"><span data-stu-id="0827b-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-833">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-834">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-834">Description</span></span>

<span data-ttu-id="0827b-835">Den här tjänsten stoppar DHCPv6-klientens aktivitet och rensar återöverförings antal, högsta antal återöverförings intervall, inaktive ring av sessionens och lånets förfallo tider och avbinder DHCPv6-klientens socket-port.</span><span class="sxs-lookup"><span data-stu-id="0827b-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="0827b-836">Om du vill starta om klienten måste du först stoppa och eventuellt initiera klienten igen innan du påbörjar en annan session med en DHCPv6-server.</span><span class="sxs-lookup"><span data-stu-id="0827b-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="0827b-837">Mer information finns i avsnittet om litet exempel.</span><span class="sxs-lookup"><span data-stu-id="0827b-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-838">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-838">Input Parameters</span></span>

- <span data-ttu-id="0827b-839">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-840">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-840">Return Values</span></span>

- <span data-ttu-id="0827b-841">**NX_SUCCESS** (0X00) klienten har stoppats</span><span class="sxs-lookup"><span data-stu-id="0827b-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="0827b-842">**NX_DHCPV6_NOT_STARTED** (0XE92) klient tråden har inte startats</span><span class="sxs-lookup"><span data-stu-id="0827b-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="0827b-843">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-844">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0827b-845">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-845">Allowed From</span></span>

<span data-ttu-id="0827b-846">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-847">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-848">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-848">See Also</span></span>

- <span data-ttu-id="0827b-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="0827b-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="0827b-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="0827b-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="0827b-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="0827b-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="0827b-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="0827b-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="0827b-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="0827b-854">Pausa aktiviteten DHCPv6-klient</span><span class="sxs-lookup"><span data-stu-id="0827b-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="0827b-855">Prototyp</span><span class="sxs-lookup"><span data-stu-id="0827b-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="0827b-856">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0827b-856">Description</span></span>

<span data-ttu-id="0827b-857">Den här tjänsten pausar DHCPv6-klient aktiviteten och alla begär Anden som den var i mitten av bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="0827b-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="0827b-858">Timers har inaktiverats och klientens tillstånd är inställt på att inte köras.</span><span class="sxs-lookup"><span data-stu-id="0827b-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0827b-859">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="0827b-859">Input Parameters</span></span>

- <span data-ttu-id="0827b-860">**dhcpv6_ptr** Pekare till DHCPv6-klient instans</span><span class="sxs-lookup"><span data-stu-id="0827b-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="0827b-861">Retur värden</span><span class="sxs-lookup"><span data-stu-id="0827b-861">Return Values</span></span>

- <span data-ttu-id="0827b-862">**NX_SUCCESS** (0X00) klienten har pausats</span><span class="sxs-lookup"><span data-stu-id="0827b-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="0827b-863">**NX_DHCPV6_NOT_STARTED** -klienten (0XE92) körs inte och kan inte pausas</span><span class="sxs-lookup"><span data-stu-id="0827b-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="0827b-864">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="0827b-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="0827b-865">NX_CALLER_ERROR (0x11) måste anropas från tråd</span><span class="sxs-lookup"><span data-stu-id="0827b-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0827b-866">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="0827b-866">Allowed From</span></span>

<span data-ttu-id="0827b-867">Konversation</span><span class="sxs-lookup"><span data-stu-id="0827b-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0827b-868">Exempel</span><span class="sxs-lookup"><span data-stu-id="0827b-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="0827b-869">Se även</span><span class="sxs-lookup"><span data-stu-id="0827b-869">See Also</span></span>

- <span data-ttu-id="0827b-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="0827b-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="0827b-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="0827b-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="0827b-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="0827b-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="0827b-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="0827b-873">nx_dhcpv6_stop</span></span>
